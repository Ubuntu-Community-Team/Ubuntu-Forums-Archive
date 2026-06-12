---
title: "Good program to make ISO from partition?"
date: 2006-09-26
forum: The Cafe
---

### Post by user1397 on 2006-09-26
is there any program at all, either on linux or windows, that can make a bootable iso image from a whole partition?

could partimage do this?  as far as i understand, partimage only copies the contents from one partition to another partition.  but what do i know.  does it create an iso image, or just a copy?  

the whole point of this is so i can put my recovery partition on a blank dvd.

thanks in advance.

---

### Post by x64Jimbo on 2006-09-26
Partimage will do this, but it's not in ISO format. It saves in GZ or BZ2.
I wrote a quick tutorial on making your own backup DVD [here.]("http://www.slax.org/modules.php?category=other&id=122&name=Partimage")
I don't know if there is a Linux equivalent of MySlax, but that's a start for you.

---

### Post by user1397 on 2006-09-26
> **x64Jimbo said:**
> Partimage will do this, but it's not in ISO format. It saves in GZ or BZ2.
I wrote a quick tutorial on making your own backup DVD [here.]("http://www.slax.org/modules.php?category=other&id=122&name=Partimage")
I don't know if there is a Linux equivalent of MySlax, but that's a start for you.wow thats like exactly what i was looking for all this time.  thanx so much man.
i'll try it out and post here how it goes.

---

### Post by NoTiG on 2006-09-26
I have a question sort of based on this... say you had a machine like a laptop... and got ubuntu installed... but had to do some tweaks to get it working... like setting up codecs... installing the wifi wrapper instuff... and once you got it to a state you wanted, then how would you make that into a new image... so you could download it to the same identical computers and have the same exact setup without having to tweak them? Is that what the oem install feature is for ?

---

### Post by x64Jimbo on 2006-09-27
You could certainly use the method described in the link i put up. That was the case for me when I was designing my first restore disc. I had a TON of tiny, nitpicky little details to figure out each time I built the machine and it was annoying, so I decided to image it. Restoring from an image can be a pain in the butt, though, so I automated it. It should be noted that partimage does NOT snapshot the MBR, so you may want to do that separately with a dd command string of sorts. I'll probably script that into my next restore DVD.

---

### Post by NoTiG on 2006-09-27
Here is the answer i found: [http://blogs.adobe.com/penguin.swf/](http://blogs.adobe.com/penguin.swf/)    * get the "Dapper Drake" Ubuntu 6.06.1 Live CD ISO image
    * mount the ISO image as part of the filesystem
    * copy the ISO contents into a temporary directory
          o the stock live CD comes with Windows installers for various free software packages like Firefox and Thunderbird; if you don't need these on your live CD, you can save over 30 MB by deleting the programs/ directory
    * mount casper/filesystem.squashfs as part of the filesystem
          o use Squashfs and compile the kernel stuff
          o alternatively, Gentoo kernels seem to already have the squashfs stuff patched in
    * copy the contents into a temporary directory; do this as root and with -a option for a correct copy
    * make any necessary modifications to the root filesystem (in my case, this simply means copying libflashplayer.so into the correct directory)
    * whittle away any components you don't strictly need for a demo live CD (OpenOffice, with a 200 MB tree, is a good candidate)
    * rebuild root filesystem; run as root: 'mksquashfs squashfs-root filesystem.squashfs'
    * overwrite the old casper/filesystem.squashfs file with the newly created one
    * build burnable, bootable ISO: 'mkisofs -o ubuntu-6.06.1-desktop-i386-custom.iso -b "isolinux/isolinux.bin" -c "isolinux/boot.cat" -no-emul-boot -boot-load-size 4 -boot-info-table -cache-inodes -r -J -l ubuntu-6.06.1-desktop-i386'
    * test: 'qemu -cdrom ubuntu-6.06.1-desktop-i386-custom.iso -boot d -m 256'

---

