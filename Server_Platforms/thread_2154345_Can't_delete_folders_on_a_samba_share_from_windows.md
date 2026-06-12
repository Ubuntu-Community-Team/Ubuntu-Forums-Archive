---
title: "Can't delete folders on a samba share from windows"
date: 2013-06-14
forum: Server Platforms
---

### Post by adotomov on 2013-06-14
I have a question regarding samba shares and ubuntu server 12.04.2 LTS. I have configured a samba share on my ubuntu 12.04.2 LTS for my 1TB external HDD. I can access the HDD from my windows pc, but I can't delete or modify any files or folders in it. I created a folder under /mnt called share/ and mounted my HDD there. What I found out is that only root can delete/modify files in that folder. I created a samba user and password with which i can log in from windows and it works. However, it says that I need permissions from root to modify files or folders. If I login with root account to my samba share, it sais "device is busy" when i try to delete files. My question is, how can I configure samba so that I can mount the drive in /mnt/share and have full access to the storage from windows.

---

### Post by darkod on 2013-06-14
To configure read/write permissions for all on /mnt/share you can do:
sudo chmod -R 777 /mnt/share

That will implement RW for all subfolders too.

In future, it will depend who creates the folders/files. If you create a folder as root the chances are you will have to do the above again to reassign permissions.

Also, make sure you are not passing other permissions with the samba share definition, or a read-only option.

---

### Post by slickymaster on 2013-06-14
> **adotomov said:**
> I have a question regarding samba shares and ubuntu server 12.04.2 LTS. I have configured a samba share on my ubuntu 12.04.2 LTS for my 1TB external HDD. I can access the HDD from my windows pc, but I can't delete or modify any files or folders in it. I created a folder under /mnt called share/ and mounted my HDD there. What I found out is that only root can delete/modify files in that folder. I created a samba user and password with which i can log in from windows and it works. However, it says that I need permissions from root to modify files or folders. If I login with root account to my samba share, it sais "device is busy" when i try to delete files. My question is, how can I configure samba so that I can mount the drive in /mnt/share and have full access to the storage from windows.

Open and edit your smb.conf file:```
gksu geany /etc/samba/smb.conf
```and add this to the very end of the file:
```
[sharedfolder]
path = /home/your_username/sharedfolder
available = yes
valid users = your_username
read only = no
browsable = yes
public = yes
writable = yes
```Save and close. Then restart Samba:```
sudo restart smbd
```

---

### Post by bab1 on 2013-06-14
> **adotomov said:**
> I have a question regarding samba shares and ubuntu server 12.04.2 LTS. I have configured a samba share on my ubuntu 12.04.2 LTS for my ***1TB external HDD***. ... My question is, how can I configure samba so that I can mount the drive in /mnt/share and have full access to the storage from windows.
Most external HDD's are connected via a USB port and use NTFS formatting.  Is this what your HHD is like?  If so the only way you can set initial the ownership is at mount time.  If you are the only user then the mount options are uid=1000,gid=1000.  This will make you the owner with full permissions.  Then you can share it and access it with your user name.

---

### Post by adotomov on 2013-06-14
> **bab1 said:**
> Most external HDD's are connected via a USB port and use NTFS formatting.  Is this what your HHD is like?  If so the only way you can set initial the ownership is at mount time.  If you are the only user then the mount options are uid=1000,gid=1000.  This will make you the owner with full permissions.  Then you can share it and access it with your user name.

I honestly tried every other possible configuration besides this one. I completely neglected the mount options. Thanks a lot, this solved my problem.

---

