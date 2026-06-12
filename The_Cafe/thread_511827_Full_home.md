---
title: "Full /home"
date: 2007-07-28
forum: The Cafe
---

### Post by vexorian on 2007-07-28
Hmm I have just noticed how  dangerous a full /home/ is. Nautilus barely showed an small warning that faded away instantly I could hardly read 'disk full' I was actually browsing a read-only ntfs partition so it was odd, then I noticed /home/ was full when I pasted something to desktop.

The issue is, that you can't even clean space since apps will just crash eventually because /home/ is fulll... It was hard to take my downloads folder and move it to /

I think people shouldn't be encouraged to have /home/ in a separate partition, it is very hard to decide what's a good  amount of stuff for /home and / , in my previous attempt I gave too much to /home/ and then installing stuff got hard, in the newest attempt I gave too little to /home/ .

I also noticed that installing another OS and keeping the /home is not really that good, if anything it is messy, so I am really starting to think it is better to just have swap and /

Also discovered it is not really a good idea to collect icon themes if you are not going to use them...

---

### Post by aysiu on 2007-07-28
It depends on how much total hard drive space you have. If you have 20 GB or less, a separate /home partition may be a bad idea. If you have 10 GB or less, a separate /home partition is a *terrible* idea!

If, however, you have 30 GB or more, a separate /home partition should benefit you. I'd allocate no more than 8 GB for the / partition and then give the rest to /home.

---

### Post by init1 on 2007-07-28
> **vexorian said:**
> Hmm I have just noticed how  dangerous a full /home/ is. Nautilus barely showed an small warning that faded away instantly I could hardly read 'disk full' I was actually browsing a read-only ntfs partition so it was odd, then I noticed /home/ was full when I pasted something to desktop.

The issue is, that you can't even clean space since apps will just crash eventually because /home/ is fulll... It was hard to take my downloads folder and move it to /

I think people shouldn't be encouraged to have /home/ in a separate partition, it is very hard to decide what's a good  amount of stuff for /home and / , in my previous attempt I gave too much to /home/ and then installing stuff got hard, in the newest attempt I gave too little to /home/ .

I also noticed that installing another OS and keeping the /home is not really that good, if anything it is messy, so I am really starting to think it is better to just have swap and /

Also discovered it is not really a good idea to collect icon themes if you are not going to use them...
Clean it out with a Live CD. I don't really see the benefit of having separate partitions for everything. I think you can fix it with a fstab change, but I'm not sure. It's risky business messing with that sort of thing.

---

### Post by aysiu on 2007-07-28
> **init1 said:**
> Clean it out with a Live CD. I don't really see the benefit of having separate partitions for everything. I think you can fix it with a fstab change, but I'm not sure. It's risky business messing with that sort of thing.
It's not for *everything*--just /home.

A separate /home partition allows you an easy way to do clean reinstalls without losing your personal settings and files.

---

### Post by init1 on 2007-07-28
> **aysiu said:**
> It's not for *everything*--just /home.

A separate /home partition allows you an easy way to do clean reinstalls without losing your personal settings and files.
But you can segregate it into different partitions, I think some distros recommend putting /boot into a separate partition. I guess it has it's purposes.

---

### Post by aysiu on 2007-07-28
Sure you *can* have separate partitions for everything (including /boot), but the only one I recommend for desktop users is a separate /home.

---

### Post by celsofaf on 2007-07-28
I don't realy see the benefits of a separate /home partition, but of a separate partition for personal data, yes definetly. :)

---

### Post by aysiu on 2007-07-28
/home is where your personal data is stored.

---

### Post by yatt on 2007-07-28
> **aysiu said:**
> Sure you *can* have separate partitions for everything (including /boot), but the only one I recommend for desktop users is a separate /home.
I have a I have only / and /boot. I'd probably do just one big partition, but / is on a RAID0 and grub does not have the drivers needed for RAID.

---

### Post by bonzodog on 2007-07-29
I would say allocate 8-10GB to root, as you are unlikely to fill that up, then allocate 500MB Swap, and the rest to /home.

Most modern PC's ship with a minimum of 80GB of space (this is two years old and has 160GB).
But if you are going to have a lot of stuff, you might be better getting an external HDD, you can get 500GB disks now.

---

### Post by vexorian on 2007-07-29
problem was mostly due to my XP partition taking most of the hard drive, the good thing is that ntfs support lately has improved so I actually use it to host music and some games that work well on WINE.

---

### Post by koenn on 2007-07-29
> **vexorian said:**
> 
The issue is, that you can't even clean space since apps will just crash eventually because /home/ is fulll... 
Thats's way a certain portion (default in Ubuntu : 5%) of any partition is reserved for root. That way, you can always log in as root, and clean up / move stuff / add drives / ... . You'd probably have to do it from a shell (maintenance mode)  in stead of drag&drop, but at least you can get your system to survive a serious lack of disk space.

---

### Post by init1 on 2007-07-29
> **bonzodog said:**
> I would say allocate 8-10GB to root, as you are unlikely to fill that up, then allocate 500MB Swap, and the rest to /home.

Most modern PC's ship with a minimum of 80GB of space (this is two years old and has 160GB).
But if you are going to have a lot of stuff, you might be better getting an external HDD, you can get 500GB disks now.
8-10GB? I filled up 30GB Ubuntu partition. There's barely any space left.

---

### Post by tbroderick on 2007-07-29
> **init1 said:**
> 8-10GB? I filled up 30GB Ubuntu partition. There's barely any space left.

What???

---

### Post by init1 on 2007-07-29
> **tbroderick said:**
> What???
I kept the ISO's I downloaded. 
adamantix-v1.0.4-4.iso              kwort-2.2.iso
alinex-live-tic.iso                 LinuxMint-2.2-Light.iso
alinux.iso                          mandriva-one-2007-free-gnome.iso
Archlinux-i686-0.8-Voodoo.base.iso  MCNLive-VirtualCity.iso
arklinux-2006.1.iso                 murix-2.6.19-murix-2006-12-31__12-51-00.iso
BeatrIX_2005.1F.iso                 Myah-OS-2.3-SE.iso
belenix0.5.1.iso                    MySlax2.iso
BLAG-60000.iso                      MySlax3.iso
bluewall-1.2.2-lite.iso             nubuntu-6.10-386.iso
bootcd-i386-5.3.iso.gz              olivebsd.iso
bootcd-i386-5.3tty.iso              opendarwin-7.2.1.iso
cdlinux.iso                         openlab-live-4.0.0.iso
crux-2.3.iso                        OpenLX-Edge1.0_Desktop.iso
DesktopBSD-1.0-x86-CD.iso           Oralux_0.7_alpha.iso
dexiso.iso                          pclinuxos-TR4.iso
dtCDlinux-0.5.7.iso                 penguinsleuth-07-05-2003.iso
Eagle_2_2_0.iso                     pld.iso
Eagle_linux.iso                     privare.iso
ekaaty-aymores-disc1.i386.iso       railslive-0.2.1.iso
Evinux-200700e.iso                  ReactOS.iso
famelix-1.3.iso                     RIPLinux-2.4.iso
fdfullcd.iso                        RIPLinuX-2.4.iso
finnix-89.0.iso                     shiftgnome031.iso
FreeSBIE-2.0-RELEASE.iso            SimplyMEPIS-CD_6.5.00_32.iso
freespire_1.0.13.iso                slax-5.1.8.1.iso
frenzy-1.0-ext-EN.iso               slax-6.0.0rc3.iso
GNUSTEP-i486-1.0.iso                Slax_Frodo1.iso
GoboLinux-013-i686.iso              syllable-0.6.3.iso
gparted-livecd-0.3.4-5.iso          Syllable-0.6.3-LiveCD-1.iso
Grafpup_deluxe-104.iso              symphonyos-2006-12.iso
hikarunix-0.4.iso                   talinux-0.2.0-rc1-i386-20041207.iso
IDE-3.1.2a.iso                      trinity-rescue-kit.3.2-build-279.iso
INSERT-1.3.8a_en.iso                underground.iso
install-x86-minimal-2006.1.iso      visopsys-0.66.iso
JULEX0.5.2.26.iso                   VL-5.8-std-Gold.iso
Kinneret-0.6RC5-yarden.iso          wolvix-hunter-1.0.5.iso
kubuntu-7.04-desktop-i386.iso       yos-i686-2.1.0-4.iso

---

### Post by tbroderick on 2007-07-29
> **init1 said:**
> I kept the ISO's I downloaded. 


You downloaded them to your root partition?

---

### Post by taishi28012 on 2007-07-30
If you really downloaded all that to root then you must have screwed up bad somewhere along the line.

---

