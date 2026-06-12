---
title: "HP Proliant ML150 Drives not detected"
date: 2011-11-21
forum: Server Platforms
---

### Post by doctorzeus on 2011-11-21
Hey, 

I've got a ML150 which I am trying to install Ubuntu Server (64-bit) 11.10. However when the installer asks to choose a drive to partion and install to, none show up and I'm sorry to say that I am not that familiar with Serial ATA Raid HDD configirations.

Can someone please help me solve this?

Here is some info that may help from hp:

[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c00353768&lang=en&cc=us&taskId=101&prodSeriesId=372786&prodTypeId=15351](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c00353768&lang=en&cc=us&taskId=101&prodSeriesId=372786&prodTypeId=15351)

---

### Post by volkswagner on 2011-11-21
Did you set up your Raid before booting Ubuntu?

I previously setup an Adaptec raid.  The one issue I had was white space was created in the array name.  This caused different problems with different os's.

The solution for me was to make sure to fill all characters in the Array name in the Adaptec Bios setting (alt + A) when booting.  I believe my controller took 13 or 15 characters.  Just make sure you fill the field.

Try booting Ubuntu desktop live CD and check the output of:

```
sudo fdisk -l
```

---

### Post by doctorzeus on 2011-11-22
> **volkswagner said:**
> Did you set up your Raid before booting Ubuntu?

I previously setup an Adaptec raid.  The one issue I had was white space was created in the array name.  This caused different problems with different os's.

The solution for me was to make sure to fill all characters in the Array name in the Adaptec Bios setting (alt + A) when booting.  I believe my controller took 13 or 15 characters.  Just make sure you fill the field.

Try booting Ubuntu desktop live CD and check the output of:

```
sudo fdisk -l
```

Wow thanks your first suggestion helped alot! What I did was I simply removed all the arrays compleatly and everything popped up fine after that, I don't plan on doing any hotswaping anyhow!

---

