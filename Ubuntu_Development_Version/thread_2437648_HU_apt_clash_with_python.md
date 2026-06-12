---
title: "HU apt clash with python"
date: 2020-02-27
forum: Ubuntu Development Version
---

### Post by zika on 2020-02-27
```
Traceback (most recent call last):
  File "/usr/lib/cnf-update-db", line 8, in <module>
    from CommandNotFound.db.creator import DbCreator
  File "/usr/lib/python3/dist-packages/CommandNotFound/db/creator.py", line 11, in <module>
    import apt_pkg
ImportError: /usr/lib/python3/dist-packages/apt_pkg.cpython-38-x86_64-linux-gnu.so: undefined symbol: _ZTI9pkgDPkgPM, version APTPKG_6.0
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 63, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 5, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 30, in <module>
    import apport.fileutils
  File "/usr/lib/python3/dist-packages/apport/fileutils.py", line 23, in <module>
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python3/dist-packages/apport/packaging_impl.py", line 23, in <module>
    import apt
  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
    import apt_pkg
ImportError: /usr/lib/python3/dist-packages/apt_pkg.cpython-38-x86_64-linux-gnu.so: undefined symbol: _ZTI9pkgDPkgPM, version APTPKG_6.0

Original exception was:
Traceback (most recent call last):
  File "/usr/lib/cnf-update-db", line 8, in <module>
    from CommandNotFound.db.creator import DbCreator
  File "/usr/lib/python3/dist-packages/CommandNotFound/db/creator.py", line 11, in <module>
    import apt_pkg
ImportError: /usr/lib/python3/dist-packages/apt_pkg.cpython-38-x86_64-linux-gnu.so: undefined symbol: _ZTI9pkgDPkgPM, version APTPKG_6.0
...
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/lib/command-not-found/ -a -e /usr/lib/cnf-update-db; then /usr/lib/cnf-update-db > /dev/null; fi'
E: Sub-process returned an error code
``````
:~$ apt policy apt
apt:
  Installed: 1.9.11
  Candidate: 1.9.11
  Version table:
 *** 1.9.11 500
        500 http://us.archive.ubuntu.com/ubuntu devel-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     1.9.10+0~202002252104~ubuntu20.04.1 500
        500 http://ppa.launchpad.net/deity/sid/ubuntu devel/main amd64 Packages
     1.9.10 500
        500 http://us.archive.ubuntu.com/ubuntu devel/main amd64 Packages
```
```
apt (1.9.11) experimental; urgency=medium

  [ Tomá&#353; Janou&#353;ek ]
  * bash completion: Add autopurge command

  [ Tris Emmy Wilson ]
  * apt-mark: don't lie about successful marks

  [ Julian Andres Klode ]
  * apt(8): Wait for lock (Closes: #754103)
  * policy: Implement pinning by source package (Closes: #166032)
  * Initialize libgcrypt on first use (Closes: #949074)
  * Fix various compiler warnings
  * Bump ABI to 6.0; update symbols file; cleanup ABI:
    - Merge various function overloads together
    - Make stuff that should be virtual virtual
    - Default to hidden visibility
  * Code removals:
    - Use a 32-bit djb VersionHash instead of CRC-16
    - Remove CRC-16 implementation
  * Hardening:
    - tagfile: Check if memchr() returned null before using
    - tagfile: Check out-of-bounds access to Tags vector
  * Cache improvements:
    - Type safe cache: Replace map_pointer_t with map_pointer<T>
    - Extensibility: Add d-pointers to groups, packages, versions, and files
    - Prepare for package hashtable removal: Swap locations of hashtables

  [ Nis Martensen ]
  * apt-pkg/srcrecords.cc: 'source' means 'deb-src' in error message

  [ David Kalnischkies ]
  * Parse records including empty tag names correctly

 -- Julian Andres Klode <jak@debian.org>  Wed, 26 Feb 2020 21:29:48 +0100
```

Update&#8321;:
No change with:
```
:~$ apt policy apt:
  Installed: 1.9.12
  Candidate: 1.9.12
  Version table:
 *** 1.9.12 500
        500 http://uk.archive.ubuntu.com/ubuntu devel-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     1.9.10+0~202002252104~ubuntu20.04.1 500
        500 http://ppa.launchpad.net/deity/sid/ubuntu devel/main amd64 Packages
     1.9.10 500
        500 http://uk.archive.ubuntu.com/ubuntu devel/main amd64 Packages
```

Update&#8322;: It seems that it is not due to apt but it gives same sort of error if You choose to give non-existing command on bash command line... I would say it is corrected with today's updates...

---

