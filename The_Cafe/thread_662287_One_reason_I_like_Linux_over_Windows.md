---
title: "One reason I like Linux over Windows"
date: 2008-01-08
forum: The Cafe
---

### Post by TheOrangePeanut on 2008-01-08
Both installations are vanilla, except I've installed some codec packages on the Mint installation.  The point is that the Windows installation is completely fresh except for updates... that sucks.

[IMG]http://img.photobucket.com/albums/v258/TheOrangePeanut/Screenshot-1.png[/IMG]

---

### Post by Ocxic on 2008-01-08
that's bloat ware for ya

---

### Post by mikewhatever on 2008-01-08
Is that Vista, cause in my experience, XP takes about 4 times less space. I also thought Linux Mint was famed for having codecs preinstalled. Was that not so? Those codecs must have been pretty big, cause a regular Ubuntu installation is way under 3 GB.

---

### Post by TheOrangePeanut on 2008-01-08
That is Windows XP Professional with all of the required (security) updates and ATI video drivers.  No .NET or any optional updates.  And yea, I shouldn't have said codecs for installation on Mint.  I did install some additional gstreamer codecs because Sound Converter didn't see them at first, and I also installed build-essential and the java JDK because I'm a programmer.  But those installations even further my point.

---

### Post by macogw on 2008-01-08
No way....I ran Windows XP on a computer that only has a 5GB hard drive for years.  It runs Debian now, but I know XP isn't that big.

---

### Post by TheOrangePeanut on 2008-01-08
How long ago were you running XP?  The only thing installed is Ati video drivers, my motherboard chipset drivers (network, audio), and SP2 + whatever other security updates were released since then.  It's XP Pro if that makes a difference, I'm not sure if it is any bigger than Home but I can't imagine it being so.

Edit:  Take a look

[IMG]http://img.photobucket.com/albums/v258/TheOrangePeanut/windows.jpg[/IMG]

---

### Post by bufsabre666 on 2008-01-09
my vista x64 install was 6gb before i added stuff and my xp was only like 2gb

---

### Post by Meep3D on 2008-01-09
Those numbers definitely look screwy.  How much RAM do you have?  Windows creates a pagefile of ~150% of your memory and a pre allocates a hibernation file of the same size as your RAM.

Do you not also have a separate swap partition on your Linux install that you are not counting?

---

### Post by TheOrangePeanut on 2008-01-09
Yes, the Linux partition is technically 800 MB bigger than Nautilus shows because of the swap partition, but Linux is still taking up much less space.  I don't see how it is screwy; as I said, the Windows install is FRESH (as in, I did it 2 or maybe 3 days ago and haven't installed anything onto it).

[IMG]http://img.photobucket.com/albums/v258/TheOrangePeanut/gparted.png[/IMG]

---

### Post by quanumphaze on 2008-01-09
This is definitely not normal. My laptop originally used less than that with OEM bloatware and all. Now it takes up 10.5 GB after I went uninstall crazy in November.

Try using the Disk Usage Analyzer to find what is taking up that space.

---

### Post by hyper_ch on 2008-01-09
why do you still compare to XP? XP is already 7 years old... Vista and Gutsy are from last year. So if compared it should be them and VISTA is totally bloated.

---

### Post by capink on 2008-01-09
Also don't forget excluding restore points and and any personal files might have in "Documents and Settings".

I have my windows xp sp2 partition mounted under linux on /c. I use the following command to determine how space much xp takes.

```
du --apparent-size -csh /c --exclude=Recycled --exclude="System Volume Information"  --exclude="Documents and Settings" --exclude=pagefile.sys
```

On my computer it takes 5.3G. But it is not fresh installation as it has some programs and dirvers installed.

I excluded "Documents and Settings" since in a fresh install it does not take a lot of space.

---

