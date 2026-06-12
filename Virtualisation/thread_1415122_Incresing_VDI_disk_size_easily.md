---
title: "Incresing VDI disk size easily"
date: 2010-02-24
forum: Virtualisation
---

### Post by clenched_sphere on 2010-02-24
Hi all.

I've run into a problem on my VirtualBox install of Windows XP Home, namely that I gave it a static 4GB drive which has very quickly run out of space.
After googling around to find out how you make it bigger, I found that most people seemed to use direct dump (dd) and other complex command line stuff to accomplish the task.

Eventually I decided to do it a slightly different way, worked well for me so I'm posting it here for anyone in the same situation.

To do this you need 3 things: a blank CD, an ISO of Clonezilla ([http://clonezilla.org/](http://clonezilla.org/)) and enough free disk space - namely the size of your too small VDI times 2.

Download the Clonezilla ISO and burn it to the CD. If you haven't used it before don't worry it's very easy.

Next, create a new virtual drive with VirtualBox. Make it the size you wanted the original to be, make sure you pick a dynamic drive unless you need a static one, this means the whole process will only use 2x the size of the smaller VDI. Creating a static drive would use up the original VDI's size + the size of the bigger one.

After you are done, assign both drives and your CD drive to your virtual machine, and tell it to only boot from CD.
Power it up (making sure the Clonezilla cd is in the drive) and just hit the defaults for most of the options. 
You want to select local drive --> local drive clone when it asks.
When selecting the source, pick the smaller drive, then pick the bigger new drive as the destination, and tell it to go ahead when it asks about 4 times.

Once this is done, you will have cloned your smaller drive to the new larger space. Only 2 things left to do - resize the partition in the larger drive to give it all the unallocated space, and delete the original drive (once you verify it worked).

As my virtual machine was XP, I booted it from an Ubuntu live cd courtesy of Linux Format and used Gparted to resize the new disk's partition to use all available space. After that, I removed the smaller drive from the virtual machine and booted using the new drive. 

Everything worked nicely, so I deleted the original disk, and my little pet XP installation behaved itself.

This seems to me to be an easier way to do this than most of the ones I've seen, let me know if this works for you.

---

### Post by PatKam_AU on 2010-05-23
I have a easier way to "increase vdi size" of a Windows VM.

I have done screen shots for step by step, joining them via simple html codes.

[http://rapidshare.com/files/390892218/VirtualBox_HDD_Resize_InstructionsOnly.zip](http://rapidshare.com/files/390892218/VirtualBox_HDD_Resize_InstructionsOnly.zip)

:)

---

### Post by clenched_sphere on 2010-05-24
> **PatKam_AU said:**
> I have a easier way to "increase vdi size" of a Windows VM.

I have done screen shots for step by step, joining them via simple html codes.

[http://rapidshare.com/files/390892218/VirtualBox_HDD_Resize_InstructionsOnly.zip](http://rapidshare.com/files/390892218/VirtualBox_HDD_Resize_InstructionsOnly.zip)

:)


this is a little easier, yes.
but, fail for using rapidshare. better to describe each step imho, or host the imags on photobucket or similar.

thanks
alan

---

### Post by riph72 on 2010-05-25
Something I thought of to avoid this is to create a 2Tb **dynamic** drive (my physical drive is only 120Gb) and let the VM expand as needed.  Initially I expect it to just use a few Gb following installation, even though it thinks it has access to 2Tb.  I'd monitor it to make sure it doesn't gobble up too much real space.
 
Can anyone see a drawback with this approach?
 
Cheers,
Richard.

---

### Post by clenched_sphere on 2010-05-28
> **riph72 said:**
> Something I thought of to avoid this is to create a 2Tb **dynamic** drive (my physical drive is only 120Gb) and let the VM expand as needed.  Initially I expect it to just use a few Gb following installation, even though it thinks it has access to 2Tb.  I'd monitor it to make sure it doesn't gobble up too much real space.
 
Can anyone see a drawback with this approach?
 
Cheers,
Richard.


Hi Richard,
the issue I see with this is that it is possible for the dynamic drive to gobble up all your available space.
Dynamic drives are better because they don't immediately use all the space you allocate to them, but there is no real reason to allocate more space than you actually have.

I'd suggest you assign an absolute maximum of 100GB to your dynamic drive, in order to make sure it doesn't eat up all your available disk space while thinking there is more.

To be honest, depending on the requirements of the OS you are going to install, 10GB is usually more than enough for a basic install.

My original post was really about solving the problem of not having enough space once you had already created a drive that is too small, and installed your OS to it. 
Fortunately, as I assume you haven't actually started yet, you are in a good position to avoid the issue completely :D

Good luck
Alan

---

### Post by riph72 on 2010-05-28
I'm only really playing about with VirtualBox at the moment, so I've followed the dynamic 2Tb route.  WinXP is currently using 6Gb or thereabouts, I'll monitor things and see how it goes though!

Although in theory it can gobble up all my hard-drive, unless I go installing lots of stuff etc, I don't see why it would.  At least this way, hopefully I'll never be in the position where I wish I'd made it bigger in the beginning... and if the 2Tb thing proves to be a mistake, I'll probably just start again  :)

---

