---
title: "Samba multi user setup"
date: 2019-12-22
forum: Ubuntu/Debian BASED
---

### Post by mr-glasspoole on 2019-12-22
Hi,

i hope i can get some quick help here. The thing is i bought my parents a Fire TV Stick for Christmas and thought I'm done until they get it.
I'm fighting with Samba since a view days and it does not work how i want it. There was never a need for multiple users until now.
But i want to make shares that my parents can access and listen to music and can record with TVHeadend.

I always thought you set all the permissions in SMB and just found out you do it in Windows:
[https://www.youtube.com/watch?v=QhwOyLtArw0](https://www.youtube.com/watch?v=QhwOyLtArw0)

From the video it must be possible to hide folder/files for people who don't have any permissions on the files.

I thought then its enough to give me (Ragnar) access and all permissions on the root of the disk and create all the folder there from my windows workstation and set permissions with it?
But i can't make it work.

I want two users: Ragnar and Harald

I have two drives I call "Records" and "Media":

Records (sdb1 | /mnt/records)
- TV records Harald
- TV records
- Download

Archiv (sdc1 | /mnt/archiv)
- Harald

-Backup
--- PC1
--- PC2

-Media
--- Music
--- Music Videos
--- eBooks

Harald should be able see "Records/TV records Harald" and have all permissions there.
Harald should be able see "Archiv/Harald" and have all permissions there.
Harald should be able see "Archiv/Media" and have ONLY read permissions.
Friends who visit me should be able to see "Archiv/Media" and have ONLY read permissions (maybe its best to make a user with a simple password for that?).
Ragnar should be able to see and do everything everywhere.

What i did so far:

```
~# sudo apt install samba

~# sudo useradd Ragnar -s /usr/sbin/nologin
~# sudo smbpasswd -a Ragnar

~# sudo useradd Harald -s /usr/sbin/nologin
~# sudo smbpasswd -a Harald

~# sudo nano /etc/samba/smb.conf

[global]
   workgroup = WORKGROUP
   log file = /var/log/samba/log.%m
   max log size = 1000
   logging = file
   panic action = /usr/share/samba/panic-action %d
   server role = standalone server
   obey pam restrictions = yes

[Records]
   comment = Disk 1
   path = /mnt/records
   browsable = yes
   read only = no
   create mask = 0666
   directory mask = 0777
   force user = Ragnar
   force group = Ragnar
   hide files = /lost+found/

[Archiv]
   comment = Disk 2
   path = /mnt/archiv
   browsable = yes
   read only = no
   create mask = 0666
   directory mask = 0777
   force user = Ragnar
   force group = Ragnar
   hide files = /lost+found/

~# sudo chown Ragnar /mnt/records
~# sudo service smbd restart
```

If look at security in Windows on the "Records" share i have:
Everyone: Special permissions
root (Unix Group\root): Special permissions
Ragnar (HECTOR\Ragnar): Special permissions

Do i need to change the group somehow?
Are the "Special permissions" normal instead of showing "Full control" for Ragnar and Read, Write for Everyone?

If i now create a file in records and look at security in Windows i have:
Everyone: Read, Write
Ragnar (Unix Group\Ragnar): Read, Write
Ragnar (HECTOR\Ragnar): Read, Write

So also no "Full control" for Ragnar...

What needs to be changed?
Or do i now just create my subfolders on Windows and set the permissions there?

Then is there a way to hide that lost+found entirely?
You still see it in Windows if explorer is set to "show hidden files".
I also see it on my Android devices.

Then there is a folder IPC$ on Android?

EDIT 1:
I cant remove Everyone on folders/files inside Records because of lost+found (access is denied).

EDIT 2:
I did a sudo chown -R Ragnar:Ragnar /mnt/records and can now remove the permissions for Everyone.
But Harald can read and write in Records???

EDIT 3:
Found out the problem is "force user/group". I thought that forces the permissions on file creation but that means every user looks like Ragnar and has permissions to anything.
So i removed that.

Then its not nice if Harald goes to \\hostname that he sees Records and Archiv.
Would be nice he would see TV records Harald, Harald and Media.

There is *browsable* = no, but that means I also cant see Records and Archiv.

If you search around many people suggest "access based share enum = yes".
But after more Google Fu it seems like it only works with AD/Domains.

---

