---
title: "Ubuntu file server"
date: 2010-12-10
forum: Server Platforms
---

### Post by eldar on 2010-12-10
I am sure there is an answer for this already but I am quite a noob with linux in general and terms that may be used.
I want to set up a server for my network at home. This will be mainly a media server for home use. Used to house pics, music, and movies. 
My other computers are windows 7 professional(3).
Of course since this will be on a network, I would like security so my 3 computers can access but prevent outside users.

What would be the best way to do this? GUI if possible otherwise I can do terminal but I am super inexperienced at it.

---

### Post by MSPdwalt on 2010-12-11
Well,

If you're just planning on doing I file server all you really need to install is samba. (Microsoft file sharing) 

If it were me I would install Ubuntu server (really small footprint to maximize usable space for your files/media) and

```
sudo apt-get install swat
```It's the Samba Web Administration Tool, it should install all the dependencies for you (such as samba server, the client, ect, ect)

Then it allows you to create shares from a nice easy web interface.

---

### Post by HermanAB on 2010-12-11
If you want a GUI, install regular Ubuntu.  If you want pointy-clicky wizards as in Windows, install OpenSuse.

---

### Post by ingeva on 2010-12-11
> **MSPdwalt said:**
> If you're just planning on doing I file server all you really need to install is samba. (Microsoft file sharing)
I believe that Windows 7 now supports nfs.
It may not be as easy to set up, but since it a lot faster than samba it may be worth the try.
The setup for NFS4 on linux is described here:

[http://www.crazysquirrel.com/computing/debian/servers/setting-up-nfs4.jspx](http://www.crazysquirrel.com/computing/debian/servers/setting-up-nfs4.jspx)

I guess the setup is easier on the Windows side as long as you don't get problems,
because then you'll end up with trying to bite your tail. And even a dog can't do that, and they actually HAVE a tail. :)

---

### Post by eldar on 2010-12-13
Thanks for the repies. I will give these ideas a try and see if I can pull it off.

---

### Post by HermanAB on 2010-12-14
Howdy,

You can either install Samba on Linux, or install NFS clients on Windows.  NFS is two orders of magnitude simpler, since it only needs ONE line of configuration on each machine, while Samba needs a myriad.

[http://technet.microsoft.com/en-us/magazine/ee767578.aspx](http://technet.microsoft.com/en-us/magazine/ee767578.aspx)

[https://sagehacks.wordpress.com/2009/01/21/howto-mount-nfs-shares-under-windows-7/](https://sagehacks.wordpress.com/2009/01/21/howto-mount-nfs-shares-under-windows-7/)

---

### Post by eldar on 2010-12-23
OK so I have time to work on this and being just a home setup, I am going to do the nfs set up. However, when trying to type the commands, I get an error of syntax error near unexpected token `('
and this is even if I try to copy/paste it from the source.

Any ideas?

---

### Post by ingeva on 2010-12-24
> **eldar said:**
> OK so I have time to work on this and being just a home setup, I am going to do the nfs set up. However, when trying to type the commands, I get an error of syntax error near unexpected token `('
and this is even if I try to copy/paste it from the source.

Any ideas?It would be nice to know in which file that error occurs.
And you must distinguish between NFS and NFS4, which is probably the version you are using now, and is a bit more complicated to set up. The links you were given below are for Windows 7 and for the old NFS (version 2 I believe).

SAMBA is VERY easy to set up. Don't worry about the complexity of the configuration file; all you really need to do is to change the network name if it's different from WORKGROUP, and set up the shares at the end of the file. If you need to access other shares from Linux mu must enter them into you /etc/fstab file. This is quite well described in the help files.

After you have set up SAMBA and got that working, you can start NFS4, which is the default from 9.04 I believe. For checking out errors like the one you describe, use common logic, or post the file here.

Good luck and Merry Christmas!

---

### Post by eldar on 2010-12-24
My problem is just understanding what I need to type in terminal. I tried samba and I have not found the "complete terminal tard" instructions I need. Same with the 2 links for nfs that HermanAB posted.

---

### Post by ingeva on 2010-12-24
> **eldar said:**
> My problem is just understanding what I need to type in terminal. I tried samba and I have not found the "complete terminal tard" instructions I need. Same with the 2 links for nfs that HermanAB posted.

Send me a message at [http://inge.qreply.net](http://inge.qreply.net) so we can communicate directly, e-mail, skype or phone. Faster and easier.

---

### Post by 1v82TIn1 on 2010-12-26
The answer is FTP.

Try installing GADMIN-ProFTPd.
It is a GUI-based control for ProFTPd. You can configure users in it and secure each user with a password and define their directory.

It is much easier to set up than Samba or NFS.

Windows has support for FTP.

---

### Post by ingeva on 2010-12-26
> **Ryan Brothers said:**
> The answer is FTP.
Try installing GADMIN-ProFTPd.
It is a GUI-based control for ProFTPd. You can configure users in it and secure each user with a password and define their directory.
It is much easier to set up than Samba or NFS.
Windows has support for FTP.

This is by far the same thing. You can't open, read or write files over a regular ftp connection as if they were local. For that you'll have to mount the volume; in Windows as a disk with a drive letter, and in Linux a regular mounted filesystem.
There's a BIG difference between an ftp connection and a network connection.

---

### Post by eldar on 2010-12-30
Thanks for the offer. I will contact you when I am home again.
Do I have to set up both samba and nfs? I didnt think so but I have a better chance of being wrong than I do right.
How do I check to see what version of nfs I have? Running latest ubuntu.

---

### Post by ingeva on 2010-12-30
> **eldar said:**
> Thanks for the offer. I will contact you when I am home again.
Do I have to set up both samba and nfs? I didnt think so but I have a better chance of being wrong than I do right.
How do I check to see what version of nfs I have? Running latest ubuntu.
That's OK. Many are celebrating their holiday now! :)

No, you won't have to set up both. In fact, SAMBA alone may be sufficient
if you have both Windows and Linux computers on your network.

NFS is much faster, and is also supported by Windows 7, so if your Windows computer(s) have that, you shouldn't need Samba.

Samba runs "out of the box" so to speak, except for a few simple editions to set up the shares.

I'm running both on my computer, for two reasons:
1. I have not been able to reach the root directory on the other computer using NFS,
and I may need that from time to time.
2. I'm using Windows less than once a month but may still need access over the network.
3. I'm going to place the other computer at a remote location so physical access to it will be limited. I want to do as much as possible from the office.

If you are using Ubuntu 9.04 (I think) or later, you are using NFS4, so if you find instructions for setting NFS, make sure you are reading the right ones. :)

Here's a good help:
[http://www.crazysquirrel.com/computing/debian/servers/setting-up-nfs4.jspx](http://www.crazysquirrel.com/computing/debian/servers/setting-up-nfs4.jspx)

---

### Post by drave on 2010-12-30
only windows 7 ultimate has the nfs client. professional does not.

---

### Post by ingeva on 2010-12-30
> **drave said:**
> only windows 7 ultimate has the nfs client. professional does not.
I think that it's compatible anyway, but you may have to purchase it extra if you have one of the simpler versions.
(WHO WOULD? :) ) - and the reason I say that is that I have tried some of the "home" versions. They are totally useless, but a Pro windows is still Windows -- meaning a lot of bling and gimmicks, and a huge amount of trouble! :)
Probably OK if you're playing games, but I don't have to play games to have fun.

(I have never even considered getting a newer Windows version. I still use XP which can handle my scanner, and that's the only thing I need that Linux doesn't do easier, better, faster, and more securely).

---

### Post by CharlesA on 2010-12-30
You can download Windows Services for Unix from Microsoft for free, you don't need to buy Win7 Ultimate just to get a NFS client.

---

