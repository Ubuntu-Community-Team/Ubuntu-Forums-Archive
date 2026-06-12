---
title: "FTP server"
date: 2005-05-30
forum: Server Platforms
---

### Post by Krank on 2005-05-30
Hello.

I am currently trying to find and configure an FTP server. Problem is, I cannot seem to find one that can do what I want it to do.

The goal is to have a FTP server in which I can create virtual users. The virtual users should have access to one "private" directory (rwx), and one "public archive" ("r-x").

Ideally, they should be chrooted in some way, so that they cannot browse the rest of my system. They should ONLY see their private dir, and the public one.

The ideal solution allows for simple user and perhaps also group management - proFTPd, for instance, demands that I create virtual user configs manually and that I place actual mount points for each user, because symlinks won't work if the users are chrooted.


So does anyone have a FTP server to recommend?

---

### Post by Ubuntu_User on 2005-05-30
try out VSftpd for size

---

### Post by mythalethe on 2005-05-31
[QUOTE=Ubuntu_User]try out VSftpd for size[/QUOTE]
 Is VSftpd in synaptic?

---

### Post by Krank on 2005-05-31
Hmmm... Having checked the capabilities and how VS is configured, I have to say it feels a bit cumbersome.

I'm currently testing PureFTPd, which should be able to do what I want - but I cannot seem to make Virtual users work in it (they refuse to become authenticated, which is very weird. They are in the database, they _exist_ in the system - but something's wrong with their passwords or something...).

---

### Post by skela on 2005-06-12
I promise you'd find vsftpd much easier. Just make yer own config file called in /etc/ called vsftpd.conf   . Command : "man vsftpd.conf" and check out which options you want. It's easy as hell , even a noob like me got it working great :D

---

### Post by relix42 on 2005-06-13
Check the doc files for VSFTPd for example configurations.

I've used it quite a bit for virtual users and have found to to *very* fast and *very* secure.

Reply if you need more help with config files.

---

### Post by Krank on 2005-07-11
Well, I've now installed VSFTP - and I'm rather impressed. I haven't had the time to try everything I want my FTP server to be able to do yet, but I am still impressed. Thanks for the tip!

---

### Post by DreadHead on 2006-02-07
relix42: (or anyone else for that matter)

I have followed the guide at [ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.3/EXAMPLE/VIRTUAL_USERS/README](ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.3/EXAMPLE/VIRTUAL_USERS/README)
since I couldn't find db_load on my system. So after som research I found that I could apt-get install libdb3-util
and then I used db3_load instead of db_load and followed the guide.

When I try to connect I get:
```
dread@c-452972d5:/lib/security$ ftp localhost 10021
Connected to localhost.localdomain.
220 Welcome to Dread FTP service.
Name (localhost:dread): mx
331 Please specify the password.
Password:
530 Login incorrect.
Login failed.

```

Any idea of what I have done wrong?

---

### Post by dizzie on 2006-02-08
Checked for PAM issues?

---

### Post by DreadHead on 2006-02-08
How do I check for PAM issues? I'm totally new to GNU/Linux...

---

