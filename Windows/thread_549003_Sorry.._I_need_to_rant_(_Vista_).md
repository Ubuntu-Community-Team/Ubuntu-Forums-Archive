---
title: "Sorry.. I need to rant ( Vista )"
date: 2007-09-12
forum: Windows
---

### Post by thewump on 2007-09-12
Sorry guys, I know you'll understand my pain, and I think I have some time to kill - so I'll share my misery.

So.. I bought a new HP laptop about 4 hours ago.. pulled it out of the box, stuck a xubuntu live CD in there and fired it up.  While that was booting I went through the box and.. WHAT?  No Windows CDs?  How come?  I don't have a vista install cd so that would be a useful thing to have, and I often install windows under VirtualBox so I can test designs with IE7.

So.. crap... so I have to boot this friggin thing into Vista, and then run a untility to create recovery disks? WTF?

Well first off - HP, what are you THINKING?  You couldn't spend the 24 cents to include the disks? Shame on you.. You managed to include an UPGRADE Cd that would allow me to pay to upgrade to Vista ultimate or whatever the hell it is.. 

Anyway.  So, I boot the machine and install Vista.. and start the recovery disk utility.. and that was, oh, 3 hours ago.. I **** THEE NOT!!!!  It's friggin 8gigs or something!  I'm 61% through verifiying DVD disk 1 of 2.

Good God.  Just how utterly **** can a company be at creating solutions.

So here I am.. 10:56pm and not sure when I'll get to start the job at hand.  Just pulled Blades of Glory from Pay Per View to ease my pain.

---

### Post by splintercellguy on 2007-09-12
It's not just HP. Microsoft has told OEMs not to ship machines with Windows installer CDs/DVDs to curb piracy.

---

### Post by Maestro23 on 2007-09-12
> **splintercellguy said:**
> It's not just HP. Microsoft has told OEMs not to ship machines with Windows installer CDs/DVDs to curb piracy.

Yep, HP is not the only one. And you would be surprised at how many people don't make those Recovery discs.  Then when they run into a problem...

Good 'ole Bill :smile:

---

### Post by lisati on 2007-09-12
You're not alone in not having access to a recent Windows disk.

My Compaq desktop didn't come with a Windows disk but a recovery partition (HP own Compaq), one of the first things I did (before realizing there was a recovery partition) was to make a set of recovery CDs. I've since made a copy of the recovery partition to DVD, but some rubbish on it from somewhere prevents me from booting from the DVD copy.

My Toshiba laptop didn't come with a WinXP disk either, but came with a recovery DVD in place of a recovery partition. What I thought was an XP disk turned out to be a "getting started with XP" booklet with a large piece of cardboard keeping it firm, when I checked it for the first time after having it for a year. I was hoping to do some troubleshooting with it but out of luck!

---

### Post by splintercellguy on 2007-09-12
Linux System Rescue CD helps a lot for troubleshooting, if you require MBR fixing, Super GRUB is what I use.

---

### Post by FuturePilot on 2007-09-12
> **thewump said:**
> Sorry guys, I know you'll understand my pain, and I think I have some time to kill - so I'll share my misery.

So.. I bought a new HP laptop about 4 hours ago.. pulled it out of the box, stuck a xubuntu live CD in there and fired it up.  While that was booting I went through the box and.. WHAT?  No Windows CDs?  How come?  I don't have a vista install cd so that would be a useful thing to have, and I often install windows under VirtualBox so I can test designs with IE7.

So.. crap... so I have to boot this friggin thing into Vista, and then run a untility to create recovery disks? WTF?

Well first off - HP, what are you THINKING?  You couldn't spend the 24 cents to include the disks? Shame on you.. You managed to include an UPGRADE Cd that would allow me to pay to upgrade to Vista ultimate or whatever the hell it is.. 

Anyway.  So, I boot the machine and install Vista.. and start the recovery disk utility.. and that was, oh, 3 hours ago.. I **** THEE NOT!!!!  It's friggin 8gigs or something!  I'm 61% through verifiying DVD disk 1 of 2.

Good God.  Just how utterly **** can a company be at creating solutions.

So here I am.. 10:56pm and not sure when I'll get to start the job at hand.  Just pulled Blades of Glory from Pay Per View to ease my pain.
Yep, I had to go through that same thing when I got my HP laptop. It took like 3 hours to make the recovery DVDs. Imagine being all excited to install Ubuntu and then have to wait 3 hours while you make recovery DVDs for Vista.:mad:

---

### Post by bigboy_pdb on 2007-09-12
I know someone with one of the DVDs (I'm not certain about what version it is), but I don't know if "dd" can be used to make a copy. I can take a look into this for you. I have a copy of Windows XP SP2. thewump, lisati, and FuturePilot, send me a private message if you want me to look into the Vista DVD for either of you (or regarding the Windows XP SP2 CD).

---

### Post by Overbyte on 2007-09-12
> **thewump said:**
> Sorry guys, I know you'll understand my pain, and I think I have some time to kill - so I'll share my misery.

It's okay...we are here to help you :)
We've all experienced all those coming from the so-called "dark side" one way or another.

Those recovery disks are a PITA to use...clean installs are the way to go :lolflag:

---

### Post by splintercellguy on 2007-09-12
> **bigboy_pdb said:**
> I know someone with one of the DVDs (I'm not certain about what version it is), but I don't know if "dd" can be used to make a copy. I can take a look into this for you. I have a copy of Windows XP SP2. thewump, lisati, and FuturePilot, send me a private message if you want me to look into the Vista DVD for either of you (or regarding the Windows XP SP2 CD).

Real simple:

dd if=/dev/cdrom (I think, you'll have to see what device corresponds to your DVD reader) of=isofile.iso bs=4096

---

### Post by newman on 2007-09-12
Same here - my Compaq laptop didn't include any discs and I had to make restore DVD's from the hard drive restore partition - what a pain!
I did call Compaq and after lots of phone games they sent me the Windows CD's.
I wiped the 8 gig restore partition off the hard drive.

---

### Post by caedmon on 2007-09-12
Yep, same problem with Vista on wife's new pc. Vista creates a 'recovery partition' that starts off, as you say at around 8gb. four months after purchase this 'recovery partiton is now 18gb.....go figure!! We,though were lucky enough have the vista dvd supplied (so why the partition?) Its incredibly difficult to control or delete that partition in vista, I think cnet did an article on it. My advice......scrap vista, if you need windows sometimes as we do, go for XP.....

good luck:


:lolflag:

---

### Post by slayerboy on 2007-09-12
Yeah I bought an Acer laptop back in May/June.  Spent more time getting windows setup, creating the recovery DVD's (2 of those buggers!), and making sure I had everything backed up.

THen I wiped it and installed Ubuntu in about 25% of the time it took me to do all that!

---

### Post by Warren Watts on 2007-09-12
> **newman said:**
> I wiped the 8 gig restore partition off the hard drive.> **caedmon said:**
> Vista creates a 'recovery partition' that starts off, as you say at around 8gb. four months after purchase this 'recovery partiton is now 18gb.....go figure!!   Sheesh!  8-18 GB :confused:
I have a Linux box with two HDD's; one 8 GB and one 4.3 GB with four OS's on it and room to spare!  Scary, I tell you....

---

### Post by K.Mandla on 2007-09-12
Dell used to pull the same stunt a couple of years ago, and they might still do it. Unless you paid an extra fee, you didn't get a system disc from them.

The solution was to call and say, "Send me a disc. Now." And they would, if somewhat begrudgingly.

It might be different now, but that's what it was like around November 2005 ... the last time I bought a Dell machine.

P.S.: Moving to Windows discussion area. ;)

---

### Post by Brightbelt on 2007-09-12
What some don't realize is that because of having only homemade recovery disks, there is actually No 'free-standing' version of windows there that you could install on a virtual machine.  

Also, even if you do have a separate, store-bought version of windows and you want to install it with a clean wipe, you're screwed if you have to go into the Bios or make any adjustments that call for having the motherboard drivers. 

They're deeply buried in many files and folders in the recovery disks so that they're almost impossible to locate. 

:(

---

### Post by bigboy_pdb on 2007-09-12
> **splintercellguy said:**
> 
dd if=/dev/cdrom (I think, you'll have to see what device corresponds to your DVD reader) of=isofile.iso bs=4096


I already know how to use dd. There are some CDs that don't seem to work with it (they produce errors). Thank you for the response though.

The following site is also pretty informative for anyone who wants to know about copying CDs (or DVDs):
[http://www.troubleshooters.com/linux/coasterless.htm](http://www.troubleshooters.com/linux/coasterless.htm)

A short summary is as follows. You use "isoinfo -d -i */dev/cdrom*" to get the "Logical block size" and "Volume size" of the disc, and then you use "dd if=*/dev/cdrom* bs=*BS* count=*VS*" to copy it (where */dev/cdrom* is the device that corresponds to your CD-ROM drive, *BS* is the "Logical block size", and *VS* is the "Volume size"). To find the CD-ROM device you can type "mount". The device will be the first sequence of characters in a line that has the words "type iso9660".

---

### Post by Bungo Pony on 2007-09-12
I didn't bother with recovery discs or backing up that "hidden" 6G Vista partition. I scrubbed the whole works, installed Win2k and Ubuntu, and have been happy ever since :)

Most people don't get a disc with their PCs anymore. Correction, I got a disc, but it was a MS Easy Upgrade DVD to $-upgrade-$ from Home to Premium. I accidently dropped it in my shredder :)

---

### Post by tech9 on 2007-09-12
> **thewump said:**
> Sorry guys, I know you'll understand my pain, and I think I have some time to kill - so I'll share my misery.

So.. I bought a new HP laptop about 4 hours ago.. pulled it out of the box, stuck a xubuntu live CD in there and fired it up.  While that was booting I went through the box and.. WHAT?  No Windows CDs?  How come?  I don't have a vista install cd so that would be a useful thing to have, and I often install windows under VirtualBox so I can test designs with IE7.

So.. crap... so I have to boot this friggin thing into Vista, and then run a untility to create recovery disks? WTF?

Well first off - HP, what are you THINKING?  You couldn't spend the 24 cents to include the disks? Shame on you.. You managed to include an UPGRADE Cd that would allow me to pay to upgrade to Vista ultimate or whatever the hell it is.. 

Anyway.  So, I boot the machine and install Vista.. and start the recovery disk utility.. and that was, oh, 3 hours ago.. I **** THEE NOT!!!!  It's friggin 8gigs or something!  I'm 61% through verifiying DVD disk 1 of 2.

Good God.  Just how utterly **** can a company be at creating solutions.

So here I am.. 10:56pm and not sure when I'll get to start the job at hand.  Just pulled Blades of Glory from Pay Per View to ease my pain.


Yeah... it's not just HP all company's like dell and Microsoft do not include the disks - you have to pay an additional 10 - 30 dollars sometimes to include the recovery media. 

Most linux flavors are free.

Ubuntu is just looking better and better

---

### Post by Happy_Man on 2007-09-12
Aaah.... if the computer breaks beyond repair (but data is still there), I get to play with it, and recover the data. If the OS is not salvageable, then I get the computer. 


And also, my Dell computer came with a Windows XP SP1 Install CD.... what are you people talking about?

---

### Post by tech9 on 2007-09-13
> **Happy_Man said:**
> Aaah.... if the computer breaks beyond repair (but data is still there), I get to play with it, and recover the data. If the OS is not salvageable, then I get the computer. 


And also, my Dell computer came with a Windows XP SP1 Install CD.... what are you people talking about?

and sometimes they don't

---

### Post by thewump on 2007-09-13
Well it's good to see that I was not the only person to go through this grief. In the end after 3 hours the process stalled while verifying DVD 2 of 2 so I don't even know if I got anything from the process.

Needless to say.. my experience of vista was not a great one.. between that and having to tell it "YES I'M ******* SURE" at every turn it was horrific.

Keith

---

### Post by Depressed Man on 2007-09-13
Lack of recovery disks is likely a new thing. My laptop didn't come with one and has a recovery partition instead. Which kinda stinks..I could cannibalize the 10-12 GBs it uses for Linux or Windows (or hell even OSX) but I have to keep it in case my Vista install screws up (doubt it ever will. But I like having backups).

---

### Post by marx2k on 2007-09-13
This is exactly WHY a lot of people pirate XP/Vista ISOs

---

### Post by Depressed Man on 2007-09-13
I'd imagine it caused the opposit effect of what it was intended to do (I'm assuming that they stopped shipping these for piracy reasons).

But now because nobody has them, they just pirate them to get them when they should've had recovery disks to begin with. 

And ugh at recovery partitions too. If you have to use it, it likely brings back all the **** that came with the preinstalled OS.

---

### Post by Wiebelhaus on 2007-09-13
> **splintercellguy said:**
> It's not just HP. Microsoft has told OEMs not to ship machines with Windows installer CDs/DVDs to curb piracy.

also with the recent change to the stickers one can only assume they don't want people using the software that they own after the initial machine has been destroyed , use to you could use the sticker on as many machines as you wanted but only ONE machine at a time.


Microsuck #1 in resales , suck my *expletive"

---

### Post by sstusick on 2007-09-13
Ditch Winblows and say Hello Ubuntu!

---

### Post by karellen on 2007-09-14
if you bought vista with a new pc and you didn't get a install disk, downloading (pirating) it from the net seems to me a both moral and recommended solution

---

### Post by sstusick on 2007-09-14
> **karellen said:**
> if you bought vista with a new pc and you didn't get a install disk, downloading (pirating) it from the net seems to me a both moral and recommended solution
Actually, the way MS does business, I'd say pirating their shitty OS is moral.

---

### Post by karellen on 2007-09-14
> **sstusick said:**
> Actually, the way MS does business, I'd say pirating their shitty OS is moral.

;) especially the over-priced vista ultimate version...

---

### Post by thewump on 2007-10-02
So here's how this story ended.  A month later, and HP have sent me a recover DVD because my create DVD failed.

I went to install it in Virtualbox.. Why?  Because IE7 is an utter crock of ****, and I have to test CSS designs with it.. Anyway, of COURSE there is something in this DVD that makes sure that it's not going to work for me. Gives me an error that the disk can not recover this machine.

MOTHER-******

---

### Post by sstusick on 2007-10-02
I always wondered if there was a way to extract the OS from a recovery disc. But I'm under the assumption that there is none.

---

### Post by markp1989 on 2007-10-02
with the last computer i got, it came with xp, and it came with a recovery dvd that was BLANK, and then on first boot up it makes me copy the recovery partition to the dvd, whats so hard about making a disk, and why do i have to go through the hassle of burning the DVD then deleting the recovery partition,

---

### Post by wesley_of_course on 2007-10-02
Too  Funny  , ROFL , goodness you couldn't of made that up !  :lolflag:

      That was  one of the best rantings  I have ever read .

           Welcome  , and Thanks for sharing that with us !


  :lolflag:

---

### Post by sstusick on 2007-10-02
> **markp1989 said:**
> with the last computer i got, it came with xp, and it came with a recovery dvd that was BLANK, and then on first boot up it makes me copy the recovery partition to the dvd, whats so hard about making a disk, and why do i have to go through the hassle of burning the DVD then deleting the recovery partition,
They do this because Micro$oft asked them to. It's supposed to cut down on piracy.

---

### Post by kulturloseramerikaner on 2007-10-03
> **sstusick said:**
> They do this because Micro$oft asked them to. It's supposed to cut down on piracy.
Now THAT is funny; what's to stop someone from just telling their burner program they want 75 copies of their recovery partition?  Sounds like MS is being cheap to me; they can save a few cents for the cost of the disk for every license they sell.

---

### Post by jpittack on 2007-10-03
Lucky I have a friend that is a Microsoft partner that I can borrow a disc from for any version of anything and run a recover.  It happens often.  98, xp, vista, vista again, xp again. sigh.  why won't my family switch.

---

