---
title: "Samba Server Size Limit"
date: 2014-03-09
forum: Server Platforms
---

### Post by katie2 on 2014-03-09
Hi. 

I have created a new user & home folder on samba for several mounted hard drives to be used as data dumps.  The hope is that I can move stuff from my Windows machine directly to one of my mounted hard drives to free-up space and use as a a back-up. My hard drives are 2TB in size.  Problem is I have several mounted hard drives (4) of 2TB in size (so 8TB total), but the entire directory in samba server called "mounted drives" is being maxed out at 1TB?

Very confused and need some help!

Thanks!!!

---

### Post by TheFu on 2014-03-09
I've never seen that limitation. Are you certain the place you believe under samba is really the correct place?  

Can you post the output from **testparm**, please?

Are you using any partition merging tools like aufs?

---

### Post by katie2 on 2014-03-09
```
root@eliot:/# testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Unknown parameter encountered: "unix passwd sync"
Ignoring unknown parameter "unix passwd sync"
Unknown parameter encountered: "wide symlinks"
Ignoring unknown parameter "wide symlinks"
Processing section "[public]"
Processing section "[mark]"
WARNING: The "only user" option is deprecated
Unknown parameter encountered: "revalidate"
Ignoring unknown parameter "revalidate"
Processing section "[dan]"
Unknown parameter encountered: "revalidate"
Ignoring unknown parameter "revalidate"
WARNING: The "only user" option is deprecated
Processing section "[katie]"
Unknown parameter encountered: "revalidate"
Ignoring unknown parameter "revalidate"
WARNING: The "only user" option is deprecated
Processing section "[peter]"
Unknown parameter encountered: "revalidate"
Ignoring unknown parameter "revalidate"
WARNING: The "only user" option is deprecated
Processing section "[lise]"
Processing section "[pasha]"
Processing section "[angela]"
Processing section "[megan]"
Processing section "[mounted_drives]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions


[global]
        workgroup = RABBIT HOLE
        server string = %h server (Samba, Ubuntu)
        log file = /var/log/samba/log.%m
        max log size = 1000
        unix extensions = No
        dns proxy = No
        idmap config * : backend = tdb
        path = /home/mounted_drives/
        read only = No
        create mask = 0644
        hosts allow = all


[public]
        path = /home/public
        username = @LabFolks
        valid users = @LabFolks
        write list = @LabFolks


[mark]
        path = /home/mark
        username = mark
        valid users = mark
        only user = Yes


[dan]
        path = /home/dan
        username = dan
        valid users = dan
        only user = Yes


[katie]
        path = /home/katie
        username = katie
        valid users = katie
        only user = Yes


[peter]
        path = /home/peter
        username = peter
        valid users = peter
        only user = Yes


[lise]
        path = /home/lise/
        username = lise
        valid users = lise


[pasha]
        path = /home/pasha


[angela]
        path = /home/angela


[megan]
        path = /home/megan


[mounted_drives]
        path = /home/mounted_drives
```

---

### Post by katie2 on 2014-03-09
I am also trying to potentially create a soft link from samba and/or the mounted drive to a public_html directory for an ubuntu user in his /home/user/public_html directory.  It's not quite working out

---

### Post by katie2 on 2014-03-09
partitioned as fat32 if that helps

---

### Post by TheFu on 2014-03-09
First, hopefully someone smarter will respond. There are a few samba experts here.  I'm sharing solution ideas and opinions below that have worked well for me over the yrs.

I think FAT32 is the major issue. I've only shared Linux File Systems via samba. Something like ext4. NTFS might work, but with user and group permissions, I'd be worried. FAT32, IMHO, should die, die, die, die.  A spinning HDD connected permanently connected to a Linux system needs EXT3/4, even if USB.  Regardless, both FAT32 and NTFS permissions will cause issue if when more than 1 userid/grpid needs access to the storage, only one groupid can be specified on the mount, right? UNIX permissions really need UNIX file systems - again, IMHO.

All those user HOME accounts can be handed automatically using something like this:
```
[homes]
        comment = Home Directories
        valid users = %S
        read only = No
        create mask = 0640
        directory mask = 0750

```
This will map the userid to the HOME and allow write for the user, read-only for the group.

Softlinks open up security issues, so samba requires a special parameter if you want to use them. 
```
wide links = Yes
```  This goes in the specific section for the specific share.

Hopefully, you saw all the warnings in the testparm output and plan to correct them.

If you need to share disks with multiple users, do that outside their HOME directories. Create groups as needed, put userids into the group who needs access and setup the samba share to allow members of that group access.  Are you running NIS?  If not, may want to change the '@group" into a '+group'. [https://www.samba.org/samba/docs/using_samba/ch09.html](https://www.samba.org/samba/docs/using_samba/ch09.html)  I ran NIS in the 1990s.

I don't know if this is important at all or not, but having spaces inside a workgroup might be an issue too. Don't know for certain. Spaces have a way of breaking scripts that glue things together. Most UNIX/Linux scripters know how to avoid it, but we don't always catch all the problems in the scripts.  I find it easier to just avoid spaces in any names, file names, or directory names - PERIOD.

I'd strongly recommend starting with a much simpler config, get that working, then add 1 more section at a time.  Make sense?

---

### Post by katie2 on 2014-03-09
I'll definitely give it a shot. Thanks for the advice!

---

