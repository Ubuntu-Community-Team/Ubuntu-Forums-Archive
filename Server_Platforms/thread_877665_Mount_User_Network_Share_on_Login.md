---
title: "Mount User Network Share on Login"
date: 2008-08-02
forum: Server Platforms
---

### Post by Benismyhorse on 2008-08-02
Hi, I am setting up Ubuntu to work in a school environment, which runs a windows 2003 server.

My Question: I have joined the school domain using Likewise, and edited a Samba Conf file so it is possible to logon using only username and not DOMAIN/username,
How would I get Ubuntu to mount and unmount a user's share on our file server on login and logout?

Can anyone Please Help:confused:

Thanks

---

### Post by redraiderbum on 2008-08-02
I know this isn't much help, but if you know a scripting language you could run a simple script that is run at login and logout to simply mount and umount a users home directory.

---

### Post by redraiderbum on 2008-08-02
My previous response leaving a wanting feeling, I thought you could try to do it with fstab.  You would want to add a line to fstab that mounts a networked drive that is always in the same place.  I'm not sitting in front of a linux computer currently, but it seems like this should be an easy fix.  I will test it out tonight to see if I can figure it out.

---

### Post by tdcdodger on 2008-08-02
redraiderbum is right, the simplest (and less secure way) to do this is to add a line to fstab. The reason that it is insecure is because using this method, you leave your password exposed in plain text.

Here is a guide on how to do this:

[http://bubble.gritto.net/db/query.php?id=43&ty=HOWTO](http://bubble.gritto.net/db/query.php?id=43&ty=HOWTO)

If you have any questions let me know.

---

### Post by yeaitsdark on 2008-08-02
Personally, I "secure" my password by adding the line in fstab to read a file read only by root.

```
//SERVER/SHARE     /media/share     cifs    credentials=/home/USER/.smbcred 0 0
```

.smbcred contains
> 
domain=DOMAIN
username=USERNAME
password=PASSWORD


Change owner and group of file to root.
```
sudo chown root:root .smbcred
```

Make file read/write ONLY to root.
```
sudo chmod 0700 .smbcred
```

Because /etc/fstab is able to be read by anyone. This is a simple way to add some security to your password.

---

### Post by Benismyhorse on 2008-08-03
Thanks for the Reply,
Editing the fstab won't work because we have around 1000 students with all different network shares,
Any More Ides???:confused:

---

### Post by tanveer on 2008-08-03
Hi,
I am facing the same problem like you.
And seems pam_mount is the solution so far. I am currently trying to make it work.

---

### Post by songshu on 2008-08-03
you might want to have a look at autofs

---

### Post by Benismyhorse on 2008-08-03
Hi, could you please tell me the results you get using pam_mount Please

Thanks

---

### Post by tanveer on 2008-08-03
Working on make it work under Hardy. Already posted in networking section the problem.

---

### Post by Benismyhorse on 2008-08-04
songshu how would I go about setting up autofs?

---

### Post by Benismyhorse on 2008-08-05
Bump

---

