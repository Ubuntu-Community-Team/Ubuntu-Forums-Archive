---
title: "[SOLVED] Tomcat access to Windows (CIFS) Share"
date: 2008-01-24
forum: Server Platforms
---

### Post by mattias_reichel on 2008-01-24
Hi, this is my first post an I'm new to Linux and Ubuntu.
This is a great forum btw!

My problem is that I need the standard Tomcat 5.5 installation that comes with Gutsy to access a shared folder on a Windows computer that is member of a Win2000 domain (with read/write permissions).

To do this I have setup a mount point directory for this share on Ubuntu (/home/tomcat55/sharedir) and managed to get my web application to read/write to it. So far so good.

Then I have setup a user on the Windows Domain with username=tomcat55 and password=tomcat55 and added this user to the list of accepted user accounts on the windows share.

I then mount the share on Ubuntu with:
sudo mount -t cifs //windowshost/sharedir /home/tomcat55/sharedir -o user=tomcat55,pass=tomcat55,domain=MYDOMAIN,rw

After this I can without problem access the files on Windows host by going to the /home/tomcat55/sharedir directory with the shell or nautilus.

But now, my web application is no longer able to write to /home/tomcat55/sharedir.

I have also tried adding tomcat55 to Samba with:
sudo smbpasswd -a tomcat55
and
sudo smbpasswd -L -a tomcat55
sudo smbpasswd -L -e tomcat55
but this has not helped.

Any pointers on how to get this to work is much appreciated!

/Mattias

---

### Post by cdenley on 2008-01-24
Try this:

```

sudo mount -t cifs //windowshost/sharedir /home/tomcat55/sharedir -o uid=33,user=tomcat55,pass=tomcat55,domain=MYDOMAIN,rw

```

Change uid=33 to whatever the uid is of the user that tomcat runs as. On my computer, 33 is the uid for www-data.

---

### Post by mattias_reichel on 2008-01-24
Thanks cdenley, but this did not help.

I did:
```
id tomcat55
```
and got:
```
uid=110(tomcat55) gid=65534(nogroup) groups=65534(nougroup)
```

Then I did as suggested:
```
sudo mount -t cifs //windowshost/sharedir /home/tomcat55/sharedir -o uid=110,user=tomcat55,pass=tomcat55,domain=MYDOMAIN,rw
```
But regrettably my webapp still cannot access the shared directory.

---

### Post by cdenley on 2008-01-24
If you "sudo su tomcat55", can you write to it? You could try setting umask=000.

---

### Post by mattias_reichel on 2008-01-24
I tried:
```
sudo su tomcat55
```
and then
```
cp /home/tomcat55/text.txt /home/tomcat55/sharedir/text.txt
```
and this copied the file.

Or should I have used:
```
sudo su tomcat55 cp /home/tomcat55/text.txt /home/tomcat55/sharedir/text.txt
```
I'm not familiar with this concept :)
This did by the way not copy the file. I just returned with no message.

Could you elaborate on the umask 000 as I'm not familiar with this either, (I'm a bit of newbie on Linux coming from Windows environments.)

---

### Post by cdenley on 2008-01-24
sudo=gain root permissions
su=change user

sudo su tomcat55=gain root privileges to switch to user tomcat55
After running it, if you run the command whoami, it should say tomcat55. All commands run in that terminal will be run as tomcat55, until you exit.

If after running that command, you successfully copied a file into the share, then it is working as it should. Either your web application is not running as tomcat55, not functioning correctly, or tomcat is not configured right. I'm not really familiar with tomcat, so I can't help you with that.

The umask settings I was referring to is another mount option.
```

sudo mount -t cifs //windowshost/sharedir /home/tomcat55/sharedir -o uid=110,umask=000,user=tomcat55,pass=tomcat55,domain=MYDOMAIN,rw

```
umask is basically default unix permissions. For filesystems that don't support unix permissions, the umask is applied. umask=000 will give all users full access to all directories and files. This shouldn't be necessary, since you specified the owner with uid=110, and the owner should have full access by default.

---

### Post by mattias_reichel on 2008-01-25
Aha, thanks for the info!

Hmm, after:
```
sudo su tomcat55
```
I still get mattias from whoami, so I guess the user switch did not take place and therefore I'm still not sure if tomcat55 is allowed to write to sharedir. Any idea why su didn't work.

This is the tomcat55 line from /etc/passwd, perhaps the /bin/false shell stuff is the problem with changing to this user.
```
tomcat55:x:110:65534::/usr/share/tomcat5.5:/bin/false
```

The umask=000 parameter on mount did not help either :(

Also tomat is running three instances jsvc (which is the daemon used to by tomcat). One is running as user tomcat55 and the other two are running as root (see attached screenshot of system monitor). When I look in the daemon.log for the webapps write error on sharedir I can see the pid that the process had (11280). This pid seems to be mapped to one of the processes running as root:
```
Jan 25 06:36:22 webserver02 jsvc.exec[11280]: Jan 25, 2008 6:36:22 AM se.originalab.ia.core.mvc.CreateImagePreviewController onSubmit SEVERE: Could not enhance image.; nested exception is se.originalab.ia.core.image.w: Could not move file: '/var/lib/tomcat5.5/temp/a45pgi684f04b.jpg' to '/home/tomcat55/Q-in/a45pgi684f04b.jpg'
```

I guess this means I must setup a root account on the windows domain, or what should conclusions should I draw from this?

---

### Post by cdenley on 2008-01-25
Yeah, if the user has no shell, then su will immediately exit. You can change /bin/false to /bin/bash or /bin/sh, or troubleshoot in a different way.

You are working with permissions for two different computers, windows and linux. Since you can write to it using nautilus, the windows user tomcat55 has the approriate permissions. The mount on your linux server then gets unix permissions based on the gid, uid, umask, fmask specified by the mount options, or the defaults if not specified.  If one unix user can write and not the other, then it is a problem with unix permissions, not Windows permissions since you're computer is already authenticated as tomcat55 when it is mounted.

Does that error reference anything on your windows share? I though the share was mounted at /home/tomcat55/sharedir? Are you sure tomcat55 has permissions for the original file you are trying to move? I'm not sure, but I think it is possible that the process performing the move switches to user tomcat55 first to restrict file i/o, but I would try giving both permissions until you get it to work.

You can check effective unix permissions with "ls -l /path/to/file" or "ls -ld /path/to/dir".

---

### Post by mattias_reichel on 2008-01-26
I am sure that the tomcat55 user has sufficient permissions on the file that gets moved, because if I unmount the share the webapp has no problem to move the file to /home/tomcat55/sharedir. If I mount the share again, it cannot move it any longer.

I have since then installed tomcat6 (not coming with ubuntu) and am running i as root (not via jsvc). Still have exactly the same issue.

One thing I noted is that when I mount the share it gets tagged as read-only (shadowed checkbox) if I look at the folder properties on the windows box. Also if I copy a file into the share (from the linux box) and den delete it, I get a warning about deleting a write-protected file.

```

mattias@webserver02:~$ ls -l Documents/ia-folders/test.txt
-rw-r--r-- 1 mattias mattias 5 2008-01-25 16:45
mattias@webserver02:~$ cp Documents/ia-folders/test.txt Documents/ia-folders/Q-in
mattias@webserver02:~$ ls -l Documents/ia-folders/Q-in/test.txt
-rw-r--r-- 1 root root 5 2008-01-26 16:00 Documents/ia-folders/Q-in/test.txt
mattias@webserver02:~$ rm Documents/ia-folders/Q-in/test.txt
rm: remove write-protected regular file `Documents/ia-folders/Q-in/test.txt'? y
mattias@webserver02:~$

```

I see your point that it should not be the permissions on the windows side that gets in the way as the only user it will see is the one specified when mounting.

---

### Post by mattias_reichel on 2008-01-28
This is now working after changing my Java code from using the standard API call srcFile.renameTo(dstFile) to my own file copy (and delete) code.

Thanks for your help cdenley and I've certainly learned a lot about Linux while dabbling around with this issue (for far too long). :)

---

