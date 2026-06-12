---
title: "Samba share issues"
date: 2015-10-13
forum: Windows
---

### Post by andy150 on 2015-10-13
Hi All. I hope i am in the right place for this - forgive me if not

I setup a plex media server setup on the device with an external USB attached (via USB hub). I intend to browse from my windows and other machines on my local network to this drive and upload movies, ideally without being prompted for credentials.
The OS can see the disk, which i have mapped to /media/PLEXHDD

I have installed samba and configured the smb.conf several times. 
My windows machine can see the machine and the share - but either cannot access the share or is prompted for credentials.

Pretty new to this, so guidance would be welcomed. My guess is the smb.conf is wrong and/or the permissions are wrong on the drive.
Below is my bare-bones smb.conf

[global]
    map to guest = bad user


[RaspPiUSB]
   comment = Raspberry Pi USB
   path = /media/PLEXHDD
   guest ok = yes

---

### Post by TheFu on 2015-10-13
How is the storage mounted?
What options are used?

I think you need to add a userid for the smbpasswd and a list of valid users. I've seen people use "guest users", but have never done that myself. [https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide) might help.

Also, please post the **testparm** output - and please use "code tags" [http://blog.jdpfu.com/code_tags](http://blog.jdpfu.com/code_tags)

---

### Post by andy150 on 2015-10-14
[FONT=arial]How can i check the storage and how its mounted?
It automatically added itself to \media\PLEXHDD from memory

Thanks for the suggestion. I did create a test user using [COLOR=#333333]smbpasswd 'Andy' with the password 'Andy' as a test. No joy trying that.
I'll run the testparm again but dont remember seeing any issues.

I'm pretty much new to all of the Linux world. Obviously i've been checking out forums and absorbing what i can, but i feel like i really need a hand now as far as steps to go forward.
I'm also confident a Linux guru could resolve it in minutes! Its so frustrating being 99% complete but i cant do this last part....[/COLOR][/FONT]

---

### Post by TheFu on 2015-10-14
If you didn't manually mount the storage -  using the /etc/fstab - then the defaults are what you have. Not good for services. It is fine for a single-user system when you are logged in,  but not for what you want here. The mount  options  need to allow your userid and plex to have full access.

BTW, it would be much easier if a linux file system was used, not NTFS.

userids need to be all lowercase. Do NOT mix case. Don't know if this is an issue or not, just that it is a 40+ yr old convention. Why tempt fate.

> please post the testparm output  Help us help you by answering the questions, please.

---

### Post by andy150 on 2015-10-16
OK we're getting somewhere!
So i need to mount my drive. Although should the drives have odd characters?

[ATTACH=CONFIG]264980[/ATTACH]

Testparm below
[ATTACH=CONFIG]264982[/ATTACH]

---

### Post by The Cog on 2015-10-16
I think you are having characterset problems with your SSH client. Those odd characters are actually line drawing characters showing a child relationship with the lines above. Here's mine:
```
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
mmcblk0     179:0    0   7.4G  0 disk 
&#9500;&#9472;mmcblk0p1 179:1    0    56M  0 part /boot
&#9492;&#9472;mmcblk0p2 179:2    0   7.4G  0 part /

```

---

### Post by andy150 on 2015-10-17
you were right - tried from my mac and its looking more 'normal'
[ATTACH=CONFIG]264995[/ATTACH]

whats the next step from here guys?

---

### Post by andy150 on 2015-10-17
i added the drive to fstab too. hoping this is right

[ATTACH=CONFIG]264996[/ATTACH]

---

