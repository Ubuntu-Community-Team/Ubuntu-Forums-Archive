---
title: "Samba sub-directory write/modify permissions?"
date: 2017-02-19
forum: Server Platforms
---

### Post by JusticeEmpire on 2017-02-19
Hi All,

I had a thread for my server setup --> [https://ubuntuforums.org/showthread.php?t=2339981](https://ubuntuforums.org/showthread.php?t=2339981) but I now have a more specific issue relating to samba permissions, and again I think I am confused from what I've been reading up

I have a share setup, containing multiple directories etc, that I have previously had full (unsecured) access to from my Win10 laptop, and had no major issues. 
It's structured as...

/data
../Audio
../Photos
../Video


Following a recent security breach, I needed to get on with securing that share. I spent a bit of time going through the samba docs, but found them confusing, and a lot of the search results seem to provide conflicting information.

**What I'm looking to achieve:**

Primarily, I want to have a singular login access via win10, that gives me full access to the share and its contents, including sub-directories. After that, I want to create multiple users with different levels, e.g. 'family' user, given read-only access to certain folders for photos, music etc.

**What I currently have:**

I have currently have login access to the share from Win 10, and I have the ability to create a new folder within /data. However, I have no write/modify access to any of the other directories. I only noticed this when I went to modify and save an existing file.

**/etc/samba/smb.conf**

```
[Data]
comment = Data
path = /data
browseable = Yes
writeable = Yes
read only = no
guest ok = no
create mask = 0777
directory mask = 0777
public = no
```

I am not sure if I am getting confused with the Ubuntu/Linux/Samba/Windows users etc, the create/directory masks, or a combination of the two.

If someone could point me in the right direction it would be greatly appreciated.

Thanks in advance

---

### Post by simonlap on 2017-02-19
I had the same issue last week! What I did was the following
1 main group for the entire family : Famille
1 sub group for the wife and I : Conjoint
the other users don't have any other group because they are the only one to have access to their folder.
/data 
../Conjoint
../Lise
Here's the permissions to the folders :
drwxrwx---  5 root     famille  ./
drwxr-xr-x 24 root     root      ../
drwxrwx---  5 simonlap conjoint /Conjoint
drwx------  3 lise     lise      /Lise
d----w----  2 root     root    /lost+found

Here's my samba file :
[Data]
        write list = @famille
        writeable = yes
        browsable = yes
        comment = Data
        valid users = @famille
        path = /Data

---

### Post by JusticeEmpire on 2017-02-19
That's just reminded me about the folder permissions, I was having a look from the win10 laptop but obviously couldn't apply any changes. That could well be a way around it for now, not really at the stage yet where I want to setup multiple users, that's more a phase 2 mission.

Can you remind me of the command for the drwxr..... etc?

---

### Post by JusticeEmpire on 2017-02-19
```
rhysuser1@JEServer:~$ ls -l /data
total 44
drwxr-xr-x  4 nobody    nogroup    4096 Oct 26 19:37 Audio
drwxr-xr-x  4 nobody    nogroup    4096 Nov  4 19:27 Business
drwxrwxrwx  2 root      root      16384 Oct 16 09:31 lost+found
drwxr-xr-x 15 nobody    nogroup    4096 Jan  8 13:55 Photos
drwxr-xr-x  7 nobody    nogroup    4096 Nov  4 19:38 Rhys
-rwxrw-rw-  1 rhysuser1 rhysuser1   152 Feb 19 17:06 test.txt
drwxr-xr-x  3 nobody    nogroup    4096 Oct 18 06:16 Video
drwxrwxr-x  2 rhysuser1 rhysuser1  4096 Feb 19 17:04 z Test Folder
```

The z Test Folder and test.txt are what I have been able to do from Win10. I've also disabled the auto login from Win10 so I now have to enter the pw every time, but I can get it with both JESERVER\rhysuser1 & rhysuser1  (hence why I said I might be getting confused with the users etc)

Or, is my issue to do with the 'nobody' & 'nogroup'?

---

### Post by simonlap on 2017-02-19
Fully explained here : [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
chown command to setup owner and group
chmod to setup permission! Don't use -R as, you will not want every user to have access to child folders. Set permissions 1 folder at the time, longest route, but safer! The good side of it - you'll be a champ at settings permissions ;)

---

