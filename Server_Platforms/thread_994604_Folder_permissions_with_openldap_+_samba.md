---
title: "Folder permissions with openldap + samba"
date: 2008-11-26
forum: Server Platforms
---

### Post by johnybgood11 on 2008-11-26
Hi everyone,

I have installed and openldap server according to this tutorial:

[http://www.rrcomputerconsulting.com/view.php?article_id=3](http://www.rrcomputerconsulting.com/view.php?article_id=3)

Now I can successfuly join a domain with a windows xp pro machine and login. But I'm still facing some problems which I hope you can help.

First, I want to put user folders and files in a raid 1 partition mounted on /media/disk. In smbtools.conf I have:

[HTML]userHome="/media/disk/ldaphome/%U"
userHomeDirectoryMode="700"

userSmbHome="\\welkadc01\ldaphome\%U"
userProfile="\\welkadc01\profiles\%U"
userHomeDrive="H:"
[/HTML]
and I have mount manager mounting the raid. Right now, when I login in windows I can see all users folders in my server share. Is there a proper way to mount an ntfs raid 1 disk to properly work with windows shares and permissions?

I'm also having problems with user permissions when logging into windows. Somehow even when I log with root (domain admin user) I don't have permissions to install anything under windows.

Sorry about talking so much in windows but i'm sure that this is due to some server configuration error...

Oh and by the way my smb.conf home share looks like this:

[HTML][ldaphome]
path = /media/disk/ldaphome
writeable = yes
browseable = yes
security mask = 0777
force security mode = 0
directory security mask = 0777
force directory security mode = 0[/HTML]

For full reference please see the attachement

Thanks in advance
Joao Ribeiro

---

### Post by Drezard on 2008-11-27
Im a little lost here. 

Can you break it down and explain each problem a little more? From what I understand you can either see all or none of the home folders, and you need a driver to fix this? 

Please break it down problem by problem. 

Daniel

---

### Post by johnybgood11 on 2008-11-27
> **Drezard said:**
> Im a little lost here. 

Can you break it down and explain each problem a little more? From what I understand you can either see all or none of the home folders, and you need a driver to fix this? 

Please break it down problem by problem. 

Daniel

OK. sorry about that. So breaking down.

First problem: how to auto mount an ntfs disk in Ubuntu server 8.10 so that it can be usablable to store files and definitions from my network users. The disk is ntfs.

The way things are working now. I can mount my ntfs disk. User can login but his/her definitions and profile settings are not stored and he can write on all disk even folders that he should not.

Any help?

thanks

---

