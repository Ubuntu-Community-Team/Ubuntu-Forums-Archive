---
title: "Install says no hard drive"
date: 2019-05-12
forum: Windows
---

### Post by acefromspace on 2019-05-12
Windows XP install disc starts, then says I have no hard drive. I am using ubuntu 14.04 right now, so ran disk utility and self-test. Says my hard drive is OK with 233 bad sectors (but it has shown this before) Laptop is Toshiba Satellite A-205 Also, BIOS shows hard drive. Even Ubuntu install disc starts, then fails. I was going to do dual boot (fresh install) Windows XP (will never see internet... just need it for a canon scanner) and Ubuntu 16.04

---

### Post by oldfred on 2019-05-12
Are you sure there is not a Canon driver somewhere.
Have only used HP in recent years and its cheap printers (with expensive ink) have very good scanners. Do not print much so HP ok.
Years ago I had a new Canon printer, but Ubuntu had no drivers. But after a lot of looking around a Canon Asia site seemed to have more support for Linux and had a driver.

XP only installs to a blank drive or a primary NTFS partition with the boot flag and MBR. If you have Linux partitions on drive, XP will not see it.
Also I stopped using XP as a then new SSD needed AHCI mode in BIOS and XP would not boot with AHCI on. Turning AHCI on, spending all morning once a week to update XP for one app became just not worthwhile. That old system took 5 min to boot XP, but did not tell me it needed chkdsk and after that it booted really quick, only 3 min. Of course Ubuntu was only 40 sec.

---

### Post by acefromspace on 2019-05-12
I have installed XP many times from this same disc. It asks if it can delete everything on hard drive and install (has always worked before) Am I correct that windows uses first part of hard drive for MBR and if this part is not usable it will not install? Ubuntu does not seem to care where it boots from. I want to do dual boot (windows and ubuntu) and have done this before doing windows first, then creating free space partition to install ubuntu. Strange thing is even my ubuntu install disc starts, then won't work. Is this because my hard drive is fried?

---

### Post by acefromspace on 2019-05-12
About the canon scanner... can I just use WINE and windows driver (that I have)?

---

### Post by oldfred on 2019-05-12
Drivers do not normally work in wine, just limited Windows software and some better than others.

Could be hard drive, since now both seem to have issues. Normally drives internally map back sectors, so not used. And increasing number of bad sectors means drive is dying or dead.

---

### Post by acefromspace on 2019-05-13
Forget about the scanner for now... more concerned about my hard drive. I have done self-test in the pastand same thing... 233 bad sectors and shows OK. No more bad sectors since then.

---

### Post by oldfred on 2019-05-13
Have you run the full fsck on every ext4 partition? If NTFS, you have to run chkdsk from Windows.
To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Then perhaps this:
[https://askubuntu.com/questions/241944/how-to-fix-the-hard-drive-bad-sector](https://askubuntu.com/questions/241944/how-to-fix-the-hard-drive-bad-sector)

---

### Post by acefromspace on 2019-05-13
I did the "quick" self-test... there is also an option to do "extended" self-test. Should I try that or do as you suggested? Problem is I can't get live ubuntu to work with DVD or USB. It starts, then goes to black window with text and numbers... no way to take screenshot, and don't want to write the whole thing down by hand. It is mostly pairs of numbers. I have never had this issue before with this laptop, but it is old and high mileage. No funds or I would just buy new hard drive.

---

### Post by oldfred on 2019-05-13
If you have trouble booting USB or DVD, it may be RAM or other hardware issue. Bad RAM can cause defective writes onto a drive. And many other issues when systems get old.

---

### Post by acefromspace on 2019-05-13
No surprise if the laptop has other issues. I could do memory test (have "ultimate boot disc" with memtest) I did post this on other forums here, but broke the rules and double posted... panicked because it showed 0 views (I was told that doesn't work)

---

### Post by VMC on 2019-05-13
What model Cannon scanner? Mine is N1220U, and builtin Ubuntu scanner works very well. VueScan was the only one that worked for Windows.

---

### Post by acefromspace on 2019-05-14
Booted "ultimate boot disc" and ran memtest. No errors (2 passes) Seems the memory is OK. My son (know more about computers than me) suggested removing hard drive and re-inserting (maybe bad connections) Also, I will confirm what brand the hard drive is and get proper utility to diagnose drive.

---

### Post by acefromspace on 2019-05-14
Scanner is canon 9950f and I am aware of vuescan. Great software... not free, but affordable (will try it when I can) Also like turboprint for printing.

---

### Post by acefromspace on 2019-05-14
Using a hard drive diagnostic that is on my "ultimate boot disc" Running scan for bad sectors... will take several hours so I'll post results later.

---

### Post by acefromspace on 2019-05-15
Hard drive seems OK (used HDAT2) Took all night to scan.

---

### Post by acefromspace on 2019-05-15
Got ubuntu 16.04 to install, but had issues during install. Did restart and got message about graphics. Looked it up and I don't meet system requirements (RAM and graphics) Going back to ubuntu 12 0r 14. Don't really need windows because I'm using free version of viewscan.

---

### Post by acefromspace on 2019-05-15
My old laptop is doing fine... went back to ubuntu 12.04 RAM and graphics OK. Still don't know why windows xp install didn't work.

---

### Post by CelticWarrior on 2020-01-31
> **acefromspace said:**
> My old laptop is doing fine... went back to ubuntu 12.04 RAM and graphics OK. Still don't know why windows xp install didn't work.

Unsupported OSes shouldn't be used connected to the internet. This is NOT debatable!
Either Ubuntu 12.04 - support ended in 2017 - and especially Windows XP - support ended in 2014!!! - shouldn't be used outside of retrocomputing experiments, without internet connection, and by more experienced users.

---

