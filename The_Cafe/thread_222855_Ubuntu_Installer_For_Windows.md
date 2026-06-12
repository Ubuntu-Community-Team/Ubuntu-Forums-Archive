---
title: "Ubuntu Installer For Windows?"
date: 2006-07-25
forum: The Cafe
---

### Post by Johnsie on 2006-07-25
Would it be possble to have an exectuable Ubuntu installer for Windows? So curious windows users woudn't need to download and burn and iso?

---

### Post by T700 on 2006-07-25
I doubt it, as the whole idea of the ISO image is that the OS is started *instead* of Windows.  

Paul

---

### Post by Brunellus on 2006-07-25
it would have to

1) install itself
2) install an iso burning app
3) get the ubuntu iso (hopefully via something like bittorrent or whatever windows' equivalent to wget is)
4) prompt the user to insert a blank disc
5) burn the disc and verify same.

Shouldn't be too complex...eh?

---

### Post by BuffaloX on 2006-07-25
Good idea, but I guess it would be too much work.

It could be possible, if Microsoft wasn't so keen on protecting their inferior technology through patents and secrecy.

One problem is NTFS, which is default format for XP systems.
If the installation should be from windows, it would mean that all programs needed by the installer should be ported to Windows.

---

### Post by Brunellus on 2006-07-25
I think most users can get the "put the CD in the drive and boot the computer" step.  But many newbies have problems understanding what an iso is and what to do with it.  

The intermediate step would be a windows "installer" step that would do what I've outlined above.

---

### Post by BuffaloX on 2006-07-25
> **Brunellus said:**
> I think most users can get the "put the CD in the drive and boot the computer" step.  But many newbies have problems understanding what an iso is and what to do with it.  

The intermediate step would be a windows "installer" step that would do what I've outlined above.

I agree.

---

### Post by Mathiasdm on 2006-07-25
I think the original poster means another type of .exe.
You start the .exe, you press next a couple of time. The installer prompts: "Please restart the computer, and select 'Ubuntu' at start-up."

And then Ubuntu would be installed.

I could be wrong, of course. ;) 
Seeing as some people don't know how to set their BIOS to first boot a CD-ROM, it might be useful.

---

### Post by Brunellus on 2006-07-25
plus, the satisfaction of making windows dig its own grave is its own reward.

---

### Post by DoktorSeven on 2006-07-25
[http://www.vmware.com/](http://www.vmware.com/) ?

:)

---

### Post by Johnsie on 2006-07-25
Matt got what i meant...

It would do all the installing/partioning from within windows just by clicking an .exe ..... And then when you reboot you have a dual boot system. There might be a major flaw in that though... Is it possible to re-partition an already mounted drive? I don't really know enough about this.

Ideally this way would mean that you wouln't need to have  or burn an iso as it would be doing everything from the internet and hard disk.

I just think this would make it simpler for Windows users to migrate to ubuntu without needing to learn about ISO's, setting the bios to boot from cd etc...

Basically the program would just be like the GIU installer that runs on the Desktop cd only it could run on Windows. You double click the exe, say how much HDD space you want to give to Ubuntu wait a while for installation to happen and hey presto, you have a dual boot system with very little effort.

Phat Linux did this but it  made both operating systems share the same file system. I'd rather it repartitioned the drive as per a normal dual boot Ubuntu& Windows computer.

---

### Post by TravisNewman on 2006-07-26
or extending this... download an exe and get a blank disk in your drive

Double click "Install_Ubuntu_<version>.exe"
It asks you time zone questions, user/password questions, partitioning questions... basically everything it would ask during intiial setup.
It burns a cd that will automatically do everything you want it to. No interaction at all.

---

### Post by Johnsie on 2006-07-26
Hmmm.... i think we're getting close there... How about this? (it's the lazy mans approach)


1. User double clicks Ubuntu_Installer.exe
2. Asks the user whether they want a liveCD or a Desktop CD
3. Ubuntu installer.exe downloads requred Ubuntu ISO
4. Ubuntu Installer.exe tells user to put the cd in
4. Burns the cd from the ISO
5. Displays a message telling the User how to set the bios to boot from CD (also saves a txt file with these instructions on the desktop) and telling the user to reboot to conitnue installation.
6. The  Cd is just a standard Ubuntu instaltion cd so user can do all partitioning etc using the install cd.

That way the user would be able to get around the learning curve of of being introducted to ISO's. , which may seem simple and strightforward to us but can be confusing and scary for many less computer literate people.


I do like my other idea though too... of not needing a cd at all.

---

