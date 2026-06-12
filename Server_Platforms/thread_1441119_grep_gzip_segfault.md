---
title: "grep gzip segfault"
date: 2010-03-28
forum: Server Platforms
---

### Post by hyperdaz on 2010-03-28
I have an interesting issue Ubuntu Server 8.04, The server has been running for quite a while (not designed or put together by me) but recently it has started segfualting and now will not boot apart from in read-only mode.

I see the following errors in dmesg.
-----------------------------------------
[   75.010093] grep[2671]: segfault at 0000000b eip 0804ccbd esp bfc1d890 error 4
[   75.010669] grep[2673]: segfault at 0000000b eip 0804ccbd esp bf84bcc0 error 4
[   75.014977] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:1a.1/usb2/2-2/2-2:1.1/input/input8
[   75.019083] grep[2672]: segfault at b7f84d48 eip 08060207 esp bfc1d9ec error 6
[   75.019103] grep[2674]: segfault at b7f3dd48 eip 08060207 esp bf84be1c error 6
[   75.033642] input,hiddev96,hidraw3: USB HID v1.10 Device [NOVATEK USB Keyboard] on usb-0000:00:1a.1-2
[   75.298325] mountpoint uses obsolete (PF_INET,SOCK_PACKET)
[   75.350314] grep[2686]: segfault at 0000000b eip 0804ccbd esp bfa7cef0 error 4
[   75.350923] grep[2688]: segfault at 0000000b eip 0804ccbd esp bfa00e70 error 4
[   75.356079] grep[2696]: segfault at 0000000b eip 0804ccbd esp bfce7950 error 4
[   75.356679] grep[2698]: segfault at 0000000b eip 0804ccbd esp bfe0da80 error 4
[   75.400966] grep[2712]: segfault at 0000000b eip 0804ccbd esp bfae5f50 error 4
[   75.401667] grep[2714]: segfault at 0000000b eip 0804ccbd esp bf9bb630 error 

[  104.925252] gzip[2820]: segfault at 63000000 eip 08054555 esp bfe2c458 error 
-----------------------------------------

The logic would be to reinstall grep and gzip if possible.

Urgently need to get this machine to boot fully

Thanks for any help

---

### Post by craigp84 on 2010-03-28
Hmmm i'm more inclined to think the segfaults are symptoms rather than the reason your box wont boot up.

Try booting off a LiveCD, assuming that works (more or less rules out CPU, Mobo, Ram), try mounting the local disk. Do an fsck to see if that works. If so, probably not the HDD. In that case then i'd chroot into the installation and see if basic commands work (i'd also try gzip and grep just in case they are the real faults). Then assuming that goes well, i'd try some of the init.d scripts and simulate starting the box.

Hopefully at one point above something will jump out. Past experience though suggests faulty hardware.

Let me know how you get on?

---

### Post by hyperdaz on 2010-03-28
Thanks for the quick reply

Iv done most of what you have said so far.
I am using a LiveCD atm to backup as much data as possible. everything works fine from LiveCD, I have also run the memory tester on the RAM to check that..

I can mount the local disk, in fact I can boot the machine but everything is read-only and I cant stop Ubuntu from giving me the rescue menu every time.

grep does not work (and was one of the first things I noticed) I have not tried gzip but I believe there are more broken packages, ping firestarer possibly more but have not seen anything that tests for broken Debian packages (apart from dependencies)... While the machine is in this reduced state (even though the menu option is boot normally) there's no networking.

Grep, I did re-install grep from a the debian package but as things are in read-only when I reboot it's straight back to the broken grep.

"i'd chroot into the installation" Not 100% sure how to do this... 

Then assuming that goes well, i'd try some of the init.d scripts and simulate starting the box.

I don't believe its faulty hardware, at this point in time :-|

I have also run fsck on the drive with no errors.

hmmm

---

### Post by craigp84 on 2010-03-29
> "i'd chroot into the installation" Not 100% sure how to do this... 

From the live cd mount the root filesystem (read / write) from disk onto say /recovery. Then use "chroot /recovery /bin/sh" which will drop you into a statically linked sh shell from your installation -- this shell has no dependencies so has maximum chance of avoiding corruption that may lie in libraries.

Assuming that gets you in, a quick peek about to see what's stuffed and what's not is in order. Depending on how far things go, i'd maybe even attempt an "apt-get install --reinstall grep" just out of curiosity and see what works and what doesn't.

> I don't believe its faulty hardware, at this point in time

Yup i'd agree from what you've said it's totally possible it's something else.

Do you have any inkling towards what may have caused this? It's a really big failure whatever's gone wrong. 

Whatever the sysadmin version of "spidey sense" is, i just cant shake mine, it's still tingling a sensation of hardware (south bridge/raid card/whatever or disk) failure right now. I couldn't, with a clear conscience, reinstate that box in production just yet.

---

