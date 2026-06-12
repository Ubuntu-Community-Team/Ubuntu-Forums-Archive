---
title: "Announcing the Release of the World's First 64-bit Build of Google's ChromiumOS"
date: 2009-11-29
forum: The Cafe
---

### Post by Teo En Ming on 2009-11-29
[B]Announcing the Release of the World's First 64-bit Build of Google's ChromiumOS for Netbooks

[/B]I have ported the development code of the open source ChromiumOS project to 64-bit. Google Chrome OS will be officially released in late 2010, and it will be based on the Chromium OS project.

My 64-bit build of ChromiumOS is called ChromiumOS64. Download your copy now!

Download link: [http://www.chromiumos64.org/](http://www.chromiumos64.org/)

---

### Post by gnomeuser on 2009-11-29
Is there any reason why this code is not worked up upstream?

---

### Post by earthpigg on 2009-11-29
have you considered trademark issues?

Google has the right to have control over anything called "Chrome" or "Chromium"...

---

### Post by Teo En Ming on 2009-11-30
Martin Bligh from Google commented:

[http://groups.google.com/group/chromium-os-discuss/browse_thread/thread/1b8766e81e94bf58](http://groups.google.com/group/chromium-os-discuss/browse_thread/thread/1b8766e81e94bf58)

---

### Post by HappinessNow on 2009-11-30
> **Teo En Ming said:**
> Martin Bligh from Google commented:

[http://groups.google.com/group/chromium-os-discuss/browse_thread/thread/1b8766e81e94bf58](http://groups.google.com/group/chromium-os-discuss/browse_thread/thread/1b8766e81e94bf58)Interesting you may have reserved yourself a job with Google, one day.

Congratulations, I will keep an eye on it and test it one day.

Thanks!

---

### Post by Teo En Ming on 2009-11-30
> **&#20170 said:**
> Interesting you may have reserved yourself a job with Google, one day.

Congratulations, I will keep an eye on it and test it one day.

Thanks!

I don't think that will happen because I am not a software engineer.

I need testing for my 64-bit build of Chromium OS on real hardware. So far I have only tested it in Xen virtualization environment.

---

### Post by NoaHall on 2009-11-30
Hm... Could you make a compact .iso or .image file to use on a USB stick? I'd download it then.

---

### Post by toupeiro on 2009-11-30
Some constructive criticism, not necessarily on the OP but on the state of Chromium and the need for 64-bit at this time:

32-bit or 64-bit, it still cannot handle very common wireless adapters on bootup and has no poweroff button, alongside a slew of other functionality its currently lacking.  There's still quite a bit more work to do, and since the OS is geared towards lightweight uses, I don't see the advantages of x64 bit here. (web browser work taking up more than 4GB of RAM in alpha?)  Not to discredit your efforts, I just think much more work is needed upstream on things that are truly lacking in the OS itself with the same level of commitment you have to seeing x64-bit at this stage in the game, but congrats on your success in getting x64-bit compiled!

Cheers and Kudos!

-T

---

### Post by 3rdalbum on 2009-11-30
Most, if not all Intel Atoms that land in netbooks are 32-bit only (and can only address 2 GiB anyway). The Via Nano is 64-bit-compatible, but not widely available in netbook computers.

If you could help with something other than compiling Chromium OS in 64-bit, then I'm sure your efforts would be more appreciated.

---

### Post by Teo En Ming on 2009-11-30
I've used qemu-img to convert the WMware VMDK image to raw harddisk image. Then I dd the raw harddisk image to a 20 GB USB external harddisk. You don't need to use a USB thumb drive or USB flash memory.

ChromiumOS64 works on real hardware. I've successfully booted up ChromiumOS64 on my Intel Pentium Dual Core E6300 @ 2.8 GHz, Intel Desktop Board DQ45CB, 6 GB DDR2-800 memory and nVidia GeForce 8400 GS PCI Express x16 graphics card. It can't detect the Intel GMA4500 onboard graphics though.

I am posting this message and watching Youtube videos at the same time using my 64-bit build of Google Chromium OS (ChromiumOS64).

---

### Post by Teo En Ming on 2009-11-30
> **NoaHall said:**
> Hm... Could you make a compact .iso or .image file to use on a USB stick? I'd download it then.

Dear NoaHall,

You could download the WMware VMDK image file, convert it to raw harddisk image and dd the raw image to your USB thumb drive or USB external harddrive.

The commands are as follows:

$ qemu-img convert -f vmdk chromiumos64.vmdk -O raw chromiumos64.img

If /dev/sdc is your USB stick,

# dd if=chromiumos64.img of=/dev/sdc

Then you can boot up ChromiumOS64 using your USB stick. There's no need to install ChromiumOS64. Just run it like a Linux Live USB.

You need at least 9.5 GB free space on your USB stick.

---

### Post by Teo En Ming on 2009-11-30
> **toupeiro said:**
> Some constructive criticism, not necessarily on the OP but on the state of Chromium and the need for 64-bit at this time:

32-bit or 64-bit, it still cannot handle very common wireless adapters on bootup and has no poweroff button, alongside a slew of other functionality its currently lacking.  There's still quite a bit more work to do, and since the OS is geared towards lightweight uses, I don't see the advantages of x64 bit here. (web browser work taking up more than 4GB of RAM in alpha?)  Not to discredit your efforts, I just think much more work is needed upstream on things that are truly lacking in the OS itself with the same level of commitment you have to seeing x64-bit at this stage in the game, but congrats on your success in getting x64-bit compiled!

Cheers and Kudos!

-T

Thank you.

---

### Post by Teo En Ming on 2009-11-30
> **3rdalbum said:**
> Most, if not all Intel Atoms that land in netbooks are 32-bit only (and can only address 2 GiB anyway). The Via Nano is 64-bit-compatible, but not widely available in netbook computers.

If you could help with something other than compiling Chromium OS in 64-bit, then I'm sure your efforts would be more appreciated.

I am not a software developer.

---

### Post by Teo En Ming on 2009-11-30
[http://chrometecha.blogspot.com/2009/11/install-chrome-os-64-bit-version.html](http://chrometecha.blogspot.com/2009/11/install-chrome-os-64-bit-version.html)

---

### Post by Teo En Ming on 2009-11-30
I've uploaded the ChromiumOS64 files to Amazon S3 online storage cloud. If you use a download accelerator like prozilla, axel, or SKDownloader (all Linux based), you can achieve download speeds of up to 1 MegaBytes per second.

---

### Post by HappinessNow on 2009-11-30
> **Teo En Ming said:**
> I've uploaded the ChromiumOS64 files to Amazon S3 online storage cloud. If you use a download accelerator like prozilla, axel, or SKDownloader (all Linux based), you can achieve download speeds of up to 1 MegaBytes per second.do you have a simple link to a torrent download of the iso?

---

### Post by Teo En Ming on 2009-11-30
> **&#20170 said:**
> do you have a simple link to a torrent download of the iso?

No. I didn't create any torrent downloads. Sorry.

---

### Post by Teo En Ming on 2009-11-30
**ChromiumOS64 &#12503;&#12525;&#12472;&#12455;&#12463;&#12488;**

[http://royalwin.blog.so-net.ne.jp/2009-11-30](http://royalwin.blog.so-net.ne.jp/2009-11-30)

> 
ChromiumOS64 &#12503;&#12525;&#12472;&#12455;&#12463;&#12488;&#12391;&#12399;&#12289;Google Chrome OS &#12398;&#12477;&#12540;&#12473;&#12434; &#12509;&#12540;&#12486;&#12451;&#12531;&#12464;&#12375;&#12390; Chrome OS &#12398; 64 &#12499;&#12483;&#12488;&#29256;&#12434;&#12499;&#12523;&#12489;&#12375;&#12383;&#12381;&#12358;&#12384;&#12290; 
[http://www.chromiumos64.org/](http://www.chromiumos64.org/)
VMware &#12398;&#12452;&#12513;&#12540;&#12472;&#12501;&#12449;&#12452;&#12523;&#12364;&#20844;&#38283;&#12373;&#12428;&#12390;&#12356;&#12427;&#12290;
64&#12499;&#12483;&#12488;&#12364;&#12394;&#12380;&#24517;&#35201;&#12363;&#65311;&#12398;&#29702;&#30001;&#12384;&#12364;&#12289;x86-64 &#12434;&#12469;&#12509;&#12540;&#12488;&#12377;&#12427;Itel Atom 300&#12471;&#12522;&#12540;&#12474;&#12420; AMD Neo, Via Nano &#29992;&#12392;&#12398;&#12371;&#12392;&#12384;&#12290;&#12418;&#12385;&#12429;&#12435; Core 2,Core i,Phenom&#12394;&#12393;&#12391;&#12418;&#20351;&#12360;&#12427;&#12381;&#12358;&#12384;&#12290;
winimage &#12391; VMware &#12398;&#12452;&#12513;&#12540;&#12472;&#12501;&#12449;&#12452;&#12523;&#12434; USB &#12513;&#12514;&#12522;&#12395;&#26360;&#12365;&#36796;&#12435;&#12391; LiveUSB &#12398;&#20316;&#25104;&#12418;&#21487;&#33021;&#12392;&#12398;&#12371;&#12392;&#12290;(16GB&#20197;&#19978;&#12398;USB&#12513;&#12514;&#12522;&#12364;&#24517;&#35201; ??)
[http://www.winimage.com/download.htm](http://www.winimage.com/download.htm)
Windows &#12420; &#20182;&#12398; Linux &#12418; 64&#12499;&#12483;&#12488;&#29256;&#12364;&#12354;&#12427;&#12290;
Chrome OS &#27491;&#24335;&#29256;&#12418; 32 &#12499;&#12483;&#12488;&#65292;64 &#12499;&#12483;&#12488;&#29256;&#12398; 2 &#31278;&#12364;&#25552;&#20379;&#12373;&#12428;&#12427;&#12398;&#12363;&#12418;&#12375;&#12428;&#12394;&#12356;&#12290;


---

### Post by Teo En Ming on 2009-12-01
Enthusiast makes 64-bit build of Google Chrome OS available

Link: [http://www.liliputing.com/2009/11/enthusiast-makes-64-bit-build-of-google-chrome-os-available.html](http://www.liliputing.com/2009/11/enthusiast-makes-64-bit-build-of-google-chrome-os-available.html)

---

### Post by NoaHall on 2009-12-01
> **Teo En Ming said:**
> Dear NoaHall,

You could download the WMware VMDK image file, convert it to raw harddisk image and dd the raw image to your USB thumb drive or USB external harddrive.

The commands are as follows:

$ qemu-img convert -f vmdk chromiumos64.vmdk -O raw chromiumos64.img

If /dev/sdc is your USB stick,

# dd if=chromiumos64.img of=/dev/sdc

Then you can boot up ChromiumOS64 using your USB stick. There's no need to install ChromiumOS64. Just run it like a Linux Live USB.

You need at least 9.5 GB free space on your USB stick.

I know I could, but it's too big for me to download just to play with.

---

### Post by Teo En Ming on 2009-12-01
> **NoaHall said:**
> I know I could, but it's too big for me to download just to play with.

I've already used the maximum compression with the zip archive utility on linux. It reports 53% deflated.

Currently, the vmware vmdk image file I have uploaded is my "one size fits all" solution.

I will try to see if I can reduce the size of the image further.

Ideally, LZMA compression algorithm provides the best compression ratio over bzip2 and gzip. But, in considering Windows users, I have changed the archiving utility to zip. I've got users asking me how to decompress .bz2 file extension.

---

### Post by Teo En Ming on 2009-12-01
Google Chrome OS update: netbook compatibility, 64-bit version and 1Gb USB flash drive image

Link: [http://www.mobilecomputermag.co.uk/news/091201/google-chrome-os-update-compatibility-64-bit-version-and-1gb-drive-image](http://www.mobilecomputermag.co.uk/news/091201/google-chrome-os-update-compatibility-64-bit-version-and-1gb-drive-image)

---

