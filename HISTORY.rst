=======
History
=======

May 1, 2014
===========

* Renamed to ``python3-ping`` for Python 3 by Mohammad Emami on PyPI_
  and GitHub_.

.. _PyPI: https://pypi.python.org/pypi/python3-ping
.. _GitHub: https://github.com/emamirazavi/python3-ping

March 19, 2013
==============

* Fixing bug to prevent divide by 0 during run-time.

January 26, 2012
================

* Fixing BUG #4 - compatibility with python 2.x [tested with 2.7]

  Packet data building is different for 2.x and 3.x because of the string/bytes
  difference.

* Fixing BUG #10 - the multiple resolv issue.

  When pinging domain names instead of hosts (for example ``google.com``) you
  can get different IP every time you try to resolve it, we should resolve the
  host only once and stick to that IP.

* Fixing BUGs #3 #10 - Doing hostname resolution only once.
* Fixing BUG #14 - Removing all ``global`` stuff.

  You should not use ``global``! It's bad for you...and its not thread safe!

* Fix - forcing the use of different times on Linux/Windows for more accurate
  measurements. (``time.time`` for Linux and ``time.clock`` for Windows)
* Adding ``quiet_ping`` function - This way we'll be able to use this script
  as external lib.
* Changing default timeout to 3s. (1second is not enough)
* Switching data size to packet size. It's easier for the user to ignore the
  fact that the packet header is 8b and the datasize 64 will make packet with
  size 72.

October 17, 2011
================

* Bugfix if host is unknown

October 12, 2011
================

Merge sources and create a separate GitHub repository:

* ``https://github.com/jedie/python-ping``

Add a simple CLI interface.

September 12, 2011
==================

Bugfixes + cleanup by Jens Diemer. Tested with Ubuntu + Windows 7

September 6, 2011
=================

`Cleanup by Martin Falatic`__.Restored lost comments and docs. Improved
functionality: constant time between pings, internal times consistently use
milliseconds. Clarified annotations (e.g., in the checksum routine). Using
unsigned data in IP & ICMP header pack/unpack unless otherwise necessary.
Signal handling. Ping-style output formatting and stats.

__ http://www.falatic.com/index.php/39/pinging-with-python

August 3, 2011
==============

Ported to py3k by Zach Ware. Mostly done by 2to3; also minor changes to
deal with bytes vs. string changes (no more ``ord()`` in ``checksum()`` because
``source_string`` is actually ``bytes``, added ``.encode()`` to data in
``send_one_ping()``).  That's about it.

March 11, 2010
==============

Changes by Samuel Stauffer: replaced ``time.clock`` with ``default_timer``
which is set to ``time.clock`` on Windows and ``time.time`` on other systems.

November 8, 2009
================

Fixes by `George Notaras`_, reported by Chris Hallman: Improved compatibility
with GNU/Linux systems.

.. _George Notaras: http://www.g-loaded.eu/2009/10/30/python-ping/

Changes in this release:

Re-use ``time.time()`` instead of ``time.clock()``. The 2007 implementation
worked only under Microsoft Windows. Failed on GNU/Linux. ``time.clock()``
behaves differently under `the two OSes`_:

.. _the two OSes: http://docs.python.org/library/time.html#time.clock

May 30, 2007
============

little rewrite by Jens Diemer:

* change socket asterisk import to a normal import
* replace ``time.time()`` with ``time.clock()``
* delete ``return None`` (or change to ``return`` only)
* in ``checksum()`` rename ``str`` to ``source_string``

December 4, 2000
================

Changed the ``struct.pack()`` calls to pack the checksum and ID as
unsigned. My thanks to Jerome Poincheval for the fix.

November 22, 1997
=================

Initial hack. Doesn't do much, but rather than try to guess
what features I (or others) will want in the future, I've only
put in what I need now.

December 16, 1997
=================

For some reason, the checksum bytes are in the wrong order when
this is run under Solaris 2.X for SPARC but it works right under
Linux x86. Since I don't know just what's wrong, I'll swap the
bytes always and then do an htons().
