---
title: "ftp server hiding files"
date: 2012-10-14
forum: Server Platforms
---

### Post by bigmonmulgrew on 2012-10-14
Hi all
I've been following the guide here
[https://help.ubuntu.com/12.04/serverguide/ftp-server.html](https://help.ubuntu.com/12.04/serverguide/ftp-server.html)
and I'm at the point of securing the server. I was under the impression that the security settings hide the rest of the file system from a user.

Lets say the user is user1. he has a home directory /home/user1

I've enabled the chroot options as described in the guide but the user is still able to see, and download the entire filesystem.

Is there a step I've missed or some permissions I need to set.

This is on a fresh install of ubuntu server 12.04 set up (during install) as OpenSSH, and LAMP.

How can I make it so the user sees their home directory and nothing else

---

### Post by bigmonmulgrew on 2012-10-14
perhaps this should better be posted in the server section, mods feel free to move it.

---

### Post by CharlesA on 2012-10-14
The chroot should have made the users confined to their home directories.

Personally, I just use sftp instead of plain ftp as it is more secure and easier to manage (imo, of course).

---

### Post by bigmonmulgrew on 2012-10-14
> **CharlesA said:**
> The chroot should have made the users confined to their home directories.

Personally, I just use sftp instead of plain ftp as it is more secure and easier to manage (imo, of course).

I'm happy to use sftp, how do I configure that to only show the user the correct files

---

### Post by CharlesA on 2012-10-14
The best you can do is confine each user their their home directories so they cannot access another user's files. I do not believe there is a way to filter that list.

See here:

[http://www.techrepublic.com/blog/opensource/chroot-users-with-openssh-an-easier-way-to-confine-users-to-their-home-directories/229](http://www.techrepublic.com/blog/opensource/chroot-users-with-openssh-an-easier-way-to-confine-users-to-their-home-directories/229)

---

### Post by bigmonmulgrew on 2012-10-14
I'd been googling and found this
[http://www.ericstockwell.com/?p=54](http://www.ericstockwell.com/?p=54)
with the exception of setting the home chroot directory to %h because I moved it I followed it exactly.

Yet I was still able to see the entire file system.
I'm using fireFTP and I had the idea to clear my browser history as FireFTP caches files.
As soon as I connected after clearing the browser cache it displayed fine.
I wonder if this was why I was still able to see the entire directory structure using ftps.
I'm going to test this and then post my results

---

### Post by bigmonmulgrew on 2012-10-14
OK following the official vsftpd method described in the ubuntu docs here
[https://help.ubuntu.com/12.04/serverguide/ftp-server.html](https://help.ubuntu.com/12.04/serverguide/ftp-server.html)
does NOT work.

I'm more than happy using the sftp jail method described here though

I followed the guide here
[http://www.ericstockwell.com/?p=54](http://www.ericstockwell.com/?p=54)

This worked perfectly once I cleared FireFTP's cache. Refreshing the browser in FireFTP does NOT work. I had to clear my entire browser history although I imagine disabling directory caching would do the job too.

---

### Post by bigmonmulgrew on 2012-10-14
I'm marking this thread as solved as it has accomplished what I set out to achieve however if anyone has any input on why the vsftpd method did not work please post. I have a vpc setup for testing so I can experiment.

---

