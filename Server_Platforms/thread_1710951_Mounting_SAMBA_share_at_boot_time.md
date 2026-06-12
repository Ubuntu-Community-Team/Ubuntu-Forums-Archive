---
title: "Mounting SAMBA share at boot time"
date: 2011-03-20
forum: Server Platforms
---

### Post by Krupski on 2011-03-20
Hi all,

I have Ubuntu 64 bit server 10.10 which is both my family media server and web server (LAMP).

Now, I tried something: I mount my web server root directory as a SAMBA share, then have a symlink which points "/var/www" to the SAMBA share.

I do this so that filenames on the web server are case insensitive. That is, if I have an actual file named "./images/smilies/laugh.gif", I can access it with "./IMAGES/SMILIES/Laugh.GIF" (any combination of case works).

My problem / question is that, even though this works (the share mounts), I get an error message in DMESG:

[QUOTE="dmesg"][   74.386850] CIFS VFS: Error connecting to socket. Aborting operation[/QUOTE]

This is how I'm mounting it (in /etc/fstab):

```

# samba / web pass-through for case insensitive filenames
//localhost/webroot             /var/www-smb        cifs    credentials=/root/.credentials 0       0

```

In .credentials are username=name,password=password.

Anyone know why it WORKS, but I get an error message? And, am I doing it right, or is there a better way?

By the way, if I "umount" the Samba share, then type "mount -a" it re-mounts with NO error message. So, I think it's some kind of timing issue... something isn't up and ready before it's called... I just don't know what.

Any ideas will be greatly appreciated.

Thanks!

-- Roger

---

### Post by volkswagner on 2011-03-20
Have you seen [this thread]("http://ubuntuforums.org/showthread.php?t=1705052")?

Do you have mount.cifs installed?

```
mount.cifs -V
```

---

### Post by Krupski on 2011-03-20
> **volkswagner said:**
> Have you seen [this thread]("http://ubuntuforums.org/showthread.php?t=1705052")?

Do you have mount.cifs installed?

```
mount.cifs -V
```

Yes I do... 

```
root@storage:/# mount.cifs -V
mount.cifs version: 4.5
```

What confuses me is that it WORKS, but it throws the error message... :confused:

---

### Post by volkswagner on 2011-03-20
My guess it is because it is already part of the file system.  I'm no expert, and I have never seen such a setup. 


Did you create the SAMBA share /webroot in smb.conf?

---

### Post by Krupski on 2011-03-21
> **volkswagner said:**
> My guess it is because it is already part of the file system.  I'm no expert, and I have never seen such a setup. 


**Did you create the SAMBA share /webroot in smb.conf?**

Yes I did! :)

Here's everything I did:

* Created a user "smbuser" and assigned a password

* Ran "smbpasswd -a...." also named "smbuser" and assigned the same password to the SMB user

* Created a ".credentials" file in /root which contains the "username=smbuser" and "password=the_password".

* Created an empty directory in /var named "smb-www"

* Added "webroot" as a SAMBA share in smb.conf

* Added the mounting info for it in FSTAB:
--- Filesystem: //localhost/webroot
--- Mount point: /var/www-smb
--- Type: cifs (also tried smbfs - same result)
--- Options: credentials=/root/.credentials
--- Dump: 0
--- FSCK: 0

* Added a symbolic link /var/www -> /var/www-smb


As I said, it works fine... only problem is the error message in DMESG. If I don't auto-mount it with FSTAB and instead do it "by hand" later, it mounts instantly with no error message.

I'm completely stumped on this one... :confused:

---

### Post by ClayMitchell on 2011-04-03
You ever come up with anything here? I'm having the exact same issue.

edit: actually mine isn't the same issue, it just doesn't work at boot at all. The /bin/mount -a works fine.

---

### Post by utp216 on 2011-04-03
If it is working why bother worrying about the error message? I would leave well enough alone with your setup.

---

