---
title: "[SOLVED] How to set up VSFTPD"
date: 2008-12-04
forum: Server Platforms
---

### Post by nickski on 2008-12-04
Okay, i want to set up and ftp server with a spare computer that i have.  I have installed vsftpd and it runs.  I have port forwarded my router, and i can access the server from a web browser.  What i really want to do now is put files on the server from the actual computer.  I see there is a ftp folder in the Home directory when i log in as root, but if i put something in that folder, nothing happens when i connect to the server, it is the same.  I just really want to know where to put files so i can access them from outside my network.  I also would like to know how to grant access to people with a user name and password, and allow these users to upload files from their own computer.  I have looked at a lot of tutorials, but nothing seems to work.  Any help/tips would be greatly appreciated.:o

Update:  I realize that i am not actually logging on the the server.  I thought i was logging on by typing ftp:Ip address, but when my server is turned off, it does the same thing.  Now i really need some help :(

---

### Post by lykwydchykyn on 2008-12-05
By default, vsftpd will login users to their respective home directories.  So the simplest way is to simply create users on the system.  If you're exposing this to the internet, I would make sure you are implementing some good security on the system -- i.e. password policies and turning on the chroot option in vsftpd.  Personally I'd probably just use ssh and make users install winscp or some other sftp client.  

As for your bigger issue, are you typing ftp:ip_address or [ftp://ip_address?](ftp://ip_address?)  The slashes are necessary, typically.  What browser are you using?

---

### Post by nickski on 2008-12-05
Firefox, and when you type in ftp:ipaddress, it automatically puts the slashes in there.  I want to be able to know how to give usernames and passwords, and i do not mind handing out a client to people in order to connect.  What i am saying is i cannot figure out how to do all of this, and i've looked on my tutorials including [http://www.wikihow.com/Setup-vsftpd-FTP-on-Ubuntu-Linux](http://www.wikihow.com/Setup-vsftpd-FTP-on-Ubuntu-Linux) and [https://help.ubuntu.com/7.10/server/C/ftp-server.html](https://help.ubuntu.com/7.10/server/C/ftp-server.html) and it really isn't explaining anything that well.  It doesn't give instructions on how to log on to it over the internet, how to port forward your rounter (but i already know how to do that), or how to make usernames and passwords.  They just throw a list of sudo commands at you and expect them to work without knowing truly what they will do for you.  I also want everyone to use the same directory, not just their own directory.  I want all the files to be shown to everyone who owns a user name.

---

### Post by lykwydchykyn on 2008-12-05
Well, here's my advice; it'll be easier and much more secure as well:

- Uninstall vsftpd.
- Install openssh-server (if it's not already installed).
- create login accounts on your server for everyone who wants to log in.  Easiest way is the adduser command.
- forward port 22 on your router to your server.
- have your clients install winscp (for people using windows, of course; in linux you can use all kinds of things).

That will pretty much give you what you want, and it will all be encrypted.

As for tutorials and howtos, yeah a lot of them just give you the simple install commands and leave you hanging.  On the flip side, a lot of things like creating system users and forwarding ports don't need to be reiterated in every how to.  It'd get a bit pedantic if every network-service-setup tutorial included full instructions on port forwarding, or every setup that required editing config files contained a full vim tutorial.

---

### Post by nickski on 2008-12-05
Okay, thank you very much.  That was super easy to set up, and i had the server up and running in no time :D.  Just one last question:  Is there any way i can hide files from people, like important system files that are displayed when i tried using winscp in windows?  I would hate for any important files to get accidently deleted.  I look at  permissions on the server, and tried to change some, but nothing really happened.  Thanks alot, you have been a huge help...

---

### Post by lykwydchykyn on 2008-12-05
Just make sure they are not part of the admin group, and they will not be able to change anything outside of their own home directories.  I don't think you can sudo in sftp anyway, which would be required to edit any of these files if they were in the admin group.

If you want to make it so they cannot leave their home directory, you want to do what's called a chroot (short for 'change root').  Check out this post for how to do that:

[http://ubuntuforums.org/showthread.php?t=451510](http://ubuntuforums.org/showthread.php?t=451510)

It's a bit more complicated, but not a bad idea if you don't necesarrily trust the people who are logging in.  SSH is quite powerful after all, and you can do a lot when you have ssh access to a system.  (though for anything truly dangerous and destructive you need root access).

---

### Post by nickski on 2008-12-05
Okay, so if i give everyone a username, and give them no priviliages, is there anyway i can let them access some files in admin, such as "documents" on the admin acount?  I want everyone to go to the same place basically with diff usernames.

---

### Post by lykwydchykyn on 2008-12-05
Well, create a directory, say "/home/shared", and give it universal read/write permissions.  That, of course, rules out chrooting everyone to their own home directory.

If you're only doing sftp and not actually having anyone log in to a shell or GUI, the really easy thing to do would be to assign everyone's home directory to the shared directory.  This shouldn't cause any issues, though it's a bit hacky.

You might just want to read up a bit on user/permissions management in general; I think you'll be able to answer most of your own questions about this.  Here are some good links:

[http://www.debian.org/doc/manuals/system-administrator/ch-sysadmin-users.html](http://www.debian.org/doc/manuals/system-administrator/ch-sysadmin-users.html)
[https://help.ubuntu.com/8.04/serverguide/C/user-management.html](https://help.ubuntu.com/8.04/serverguide/C/user-management.html)
[http://tldp.org/LDP/sag/html/managing-users.html](http://tldp.org/LDP/sag/html/managing-users.html)

---

### Post by nickski on 2008-12-06
thanks a lot, you have been a big help

---

