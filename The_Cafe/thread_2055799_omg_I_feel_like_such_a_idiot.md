---
title: "omg I feel like such a idiot"
date: 2012-09-10
forum: The Cafe
---

### Post by Epodx64 on 2012-09-10
So I just put a Emachines restore disc into my computer and I was going to install windows on a second hdd on a small partition so, I put the Emachine's disc in I wasn't even sure if it was gonna boot since my computer is a custom build but i thought I'd just see what happens so... anyway I put the cd in and boot to the cdrom and then i walked outside to have a cigarette and make a phone call when I got back not only had the cd booted it was running some program called PC Angel some custom recovery crap unsure about that I hardbooted my computer because I had a bad feeling about it....... After my computer reboots in the course of 10 minutes that PC angel program managed to wipe out all my partitions all my files and formatted then to ntfs without even asking for comfirmation <snip>! seriously <snip>! WHY WOULDN'T IT ASK ME IF I WANTED TO DESTROY ALL MY FILES?!  I can't even believe it I thought the worst thing that could happen was it would just tell me "this isn't an emachines computer" but not it wipes out my harddrives completely... I seriously dumb struck by this and to make matters worse the USB pendrive that I had a partial back-up of my important files decided to die on me yesterday.... sorry had to make a rant about this because I still can't quite believe it.......

/end rant

---

### Post by nothingspecial on 2012-09-10
Not support.

*Thread moved to **The Community Cafe**.*

---

### Post by Paqman on 2012-09-10
A harsh lesson about the importance of keeping full and up-to-date backups, but an important one.

*goes off to check his backup script is still doing its job*

---

### Post by Epodx64 on 2012-09-10
> **Paqman said:**
> A harsh lesson about the importance of keeping full and up-to-date backups, but an important one.

*goes off to check his backup script is still doing its job*

I know man I know since I had 2 Hdd's I had 30Gb fat32 partition off (always unmounted) as a quick backup I figured if I kept it isolated away from everything even if my system crashed i'd atleast have that then I had a 8Gb Pendrive with just my really important stuff like pictures but that died... I seriously just can't believe it wouldn't atleast prompt you before it decided to erase your hdds.

---

### Post by Epodx64 on 2012-09-10
uhg now my optical media (Dvd-Rw) drive is acting weird I'm just trying to grab the new 12.10 beta might as well upgrade i'm trying to get the iso off a Xubuntu 12.04 cd to put it on a usb drive im on my 3 attempt 2nd restart had a Checksum error the first 2 times and then Xubuntu would crash wtf is really going on here.

---

### Post by spaceshipguy on 2012-09-10
> **Epodx64 said:**
> uhg now my optical media (Dvd-Rw) drive is acting weird.
I had that after Windows died. I just kept trying, and one time it decided to work. I hope yours is ‘intermittent’ like mine was.

---

### Post by Epodx64 on 2012-09-10
> **spaceshipguy said:**
> I had that after Windows died. I just kept trying, and one time it decided to work. I hope yours is ‘intermittent’ like mine was.

yeah, I finally got it to work I'm back on Kubuntu now decided to go with 12.10 That sucked though I still can't believe it wiped out my drives without even asking me

---

### Post by Version Dependency on 2012-09-10
I have also destroyed an Ubuntu partition by running a recovery/restore disc.  Just don't do it.

---

### Post by mamamia88 on 2012-09-10
Really not your fault for a dumb design decision.   Anyway I had a simliar moment to you.  I had just installed arch off of a usb drive on my netbook.   I had set my bios to boot first off the usb drive.   Then i boot into the new install and get everything setup and and then copy my stuff back off a portable harddrive.     Then I reboot but forget the harrddrive is connected and am freaking out when it's just a black screen.

---

### Post by Epodx64 on 2012-09-10
Finally got my installation back near where I like it just gotta recover some music now here's how it looks

---

### Post by iponeverything on 2012-09-10
> PC Angel

thats rich.. should be "PC Destroyer"

---

### Post by Epodx64 on 2012-09-10
> **iponeverything said:**
> thats rich.. should be "PC Destroyer"

lol yeah I was pretty shocked when I came back in and an angel had touched my desktop.

---

### Post by jwbrase on 2012-09-10
I've had similar trouble with an E-machine restore disk (this is for a machine that came with WinME that we bought about 10 years ago and that I've been tinkering with recently). In that case it did warn me that it would destroy everything on C: (which I took to mean a partition that I had created for the purpose), but by "C:" it actually meant "First hard disk, all partitions". Fortunately, the image on the CD was written to the front of the disk, into the empty space I had reserved, and the only actual damage done was that the MBR was overwritten with one designating a single FAT32 partition covering the whole disk, which meant that my original partition(s) (I forget exactly how many other partitions I had) were still there, but inaccessible. I was able to recover everything with TestDisk running off of [SystemRescueCD]("http://www.sysresccd.org/SystemRescueCd_Homepage"). It was a bit tricky because the new partition overlapped the old one(s), and I wanted to keep both, but it worked.

The biggest thing to remember in situations like this is not to panic. You probably will lose some data (I got lucky, I had free space at the beginning of the disk that was big enough to hold the contents of the image on the restore disk, and FAT32 stores all of its filesystem information at the beginning of the partition, which I'm not sure is true of all filesystems) but incidents like this often leave a lot more data untouched than you realize (in cases like mine, you can even find whole partitions that haven't been touched, just delisted in the MBR).

Because of this, it's critical that you run a utility like TestDisk *before* doing anything else (like reinstalling Linux) to see what you can still recover. In your case you've already reinstalled, but if you had any critical data on the disk before the restore disk wiped it, it *may* still be possible to recover it if you run TestDisk (or something similar) as soon as you can (preferably before writing anything more to the disk in question, each write risks overwriting something that's still recoverable. So you'll want to download and burn SystemRescueCD on another computer).

Basically, imagine your hard disk as a large book (say, 1000 pages). For the sake of speed and organization, your operating system only accesses the book by looking through the table of contents and going to the page numbers listed there. As far as it is concerned, anything not listed in the table of contents isn't in the book. An E-machine restore disk basically dumps white-out over a number of pages at the beginning (let's say 100 pages), writes new stuff in those hundred pages, and then dumps white-out all over the table of contents and replaces it with one that only lists the stuff it wrote in the first hundred pages, and says that anything new written in the book can be written after the first hundred pages. So the first hundred pages are lost beyond recovery. 

But the rest of the book can still be recovered: TestDisk basically does the job of flipping through the book page-by-page so that you can recover what was written in the book that's no longer listed in the table of contents. But the more you do before running TestDisk (repartitioning, operating system reinstalls, making new files, writing to existing files, etc) the more likely you are to write to a page after page 100, in which case that page is also lost.

---

### Post by Epodx64 on 2012-09-10
Thanks for the advice if it happens again sometime ill use testdisk as of right now though the biggest thing I lost was all my music and some pictures but I remembered I made a backup of all my pictures awhile ago on my mom's computer for safe keeping i lost some recent ones but that's really it everything else lost though it sucked at this point it's not worth recovering

---

### Post by Epodx64 on 2012-09-10
oh man oh man so the disk drive errors I thought I was having turned out to be my brand new Corsair XMS3 DDR3 Ram I was getting some strange errors and decided to run memtest86 and immediately it started getting errors at just 4% it had 0 pass and about 20,000 errors I tried underclocking running the exact specs reseating nothing still errored  I seriously just bought that ram like 4-5 days ago and I gotta RMA it.... ..... ... .. .

---

### Post by neu5eeCh on 2012-09-10
> **Epodx64 said:**
> So I just put a Emachines restore disc into my computer and I was going to install windows on a second hd ... then i walked outside to have a cigarette...

Dude, between the restore disc and the cigarette, you've got a real death wish, eh? Too bad about that, but those restore discs are black magic. I won't let one be in the same room as my laptop. I think that all of them, by in large, go on the assumption that you want to _**restore**_ _***everything***_.:popcorn: If they could reset your brain, they would.

---

### Post by Erik1984 on 2012-09-10
> **Epodx64 said:**
> Finally got my installation back near where I like it just gotta recover some music now here's how it looks

That's KDE 4.9?

---

### Post by Epodx64 on 2012-09-10
> **VTPoet said:**
> Dude, between the restore disc and the cigarette, you've got a real death wish, eh? Too bad about that, but those restore discs are black magic. I won't let one be in the same room as my laptop. I think that all of them, by in large, go on the assumption that you want to _**restore**_ _***everything***_.:popcorn: If they could reset your brain, they would.

I know man, I seriously forgot about OEM restore discs it's probably been 11-12 years since I last used one last OEM system I bought was A Gateway something something w/ a First line P4 at like 1.6-1.8Ghz I thought my 512mb of Ram was sick and the best part I had a VoodooFx card in it lol Then I learned how much cheaper it is to build a system. The system i'm running right now someone just gave me a "broken" compaq elite 8000 which had 3Gb DDR3 PC3-10600 Ram on it and an Intel Core 2 Duo E8400 and a 160Gb WD 7200rpm Hdd for free because it was "broke" cheapest system i've ever build I spent 50$ on an LGA775 Socket mobo w/DDR3 support spend 30 on ram I already had a PSU case and another sata 250 gb hdd and a  good fan so this particular build Intel C2D E8400 4Gb 1066mhz Ram 160x250GB WD 7200RPM Cost me a grand total of 80$

---

### Post by Epodx64 on 2012-09-10
> **Euroman said:**
> That's KDE 4.9?

yeah that's my version of KDE I don't like clutter on my desktop my Gnome 2.x & Xfce installs are about the same but I like the way KDE integrates everything there's seriously nothing in KDE that I can't tweek to my exact liking it's limitless you could have a Desktop like mine or one with a thousand plasma-widgets on it like this took me 2 minutes to clutter it up

---

### Post by Epodx64 on 2012-09-15
Well that's never gonna happen again. I overwrote my Debian install with a basic CentOS Server got my computer backed up 3 ways now I won't have to learn that lesson twice my backups now consist of USB Pendrive x2 10Gb drives, a separate ext3 partition on my local hdd's (70Gb) and now finally backed up to a proper server installation trusty CentOS which I completely locked down after I backed up my system  that uhm that sured sucked alot more then I thought initially

---

### Post by AllRadioisDead on 2012-09-16
[IMG]http://seminariopbrasilia.com.br/home/plugins/search/jackie-chan-wtf-face-meme-i17.jpg[/IMG]
Please, use some punctuation.

---

### Post by vasa1 on 2012-09-16
> **AllRadioisDead said:**
> ...
Please, use some punctuation.
[Stream of consciousness technique]("http://en.wikipedia.org/wiki/Ulysses_%28novel%29")?
Or maybe a pupil of the *we don't need no steenkin' punctuation* school?

---

