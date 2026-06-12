---
title: "Dumbest, stupidest most moronic thing you've ever done in Linux?"
date: 2012-12-16
forum: The Cafe
---

### Post by DuckHook on 2012-12-16
In the spirit of humility that comes with the season, I thought I would pose this question:

What's the dumbest, stupidest most moronic thing you've ever done to/in Linux?

I'll start by admitting that I've rm-ed my / directory as root when first learning Linux. Back then, I'd just changed over from Mandrake, thought I knew everything and wasn't about to put up with this sudo nonsense, so I activated my root account. Not long afterwards, trying to clear out an insignificant minor subdirectory, I su-ed to root to momentarily administer something, was distracted by a phone call, and upon returning, brainlessly proceeded to execute my original intent on the worst possible directory.

I know, I know... has probably happened thousands of times. So not only is it moronic, it's not even original.:oops:

---

### Post by Jakin on 2012-12-16
Back on Natty,i wanted to format a 20GB unused bit of the HDD, with Gnome Disk Utility. I highlighted the bit labelled "unallocated" and hit format... in an instant, it formated- but before i could stop the process, it had actually quick formatted the ENTIRE DRIVE.

I tried to use various tools to get my partition table back, someone here on the forums helped me to the best of their knowledge... but apparently it was too late. Anyway i no longer use Gnome's Disk Utility since, so that i wont make the same mistake,

---

### Post by Jocklad on 2012-12-16
[Dumbest, stupidest most moronic thing you've ever done in .......Windows.]("http://ubuntuforums.org/showthread.php?t=2095192")

Thats an easier one..........


Installed it.

Jocklad:D
[]("http://ubuntuforums.org/showthread.php?t=2095192")

---

### Post by chadk5utc on 2012-12-16
Ill second that

---

### Post by Giant Speck on 2012-12-16
I moved a partition containing Linux to make room for a Windows 8 install only to not check to make sure the partition moved correctly.  Needless to say, it didn't, and I overwrote the partition when I installed Windows.

---

### Post by sffvba[e0rt on 2012-12-16
Left my back-up HDD connected via USB and installed Linux (can't remember which distro or version)... then I saw it was busy formatting and partitioning a drive number I don't normally see, saw the drive and panicked and pulled out the cable... too late... RIP back-up of all important data :'(


404

---

### Post by coldraven on 2012-12-16
I just did one today :(
I was flashing the BIOS in a netbook and it fell off what I had balanced it on and onto a stone floor. About 10 inches!
Much cursing and grumbling ensued.
Remarkably it completed flashing and works OK.
Tough little things these Asus eeepcs!

---

### Post by mamamia88 on 2012-12-16
Changed the boot order of my netbook to boot from usb first and when i rebooted with a flash drive containing no os on it freaked out.

---

### Post by kurt18947 on 2012-12-16
> **coldraven said:**
> I just did one today :(
I was flashing the BIOS in a netbook and it fell off what I had balanced it on and onto a stone floor. About 10 inches!
Much cursing and grumbling ensued.
Remarkably it completed flashing and works OK.
Tough little things these Asus eeepcs!

They won't survive reversed polarity on the charger though - wispy smoke will issue from near the charger jack.  How do I know that? :oops:

---

### Post by C.S.Cameron on 2012-12-16
> What's the dumbest, stupidest most moronic thing you've ever done to/in Linux?

Insulted Forum staff.

---

### Post by pqwoerituytrueiwoq on 2012-12-16
installed it then went to login and had already forgot my password

---

### Post by David D. on 2012-12-16
Used Ubunto Tweak to automatically remove all unnecessary files and ruined my Ubuntu.  I ended up having to reintsall.

---

### Post by ubunterooster on 2012-12-16
Set all windows to 0% opacity

---

### Post by vasa1 on 2012-12-17
Got into pointless arguments ;)

---

### Post by Zane Pepper on 2012-12-17
When I was first getting into Ubuntu I applied 777 permissions to the /etc directory to edit the fstab file.

---

### Post by Ubun2to on 2012-12-17
Hmmm...I was using the startup disk creator, and I managed to select my USB backup drive because my computer was lagging like crazy. Lesson learned-do not try to run the startup disk creator if your computer is slow before removing your backup drive, or your data will become unrecoverable.
Now, I use internal drives for my backups, and take backups of my  backups (yes, you just read that correctly-I have a backup drive for my backup drive).

---

### Post by fdrake on 2012-12-17
looking for the "My Programs" folder or for the C:\ drive, hahahha......  back than i thought I knew everything (i still do now ..:D)

---

### Post by whatthefunk on 2012-12-17
Changed my root partition size but forgot to adjust the filesystem accordingly before rebooting.  Goodbye OS):P

---

### Post by coldcritter64 on 2012-12-17
Running a 32 bit lucid dchroot on my 64 bit machine, with home and about 4 media partitions bind mounted into it, promptly decided to "rm" the chroot directory /var/chroot/lucid, forcibly and recursively as "root" ... not smart ](*,).

It was the quickest I've ever reacted hitting CTRL + C, on realizing how brain numbingly stupid what I'd done was. I Lost the main system bind mounted folder /usr/share/fonts only luckily, my OS interface fonts all turned to "little blank rectangles", but my home folder and media partitions were saved thankfully :D. I was very lucky indeed to get away so relatively unscathed.

---

### Post by Max Blyss on 2012-12-17
1.  Didn't MD5 'til I had been using Linux for a year.  Learning to do that really improved my install experiences, lol.

2. Have broken my software directory by getting absent minded and closing Synaptic while it was working, and on one notable occasion powered off my system while installing a DE in the terminal because I had it minimized.

Them's prob'ly the dumbest.:guitar:

---

### Post by Roasted on 2012-12-17
I was trying to set up ext support from my XP partition, but managed to format the entire thing from within Windows. I ended up booting to a live instance so I could utilize TestDisk to bring the partition table back. It recovered in seconds, but dang that made me skip a few heartbeats.

---

### Post by Bandit on 2012-12-17
I installed windows one time.. Man that was dumb!!

---

### Post by Frogs Hair on 2012-12-17
Attempted an upgrade from Wubi 9.10 to 10.04.

---

### Post by makitso on 2012-12-18
Kept my backup HD mounted all the time.  Six months ago I messed up a thumb drive and in the process of deleting files, somehow it deleted everything on my /home/user drive.  Since the backup drive was mounted it deleted everything there as well.  Lost 3 years of data.  So, now, I only mount my HD when doing actual backups.

---

### Post by Sylos on 2012-12-18
Recently installed some updates and found Grub had changed a little and was noticably slower. So I thought I'd try and optimise it a little. Was in a hurry, skim-read a little bit of internet chatter and piled right. Went to reboot - no grub.
Tried using a Live CD but couldnt seem to get it re-installed (somehting to do with GPT partitions). In the end posted up here on the forums and found a nice little boot repair prog that pulled my festive chestnuts out of the fire. :D

A little knowledge is a dangerous thing.....

---

### Post by Grenage on 2012-12-18
The one and only time I didn't pre-check a bash loop for renaming files, I renamed 300GB of data files to the same file name.

---

