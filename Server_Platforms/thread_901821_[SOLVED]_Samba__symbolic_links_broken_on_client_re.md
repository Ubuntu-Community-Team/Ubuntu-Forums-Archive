---
title: "[SOLVED] Samba : symbolic links broken on client restart"
date: 2008-08-26
forum: Server Platforms
---

### Post by sym_zo on 2008-08-26
Hello,

I have a problem with samba shares and symbolic links.

I have a server and a client, and on the server I share two folders (public and private). These folders are actually folders where I put symbolic links targeting the real folders I want to share. For this to work, I added this line to each folder shared in /etc/samba/smb.conf : 
```
follow symlinks=yes
```

All this working very well, I decided to add these folders to /etc/fstab on the client : 
```
//server/public/		/media/server-public    smbfs   credentials=/etc/smbmountlogin,iocharset=utf8   0       0
//server/private/	        /media/server-private    smbfs   credentials=/etc/smbmountlogin,iocharset=utf8   0       0

```

After restarting my client, the connection is successful, and I can access my two folders /media/server-public and /media/server-private.

The problem is that the symlinks aren't "followed" anymore.
The only way to restore these symlinks is to : 
[LIST=1]
[*]unmount the folders on the client
[*]restart samba on the server ( /etc/init.d/samba restart )
[*]mount the folders again on the client
[/LIST]

Does anybody know a way to fix this, or where I should look to find an answer (or at least better diagnose my problem) ? 

Thank you !

---

### Post by windependence on 2008-08-27
Looks like the stuff you are symlinking to may be on removable media, no? If so, the media probably isn't mounted at the time fstab is read to mount the symlinked folders, just a guess.

-Tim

---

### Post by MJN on 2008-08-27
Have you searched the forums? In particular, did [this thread](http://ubuntuforums.org/showthread.php?t=352016) help?
 
Mathew

---

### Post by sym_zo on 2008-08-27
> **windependence said:**
> Looks like the stuff you are symlinking to may be on removable media, no? If so, the media probably isn't mounted at the time fstab is read to mount the symlinked folders, just a guess.

-Tim

Thank for your reply, Tim. Does a SATA internal hard drive count as removable media ? On the server, the symlink in the shared folder point to a folder on another hard drive, which is mounted in the server's fstab. 

I'm suprised this could be a problem since I thought samba would be started after the mount points of fstab were mounted. Moreover, I thought that samba would follow the symlink once it was working, even if it didn't work at first.

sym_zo

---

### Post by windependence on 2008-08-27
Sorry, it was late and the /media mount thew me off on that one.

It does look like Mathew's link is the ticket for you on this. Give it a try and let us know.

-Tim

---

### Post by MJN on 2008-08-27
That said, it's strange that it works with a mount cycle (and Samba restart). In the absence of anything else it's got to be worth a try though.

Mathew

---

### Post by sym_zo on 2008-08-28
> **MJN said:**
> That said, it's strange that it works with a mount cycle (and Samba restart). In the absence of anything else it's got to be worth a try though.

Mathew

Ok, I got it to work ;-). Thank you for your replies. Quite funny, I had already read that thread when I first tried to mount my folders, and consequently I had : 

[LIST=1]
[*]Added this parameter in the folder share definition in smb.conf : ```
follow symlinks=yes
``` 
[*]Disabled linux extensions using  : ```
echo "0" > /proc/fs/cifs/LinuxExtensionsEnabled
```
[/LIST]

But this apparently was not enough, hence this post. This time, I added the instructions of [this reply]("http://ubuntuforums.org/showpost.php?p=4095531&postcount=10") ( [http://ubuntuforums.org/showpost.php?p=4095531&postcount=10](http://ubuntuforums.org/showpost.php?p=4095531&postcount=10) ) :

> This is what worked for me; edit the [global] section of /etc/samba/smb.conf this way (correct or add the missing lines):
```
follow symlinks = yes
wide symlinks = yes
unix extensions = no
```

(The referenced smb.conf is the server's one).

... And after reboot, my problem had disappeared ! So the solution was either "wide symlinks" or "unix extensions".

Once again, thank you guys ;-)

---

### Post by skralljt on 2010-08-07
I tried using the standard three lines including wide symlinks=yes but was still having trouble.  I noticed in syslog that ubuntu didn't know what wide symlinks were: 

(Aug  7 08:37:00 amd64 smbd[3297]: [2010/08/07 08:37:00,  0] param/loadparm.c:7472(lp_do_parameter)
Aug  7 08:37:00 amd64 smbd[3297]:   Ignoring unknown parameter "wide symlinks")

....so I added another line:

follow symlinks = yes
wide symlinks = yes
wide links = yes
unix extensions = no

and now my share works again.  I saw somebody else using wide links=yes elsewhere, I wonder if wide symlinks option is deprecated.  HTH somebody before they lose all their hair!

---

### Post by DiGiTGOD on 2011-02-20
Just thought I'd add to this in case anyone comes looking.

"wide links =yes" is a share specific setting.

"Follow symlinks = yes" and "unix extentions = no" are global.

you can use testparm from the commandline to find out whether samba is recognising your settings.

Hope this helps someone...

Thanks,
Martin

---

### Post by bonfire89 on 2011-05-20
> **DiGiTGOD said:**
> Just thought I'd add to this in case anyone comes looking.

"wide links =yes" is a share specific setting.

"Follow symlinks = yes" and "unix extentions = no" are global.

you can use testparm from the commandline to find out whether samba is recognising your settings.

Hope this helps someone...

Thanks,
Martin



This did help someone... that someone being me. Thanks!

---

### Post by pbounds on 2011-07-17
What burns my butt is everytime I run an aptitude update from Ubuntu and it updates Samba, it breaks my symlinks in the samba shares, to my Windows machine.  This happens every friggin time!  Jezz then I gotta go fix the damn symlinks all over again.  

And Ubuntu used to be so good about not breaking stuff!!

:mad:

---

### Post by capscrew on 2011-07-17
> **pbounds said:**
> What burns my butt is everytime I run an aptitude update from Ubuntu and it updates Samba, it breaks my symlinks in the samba shares, to my Windows machine.  This happens every friggin time!  Jezz then I gotta go fix the damn symlinks all over again.  

And Ubuntu used to be so good about not breaking stuff!!

:mad:

This is most likely due to the changes in the default behavior in Samba for security reasons.  It is not an Ubuntu problem.  See [**_[COLOR="DarkSlateGray"]here[/COLOR]**_]("http://www.samba.org/samba/news/symlink_attack.html") and [**_here_**]("http://think-security.com/exploiting-the-samba-symlink-traversal/").  FYI This change occurred 2 years after this thread was started.  The OP's problem had nothing to do with yours.

---

