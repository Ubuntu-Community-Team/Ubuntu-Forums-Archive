---
title: "sudo su is behaving funny"
date: 2008-08-07
forum: Security
---

### Post by violagirl23 on 2008-08-07
I recently tried enabling the root account (by doing sudo passwd root) because I was so used to it on Arch. However, it woudn't let me log in anyway and kept saying the account was expired, so I decided to disable it again after all. The only problem is now when ever I do sudo su I get the following message:
Your account has expired; please contact your system administrator
su: User account has expired
(Ignored)
It still asks for my password and goes to root, but I would like to figure out how to get rid of this message. Also, the weirdest thing? If I type sudo sudo su, it gives me root access without asking for a password!!!!!!!!!!!!!!!!!!!!!!!! Is this normal? I hope not... otherwise that could be a MAJOR security breach.

Edit: I'm finding that applies for any command. If I type sudo sudo and then any command, it does it without asking for a password and just automatically gives the root access. O______O

---

### Post by tamoneya on 2008-08-07
i dont know anything about the "account expired" stuff but Im pretty certain that is not an exploit.  Inside the same terminal session once you use sudo once and enter the password you dont have to enter the password in again for following sudos for a certain amount of time.

---

### Post by tuxxy on 2008-08-07
> Also, the weirdest thing? If I type sudo sudo su, it gives me root access without asking for a password!!!!!!!!!!!!!!!!!!!!!!!! Is this normal? I hope not... otherwise that could be a MAJOR security breach

Once an attacker had local access to the machine though it would only be a matter of time before they got in

As for the sudo problem you should read root/sudo guide

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by tamoneya on 2008-08-07
> **tuxxy said:**
> Once an attacker had local access to the machine though it would only be a matter of time before they got in

As for the sudo problem you should read root/sudo guide

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

the command sudo su has nothing to do with remote or local access.  It could be run from either.

---

### Post by violagirl23 on 2008-08-07
Oh, I got it! Via chage I discovered that the account expiration date was set to 1970-01-02. I compared it to my regular user and saw that to make it never I had to change the date to 1969-12-31. Am I the only one who finds that bizarre? Anyhow, now the root account works and is not expired.

Oh, by the way, I am noticing there is a file that I, as root, do not have permission to access at all. This boggles me, as I thought root was the equivalent of god and could get into anything. The file (actually, the directory) is in the home directory of my regular user account and is called .gvfs. I can't do anything as root with it without getting a Permisison Denied error. I can't even view the permissions on it as root:
```
d?????????  ? ?      ?          ?                ? .gvfs
```
If I do it actually as that user, the correct permissions pop up but don't look like anything that should inhibit root:
```
dr-x------  2 megini megini     0 2008-08-07 17:26 .gvfs
```
What exactly is this folder that is so good not even root can get at it? I don't understand why I can't see it as root. Can anyone tell me?

---

### Post by tamoneya on 2008-08-07
it appears to me as if megini can read(and execute) it.

---

### Post by violagirl23 on 2008-08-07
Yes, but I thought root was like god and should be able to get in the directory regardless. To have root denied access boggles me. That's what I don't get. I went in as megini to find it to be an empty directory. All I want to know is why root can't read it (or even change its permissions so it can)

---

### Post by tamoneya on 2008-08-07
can you chown?```
chown root:root /directory/file
```

---

### Post by violagirl23 on 2008-08-08
```
root@Squeesama:~# chown root:root /home/megini/.gvfs 
chown: cannot access `/home/megini/.gvfs': Permission denied
```
So... that's a no. O-o Is this a common file to have lying around? (~/.gvfs) And does it always behave this way?

---

### Post by cariboo on 2008-08-08
For .gvfs that is normal. Gnome Virtual File System from wikipedia:

> It provides an abstraction layer for the reading, writing and execution of files. It was primarily used by the Nautilus file manager and other GNOME applications before GNOME 2.22.

A cause of confusion is the fact that the file system abstraction used by the Linux kernel is also called the virtual file system (VFS) layer. This is however at a lower level.

A replacement called GVFS, is currently in development which also allows partitions to be mounted through FUSE.

As of April 2008, the GNOME project has declared GnomeVFS deprecated in favour of GVFS and GIO, requesting that developers not use it in new applications

Jim

---

### Post by hyper_ch on 2008-08-08
howtos regarding to enabling root account is against forum policies. See the stick on that issue.

---

### Post by violagirl23 on 2008-08-08
Actually, my question was more entailing why sudo su was behaving oddly, not enabling the root account itself. And the issue I am having with .gvfs happens with su AND sudo, so that is also not an issue with having the root account enabled. In my main distro (Arch Linux) I have a /home/megini/.gvfs as well. But the difference is that I seem able to access it with su/sudo, unlike in Ubuntu. So that is why I am so puzzled as to why even root (or sudo if you like) does not have access.

---

