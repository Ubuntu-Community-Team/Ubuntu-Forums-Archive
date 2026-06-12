---
title: "not authorized to mount usb or DVD drives"
date: 2011-01-02
forum: Server Platforms
---

### Post by sjhupp on 2011-01-02
Hi all, I've got a 10.04 server install, on which I installed a basic gnome desktop.  But I've never been able to automount usb drives or DVD/CDs!?  Have searched and seen similar complaints here:
[http://ubuntuforums.org/showthread.php?t=1336847](http://ubuntuforums.org/showthread.php?t=1336847)
but seem for desktop. May relate to not having standard gnome install?  I don't have users-admin to try that, and don't see install package.

I also saw this bug/fix, but unsure how to patch to test??
[https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/483130](https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/483130)
I can see:
simon@starbug:~$ ck-list-sessions
Session1:
	unix-user = '1000'
	realname = 'Simon'
	seat = 'Seat2'
	session-type = ''
	active = FALSE                   ** is this a problem??? **
	x11-display = ':1'
	x11-display-device = ''
	display-device = ''
	remote-host-name = ''
	is-local = TRUE
	on-since = '2010-12-31T11:15:12.280760Z'
	login-session-id = '4294967295'

Any guidance appreciated!
I can sudo mount from cli, but I do like to vnc in to a gui.
Thanks.

---

### Post by cipherboy_loc on 2011-01-02
What are the permission on mount? I remember having to modify those permissions when I failed to restore from one of my backups properly.

```
ls -l $(which mount)
```


Cipherboy

> **sjhupp said:**
> Hi all, I've got a 10.04 server install, on which I installed a basic gnome desktop.  But I've never been able to automount usb drives or DVD/CDs!?  Have searched and seen similar complaints here:
[http://ubuntuforums.org/showthread.php?t=1336847](http://ubuntuforums.org/showthread.php?t=1336847)
but seem for desktop. May relate to not having standard gnome install?  I don't have users-admin to try that, and don't see install package.

I also saw this bug/fix, but unsure how to patch to test??
[https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/483130](https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/483130)
I can see:
simon@starbug:~$ ck-list-sessions
Session1:
    unix-user = '1000'
    realname = 'Simon'
    seat = 'Seat2'
    session-type = ''
    active = FALSE                   ** is this a problem??? **
    x11-display = ':1'
    x11-display-device = ''
    display-device = ''
    remote-host-name = ''
    is-local = TRUE
    on-since = '2010-12-31T11:15:12.280760Z'
    login-session-id = '4294967295'

Any guidance appreciated!
I can sudo mount from cli, but I do like to vnc in to a gui.
Thanks.

---

### Post by sjhupp on 2011-01-03
Thanks for the suggestion.

simon@starbug:~$ ls -l $(which mount)
-rwsr-xr-x 1 root root 82256 2010-03-23 04:57 /bin/mount

Do I change this?
Not sure where things should mount to.

---

### Post by cipherboy_loc on 2011-01-03
> **sjhupp said:**
> ls -l $(which mount)
-rwsr-xr-x 1 root root 82256 2010-03-23 04:57 /bin/mount


Is what I get. If you want, you could try adding the devices that you will be mounting to fstab. Make sure you mount them by UUID, instead of by /dev/sdb1 (I think they are callEd device handles, but I am not sure). Then you can mount them with `mount -a` I think.


Cipherboy

---

### Post by sjhupp on 2011-01-03
> **cipherboy_loc said:**
> Is what I get. If you want, you could try adding the devices that you will be mounting to fstab. Make sure you mount them by UUID, instead of by /dev/sdb1 (I think they are callEd device handles, but I am not sure). Then you can mount them with `mount -a` I think.


Cipherboy

Hmm, thought that was for fixed disks though?
I've got my hard drives in fstab, but I don't know UUID of every flash drive I may use!  Didn't think you should add removable drives in fstab? Maybe!!:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Will try it out,

Should work for the optical drive though.
Any idea exactly what options and path to pass?
Thanks!

---

### Post by sjhupp on 2011-01-04
Also worth noting I can automount an audio CD, but not a DVD ??
Have to do a DVD manually:
simon@starbug:~$ sudo mount /dev/cdrom /media/cdrom
mount: block device /dev/sr0 is write-protected, mounting read-only
simon@starbug:~$ 

And read only... will try fstab.

---

### Post by sjhupp on 2011-01-15
Just a followup note - CDs and DVDs can now automount ok.
Still work to be done on usb drives.

---

