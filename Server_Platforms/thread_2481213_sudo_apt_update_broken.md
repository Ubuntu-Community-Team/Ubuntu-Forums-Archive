---
title: "sudo apt update broken"
date: 2022-11-22
forum: Server Platforms
---

### Post by janderion on 2022-11-22
Hello, I recently updated software on my ubuntu server using apt and now "sudo apt update" is broken.
The output appears as follows:

```
sudo apt update
Hit:1 http://ports.ubuntu.com/ubuntu-ports jammy InRelease
Get:2 http://ports.ubuntu.com/ubuntu-ports jammy-updates InRelease [114 kB]
Get:3 http://ports.ubuntu.com/ubuntu-ports jammy-backports InRelease [99.8 kB]
Get:4 http://ports.ubuntu.com/ubuntu-ports jammy-security InRelease [110 kB]
Get:5 http://ports.ubuntu.com/ubuntu-ports jammy-updates/main arm64 Packages [675 kB]
Get:6 http://ports.ubuntu.com/ubuntu-ports jammy-updates/restricted arm64 Packages [175 kB]
Get:7 http://ports.ubuntu.com/ubuntu-ports jammy-updates/universe arm64 Packages [649 kB]
Fetched 1823 kB in 4s (468 kB/s)                        
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
Python path configuration:
  PYTHONHOME = (not set)
  PYTHONPATH = (not set)
  program name = '/usr/bin/python3'
  isolated = 0
  environment = 1
  user site = 1
  import site = 1
  sys._base_executable = '/usr/bin/python3'
  sys.base_prefix = '/usr'
  sys.base_exec_prefix = '/usr'
  sys.platlibdir = 'lib'
  sys.executable = '/usr/bin/python3'
  sys.prefix = '/usr'
  sys.exec_prefix = '/usr'
  sys.path = [
    '/usr/lib/python310.zip',
    '/usr/lib/python3.10',
    '/usr/lib/lib-dynload',
  ]
Fatal Python error: init_fs_encoding: failed to get the Python codec of the filesystem encoding
Python runtime state: core initialized
ModuleNotFoundError: No module named 'encodings'


Current thread 0x0000ffff8cc0a420 (most recent call first):
  <no Python frame>
Reading package lists... Done
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/lib/command-not-found/ -a -e /usr/lib/cnf-update-db; then /usr/lib/cnf-update-db > /dev/null; fi'
E: Sub-process returned an error code

```

If anyone could help me out, it would be a blessing. Thanks.

---

### Post by janderion on 2022-11-22
In attempting to do more things with my server, it appears the problem is in Python, perhaps it is lacking some files as if something was not downloaded in the last update. In attempting to run "s-tui", the following occured.

```

s-tui
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
Python path configuration:
  PYTHONHOME = (not set)
  PYTHONPATH = (not set)
  program name = '/usr/bin/python3'
  isolated = 0
  environment = 1
  user site = 1
  import site = 1
  sys._base_executable = '/usr/bin/python3'
  sys.base_prefix = '/usr'
  sys.base_exec_prefix = '/usr'
  sys.platlibdir = 'lib'
  sys.executable = '/usr/bin/python3'
  sys.prefix = '/usr'
  sys.exec_prefix = '/usr'
  sys.path = [
    '/usr/lib/python310.zip',
    '/usr/lib/python3.10',
    '/usr/lib/lib-dynload',
  ]
Fatal Python error: init_fs_encoding: failed to get the Python codec of the filesystem encoding
Python runtime state: core initialized
ModuleNotFoundError: No module named 'encodings'


Current thread 0x0000ffff9b81a420 (most recent call first):
  <no Python frame>

```

---

### Post by LHammonds on 2022-11-23
I assume you are running Ubuntu Server 22.04 LTS because of the "jammy" repositories.

Python3 comes pre-installed with Ubuntu.   Did you install any other versions of Python on the system?

LHammonds

---

### Post by janderion on 2022-11-23
No, I have not installed any other versions of python. This behavior just occurred after updating software recently using apt.

---

### Post by grigglestone on 2023-01-18
I also had this issue and from this thread realized it was because I had installed an earlier release of Python (3.7) (and created an alternative to the more recent 3.10 version). This also broke my command line terminal. So to fix I set the alternative back to the original version 3.10 and only use 3.7 when I really have to be cause of the project I'm working on.

---

### Post by MAFoElffen on 2023-01-19
For Jammy:
```

mafoelffen@Mikes-ThinkPad-T520:~$ python3 --version
Python 3.10.6
mafoelffen@Mikes-ThinkPad-T520:~$ lsb_release -d
Description:    Ubuntu 22.04.1 LTS

```
It might help if you posted yours to see if different(?)

---

