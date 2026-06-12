---
title: "Windows 8.1 cannot access SAMBA share with mhddfs folder"
date: 2014-09-16
forum: Server Platforms
---

### Post by kiena on 2014-09-16
I setup a file-server in home with Ubuntu server 14.04. I use mhddfs to merge all my HDDs into one big folder  /storage/pool
           >  mhddfs /media/hdd1,/media/hdd2,.....,/media/hdd6 /storage/pool -o allow_other,nonempty
I can access folder /pool over my LAN (SAMBA and NFS) with all devices running IOS/ Android/Windows 7. Problems happening when i use any PC which running Windows 8.1 to access /pool, I always get the message:
>  "Windows cannot access \\HOME-SERVER\pool. Contact your network administrator to request access". 
but after I try:
>  fusermount -u  /storage/pool
I can access that folder without any problem same as another devices which running Windows 7.

Please help !!!

---

### Post by volkswagner on 2014-09-16
How are you logged into Windows 8 (local user or an online account like [email]user@hotmail.com[/email])?

---

### Post by kiena on 2014-09-16
I login into Windows 8 with online account  like [email]xxx@live.com[/email]

---

### Post by kiena on 2014-09-16
Thanks @Volkswagner. Fully understood what you mean. I try to creat an local account on my laptop and access to server again. Now it worked as it be.
Last question: why I can access with online account  if do not merge all my HDDs ? Are there any way to access my "big folder" with online account instead of have to creat a local account ?

---

### Post by volkswagner on 2014-09-16
Sorry I don't know the technical details. Think about this, a local user can't use the appstore!

It's Microsoft proprietary ways.  It may be simply related to the username containing an "@" character. This is a special
character which indicates a group for SAMBA.  I'm not sure if your issue has anything to do with mhddfs, my hunch it's 
simply not authenticating based on the username.

You can try mapping a drive and select login using different username and password.

EDIT:
Well sorry, I'm not sure if mhddfs has anything to do with it.  Did you make changes to the samba permissions?

I also just found this.  In windows 8, while logged in as user@emailAddress, go to Control Panel > User Accounts and Family Safety > Credential Manager.
You can add specific username and password on a per server basis!

---

### Post by kiena on 2014-09-17
Nothing changed in SAMBA permissions. Problem happening after mount "big folder". I have been tried in both mddfs and aufs and got same results.
Try follow your guide with Windows Credential Manager but still not worked. After Googling, I also found some ways but all of them required some setup in both Windows 8.1 and SAMBA server (add group user/group valid user) so unworkable.

---

### Post by lilw on 2014-09-21
I am able to access to my share folder in ubuntu 14.04.1 from windows 8.1 by create a password for samba

sudo smbpasswd -a [user_name]

Hope it will help!

---

