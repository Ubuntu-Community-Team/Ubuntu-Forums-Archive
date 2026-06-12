---
title: "Rdiff-Assertion Error"
date: 2009-05-03
forum: Server Platforms
---

### Post by shoaibi on 2009-05-03
Anybody who could give me an idea about:




on backup server:
```


/usr/bin/rdiff-backup -v5 --print-statistics --test-server backup@fileserver::/var/exports/ /var/backups/fileserver/
Using rdiff-backup version 1.2.8
Executing ssh -C backup@fileserver rdiff-backup --server
Exception '' raised of class '<type 'exceptions.AssertionError'>':
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 304, in error_check_Main
    try: Main(arglist)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 324, in Main
    take_action(rps)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 291, in take_action
    elif action == "test-server": SetConnections.TestConnections(rps)
  File "/var/lib/python-support/python2.5/rdiff_backup/SetConnections.py", line 248, in TestConnections
    assert len(Globals.connections) == len(rpaths) + 1

Traceback (most recent call last):
  File "/usr/bin/rdiff-backup", line 30, in <module>
    rdiff_backup.Main.error_check_Main(sys.argv[1:])
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 304, in error_check_Main
    try: Main(arglist)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 324, in Main
    take_action(rps)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 291, in take_action
    elif action == "test-server": SetConnections.TestConnections(rps)
  File "/var/lib/python-support/python2.5/rdiff_backup/SetConnections.py", line 248, in TestConnections
    assert len(Globals.connections) == len(rpaths) + 1
AssertionError
root@backup:~# Fatal Error: Lost connection to the remote system

root@backup:~# dpkg -l | grep python
ii  python                                2.5.2-1ubuntu1                An interactive high-level object-oriented la
ii  python-apt                            0.7.7.1ubuntu4                Python interface to libapt-pkg
ii  python-central                        0.6.7ubuntu1                  register and build utility for Python packag
ii  python-gdbm                           2.5.2-1ubuntu1                GNU dbm database support for Python
ii  python-gnupginterface                 0.3.2-9ubuntu1                Python interface to GnuPG (GPG)
ii  python-minimal                        2.5.2-1ubuntu1                A minimal subset of the Python language (def
ii  python-pexpect                        2.1-1build1                   Python module for automating interactive app
ii  python-pylibacl                       0.4.0-1ubuntu1                module for manipulating POSIX.1e ACLs
ii  python-pyxattr                        0.4.0-1ubuntu1                module for manipulating filesystem extended 
ii  python-support                        0.8.4                         automated rebuilding support for Python modu
ii  python2.5                             2.5.2-11.1ubuntu1             An interactive high-level object-oriented la
ii  python2.5-dev                         2.5.2-11.1ubuntu1             Header files and a static library for Python
ii  python2.5-minimal                     2.5.2-11.1ubuntu1             A minimal subset of the Python language (ver
root@backup:~# dpkg -l | grep rdiff
ii  rdiff-backup                          1.2.8-1~andol2~intrepid1      remote incremental backup

```




on Fileserver:


```

root@fileserver:~# dpkg -l | grep python
ii  python                                2.5.2-1ubuntu1                An interactive high-level object-oriented la
ii  python-apt                            0.7.7.1ubuntu4                Python interface to libapt-pkg
ii  python-central                        0.6.7ubuntu1                  register and build utility for Python packag
ii  python-gdbm                           2.5.2-1ubuntu1                GNU dbm database support for Python
ii  python-gnupginterface                 0.3.2-9ubuntu1                Python interface to GnuPG (GPG)
ii  python-minimal                        2.5.2-1ubuntu1                A minimal subset of the Python language (def
ii  python-pexpect                        2.1-1build1                   Python module for automating interactive app
ii  python-pylibacl                       0.4.0-1ubuntu1                module for manipulating POSIX.1e ACLs
ii  python-pyxattr                        0.4.0-1ubuntu1                module for manipulating filesystem extended 
ii  python-support                        0.8.4                         automated rebuilding support for Python modu
ii  python2.5                             2.5.2-11.1ubuntu1             An interactive high-level object-oriented la
ii  python2.5-dev                         2.5.2-11.1ubuntu1             Header files and a static library for Python
ii  python2.5-minimal                     2.5.2-11.1ubuntu1             A minimal subset of the Python language (ver
root@fileserver:~# dpkg -l | grep rdiff
ii  rdiff-backup                          1.2.8-1~andol2~intrepid1      remote incremental backup

```


Both have:
```

dpkg -l | grep ssh
ii  openssh-blacklist                     0.4.1                         list of default blacklisted OpenSSH RSA and 
ii  openssh-client                        1:5.1p1-3ubuntu1              secure shell client, an rlogin/rsh/rcp repla
ii  openssh-server                        1:5.1p1-3ubuntu1              secure shell server, an rshd replacement
ii  ssh                                   1:5.1p1-3ubuntu1              secure shell client and server (metapackage)
root@fileserver:/home/shoaibi# dpkg -l | grep rsync
ii  librsync-dev                          0.9.7-5                       rsync remote-delta algorithm library (develo
ii  librsync1                             0.9.7-5                       rsync remote-delta algorithm library
ii  rsync                                 3.0.3-2ubuntu1                fast remote file copy program (like rcp)


```

Both machine are Ubuntu 8.10 Intrepid Ibex.

---

### Post by samosamo on 2009-05-03
Looks like a python error to me

---

### Post by shoaibi on 2009-05-03
Nope, I was mistaken.
The correct command is:
/usr/bin/rdiff-backup -v5 --print-statistics --test-server backup@fileserver::/var/exports/

See, no destionation required just to test.

---

### Post by matsti on 2009-05-03
Could your rdiff-backup depends on python (< 2.5) but you have a higher version (2.5.2-3?) installed?

---

