---
title: "Getting around system-76's too-small root partition"
date: 2009-10-06
forum: System76 Support
---

### Post by jwbrase on 2009-10-06
About a month or so ago a bought a Pangolin from System76. While I'm generally happy with it, I find that System76's balance of the / and 
/home partitions is far too biased towards the home partition. I tend to accumulate lots and lots of software and associated data, while my I don't tend to accumulate very much of whatever System76 thinks I need all that space in /home for. So my 13 gig / partition is filling up rapidly (although its still far from full), while my /home partition is pretty much empty (and about half of what actually is used in /home is actually taken up by a program that I compiled from source and its data).

The problem is that, since there's only one OS on this machine, I can't unmount / to increase its size in GParted. (And I'm not sure about /home, can that be unmounted during operation without causing trouble?) I'm also out of the country for a year, left my PartedMagic Live CD (or some other linux-based partition editing live CD, I forget exactly what I was using) at home, and have been having a dickens of a time creating a PartedMagic Live USB.

Also, there's the issue that I don't really have anywhere to back up to upon resizing (except for a couple USB sticks that aren't quite big enough to hold everything), so a problem in the middle of that operation could leave me with lost data. Then again, I don't have all that much to back up either...

So a few questions:

1: Is it possible to simultaneously assign two paritions to / , and can I safely unmount /home while logged in? If I can do that, I can shrink /home, make another more reasonably sized / partition, and assign it to / , giving myself two / partitions and a lot more breathing room.

2: If the above item is possible, would it be a better, safer, and/or more hassle-free way of doing things than resizing through a live USB? Is there a third option that is better than either.

If the general consensus seems to be that a live USB is my best option, I will give details on what I have tried so far and how it failed.

---

### Post by thomasaaron on 2009-10-06
Boot from a live CD.
Go to System > Admin > Partition Editor.
Right-click the Swap partition (the smallest one) and click "Swapoff"
Resize your home partition.
Move home partition to the right.
Move your swap partition to the right.
Increase the size of your root partition.
Click Apply.
It'll take a while.

---

### Post by jwbrase on 2009-10-07
Re-read my above post, please.

I know how to use GParted. The problem is finding a LiveCD. But all of my Live CD's (PartedMagic, Ubuntu 9.04, etc.) are at home in the States, and I don't plan on going back there for a year (I knew I was forgetting something). I also don't have any blank CD's to burn to. I do have a USB stick, but attempts to make a Live USB of PartedMagic have so far failed.

---

### Post by HotShotDJ on 2009-10-07
> **jwbrase said:**
> but attempts to make a Live USB of PartedMagic have so far failed.Have you tried using System -> Administration -> USB Startup Disk Creator?  I believe that tool will help you accomplish your goal.

---

### Post by jwbrase on 2009-10-07
Can that create a PartedMagic Live USB? I was under the impression it was only for creating Live USB's of Ubuntu, which will work as a last resort, but I don't currently have an ISO of it on hand (whereas I do have one of PartedMagic), and it's a fairly heavy download, which is a bit hard (but not impossible) to do on my connection, as it is fairly unreliable (but can be fairly fast if I'm lucky).

Anyways, I think I may have found out why I couldn't get my live USB to boot (from the Parted Magic site): "NOTE: If you are using any version of Ubuntu, your syslinux version is too old. Update it or Parted Magic won't boot. Ubuntu typically comes with very old versions of syslinux." (And, sure enough, the version in Synaptic seems to be well behind the latest version on the Syslinux site).

---

### Post by thomasaaron on 2009-10-07
Jwbrase,

> Re-read my above post, please.

I don't see anything in your post that indicated creating an Ubuntu Live CD was an impossibility. Most folks this forum try to maintain a friendly, non-condescending demeanour.

> Can that create a PartedMagic Live USB?
No. It will only create an Ubuntu USB image. I'm also not sure if it will include gparted on it.

If you have an .iso already for PartedMagic, I can send you instructions on how to burn it to a USB from a terminal. Perhaps that will help. If so, please email me at support---at---system76---dot---com.

---

### Post by Eldera on 2009-10-07
[quote=thomasaaron]I'm also not sure if it will include gparted on it.[/quote]

It does include gparted. I used System -> Administration -> USB Startup Disk Creator to make a live USB of Hardy a few weeks ago for emergency purposes.

[quote=jwbrase]it's a fairly heavy download, which is a bit hard (but not impossible) to do on my connection,[/quote]

I understand how you feel. Until about a year ago I was using a dial-up connection (before I started using Ubuntu) and I worried every time I had to do a large download. Some of them timed out and some were corrupted and unusable. I hope you find a way around your problem.

---

### Post by jwbrase on 2009-10-07
> **thomasaaron said:**
> 
I don't see anything in your post that indicated creating an Ubuntu Live CD was an impossibility. Most folks this forum try to maintain a friendly, non-condescending demeanour.

Not an impossibility, just a difficulty. Sorry if I sounded a bit snippy, but your directions were mostly about how to use GParted, which I already knew how to do, while my main question was about how to get to that point (Whether it would be easier/possible to shrink /home, add a new partition, and use that partition as a second / partition, or whether having two / partitions or unmounting /home during operation is impossible, and I would have to press on with attempts to get a LiveUSB running).

> 
No. It will only create an Ubuntu USB image. I'm also not sure if it will include gparted on it.

If you have an .iso already for PartedMagic, I can send you instructions on how to burn it to a USB from a terminal. Perhaps that will help. If so, please email me at support---at---system76---dot---com.

I do have an ISO, and I also have a zip file purpose built for USB. I had been following the readme in that zip file, and couldn't get it to boot. I had tried figuring out a few other methods without luck. Just before my last post I had a look at [these instructions]("http://partedmagic.com/documentation/130-creating-the-liveusb.html") on the PartedMagic site, and saw that I'd need a newer version of Syslinux than is in the Ubuntu repositories. I found an *.rpm of the latest version and converted it to a *.deb with alien, only to have Ubuntu refuse to install it, claiming that the presently installed version (3.63), is newer than the one I'm trying to install (3.83), which, I suppose, is a quirk of having converted it with alien.

At this point it seems the obvious thing to do would be to uninstall Syslinux 3.63 in Synaptic and then install 3.83. The potential problem with this is that I don't know if Ubuntu would try installing 3.63 back over 3.83 at the next update, or what other problems this might cause due to the system being confused over which is more recent. (Doing it this way would also involve removing the USB Startup Disk Creator, at least temporarily, since it depends on Syslinux, but I don't see that as a huge problem).

If anyone can direct me to a *.deb of 3.83, or tell me how to make sure the one I generated with alien doesn't cause trouble down the road due to Ubuntu thinking it's older than the current version in the repositories, I think I should be able to do the rest myself (assuming no gremlins or Murphy's Lawyers show up).

---

### Post by jwbrase on 2009-10-07
> **Eldera said:**
> It does include gparted. I used System -> Administration -> USB Startup Disk Creator to make a live USB of Hardy a few weeks ago for emergency purposes.

That's good, if all else fails.

> 
I understand how you feel. Until about a year ago I was using a dial-up connection (before I started using Ubuntu) and I worried every time I had to do a large download. Some of them timed out and some were corrupted and unusable. I hope you find a way around your problem.

I've not had a corrupt download on this connection, it's just that I never know how long it will take. It's to a wireless router over in the next building, and sometimes it flies along at 300 kB/s or more, sometimes I have time between bits to organize a betting pool on whether the next will be a one or a zero, and sometimes I don't have any connection at all (rarer since I moved my computer over by the window).

The larger the download, the more likely it is that some part of it will be delivered by snail.

---

### Post by miniyak on 2009-10-07
if all else fails Ubuntu can send you a free live cd.
Here-[https://shipit.ubuntu.com/]("https://shipit.ubuntu.com/")

Though it may take just as long as your web connection.(might be faster buying but idk)

---

### Post by _duncan_ on 2009-10-07
Hi,

I don't use System76, so my comments are based on a standard Ubuntu install.

One way to free up some space in the / partition is to clean out all the deb packages downloaded from the ubuntu repos while installing/updating packages. Depending on how much you installed in the past, these deb files can take up about 500 MB - 1.5 GB. The location is /var/cache/apt/archives.

The safe thing to do is to create a folder in your /home partition, copy over all the deb files found in the aforementioned folder, open a terminal and issue the following command:

```
sudo apt-get clean
```

The nice thing about stowing away these deb files is if you need to reinstall ubuntu in the future. You can just reinstall as usual, then copy back all those deb files to the /var/cache/apt/archives from the cached /home folder, and save yourself hours of downloading.

---

### Post by Derath on 2009-10-08
One of the workarounds that I have done, if just needed for a short period of time, is to use a jumpdrive, and copy the files abd make a symlink for /var/cache/apt to the jumpdrive... it'll at least get packages installed, and then can always remove the symlink, copy back, apt-get clean. I've also had an occassion to move that to the my /home directory just to get by it

---

### Post by jwbrase on 2009-10-08
Can anybody give a recommendation as to the best course of action with regards to my above post about Syslinux 3.83 and 3.63?

---

### Post by jdb on 2009-10-08
> **jwbrase said:**
> Can anybody give a recommendation as to the best course of action with regards to my above post about Syslinux 3.83 and 3.63?

That's probably something that no one on this list has ever had to do.
Here's something you might try.
The root user doesn't use the home directory, it uses /root.
I believe there is an option somewhere in one of the setup menus where you can allow root to log on from the startup screen.
You'll have to assign root a password first.

sudo su
passwd
exit

After rebooting & logging in as root you should be able to:

1) make a dummy directory & name it something like dummy.

2) copy your configuration files from /home to /dummy

3) unmount home

4) delete the empty directory home

5) rename dummy to home

6) make a new directory, something like bigPart

7) edit fstab to change the mount point from /home to /bigpart

You should now be able to log in as yourself & have the big partiton mounted on /bigPart.
After you mirror your system stuff to it you can put an entry in /boot/grub/menu.lst so you can boot to it.

If you decide to try something like this,
make sure you research any part of this you don't understand.
It's a little scary to start fooling around when you don't have a live CD available.

jdb

---

### Post by thomasaaron on 2009-10-08
> Can anybody give a recommendation as to the best course of action with regards to my above post about Syslinux 3.83 and 3.63?

I'm really not trying to be worthless here, but honestly that really seems overly complicated for resizing your partitions. I've never done it that way before, though, so maybe I'm mistaken.

I would make a USB Ubuntu drive and use GPARTED.

---

### Post by jwbrase on 2009-10-08
> **jdb said:**
> That's probably something that no one on this list has ever had to do.
Here's something you might try.
The root user doesn't use the home directory, it uses /root.
I believe there is an option somewhere in one of the setup menus where you can allow root to log on from the startup screen.
You'll have to assign root a password first.

sudo su
passwd
exit

After rebooting & logging in as root you should be able to:

1) make a dummy directory & name it something like dummy.

2) copy your configuration files from /home to /dummy

3) unmount home

4) delete the empty directory home

5) rename dummy to home

6) make a new directory, something like bigPart

7) edit fstab to change the mount point from /home to /bigpart

You should now be able to log in as yourself & have the big partiton mounted on /bigPart.
After you mirror your system stuff to it you can put an entry in /boot/grub/menu.lst so you can boot to it.

If you decide to try something like this,
make sure you research any part of this you don't understand.
It's a little scary to start fooling around when you don't have a live CD available.

jdb

I'd thought of the idea of trying something based on logging in as root, but had decided to forgo that for the moment and see what I could do with other methods. One thing though: I thought revealing how to create a root password was forbidden on these forums, with the official policy being "if you want to know, look somewhere else, we won't be responsible for you doing stupid things to your machine while logged on as root". As a result, I hadn't asked (though I had started considering looking elsewhere once this situation gave me a potential use for such knowledge).

---

### Post by jwbrase on 2009-10-08
> **thomasaaron said:**
> I'm really not trying to be worthless here, but honestly that really seems overly complicated for resizing your partitions. I've never done it that way before, though, so maybe I'm mistaken.

I would make a USB Ubuntu drive and use GPARTED.

Well, at the moment, since I'm willing to learn and on a flaky connection, big, as yet undownloaded, and simple takes a back seat to small, downloaded, and complex.

That said, jdb's comment about "fooling around" without a live cd/usb being "scary" does make me think that it is probably best to make sure I have a means of reinstalling on hand and that the download time is worth it, regardless of complexity. (Heck, even if I wasn't trying to repartition it would be a good idea)

---

### Post by Maczimus on 2009-10-10
You could also try unetbootin...

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

it will download an iso of your choice and place it on the USB flash device for use. many different distros and utilities are available. i believe gparted is on there as well. hope it will help.

---

### Post by theZoid on 2009-10-13
> **jwbrase said:**
> Re-read my above post, please.

I know how to use GParted. The problem is finding a LiveCD. But all of my Live CD's (PartedMagic, Ubuntu 9.04, etc.) are at home in the States, and I don't plan on going back there for a year (I knew I was forgetting something). I also don't have any blank CD's to burn to. I do have a USB stick, but attempts to make a Live USB of PartedMagic have so far failed.

May I?  How much space of your / is used?  I always use a 12 gig / and I pretty much install the whole world.  I will get up to around 3 gigs left, but it never goes over that, now with Ubuntu for 2 years.  Are you a gamer?

I'm just saying, there might be no reason to panic too much about the size.

so, OPTION B:  do nothing or hold back on some games or keep save files.  Where are you? Congo or somewhere?  you really should order the Live install CD if you have a flaky connection..then if you need to you can resize with that...need it anyway.  Sorry, it's late here now..just running it up the flagpole to see if I get a salute...:)  Hope you get it resolved.

---

### Post by satsujinka on 2009-10-14
Just as an alternate suggestion. Most programs can be installed to your /home directory. To give you an idea of how well this works I have only about 5gb for / (another 5gb for /tmp and the rest for /home.)

---

### Post by jwbrase on 2009-10-30
As I mentioned in my previous post, I decided it would be a good idea to have a LiveUSB on hand just as an emergency measure, and so I did eventually make a LiveUSB.

The problem is that I can't get it to boot to a GUI.

It gives the splash screen, then gives me a console screen with "Loading... Please wait," and then drops into Busy Box with an "initramfs" prompt.

Searching for "initramfs," I eventually found [this thread]("http://ubuntuforums.org/showthread.php?t=765195"), which, after reading the first and last few pages, seems to indicate that the problem is a long standing kernel issue that affects certain hardware, and that people have run into it on other distros as well.

Are there any known workarounds for System76 hardware?

(Specifically, Pangolin with 2.1 GHz Core Duo, 3 Gigs RAM, and 300 gig HD).

> **satsujinka said:**
> Just as an alternate suggestion. Most programs can be installed to your /home directory. To give you an idea of how well this works I have only about 5gb for / (another 5gb for /tmp and the rest for /home.)

Really? I've looked for options to do that in Synaptic and haven't found anything...

> **theZoid said:**
> Where are you? Congo or somewhere?

No, Germany, but I'm an exchange student on a budget, so I'm using a wireless service run by another student that costs about half as much as it would to get a wired connection in my own room. The router is in the next building over, so the signal isn't always great. Anyways, I've now got the LiveUSB.

---

### Post by Maczimus on 2009-10-30
> **jwbrase said:**
> Re-read my above post, please.

I know how to use GParted. The problem is finding a LiveCD. But all of my Live CD's (PartedMagic, Ubuntu 9.04, etc.) are at home in the States, and I don't plan on going back there for a year (I knew I was forgetting something). I also don't have any blank CD's to burn to. I do have a USB stick, but attempts to make a Live USB of PartedMagic have so far failed.

look for unetbootin. will work on linux, mac and windows computers and will make a usb bootable disk from many different distros and i believe parted magic to be one of them.

---

