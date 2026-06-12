---
title: "File Sharing"
date: 2009-11-27
forum: Server Platforms
---

### Post by Sock puppet on 2009-11-27
I'm pulling my hair out here. This seems like it should be a simple thing and I'm quickly losing the confidence of my wife that we should stick with Linux for this. Anyways, I'm trying to set up a filesharing server for all our music, pics etc.. print sharing down the road. I installed ubuntu server 9.10 selecting samba to be installed also. I edited the smb.conf to include
```

[home]
comment = home
        browseable = yes
        path = /home/daniel
        guest ok = yes
        read only = no
        writeable = yes
        create mask = 0775
        directory mask = 0775

```

but I can't connect from my ubuntu desktop. I tried chmod the home directory. I googled and searched this forum, trying different things all to no avail. Even if I can recognize the drive I am unable to write to it. I get a permission denied error. This seems like it should be fairly simple but I seem to be goofing it up somehow.

---

### Post by KiLaHuRtZ on 2009-11-27
Use NFS.  Samba is only needed for Linux to Windows.  NFS is *NIX native and is a much better solution going from Linux to Linux (also faster).

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by Sock puppet on 2009-11-27
> **KiLaHuRtZ said:**
> Use NFS.  Samba is only needed for Linux to Windows.  NFS is *NIX native and is a much better solution going from Linux to Linux (also faster).

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)


I have windows boxes on the network I'm going to need to get in on the action.

---

### Post by KiLaHuRtZ on 2009-11-27
In that case, try this...

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by Sock puppet on 2009-11-27
> **KiLaHuRtZ said:**
> In that case, try this...

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
Thanks that had a lot of great info. I'm still stuck though. It seems like my ubuntu client should be asking for a password and it's not. I can't browse the shared files but can't copy or create anything, I get an "permission denied: error. Any ideas anyone?

---

### Post by Vegan on 2009-11-27
Add 

```
force group = mygroup
force user = username

```
this will solve some problems

---

### Post by Sock puppet on 2009-11-27
> **Vegan said:**
> Add 

```
force group = mygroup
force user = username

```
this will solve some problems

Thanks Vegan. Would this be under Global or for the share?

---

### Post by Vegan on 2009-11-27
In the specific shares

I use 777 for my files to eliminate all problems

---

### Post by windependence on 2009-11-28
> **Vegan said:**
> In the specific shares

I use 777 for my files to eliminate all problems

Yes, I'm sure those hackers will make sure all your troubles go away.

@Sock puppet, please don't mod your files to 777 unless you want to open up a serious security hole. 755 is usually enough if the groups and users are set up properly.

-Tim

---

### Post by koenn on 2009-11-28
> **Sock puppet said:**
>  It seems like my ubuntu client should be asking for a password and it's not. 
what did you set for 'security' in the global section of smb.conf ?

---

### Post by Sock puppet on 2009-11-28
> **koenn said:**
> what did you set for 'security' in the global section of smb.conf ?

I tried both =user and =share to no avail.

---

### Post by koenn on 2009-11-28
> **Sock puppet said:**
> I tried both =user and =share to no avail.
from memory, and it's been a while, so I might be wrong, but
-security=share would not prompt for passwords, but rely on the filesysem security.  Or Samba may default to "guest". So that may be part of your problem.  'force user' and 'force group' may help to work around that, but I would be weary about the chmod 777.

-security=user requires you create samba user accounts for all users that need access to the shares. If you haven't done that, it wont work. 
In my experience, security=user is more predictable, so easier to troubleshoot (it's just a matter of accounts and permissions) although it may be a bit more complex to design a suitable solution. 

I suggest you decide which route to take, and have a look at the relevant samba documentation. Come back if you have more questions

edit: here's a brief intro: [http://users.telenet.be/mydotcom/howto/linuxsbs/samba1.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba1.htm)

---

### Post by Sock puppet on 2009-11-28
Thanks everyone, I got it. Changed to force user, force group and set up a directory mask to 755. security = user.

---

