---
title: "Running programs installed on windows from wine"
date: 2009-05-22
forum: Wine
---

### Post by Dracu@l on 2009-05-22
Is Running programs already installed on windows from wine possible? 
I keep on wondering about this because I am forced to dual boot to run too many programs
I would like to be able to run a Ubuntu only environment and let wine be the controller of the Vista partition on my harddrive, so that i could use my Vista when I'm in Ubuntu. 
anybody know how to or if its possible?

---

### Post by mrog on 2009-05-22
This doesn't exactly answer your question but I've never had a reliable experience with wine.

If your computer is reasonably new enough you could try VirtualBox. It's in the apt repositories and from virtualbox.org and is not a headache to get working.

It will also work in "seamless mode". Download the pdf documentation and start at page 59.

---

### Post by u235sentinel on 2009-05-22
> **Dracu@l said:**
> Is Running programs already installed on windows from wine possible? 
I keep on wondering about this because I am forced to dual boot to run too many programs
I would like to be able to run a Ubuntu only environment and let wine be the controller of the Vista partition on my harddrive, so that i could use my Vista when I'm in Ubuntu. 
anybody know how to or if its possible?

Depends on what you are running.  I've had a great experience with Wine which has allowed me to finally switch over to Linux for everything now.  I check winehq.com before purchasing windows applications.  anything below the Gold level isn't considered.  I still have a couple programs that just don't work under Wine (quickbooks pro for example) however it's great to be able to run stuff like Oblivion, CSS of TF2 under Linux.  

My kids love it :D

---

### Post by milton1 on 2009-05-22
If the program is a stand-alone executable, then yes, you can just point wine at that .exe and it will run. However, many windows programs require the use of different registry entries. When the program is installed, the appropriate registry entry is created or updated. Trying to run this program in wine will most likely not work, because the program's registry data is in your windows install, and wine is reading a registry file in your ~/.wine directory.

---

### Post by SlickRick on 2009-05-24
I've had luck running spore from a windows installation. Didn't have any registry problems what-so-ever. I just had to add my windows hard drive in the wine configuration.

Most games/applications should technically work from a windows partition/hard-drive if they work on wine anyway. The only problems you could come across is with registry but you can try exporting windows registry entries then importing them to the wine registry and changing the paths to point to the correct locations (depending on what you set the drive letter for the windows installation). However, this would be quite tedious. ;)

---

### Post by NightMKoder on 2009-05-24
Also, many things won't work. Wine expects to be run on an ext3 file system, so running it on ntfs will make it flip (sometimes). For a simple example, wine cannot use mmap on ntfs, so steam doesn't work.

---

### Post by SlickRick on 2009-05-24
i don't think that linux is as restrictive as windows and will recognise most filesystems. I'm running on ext4 and can't mount my linux partition on windows but can mount my windows partition on linux.

---

### Post by NightMKoder on 2009-05-24
> **SlickRick said:**
> i don't think that linux is as restrictive as windows and will recognise most filesystems. I'm running on ext4 and can't mount my linux partition on windows but can mount my windows partition on linux.

Linux recognizes more, but wine requires some advanced features that are only implemented for ext3/4. You can also get windows to recognize ext* by installing [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Dracu@l on 2009-05-26
well, i installed virtualbox. so.. im not really sure what to do now. 
Virtualbox needs a virtual harddrive, so i thought there was a possibility that i could make a virtual image of the vista partition, and see how that works. anyone know any good tools for making a good virtual image of the partition ?

---

### Post by asdfoo on 2009-05-26
> **Dracu@l said:**
> well, i installed virtualbox. so.. im not really sure what to do now. 
Virtualbox needs a virtual harddrive, so i thought there was a possibility that i could make a virtual image of the vista partition, and see how that works. anyone know any good tools for making a good virtual image of the partition ?

If your question isn't about Wine you should post in a different forum.

Wine works quite well, but you need to install applications in Wine, just as you would do if you were dual booting two different versions of Windows.

Aside from the matter of somehow destroying your Windows files by attempting to run things from there, it's not supported because the ntfs linux driver does not support the required features for executing files on that filesystem.

---

