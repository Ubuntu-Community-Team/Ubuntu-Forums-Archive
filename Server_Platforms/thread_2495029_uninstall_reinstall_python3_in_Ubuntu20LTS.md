---
title: "uninstall reinstall python3 in Ubuntu20LTS"
date: 2024-02-04
forum: Server Platforms
---

### Post by Heeter on 2024-02-04
Hi all,

Tried upgrading the python from 2.7 to 3.7 on my mailserver. This is on Ubuntu20LTS

I think that I botched it

```

root@mail:~/mlmmjadmin-3.1.9/tools# python -V
Traceback (most recent call last):
  File "/usr/lib/command-not-found", line 28, in <module>
    from CommandNotFound import CommandNotFound
  File "/usr/lib/python3/dist-packages/CommandNotFound/CommandNotFound.py", line 19, in <module>
    from CommandNotFound.db.db import SqliteDatabase
  File "/usr/lib/python3/dist-packages/CommandNotFound/db/db.py", line 5, in <module>
    import apt_pkg
ModuleNotFoundError: No module named 'apt_pkg'
root@mail:~/mlmmjadmin-3.1.9/tools# 

```

```

root@mail:~/mlmmjadmin-3.1.9/tools# sudo apt update
Hit:1 http://security.ubuntu.com/ubuntu focal-security InRelease
Hit:2 http://ca.archive.ubuntu.com/ubuntu focal InRelease
Get:3 http://ca.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Hit:4 http://ppa.launchpad.net/deadsnakes/ppa/ubuntu focal InRelease
Hit:5 http://ca.archive.ubuntu.com/ubuntu focal-backports InRelease
Fetched 114 kB in 1s (84.1 kB/s)
Traceback (most recent call last):
  File "/usr/lib/cnf-update-db", line 8, in <module>
    from CommandNotFound.db.creator import DbCreator
  File "/usr/lib/python3/dist-packages/CommandNotFound/db/creator.py", line 12, in <module>
    import apt_pkg
ModuleNotFoundError: No module named 'apt_pkg'
Reading package lists... Done
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/lib/command-not-found/ -a -e /usr/lib/cnf-update-db; then /usr/lib/cnf-update-db > /dev/null; fi'
E: Sub-process returned an error code
root@mail:~/mlmmjadmin-3.1.9/tools# 

```
```

root@mail:~/mlmmjadmin-3.1.9/tools# python3
Python 3.7.17 (default, Jun  6 2023, 20:10:10) 
[GCC 9.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
root@mail:~/mlmmjadmin-3.1.9/tools#

```

Is there someway to uninstall everything python and reinstall the latest and greatest?

Everything that I am trying seems to be making it worse, LOL

Regards

---

### Post by guiverc on 2024-02-04
> **Heeter said:**
> Hi all,

Tried upgrading the python from 2.7 to 3.7 on my mailserver. This is on Ubuntu20LTS

I think that I botched it


Ubuntu 20.04 LTS did not install with Python2; it was already EOL (see  [https://www.python.org/doc/sunset-python-2/](https://www.python.org/doc/sunset-python-2/)) and thus not included by  default on Ubuntu 19.10 & later releases.

If your system included python2, it was added, or your system had it marked as *manually installed* from a prior release & you *release-upgraded* to 20.04; as otherwise it was not there.

Python3 is included by default for all Ubuntu releases, and was 3.8 on a default Ubuntu 20.04 LTS install

So your original details make no sense to me.  You upgraded something *that wasn't there*, and possibly **downgraded **to an earlier version the default python3; where downgrading python3 version will cause problems for the Ubuntu tools that rely on python3 (*which can includes parts of package management*).

The following is what is included on the [Ubuntu 20.04.6 Desktop ISO]("https://releases.ubuntu.com/20.04/ubuntu-20.04.6-desktop-amd64.manifest")

```

libpython3.8:amd64    3.8.10-0ubuntu1~20.04.6
libpython3.8-minimal:amd64    3.8.10-0ubuntu1~20.04.6
libpython3.8-stdlib:amd64    3.8.10-0ubuntu1~20.04.6

python3    3.8.2-0ubuntu2
python3-apport    2.20.11-0ubuntu27.25
python3-apt    2.0.1ubuntu0.20.04.1
python3-aptdaemon    1.1.1+bzr982-0ubuntu32.3
python3-aptdaemon.gtk3widgets    1.1.1+bzr982-0ubuntu32.3

python3.8	3.8.10-0ubuntu1~20.04.6
python3.8-minimal	3.8.10-0ubuntu1~20.04.6

``` 
ie. python3 at 3.8  (*which should not be changed, at least as default; you can include other python3 versions - but do not make them the default*)

---

### Post by Heeter on 2024-02-04
Hi

Yes it was a release upgrade from 18lts to 20lts, that gas completed a few days ago.

Was continuing with upgrades to the mail server components like postfix, dovecot, mysql, etc

This Python was 2.7 before I did the release upgrade

Managed to update all the other components of the server, this one component is left to update, but having this Python issue

---

