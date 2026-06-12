---
title: "Is installing Ubuntu Studio the same as installing Ubuntu?"
date: 2011-12-01
forum: Ubuntu Studio
---

### Post by peGGi on 2011-12-01
I will hopefully be installing Ubuntu Studio as part of a dual-boot with Windows this weekend.  I'm an Ubuntu and Linux newbie.

I realise that there is no Live CD for Ubuntu Studio.  

Is the installation procedure different?  Does it also have a GUI?

---

### Post by Quinflax on 2011-12-01
It is a significantly different process to installing "normal" Ubuntu, but still fairly easy.

You can find more information about Ubuntu Studio here. There are some links to installation guides in the second block of links (Installation/Upgrade).

[https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)

There is another installation guide here:

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-studio-11.10](http://www.howtoforge.com/the-perfect-desktop-ubuntu-studio-11.10)

All fairly easy (don't be put off by the length of the guides). The bit I stumbled at was the selection of software packages to install: use the cursor keys to move up and down the list and use the Spacebar to select/deselect the packages you want to install/not install.

---

### Post by beefheartvliet on 2011-12-01
I use Dream Studio myself, it's based on Ubuntu Studio. It has a easy installer. (just the same as ordinary Ubuntu) Furthermore. I appreciate you won't know anything about this at the moment, but...... Dream Studio is pre-configured with Pulse-Audio Jack Sync, Meaning that You could be playing a Synth through jack whilst having a Vid playing in Youtube.
You can't do that straight out of the box with Ubuntu Studio. It's also a Live Disk. 

I'd say to give it a go, I think you will have a better first time Experience ;-) 

Here's the link 

[http://dream.dickmacinnis.com/](http://dream.dickmacinnis.com/)

---

### Post by peGGi on 2011-12-01
Thanks Quinflax - this definitely eases the challenge, to see what's ahead of me, if I decide to go with Ubuntu Studio (beefhearvliet just threw a spanner in the works!) I'm grateful for the illustrated installation guide.

However there is a problem, as I feared.  Because of my laptop's already rather complicated partition table, and because I want to have a dual-boot Ubuntu/Windows set up, I have a fairly tricky re-partitioning ahead of me.  This is why I was keen on a GUI for the installation.  I understand that the 'normal' Ubuntu uses a graphical Gparted for partitioning.  I'm afraid I'll mess up if it's just text....  Do you think there is a secure way I can partition my hard-drive for Ubuntu in advance of installation?  This is another thread that shows why I have such a complicated partition issue: [http://ubuntuforums.org/showthread.php?t=1844324](http://ubuntuforums.org/showthread.php?t=1844324)

And thank you beefheartvliet - this sounds like good advice.  I will definitely check out the live CD.  The main purpose I want Studio for is to record/edit/produce music, so Dream Studio sounds promising.  Yet another decision to mull over!

---

### Post by jejeman on 2011-12-01
Yes, you can boot livecd and use gparted to make partitions. But, ubuntu studio installer has also very easy partition manager. It has textual interface. It's not CLI.

---

### Post by beefheartvliet on 2011-12-02
Just make sure you have about 20 or 30 GB to spare, The Ubuntu installer will detect you other operating system(s) and allow you to install alongside Windows etc
Ubuntu will create two partitions on your hard drive. You do have an opportunity to elect how much space you give to Ubuntu.
It will create an EXT3 or 4 Partition. Think of this as  NTFS, that Windows uses. It will also create a Swap File. Usually this is about 2 or 3GB, I'm most probably gonna show a bit of ignorarance now, but I understand the swap file to be much like Windows Virtual Memory:lolflag:

I guessing the complicated Hard-drive structure is the following.
Your windows Partition
A recovery partition.
And then maybe a partition for storage.

The Installer will detect the hard-drive structure.
Windows will be on SDA and will show as having two partitions (assuming it has 7 on it)
a 100 Meg Partition and however much was/is allocated to windows.
Ubuntu can be installed alongside windows on SDA
The Recover partition Will most prob show as B (I'm only guessing by the way)
An your Backup/Storage Will also have a letter assigned to it.
I'm sure I'm right in saying that the installer tells you its ignoring them anyway.

Either way, the installer makes it none scary, It's not as daunting as you might think. Regardless as to whether you install Ubuntu Studio or Dream. 

Once you are up and running, you will need to understand Jack. It's dead simple. Just think of it as ins and outs on a patch bay :-)

---

