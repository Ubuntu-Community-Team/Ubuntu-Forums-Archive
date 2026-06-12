---
title: "&quot;Packages.gz&quot; was corrupt... every time?"
date: 2008-07-08
forum: Server Platforms
---

### Post by eternicode on 2008-07-08
I'm trying to install Ubuntu 8.04 Server i386 on a Pentium III machine.  Everytime I get to "Install base system", I get an error saying that "file:///cdrom/dists/hardy/main/binary-i386/Packages.gz was corrupt".  I'm guessing this is a *fairly* essential file, and, as such, I can't go any farther.

At first I downloaded the 8.04.1 cd directly from the Ubuntu server, then I downloaded both the 8.04.1 and 8.04 cds from torrents.  Same thing all three ways.

Now I've extracted the 8.04 ISO's contents to my hdd, and ran md5sum on the md5sums.txt:

```

andrew@Ximplix:/media/share/ubuserv$ md5sum -c md5sum.txt | grep -v OK
md5sum: ./install/netboot/pxelinux.cfg/default: Not a directory
./install/netboot/pxelinux.cfg/default: FAILED open or read
./install/netboot/pxelinux.0: FAILED
md5sum: ./pool/restricted/l/linux-restricted-modules-2.6.24/linux-restricted-modules-2.6.24-16-generic_2.6.24.12-16.34_i386.deb: No such file or directory
./pool/restricted/l/linux-restricted-modules-2.6.24/linux-restricted-modules-2.6.24-16-generic_2.6.24.12-16.34_i386.deb: FAILED open or read
md5sum: ./pool/restricted/l/linux-restricted-modules-2.6.24/nic-restricted-modules-2.6.24-16-generic-di_2.6.24.12-16.34_i386.udeb: No such file or directory
./pool/restricted/l/linux-restricted-modules-2.6.24/nic-restricted-modules-2.6.24-16-generic-di_2.6.24.12-16.34_i386.udeb: FAILED open or read
md5sum: ./pool/restricted/l/linux-restricted-modules-2.6.24/nic-restricted-firmware-2.6.24-16-generic-di_2.6.24.12-16.34_i386.udeb: No such file or directory
./pool/restricted/l/linux-restricted-modules-2.6.24/nic-restricted-firmware-2.6.24-16-generic-di_2.6.24.12-16.34_i386.udeb: FAILED open or read
md5sum: ./pool/main/l/linux/firewire-core-modules-2.6.24-16-generic-di_2.6.24-16.30_i386.udeb: No such file or directory
./pool/main/l/linux/firewire-core-modules-2.6.24-16-generic-di_2.6.24-16.30_i386.udeb: FAILED open or read
md5sum: ./pool/main/l/linux/pcmcia-storage-modules-2.6.24-16-generic-di_2.6.24-16.30_i386.udeb: No such file or directory
./pool/main/l/linux/pcmcia-storage-modules-2.6.24-16-generic-di_2.6.24-16.30_i386.udeb: FAILED open or read
md5sum: WARNING: 6 of 1269 listed files could not be read
md5sum: WARNING: 1 of 1263 computed checksums did NOT match

```
In the first two instances (./install/netboot/pxelinux.cfg/default), ./install/netboot/pxelinux.cfg is a zero-byte file.  In the third instance, pxelinux.0 is also a zero-byte file.

Also, when I burned the ISOs in K3B, I had turned on "verify written data", and every time it complains that the "data in track 1 differs from the original".

Has Ubuntu put up corrupted ISOs for us to download, is the program I used for unzipping (PeaZip) unfit for ISOs, or am I just having bad luck?

----

Hm.  For good measure, I mounted the ISO and ran md5sum on the files from there, and everything came out OK.  Help?

---

### Post by windependence on 2008-07-08
Might want to unzip from the command line using gunzip.

-Tim

---

### Post by eternicode on 2008-07-08
> **windependence said:**
> Might want to unzip from the command line using gunzip.

-Tim

```

andrew@Ximplix:/media/share$ gunzip /home/andrew/Desktop/ubuntu-8.04-server-i386.iso
gzip: /home/andrew/Desktop/ubuntu-8.04-server-i386.iso: unknown suffix -- ignored

```
If you meant to unzip Packages.gz, that's one of the files listed in the ISO's md5sum.txt file.  And it checks out fine when I loop-mount the ISO.

Thanks anyway.

---

### Post by windependence on 2008-07-08
Well I don't know what you were unzipping, but you mentioned:

> Has Ubuntu put up corrupted ISOs for us to download, is the program I used for unzipping (PeaZip) unfit for ISOs, or am I just having bad luck?

and I never heard of PeaZip, so I thought maybe a more mainstream tool might work for you.

If the ISOs were corrupt, I think we'd be hearing from a lot more people. :)

Sorry, I'm out of ideas on this one.

-Tim

---

### Post by eternicode on 2008-07-08
Well...as my gunzip line shows, I was referring to the ISO file :) .  PeaZip I believe uses 7Zip as a backend for unzipping most filetypes, and it can open/browse/unpack ISO files.  Though apparently it's having issues here.

And, yes, everyone else seems to be doing fine with their copies... :/

---

### Post by hugh222 on 2008-07-26
I have been having the exactly the same problem with a Pentium III machine but I am new to linux and have no idea how to fix it.

---

### Post by eternicode on 2008-07-26
Oh sorry; I eventually gave up trying to install it on that computer and tried another computer, an old Compaq 5000a series.  The installation ran fine, no errors, first time through.  I would assume this means I originally had a bad CD drive, a bad motherboard, bad RAM, or something.  Though I would think that any one of these would prevent Ubuntu from booting up at all.

---

### Post by Rhemat on 2009-07-18
I'm having the same problem on an Intel PIII 1.3GHz processor (Ubuntu Server 9.04), except I'm getting a LOT of packages that are corrupt (the only one I can remember is ncurses).

Everything in the system should be fine because I used to use this system as my main desktop.

Thanks in advance.

---

### Post by ktrnka on 2009-07-19
I've had this problem many times and the problem always seems to be a defective cd drive. Try another one.

---

### Post by windependence on 2009-07-19
I agree that it's probably hardware. Could be memory as well as drives creating CRC errors.

-Tim

---

