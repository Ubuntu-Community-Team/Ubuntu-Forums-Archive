---
title: "apt-get mess due to zope..."
date: 2007-08-14
forum: Server Platforms
---

### Post by wanabewired on 2007-08-14
I recently tried to install Zope3 on FF/7.04 server and it threw a bit of a paddy. I have since successfully installed Zope on another server so that part of my problem is solved, the problem i am left with is my apt-get feedback is now a mess. When i run apt-get install <package> I get about 50 lines of python exceptions, tracebacks and dependancy warnings relevant to the failed zope installation.

The output is as below. Any help on cleaning up would be very much appreciated.

```

andy@epserver1:/etc/apt$ sudo apt-get install wget
Reading package lists... Done
Building dependency tree
Reading state information... Done
wget is already the newest version.
The following packages were automatically installed and are no longer required:
  python2.4-minimal
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
11 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up python-crypto (2.0.1+dfsg1-1.2ubuntu1) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 875, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 198, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 126, in default_version
    _default_version = link = os.readlink('/usr/bin/python')
OSError: [Errno 22] Invalid argument: '/usr/bin/python'
dpkg: error processing python-crypto (--configure):
 subprocess post-installation script returned error exit status 1
Setting up python-roman (0.4-3build2) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 875, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 198, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 126, in default_version
    _default_version = link = os.readlink('/usr/bin/python')
OSError: [Errno 22] Invalid argument: '/usr/bin/python'
dpkg: error processing python-roman (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-docutils:
 python-docutils depends on python-roman; however:
  Package python-roman is not configured yet.
dpkg: error processing python-docutils (--configure):
 dependency problems - leaving unconfigured
Setting up python-zopeinterface (3.3.1-0ubuntu3) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 875, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 198, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 126, in default_version
    _default_version = link = os.readlink('/usr/bin/python')
OSError: [Errno 22] Invalid argument: '/usr/bin/python'
dpkg: error processing python-zopeinterface (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-twisted-core:
 python-twisted-core depends on python-zopeinterface (>= 3.2.1-3); however:
  Package python-zopeinterface is not configured yet.
dpkg: error processing python-twisted-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-web2:
 python-twisted-web2 depends on python-twisted-core (>= 2.5); however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-twisted-web2 (--configure):
 dependency problems - leaving unconfigured
Setting up python-xml (0.8.4-6ubuntu4) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 875, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 198, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 126, in default_version
    _default_version = link = os.readlink('/usr/bin/python')
OSError: [Errno 22] Invalid argument: '/usr/bin/python'
dpkg: error processing python-xml (--configure):
 subprocess post-installation script returned error exit status 1
Setting up python-clientform (0.2.2-3) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 875, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 198, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 126, in default_version
    _default_version = link = os.readlink('/usr/bin/python')
OSError: [Errno 22] Invalid argument: '/usr/bin/python'
dpkg: error processing python-clientform (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-mechanize:
 python-mechanize depends on python-clientform (>= 0.2.2); however:
  Package python-clientform is not configured yet.
dpkg: error processing python-mechanize (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-conch:
 python-twisted-conch depends on python-crypto (>= 2.0.1+dfsg1-1.1); however:
  Package python-crypto is not configured yet.
 python-twisted-conch depends on python-twisted-core (>= 2.5); however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-twisted-conch (--configure):
 dependency problems - leaving unconfigured
Setting up python-tz (2007c-0ubuntu1) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 875, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 198, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 126, in default_version
    _default_version = link = os.readlink('/usr/bin/python')
OSError: [Errno 22] Invalid argument: '/usr/bin/python'
dpkg: error processing python-tz (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-crypto
 python-roman
 python-docutils
 python-zopeinterface
 python-twisted-core
 python-twisted-web2
 python-xml
 python-clientform
 python-mechanize
 python-twisted-conch
 python-tz
E: Sub-process /usr/bin/dpkg returned an error code (1)
andy@epserver1:/etc/apt$

```

Thanks in advance for any help.

---

### Post by tjk on 2008-01-16
Did you ever get this resolved, or does anyone else know what the answer is?  I now have the same problem with zope 2.10 (after I uninstalled all the other zope versions)

I found some ideas else where, like: [http://ubuntuforums.org/showthread.php?t=526497&page=2](http://ubuntuforums.org/showthread.php?t=526497&page=2)  -- but they didn't help...

---

### Post by Claytonious on 2008-03-12
This is because /usr/bin/python is supposed to be a soft link to the actual versioned python executable, but yours is probably the actual python file itself. To fix the problem, do something like this:

cd /usr/bin
sudo ln -sf python2.5 python

---

