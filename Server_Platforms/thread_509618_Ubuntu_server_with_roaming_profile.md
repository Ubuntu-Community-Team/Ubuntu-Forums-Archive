---
title: "Ubuntu server with roaming profile"
date: 2007-07-25
forum: Server Platforms
---

### Post by golfarn on 2007-07-25
Hi.

I'm building a small testing network with ubuntu.

I want to set up the user accounts on the server and have the client computers confirm the user identity from the server and as a roaming profile. So that the users home-dir is stored on the server, what I want to accomplice is that the user is able to use different computers and still have his/hers home dir.

I all sow like to be able to show/hide the clients local devices like local hard disk.

How do I do this? Is there any good guides out there?

Thankful for your answers.

Kind Regards!

---

### Post by meatpan on 2007-07-25
It sounds like a network filesystem might be what you are looking for.  Take a look at this nfs howto and see if you can use nfs as a solution:  [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by koenn on 2007-07-26
> **golfarn said:**
> ...  that the users home-dir is stored on the server, what I want to accomplice is that the user is able to use different computers and still have his/hers home dir.

I all sow like to be able to show/hide the clients local devices like local hard disk.

you're using Windows speak  ;)
"roaming profiles" is irrelevant on Linux, because all user-specific settings are in the user home directory. So, by having the homes on a server, make them available over an network (NFS as previous poster suggests, but also possible with Samba, or even ftp, ..), then mount them in the local file system, your users can roam and always have the same home/profile. You will have some user acccount /passwd and access rights issues to figure out - there's no default "Everyone Full Controll"

because the remote directories are mounted locally, they appear as eg /home/johnnybgoode. There's no way johnny can know what drive that directory is on, not only because it's on another server, but also because the ubix/linux file system is independent of the underlying disks. There's no drive letters (C:\, D:\, ... ) in the paths - so what is it you need to hide then ? 
Besides that, users have no write access outside their homes. They do have read and execute rights on some system files, to allow them to use the system (eg run a program).

---

### Post by golfarn on 2007-07-27
I'm use to the windows environment that is why I "speak windows" but is there any easy guide that I can use to accomplice this?

---

### Post by koenn on 2007-07-27
That link to the NFS Guide is a good starting point - try that to get the feel of things. 
My comments were just elaboration on NFS, and to stear you towards a Linyx-way-of-thinking; just translating Windows-cocepts into linux tools will hinder you in the long run. 
Have  fun.

---

