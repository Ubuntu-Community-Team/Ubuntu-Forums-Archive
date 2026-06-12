---
title: "Give me a hand, I need a live USB distro."
date: 2010-06-04
forum: The Cafe
---

### Post by kaldor on 2010-06-04
I lent my mother a USB device, but she ended up losing it so I am left with a 1 GB USB stick. 

I need a distro that I can fit on 1 GB and carry with me anywhere so that I can save files to it and use it as if it were a "real" computer. 

I'd like a Debian installation on it, but how small can I go with that? I dislike Damn Small Linux though. Too outdated and doesn't do anything I want.

Any ideas? This is temporary anyway.

---

### Post by MasterNetra on 2010-06-04
Nevermind

---

### Post by snowpine on 2010-06-04
Ubuntu will fit OK on a 1gb USB stick. (You won't have a ton of room left over for your files, though.)

If you want something more minimalistic, check out Puppy (~100mb) or SliTaz (~30mb).

---

### Post by dragos240 on 2010-06-04
How about puppy. It's still being updated, and it's lightning fast. I don't know if it's debian based though....

---

### Post by Joe of loath on 2010-06-04
Puppy used to be based on slackware. It's pretty much its own distro now though, the latest version (5) is built from ubuntu packages.

I run puppy 4.31 on an intel celeron 433 w/ 256mb of RAM. It's great!

---

### Post by NightwishFan on 2010-06-04
I second puppy, I am unsure how to make a persistent live USB of Debian, but that would rock.

---

### Post by Simian Man on 2010-06-04
Isn't Wolvix, the first link in your signature, specifically suited for this task?

---

### Post by Joe of loath on 2010-06-04
I'm not sure it's been done yet. I'd imagine you could use the code from the ubuntu usb-creator program and fiddle it so it works with debian unstable.

---

### Post by NightwishFan on 2010-06-04
Perhaps this would work. I do not know.
[http://wiki.flimzy.com/index.php/Debian_on_USB_Quick_Install](http://wiki.flimzy.com/index.php/Debian_on_USB_Quick_Install)

---

### Post by pastalavista on 2010-06-04
[Unetbootin]("http://unetbootin.net/") will let you download and install many distros directly to a USB flash drive.

---

### Post by Megaptera on 2010-06-04
Loads of suggestions here too, I've used these guides with no probs:

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by kaldor on 2010-06-04
> **Simian Man said:**
> Isn't Wolvix, the first link in your signature, specifically suited for this task?

While wolvix is great, it has a bit too much stuff that I won't need and I don't want to waste time uninstalling too much. 

Puppy seems to be the winner so far, but keep going :)

---

### Post by sydbat on 2010-06-04
This might sound stupid, but...have you considered buying a larger USB stick (like 4, 8 or 16GB)? Then you wouldn't have the restrictions of the 1GB.

Or are you just looking for a challenge?

---

### Post by kaldor on 2010-06-04
No, my problem is that my other USB drive was lost. I only have a 1 GB available right now.

---

### Post by Chilli Bob on 2010-06-04
Puppy is the way to go.  It is small, fast and comes with just about any program you will need.  It includes the "puppy universal installer" which makes putting it on a USB stick a breeze, and is customised to run with minimal USB writes, to reduce wear on the flash RAM.

The latest version - Lucid Puppy - is based on Ubuntu packages, and anything in the Ubuntu repository can be added easily.

It's not Debian based though.  It's an original distro.


[http://puppylinux.org/news/petstests/lucid-puppy-from-woof-and-ubuntu-lucid-lynx-/](http://puppylinux.org/news/petstests/lucid-puppy-from-woof-and-ubuntu-lucid-lynx-/)

---

### Post by C.S.Cameron on 2010-06-04
Puppy 5 or NimbleX 2008.

---

### Post by Plumtreed on 2010-06-04
You could put Peppermint on it and have it persistent. 

Peppermint is a 'fork' of Lubuntu so is not big. It is also Mint/Ubuntu based so it will be easy to use and set up.

You really can't expect a lot from 1GB but I have it running on 2GB

....or even try Lubuntu!!!!

---

### Post by koolblue3 on 2010-06-04
+1 for Puppy. It is a great lightweight yet feature filled distro.

---

### Post by kaldor on 2010-06-04
Great luck today; my mother found my drive after 5 months of it being missing on the floor at work. Wow.

That being said, how do I make the Ubuntu install persistent? I don't want to go into "Try Ubuntu" each time I use it and not be able to save files.

---

### Post by Austin25 on 2010-06-04
Dsl + unetbootin
Will run on/off-of *anything*.

---

### Post by Plumtreed on 2010-06-04
@kaldor ....Use startup disk creator in Ubuntu, if you don't have it now simply download it from synaptics.

It will create a persistent live 'disk'

You should still check out Peppermint OS.......just google it.

---

### Post by mmix on 2010-06-04
slitaz + unetbootin

[http://www.slitaz.org/](http://www.slitaz.org/)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by snowpine on 2010-06-04
> **mmix said:**
> slitaz + unetbootin

[http://www.slitaz.org/](http://www.slitaz.org/)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Correction: SliTaz + TazUSB

[http://www.slitaz.org/en/doc/handbook/liveusb.html](http://www.slitaz.org/en/doc/handbook/liveusb.html)

More powerful and "persistent" than Unetbootin. :)

---

### Post by C.S.Cameron on 2010-06-05
To make a usb-creator install persistent using casper-rw partition:

Boot Live CD.
Plug in flash drive.
Start Partition Editor
Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional)
Create a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk / syslinux / text.cfg and added "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.
You are persistent.


To make an UNetbootin install persistent is similar except:
Run "gksu nauilus", open filesystem / cdrom and then open syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent

---

