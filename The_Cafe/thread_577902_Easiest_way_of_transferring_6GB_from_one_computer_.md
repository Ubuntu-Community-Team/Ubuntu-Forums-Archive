---
title: "Easiest way of transferring 6GB from one computer to another, then back?"
date: 2007-10-16
forum: The Cafe
---

### Post by Old Pink on 2007-10-16
Basically, I want to store the 5 to 6 Gigabytes in my laptop's hard drive temporarily elsewhere while I install a new 20GB hard drive before transferring it all onto that.

Only viable option seems to be putting it on the 80GB desktop temporarily. 

No CD drive, DVD drive, for reading or writing on the laptop. 

Ideas?

---

### Post by rfruth on 2007-10-16
A Thumb (USB) drive  ?

---

### Post by p_quarles on 2007-10-16
I'm working from the assumption that the 5 to 6 gigs is all or most of your home folder. 

On the desktop:
First, make a directory for the backup files in your home folder. Then,
```
sudo apt-get install openssh-server
```
On the laptop:
```
scp -r ~/username username@desktop-IP-address://~/username/backup_dir
```
Once you've got the laptop completely reconfigurded, get the files back by using scp again, only this time reverse the order of the two filepaths. 

Then you should probably remove the ssh server unless you need it for anything else.

---

### Post by Old Pink on 2007-10-16
No no, it's the whole /

Root. 5GB. On a 6GB hard drive. Hence the upgrade.

And thumb drive is a good idea, but I only have a 2GB, so it'd be at least 6 copy/pastes. Not too bad, I suppose. Might be quicker than wifi.

Samba seems slow whenever I've used it. Painful slow...

---

### Post by p_quarles on 2007-10-16
> **Old Pink said:**
> No no, it's the whole /

Root. 5GB. On a 6GB hard drive. Hence the upgrade.

And thumb drive is a good idea, but I only have a 2GB, so it'd be at least 6 copy/pastes. Not too bad, I suppose. Might be quicker than wifi.

Samba seems slow whenever I've used it. Painful slow...
Well, then just replace "~/username" with "/"

Seriously, scp is going to be the simplest way of doing this. Depending on how fast your wifi connection is, the thumb drive *might* be faster, but a 6 gig transfer would take about 12 minutes on my 54 mbps wifi connection. If your laptop has an ethernet jack, of course, that will be faster.

---

### Post by Old Pink on 2007-10-16
OK, thanks. 

So say I've got the 6GB stored on the desktop.

I take out my 6GB drive, insert my 20GB drive, but have no operating system. 

How do I then transfer to something with no operating system?

Will I need DSL or Puppy on a pen drive? Or not? 

With WiFi not working here, looks like thumb drive is the option for me. 

What's the best way to boot a Linux terminal from nothing? Bash on a pen drive, type of thing? Just need to mount, and mv or cp into / from the USB?

---

### Post by p_quarles on 2007-10-16
Duh. No operating system. I didn't even think of that. '](*,)

Yeah, you're going to need to boot up from a flash-drive version of LInux, and install the system before you do anything. Just copying the contents of the old hard drive won't work -- you won't have any formatted partitions to copy anything onto.

---

### Post by Old Pink on 2007-10-17
OK, here's the plan, help me find the flaws?

[LIST=1]
[*]Take everything off the laptop, onto the desktop, using two USB transfers (after cutting down to less than 4GB)
[*]Remove 6GB (old) drive
[*]Insert 20GB (new) drive
[*]Boot Feisty live CD using plug in CD drive (works, installed from it a while back)
[*]Format a partition & swap partition
[*]Take everything off the desktop and copy it onto the laptop using two more USB transfers.
[*]Reboot[/LIST]Now I understand I may need to configure GRUB or something in there? But if I'm not changing the MBR and /boot is in the same place it should be OK?

Anything else I need to do?

---

### Post by saulgoode on 2007-10-17
How can you **not** be changing the MBR if you have installed a new hard drive?

---

### Post by smoker on 2007-10-17
easiest way is to use an adapter cable like this:
[http://www.maplin.co.uk/Module.aspx?ModuleNo=28724&criteria=ide%20adapter&doy=17m10](http://www.maplin.co.uk/Module.aspx?ModuleNo=28724&criteria=ide%20adapter&doy=17m10)

slave your laptop drive to your pc, copy your drive with some image app, put your new drive on as a slave, and restore the image you copied, this should make your new drive as good as your old, except more space,

best of luck

---

### Post by ssam on 2007-10-17
as you will be opening up the laptop anyway a USB caddy would work. it is an enclosure with ide or sata on the inside and usb on the out side.

---

### Post by proalan on 2007-10-17
Best investments i've made is one of those portable usb harddrives without external power supply. Made things easier all those times i've had to install fresh OSes.

There was even a time i ran ubuntu from the usb harddrive.:guitar:

---

### Post by bigken on 2007-10-17
> **proalan said:**
> Best investments i've made is one of those portable usb harddrives without external power supply. Made things easier all those times i've had to install fresh OSes.

There was even a time i ran ubuntu from the usb harddrive.:guitar:

totally agree for the sake of about £8 then you also get an external usb hdd

---

### Post by popch on 2007-10-17
> **Old Pink said:**
> No no, it's the whole /

Root. 5GB. On a 6GB hard drive. Hence the upgrade.

And thumb drive is a good idea, but I only have a 2GB, so it'd be at least 6 copy/pastes. Not too bad, I suppose. Might be quicker than wifi.

Samba seems slow whenever I've used it. Painful slow...

If both computers have an ethernet interface, you can connect them with a crossed ethernet cable, if you have no bridge or hub. Much faster than Wifi.

BTW: I do not think that simply copying all of the contents of a disk drive to one of a different size will result in a ***bootable ***disk. I am, however, still a Linux novice, so I would like a second opinion on that.

---

### Post by notwen on 2007-10-17
> **popch said:**
> BTW: I do not think that simply copying all of the contents of a disk drive to one of a different size will result in a ***bootable ***disk. I am, however, still a Linux novice, so I would like a second opinion on that.

I don't believe this would work either, but I'm no expert either. =]

---

### Post by bigken on 2007-10-17
what you need to be looking for is some kind of cloning software have you tried google ?

---

### Post by Tom Mann on 2007-10-17
Have you considered using disk imaging?

Ghost4Linux (i think) or dd (if you're pro)

---

### Post by Old Pink on 2007-10-17
I've never used the ethernet ports on these computers though, no idea if they're working with Linux. 

I then just connect the two computers ethernet to ethernet and.... ? 

And why won't it be bootable? What if I do as I said before, put everything back on the 20GB, then reinstall/update GRUB?

And yeah, made a mistake about MBR.

---

### Post by Crashmaxx on 2007-10-17
Sounds like you mostly have a default Ubuntu install you're trying to save anyway. I'd just do a fresh install on the new hard drive.

The only stuff I'd bother keeping on the current install is a copy of /home, maybe /etc if you have custom settings there, and a list of installed packages.

Oh, and since Gutsy is coming out tomorrow, maybe you'd want to just wait and do a fresh install of that. A lot of people prefer that to upgrading anyway.

---

### Post by bigken on 2007-10-17
you could use APTonCD  do a clean install and then run the APTonCD :)

---

### Post by Old Pink on 2007-10-17
It's not a clean install.

Already using Gutsy RC.

Fresh install is awkward, need to download 700Mb of Gutsy alternate CD? No thanks.

Backing up onto the iPod now. Will then extract into root. Trust me, this will work. :)

---

### Post by bigken on 2007-10-17
I doubt it :(

---

### Post by pennygov on 2007-10-17
Read this about backup and restore using a tarball. It works. You would just install the same verstion of ubuntu on your new drive (it would install grub in your mbr). Then within your new install you can extract your tarball backup.

Here is the link: [http://ubuntuforums.org/showthread.php?t=35087&highlight=howto%3A+backup+restore+your+system](http://ubuntuforums.org/showthread.php?t=35087&highlight=howto%3A+backup+restore+your+system)

I guess you could use an ethernet connection between your desktop and your laptop to make the backup tar (think of your desktop as an external hd). If you can burn the backup tar on a cd (using your desktop?) you can then restore it (by extracting from the cd). 

Good luck :)

---

### Post by koenn on 2007-10-17
> **Old Pink said:**
> Basically, I want to store the 5 to 6 Gigabytes in my laptop's hard drive temporarily elsewhere while I install a new 20GB hard drive before transferring it all onto that.

Only viable option seems to be putting it on the 80GB desktop temporarily. 

No CD drive, DVD drive, for reading or writing on the laptop. 

Ideas?
How about this : 
put the old laptop-disk and the new one in your desktop ; say that's /dev/hdb for old disk and /dev/hdc for new disk. 

clone the old disk on the new disk : 
```
dd if=/dev/hdb of=/dev/hdc
```

This will include MBR, partition table etc. 
Use GpartEd to change partition sizes on new disk (because the'll be the same sizes as on the old disk so you'll have some unused space. Or just add a partition - depands on what you want)

put new disk in laptop, and boot as if nothing has changed, except for a whole lot of space. 

alternative : if you can connect 2 hard drives to your laptop, you can do it there : clone, then put the new disk where the old one used to be. 

pitfall : if there are UID's in /etc/fstab, you might want to replace those. 

I've done this a few weeks back in VMware, it worked there (notes : [http://users.telenet.be/mydotcom/howto/linux/disks1.htm](http://users.telenet.be/mydotcom/howto/linux/disks1.htm)). If it doesn't : you still have the old disk unmodified, so it's quite safe.

---

### Post by Old Pink on 2007-10-18
It won't copy. Or back up. Or anything. Followed many guides, but there are always folders in the end tarball/folder missing (home, boot, a few others)

I've ordered an external USB hard drive case thing, so I can plug two in at once. In which case I'll just try ```
dd if=/dev/hdb of=/dev/hdc
```right?

---

### Post by koenn on 2007-10-18
> **Old Pink said:**
> 
I've ordered an external USB hard drive case thing, so I can plug two in at once. In which case I'll just try ```
dd if=/dev/hdb of=/dev/hdc
```right?
well, sort of.
the disks might be called sda, sdb, ... in stead of .hda, hdb, ... 
also, you'd have to be sure which is which, i.e. check that your old disk is really hd**b** and not hda or hdc. 
Also, I've never done this with usb drives and I don't know how their dev names are made ...
But it's worth a shot, as long as you make sure you're not writing anything to the original hard disk, nothing is lost. 
Personally, I'd prefer to use the desktop machine, if it has connectors for 2 extra disks.

---

### Post by bionnaki on 2007-10-18
copying / and then transferring it to another computer, expecting it to be a bootable and working system will be a failure.

---

### Post by koenn on 2007-10-18
dd doesn't copy files, it copies blocks, below the filesystem. that's how it is capable of copying boot sectors and partition tables and thus 'clone' or 'mirror' disks.

---

