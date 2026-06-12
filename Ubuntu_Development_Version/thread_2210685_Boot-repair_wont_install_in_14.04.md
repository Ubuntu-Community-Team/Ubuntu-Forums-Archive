---
title: "Boot-repair wont install in 14.04?"
date: 2014-03-12
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-03-12
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Tried yesterday, the ppa adds in , but nothing to install.

Can someone try it?

---

### Post by Hazzabin on 2014-03-12
I had to change in the synaptic settings repos/ other software go edit and change from 
Trusty to Saucy and then reload, it should then show up as normal in synaptic so you can install as per normal

---

### Post by kansasnoob on 2014-03-12
There is no Trusty version yet:

[ATTACH=CONFIG]251067[/ATTACH]

---

### Post by donmyers on 2014-04-01
I totally lost my ability to boot windows with my Ubuntu 14.04 install today. I have work I must get done in the Windows sie of my computer. I tried everything I could try to make the disk repair work, and then went searching and found this. I could not get the ropo information added to try to run the utility to fix things. Could you please give me some additional guidance? This needs to be run in the Live cd, correct? Thank you.

---

### Post by orj-gmail on 2014-04-10
> **donmyers said:**
> I totally lost my ability to boot windows with my Ubuntu 14.04 install today. I have work I must get done in the Windows sie of my computer. I tried everything I could try to make the disk repair work, and then went searching and found this. I could not get the ropo information added to try to run the utility to fix things. Could you please give me some additional guidance? This needs to be run in the Live cd, correct? Thank you.

try this: [http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

---

### Post by amgd-moh on 2014-04-18
You can use the following commands to install boot-repair in Ubuntu 14-04 :-
```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo sh -c "sed -i 's/trusty/saucy/g' /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list"
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
```

---

### Post by sdowney717 on 2014-04-18
Thanks, but this line will run it.

sudo apt-get install -y boot-repair && boot-repair

just do this line,

sudo apt-get install -y boot-repair

 I ended up using xkill, because I did not want boot-repair to do anything.

Also doing that so it uses saucy, what happens when trusty repo gets going? Is there a downside?

---

### Post by monkeybrain20122 on 2014-04-19
The downside is it may have conflicting dependencies, if there is no dependency you can just install the .deb instead of trying to use a repo for a different release.
Also don't use -y in your apt-get install command. You don't know what dependencies it will bring and whether it may cause problems, you exactly want the package manager to prompt you instead of going by 'best guess'!

One reason why I don't make zeroth day releases my working system. ppas often take time to set up.

---

### Post by MikeCyber on 2014-04-21
Most people will fix Grub from the live CD hence it doesn't matter. But I find it very poor that they still have not updated to trusty.- Also Grub is somehow poor as I've had the very same error with 12.04, but this might be of it's complexity.

---

### Post by Elfy on 2014-04-21
> **MikeCyber said:**
> Most people will fix Grub from the live CD hence it doesn't matter. But I find it very poor that they still have not updated to trusty.- Also Grub is somehow poor as I've had the very same error with 12.04, but this might be of it's complexity.

You do know that 'they' is one person and that boot-repair is only available from a PPA.

If you think that someone not having time for it is very poor then I am sure that they will be happy to receive your help.

---

### Post by ventrical on 2014-04-22
Trusty now comes with the capability of restoring broken systems. If all else fails (Grub Rescue .. etc.. ) then you can use the TT.iso.  

When booting up you can choose re-install or  go to <something_else> during the partitioning session of Ubiquity.  Choose sda(n),  (where 'n' equals the partition to be restored) then,  Change. Make partition ext4, choose '/' (root) but do not format. It will save all fo your home files and bookmarks but you will have to reinstall some programs. Grub Rescue has always worked for me when installing an Ubuntu Product side by side with a Windows product.  Especially Windows 8 and UEFI.

---

### Post by clinklet on 2014-06-06
The problem I have is that Canonical would put out a release that has so many boot problems with UEFI systems.  It just makes me want to purchase support just so that I can yell and scream and  get listened to.

---

### Post by cariboo on 2014-06-06
Seeing as this thread isn't about Utopic, thread closed.

---

