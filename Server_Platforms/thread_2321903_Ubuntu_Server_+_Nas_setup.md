---
title: "Ubuntu Server + Nas setup"
date: 2016-04-25
forum: Server Platforms
---

### Post by stan26 on 2016-04-25
I have rolled my home over to Ubuntu and thing couldn't be better i am trying to setup and ubuntu server with the following

Server: Ubuntu 15.10
 X6 Amd cpu
16GB HyperX ram
60GB Samsung ssd
1gb  nic

Nas:
Marvell 88F5281 cpu 500Mhz
128mb DDR2 ram speed unkown
1gb nic

Things I'm using this server for

http (working)
phpbb3 (working)
owncloud working)
squid (still setting up)
openfire jabber (still learning)



i am trying to use my acer aspire easy store link: [http://www.pcworld.idg.com.au/review/acer/aspire_easystore/254404/specs/](http://www.pcworld.idg.com.au/review/acer/aspire_easystore/254404/specs/)
as storage but i having troubles setting this up, The nas is setup in raid 1 as raid 5 fails for some reason so i have two volumes Volume_1 and Volume_2 i have mounted these on server and book marked them also and i can see them under ```
/run/user/1000/gfvs/smb-share:server=xserver2,share=volume_1
```

Im trying to use the nas storage as some thing like **/var/www/html/**"symlink" to my nas**/data** this will be the best option moving forward for me we all things after the /html folder are on the nas  

the nas uses user name and password access i would like to keep it this way but if it is to much hassle i can always give access to everyone  
 
i have been reading alot of tuts about getting this setup but im running to brick walls based on my knowledge and understandings

so any kinda help in helping me getting this resolved will be great!

---

### Post by TheFu on 2016-04-25
Welcome to the forums.

Don't use gvfs access for system-level storage.  In short, you need to put this into the /etc/fstab and mount it that way.  Also, not all NAS storage is created equal.  CIFS storage should NOT be used for a web server due to security considerations - at least I wouldn't do it.  Make certain that storage device supports NFS and that the disks are formatted with a Linux file system, not FAT32 or NTFS.  It appears you have accessed it using CIFS/SMB.

Never give userids and passwords to people like us.

---

### Post by stan26 on 2016-04-25
yeah i had that in mind as at the moment i know the whole is open at the moment.
im 100% sure that the nas uses a linux os and the ext2 file sys ill have a look into what fstab is

---

### Post by stan26 on 2016-05-01
Well finally got around to trying to fstab this nas to the server and as of yet have had no luck, in the meantime, I've started using the mount -t cifs command instead of using gvfs to navigate my way to the nas this is the line i have added into the fstab

I tried this first
```
//192.168.1.11/volume_1/ /nas/dsk1 cifs uid=1000,gid=1000,credentials=/home/xstan/.nascredentials,iocharset=utf8,sec=ntlm 0 0
```

Then I changed to this
```
//192.168.1.11/volume_1/ /nas/dsk1 cifs credentials=/home/xstan/.nascredentials,uid=1000,gid=1000 0 0
```

/home/xstan/.nascredentials
```
username=username
password=password
domain=workgroup
```

current error when using mount -a
error 2 (No such file or directory) opening credential file /home/xstan/.nascredentials

if anyone could let me know where im going wrong that will be most helpful

---

### Post by darkod on 2016-05-01
Are you sure the spelling of the path and filename is correct? It complains it can't find the file.

I am not sure if root has to own that file, but you can try that- Of course, any modification in future will have to be done as root in that case.

If you go to the path and list all files, does it show it as hidden (with the dot in front)?
```
cd /home/xstan
ls -al
```

---

### Post by TheFu on 2016-05-01
a) the mount cmd that I've used is:
```
sudo mount -t cifs //192.168.1.14/D /Data  -o rw,iocharset=utf8,file_mode=0666,dir_mode=0777,credentials=/etc/samba/win7lap-D.credentials 
```
The credentials file DOES NOT have any domain specified in my use, but looks like yours otherwise. I don't know if that matters or not. The "no such file or directory" means you need to check the spelling carefully.  I bet you have already - I'd copy/paste the filename from the fstab to be positive. Also check that permissions are 600 on that file.  Don't know if that matters or not, but I do know that some tools, like ssh, are really picky about file permissions. Anything holding credentials should be 600 anyway.
Does the /nas/dsk1 directory already exist? It must. Also, might want the directory owner to match the username inside the creds file.

b) I've never used the /etc/fstab for CIFS mounts.  Windows locks up too much, which would lock up my linux machines. My Linux systems will use NFS, NOT CIFS for file sharing.  I would post a CIFS fstab example, if I had one, honest.  I prefer to use autofs for CIFS mounts. An example:
```
$ more /etc/auto.Data 

D      -fstype=cifs,rw,iocharset=utf8,file_mode=0666,dir_mode=0777,credentials=/etc/samba/win7lap-D.credentials  ://172.22.22.14/D
```
This way, if the other machine (.14) dies, the Linux machine won't be impacted.

Lastly, thanks for posting the contents of files, but it would be easier to read if "*code tags*" are used, as I've done (Adv Edit '#'). 

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently) has step-by-step info for setting up fstab with CIFS mounting and also explains what isn't a good idea.  Nothing is jumping out to me, except that using .nascredentials AND uid/gid probably doesn't work. Pick 1 method to specify users. 

Again, if your NAS supports NFS, I'd strongly advise using that rather than CIFS. There are many reasons, but mainly to enhance the security for the data being stored on the NAS - so all normal Unix-style permissions work.

Anyway, hope the examples above (which work) provide some other ideas for you.

---

### Post by stan26 on 2016-05-01
[TABLE="class: ui_table sortable ui_columns, width: 665"]
[TR="class: row0 ui_checked_columns mainbody, bgcolor: #f5f5f5"]
[TD][[IMG]https://192.168.1.8:10000/filemin/images/icons/mime/text-plain.png[/IMG]]("https://192.168.1.8:10000/filemin/download.cgi?file=%2Enascredentials&path=%2Fhome%2Fstanx")[/TD]
[TD][.nascredentials]("https://192.168.1.8:10000/filemin/download.cgi?file=%2Enascredentials&path=%2Fhome%2Fstanx")[/TD]
[TD][IMG]https://192.168.1.8:10000/filemin/images/icons/quick/rename.png[/IMG][[IMG]https://192.168.1.8:10000/filemin/images/icons/quick/edit.png[/IMG]]("https://192.168.1.8:10000/filemin/edit_file.cgi?file=%2Enascredentials&path=%2Fhome%2Fstanx")[/TD]
[TD]51 bytes[/TD]
[TD]root:root[/TD]
[TD]0600[/TD]
[TD]2016/05/01 - 15:17:26[/TD]
[/TR]
[/TABLE]
 

omg ty think i found it
[TABLE="class: ui_table sortable ui_columns, width: 665"]
[TR="class: row1 ui_checked_columns mainbody, bgcolor: #f5f5f5"]
[TD][[IMG]https://192.168.1.8:10000/filemin/images/icons/mime/inode-directory.png[/IMG]]("https://192.168.1.8:10000/filemin/index.cgi?path=%2Fhome%2Fstanx")[/TD]
[TD][stanx]("https://192.168.1.8:10000/filemin/index.cgi?path=%2Fhome%2Fstanx")[/TD]
[TD][IMG]https://192.168.1.8:10000/filemin/images/icons/quick/rename.png[/IMG][/TD]
[TD]4 kB[/TD]
[TD]stanx:stanx[/TD]
[TD]0755[/TD]
[TD]2016/05/01 - 15:41:06[/TD]
[/TR]
[/TABLE]

i was using   
```
[COLOR=#000000][FONT=Ubuntu Mono]/home/xstan/[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]

ill correct error and test again

allgood! ty very much in helping get this done! [/FONT][/COLOR]

---

