---
title: "Strange DVD playback issue - The Community Cafe Edition"
date: 2010-05-29
forum: The Cafe
---

### Post by sydbat on 2010-05-29
I posted this a few days ago in the [Multimedia & Video]("http://ubuntuforums.org/showpost.php?p=9358081&postcount=1") board, but got no answer at all. I figure someone here, who may not frequent those particular support boards, might be able to help.

Here's the original post:> I can play regular DVD's without a problem. However, if I record something with my Samsung DVD-R150 (part of my home theatre), I cannot play it at all on my computer. Even when I had Windows XP, I could not play anything from this DVD recorder.

I have tried several DVD players/DVDRW in this computer, along with both WinXP and Ubuntu, and they all give the same result...the discs recorded with the Samsung DVD-R150 are not read at all and I have to reboot to get the disc out of the computer. This has been going on since Hardy (currently on Karmic). I no longer have XP on this box.

Now the really strange bits - the DVDRW in my computer is a Samsung. Also, everyone else can play these discs in their computers (regardless of OS) and home DVD players without any issues. I have never had a problem recording with the DVDRW in my box, or with playback anywhere...only the stuff I have recorded with the home theatre DVD recorder.

First, has anyone else had this problem? With the same DVD recorder?
Second, any theories why only my computer will not play these discs?

I know it is not a hardware problem, as I stated above I can play every other DVD with no issue (yes, even ones burned by others). And there is nothing copy written that I am recording, just my own home videos.

Thanks in advance.

---

### Post by Cathhsmom on 2010-05-29
Your problem might be as simple as installing some codecs.  You might want to look at this thread. [http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by sydbat on 2010-05-29
> **Cathhsmom said:**
> Your problem might be as simple as installing some codecs.  You might want to look at this thread. [http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")Thanks. However, all of that has been done. Even reinstalling all the codecs hasn't done a thing. And remember, I can play any other DVD without problems.

---

### Post by buddyd16 on 2010-05-29
do the disks play in the recorder itself?

Is the recorder finalizing the disks?

---

### Post by sydbat on 2010-05-29
> **buddyd16 said:**
> do the disks play in the recorder itself?

Is the recorder finalizing the disks?Yes to both. And they play in other peoples DVD players and computer DVD players without a hitch. They just do not play in MY computer DVD player...and I have tried 3 different DVDRW's that all work fine with (previously XP and) Linux and every other DVD, just not the ones recorded in the Samsung.

I hope you can see my frustration.

---

### Post by buddyd16 on 2010-05-29
this may be going out on a limb but have you tried to mount the dvd drive/disc in a terminal and see if it spits out any errors?

---

### Post by sydbat on 2010-05-29
> **buddyd16 said:**
> this may be going out on a limb but have you tried to mount the dvd drive/disc in a terminal and see if it spits out any errors?I'll do that and post anything back here.

---

### Post by sydbat on 2010-05-31
Nothing. Won't mount with those particular DVD's in the drive. I have no problem with any other DVD's.

I'm getting really frustrated with this Samsung DVD recorder.

---

### Post by Linux_junkie on 2010-05-31
I notice that you mentioned your Samsung DVD recorder is a -r DVDRW machine and from what I gather there are two "versions" of DVD-RW's +r and -r.  If your PC DVDRW is a +r drive it won't be compatible with the -r DVDRW drive of the Samsung.

I hope this has helped.

---

### Post by sydbat on 2010-05-31
> **Linux_junkie said:**
> I notice that you mentioned your Samsung DVD recorder is a -r DVDRW machine and from what I gather there are two "versions" of DVD-RW's +r and -r.  If your PC DVDRW is a +r drive it won't be compatible with the -r DVDRW drive of the Samsung.

I hope this has helped.If I understand correctly, my home theatre DVD writer is -r and so is my computer DVDRW. That both right now are Samsung makes this even weirder.

Also, the DVD discs are -r too.

And, as I stated in my OP, I have tried playing those home theatre recorded DVD's on my computer in both XP and Ubuntu to no avail. I have also tried older DVD players/writers in my computer with the same result - no mounting and no playing. Yet the same DVD's made with the home theatre DVD writer play EVERYWHERE else.

I'm getting to the point where I will need hair replacement therapy...soon...

---

### Post by Linux_junkie on 2010-06-01
Very strange! The only other thing I can think of that may cause the problem is that the Samsung DVDRW is recording at a much higher speed to what the computer DVDRW can read.  But then you said they will play in other DVD players / computers.

It must be a problem with your computer / DVDRW drive!  

Could you connect an external DVDRW drive to your computer to test if the disk works that way?

---

### Post by sydbat on 2010-06-01
> **Linux_junkie said:**
> Very strange! The only other thing I can think of that may cause the problem is that the Samsung DVDRW is recording at a much higher speed to what the computer DVDRW can read.  But then you said they will play in other DVD players / computers.

It must be a problem with your computer / DVDRW drive!  

Could you connect an external DVDRW drive to your computer to test if the disk works that way?Haven't connected an external yet, but have tried 2 different internal ones. I will borrow an external and try it.

I think everyone who is trying to help (THANK YOU ALL) is starting to see my frustration with this.

---

### Post by blueturtl on 2010-06-01
This has been said already but it's probably a problem with the combination of media and drives being used.

I've been recently dealing with recordable DVDs and it turned out that from the stuff our local shop sells, one brand of rewritable DVDs is readable in my HTPC, the other not at all.

In my case it's a Sony-Nec (Optiarc) DVD Writer and it won't even read Sony's own brand DVD-RW discs once I used the external recorder fill them with data. :D Wife's lappy on the other hand has no issue with them and it has an older drive.

My suggestion: try burning different media.

---

### Post by Ebere on 2010-06-01
I would try different disks, first. (Different brand, etc.)

It sounds to me like there is something proprietary that the samsungs do, when writing to dvd, which... Although the disk is getting 'closed', the proprietary process is -not- finalizing.

Put the disk in the other samsung, and it gets hung up, because of that unfinalized process.

Put it in any other drive, and there is no problem, because they ignore the open process.

Try to find someone else with the same brand, model, etc, of the dvd drive, and try one of your disks in their drive.

~~~

To get the disk out, without rebooting, try going to the computer icon, open that. Locate the icon for the dvd drive. Now right click on the icon, and select "eject".

---

