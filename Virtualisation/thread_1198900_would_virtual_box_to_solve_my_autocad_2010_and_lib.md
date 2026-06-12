---
title: "would virtual box to solve my autocad 2010 and libmtp problem"
date: 2009-06-28
forum: Virtualisation
---

### Post by Mia1990 on 2009-06-28
my problem is my collage requires me to have autocad they would prefer 2010 but 2008 will do my system is ubuntu 9.04 3GB ram and 512 on the video card wine will run autocad but it is slow real slow how much slower would it be on virtual box?Also my sansa view will not work with mtp tools could i use virtual box and winamp to put music on my mp3 player? 

thank you
i really don't want to dual boot i hate that

Mia

---

### Post by X_Splinter on 2009-06-29
I never try it, but with that much of ram video memory if you use VirtualBox 3.0 Beta that has a new video acceleration driver I am pretty sure you can do it.

Just release half of your RAM and video memory to a guest Win XP.

It should work great.

If you try it let us know the result

---

### Post by Mia1990 on 2009-06-29
> **X_Splinter said:**
> I never try it, but with that much of ram video memory if you use VirtualBox 3.0 Beta that has a new video acceleration driver I am pretty sure you can do it.

Just release half of your RAM and video memory to a guest Win XP.

It should work great.

If you try it let us know the result
how do i  release half of my ram and video memory to the guest i have never used
anything other then wine.Will that will solve my libmtp problem to?

---

### Post by X_Splinter on 2009-06-30
> **Mia1990 said:**
> how do i  release half of my ram and video memory to the guest i have never used
anything other then wine.Will that will solve my libmtp problem to?

You first need to install Virtual Box.

[Download Virtualbox3.0.0_BETA1 here]("http://download.virtualbox.org/virtualbox/3.0.0_BETA1/")

Then Install WIN XP on it

[URL="http://www.youtube.com/watch?v=YhTb_7TSDXQ"]Video of How to install it
[/URL]
Then I tell you what to do next

---

### Post by tvtech on 2009-07-01
> **Mia1990 said:**
> my problem is my collage requires me to have autocad they would prefer 2010 but 2008 will do my system is ubuntu 9.04 3GB ram and 512 on the video card wine will run autocad but it is slow real slow how much slower would it be on virtual box?Also my sansa view will not work with mtp tools could i use virtual box and winamp to put music on my mp3 player? 

thank you
i really don't want to dual boot i hate that

Mia

I am currently running autocad 2009, 2010, microsoft visual studio in windows xp sp3 on a virtual machine in vbox. 


They work GREAT

Autocad takes a little longer to render on large drawings but I have used it for production scale work with no noticeable slow down.  I gave my virtual machine 1028 of my ram.  The 3d rendering even works although it's a little slow and choppy due to vbox not supporting direct 3d.  NXtop and vmware both have experimental direct 3d support but they cost money. 

my hardware is pretty up there though.  I've got a 64 bit ubuntu install on a core 2 2.5 gig with 4 gigs of ram and 512 meg video card.  Windows runs pretty much flawlessly in Vbox although I've been having registry errors due to visual studio lately.  In fact windows runs faster in my vbox install than it does on the hardware natively.  Boots faster runs better and I can snap shot it to save my butt.  I highly recommend this. 

let me know if this helps. **the best thing is** you can snap shot your original install and just revert to it when your trial runs out!!!! so autodesk can take their 5k price tag and stick it to the wall.

---

### Post by tvtech on 2009-07-01
> **Mia1990 said:**
> how do i  release half of my ram and video memory to the guest i have never used
anything other then wine.Will that will solve my libmtp problem to?



should solve the libmtp problem as well you may have to tweek that though.  it's part of the set up of virtualbox to release the memory to it.  

The best thing is that once you set the image up you can move it to any other computer you want.  if you use clonezilla via parted magic "a great live cd"  you can even add multiple versions of the same install and avoid using vbox's clone hdd  which is command line cumbersome and tends to not work well. 

Vbox actually comes with an excellent pdf manual which is easy to read and describes in detail how to do EVERYTHING you need.  If I remember correctly there was even a walk through on building your first VM.  Basically it's a point and click GUI, with some really advanced configuration in the command line architecture.  If you understand wine you'll have no problem setting up vbox.  I do recommend though.  Dual hard drives are a must.  you should** always always always** run your vbox image on a different hard drive than your host OS.  if you don't your slow down won't be because of your hardware it will be because two hosts are trying to access info off the same platter at the same time.

---

### Post by X_Splinter on 2009-07-01
"NXtop and vmware both have experimental direct 3d support but they cost money. "

Virtual Box 3 Beta has an direct 3d support, it is still beta but you should give it a try.

How much video memory do you give to Winxp on VB?

---

### Post by tvtech on 2009-07-01
I just upgraded to vbox 3.0 a few hours ago.  It is out of beta and in final release.  The 3d acceleration is still experimental and may be hardware dependent.  It has to be installed while windows is in safe mode.  I installed the guest additions acceleration for use with direct x9 which is what autocad is dependent on.  It works quite well with Autocad 2010  and 2009 increases the render rate to an acceptable level.  please note this was done with nvidia 9600GS video card running driver 180.44  on ubuntu jaunty 9.10 kernel 2.6.28-13 generic under gnome 2.26.1 


> How much video memory do you give to Winxp on VB? 
I give up 128 meg of ram to vbox as I have 512 dedicated on my video card.  leaving me more than enough to run compiz fusions heaviest plug ins without much complaint at all. 

However, I've started doing some live video editing with KDEnlive and have discovered that two terabytes of hdd is not nearly enough.  the computer that I edit from is a laptop with two 250gig hdds and I'm seriously thinking of upgrading to two 500gig drives.  or I may finally blow my vista dual boot away. I don't know yet.

---

### Post by Mia1990 on 2009-07-02
I have 3GB system ram and 512 mb on the video card

---

### Post by X_Splinter on 2009-07-02
I only have 2g Ram and 128mb of video

---

### Post by Mia1990 on 2009-07-03
ok guy's i could really use your help setting this up i have installed virtual box 3 that was easy and i am getting ready to install win xp.

Edit How much ram should i give up i guess should be my first question here is what the system requirements for autocad 2010 is

Microsoft® Windows® XP Professional or Home edition (SP2 or later)Intel® Pentium® 4 or AMD Athlon® dual-core processor, 1.6 GHz or higher with SSE2 technology2 GB RAM
1 GB free disk space for installation
1,024 x 768 VGA display with true color
Microsoft® Internet Explorer® 7.0 or later  
Install from download, DVD, or CD

my next question is when i get to the pick hard drive window this is what it says

 p, li { white-space: pre-wrap; }  Select a hard disk image to be used as the boot hard disk of the virtual machine. You can either create a new hard disk using the New button or select an existing hard disk image from the drop-down list or by pressing the Existing button (to invoke the Virtual Media Manager dialog).
 If you need a more complicated hard disk setup, you can also skip this step and attach hard disks later using the VM Settings dialog.
 p, li { white-space: pre-wrap; } The recommended size of the boot hard disk is 10240 MB.
boot hard disk(primary master)

  create new hard disk
  use existing hard disk
then it looks like there is a drop down list but it says no media
please help i do not want to use the entire hard drive what i'm installing it on is only a test pc

---

### Post by X_Splinter on 2009-07-03
Create a new disk(which is a virtual one).

Select the size you want, 10 g should do it.

Then select the RAM, usually we put less than 50% but if you have 3g you can put 2g

---

