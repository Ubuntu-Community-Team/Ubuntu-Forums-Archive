---
title: "Creating a file share on Ubunto 7.10 Server"
date: 2007-10-21
forum: Server Platforms
---

### Post by petersfreeman on 2007-10-21
I want to set up a file share on an Ubuntu server.

I set up an Intel box with Ubuntu 7.10 using the LAMP option.

The Intel box has two physical hard drives.  The smaller hard drive is a 20Gb and the larger is 80GB.  I set up Ubuntu Server on the 20GB drive and I want to use the 80GB drive as a file server serving various multi-media files.

I believe that I need to:
1.	Create file shares on the 80GB drive
2.	Set the permissions so that all of the drive can be red or written to
3.	Expose the drive on the net so that Windows XP machines can see it

Can you point me to tutorials or forum posts that explain how I can go about it, or can you give me a better idea of the steps I need to take to achieve this goal.

Thanks,

Peter Freeman

---

### Post by notaloafer on 2007-10-22
Is this what you're looking for? Samba allows you to share files to any kind of OS in your network (Windows, Linux, or Mac)...

Here's the tutorial. If you use Gnome at all it's extremely easy to setup.

[http://ubuntuforums.org/showthread.php?t=76647](http://ubuntuforums.org/showthread.php?t=76647)

Hope this helps...
-Eric

---

### Post by petersfreeman on 2007-10-23
Thanks Eric.

I have installed Samba and I have made very minimal changes to the smb.conf file to set the Workgroup to the name of my home network work group and I have exposed the cdrom, however I still cannot see my Ubuntu Server from a Windows XP box.  Here are the changes I made in the [global] section:

workgroup = HOME

Then as a test, I uncommented this section to see if I could see a share from a Windows box:

[cdrom]
   comment = Samba server's CD-ROM
   writable = no
   locking = no
   path = /cdrom
   public = yes
   preexec = /bin/mount /cdrom
   postexec = /bin/umount /cdrom

I let everything else the same as the default installed smb.conf.

I went to the Windows XP box and I was expecting to click on My Network Places/Entire Network/Microsoft Windows Network/Home and see the Ubuntu Server show up in the "Home" workgroup.  It didn't.  I guess, I have to get Samba to broadcast itself. 

How do I do that?

Thanks Eric,

Peter

---

### Post by petersfreeman on 2007-10-23
Hi Eric,

I read the information in the link you provided and I added the netbios name =  <servername> information as well as setting browseable and writable to yes, however I still do not see the server from the Windows box.  Any clues? 

Thanks Eric,

Peter

---

### Post by petersfreeman on 2007-10-23
Hi Eric,

More info:

I tried connecting to the CDROM from the windows box by mapping a network drive and using the ipaddress:  \\192.168.1.10\cdrom and it worked.  I can see th disk in the drive. 

So far so good.

Now I need to make the 80GB drive shareable.  Can I make the whole drive shareable (it is empty)?  If so, the question is:  What is its name so I can do a [drivename] section?

If not, do I have to create a high level folder under the root and make that a share?

Thanks Eric.

Peter

---

### Post by petersfreeman on 2007-10-23
Got it!  Found out how to do it with some trial and error and a late night.  I am now serving my big second drive.  Thanks for your help.

Peter

---

### Post by notaloafer on 2007-10-23
Sorry I didn't get back to you sooner :P but Samba has issues with Name-based networking.. with my network as well I had to go to using IP addresses instead of the actual "name" of my server.
Glad it worked out!

-Eric

---

### Post by hkgonra on 2007-10-24
> **notaloafer said:**
> Sorry I didn't get back to you sooner :P but Samba has issues with Name-based networking.. with my network as well I had to go to using IP addresses instead of the actual "name" of my server.
Glad it worked out!

-Eric

If Samba has issues with name based networking is there any other program that would work well with name based networking ?

---

### Post by trmentry on 2007-10-25
I'm still stuck on getting my shares to work.  I keep getting these errors.

```

#tail log.smbd
[2007/10/24 00:37:27, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[2007/10/24 00:37:29, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2007/10/24 00:37:29, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[2007/10/24 00:37:30, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2007/10/24 00:37:30, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users

```

I made a post 24 hour ago or so but nada... 

[http://ubuntuforums.org/showthread.php?t=589364](http://ubuntuforums.org/showthread.php?t=589364)

Anyone please help.
Thanks

---

### Post by tsella on 2007-12-04
after banging my head on this error for an hour or so, going through a myriad dead posts all this same error, i found this [http://bugs.donarmstrong.com/cgi-bin/bugreport.cgi?bug=385372](http://bugs.donarmstrong.com/cgi-bin/bugreport.cgi?bug=385372)

(reprinting so not lost)

> 
From: Gustaf Räntilä <opera@kth.se>
To: [email]385372@bugs.debian.org[/email]
Subject: "Solved", sort of...
Date: Fri, 01 Sep 2006 00:33:28 +0200

By stracing, I found that it was winbind messing. When shutting down 
winbind (I don't use it anyway), and removing its pid file 
/var/run/samba/windbindd.pid and the socket 
/var/run/samba/windbindd_privileged/sock and restarting samba it now works!

To me, this is a major bug. Samba shouldn't fail completely just because 
winbind fails, if I've told it to use smbpasswd or tdbsam, or am I wrong 
here?

Btw, it works with my previous setting (smbpasswd), so I'm happy as it 
is. But someone needs to explain why one service should cause another to 
die, when it's not needed in the first place.

Regards,
Gustaf


---

