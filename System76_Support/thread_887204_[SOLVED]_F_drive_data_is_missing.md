---
title: "[SOLVED] F drive data is missing"
date: 2008-08-11
forum: System76 Support
---

### Post by karthiknoble on 2008-08-11
Hi I'm new to ubuntu. I have win xp on C and Ubuntu on F drive, but i'm not able to access the other data like photos and pics that i have stored in F. can anyone help me out ?

---

### Post by sonofusion82 on 2008-08-11
ok. it seems that you are trying to access photos and pics in ubuntu drive/partition from windows?
i believe there are some ext3 driver/software that can be used to access your ubuntu "F drive" . but i have not tried it myself.
if not you can probably copy the files from ubuntu to your wind xp C drive.

---

### Post by karthiknoble on 2008-08-11
Nope ubuntu is not accessing any data in f drive it shows only three drives the fourth one (F drive) where i have loaded ubuntu is not displayed.

---

### Post by sonofusion82 on 2008-08-11
ok, you mean that you are using windows and you want too see the files in that ubuntu drive?

---

### Post by karthiknoble on 2008-08-12
nope these data were stored in f drive before i loaded ubuntu. now when i switch on my system and choose to load ubuntu i'm unable to view these files in the ubuntu interface

---

### Post by lisati on 2008-08-12
> **karthiknoble said:**
> Hi I'm new to ubuntu. I have win xp on C and Ubuntu on F drive, but i'm not able to access the other data like photos and pics that i have stored in F. can anyone help me out ?

> **karthiknoble said:**
> nope these data were stored in f drive before i loaded ubuntu. now when i switch on my system and choose to load ubuntu i'm unable to view these files in the ubuntu interface

If I've understood you properly, the photos etc, were previously on F:, and now Ubuntu is on the drive. If this is the case, there's a good chance that your photos etc. are no longer there.

Please run ```
sudo fdisk -l
``` so we can have a better idea of how the disks on your computer are organized.

---

### Post by karthiknoble on 2008-08-12
i'm able to view these files when i load win xp but when i load ubuntu these are not seen as a matter of fact F drive where i loaded ubuntu is not to be seen at all. anpther problem that i'm facing is that the sound qualiy is quite poor in ubuntu

---

### Post by lisati on 2008-08-12
> **karthiknoble said:**
> i'm able to view these files when i load win xp but when i load ubuntu these are not seen as a matter of fact F drive where i loaded ubuntu is not to be seen at all. anpther problem that i'm facing is that the sound qualiy is quite poor in ubuntu

1) Do any of your logical disks show up when you click on the "places" menu?
2) Do you have NTFS-3G installed? (it helps with accessing Windows partitions)

---

### Post by patrickfromspain on 2008-08-12
Maybe you used the wubi install method? Did you install ubuntu from windows?

---

### Post by karthiknoble on 2008-08-12
> **patrickfromspain said:**
> Maybe you used the wubi install method? Did you install ubuntu from windows?
Hi guys,

Thanx for all the support. I downloaded pc file manager and now am able to view all data in F drive in a folder called "host". So i guess that takes care of that now if you could help me to increase the volume when i play movies or songs that would be great!!!

---

### Post by Sef on 2008-08-18
> Thanx for all the support. I downloaded pc file manager and now am able to view all data in F drive in a folder called "host". So i guess that takes care of that now if you could help me to increase the volume when i play movies or songs that would be great!!!

Please start another thread for that problem.  I am marking this one as solved.  Remember one thread, one problem.  That way your problems can all be addressed.

---

### Post by rondexx23 on 2008-12-25
I am also new to linux on a hole. I was having the same problem and reading the solution here helped. Thanks alot.

---

