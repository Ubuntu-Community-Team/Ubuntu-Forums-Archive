---
title: "Likewise, Active Directory groups, and sudoers"
date: 2008-04-25
forum: Server Platforms
---

### Post by cebesius on 2008-04-25
I have a UnixAdmins group on my Active Directory domain, and joined my Hardy Heron server to AD using Likewise using [these instructions]("http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/").  Here is the last line of my /etc/sudoers file:

```
%UnixAdmins ALL=(ALL) ALL
```

Here is [a screenshot]("http://img125.imageshack.us/img125/7771/likewiseem0.png") of what happens when I log in as a member of UnixAdmins AD group and try to use sudo.

Have I missed something?

Many thanks!

---

### Post by dendrobates on 2008-04-27
when logged in as the user, do the following command to list the groups you belong to:

*id*

---

### Post by cebesius on 2008-04-27
> **dendrobates said:**
> when logged in as the user, do the following command to list the groups you belong to:

```
MORRISVILLE\cbw@lisa:~$ id
(trimmed other group memberships before posting to forum)
82324846(MORRISVILLE\unixadmins)
```

I added the below to my /etc/sudoers file:
```
%MORRISVILLE\unixadmins ALL=(ALL) ALL
```

Unfortunately this did not work, so I did some more searching.  Turns out I need to properly escape the backslash character in order for it to work.  I made the change, and the below setting made it work:
```
%MORRISVILLE\\unixadmins ALL=(ALL) ALL
```

Thanks!

---

### Post by bharathvn on 2012-05-04
Hi,

Am trying to accompany same, but seems to be not working.

I have joined Ubuntu 12.0 to Windows 2008 AD using likewise-open, am able to query using lw-find as mentioned below

/usr/bin$ lw-find-user-by-name AB\\rajesh
User info (Level-0):
====================
Name:              AB\\rajesh
SID:               S-1-5-21-1757981266-1606980848-1957994488-14886
Uid:               1236285990
Gid:               1236271617
Gecos:             Rajesh
Shell:             /bin/bash
Home dir:          /home/likewise-open/AB/Rajesh
Logon restriction: NO


Here is my Sudoer file

# User privilege specification
root    ALL=(ALL:ALL) ALL
%AB\\Rajesh ALL=(ALL:ALL) ALL

When i tried to make any installation i get error as user is not in sudoer list

/usr/bin$ sudo apt-get install systat
[sudo] password for AB\Rajesh: 
AB\Rajesh is not in the sudoers file.  This incident will be reported

Likewise-open version : 6.1.0.406-0ubuntu3

Any help will be appreciated.


Thank You
:Bharathvn:

---

