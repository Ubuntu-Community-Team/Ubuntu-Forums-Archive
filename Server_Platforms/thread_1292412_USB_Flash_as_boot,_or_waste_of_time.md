---
title: "USB Flash as boot, or waste of time?"
date: 2009-10-15
forum: Server Platforms
---

### Post by KillaB7 on 2009-10-15
I've been attempting to install 9.10 Server Beta onto a 2GB memory stick and utilize AUFS in order to conserve power and flash writes.

My plan was to run /root from USB and spin down the two 1TB storage drives when not in use.

I started with a 2GB OCZ Rally2 and ran into numerous issues. I then tried an older 2GB Cruzer Micro. The Micro works (minus the AUFS part), but it's horribly slow.

So, my question here is: Should I continue with USB flash as my boot medium (find a faster drive on the cheap), or am I much better off making a small boot partition on one of my storage drives? Maybe attempt loading the entire OS into ramfs so that I can still spin down both drives?

---

### Post by KillaB7 on 2009-10-16
Sorry, I didn't mean to imply that USB Flash boot is a waste of time.
It's a completely worthy avenue if it's your only storage medium.
Just wondering what "you" would do in my shoes since I have two HDs to work with?

---

### Post by Vegan on 2009-10-16
Flash storage is fine for servers that need to serve high volumes with few changes. USB sticks are not the best place, but I use one with Linux for fixing non-bootable machines.

Linux server will run on almost anything so its ideal for checking machines. No GUI means fast boot and ready to go.

SSD disks are still pricey but they are coming down.

---

### Post by stlsaint on 2009-10-16
for a high production server i would recommend doing a headless install of karmic server onto one of your hdd.

---

### Post by ian dobson on 2009-10-17
Hi,

My mythbuntu MythTV Frontend system boots from a CF card in a SATA->CF adapter. For the kernel it looks like a normal but small (4Gb) SATA harddisk. Reads are very quick but writing is slow but as almost nothing gets written to the CF card I only really notice it when I do an update.

The main reason for using CF cards:-

1) CF card is noiseless (Unlike a harddisk)
2) A CF card in a CF -> SATA adapter looks like a normal HD to the BIOS/kernel
3) I had several CF cards laying around.
4) Backing up the boot partition is easy.I just pull the card out, plug it into a card reader on another PC then do a dd to a file.

Note I've mounted the CF card as ext2 to reduce the number of writes. I've been using ths card for about 9 months now and haven't seen any corruption problems.

so going solid state for you boot drive makes sense in some cases if you can powerdown your data drives when their not required or write speed isn't that important (Just make sure you have more than enough ram).

Regards
Ian Dobson

---

### Post by KillaB7 on 2009-10-17
Thanks for the replies everyone. This is just a little project I'm working on to replace my DNS-323, allowing me to also run a PBX and VPN Server on the same device.

I'm using a D945GCLF2D, so just trying to find the best way to manage power.

I like the CF idea, but since I don't have an extra card laying around, or an adapter, I'm thinking of buying an OCZ Diesel (based on [this review](http://www.xcpus.com/reviews/91-Flash-Drive-Roundup-A-Dynamic-Review-8GB-16GB-32GB-Page-14.aspx)).
Just *still* not sure if I really need it.

---

