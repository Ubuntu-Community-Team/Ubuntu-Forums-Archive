---
title: "Can't boot from LiveUSB on star3"
date: 2010-11-18
forum: System76 Support
---

### Post by 130s on 2010-11-18
star3 I just bought and received 3 days ago (and got messed up) does not boot from LiveUSB trying both 10.04 netbook ed. and 10.10 desktop ed. Is there anything I should be aware of particularly on star3 to boot from LiveUSB? 

A. Phenomenon
- When I omit harddisk from BIOS' boot device list, it shows "Operating system not found" and do nothing further.
- When I include harddisk on BIOS, star3 always boots the problematic Ubuntu (which I reported at [http://ubuntuforums.org/showthread.php?t=1623934](http://ubuntuforums.org/showthread.php?t=1623934)) from HDD 

B. Workaround tried but didn't work
- Tried various BIOS setting (excluding every device except for USBs, excluding everything except the USB that has LiveUSB inside, etc.)
- Create LiveUSB both on Mac (following instruction here: [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)), and on Windows Vista (on VMWare) using UNetbootin. Also, neither Ubuntu 10.04 netbook edition nor 10.10 desktop edition worked.

# since I have no other PC that can boot from USB, there's no way to verify the LiveUSB is made properly.

Isaac

---

### Post by Hippytaff on 2010-11-18
Hi

did you varify the md5sum? might  be that the iso is corrupt?

---

### Post by 130s on 2010-11-21
Thanks [Hippytaff]("http://ubuntuforums.org/member.php?u=1133249").
As long as I see the result of md5 command, both hash values from { 10.10, 10.04 } netbook edition match with what are shown on [UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes") page.

$ md5 ubuntu-10.10-netbook-i386.img 
MD5 (ubuntu-10.10-netbook-i386.img) = 6877bf8d673b87ba9500b0ff879091d0
$ md5 ubuntu-10.04-netbook-i386.img 
MD5 (ubuntu-10.04-netbook-i386.img) = 712277c7868ab374c4d3c73cff1d95cb

I just noticed [the page that explains how to create LiveUSB on Mac OSX]("http://www.ubuntu.com/netbook/get-ubuntu/download") encourages using CD instead of USB. But since I don't have USB CD drive that I can use with star3, I prefer sticking to LiveUSB.
<quote>
We would encourage Mac users to download Ubuntu Netbook Edition by  creating a CD for the time being. But if you would prefer to use a USB,  please follow the instructions below.
</quote>

---

### Post by Dave_L on 2010-11-21
I doubt if this helps, but I didn't have any problem booting my star3, running 10.04, from the 10.04 Live USB I made.

The file I used, ubuntu-10.04-netbook-i386.iso, had the extension ".iso" rather than ".img", but the md5sum looks the same.

I used Startup Disk Creator to make the Live USB.  I kept the "reserved extra space" at 0, since I didn't plan on saving any changes after booting.

The only change I had to make in BIOS was to make USB HDD the first boot device.

---

### Post by 130s on 2010-11-21
Now I've been able to make a little progress that my star3 can at least find something from LiveUSB, although I'm still struggling to boot Linux. Current status is:

Workaround taken
- Use UNetBootin to create LiveUSB. Ubuntu 10.10 Netbook ed.
- Put USB to the right front slot (my star3 has 3 slots and I was trying the one on the left all the time before)

Phenomenon
- When booting, it shows UNetBootin blue window and 10 seconds count down. After 10 seconds, it goes like:
<quote>
Loading /ubnkern.
Loading /ubninit.........................................................................
</quote>

Then the machine reboots. Any idea?? Now I'm downloading 10.04 netbook ed. and will try the same steps.

Dave_L, 

> The file I used, ubuntu-10.04-netbook-i386.iso, had the extension ".iso" rather than ".img", but the md5sum looks the same.

I just used the .img files that I created from .iso files since I was directed to do so [here]("http://www.ubuntu.com/netbook/get-ubuntu/download") on Mac.

---

### Post by 130s on 2010-11-22
Although I'm not sure what was the cause of this problem, I now have installed Ubuntu 10.04 Netbook ed. successfully on my star3 :D .

What worked was:
- Use UNetBootin on Windows Vista to create LiveUSB media
- Use Ubuntu 10.04 .iso, instead of .img file that I converted from .iso file
- Try all USB slot on netbook and find the good one 

I appreciate all your concerns!
Isaac

---

