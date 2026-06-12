---
title: "User account that I did not create"
date: 2014-06-12
forum: Security
---

### Post by aaron48 on 2014-06-12
Hello. I am a bit confused because I have a user account showing up that I did not add. The user is named postgres which I know is a type of database but I don't remember even installing it let alone having it make a user account. It is showing up on the login screen and when I click the gear icon in the top right corner it shows the user postgres with a check mark on it. Is this normal? I looked in the /var/log/auth.log and this is one thing I found:

Jun  9 12:55:01 aaron useradd[25052]: new group: name=postgres, GID=1001
Jun  9 12:55:01 aaron useradd[25052]: new user: name=postgres, UID=1001, GID=1001, home=/home/postgres, shell=
Jun  9 12:55:03 aaron su[25060]: Successful su for postgres by root
Jun  9 12:55:03 aaron su[25060]: + ??? root:postgres
Jun  9 12:55:03 aaron su[25060]: pam_unix(su:session): session opened for user postgres by (uid=0)
Jun  9 12:55:36 aaron su[25060]: pam_unix(su:session): session closed for user postgres
Jun  9 12:55:36 aaron su[25167]: Successful su for postgres by root
Jun  9 12:55:36 aaron su[25167]: + ??? root:postgres
Jun  9 12:55:36 aaron su[25167]: pam_unix(su:session): session opened for user postgres by (uid=0)
Jun  9 12:55:37 aaron su[25167]: pam_unix(su:session): session closed for user postgres
Jun  9 12:55:38 aaron su[25182]: Successful su for postgres by root
Jun  9 12:55:38 aaron su[25182]: + ??? root:postgres
Jun  9 12:55:38 aaron su[25182]: pam_unix(su:session): session opened for user postgres by (uid=0)
Jun  9 12:55:38 aaron su[25182]: pam_unix(su:session): session closed for user postgres
Jun  9 12:55:38 aaron su[25186]: Successful su for postgres by root
Jun  9 12:55:38 aaron su[25186]: + ??? root:postgres
Jun  9 12:55:38 aaron su[25186]: pam_unix(su:session): session opened for user postgres by (uid=0)
Jun  9 12:55:39 aaron su[25186]: pam_unix(su:session): session closed for user postgres
Jun  9 12:55:40 aaron su[25189]: Successful su for postgres by root
Jun  9 12:55:40 aaron su[25189]: + ??? root:postgres
Jun  9 12:55:40 aaron su[25189]: pam_unix(su:session): session opened for user postgres by (uid=0)
Jun  9 12:55:41 aaron su[25189]: pam_unix(su:session): session closed for user postgres
Jun  9 12:55:48 aaron su[25246]: Successful su for daemon by root
Jun  9 12:55:48 aaron su[25246]: + ??? root:daemon

I may be a bit paranoid because I recently switched from Windows to Linux (Ubuntu 14.04). I am also pretty new to linux.

---

### Post by sudodus on 2014-06-12
Many users are created as part of a linux system. You find them in the file **/etc/group**

---

### Post by aaron48 on 2014-06-12
Oh ok, so it seems normal? I checked that file and it was listed as this:

postgres: x :1001: (minus the space between x)

---

### Post by sudodus on 2014-06-12
I think the user ID belongs to the database program system and it is better to use a separate user than to use root (more secure). Can you guess which application program that is using postgres? (It is *not* part of my desktop system.)

---

### Post by bab1 on 2014-06-12
> **aaron48 said:**
> Hello. I am a bit confused because I have a user account showing up that I did not add. The user is named postgres which I know is a type of database but I don't remember even installing it let alone having it make a user account. It is showing up on the login screen and when I click the gear icon in the top right corner it shows the user postgres with a check mark on it. Is this normal? I looked in the /var/log/auth.log and this is one thing I found:

Jun  9 12:55:01 aaron useradd[25052]: new group: name=postgres, GID=1001
Jun  9 12:55:01 aaron useradd[25052]: new user: name=postgres, UID=1001, GID=1001, home=/home/postgres, shell=
Jun  9 12:55:03 aaron su[25060]: Successful su for postgres by root
Jun  9 12:55:03 aaron su[25060]: + ??? root:postgres
Jun  9 12:55:03 aaron su[25060]: pam_unix(su:session): session opened for user postgres by (uid=0)
Jun  9 12:55:36 aaron su[25060]: pam_unix(su:session): session closed for user postgres
Jun  9 12:55:36 aaron su[25167]: Successful su for postgres by root
Jun  9 12:55:36 aaron su[25167]: + ??? root:postgres
Jun  9 12:55:36 aaron su[25167]: pam_unix(su:session): session opened for user postgres by (uid=0)
Jun  9 12:55:37 aaron su[25167]: pam_unix(su:session): session closed for user postgres
Jun  9 12:55:38 aaron su[25182]: Successful su for postgres by root
Jun  9 12:55:38 aaron su[25182]: + ??? root:postgres
Jun  9 12:55:38 aaron su[25182]: pam_unix(su:session): session opened for user postgres by (uid=0)
Jun  9 12:55:38 aaron su[25182]: pam_unix(su:session): session closed for user postgres
Jun  9 12:55:38 aaron su[25186]: Successful su for postgres by root
Jun  9 12:55:38 aaron su[25186]: + ??? root:postgres
Jun  9 12:55:38 aaron su[25186]: pam_unix(su:session): session opened for user postgres by (uid=0)
Jun  9 12:55:39 aaron su[25186]: pam_unix(su:session): session closed for user postgres
Jun  9 12:55:40 aaron su[25189]: Successful su for postgres by root
Jun  9 12:55:40 aaron su[25189]: + ??? root:postgres
Jun  9 12:55:40 aaron su[25189]: pam_unix(su:session): session opened for user postgres by (uid=0)
Jun  9 12:55:41 aaron su[25189]: pam_unix(su:session): session closed for user postgres
Jun  9 12:55:48 aaron su[25246]: Successful su for daemon by root
Jun  9 12:55:48 aaron su[25246]: + ??? root:daemon

I may be a bit paranoid because I recently switched from Windows to Linux (Ubuntu 14.04). I am also pretty new to linux.

This looks like you installed an email server.  But it doesn't look like you installed it from the repos.  Normally system users have a UID/GID below 500.  In Ubuntu all mortal users (accounts for humans) are 1000 or greater.  The user postgres should not have a UID of 1001.

If you want to see all the users use```
getent passwd
```...for groups use```
getent group
```

---

### Post by aaron48 on 2014-06-12
I have recently started learning pentesting, so I did install metasploit. Do you think that can be it? I believe that uses postgres. It does make me worried about that the account is set for 1001 though. Is there a chance my computer was hacked? Should I pretty much just reinstall ubuntu? I did do a scan with clamav and that came back clean

---

### Post by bab1 on 2014-06-12
> **aaron48 said:**
> I have recently started learning pentesting, so I did install metasploit. Do you think that can be it? I believe that uses postgres. It does make me worried about that the account is set for 1001 though. Is there a chance my computer was hacked? Should I pretty much just reinstall ubuntu? I did do a scan with clamav and that came back clean

I would say that this is a non-standard .deb install.  The packager was not very careful about following the Debian packaging conventions.  Who knows what else was installed.  Scanning for a virus won't help you.  I wouldn't keep that machine on my network.  I might however explore how and what went on before I wiped it clean and reinstalled the OS.

If you use Ubuntu you should be careful to always use either Ubuntu or Debian guides and repositories.  At the least you should know what it is your installing and how it works before you put it on a machine that is in your network.  The fact that a system user has been given a mortal user account number is just an indicator that something is not right.  My guess is lazy packaging of Metasploit.

Google the terms: *metasploit  debian postgre * to see  how this should be done with Debian style OS.

---

### Post by QIII on 2014-06-12
Thread closed.

Discussions about pen testing, etc, are not allowed on the Forums.

---

