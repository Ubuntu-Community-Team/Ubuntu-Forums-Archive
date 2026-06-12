---
title: "Samba and WD My Book"
date: 2008-01-20
forum: Server Platforms
---

### Post by jrdemasi on 2008-01-20
I have a computer running a very stripped down Xubuntu install on it.  I recently got a 320GB My Book for my birthday and want to add the storage onto my samba share.  The drive used for my samba share is only a 40GB hard drive, so this is a big addition which is much needed.  I used this guide (roughly)  [http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1)

As of right now, the My Book mounts fine on my Server under /mnt/sda1 but I don't know how to share it using samba.  My configuration file is as follows:

[global]
panic action = /usr/share/samba/panic-action %d
workgroup = "Name"
netbios name = "Server name"
invalid users = root
security = user
wins support = no
log file = /var/log/samba.log
log level = 3 
max log size = 1000
syslog = 1
encrypt passwords = true
passdb backend = smbpasswd
socket options = TCP_NODELAY
dns proxy = no
passwd program = /usr/bin/passwd %u
passwd chat =*Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
obey pam restrictions = yes
pam password change = no
null passwords = no

#Share Definitions

[homes]
        comment = Home Directories
        browseable = yes
        writable = yes
        security mask = 0700
        create mask = 0700

Any help would be greatly appreciated, all of the data is sitting on my iMac G5 hard drive right now and slowing it down considerably.  :(

---

### Post by Rizado on 2008-01-20
```
[MyBook]
comment = WD MyBook
path = /media/sda1
browseable = yes
writable = yes
guest ok = no
```You should be able to add something like this. There should now be a share caller MyBook :)

Also you should probably remove the homes section unless you really want to share your home directory.

---

### Post by jrdemasi on 2008-01-20
okay so my next question is - there are two samba users. If I am on my samba account in the my book and the other user logs in, will it show my files to the other user?  Also, do you know how to auto mount the mybook at startup?

Thanks in advance -

---

### Post by jrdemasi on 2008-01-20
Also - another quick update.  I tried what you said, and It just says "The Volume MyBook could not be mounted" whenever I try to access it from another computer

---

### Post by smileypaul on 2008-01-21
Yes your files wil be visible to the other user.. depending on the permissions, he/she may not be able to read, write or execute them .. 

you can automount by editing fstab 

sudo gedit /etc/fstab

add

/dev/sda1 /media/sda1 0 0 

the above may change depending on the file system type...

---

### Post by jrdemasi on 2008-01-21
It's  in /etc/fstab and it's formatted FAT32 and it won't automount still.  Also - How can I make it so the other user CAN NOT see those files?  Before, when I was sharing the Home Directories it only showed the files of whoever was logged in.  Could I make two seperate folders and direct one user to one folder and one to the other?

---

### Post by smileypaul on 2008-01-21
To hide the files in the smb.conf file... try this

hide unreadable = Yes

It basically hides all files folders that the user doesnt have permissions to..

so, if you're hiding it from others... simply

chmod -R o-r,o-x,o-w ./*

that should remove all permissions for others on your files.. 

as for the auto mounting.. is it properply put in fstab?

try plugging it in, and then run 

dmesg | tail

that should show you the last actions..

hth

---

### Post by jrdemasi on 2008-01-21
Okay - But is that technically making them NOT visible to the other users on the Samba share or just making is so they can't access them?

---

### Post by smileypaul on 2008-01-22
removing the read permission would make it so they can't access them.. as for the "hide unreadable", to me , it sounds like it would not display files that the user doesnt have read permission for. BUT.. i do not use this option in any of my samba config files..

I suggest you just simply put it in there, and see what happens. I can't see it taking more than a few minutes.

---

### Post by jrdemasi on 2008-01-22
Even so at this point It wont' let me change the permissions so i can't even access the drive, so I'm not quite worried about that part yet but I'll keep it in mind :-)

---

### Post by huotg01 on 2008-03-02
Please visit the web site: [http://mybookworld.wikidot.com/start](http://mybookworld.wikidot.com/start)

---

