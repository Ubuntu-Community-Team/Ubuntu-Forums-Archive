---
title: "Mounting SMB shares"
date: 2006-03-11
forum: The Cafe
---

### Post by hdensley on 2006-03-11
OK, I need to mount an external network drive.  I can find it fine via konqueor (it's SMB), but via the regular file system, I cannot.

how does one add the network drive (or folders within the network frive) to the regular file system?

thanks

---

### Post by cowlip on 2006-03-11
HI I would install smb4k and mount it using htat program

---

### Post by hdensley on 2006-03-11
[QUOTE=cowlip]HI I would install smb4k and mount it using htat program[/QUOTE]

 I just installed this.  But I'm getting an error within the smb4k - that it can't find smbmnt when I try to mount the shares

Any other ideas?

There's no smbmnt packages in package manager

---

### Post by SadaraX on 2006-04-16
[QUOTE=hdensley]I just installed this.  But I'm getting an error within the smb4k - that it can't find smbmnt when I try to mount the shares

Any other ideas?

There's no smbmnt packages in package manager[/QUOTE]

I have not got my smb4k working properly yet, but I know one problem that you are having. You need to install the package called "samba" that contains the smbmnt or smbumount

---

### Post by SadaraX on 2006-04-18
After I installed the samba package here is how you setup the smb4k program. Using sudo, run these commands:

chmod +s /usr/bin/smbmnt
chmod 777 /usr/bin/smbumount
chmod +s /usr/bin/smbumount
smbpasswd -a USERNAME

Be sure to add your own username and setup a password for it. You should be able to mount and unmount shares

---

### Post by nolan- on 2006-05-27
[QUOTE=SadaraX]After I installed the samba package here is how you setup the smb4k program. Using sudo, run these commands:

chmod +s /usr/bin/smbmnt
chmod 777 /usr/bin/smbumount
chmod +s /usr/bin/smbumount
smbpasswd -a USERNAME

Be sure to add your own username and setup a password for it. You should be able to mount and unmount shares[/QUOTE]


Excellent! 
I'm a Samba noob and that worked a treat :D 
Thanks!

NoL

---

### Post by SadaraX on 2006-05-27
I found this off of freshmeat.net a while ago. This is really useful for machines that do not have the nice right-click samba sharing ability that KDE gives you. This program makes creating samba shares very easy and streamlined. Here is the link: [http://www.linux-fuer-alle.de/mr/taj/](http://www.linux-fuer-alle.de/mr/taj/)

Mostly, there are two parts to the program, taju (for users) and taja (for admins). Its about 4 simple steps to make samba on your comptuer ready for this program (its very simple).

1) Compile the program from the source, which should work essentially anywhere. Its written in ANSI C, so its about as universal as you get.
2) Make sure the user has been added to the samba user list with the 'smbpasswd -a USER', and set whatever password you want. I don't know if samba stores your passwords in plain text somewhere or not, so be careful.
3) Add one line to your /etc/samba/smb.conf file, anywhere in the section [global], add 'include = /etc/taj/samba.inc.conf'.
4) Then set the user access, example 'taja --add user --name USER --access=owner --writeable', that's assuming you want the user to be able to have write access to any of his shares. See that website documentation on advanced options, but this works for most users.

You are done! An example of creating a share: user@host[/home/user/]$  taju --add --name MYTHTV_SHARES --path /myth/tv --writeable

---

### Post by superdexter on 2006-06-09
Confirmed.  I was having the same issue as discribed above and with the commands from SadaraX all is working exactly as it should.

Kudo's SandraX.

---

