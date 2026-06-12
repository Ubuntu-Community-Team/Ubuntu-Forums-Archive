---
title: "virtual box fail to start"
date: 2008-01-02
forum: Virtualisation
---

### Post by frenchsquared on 2008-01-02
the virtualbox kernal driver is not accessible to current user. Make sure that the user has write permisions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to log out for the changes to take affect

what does that mean?

running ubuntu 7.10
installing windows

---

### Post by Fixman on 2008-01-02
Have you gksudo'ed it?

---

### Post by frenchsquared on 2008-01-02
no, and im not sure how
I tried gksudo gedit /dev/vboxdrv
but it says it is not a regular file?

so i must have the wrong code or something

---

### Post by p_quarles on 2008-01-02
```
sudo useradd *username* vboxusers
```
You'll then need to log out prior to running Virtualbox again.

---

### Post by frenchsquared on 2008-01-02
WARNING: You are not a member of the "vboxusers" group.  Please add yourself
         to this group before starting VirtualBox.

         You will not be able to start VMs until this problem is fixed.
gordon@Gateway:~$ sudo useradd gordon vboxusers
Usage: useradd [options] LOGIN

Options:
  -b, --base-dir BASE_DIR       base directory for the new user account
                                home directory
  -c, --comment COMMENT         set the GECOS field for the new user account
  -d, --home-dir HOME_DIR       home directory for the new user account
  -D, --defaults                print or save modified default useradd
                                configuration
  -e, --expiredate EXPIRE_DATE  set account expiration date to EXPIRE_DATE
  -f, --inactive INACTIVE       set password inactive after expiration
                                to INACTIVE
  -g, --gid GROUP               force use GROUP for the new user account
  -G, --groups GROUPS           list of supplementary groups for the new
                                user account
  -h, --help                    display this help message and exit
  -k, --skel SKEL_DIR           specify an alternative skel directory
  -K, --key KEY=VALUE           overrides /etc/login.defs defaults
  -m, --create-home             create home directory for the new user
                                account
  -o, --non-unique              allow create user with duplicate
                                (non-unique) UID
  -p, --password PASSWORD       use encrypted password for the new user
                                account
  -r, --system                  create a system account
  -s, --shell SHELL             the login shell for the new user account
  -u, --uid UID                 force use the UID for the new user account

gordon@Gateway:~$

need something else
sorry Im a complete newby

---

### Post by p_quarles on 2008-01-02
D'oh. Sorry, I meant "adduser":
```
sudo adduser gordon vboxusers
```

---

### Post by frenchsquared on 2008-01-02
thank you

so will Virtual boxrun 0sx 10.5

---

### Post by p_quarles on 2008-01-02
> **frenchsquared said:**
> thank you

so will Virtual boxrun 0sx 10.5
No. It's also a violation of the OS X license to run it on anything but Apple hardware.

---

### Post by hundred1906 on 2009-01-28
> **p_quarles said:**
> ```
sudo useradd *username* vboxusers
```
You'll then need to log out prior to running Virtualbox again.

I have the same problem. I have added my username to the vboxusers group and checked using "groups" that it is present and recognised. The error message I get is as follows below. What is meant by the specific guidance regarding write permissions for /dev/vboxdrv?


"The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}"

---

