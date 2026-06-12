---
title: "Installing Intrepid Ibex worthwhile?"
date: 2008-11-27
forum: System76 Support
---

### Post by Modax42 on 2008-11-27
I'm still using 64 bit hardy on my Daru3 laptop, and after reading mixed reviews of 8.10, I'm torn -- should I install Intrepid Ibex or stick with Hardy.
[B]
Please give me your honest personal opinio[/B]n -- *is 8.10 worth the trouble of backing up all my files and doing a clean install, and then having to reload and set up all my add-ons and software?* I don't want to upgrade because I have read various horror stories and this post on the Ibex Upgrade Thread:

> **steveneddy said:**
> Here we go again.....another new user thinking that they know what to expect out of a operating system then they try and update.

Happens every time there is an update.

**If you have .debs, get-debs or software that is not in the repos, including video drivers, installed before you update, then you must get rid of this software before upgrading or the upgrade will fail.**

Those of us who have been doing this for a few releases (me=6+) then you will discover that the easiest way to upgrade to a new version and have as few issues as possible is to backup the /home directory and do a total re-install.

It only takes 30 minutes to do a total re-install and a little more time to get your other software re-installed.

Any OS will reveal these same issues upon installation and a new install must be dealt with accordingly.

Please tell me what you think!

---

### Post by jdb on 2008-11-27
> **Modax42 said:**
> I'm still using 64 bit hardy on my Daru3 laptop, and after reading mixed reviews of 8.10, I'm torn -- should I install Intrepid Ibex or stick with Hardy.
[B]
Please give me your honest personal opinio[/B]n -- *is 8.10 worth the trouble of backing up all my files and doing a clean install, and then having to reload and set up all my add-ons and software?* I don't want to upgrade because I have read various horror stories and this post on the Ibex Upgrade Thread:



Please tell me what you think!

If you're not sure, here's a good way to find out.

Use gparted to resize your current partition about 10 or 15 gig smaller.
Create a new ext3 partition with the newly created space.
Now load Ibex on the new partition and see what you think.

You can still boot to your old partition & nothing will be disturbed.

You can even copy the files from your old home directory to your new one & see if all the configurations work.

jdb

---

### Post by Modax42 on 2008-11-27
Thanks for the great suggestion.  Installed gparted from Hardy, but I quickly figured out that i can't resize the partition that's currently mounted.  So I booted to my Intrepid USB drive and it working away at resizing SDA3 from 448 to 432 GiB.  Its okay to run this in the background while I surf the web right.  I hope this doesn't screw up my partition, because some of my stuff hasn't been backed up yet.

Is there a program out there that would automatically synchronize say, my documents folder with a USB stick, in the same way itunes syncs your iPod with your music library? That would be so helpful.

---

### Post by Lee_Machine on 2008-11-27
I had kernal panics with the driver being used with my intel wireless card and a bluetooth issue,

Both of which have been fixed through updates. I like 8.10 much better than 8.04. 

I installed the black winter theme from gnome-looks and its a very stunning Theme.

8.10 is now very stable on my machine and runs faster than 8.04. 

This is on a Pangolin panp4n model.

The only issue is with the webcam in cheese but I dont use it so I dont bother fixing it. It works fine in Ekiga and Skype.

As far as upgrading goes I just keep all files on my 1TB external drive or my file server which still runs Feisty Fawn and write down all the apps I use to reinstall.

I prefer doing fresh install anyways. You get to see what they changed for installing and when I started ubuntu back with Warty you had to install everything manually. Codecs, apps, everything.

Now it's so easy i feel like its a mac sometimes. :lolflag:

---

### Post by eldragon on 2008-11-27
create a separate home partition, and do a clean install everytime.
maybe backup your /etc/ dir too

and after installing, backup new config files before replacing with your own (in case they break somehting)

i wouldnt count on intrepid being that different from hardy. in fact, i had a horrible experience in my laptop, but your mileage may vary.

btw, i just got my intrepid pressed cd from shipit, artwork looks much better than it used to :D too bad they still ship those nasty stickers.

if only they shipped more than 1 cd. i used to get about 5 per shipping. gave them away at my univ. that was fun :D .... and the beer got me carried away.

---

### Post by jayson.rowe on 2008-11-27
8.10 is working splendidly for me - I contemplated staying on 8.04 at least until 9.04, but decided against it in the end.

The "clincher" for me DKMS by default (and fully working). It is SO nice not to worry about kernel updates breaking some module (such as my VirtualBox) - everything is much more seamless.

I guess it's the "little things" that make me happy.

---

### Post by MorphWVUtuba on 2008-11-27
Kernel panics, mysterious freezes, choking on vmware, I think this release is complete garbage.  This is by far the worst experience I have had with Ubuntu. :mad:

I'd revert to Hardy, but the system76-driver doesn't install any drivers for it and the display is stuck in 800x600.

What a p.i.t.a.

---

### Post by Modax42 on 2008-11-28
Something is not right here.  When gparted started resizing my partition it said it would take 4 hours.  3 hours later, and there's 1 hour left.  No surprise there. I left my computer unattended for an hour. Now I look at my machine, and most of the progress is gone, and its telling me it needs 8 HOURS!  What the heck is it doing!??

Can I safely cancel it at this point?  I need to know what's going on here, and soon.  Can anyone help?

Starting to get very worried.

---

### Post by alwayshere on 2008-11-28
I would say if your current setup is all good and doing all that you want i would stick with it ,unless you want to dick around getting things to work that are already working in your current install???????

I choose to upgrade and dick around with it ,Im still having sound problems , but that the fun part i guess ,lol:-s

---

### Post by Modax42 on 2008-11-28
Anyone there?  Another hour has passed, and gparted is telling me that there's still 6 hours to go.  This would bring the total time to resize the partition to 11 hours, if it actually completes it when it says it will this time.

I am very worried for my files.  Can I safely cancel the process at this point, or is it best to just let the program run its course?  :confused:

---

### Post by Modax42 on 2008-11-28
System crashed while gparted was still running.  Now my HOME folder is unreadable.  Everything since last backup a week ago is now almost certainly lost.  What am I going to do now?

---

### Post by Alvinius on 2008-11-28
I never have used gparted so I cannot help you there with any expectations:(, but I think the best way to make 3 partitions;

A root partition that I over kill size-wise with 25 Gig, 10 gig is probably more than enough

 a swap partition, I think 2 gig is plenty, 

and the rest /home.  All programs go into /home.

that way when installing a new version you never have to mess with your home directory.

---

### Post by defg649 on 2008-11-28
[[color=#800080]wholesale Abercrombie & Fitch Swim suit[/color]](http://www.gucci-sneaker.com/catalog_332.html), bathing suit or swimming costume is an item of clothing designed to be worn for swimming. In New Zealand English and some areas of Australian English, **Abercrombie & Fitch Swim suit **are usually called togs or bathers. This term is less common in other parts of the Commonwealth where it can also refer to clothes in general. **wholesale Abercrombie & Fitch Swim suit **can be skin-tight or loosely fitting and range from garments designed to preserve as much modesty as possible to garments designed to reveal as much of the body as possible without actual nudity. They are often lined with a fabric that prevents them from becoming transparent when wet.

---

### Post by eldragon on 2008-11-28
now you got an empty system you can start from scratch with. and bork, and start again, and bork.

gparted has been doing these little annoyances when formatting sd cards or usb pen drives here too. anyway, grabbing a HDD diag boot disc (like the UBCD) and running a test on your hdd wouldnt be a bad idea. maybe your drive is failing.

---

### Post by MorphWVUtuba on 2008-11-28
Before giving up on your unreadable /home, have you tried running fsck on it?

---

### Post by thomasaaron on 2008-11-28
Also, I'm not sure why gparted messed up, but if you're manipulating a partition with gparted, the partition should be unmounted. Otherwise, you're begging for a problem. 

The best way to do this is to boot from a live CD and use the gparted (Partition Editor) that is on the CD.

---

### Post by jdb on 2008-11-28
> **Modax42 said:**
> System crashed while gparted was still running.  Now my HOME folder is unreadable.  Everything since last backup a week ago is now almost certainly lost.  What am I going to do now?

Wow, sorry about the bad advice :(

I've never had any trouble with gparted, I guess I've been lucky.

MorphWVUtuba's advice on using fsck is a good idea.

jdb

---

### Post by Modax42 on 2008-11-28
> **thomasaaron]Also, I'm not sure why gparted messed up, but if you're manipulating a partition with gparted, the partition should be unmounted. Otherwise, you're begging for a problem.

The best way to do this is to boot from a live CD and use the gparted (Partition Editor) that is on the CD.[/QUOTE]

This is exactly what I did.  I booted from my Ibex Live USB and ran gparted from there. 



[QUOTE=jdb said:**
> Wow, sorry about the bad advice :(  I've never had any trouble with gparted, I guess I've been lucky. MorphWVUtuba's advice on using fsck is a good idea.jdb

No worries.  You couldn't have known this was going to happen.  Its all my fault for not backing everything up before running gparted.


I don't know anything about fsck.  I'm using my Ibex live USB again right now, can I run fsck from the command line from here?  What's the command?

I have heard stories about data recovery experts that can partially salvage files from a hard drive that has been wiped clean, reformatted, and then overwritten more than once.  The files on my HOME folder are still there, somewhere.  Its just a question of reading them, right?

---

### Post by jdb on 2008-11-28
> **Modax42 said:**
> 

I don't know anything about fsck.  I'm using my Ibex live USB again right now, can I run fsck from the command line from here?  What's the command?


You need to first boot to your USB and open a terminal.

The format for the fsck command is:

```
fsck /dev/...
```

Substitute the partition you want to check for /dev/... , for example, /dev/sda1

To get a list of the partitions available type:

```
sfdisk -l
```

The partition should not be mounted, to see all mounted partitions type:

```
mount
```

If it finds problems it will not fix them because you are not root, you will have to then run it:

```
sudo fsck /dev/...
```

To find out more about fsck (or any command) type:

```
man fsck
```
Good luck!!

jdb

---

### Post by Modax42 on 2008-11-28
here is what I did

> ubuntu@ubuntu:~$ sudo fsck /dev/sda3
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda3: clean, 125545/56819712 files, 29600572/113637785 blocks

this took less than a second to complete.

When I mount the partition, my HOME folder is not there.  :(

---

### Post by Modax42 on 2008-11-28
tried them all, here's what happened

> ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda1: clean, 170534/1831424 files, 1111642/3662109 blocks
ubuntu@ubuntu:~$ sudo fsck /dev/sda2
fsck 1.41.3 (12-Oct-2008)
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda2
ubuntu@ubuntu:~$ sudo fsck /dev/sda3
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda3: clean, 125545/56819712 files, 29600572/113637785 blocks
ubuntu@ubuntu:~$ sudo fsck /dev/sda4
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: No such file or directory while trying to open /dev/sda4

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

gparted still reports the same partitions it did before all this happened.  HOME folder used to located at SDA3, but although SDA3 is still there, my files are not.  I did not delete anything manually.

Oh well.  The most important thing I lost was a major assignment for one of my classes, due Wednesday.  I'll have to do that all over again.  I have a decent recollection of what I said so it will take a while but I'll get it done in time.  And I lost all of the notes I took in class the last week or two, plus all of my progress in Baldur's Gate.  Also, some other miscellaneous documents I probably won't miss.  Everything else was backed up, fortunately.  

I'm not installing Ibex or doing anything with the HDD until I run out of things to try, though.

---

### Post by jdb on 2008-11-28
> **Modax42 said:**
> tried them all, here's what happened



gparted still reports the same partitions it did before all this happened.  HOME folder used to located at SDA3, but although SDA3 is still there, my files are not.  I did not delete anything manually.

Oh well.  The most important thing I lost was a major assignment for one of my classes, due Wednesday.  I'll have to do that all over again.  I have a decent recollection of what I said so it will take a while but I'll get it done in time.  And I lost all of the notes I took in class the last week or two, plus all of my progress in Baldur's Gate.  Also, some other miscellaneous documents I probably won't miss.  Everything else was backed up, fortunately.  

I'm not installing Ibex or doing anything with the HDD until I run out of things to try, though.

Very odd.

Try booting to the USB again and opening a terminal.

```
sudo mount /dev/sda3 /mnt
```

Use nautilus to browse /mnt and see what files and directories are there.

jdb

---

### Post by Modax42 on 2008-11-28
all it has in there is the lost&found folder (which I cannot access, nor can I determine what is in it...) and the HOME folder for a secondary account I made on a whim.  When I try to enter either folder, it tells me that I do not have permission.  Only 'root' has permission. the partition appears to be the correct total size though, which is the only encouraging part.

---

### Post by jdb on 2008-11-29
> **Modax42 said:**
> all it has in there is the lost&found folder (which I cannot access, nor can I determine what is in it...) and the HOME folder for a secondary account I made on a whim.  When I try to enter either folder, it tells me that I do not have permission.  Only 'root' has permission. the partition appears to be the correct total size though, which is the only encouraging part.

It's not sounding too good.

You can see if there is anything in lost+found by:

```
sudo ls -la /mnt/lost+found
```

I don't think there will be since fsck passed, but you never know.

If there is something there you can browse it (and the other home directory) as root by:

```
sudo nautilus
```

If fsck passes and the files don't show up when the partion is mounted, it's beyond me.  Recovering lost files in linux is very difficult.
Maybe someone else has some ideas.

jdb

---

### Post by Modax42 on 2008-11-29
Tried 'sudo nautilus' but there was nothing in the lost+found folder.  If there is nothing else to do I might as well install Ibex now. It seems to work very well on the live USB.  Battery life seems to be better than in Hardy and CPU usage is less erratic, especially when watching video.

---

### Post by Modax42 on 2008-11-29
Doesn't look like I'm going to be getting those files back.  I'm going to go install 8.10 now.  I'll report the results when I'm done.

---

### Post by drewbenn on 2008-11-30
I guess it's a little late to help you recover your files, but you might be interested in looking at PhotoRec (apt-get install testdisk; man photorec) ([http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)).  You need another hard drive, larger than the one you're recovering, but if you haven't written anything to the disk then PhotoRec should be able to recover all the files.  It just gives them generic names, like 'f15707512.jpg', but the extensions are preserved.  It's useful in some cases (I just used it to recover some photos for my sister from a hard drive that crashed a couple years ago) but is probably much more time-consuming than just asking your professor for an extension and copying a classmate's notes (I spent many hours over a few weeks, sorting through all the .gif and .jpg files to find the ones that were actually pictures, not just cache files).

---

### Post by Modax42 on 2008-11-30
Thank you for the helpful suggestion, but I've already installed Ibex and overwritten my HDD.  I burned the midnight oil last night, and was able to reconstruct most of my assignment from memory, so that's almost done.  As for my notes, I guess I'll ask a friend if I can photocopy theirs.  The notes I lost are probably not absolutely essential, though.  I will install the software you suggested to my live USB, so I'm ready for the next time I bork my HDD. :lolflag:

Anyway, I'm looking at software for backing up my HOME folder.  I'm not interested in having multiple, incremental backups.  I just want to synchronize my HOME folder to an external hard drive, the same way itunes syncs your music library to your ipod.  So I'm going to try "Home User Backup" and see how I like it.

Once again, thank you to everyone who has helped me here.

---

### Post by eldragon on 2008-11-30
what you are looking for is in the repos, and its called unison :D

if its a laptop, and you have a desktop, you could setup a sshd and have unison sync trhough it. quite handy for on the road backups. (it only xfers what changed, not the entire share)

---

### Post by thomasaaron on 2008-12-01
There is also Simple Backup and Restore. It's available in the repos too...

Applications > Add/Remove Software

---

