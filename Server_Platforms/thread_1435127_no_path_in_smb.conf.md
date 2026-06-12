---
title: "no path in smb.conf"
date: 2010-03-21
forum: Server Platforms
---

### Post by doru001 on 2010-03-21
I successfully shared a subdirectory of my home directory, using GNOME under Ubuntu 8.04 LTS Desktop. What drives me crazy is that I can't find this directory listed in /etc/samba/smb.conf, in a "path" line. Please tell me where is this directory specified, since smb.conf seems to be the only samba config file.

---

### Post by volkswagner on 2010-03-21
I am not 100% sure, but take a look here:

```
cat /home/yourusername/.gnome2/nautilus-share-modified-permissions
```

---

### Post by doru001 on 2010-03-22
> **volkswagner said:**
> ```
cat /home/yourusername/.gnome2/nautilus-share-modified-permissions
```

Thank you, that was it. Of course the path you gave me is not mentioned in smb.conf, but still I feel much better now. :KS I even shared a NTFS folder and Gnome remembered it, but who knows where can it be recorded. I'll stick with command line for now ... ;)

---

### Post by Morbius1 on 2010-03-22
Actually the share definitions are at /var/lib/samba/usershares

And you can also get a listing by going to your terminal and typing:

**net usershare info**

BTW, this isn't Classic Samba Sharing it's Nautilus-share

---

### Post by doru001 on 2010-03-23
> **Morbius1 said:**
> Actually the share definitions are at /var/lib/samba/usershares

And you can also get a listing by going to your terminal and typing:

**net usershare info**

BTW, this isn't Classic Samba Sharing it's Nautilus-share
Cool, thanks. I like to know a little bit around, even though samba is complicated and I can't cover it now.

---

### Post by whiteman on 2010-03-23
YOu have hit on something. I nver understood that there was Nautilus sharing and samba sharing. I have found that if I mix them up, I get logon problems..passwords that dont work...I was using the smbfs thing to add share. I didnt realize that there was a samba password. I kept typing what I knew to be my password and being told...WRONG PASSWORD. I finally unshared everything. Went back to gksudo Nautilus...shared the obvious way. Not very elegant, no file editng...just right clicking..prperties..share...etc. Yes you are so right. Usershare..samba share. Different animals. Not readily obvious.

---

