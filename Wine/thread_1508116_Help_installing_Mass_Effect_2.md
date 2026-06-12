---
title: "Help installing Mass Effect 2"
date: 2010-06-12
forum: Wine
---

### Post by chromatica86 on 2010-06-12
So i'm trying to get it installed with playonlinux.
All goes well until it's time to insert the second disc. I can't for the life of me get the second disk running with the installation.
I've searched far and wide for this answer but can't find it. Please help.

---

### Post by chromatica86 on 2010-06-12
So nobody know how to install multi disc games???:confused:


I am very sad now. Should have just bought the game for xbox, but I didn't now vista was going to go haywire.

---

### Post by ucal on 2010-06-12
> **chromatica86 said:**
> So nobody know how to install multi disc games???:confused:


I am very sad now. Should have just bought the game for xbox, but I didn't now vista was going to go haywire.

Ah, but with the xbox you don't get the joys of a community of saves, so you don't have to play through the first mass effect a thousand times >_>.  When ME3 comes out, I'm probably going to have to buy it for 360 so I won't have access to that community ;_;

You might want to try just wine.  Play on linux is based on wine, but I think wine has more tricks you can apply to get it running.  It got a silver rating on wineHQ.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=11010](http://appdb.winehq.org/objectManager.php?sClass=application&iId=11010)

There are specific tricks listed within the various ratings.

---

### Post by cogadh on 2010-06-12
> **chromatica86 said:**
> So nobody know how to install multi disc games???:confused:


I am very sad now. Should have just bought the game for xbox, but I didn't now vista was going to go haywire.

You need to be a bit more patient and wait at least 24 hours before giving up on getting some kind of response. It can often take at least that long before someone even bothers to read a new thread.

As for your problem, ucal was on the right track. Skip using the POL frontend for Wine and just use Wine as it is. When you get to the point where you need to swap disks, open a terminal and run "wine eject d:" (assuming your CD/DVD drive is defined as "D:" in Wine) to take out the old disk and insert the new. Make sure you do not have anything like the file browser open in the disk, that will prevent it from working.

---

### Post by chromatica86 on 2010-06-12
Ok thanks guys. I guess I'll try it just with wine then.
POL just makes things a little easier.

---

### Post by chromatica86 on 2010-06-19
I actually still can't seem to get this game installed.
Whether I use wine alone or use POL. Once the first disc is ejected, I can't get the installer to read the second disc.

---

### Post by ev0x on 2010-06-20
Try this:
mount -o loop me2-1.iso /media/cdrom
wine start /unix /media/cdrom/Setup.exe

Then when asks for the 2nd disk:
umount /media/cdrom
mount -o loop me2-2.iso /media/cdrom

Then continue :) let me know if it works I just did it and it worked fine

---

### Post by ev0x on 2010-06-20
> **ev0x said:**
> Try this:
mount -o loop me2-1.iso /media/cdrom
wine start /unix /media/cdrom/Setup.exe

Then when asks for the 2nd disk:
umount /media/cdrom
mount -o loop me2-2.iso /media/cdrom

Then continue :) let me know if it works I just did it and it worked fine


Actually that one didn't work but this did:
sudo mkdir /media/me
sudo mount -o loop me2-1.iso /media/me

CHECK THIS:
make sure your winecfg does NOT have the mount location because wine  eject does not work on ISO's correctly are it will not pick up the 2nd disk when you unmount it, then do:

wine start /unix /media/me/Setup.exe

When it asks for the 2nd disk do:
sudo umount -f -l /media/me
sudo mount -o loop me2-2.iso /media/me

Then click OK or whatever it says.

You will be off flying ;)

---

### Post by chromatica86 on 2010-06-20
> **ev0x said:**
> Actually that one didn't work but this did:
sudo mkdir /media/me
sudo mount -o loop me2-1.iso /media/me

CHECK THIS:
make sure your winecfg does NOT have the mount location because wine  eject does not work on ISO's correctly are it will not pick up the 2nd disk when you unmount it, then do:

wine start /unix /media/me/Setup.exe

When it asks for the 2nd disk do:
sudo umount -f -l /media/me
sudo mount -o loop me2-2.iso /media/me

Then click OK or whatever it says.

You will be off flying ;)


I tried it but I get this message

me2-1.iso: No such file or directory

I am using the dvds. Do I need to copy them and make iso's out of them??

---

### Post by ev0x on 2010-06-26
copy only the 2nd disk and make the iso image

---

### Post by brokenbynubs on 2010-07-16
Bump.

I have this exact same issue, creating an iso didn't work at all.

---

### Post by chromatica86 on 2010-07-17
> **brokenbynubs said:**
> Bump.

I have this exact same issue, creating an iso didn't work at all.

I'm now using wine 1.2 and still can't get this game installed. I'm about ready to buy it through steam, but am questioning whether or now it will play.

---

### Post by chromatica86 on 2010-07-17
Also, I've successfully installed other games with 5 cds.
It's just mass effect 2 that the second disk will not load into the installer.

---

### Post by brokenbynubs on 2010-07-19
I too have installed many games with multiple CDs, IE - WoW, Age of Empires 3, Fallout 3 and so on.  After many days of frustration with this, I broke down and bought it for xBox 360.  An unfortunate solution, but it solved my problem.

---

### Post by chromatica86 on 2010-07-23
Well I bit the bullet and re-bought it for the 360. 
I still want to play it on pc though. So I'll continue looking for a solution.

---

### Post by asdfoo on 2010-07-23
installers with multiple cd's work perfectly fine here
just type `wine eject` at a terminal when it says to put the next cd in and it all goes smoothly.

---

### Post by chromatica86 on 2010-07-23
> **asdfoo said:**
> installers with multiple cd's work perfectly fine here
just type `wine eject` at a terminal when it says to put the next cd in and it all goes smoothly.

The wine eject does not work for mass effect 2. Like stated earlier, all other multi disc intalls have gone great. Just this one game that will not work.

---

### Post by cogadh on 2010-07-23
Are you leaving the file browser open on the disk when you try to swap disks? If so, that is your problem. Even using "wine eject" won't work if the file browser is still open. If that is not the case, then you might consider creating a valid fstab entry for your CD/DVD drive. That will create a fixed mount point that Wine can use as the "D:" drive (or whatever drive letter you use) instead of hoping that Wine can deal with the dynamically created mount points that Ubuntu normally uses.

---

### Post by chromatica86 on 2010-08-07
Well, my xbox just kicked the bucket. So i'm back to square one trying to get this running with ubuntu.
I'm not sure how to create an fstab, but I'll look it up now.

---

### Post by thingyman on 2010-09-15
I just wanted to thank ev0x for his help in the thread, the mounting method worked perfectly for me.

---

