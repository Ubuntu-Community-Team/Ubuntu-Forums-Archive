---
title: "Going back to 10.04"
date: 2012-09-15
forum: System76 Support
---

### Post by tommyatkins on 2012-09-15
All,

I installed 12.04 as a update to 10.04. I have having nothing but trouble from the start. I have to log in as the administrator using a terminal using C-A-F1 to set the password and then going back to the GUI via C-A-F7. In addition the sound does not work and I have tried all the suggestions in the update forum. This is the third update I have done and had no problems before when I used a clean install.

My question is this if I do a clean install formating the / directory and not the /home directory with a 10.04 CD, as I have done in the past, can you foresee any problem with this ap[proach?

Thanks for any ideas and help

---

### Post by nevius on 2012-09-15
> **tommyatkins said:**
> All,

I installed 12.04 as a update to 10.04. I have having nothing but trouble from the start. I have to log in as the administrator using a terminal using C-A-F1 to set the password and then going back to the GUI via C-A-F7. In addition the sound does not work and I have tried all the suggestions in the update forum. This is the third update I have done and had no problems before when I used a clean install.

My question is this if I do a clean install formating the / directory and not the /home directory with a 10.04 CD, as I have done in the past, can you foresee any problem with this ap[proach?

Thanks for any ideas and help

Version updates can get borked. I'm working on fixing a bad update right now. Is there any reason why you can't just download and install from the 12.04 image?

---

### Post by cortman on 2012-09-15
Upgrades tend to be problematic (at best). Since 10.04 is only supported for another six months or so, your best bet is to do a fresh installation of 12.04.
Depending on your software versions the config files in your home directory may not work; in which case it's simple enough to remove them.
Although I can't verify this for certain, I believe you can keep the current /home and simply overwrite / - but be careful and BACK UP YOUR DATA first. :)

---

### Post by Lars Noodén on 2012-09-16
If you made a separate /home partition, then it should be easy to keep your data through any migration, upgrade, downgrade or re-installation.  Just choose the manual partitioning and make sure that /home is not formatted.

If you do not have a /home partition, then it might be time to think about adding one, but you will need to backup your data first and then restore from the backup.  

If you are wondering about how big to make the root (/) partition, you can look at the overall current size with df 
and du and use that for your guess.

```

df -h
cd /
for i in *;do du -sh "$i";done

```

(As usual, backup your data)

---

### Post by tommyatkins on 2012-09-17
Thanks for the information.
 I have a separate /home partition and have done fresh installs in the past with no problems.
 I will go back to 10.04 as I think the new interface is terrible .
Thanks again.

---

### Post by joe4ska on 2012-09-22
When 10.04 hits end of cycle you can always switch to Xubuntu 12.04 or perhaps try MATE to get that Gnome 2 experience back.

---

