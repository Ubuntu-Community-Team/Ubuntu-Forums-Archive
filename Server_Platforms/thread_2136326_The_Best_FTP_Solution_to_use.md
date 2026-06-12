---
title: "The Best FTP Solution to use?"
date: 2013-04-17
forum: Server Platforms
---

### Post by ally_uk on 2013-04-17
Hello Everyone I have been dabbling with Ubuntu and now wish to dabble further by getting some form of FTP up and running.
I have a partition /data of 500gig in size.

**What I am trying to achieve**

OK so from the client machines I want to be able to FTP to the server and download / upload files to the /data partition

Now before you mention SAMBA and share out the data share I will be crossing the SAMBA bridge at a later date.

I want some form of authentication in place i.e the ability to create users and restrict others that can access the FTP.

Implement any other security options which are best suited.

Your thoughts on how you would approach the above scenario if you have links to tutorials or guides post them up, So we can help out any other noobs :)

---

### Post by Lars Noodén on 2013-04-17
If security is anywhere on your list and you would like to allow uploads, then plain FTP is off your list.  You can use SFTP instead.  It's just as easy or easier to use and it's easy to set up.  If you have OpenSSH server running, then you already have a working SFTP server.  You can connect to it with sftp, Nautilus, or FileZilla.  If you want to tighten things further you could require log in using [keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) and/or restrict users or a group to one directory, such as /data  That kind of restriction is easy to do with the built-in SFTP server.

---

### Post by ally_uk on 2013-04-22
Is it easy to setup do you have any documentation? :)

---

### Post by Lars Noodén on 2013-04-22
SFTP is easy to set up.  All you need on the server side is to install the package openssh-server and it will run the SFTP server for you automatically.

Then to connect to the server you can use the built-in program sftp.  Or you can use something like Nautilus.  If you use Nautilus or Thunar, you can press ctrl-L and then enter the URI for your server:

sftp://ally_uk@xx.yy.zz.aa/

Where xx.yy.zz.aa is replaced by the name or address of your server.  It will ask you for your password and then after that, the remote folders and files will show up just as if they were local.  The same goes for PCManFM, which is the default for Lubuntu.  Press ctrl-L and away you go.

---

### Post by Lars Noodén on 2013-04-22
It's also possible to [restrict groups of SFTP users to specific directories](https://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#Chrooted_SFTP-only_Accounts) using ChrootDirectory and ForceCommand.

The one thing to watch out for is that the chroot target must be owned by root and not writable by anyone else.  So if it is a user home directory, make some subdirectories for the user to work in that they own because their actual home directory must be owned by root.

---

