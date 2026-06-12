---
title: "External HDD To Samba Shared Folder"
date: 2017-12-01
forum: Ubuntu/Debian BASED
---

### Post by djrikstar on 2017-12-01
I have set up a samba share on my raspberry pi which i access via other devices around the house and off my windows laptop too. I managed to set it up as I'm more use to running NFS mounts first time with Samba. It was set up and I was able to watch the videos but could not delete them or edit any files.

So after digging around on Google I came across this thread here **[https://ubuntuforums.org/showthread.php?t=2198667&page=3](https://ubuntuforums.org/showthread.php?t=2198667&page=3)** which I followed from around page 3 and set up a samba shared drive with the path **/****srv****/samba/share **which works perfectly but I need to be reading and writing from my external HDD which is mounted in the location [B]/media/pi.

[/B]I changed the path in the samba config to /media/pi and restarted samba but it did not allow me to delete a video or create files from windows pc saying about permissions. I also recursively set everything within the /media/pi folders to 755 and I still couldn't delete the videos.

So what I'm wanting to know is if there is a way to have the /**media/pi** contents show up in the **/****srv****/samba/share ** as a copy of the media folder without being a copy so it would give me access to delete and create folders straight off my windows laptop as I plan on using it as a NAS.

Any help appreciated.

---

### Post by uRock on 2017-12-01
Which distro are you running on your Pi? You may get better answers by posting on [Raspberry Pi Forums]("https://www.raspberrypi.org/forums/") if you haven't already.

---

### Post by djrikstar on 2017-12-01
The Pi is running on the latest Raspbian Stretch. But I just want to know what is the best way to have any linux distro see a shared folder from an original media folder and let me delete items on it. As the above scenario would be the exact same on Ubuntu as well so may help someone down the line that sees's the answer. ty

---

### Post by uRock on 2017-12-01
I've been playing with the latest Raspbian enough to know that a lot of simple settings that are made in ubuntu do not work in Raspbian. That said, have you added a Samba user on the Pi?

[https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated%2C%20Simple%20and%20Brief%20Way%21](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated%2C%20Simple%20and%20Brief%20Way%21)

---

### Post by djrikstar on 2017-12-01
Yes I created a samba user but called it pi which is the name of the main user but I used a different password for the share.

Seems to be a permissions problem as I just done the below and even chmod 777 all files and folders recursively in the **/media/pi** directory.

Tip2: Remember that your user must have permission to write and edit the folder you want to share.
[FONT=inherit][/FONT]Eg.:
[FONT=inherit][/FONT]sudo chown <user_name> /var/opt/blah/blahblah
[FONT=inherit][/FONT]sudo chown :<user_name> /var/opt/blah/blahblah

After running **ls -l /media/p**i I get the below output which looks like no matter if I chmod 755 etc the ownership will not change for the external drive.

> pi@raspberrypi:~ $ **ls -l /media/pi**

total 5
dr-x------ 1 pi pi 4096 Nov 14 19:43 AA92394C90391F1E
drwxrwxrwx 4 root root 1024 Nov 29 21:50 SETTINGS



This is my smb.conf

> [Vids]
comment = Shared Data
path = /media/pi
browseable = yes
read only = no
guest ok = yes
force group = users
writeable = yes
create mask = 0664
force directory mode = 0775






---

### Post by uRock on 2017-12-01
That is one of the things I do not like about Raspbian. In ubuntu, we just right click, select arguments for sharing, then share. 
Only commands I run is to add the users as I like to be able to see who adds or deletes files.

Take a look at this. Someone was nice enough to share their config.
[https://www.raspberrypi.org/forums/viewtopic.php?t=109428](https://www.raspberrypi.org/forums/viewtopic.php?t=109428)

Here's his config that the OP in that links says he copied and it fixed the problem.
```
[a_share]
  comment = a_comment
  path =/srv/a_folder/
  public = yes
  only guest = yes
  browseable = yes
  read only = no
  writeable = yes
  create mask = 0644
  directory mask = 0755
  force create mask = 0644
  force directory mask = 0755
  force user = root
  force group = root
```I think I'd change one line,```
public = no
```

---

### Post by DuckHook on 2017-12-02
*Thread moved to **Ubuntu/Debian BASED** as the more appropriate forum.*

---

### Post by djrikstar on 2017-12-02
Thanks uRock I added that in but still the same. I also tried unmounting and making a new mount point and then adding the samba share on the mounted folder but will not let me do make any files or delete files etc.

I just tried to make a txt file by running > sudo touch filename.txt but got this drive is read-only even after trying to chmod 755 the whole mount point I get read-only for every folder/file. I'm beginning to think the HDD is somehow locked as a read-only now.

---

### Post by uRock on 2017-12-02
Did you run the following after making changes? ```
sudo service smbd restart
```

---

### Post by djrikstar on 2017-12-03
Yes I restart each time after any changes to the smb.conf file. I now have my samba drive as the auto mounted point of the external USB HDD which is > /media/pi/AA90464B90311F9F

Now when i run the command > **sudo** touch filename.txt I get [B]touch: cannot touch 'filename.txt': Read-only file system

[/B]After running a ls -l command to see who owns the folders i get this

> 

pi@raspberrypi:/media/pi $ ls -l
total 5
dr-x------ 1 pi   pi   4096 Nov 14 19:43 AA90464B90311F9F
drwxrwxrwx 4 root root 1024 Nov 29 21:50 SETTINGS



So it seems a permission issue but it does not seem like the mounted point wants to change to allow itself to be written to by non root users??

Also I just tried to chroot 755 all the folders and files recursively inside the /media/pi location by doing the below

> pi@raspberrypi:/media/pi $ sudo chmod 755 -R /media/pi



But it gave me this error for every folder and file at the end of the names [B]Read-only file system

[/B]So I'm not sure how to rectify the issue so I can make the drive readable and writable now. It seems USB HDD does not want to be written to??

The hard drive is in NTFS filesystem format and not ext3 etc would this make a difference I would have thought not??

---

### Post by uRock on 2017-12-03
Change the permissions the 757 and see if that fixes it. The documentation has me thinking the Samba user and the host user may not have the same permissions, even though they have the same name.

---

### Post by djrikstar on 2017-12-03
Tried to chmod 757 and still get **read-only**** error** for every file when it's trying to change the permissions. Also tried it as root and still won't let me change it I have a feeling its something to do with the external USB HDD?

---

### Post by uRock on 2017-12-04
You get this error when logged in locally and running as root?

---

### Post by djrikstar on 2017-12-04
Yes logged in locally and I even tried it using sudo -i then trying as root.

---

