---
title: "best OS for an eeepc with 512 MB RAM?"
date: 2015-03-04
forum: Ubuntu, Linux and OS Chat
---

### Post by orange2k on 2015-03-04
Hi, I've come in posession of an old ASUS eeepc with 512 MB RAM...

There is a distro installed on the computer but its an old one, with no way to upgrade key components like browser and other stuff...

I would like to install some other OS so I could run youtube and other multimedia, but bare in mind that there is only 512 MB of RAM available...

So what would you recommend?):P

---

### Post by Lars Noodén on 2015-03-04
I'd recommend a bare bones installation and then add in fvwm-crystal for the GUI.  Otherwise, you might look at Lubuntu.  RAM is not so hard to get these days so you might go with 1 GB or 2 GB and you will really notice an improvement in performance on that machine.

---

### Post by ajgreeny on 2015-03-04
Yes, go with the [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") and add a DE such as lxde, or even just a window-manager like openbox.

I think you should avoid even a full Lubuntu installation on that machine as it is very limited and if you manage to get it to install it will still probably run very slowly.  You could, of course, try installing Lubuntu from a live USB first, but I think 512MB ram will stop that working properly.

---

### Post by pmi2 on 2015-03-04
I would be careful before you blow away whatever is on that machine.  This was a really cool Netbook in its day, but I have no idea if the RAM is even upgradable.  Find an online review using your exact model number, there were several models.

Your computer probably came with a version of Aurora Linux, later replaced by eeeBuntu.  Looking that up, I come up with Ubuntu 9.04, and "Ubuntu Netbook Edition".  It probably has an Intel Atom Processor.

You will probably need something with a kernel tuned to the Asus EEE PC, and personally I have no idea which of the current Ubuntu flavors can do this, but good chance that someone here will know the answer to that.

In any case you will be best off if you can revive the OS which is on the machine now as a first step, and before you upgrade to something else.

---

### Post by orange2k on 2015-03-05
Well, first I tried Zorin OS lite, and it installed fine, but there was no space left on the drive to update it (it only has 4 GB space)...

Then after a little research I found Easy Peasy 1.6, I think its based on Ubuntu 8.04, and it installed fine with almost everything I need (Open Office, music player, video player, it even supports flash), and everything works great, I even have about 1 GB empty space on the hard drive...:KS

The computer came with some kind of Debian preinstalled, but with outdated versions of Firefox and other components, so the upgrade to another OS was really necessary...

---

### Post by sudodus on 2015-03-05
You can also try ***ToriOS*** (that is still being developed and around 'beta'), and ***Puppy Linux*** (Wary Puppy or TahrPup). Those distros are lighter than Lubuntu and have no problems with 512 MB RAM.

See also this link [https://wiki.ubuntu.com/Lubuntu/AdvancedMethods](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods)

---

### Post by Brian_Boyle on 2015-03-05
I think that Puppy Linux may be worth trying, as"sudodus" said, the ram is no problem and for space you can save your work to a pendrive which would help keep your HDD from becoming full.

---

### Post by Lars Noodén on 2015-03-05
Or you  can keep a 16GB, or more, SD card in the slot on the side since it inserts out of the way entirely.  Then you can have root on the main drive and /home on the removable device.  Then backups can be run over any of the USB ports.

---

### Post by Tar_Ni on 2015-03-05
Puppy Linux is probably your best bet for getting the most out of this eeepc. It is incredibly small and is meant for hardware from the dinosaure era. The best thing is, you don't even need to install it. Just plug in a bootable USB stick or a CD and it will boot straight on the RAM. You can then save all your settings between each sessions. But if you wish to install it on the harddrive, you can do so as well.

Here's the latest Puppy release: [http://puppylinux.org/main/Download%20Latest%20Release.htm](http://puppylinux.org/main/Download%20Latest%20Release.htm)

---

### Post by Mike_Walsh on 2015-03-06
Agree with posts #6,#7 &#9...absolutely! Sudodus is quite right; a big '+1'!!

I've been running 'Tahrpup' 6.0 (6.02 as it is currently) since it was released at the end of October. I have a real 'dinosaur'; an ancient Dell Inspiron laptop from 2002.....an original 1100; a real 'brick' (but built like one, too...nice'n'solid)!

She originally had 128 MB of RAM. Even 'Puppy' would have struggled with that, but over the years I've gradually upgraded it to its max of 1 GB. A 20 GB HDD is lots & lots of room for a 'Puppy', but I bunged a 40 GB one in early last year.....and I've just recently changed the original Celeron for a P4 (made a big difference).

The point is, I now have a system that will do ANYTHING I ask of it, including network printing, and acting as a SAMBA client to my 'big' Compaq desktop (which is 10 yrs old this year). 'Puppy' has the SAMBA client built-in, as well as a host of other minimalist apps. If you're not too fussed about eye-candy, and are more concerned with functionality, then 'Tahrpup' will do ALL you could want. Even so, like all Linux distros, it's infinitely customizeable.....you can 'dress it up' QUITE nicely. The Puppy devs go out of their way to make all of the system coding as lean as possible, without sacrificing capability. And the installation & booting options are almost infinite; it will run from thumb drives, a 'frugal' HDD installation, SD cards.....even the old floppy disks & 'zip drives'. It really is that versatile.

I have acquaintances on the Puppy forums who've got older, less capable machines even than mine.....and you would not believe what they can do with them. I would** thoroughly** recommend it.....to **anyone** who is looking for an ultra-lightweight distro that is nevertheless 'big' on features.


Here's my desktop.....


[ATTACH=CONFIG]260488[/ATTACH]

---

### Post by dastasha on 2015-03-06
I've been playing with an Acer D270 with similar specs. Debian 7.8 LXDE works well. Puppy Wary was good though I find myself using Puppy Slacko 5.7 now - it found the wireless automagically.
Run the puppies from USB.
Ubuntu was a bit sluggish

---

### Post by leclerc65 on 2015-03-08
Distrowatch 
[http://distrowatch.com/](http://distrowatch.com/)
just announced TinyCore.

Some eeePC models have SSD and/or Ram soldered to the motherboard, not easy to upgrade.

---

### Post by simontaylor on 2015-10-22
LinuxLiteOS works perfectly on this little low-spec machine. Recommended.

---

### Post by Plumtreed on 2015-10-24
Thanks SimonT...............I gave it a try and it goes well on my eeePC701.........and has a very sophisticated look. Owners of 'still-running' eee's are always looking for an OS that will work.

Previously, I have re-installed the old Xandros........also found an older Android OS that runs incredibly fast but tends to be a bit unreliable in it's network connections.

---

### Post by him610 on 2015-10-25
With my Acer Aspire One netbook, I have had good experience using Chromixium 1.1; although, I had previously upgraded the RAM from 512MB to 1.5GB.
[http://chromixium.org/]("http://chromixium.org/")

---

### Post by The_Forgotten_King on 2015-10-25
damn small linux all the way.

---

### Post by mörgæs on 2015-10-25
> **The_Forgotten_King said:**
> damn small linux all the way.

Damn Small Linux is an abandoned project which should not be recommended. Though it might be possible to install and run the system it is unsupported and hence a security risk.

---

### Post by Sweet_Baby_Jamie on 2015-10-26
LXLE 12.04 (32 bit) brought my old Dell with similar specs back to life

---

### Post by Mike_Walsh on 2015-10-27
> **Brian_Boyle said:**
> I think that Puppy Linux may be worth trying, as"sudodus" said, the ram is no problem and for space you can save your work to a pendrive which would help keep your HDD from becoming full.

I'll agree with Brian here. I've been using Puppy for sometime now, alongside the 'buntus. Puppy can be run entirely from a USB flash-drive, and needn't touch the internal 'drives' at all. You don't have a hard drive, by the way; you have micro SATA 'flash' cards.....and they can't be upgraded, I'm sorry to say; they're soldered to the motherboard.

You can save your work to another USB 'stick' if you want, as Brian says. The beauty of Puppy is that it runs entirely in RAM (typically around 200 MB), and then, once it's 'loaded', you can remove the 'system' flash-drive from the USB port, and use it for something else (like saving 'work in progress' to a second 'data' flashdrive, for instance.)

There's over 400 different variations, masters & re-spins of Puppy. There's even a few which have been made specifically for the Asus EEEpc's. Head over to the 'Puppy' Linux Forums:-

[http://www.murga-linux.com/puppy/index.php](http://www.murga-linux.com/puppy/index.php)

....and we'll soon help you out!


Regards,

Mike. ;)

---

### Post by techie4 on 2015-10-30
Personally I'd go for Xubuntu, but it would be desirable to upgrade your RAM. 
Some net-books will allow you to upgrade to 1GB and maybe even 2GB or 4GB if you're lucky. 
If there's no chance of upgrading the RAM, and Xubuntu isn't performing well on your net-book, go with the minimal CD or something like Snappy Ubuntu Core.

---

