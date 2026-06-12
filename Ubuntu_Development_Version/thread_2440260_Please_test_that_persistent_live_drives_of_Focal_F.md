---
title: "Please test that persistent live drives of Focal Fossa work in your computer(s)"
date: 2020-04-08
forum: Ubuntu Development Version
---

### Post by sudodus on 2020-04-08
[There is an issue with the label for persistence in Focal Fossa](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1863672). The new standard label is 'writable' but the classic label 'casper-rw' should work too, if found during boot. Due to a race condition this fails in some computers.

Acouple of days ago the developer Michael Hudson-Doyle (mwhudson) linked a 'hack' in comment #36 in the bug report

[The 'new' persistent live method starting in 19.10 no longer works](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1863672).

[**This hack**](https://people.canonical.com/~mwh/casper-initrd.gz) was updated at least twice, and the current version makes my computers work with persistence **both** when using the label **writable** and the label **casper-rw**.

Please read the discussion after comment #36 and above all, **please test how it works with *casper-rw* in your computer**.

1. I made a persistent live system from a current version of Lubuntu Focal according to this link:

[help.ubuntu.com/community/Installation/iso2usb/diy](https://help.ubuntu.com/community/Installation/iso2usb/diy)

I used gunzip to extract the hack to **casper-initrd** and created an **extra menuentry** for it in **grub.cfg** and this way I could make persistence work (with the label casper-rw).

2. Of course, you can also use **Rufus** in Windows, you can test standard Ubuntu or some other community flavour (not Lubuntu that I tested) and modify that system to use the hack.

---

### Post by guiverc on 2020-04-08
I'm not sure I fully understand what you're asking, and I've not used a *persistent-live* since maybe 12.04 and that was created by install onto thumb-drive.

On my primary box [d960] I `mkusb focal-desktop-amd64.iso`
(the following was written after it was done, so not program text sorry)
Selected 'create persistent-live', I selected MBR, selected 80% for persistent storage (16gb)

I then walked thumb-drive to d755-8 and booted it, it looked good to me. I `cat >~/blah` and left a text file, then rebooted.

It booted again, and the 'blah' file was there with contents.  (*the only observation I can make is the reboot didn't have a wallpaper; it tells me it's an invalid path, I can fix that I bet easily*)

The `mkusb` worked for me in that simple test, but I'm unsure if it's the creation (ie. running `mkusb`) you want tested, or the booting of a made image on various boxes that you want tested.

It worked perfectly for me, so I saw no need to place a *hacked initrd* onto the thumb-drive, or am I missing something?

Boxes used :-
dell [optiplex] 960 (c2q-q9400, 8gb, amd/ati cedar radeon hd 5000/6000/7350/8350)
dell [optiplex] 755 (c2d-e8300, 8gb, amd/ati radeon rv610/radeon hd2400 pro/xt)

(I've got a few c2d era boxes I can test on..)

---

### Post by sudodus on 2020-04-08
@guiverc,

1. The issue affects getting persistence to work when booting into the USB drive. There is *no issue affecting making* the persistent live USB drive.

2. Since mkusb (mkusb-dus as well as mkusb-plug) are using cloned images of the iso file, and such images are read-only, you cannot test Michael Hudson-Doyle's hack that way. This is the reason why I suggest using my extracting method of [help.ubuntu.com/community/Installation/iso2usb/diy](https://help.ubuntu.com/community/Installation/iso2usb/diy) or Rufus to create the test drive. In these cases you can edit files in a FAT32 partition. Put **casper-initrd** by Michael Hudson-Doyle into the same directory as the standard **initrd** and copy and modify the main menuentry to use it instead of the standard **initrd**.

```

menuentry "Debug Lubuntu" {
        set gfxpayload=keep
        linux   /casper/vmlinuz$casper_flavour  file=/cdrom/preseed/lubuntu.seed quiet splash persistent ---
        initrd  /casper/casper-initrd$casper_flavour
}
menuentry "Start Lubuntu" {
        set gfxpayload=keep
        linux   /casper/vmlinuz$casper_flavour  file=/cdrom/preseed/lubuntu.seed quiet splash persistent ---
        initrd  /casper/initrd$casper_flavour
}

```

3. I think there is no problem with the label 'writable'. What needs to be tested is the label **casper-rw** (on the partition for persistence).

[hr][/hr]
Edit:

4. Would you be helped by, or do you think other potential testers would be helped by a custom image file for this particular purpose?

In case it would help I created such a [compressed image file](https://phillw.net/isos/linux-tools/alpha-beta/lubuntu/) and uploaded it so that you can download it and extract/flash it to a USB pendrive with at least 8 GB. If the drive is bigger you would also have to fill the remaining drive space with a partition and that partition must have a name other than 'writable'.

---

### Post by sudodus on 2020-04-08
I extracted/flashed from the [dedicated compressed image file, which needs at least 8 GB on the target drive](https://phillw.net/isos/linux-tools/alpha-beta/lubuntu/), to a 16 GB Sandisk Extreme USB pendrive with mkusb-dus:

```

dus debug_bug-1863672_with-casper-initrd-8GB.img.xz
sudo partprobe

```

Then I filled the remaining drive space with a dummy partition using gparted. (I could also have expanded the partition for persistence to use all the unallocated drive space with gparted.)

I was testing in my [Toshiba laptop](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/) which suffers from this bug.

When persistence works the /cow line matches that of the partition for persistence.

Using the grub menuentry 'Debug Lubuntu':

```

ubuntu@lubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.8G     0  1.8G   0% /dev
tmpfs           382M  3.0M  379M   1% /run
/dev/sdc1       2.5G  1.9G  659M  75% /cdrom
/dev/loop0      1.6G  1.6G     0 100% /rofs
[COLOR="#0000aa"]**/cow            4.7G   56M  4.5G   2% /**[/COLOR]
tmpfs           1.9G     0  1.9G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs           1.9G     0  1.9G   0% /tmp
tmpfs           382M  8.0K  382M   1% /run/user/999
/dev/sdc3       7.7G  4.0K  7.7G   1% /media/lubuntu/DUMMY
[COLOR="#0000aa"]**/dev/sdc2       4.7G   56M  4.5G   2% /media/lubuntu/casper-rw**[/COLOR]
lubuntu@lubuntu:~$ Debug Lubuntu --> yes persistence

```

Otherwise it may look like this.

Using the grub menuentry 'Start Lubuntu':

```

lubuntu@lubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           382M  1.5M  381M   1% /run
/dev/sdc1       2.5G  1.9G  659M  75% /cdrom
/dev/loop0      1.6G  1.6G     0 100% /rofs
[COLOR="#cc0000"]/cow            1.9G   24M  1.9G   2% /[/COLOR]
tmpfs           1.9G     0  1.9G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs           1.9G     0  1.9G   0% /tmp
tmpfs           382M  8.0K  382M   1% /run/user/999
/dev/sdc3       7.7G  4.0K  7.7G   1% /media/lubuntu/DUMMY
[COLOR="#cc0000"]/dev/sdc2       4.7G   47M  4.5G   2% /media/lubuntu/casper-rw[/COLOR]
lubuntu@lubuntu:~$ Start Lubuntu --> no persistence

```

---

### Post by guiverc on 2020-04-09
Okay

I downloaded (checking md5sum) and then
```
dus debug_bug-1863672_with-casper-initrd-8GB.img.xz
sudo partprobe
```
then used `gnome-disks` to create a partition ('filler', ext4) to use the available space.
I ran 'check disk for defects' out of habit, it reported an error :( so not sure if following can be trusted.. (or it's a result of changes I made..)

rebooted, selected "Debug Lubuntu' this time  (it found an error in 1 file too), which I'm ignoring for now..

My `df -h` at term looks like your first response... (/cow 4.5/4.7gb, I have 'filler' instead of 'dummy' etc)
This was on hp dc7700 (c2d-e6320, 5gb, nvidia quadro nvs 290)

I'll re-try writing thumb-drive, and try again.. and then later this arvo try it on other boxes?
Please confirm this procedure is what you're after (if possible & convenient)

---

### Post by sudodus on 2020-04-09
@guiverc,

Yes, it reports an error because grub.cfg is modified ('persistent' added and one whole menuentry added) so the md5sum for that file does not match :-)

It will be interesting to see

1. If it works with Michael Hudson-Doyle's hack via the menuentry 'Debug Lubuntu'

2. If it works with the standard [FONT=Courier New]**initrd**[/FONT] via the menuentry 'Start Lubuntu'

Based on the results from my computers with different age and 'horsepower' I would expect that some of your oldest computers might fail with the standard standard [FONT=Courier New]**initrd**[/FONT], and I hope that persistence will work with Michael Hudson-Doyle's hack.

[hr][/hr]
If I understand correctly, it works for you with Michael Hudson-Doyle's hack in one HP Core2Duo computer. It will be interesting to get the results from the other old computer(s) too.

If we test a fair set of old computers and the hack makes persistence work in all those computers, we can conclude that Michael has squashed the bug.

---

### Post by guiverc on 2020-04-09
I had re-written thumb-drive before I re-checked on here.
(*but thanks, error again anyway but I have reason so I'll ignore*)
Re-ran test and got same result on same hp dc7700

I'll now list the boxes I got this same result on :-
[COLOR=#000000]
debug & start as per your example :-

hp dc7700 (c2d-e6320, 5gb, nvidia quadro nvs 290)
[/COLOR]
same results for start & debug (as per your debug results) :-

hp 8200 elite sff (i5-2400, 8gb, nvidia quadro 600)[COLOR=#000000]

Nah I'll have to do this on a spreadsheet, record figures in a manner in which I can have checklist type of reminder to know what I've performed, and where I'm up to, and how each perform.  I can then summarize later.  (I'll start again & re-test those boxes)

[/COLOR]https://docs.google.com/spreadsheets/d/18-XMDjy5lWiHFqFww_865jR6hbcHf00MI_Z92PayDMM/edit?usp=sharing

(currently it'll be rather empty; I'll populate it as I can)

---

### Post by sudodus on 2020-04-09
So Michael's hack squashes the bug in these cases

```

computer_____________________________________________________________  'with hack' 'initrd'
dell [optiplex] 755 (c2d-e6850, 5gb, amd/ati radeon rv516/x1300/x1550)  4.4/4.7gb  2.4/2.4gb
dell [optiplex] 990 (i7-2600, 16gb, nvidia geforce gt 6600 gt)          4.3/4.7gb  7.8/7.8gb

```

In live-only systems it is typical that the RAM space allocated for /cow is approx half of the RAM available.

And so far the other computers are not affected by the bug. It looks good :-)

---

### Post by leok2 on 2020-04-09
I checked my oldest machine(Dell [Inspiron] 3521, (i3-3217U, 4GB,  ) with a USB with persistence created by Rufus in Windows 10 and it ran
perfectly - saved files and changed both the Lubuntu theme and wallpaper settings - so obviously I do not need the fix.

---

### Post by sudodus on 2020-04-09
Thanks for sharing this result @leok2 :-)

---

### Post by guiverc on 2020-04-09
I can continue tomorrow; i'm too tired now & calling it quits for today...

---

### Post by sudodus on 2020-04-09
Your results are promising: Most of your tested computers are not affected, and in those affected  Michael Hudson-Doyle's hack squashes the bug.

Have a good night's sleep :-)

---

### Post by C.S.Cameron on 2020-04-09
I am using Focal from 20020325, Rufus 3.9, UNetbootin 677 Windows and mkusb-plug 2.5.5.

Mkusb-plug works fine for me with Persistent live drive except for the amount of time it takes to boot and "...end of device" scrolling.

Rufus worked ok until I dropped casper-initrd into casper folder and renamed it initrd.
Then I got Busybox 
I named initrd back to casper-initrd and changed grub.cfg to suit.
It booted and worked, however it looked like it was booting syslinux.
I then edited txt.cfg to use casper-initrd and again got Busybox.

Unetbootin booted persistent with stock initrd, when casper-initrd was added and syslinux.cfg edited, Busybox resulted.

Computer s used EliteBook and Travelmate booting BIOS.

---

### Post by sudodus on 2020-04-09
@C.S.Cameron,

Thanks for sharing these results :-)

I have a question and a few comments:

- Did you check which label was used in the different cases? We are focusing here to test if persistence works with **casper-rw**, and I think you used a version of mkusb-plug that creates the label **writable**.

- I'm afraid that you are using a deprecated version of Michael Hudson-Doyle's hack, 'casper-initrd'. The current version (downloaded from the same link as the original one) works with Rufus when used by Pete Batard. You can try to download the 'hack', **casper-initrd.gz** again. Or maybe you can download [my compressed image file](https://phillw.net/isos/linux-tools/alpha-beta/lubuntu/). It works for this test.

- On the other hand, if your HP Elitebook and Acer Travelmate work with the standard 'initrd' and 'casper-rw', they are not affected by the bug.

- Maybe you can test in some other computer.

[hr][/hr]
So far (2020-04-09) we have found no HP that is affected (several models are tested), but the following computer brands (in most cases specific details can be found via links from this thread),

. three Dells (two by guiverc and one by me)
. two Intel NUCs (by Pete Batard)
. one ASUS (by Pete Batard)
. one Toshiba (by me) 
. one Lenovo (by me)

and Michael Hudson-Doyle's hack squashes the bug in all these computers.

[hr][/hr]
Edit: more questions:

- Which model of Acer Travelmate is it?
- Do I understand correctly, that your Travelmate is not affected by this bug? That persistence works also with the standard 'initrd'?

---

### Post by C.S.Cameron on 2020-04-09
Hi Sudodus:
I clicked the "This Hack" link ([https://people.canonical.com/~mwh/casper-initrd.gz](https://people.canonical.com/~mwh/casper-initrd.gz)), in your Apr 9 PM and casper-initrd started downloading automatically.
I will check a mkusb-plug drive in my wife's computer, a gigabyte, (I am pretty sure a mkusb-plug drive works okay on it), if not I will look for the latest hack in the bug report and try it. (do you have the latest link handy)?
The Travelmate is a 8572T-6806, (10 years old). I have been testing 20.04 persistent drives on it in many forms, both persistent and Full install.
Cork

---

### Post by sudodus on 2020-04-10
Hi Cork,

I noticed that the current Lubuntu Focal daily iso file contains the 'hack' of Michael Hudson-Doyle: The package casper version 1.445 is bundled with the current Lubuntu iso file dated 2020-04-09. I tested it (made a persistent live USB-connected SSD) in one of my computers that were affected by this bug, the Toshiba. Persistence works with the label 'casper-rw' :-)

So it is easy to

- simply use **mkusb-plug with the [current Lubuntu Focal daily iso file](http://iso.qa.ubuntu.com/qatracker/milestones/408/builds/210430/downloads)**
- change the label of the partition for persistence from 'writable' to 'casper-rw'
- and then test if persistence works.

I guess this is what you mean in post #15.

[hr][/hr]
Yesterday and the day before yesterday we used the image file from [this link](https://phillw.net/isos/linux-tools/alpha-beta/lubuntu/) and **described in post #4** above. And if you want to see the difference with and without the 'hack' of Michael Hudson-Doyle it is still a good way to test. (It is easier than to make an extracted system and add the 'hack' of Michael Hudson-Doyle into that system manually.)

---

### Post by guiverc on 2020-04-10
I finished my list


[TABLE="width: 0"]
[TR]
[TD="bgcolor: #FFE599"][FONT=Ubuntu]box ([/FONT][FONT=Ubuntu]*copied from list; most detail from lshw*[/FONT][FONT=Ubuntu])[/FONT][/TD]
[TD="bgcolor: #FFE599"][FONT=Ubuntu]debug (/cow [/FONT][FONT=Ubuntu]*size*[/FONT][FONT=Ubuntu])[/FONT][/TD]
[TD="bgcolor: #FFE599"][FONT=Ubuntu]start (/cow [/FONT][FONT=Ubuntu]*size*[/FONT][FONT=Ubuntu])[/FONT][/TD]
[/TR]
[TR]
[TD]hp dc7700 (c2d-e6320, 5gb, nvidia quadro nvs 290)[/TD]
[TD]4.3/4.7gb[/TD]
[TD]4.3/4.7gb[/TD]
[/TR]
[TR]
[TD]hp dc7900 (c2d-e8400, 4gb, intel 4 series integrated i915)[/TD]
[TD]4.3/4.7gb[/TD]
[TD]1.8/1.8gb[/TD]
[/TR]
[TR]
[TD]dell [optiplex] 745 (c2d-6600, 6gb, amd/ati radeon rv516/x1300/x1550)[/TD]
[TD]4.2/4.7gb[/TD]
[TD]4.2/4.7gb[/TD]
[/TR]
[TR]
[TD]dell [optiplex] 755 (c2d-e6850, 5gb, amd/ati radeon rv516/x1300/x1550)[/TD]
[TD]4.4/4.7gb[/TD]
[TD]2.4/2.4gb[/TD]
[/TR]
[TR]
[TD]dell [optiplex] 755 (c2d-e8300, 8gb, amd/ati radeon rv610/radeon hd2400 pro/xt)[/TD]
[TD]4.4/4.7gb[/TD]
[TD]4.4/4.7gb[/TD]
[/TR]
[TR]
[TD]dell [optiplex] 780 (c2q-q9400, 8gb?, amd/ati cedar radeon hd 5000/6000/7350/8350)[/TD]
[TD]4.4/4.7gb[/TD]
[TD]4.4/4.7gb[/TD]
[/TR]
[TR]
[TD]dell [optiplex] 960 (c2q-q9400, 8gb, amd/ati cedar radeon hd 5000/6000/7350/8350)[/TD]
[TD]4.4/4.7gb[/TD]
[TD]4.2/4.7gb[/TD]
[/TR]
[TR]
[TD]hp 8200 elite sff (i5-2400, 8gb, nvidia quadro 600)[/TD]
[TD]4.3/4.7gb[/TD]
[TD]4.3/4.7gb[/TD]
[/TR]
[TR]
[TD]dell vostro 430 (i7-870, 12gb, ??)[/TD]
[TD]-[/TD]
[TD]-[/TD]
[/TR]
[TR]
[TD]dell [optiplex] 990 (i7-2600, 16gb, nvidia geforce gt 6600 gt)[/TD]
[TD]4.3/4.7gb[/TD]
[TD]7.8/7.8gb[/TD]
[/TR]
[TR]
[TD]lenovo thinkpad sl510 (c2d-t6570, 2gb ram, i915)[/TD]
[TD]4.4/4.7gb[/TD]
[TD]4.4/4.7gb[/TD]
[/TR]
[TR]
[TD]lenovo thinkpad x201 (i5-m520, 4gb, i915)[/TD]
[TD]4.4/4.7gb[/TD]
[TD]4.4/4.7gb[/TD]
[/TR]
[TR]
[TD]motion computing j3400 (c2d-u9400, 4gb, intel mobile 4 series)[/TD]
[TD]4.2/4.7gb[/TD]
[TD]4.2/4.7gb[/TD]
[/TR]
[TR]
[TD]sony vaio ultrabook (i5-9400u, 4gb, intel haswell-ULT)[/TD]
[TD]4.2/4.7gb[/TD]
[TD]4.2/4.7gb[/TD]
[/TR]
[/TABLE]

the dell 780 may have had a different amount of ram to that listed (I forgot to check; I'm borrowing ram from it in testing vostro_430 that's currently complaining about its ram).

list at [https://docs.google.com/spreadsheets/d/18-XMDjy5lWiHFqFww_865jR6hbcHf00MI_Z92PayDMM/edit#gid=0](https://docs.google.com/spreadsheets/d/18-XMDjy5lWiHFqFww_865jR6hbcHf00MI_Z92PayDMM/edit#gid=0)

---

### Post by sudodus on 2020-04-10
Thanks @guiverc,

- You found 3 computers that are affected by this bug.

- For the first time an HP computer is affected: hp dc7900 (c2d-e8400, 4gb, intel 4 series integrated i915).

- The 'hack' by Michael Hudson-Doylefixes it in these 3 computers.

- And all your computers work with the 'hack'.

Edit: Maybe you would like to copy your results into the corresponding [bug report](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1863672).

---

### Post by C.S.Cameron on 2020-04-10
Got my hands on my wife's Gigabyte GB-BXi7-5775
The UNetbootin syslinux drive worked okay with standard initrd.
It did not boot in BIOS mode with casper-initrd, (I was using version on Index of /~mwh).
It also did not boot in UEFI mode.
A 20.04 drive made with mkusb-plug worked fine on the Gigabyte, but took >15min to boot.
I will try with your current Lubuntu Focal daily iso file above, after midnight when rates are low.
(Decided to ride this Virus thing out in Sri Lanka).

Discovered that pressing Enter stops the scrolling.

---

### Post by C.S.Cameron on 2020-04-11
Tested "current Lubuntu Focal daily iso file" in three computers, works with both writable and casper-rw partitions in all three.

---

### Post by sudodus on 2020-04-11
Thanks everybody for all the testing in all these computers.

The bux-fixing 'hack' by Michael Hudson-Doyle makes persistence work in all tested computers with the classic label 'casper-rw' (and of course squashes the bug in computers that were affected by the bug). So we can relax about this issue.

I mark this thread as solved :-)

---

