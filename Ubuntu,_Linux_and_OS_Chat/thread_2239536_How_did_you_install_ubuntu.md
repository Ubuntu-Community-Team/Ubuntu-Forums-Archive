---
title: "How did you install ubuntu?"
date: 2014-08-14
forum: Ubuntu, Linux and OS Chat
---

### Post by Jonathan Precise on 2014-08-14
How did you install ubuntu?

Maybe you have it installed through virtualization? Maybe you have it installed to a USB disk?

This thread is to share the way you installed ubuntu. Please do **not** post support questions about installation issues.

---

### Post by matt_symes on 2014-08-14
Other => debootstrap and chroot from an existing install.

---

### Post by Jonathan Precise on 2014-08-14
> **matt_symes said:**
> Other => debootstrap and chroot from an existing install.

I also had to do this to install ubuntu 32-bit in UEFI mode.

Is there a way to change the vote?

---

### Post by QIII on 2014-08-14
"All of the above", the answer I would give, seems to be missing.

Good thing it's a multi-select.  :)

---

### Post by frankmorris2 on 2014-08-15
Hello,

At work, I use a basic Ubuntu Server image. I clone the machine and I use SaltStack to set it up.

At home, I enjoy the CD/DVD installation :-)

Just my 2 cents.

Have a nice day

---

### Post by pizzalover1974 on 2014-08-16
Bought a pre made DVD online from a store seller of copies of multiple distros. As my DVD RW is a bit dodgy. 

I have a Pure install of Ubuntu Studio on my Media PC and had Ubuntu that I customized on my Dual WIN/Linux gaming PC...I now have Netrunner OS on that main PC. 

Netrunner contribute to Kubuntu and is based on the buntu's so i'm not so naughty not having Ubuntu on main PC.

---

### Post by Erik1984 on 2014-08-16
*To HDD alogside other OSes*

Only 'special' thing to add is that I installed Kubuntu over an existing Ubuntu install to preserve /home. [https://wiki.ubuntu.com/UbiquityPreserveHome](https://wiki.ubuntu.com/UbiquityPreserveHome)

---

### Post by Tar_Ni on 2014-08-16
I personally don't like dual booting. To me, it's one thing or another. So, on my laptop I choosed to remove Windows and install Ubuntu as my one and only OS. Same thing on my older Pentium 4 desktop computer, byebye XP and Lubuntu owns the machine now, otherwise it would be useless.

---

### Post by uRock on 2014-08-16
> **QIII said:**
> "All of the above", the answer I would give, seems to be missing.

Good thing it's a multi-select.  :)

Same here. :D

---

### Post by Irihapeti on 2014-08-17
Ditto. The only one I haven't done is through virtualisation. My favourite method seems to be via debootstrap followed up with chroot.

---

### Post by egrrenov on 2014-08-17
can i use ubuntu in iphone 6

---

### Post by Imperium Guard on 2014-08-17
I'd like to know how you guys partitioned it. I resized my Windows partition down to allow some room for Ubuntu, and made 2 partitions, a swap and an ext4 partition. I think there's a different way to do it, but this scheme works for me.

---

### Post by Erik1984 on 2014-08-17
> **Imperium Guard said:**
> I'd like to know how you guys partitioned it. I resized my Windows partition down to allow some room for Ubuntu, and made 2 partitions, a swap and an ext4 partition. I think there's a different way to do it, but this scheme works for me.

That's a fine setup, I have something similar. It's also quite popular to put /home on its own different partition, but that's not necessary to keep personal files when reinstalling Ubuntu.

---

### Post by Rob Sayer on 2014-08-17
I think one of the most important things is *before* you install.  I've always used System Information in WIndows or the live boot cd/usb to see what hardware is there.  Then I check for support issues.  That's only been an issue with my atom 2600 netbook, but at least I knew what I was getting into.  Fortunately 14.04 has a recent enough kernel that these seem to have been solved.

The only nasty surprise I've actually had was when I updated 12.04 on my old Compaq laptop with 4xxx series AMD graphics.  All of a sudden I had top boot with nomodeset and 3D acceleration was gone.  I realize that's not an install issue but it's  not what a lot of users would expect from an LTS release ...

Ditto on installing with a separate /home partition.  Isn't that the default in Debian?  It's so handy I thing it should be the ubuntu default scheme.  Performance is better too.

---

### Post by ngockhuongkk on 2014-08-19
i install ubuntu in vitua machine, for learning for code sell

---

### Post by speedwell68 on 2014-08-19
On my main machine I have Lubuntu 14.04 and a small W7 partition, just for ISP support issues.  On my other machine I have Ubuntu GNOME exclusively.  If I had my way I'd not have the W7 install at all, but UK ISPs really baulk at the idea of an OS that isn't Windows and often refuse any form of technical support without it.  I have had a few technical support calls to British Telecom where they suggested that Linux of any form was a virus and was causing my issues, and not the on street junction box that was spewing out water after a massive storm.

---

### Post by Jessie_James_A._At on 2014-08-22
hit directly to *To HDD as only Main OS*

---

### Post by Cliff_Simonds on 2014-08-23
> **Erik1984 said:**
>  It's also quite popular to put /home on its own different partition, but that's not necessary to keep personal files when reinstalling Ubuntu.
Very true. More often than not it can be problematic. That's why I simply use Backup, which also backs-up all my programs settings: conky, thunderbird, firefox, audacious, even some system settings---etc. I simply reinstall ubuntu (or install latest version) and my programs and then run restore to original files. Finished-- WOW a whole half hour and I'm up and running.:p
Something Microdollars can only dream about.

---

### Post by fireflower on 2014-08-23
Originally, out of desperation. See sig.

---

### Post by nadrach on 2014-08-23
Generally from USB disk, but with some of the h/w I have to resort to a CD/DVD because the BIOS does not have the ability to load from USB (yes ... there are some perfectly usable machines around that do not). I started with a very early Knoppix, after Slackware, Debian, Red Hat and a bunch of others ... then stayed with KDE for a long time, mostly on Kubuntu, until it became too resource heavy for the machines I had available ... enter Lubuntu after a brief excursion with Ubuntu ... I reserve judgement on Ubuntu/Unity at the moment.

---

