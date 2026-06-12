---
title: "where to next (running 14.04 LTE)? LOL"
date: 2015-12-26
forum: Ubuntu Development Version
---

### Post by Kris_M on 2015-12-26
(mods - move if necessary - thanks!)

noob
geek on Win7

Got 14.04 running perfectly for me - printer/scanner(2 debs and a little work.), phone(memory)(had to add adb), camera(memory), FF(QupZilla) tab video with no sound cutouts, 2 displays(monitor and HDTV), FF, TBird, installed Nvidia driver, etc  It's what I run.  Took a week to get there. Nice! :)
Sweet!

My 14.04 is currently dual boot with Win7  I also have grub customizer installed.
Partition is backed up with clonezilla (which has been a lifesaver !!!)(about 12 restores so far - LOL)

Playtime...
So where to next?
I read about 15.10.
Then I read about unity 8 mir
Then 16.04 (which is apparently only apr '16 away)
Now downloading 16.04 desktop iso from daily. Which I think I can boot to and play with separate from 14.04.
Wondering about installing something to play with as a third boot - this would mean reducing the size of the 70gb ext4 to make space on the SDD (gparted probably) and clone to HD again as I don't know if the backup img's care about target size.(I should do that anyway - but what size - 10gb? 20gb?- I'll ask that separately elsewhere)

It has been ages since I played with Linux and it was not debian.
google is my friend!

Be gentle!


GA-Z87N-WIFI mobo, i5 4670K, CoolerMaster Hyper TX3 hsf, 8GB ballistix 1600(2x4), UBUNTU 14.04.3 LTE, Win7 Pro x64 SP1 current, Sammy 250GB Evo SSD, BitFenix Prodigy black case.

---

### Post by sammiev on 2015-12-26
Hi,

You have been busy. :)

If you want to try 16.04, try the ISO on a USB and run it live without installing.

Try them all one at a time for a few days.

There mate, lubuntu, unity, xubuntu, gnome and likely more to play with.

You may decide to try something new or different.

---

### Post by grahammechanical on 2015-12-26
I have been running Xenial Xerus (16.04) since the first day of its development cycle and I find it very stable. But I keep my data on a separate partition. By all means triple boot with Xenial and update daily or weekly and see it progress into 16.04.

But as for Mir & Unity 8 that is something different. Ubuntu 16.04 will have Xserver, lightdm, Compiz & Unity 7. There are changes to come but getting something that we can install and test is proving difficult and we have been taken on to side roads.

There is unit8-desktop-session-mir which is supposed to be an alternative login session running on mir with Unity 8 as the user interface. Right now on xenial it does not load = blackscreen. Even if it did load it is a very limited phone OS.

There was Ubuntu Desktop Next which was installable but is no longer being developed. Again it was mir & Unity 8 with the phone OS and an app store that did not load apps and a browser that crashed.

Recently we tried personal_x86 which could be installed using the restore image function of the Disks utility. That worked and it was snappy ubuntu core + mir + Unity 8 = same old partially broken phone OS but it did do transactional updates & it did have a different partitioning scheme and folder structure than traditional Ubuntu. It was a hazy view of the shape of things to come. But it is no longer being developed.

What I am waiting for is to test installing and using snap apps on 16.04 + unity 7 and an installable ISO image of Ubuntu Personal which I expect to be Ubuntu desktop built on snappy ubuntu core with applications that are snaps running under confinement & an OS that has transactional updates that roll back to a working image if an update fails.

Join the club.

Regards

---

### Post by Kris_M on 2015-12-26
Huge thanks to both of you!!!!!!!!! :)  Off to play!!!

"Ubuntu Personal Will Have Unity 8 and Mir by Default and ..."   per google Softpedia said it back in Aug...

I will keep my eyes on that.

I had no luck getting Unity8 to go on 16.04 so I'll leave that for now.  Will run one other test re sound cutouts on 16.04 and then probably just sit back... for a few minutes...  :)

---

