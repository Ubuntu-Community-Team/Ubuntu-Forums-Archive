---
title: "This should be easy to fix"
date: 2008-06-29
forum: Windows
---

### Post by megamoo on 2008-06-29
I have Windows xp on one sata drive and Ubuntu on a second sata drive with a third sata drive as storage.  When I boot into Ubuntu it sees and can access all drives, but Windows doesn't recognize the Ubuntu drive and tries to launch the `install new hardware` wizard every time. Starting to bug me.   
Is this a windows problem??  Windows had no trouble seeing the drive before I installed Ubuntu.  
I am new to Ubuntu in the last five days so any help will need to be simplified.:???:

---

### Post by pastalavista on 2008-06-29
This may help...

[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

---

### Post by bossa on 2008-06-29
I use this [http://www.fs-driver.org/](http://www.fs-driver.org/)  works well
Hope this helps

---

### Post by megamoo on 2008-06-30
Thanks pastalavista that program helps for accessing files.

I really want to have windows stop trying to install new hardware everytime it boots.  I have been clicking cancel on the windows `search for drivers for new hardware` thing...  maybe i should let it search and install.  Don't want it to fuss with linux though.  Its not really a problem for this forum and its not a big problem anyway.

Now if only I can get ubuntu to play music I will not abandon it and return to windows.  :rolleyes:  (i have posted this problem elsewhere no need to reply)

---

### Post by rockface on 2008-06-30
> **megamoo said:**
> Thanks pastalavista that program helps for accessing files.

I really want to have windows stop trying to install new hardware everytime it boots.  I have been clicking cancel on the windows `search for drivers for new hardware` thing...  maybe i should let it search and install.  Don't want it to fuss with linux though.  Its not really a problem for this forum and its not a big problem anyway.

Now if only I can get ubuntu to play music I will not abandon it and return to windows.  :rolleyes:  (i have posted this problem elsewhere no need to reply)

I know you said 'no reply' but can you post a link to the thread?

---

### Post by mips on 2008-06-30
> **megamoo said:**
> 
I really want to have windows stop trying to install new hardware everytime it boots.  I have been clicking cancel on the windows `search for drivers for new hardware` thing...  maybe i should let it search and install. 

It wont find anything when searching.

Look at the link bossa provided and install the Ext2IFS driver for windows, this will cure your problem.

---

### Post by stinger30au on 2008-06-30
[http://ext2fsd.sourceforge.net/projects/projects.htm#ext2fsd](http://ext2fsd.sourceforge.net/projects/projects.htm#ext2fsd)


this will let windows access the linux partitions as well

---

### Post by rickyjones on 2008-07-01
Sounds like Windows is trying to install the low level driver for the SATA disk. Not for accessing the file systems.

You should be just fine with letting it detect and install the disk. It may pop up saying that it cannot read it and needs to be formatted. Just say NO to that and it won't prompt again.

Sincerely,
Richard

---

### Post by megamoo on 2008-07-02
Ok I installed the Ext2 IFS driver and the Linux partitions now show up in My Computer and can be accessed etc..   Thanks bossa and mips problem solved.=D>
Windows Device manager still question marks the hard drive but that's not my problem, the annoying Found New Hardware wizard is gone.  
  
rockface the thread is Comprehensive Sound Problem Solutions Guide  [http://ubuntuforums.org/showthread.php?p=5284449#post5284449](http://ubuntuforums.org/showthread.php?p=5284449#post5284449)

My problem in short is there's no Ubuntu support for my particular Creative X-Fi soundcard and the workarounds I've been directed to do not work :( at least I can't get them to work.  The terminal is a complete foreign language to me so if its not S P E L L E D out on an infant level I'm not going to get it. 
If you know of a solution feel free...

---

### Post by bossa on 2008-07-02
> **megamoo said:**
> Ok I installed the Ext2 IFS driver and the Linux partitions now show up in My Computer and can be accessed etc..   Thanks bossa and mips problem solved.=D>
Windows Device manager still question marks the hard drive but that's not my problem, the annoying Found New Hardware wizard is gone.  
  
rockface the thread is Comprehensive Sound Problem Solutions Guide  [http://ubuntuforums.org/showthread.php?p=5284449#post5284449](http://ubuntuforums.org/showthread.php?p=5284449#post5284449)

My problem in short is there's no Ubuntu support for my particular Creative X-Fi soundcard and the workarounds I've been directed to do not work :( at least I can't get them to work.  The terminal is a complete foreign language to me so if its not S P E L L E D out on an infant level I'm not going to get it. 
If you know of a solution feel free...

Dont know if this is the thread you used ,but some people with the same card have had some success look near the end of the thread .

[http://ubuntuforums.org/showthread.php?t=239981](http://ubuntuforums.org/showthread.php?t=239981)

Dont be afraid to ask about terminal ,some one will help ;)

---

### Post by MaxIBoy on 2008-07-03
Get a second opinion about every command someone tells you to put in the terminal. Some people have posted harmful commands as a "prank."

---

### Post by LaRoza on 2008-07-05
> **MaxIBoy said:**
> Get a second opinion about every command someone tells you to put in the terminal. Some people have posted harmful commands as a "prank."

Well, everyone command you have no clue what it does ;)

If someone tells you to run "sudo apt-get update", there is little mystery for most people what is going on, but if "scrot" is the command, which is less known, it can be worth checking the man page or asking (scrot takes a screenshot)

---

### Post by macnyak on 2008-07-06
For my opinion Ubuntu and Windows uses different FILE FORMAT,.. and Partition methods I guess,..



Windows can be installed on a hard drive with FAT32 or NTFS format 

for Ubuntu I dont really know at all,.. but Ubuntu can be installed in a hard drive that formatted in FAT32,..

for my experience I once installed Kubuntu 7.0,.. it cannot open my hard drive with NTFS format

I dont know today if its possible to open NTFS formats with Ubuntu or Kubuntu

---

