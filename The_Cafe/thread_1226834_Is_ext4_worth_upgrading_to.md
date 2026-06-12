---
title: "Is ext4 worth upgrading to?"
date: 2009-07-30
forum: The Cafe
---

### Post by Revolutionary101 on 2009-07-30
Recently I was thinking about reinstalling Ubuntu on my laptop. The reason I want to do this is I have wanted to try ext4. Do you think it is worth it to upgrade from ext3 to ext4 and if so why?

---

### Post by deer dance on 2009-07-30
[This will probably help you.](http://ubuntuforums.org/showthread.php?t=1133719)

---

### Post by elliotn on 2009-07-30
I dont c any different

---

### Post by bear24rw on 2009-07-30
i noticed a big difference in boot times when i first tried it

---

### Post by stlsaint on 2009-07-30
please see sticky on main page of Insallation & Upgrades of ext3 or ext4!

---

### Post by Arup on 2009-07-30
Upgrade is really not worth it as all old files will remain in ext3 mode, only newer files will be written in ext4 mode. To get full benefit, you need a fresh install with ext4.

---

### Post by slumbergod on 2009-07-30
I would just wait until ext4 is the default file system i.e. Koala. It just isn't that compelling a reason for most users.

---

### Post by Revolutionary101 on 2009-07-30
Thanks for all of the input.

---

### Post by SunnyRabbiera on 2009-07-30
The "Upgrade" is completely optional with EXT4, EXT4 is not a security update or a  bugfix update, its just the next and perhaps final step in the EXT filesystem series.
EXT4 promises faster boot times, but it also has drawbacks:
[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

Hey EXT2 is still around and some people still use it, it was made in 93 when linux was new.

---

### Post by binbash on 2009-07-30
You will notice a big difference at boot times.

---

### Post by ericab on 2009-07-30
do it!

---

### Post by Revolutionary101 on 2009-08-04
Does anyone know if the stability issues with ext4 will be fixed in Ubuntu 9.10?

---

### Post by Sef on 2009-08-05
> Does anyone know if the stability issues with ext4 will be fixed in Ubuntu 9.10?


Until 9.10 is released that is impossible to say.

---

### Post by Revolutionary101 on 2009-08-05
Thanks

---

### Post by gletob on 2009-08-05
I personally think it is worth it.
1. Fsck of my Ext4 Partitions take 5 secs compared to the 45-60 for EXT3
2. I think that my machine boots faster
3. I've noticed file transfers are faster

Now I would reccomend for you to back all your data up and install 9.10 with new EXT4 partitions.

---

