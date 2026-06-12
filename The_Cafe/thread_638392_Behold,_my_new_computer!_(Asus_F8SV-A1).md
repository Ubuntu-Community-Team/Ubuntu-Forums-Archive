---
title: "Behold, my new computer! (Asus F8SV-A1)"
date: 2007-12-12
forum: The Cafe
---

### Post by Mr. Picklesworth on 2007-12-12
I've switched to a new notebook as my main computer, and I am quite pleased with it.

In the end, I chose an [Asus F8SV-A1.](http://forum.notebookreview.com/showthread.php?t=194796) I have yet to regret the choice at all :)

The first thing that I noticed was the specs, which are just about on par with the Macbook Pro, but for around 800 dollars less. It is also not a bad looking computer; it doesn't seem horribly thick like many others do.

Intel T7500 (Core 2 Duo 2.20 gHz)
NVidia GeForce 8600M GT 256MB
1GB DDR2 667 RAM
160GB 5400rpm SATA Hard drive
1280x800 LCD screen
160 GB 5400 RPM hard drive
1 year free accidental damage warranty + another year of regular hardware warranty.

Okay, not absolute top of the line, but it was a good price, too.

Of course, I shrunk Vista down to 60 GB of hard drive and gave all the rest to Ubuntu. So far, I have succeeded at only using Windows for games.
I upgraded to 2GB or RAM, since 1 GB is the same as my desktop, and my desktop is less than half the power of this. Fantastically easy upgrade. They were forward-thinking enough to use a single 1 GB module instead of two 512s, and both slots are directly accessible underneath a panel on the back.
I have not given it the Crysis test (in a way, I don't want to. Would probably be depressing). However, I did try COD 4 on it, and it runs beautifully with every setting as high as they will go and native resolution. (The catch being that some settings, like model detail, would only go up to Normal. Do they just not have High, or are they disabling them for me so that I don't suffer with poor frame rates?).

One of my favourite things here is the cooling. While the manual tries hard on the first page to drop any association with laptops, (insisting that this not be used on one's lap!), I almost wonder why. Even after playing COD 4 for an hour, the surface with the keyboard hardly heats up at all; every bit of hot air is blown out the side. The bottom is a bit warmer in some areas, but even that is rather a small amount compared to other computers.
While it is quite noticeably thicker and heavier, that cooling makes for a fine counter to the Macbook Pro's favourite features. (That thing gets noticeably hot with any significant use).

My most favourite thing, of course, is that Ubuntu runs. Actually, it doesn't just run, it runs better than Windows does right out of the box! Where Windows's support of the wireless hardware is still a bit shakey, Ubuntu handled it instantly and connects long before I am logged in. It boots to my desktop in well under 30 seconds, too.
The NVidia card is so far pleasing me, especially since I can now run Compiz's fancy alpha blur effect. As expected, the difference between this and my old desktop's Radeon 9600 Pro is night and day.
Even the webcam works immediately! In Cheese, at least. Camorama gives me "could not connect to video device (/dev/video0)" and quits. It seems that one working and the other not is a common act. I'll just wait it out; judging by how these programs are directly talking to stuff in /dev, I'll guess that webcams in Linux are still waiting for a miracle library.

I should elaborate on "running better," too. I had to run the recovery disk for Windows, because Microsoft changed NTFS just enough that trying to shrink Vista's partition through the partitioner in Gutsy's Live CD resulted in it no longer booting. Actually, I had to run the recovery disk twice. The first time, I followed the on-screen directions and let it install the drivers automatically. Doing that, Windows would not boot. It didn't just give me an error and drop to a command line, though. Instead, (just as it did when I resized the partition, come to think of it) it threw a BSOD. Now, usually, this could be considered good; it gave out an informative error message for a critical situation. Actually, somehow, Microsoft even screwed up their famous BSoDs. They decided, presumably for user-friendliness, to have the computer reset as soon as a BSoD is generated, such that the error report is shown in a helpful GUI the next time Windows boots. A group of nincompoops then decided it fine to do this for *critical boot errors*, too. The result: Windows tries to boot, gives a BSoD and restarts the computer to give me the message when it boots up. However, as anyone with half a brain can probably guess, it is not going to boot up because the error is with the booting process! It goes on into an infinite loop of rebooting and BSoDing until I take control.
Anyhow, the next time I had to install Windows without that driver disk, instead doing the drivers by hand after installing. (That first boot is a woefully unstable looking experience, I might add. Immensely long wait time, staring at a blank screen with a little rotating circle for ages. Computer reboots without prompting me at least once in the process. Anyone who expects a decent operating system would assume trouble, but it's actually normal!). Absolutely nothing worked out of the box. Nothing. Wireless was toast. Video was not only a very ugly generic driver, but at the wrong resolution. Special keys on the keyboard did nothing.
Ubuntu completely worked out of the box, wireless and all. Besides the pain associated with needing to install Windows a total of 3 times before I got it right, this was a surprisingly pleasing experience.

The only major flaw here, so far, is battery life. 2 hours and 10 minutes in Ubuntu with desktop effects ( I'm addicted to them :( ), same time with Vista in power saving mode. I am sure more can be squeezed out, having seen the difference in lifetime running Vista and MacOS on a Macbook, but that is the best one usually gets here. In addition, the battery is positioned so that getting a larger one is unlikely to ever happen.
I knew what I was getting in to, so don't really mind. If I want a portable device to last all day, I'll rely on something pocket sized, preferably taking AA batteries.

That's that, I've done my babbling for today. This computer is highy recommended.

---

### Post by Kingsley on 2007-12-12
Nice laptop. I especially like how it has 160GB of HD space; mine only has 120. I would set up the partitions differently though.

30GB NTFS - Vista
110GB Fat32 - shared movies, music, etc. between Vista and Ubuntu
20GB EXT3/swap - Linux

---

### Post by maniacmusician on 2007-12-12
> **Kingsley said:**
> Nice laptop. I especially like how it has 160GB of HD space; mine only has 120. I would set up the partitions differently though.

30GB NTFS - Vista
110GB Fat32 - shared movies, music, etc. between Vista and Ubuntu
20GB EXT3/swap - Linux
But he only wanted to use Vista for gaming, so his partitioning setup makes more sense for his situation

---

### Post by Mr. Picklesworth on 2007-12-12
That, and Vista wouldn't go any smaller. I can only use its own partitioner (I'll give credit where it's due; neat feature. Resize Windows's main partition while running Windows).

Unfortunately, resizing the Vista partition results in the most insane Billy G puzzle yet!
Vista, by pure genius, stores a whole lot of "unmovable" files at random places in its partition. For example, it has a big swap file not at a particular end, but right in the middle! Even after turning off that swap file, however, there are still phantom unmovable files...
It took 3 resize operations and that many defragments to bring it down to the size I got it to, because it kept having a ridiculous limit for how much smaller I could make it, regardless of how much free space it claimed to have.
Swap partitions were a great idea.

The keyboard is nice, by the way. Rock solid. Quite unusual!
Only problem I have with it is how Home / PgUp / End are all right to the left of Enter and Shift. I am always pressing them by accident. Need some kind of selective slow keys thing to avoid that, since I doubt I will ever get used to it. Also, some nitwit thought it a good idea to put Fn on the far bottom left of the keyboard instead of Ctrl...

---

### Post by Kingsley on 2007-12-12
> **maniacmusician said:**
> But he only wanted to use Vista for gaming, so his partitioning setup makes more sense for his situation
Ah, I should have read his whole post.

---

### Post by PartisanEntity on 2007-12-12
Congrats from a fellow Asus owner, I have an Asus A6K. It is about 2 years old and since Gutsy, fully Ubuntu friendly.

---

### Post by romario_t on 2008-01-19
**Mr. Picklesworth,**
I'm a total noob in Linux and trying to install kubuntu 7.10 on my Asus F8SV from live DVD. Is there any guidlines how to setup a dual boot system (vista/kubuntu) in my case?

---

### Post by Dark Aspect on 2008-01-19
Good choice I like Asus they seem to have good hardware IMO.I have never tried one of there laptops but still their motherboards are good for the price.

btw heres the specs to my desktop.I know its not the top of the line but it does everything I need it to do:

Asus A8N-E
AMD Athlon 3200 2.4 Ghz
GeForce 6800 GS 256 MB VRam
1.5 Gb of Ram (Not DRR2 sadly)
320 GB Hard Drive (Ubuntu only sees 310 GB and windows sees 294 GB WTF)

Major Prob:No SLI,but I am not the gamer I used to be.

---

### Post by Joeb454 on 2008-01-19
To whomever posted the different partitioning advice:

When have you ever seen a 110Gb FAT32 partition...I was under the impression that was impossible

---

### Post by Spike-X on 2008-01-19
> **Dark Aspect said:**
> 
320 GB Hard Drive (Ubuntu only sees 310 GB and windows sees 294 GB WTF)

Does it have one of those damnable 'restore partitions'? Perhaps Ubuntu can't see that. Then when you're using Windows, it sees neither the restore partition nor your Linux partitions(s)?

---

### Post by Dark Aspect on 2008-01-19
> **Spike-X said:**
> Does it have one of those damnable 'restore partitions'? Perhaps Ubuntu can't see that. Then when you're using Windows, it sees neither the restore partition nor your Linux partitions(s)?

No it doesn't have a restore partition,and I don't have it set to dual boot.When I brought the drive I only used XP and did not even know Linux existed.During that period it saw 294 GB with windows.Then I backed up all my data and took the leap of faith over to Linux and told Ubuntu to use the entire disk.Now it sees 310 GB and I don't think it had a restore partition before I used Ubuntu because the drive did not come with the computer.It had a 200 GB hard drive by default.Maybe I set up Windows XP wrong on the install....or maybe windows is piece of crap,I mean 16 GB is lot of room to just not show up.

Of course I never use any more then half my hard drive any way.I had a computer scientist tell me if you go above the half way mark that you computer will slow down,don't know how much of that is true.

---

### Post by romario_t on 2008-01-20
I have installed kubunu 7.10 on my ASUS F8SV but on restart i see nothing but black screen :(

After i've tried to run vista- i'm getting grub 17 error.
crap :(
please show me the way out

---

### Post by inversekinetix on 2008-01-20
the measuring method is different between what the manufacturers put on the box and how the OS calculates size.1000 vs 1024 = 1GB or something, Im not sure. if you dont want the windows page/swap file to be all over the place, either turn it off or set the MIN and MAX size to the same value as soon as you install,  it will (should) create one contigious block for it then.

---

### Post by inversekinetix on 2008-01-20
> **romario_t said:**
> I have installed kubunu 7.10 on my ASUS F8SV but on restart i see nothing but black screen :(

After i've tried to run vista- i'm getting grub 17 error.
crap :(
please show me the way out

use wingrub to boot with, that way you can just add one line to windows boot.ini and have dual boot.

google  wingrub

---

### Post by Mr. Picklesworth on 2008-01-21
> **romario_t said:**
> **Mr. Picklesworth,**
I'm a total noob in Linux and trying to install kubuntu 7.10 on my Asus F8SV from live DVD. Is there any guidlines how to setup a dual boot system (vista/kubuntu) in my case?

I am guessing here based on what I, in retrospect, *should* have done. Firstly, beware: Vista's built in partitioner involves a horrible Billy G puzzle and should not be trifled with. At all. The better solution: Nuke the entire thing!

Make sure you have nothing important in Windows Vista. If you do, back it up...

Now, in the Ubuntu install CD, set up the partitions as follows:

-Delete existing partition Windows is in.
-New partition for Windows, as big / small as you please. This will be empty space for now.
-Give the rest to (K)Ubuntu.

You can kill the Restore partition safely if you have the restore disk, but beware that it is quicker to run a system restore from that partition. (It also takes up a lot of space).

...After installing Ubuntu (don't get too accustomed to it; this might not work)...

Pop in the recovery disk, tell it you want to install Windows to the first partition. Alas, this recovery disk really sucks; we don't get much control over where it goes other than those few little options. Just hope it knows what it's doing.
...Once it asks for the driver CD...
Speaking of which, this disk does not know what it's doing. Indeed, it would seem that the drivers packed in here kill Windows on arrival if you let the recovery system install them. May be worth a shot, (at any rate, it is hilarious watching how Windows handles the errors), but I had no luck with them. Instead, reset the computer when it asks for the driver CD.

Windows should boot, probably with *really* ugly screen resolution. (Just so you know: You can change this! Probably a good idea to avoid going mad).
Now, put in the driver CD. Here is a fun part: You can pick your bloatware!

Hope it works. Now you *should* have a dual-boot setup...


If that did not work, try again. This time, install Windows across the entire disk. Choose the 2 partitions option.
In Windows, open up Disk Management. You can resize the C drive even while running from it. This is not as impressive as it should be; Windows "cleverly" puts its swap files and other garbage right dead center in the partition, so you can't shrink it any more than 50%. Sometimes there are unmovable files near the end of the partition, too! Cross your fingers and hope it can shrink far enough. If not, it will take a lot of prodding that I can't really explain here; the documentation fails to mention what "unmovable files" are. One trick is to stop it from swapping, which seems to free a bit of shrinking room, but not all of it...
This may require resizing, restarting, resizing, restarting... as I said, it is fiddly. Come to think of it, you may want to check if the gparted live CD supports resizing Vista's NTFS yet.
Put (K)Ubuntu on the other partition (currently NTFS) that does not have Windows on it. (The second one, not counting the recovery partition).


As for black screen with booting, make sure you wait a while. (40 seconds?). USPlash does not work. In the Grub boot options, remove "usplash" and "quiet" to get a working boot screen feedback. It may be running fschk for some reason.

---

### Post by mips on 2008-01-21
> **Mr. Picklesworth said:**
> 
1280x800 LCD screen

Now that would seriously tick me off unless you have a external display.
Minimum resolution for a 14"-15"  laptop should be (w)sxga+

---

### Post by romario_t on 2008-01-21
**Mr. Picklesworth**
i've installed kubuntu from alternateCD once again
have removed "usplash" and "quiet" in grub and i'm getting more feedback but at the end i see the same black/darkgrey screen and can do nothing :(

---

