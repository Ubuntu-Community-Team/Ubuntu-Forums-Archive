---
title: "Ubuntu One repeatedly asks for authorizations"
date: 2009-11-06
forum: Ubuntu One (CLOSED)
---

### Post by arnab_das on 2009-11-06
Ubuntu one is asking for authorization to the same PC each and everytime i log in/reboot.

any solutions?

---

### Post by avdzm on 2009-11-07
i have the same problem,
every time ubuntu one starts it fails to autorizations my laptop and i have to re-add it again and again.

---

### Post by joshuahoover on 2009-11-09
> **avdzm said:**
> i have the same problem,
every time ubuntu one starts it fails to autorizations my laptop and i have to re-add it again and again.

I'm sorry to hear this is happening to you. This problem doesn't appear to be consistent, so I'm having a hard time tracking down the root cause. Before you start the Ubuntu One client the next time, can you check to see if you have an Ubuntu One token in Applications->Accessories->Passwords & Encryption Keys under the "Passwords" tab. Also, can you let me know if you're running Ubuntu 9.10 or 9.04? 

Thank you,

Joshua

---

### Post by nate_2001 on 2009-11-12
I'm having the same problem. I do currently have the key under the passwords and keys application, but it appears that it is being deleted when I shut down. The laptop is thus listed multiple times on the Ubuntu One authorized machines section on the server. It keeps issuing a new key because the old one is deleted and it thinks it's a new machine. This is a Karmic upgrade from 9.04 on a Lenovo x200.

Thanks!

---

### Post by avdzm on 2009-11-12
Hey Joshua,

Apparently there isn't a password saved under passwords.
I am using a fresh installation of Karmic.

---

### Post by Merovius on 2009-11-12
Same thing here on Karmic. U1 is listed under Passwords & Encryption keys. Been doing it for two days or so. My system was listed on the U1 account tab (web) 4 times. I removed the oldest three earlier. Will see if it happens again after next boot.

---

### Post by tekstr1der on 2009-11-12
I am experiencing the same behavior on Karmic. The U1 token disappears after a suspend-resume cycle in addition to reboot. I have authorized this machine countless times now. Every few days, I delete all the old computer accounts via the web interface. This is getting old fast.

Has a bug been filed for this issue? Hopefully this is a serious enough regression to make SRU. I would love to use U1 regularly in Karmic. Hope I don't have to wait on Lucid or add a PPA.

---

### Post by antisa on 2009-11-13
I bet you all automaticaly log on to your systems. 
I had the same problem. Here's the solution

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8089453](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8089453)

---

### Post by avdzm on 2009-11-13
> **antisa said:**
> I bet you all automaticaly log on to your systems. 
I had the same problem. Here's the solution

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8089453](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8089453)

I actually log on with a password.

---

### Post by arnab_das on 2009-11-13
> **antisa said:**
> I bet you all automaticaly log on to your systems. 
I had the same problem. Here's the solution

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8089453](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8089453)


ah that solved it for me thanks! :)

btw will leaving my keyring password blank cause any significant security issues? i'm the only one using my PC.

---

### Post by tekstr1der on 2009-11-13
> **antisa said:**
> I bet you all automaticaly log on to your systems. 
I had the same problem. Here's the solution

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8089453](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8089453)

No automatic logon on my laptop here. That would be foolish. Please don't assume.

---

