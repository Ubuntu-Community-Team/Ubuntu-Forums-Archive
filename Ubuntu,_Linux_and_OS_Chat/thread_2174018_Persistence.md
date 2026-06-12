---
title: "Persistence"
date: 2013-09-12
forum: Ubuntu, Linux and OS Chat
---

### Post by sterlingbutters on 2013-09-12
I have a question regarding persistence, where changes are saved to a burned iso. I use BackTrack 5 which is Ubuntu based and my question is: Can persistence be created directly on the iso, or must it be burned to a destination first. The reason I ask, is I have a VM created to boot from a disc image which I have stored on my computer but I would like to apply persistence to it. Also BackTrack 5 has the install icon on the desktop and I was wondering if it installs all changes made with persistence or if it just installs the basic/original iso.

---

### Post by ajgreeny on 2013-09-12
Persistence is set up at the time you make the USB live system from the iso file, and can be done either using the ubuntu startup-disk-creator or unetbootin.  To my knowledge it is not something that can be added directly to the iso image file, though I could be wrong about that.  A live system with persistence has a separate file named casper-rw of up to 4GB on the fat32 partition that the live system is on.  If you want to get more adventurous you can use a separate ext4 partition with a single file on it named casper-rw, but I will have to let you research that more fully as it is something I know nothing more about.

Whether this answers your question I'm not sure as I do not fully understand what exactly you want, nor why you want it.

---

### Post by sterlingbutters on 2013-09-12
Any tips on what I should look for, like key words, if i wanted to find out if I could apply persistence directly to an iso? Also, did you have any input on the second part of the question? I suppose that in order to answer it, you would need to be familiar will BackTrack 5... Also, an after thought, is there any possible way to make changes to an OS and then convert all system files and settings into a bootable iso? If so, that would work just as good.

---

### Post by C.S.Cameron on 2013-09-12
Welcome to the Forums.

Ubuntu based "Live" images will grab the first casper-rw file or partition they find when booting up to use as persistence.
If you include a casper-rw file in your iso, the O/S should read the information in the file.
I don't think new information will be written to the casper-rw file when you log off, if the file is contained in the iso.

Perhaps someone else might know where to locate a file or partition that will be seen by a VM iso when booting.

Persistence is not used when burning an iso to disk.

Edit:
If you put an ext2,3 or 4 partition on your hard drive, or flash drive then you can get persistence when booting a Live CD or USB and press F6 then type <space>persistent, ```
 persistent
``` ,

---

### Post by sterlingbutters on 2013-09-12
So as for my other question: There is no way to create an iso from an existing operating system that contains all settings and files, etc?

---

### Post by mastablasta on 2013-09-13
to create and iso from existing OS you can use remastersys or (the fork) system imaging: [http://system-imaging.blogspot.com/](http://system-imaging.blogspot.com/)

---

### Post by sudodus on 2013-09-13
Why do you want persistence in a CD or iso file? Or should I ask:

- Do you want to store files and changes to the system almost like in a normal installed system? This the what a persistent live system is meant to do as explained by ajgreeny and C.S.Cameron.

- Or do you want the change your backtrack system (make some tweaks) and then keep it that way? Then remastering as described by mastablasta would be the way to go.

- There is also the alternative to make a USB boot drive with an installed system, installed in the same way as to an internal hard disk drive, but to a USB pendrive.

---

### Post by sterlingbutters on 2013-09-13
Since I use a Macbook pro, for hardware to work correctly, I have to install lucid/pommed drivers every time and ideally, I would like to create a bootable iso that contains the drivers AS WELL AS the ability to click the install file on the desktop and have THOSE SAME DRIVERS INSTALLED to a partition or hard drive. I am exploring possibilities but that would be ideal.

---

### Post by sudodus on 2013-09-13
Does the Macbook pro boot from a USB drive? In that case a persistent USB drive might be a good idea. Otherwise you can try according to the 'edit' in post #4 by C.S.Cameron: put a partition with the label casper-rw on a HDD or USB pendrive and boot with the boot option persistent from the CD.

---

