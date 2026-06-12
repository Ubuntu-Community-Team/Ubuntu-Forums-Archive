---
title: "Failling to upgrade to 12.10 from 12.04lts"
date: 2012-09-23
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Drefhill on 2012-09-23
Hello
It wated to install the new 12.10 version from the 12.04LTS.
But the computer went to sleep during the installation and with linux the sleeping mode never work so it froze everything and the upgrade coundun't finish correctly.
When i restarted the computer i got a black screen after the Ubuntu loading screen.
I did a couple o command but nothing had fixed the problem i still with the black screen.
```
sudo apt-get update
``````
sudo apt-get install -f
``````
sudo dpkg --configure -a
``````
sudo apt-get dist-upgrade
``````
sudo service lightdm restart
```etc.... but i still with the black screen

and now i can't even open a terminal i get the following error
```
mountall: La commande de Plymouth a échoué 
mountall: Déconnecté de Plymouth
```How can i fix this ?

---

### Post by darkod on 2012-09-23
There is no "new 12.10 version". It's still not released.

If you forced it to upgrade to a development release, even if the upgrade finished not always it works properly and should be done only for testing.

Are you doing this for testing or this is your main system?

---

### Post by Drefhill on 2012-09-23
It's my laptop, i have a desktop also.
And i know that it's only for testin, but i want to fix it..

---

### Post by Alecossy on 2012-09-23
I'm having the same problem... using the recovery mode is totally useless as it always gets stuck at fsck..
I think the only solution would be to run a bootable disk, save our files and re-install... then try the update again...

---

### Post by darkod on 2012-09-24
> **Drefhill said:**
> It's my laptop, i have a desktop also.
And i know that it's only for testin, but i want to fix it..

If you are running the command you posted in recovery mode with the root partition mounted as read/write (make sure it's not read/only) then I am not aware of other commands to try and fix a broken upgrade.

I guess it's not ready yet.

Also, you should discuss the current development release in the Ubuntu+1 section of the forum, some of the people working on it actually read the threads there while they don't visit this section.

So, we are talking about development release, go to Ubuntu+1.

---

### Post by Drefhill on 2012-09-24
> **Alecossy said:**
> I think the only solution would be to run a bootable disk, save our files and **[COLOR=Red]re-install[/COLOR]**... then try the update again...
That's what i don't wanna do.
It must have an other solution to remake the starting part.
Maybe with the help of an USBlive.
Reinstall the grub or lightdm or something else.

> **darkod said:**
> If you are running the command you posted in  recovery mode with the root partition mounted as read/write (make sure  it's not read/only)
How can i know if it's in read/write or only read ?

---

### Post by Drefhill on 2012-09-24
to erase

---

### Post by darkod on 2012-09-25
If you select recovery mode and in the menu that shows select Drop to root shell, that mount the root partition in read only.

It's best to select from the menu first Network, so that it activates internet and at the same time mount root in read/write, and then Drop to root shell.

---

### Post by nothingspecial on 2012-09-25
*Thread moved to **Ubuntu +1 (Quantal Quetzal)**.*

---

### Post by Drefhill on 2012-09-25
> **darkod said:**
> If you select recovery mode and in the menu that shows select Drop to root shell, that mount the root partition in read only.

It's best to select from the menu first Network, so that it activates internet and at the same time mount root in read/write, and then Drop to root shell.
I can acces to the terminal by pressing Ctrl + Alt +F1

If i load the GRUB and choose "network"
[[IMG]http://img6.imagebanana.com/img/d5mlgd8d/thumb/DSC04273.JPG[/IMG]]("http://www.imagebanana.com/view/d5mlgd8d/DSC04273.JPG")

then i get this and i can't quit, it stay like that.
[]("http://www.imagebanana.com/view/kg56gop0/DSC04274.JPG")[[IMG]http://img6.imagebanana.com/img/3wc2x0hm/thumb/DSC04275.JPG[/IMG]](http://www.imagebanana.com/view/3wc2x0hm/DSC04275.JPG)
[IMG]http://imm.io/FEnH[/IMG]

---

### Post by cariboo on 2012-09-25
Are you sure the fsck problem is related to your upgrade problem? Have you booted from a Live CD and run fsck on the partition you are having the problem with?

---

### Post by Drefhill on 2012-09-26
I'm not sure if it's related but before i make the update everything (if we forget all the habituals problems) were working well and now nothing.
I booted from an USB drive and i don't find how to lunch fsck from the USb drive.

---

### Post by Drefhill on 2012-09-27
up

---

### Post by cariboo on 2012-09-27
> **Drefhill said:**
> I'm not sure if it's related but before i make the update everything (if we forget all the habituals problems) were working well and now nothing.
I booted from an USB drive and i don't find how to lunch fsck from the USb drive.

Open a terminal, and type:

```
sudo fsck -y /dev/sda1
```

OF course substitute the partition in the command above, for the one you're having a problem with.

For more command options, see:

```
man fsck
```

---

### Post by Drefhill on 2012-09-28
it just take like half a second and it just say that it's clean.

---

### Post by Drefhill on 2012-09-29
message to be erased.

I can't find how to do it.

---

### Post by Drefhill on 2012-09-30
up

---

### Post by cariboo on 2012-09-30
HAve you tried using nomodeset to get to a desktop, at the grub menu press ***e***, and add nomodeset to the end of the kernel line. If that doesn't work. try removing quiet and splash from the kernel line.

---

### Post by jerrylamos on 2012-10-01
> **Drefhill said:**
> That's what i don't wanna do.
It must have an other solution to remake the starting part.
Maybe with the help of an USBlive.
Reinstall the grub or lightdm or something else.


How can i know if it's in read/write or only read ?
In development release, expect to install often and have backup partitions.  Updates do crap out.  We learn a lot of linux dealing with the wreckage.  A few of the bugs I enter into Launchpad get fixed, some go away with updates, some are ignored and I have to do workarounds. Beta 2 is worse on wireless WPA and TV monitor support.  Despite bugs entered, I think Ubuntu is far more interested in dumping in fancy features I don't use.  I run Beta2 looking for bugs then boot 12.04 2D to get some work done faster.

---

### Post by Drefhill on 2012-10-01
> **cariboo907 said:**
> HAve you tried using nomodeset to get to a desktop, at the grub menu press ***e***, and add nomodeset to the end of the kernel line. If that doesn't work. try removing quiet and splash from the kernel line.
How can i get to the GRUB ? I only get it randomly once in a while.

---

### Post by wojox on 2012-10-01
> **Drefhill said:**
> How can i get to the GRUB ? I only get it randomly once in a while.

Reboot and hold down the left shift key.

---

### Post by Drefhill on 2012-10-01
> **cariboo907 said:**
> HAve you tried using nomodeset to get to a desktop, at the grub menu press ***e***, and add nomodeset to the end of the kernel line. If that doesn't work. try removing quiet and splash from the kernel line.
Like this ? and then i press F10 to start  ? It doesn't work, it say "impossible to find the command  nomodeset"
[[IMG]http://pix.toile-libre.org/upload/img/1349127322.jpg[/IMG]]("http://pix.toile-libre.org/?img=1349127322.jpg")

If i remove quiet and splash it just open a terminal asking my login

---

### Post by wojox on 2012-10-01
[How to set NOMODESET and other kernel boot options in grub2]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by cariboo on 2012-10-01
> **Drefhill said:**
> Like this ? and then i press F10 to start  ? It doesn't work, it say "impossible to find the command  nomodeset"
<snip>

If i remove quiet and splash it just open a terminal asking my login

Can you start the desktop from the prompt with the:

```
startx
```

command?

---

### Post by Drefhill on 2012-10-03
i deleted **$vt_handoff** and replaced by **nomodeset**
and then pressed Ctrl + X  or tryed olso with F10
i get this low resolution screen and it doesn't go further, usualy after that i get a black screen but with this command i don't get the black screen.
[[IMG]http://pix.toile-libre.org/upload/img/1349308732.jpg[/IMG]]("http://pix.toile-libre.org/?img=1349308732.jpg")

If i tipe startx in the terminal i get this fatal error[IMG]http://i.minus.com/j91hLylAHBy1m.jpg[/IMG]
[IMG]http://minus.com/l91hLylAHBy1m[/IMG]
[[IMG]http://pix.toile-libre.org/upload/img/1349309246.jpg[/IMG]]("http://pix.toile-libre.org/?img=1349309246.jpg")

---

### Post by techvish81 on 2012-10-04
your system is already broken, you should take a bit risk and try to upgrade through installation disk.  upgrade option is active in the beta2 desktop, I successfully upgraded my 12.04 system that way and it is working flawlessly.

---

### Post by Drefhill on 2012-10-04
are you sure of what you say? because of i think that my system is allready upgraded at 12.10, so i don't think that getting an upgrade from a DVD probably older will change anything.

What do you mean by "Beta2 desktop ?"

---

### Post by dino99 on 2012-10-04
at grub menu, choose the recovery mode, then select "repair" (dont remember exactly what is written, might be the second line)

---

### Post by Drefhill on 2012-10-05
> **dino99 said:**
> at grub menu, choose the recovery mode, then select "repair" (dont remember exactly what is written, might be the second line)
and then which option ? I have 9 options.
You can see them here in the message #10 [http://ubuntuforums.org/showpost.php?p=12260994&postcount=10](http://ubuntuforums.org/showpost.php?p=12260994&postcount=10)

---

### Post by Drefhill on 2012-10-06
> **techvish81 said:**
> try to upgrade through installation disk.  upgrade option is active in the beta2 desktop, I successfully upgraded my 12.04 system that way and it is working flawlessly.
It says that Ubuntu 12.10 Quantal is allready present on the computer and ask me to install it beside, not to upgrade.
And i can just "try Ubuntu whithout installing" or "Install Ubuntu", i can not "Repair"

---

### Post by cariboo on 2012-10-06
> **Drefhill said:**
> It says that Ubuntu 12.10 Quantal is allready present on the computer and ask me to install it beside, not to upgrade.
And i can just "try Ubuntu whithout installing" or "Install Ubuntu", i can not "Repair"

It might be best to do a reinstall, as your system is broken any how, If you have your partitions already set up, you may want to use the ***Something else*** option when it comes to the partitioning section, this is especially helpful, if you have a separate /home partition.

---

### Post by Drefhill on 2012-10-07
> **Drefhill said:**
> If i tipe startx in the terminal i get this fatal error[IMG]http://i.minus.com/j91hLylAHBy1m.jpg[/IMG]

I think that there is something to do with this error.
[http://wiki.x.org/wiki/](http://wiki.x.org/wiki/)

---

