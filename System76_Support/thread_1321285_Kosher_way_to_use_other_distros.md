---
title: "Kosher way to use other distros?"
date: 2009-11-09
forum: System76 Support
---

### Post by ebeyer on 2009-11-09
Is there an officially-endorsed method for using distros other than Ubuntu with the Starling netbook?  I'm considering trying OpenSuse but would like to avoid any nasty surprises like broken drivers and such.

EB

---

### Post by Aemaeth on 2009-11-09
Depending on your hardware you can always 

+ check the distro pages and look at the system requirements

+ use live on CD os's like knoppix or damm small linux

+ check [http://distrowatch.com/](http://distrowatch.com/) and browse the repos...

Cheers!

---

### Post by Lee_Machine on 2009-11-09
Ubuntu is the only officially supported Linux distribution that S76 supports, with their driver. 

A good way to see if all your hardware will work is to try a live cd. 

Also check which kernel your laptop has. If the distro you want to install is equal to or greater, then all your hardware should work.

Distros I would recommend are Linux Mint, Fedora, and the new Mandriva is nice.

You have a netbook, so I would try out Moblin, Ubuntu Moblin Remix, and Jolycloud.

---

### Post by jdb on 2009-11-10
> **ebeyer said:**
> Is there an officially-endorsed method for using distros other than Ubuntu with the Starling netbook?  I'm considering trying OpenSuse but would like to avoid any nasty surprises like broken drivers and such.

EB

Just make sure you do a backup first, If it doesn't work out, no harm done.
Let us know what you think, I tried Suse about 10 years ago but I imagine it's changed a bit :)

jdb

---

### Post by Simian Man on 2009-11-10
I don't uses System76, so take this with a grain of salt, but I would imagine that they chooses devices that have solid support in the mainline kernel.  I would guess you'll find that just about any distro will work well.

---

### Post by thomasaaron on 2009-11-10
Actually, the System76 Driver applies a few important patches to the Starling. I'm sure other distros could be *made* to work on it, or the System76 driver could be hacked to run on other distros, but I'm pretty sure that most other distros will not be that solid out of the box.

That said, we're working hard to get some of our patches into Ubuntu's mainstream kernel by the next release. If that goes well, I think you will see more distros running well on the Starling.

---

### Post by betrunkenaffe on 2009-11-11
On this: OpenSuse works well on PanP4. I haven't tested camera, fingerprint reader, SD Card or eSata ports..

I'm not even using nvidia drivers yet (using beta).

---

### Post by jml on 2009-11-11
I have to agree with Tom an this one.  While the Starling generally comes with very Linux friendly hardware, the wireless card is a different issue.  The wireless card that comes with the Starling has major issues with Linux.  In my opinion, the main benefit that the System 76 driver offers is a patch for the wireless card.

I have tried live CD versions of Fedora, Mandriva, PCLinuxOS, Mepis, Linux Mint, Anti-X, PuppyLinux, DamnSmall Linux, and a few others I can't remember and was never able to get the wireless card to work properly.  In my opinion, a netbook with faulty wireless is worse than useless.  So I still run Ubuntu on my Starling.  

Joe

---

### Post by jmwink on 2009-11-12
The Crunchbang distribution is based on Ubuntu, and unlike Mint, the System 76 driver works without any sort of hacks.

---

### Post by Simian Man on 2009-11-12
> **jml said:**
> I have to agree with Tom an this one.  While the Starling generally comes with very Linux friendly hardware, the wireless card is a different issue.  The wireless card that comes with the Starling has major issues with Linux.  In my opinion, the main benefit that the System 76 driver offers is a patch for the wireless card.

I have tried live CD versions of Fedora, Mandriva, PCLinuxOS, Mepis, Linux Mint, Anti-X, PuppyLinux, DamnSmall Linux, and a few others I can't remember and was never able to get the wireless card to work properly.  In my opinion, a netbook with faulty wireless is worse than useless.  So I still run Ubuntu on my Starling.

Just out of curiosity, if one were to install a downloaded version of Ubuntu to replace System76's OEM version, would that include the patch for the wireless card?

---

### Post by thomasaaron on 2009-11-12
It depends on what computer you have. Straight Ubuntu works out of the box with a lot of wireless cards.

System76 doesn't use a special version of Ubuntu. We install standard Ubuntu and then run our System76 Driver, which identifies the version of Ubuntu being run, the System76 model number of the machine, and applies the appropriate patches. All of the machines are a little different, so different patches are applied on each.

---

