---
title: "Running DOS in a virtual machine from Ubuntu?!"
date: 2008-09-16
forum: Virtualisation
---

### Post by extruct on 2008-09-16
Hmm I think I'm the only idiot on the earth who wants to run DOS in virtual machine from Ubuntu..:-D

Anyway I need a pure DOS system to work with assembler. Since we are learning assembler for DOS in college and using TASM I need DOS. I tried to execute tasm from dosbox but as I understood Linux kernel uses different interrupt functions than DOS. I can of course boot inei WindowsXP any time when I need/want to program in assembler but I would like to try run DOS in a virtual machine from Ubuntu since its more conformable.

Anyone can guide me or point me to a guides/software to be able execute my evil pan :p

Thanks :)

---

### Post by Thelasko on 2008-09-16
Well, [VirtualBox]("http://www.virtualbox.org/wiki/Guest_OSes") says it supports DOS.  My question is where will you get a copy of DOS?  If you can't get a copy of DOS, there is always [FreeDOS]("http://en.wikipedia.org/wiki/FreeDOS").

Once you get VirtualBox/VMWare installed on your machine, you must install it in the VM like you would on a physical computer.  The only difference is, there are menus to mount .iso files etc. instead of physically putting a disk in the drive.

Just treat the VM as you would a physical machine and you should be fine.

P.S. In VirtualBox, since the guestadditions doesn't work in DOS you must press the right control button to get the mouse back.  I think it's ctrl+alt on VMWare.

---

### Post by UbuWu on 2008-09-16
Don't know if it satisfies your needs, but there is also dosbox, a dos emulator, in the repositories. It works perfect for playing most games, but I don't know if you could do assembler in it.

Running dos in a vm is also perfectly possible. Indeed the hardest part is probably obtaining a copy of dos, although it is available from many file sharing sites.

---

### Post by UbuWu on 2008-09-16
Here are some tips for setting up dos in a vm:
[http://forums.virtualbox.org/viewtopic.php?t=845](http://forums.virtualbox.org/viewtopic.php?t=845)

---

### Post by extruct on 2008-09-17
Well I was able to run FreeDOS in VirtualBox but I wasn't able to copy files from Linux to FreeDOS Virtual Hard Dist, therefore I couldn't copy TASM to program on assembler.

Anyone know how to copy files from Linux partition to a virtual FreeDOS partition?

Thanks.

---

### Post by lazyart on 2008-09-17
You might have to create a floppy disk image, then mount the image into the VM as a disk.  I'm not at my linux box now, but try this-

From Ubuntu terminal, type:```
dd bs=512 count=2880 if=/dev/zero of=floppy.img
mkfs.msdos floppy.img
```

That should create the disk.  Now mount it so you can add files to it:```

sudo mkdir /media/floppy1/
sudo mount -o loop floppy.img /media/floppy1/
```

Copy your files to /media/floppy1

Now in your VM console point your virtual floppy disk to floppy.img.

DIR in FreeDOS should show the files.

[Here]("http://untitledfinale.wordpress.com/2007/10/09/create-mount-and-copy-floppy-disks-images-under-linux/") is the source of my information.

---

### Post by Thelasko on 2008-09-17
> **lazyart said:**
> You might have to create a floppy disk image, then mount the image into the VM as a disk.
I think FreeDOS works with CD ROMs too.  So you could mount an ISO to transfer larger files.

---

### Post by Bladeforger on 2009-01-07
> **extruct said:**
> Hmm I think I'm the only idiot on the earth who wants to run DOS in virtual machine from Ubuntu..:-D


Naaaahhhhh, you're not the only one.  Me too!!
I found this thread and am going to try the links and info myself.

I spent half an hour today explaining to a friend why I had to be able to run this old DOS software.  It's Easy Accounting, and it works wonderfully.  It never loses data.  Financial statement formats don't disappear.  It doesn't have weird rounding problems.  It doesn't require annual updating (for a fee) to keep it from quitting.   It's pick-a-number menu old-fashioned; however, it's lightning fast in use.  I never found a Windows program to replace it--certainly not that Quickbooks junk.  

I can run it from Windows XP hosted via Win4Lin with less than stellar results.  At the other end of the spectrum I can figure out how to make the grub let me dual boot into DOS.  An ideal alternative is to boot the DOS environment from a virtual machine.  That's what I'll try to do.  (Wish me luck!)

> **Thelasko said:**
> Well, [VirtualBox]("http://www.virtualbox.org/wiki/Guest_OSes") says it supports DOS.  My question is where will you get a copy of DOS?  If you can't get a copy of DOS, there is always [FreeDOS]("http://en.wikipedia.org/wiki/FreeDOS").

DOS was, as it turned out, incredibly easy to find.  (It should have been in the right place in my software collection, but it wasn't.. That would have been the easiest.)

Anyway, I found it on ebay for less than 20 bucks, including shipping.  I doubt that there are unlimited quantities, but I only needed one of the several that were available.  FreeDOS might have worked, but by the time I get all the virtual part done having a modest investment in real DOS 6 isn't gonna kill me.

> **lazyart said:**
> You might have to create a floppy disk image, then mount the image into the VM as a disk. I'm not at my linux box now, but try this-

From Ubuntu terminal, type:```
dd bs=512 count=2880 if=/dev/zero of=floppy.img
mkfs.msdos floppy.img
```That should create the disk.  Now mount it so you can add files to it:```

sudo mkdir /media/floppy1/
sudo mount -o loop floppy.img /media/floppy1/
```Copy your files to /media/floppy1

Now in your VM console point your virtual floppy disk to floppy.img.

DIR in FreeDOS should show the files.

[Here]("http://untitledfinale.wordpress.com/2007/10/09/create-mount-and-copy-floppy-disks-images-under-linux/") is the source of my information.
Lazyart!  Thanks a bunch!  I'll have to read, reread, and read again but this helps!!!

---

### Post by Dedoimedo on 2009-01-08
Hello,

See if this helps you:
[http://www.dedoimedo.com/computers/dos.html](http://www.dedoimedo.com/computers/dos.html)

BTW, DOSBox does not work for you?

Dedoimedo

---

### Post by HermanAB on 2009-01-08
FreeDOS should have a FTP client.  So install Proftp on the host and then use FTP from the DOS command line to transfer files.

Cheers,

Herman

---

