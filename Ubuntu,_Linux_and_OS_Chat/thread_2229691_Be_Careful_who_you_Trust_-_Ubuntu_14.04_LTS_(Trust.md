---
title: "Be Careful who you Trust - Ubuntu 14.04 LTS (Trusty Tahr)"
date: 2014-06-14
forum: Ubuntu, Linux and OS Chat
---

### Post by Johnny M! on 2014-06-14
Ubuntu 14.04 LTS (Trusty Tahr) Installation Woes


I'm a big fan of Ubuntu who's used 8.04 and 10.04 for the last 7 years.   Since I just finished building a brand new PC; I was excited (and long past due) about dual-booting Ubuntu 14.04 with Windows 7 (both 64-bit).
I'm not a computer novice and I'm quite willing and able to search the Forums to extract solutions.      I've spent the last few months scanning 14.04 Installation information to see what kind of troubles I might encounter with my new higher-end Machine.   But my last 36 hours with Trusty Tahr was not (what one would call) enjoyable. 

So here Goes:

- The Ubuntu (Live) Install DVD I burned from the iso Image was recognized by my 5 year old Machine, but NOT be my brand new PC.   So I have to reaccomplish this (using the exact same brand & type DVD) using my new PC.   

- Booting from the Ubuntu Install DVD gave me the initial text menu (Demo, Install, etc Choices), but beyond this step the Monitor went Black and stayed Black !   Again & again - No Nothing !  All-Right: to the Help Forums (Blessed Lady of Google, don't fail me now).     Here we go - Ubuntu can fail to output Video thru the (discrete) Video Card, and you have to hook up to the Onboard CPU Graphics.   OK - back to BIOS to swap Graphics.   Re-attach the DVI Cable.   Hey, even 13 year Old Windows XP could output low-res graphics thru whatever Video Card you had installed.   Here we are at Ubuntu 2014 and WHAT is this ???   **STRIKE One !**

- OK, now were cooking.   Install is working (yes I want English, etc...).   I had reserved un-allocated space on my main System SSD for Ubuntu, and its Swap Partition (Windows 7 Pro is already up and running).  Since I know exactly where I want to put Ubuntu, I selecting "Something Else" on the Installation Type Dialog Box.  So Ubuntu knows I want a brand new Installation - why is it asking me for what Type of Partition (Primary vs Logical) and Mount Point (aren't OS's always installed on Primary Partitions, and at the Root of their assigned System Partition) ???   Sort of a Curve Ball here without a conveniently placed Help link to explain why Ubuntu isn't clear about what should be its Default install settings.

- Ubuntu is Installed !   Great - time to Re-Boot and test out this new GRUB 2 and see if if got things right.   Re-Start and BAM - straight to Ubuntu.  No Dual-Boot Options!   Well that Sucks!   Back to Google - OK, Update GRUB.   Why isn't this part of the Install Routine to check on already installed OSs and just make it So ?????    **STRIKE Two !**

- With GRUB now up to speed, lets change which OS is default; back to Google.   I had the previous GRUB's Menu.lst figured out pretty well, but now it aint that simple.  But I'm OK with it; I changed Windows 7 Boot Name (to "Windows 7 Professional") and made it the Default OS Choice.

- OK, Lookin Good.   No all I have to do is get the NVIDIA Video Driver installed, swap graphics in BIOS and change the DVI Cable.    

- Now a quick word about Ubuntu and Video Drivers.   I'm sure most users would agree that there's definitely still some opportunity for improvement here.   I thought installing AMD Drivers were awkward, try NVIDIA.   What a convoluted process (and that's just to figure out how to).   The actual procedure is ridiculous. For the life of me, I just can't figure out why this has to be this user unfriendly. 

- So after re-typing "sudo sh ./NVIDIA-Linux-x86_64-331.79.run" numerous times, I proceeded thru the arcane and cryptic menu choices and it looked like it Worked.  Wonderful!  OK - I've made some mega-progress on my Dual-Boot Machine.   Time to re-boot and see Ubuntu in all its 2560x1600 pixel glory !

- Swap BIOS Graphics and DVI Cable, Boot back to Ubuntu and BAM - A Kick in the Gonads !    I'm staring at a Blank Ubuntu Desktop - No Icons - No Nothing !    Re-Boot - SAME. 
That's the last straw - **STRIKE Three ! **   Ubuntu - You're Outta Here ! 

OK - I cried "Uncle".   

Additionally, I was also leery of getting Ubuntu connecting on my hi-end Wireless Adapter.   Hear about a lot of frustration in this area; and since my Wireless Adapter came with Windows only drivers - I wasn't looking forward to that wrestling match.

Ubuntu was like Icing on the Cake for this Build - Nice to have but not totally necessary.   I'm sad and discouraged, but still admire Ubuntu. 

I was disappointed that (in the intervening 4 years since I last installed a LTS) Ubuntu hadn't better automated things I was hoping I could take for granted.    The look & feel of 14.04 just didn't snap onto my "Must Have" list.  And who's idea was it to make the Terminal Window Black - that's Morbid !

Don't worry - I'll be Back !    I love the Open Source (and did I mention, FREE) Ubuntu Linux concept.   Maybe I'll next build a (dedicated Ubuntu Only) basic PC just for simple Word Processing, Internet and e-Mail.  I'm guessing a basic PC using onboard graphics will be a piece of cake for Ubuntu.  If I have to wait for 16.04; that's OK !

---

### Post by QIII on 2014-06-14
Moved to Ubuntu, Linux & OS Chat

---

### Post by CharlesA on 2014-06-14
Sounds like a problem that would probably have been solved with nomodset.

See here:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by grahammechanical on 2014-06-14
> [COLOR=#000000]And who's idea was it to make the Terminal Window Black - that's Morbid ![/COLOR]

Certainly not the Ubuntu developers because the background to the terminal is Canonical purple. **Strike 1 against you! **How I love it when complainers and moaners get it wrong. Now what else can I find? But why bother? I have a life to live.

---

### Post by Johnny M! on 2014-06-15
Thank you to "CharlesA" for the nomodset Tip:  I will try that on my next Install Attempt

And Thank You to "grahammechanical" for reminding me that Beggars can't be Choosy" !

I didn't mean to complain and moan (but I did)!   Yeah - I was venting frustration at not getting my way with Ubuntu.
But there were two main reasons I took the time & effort to document my unsuccessful attempt to install Ubuntu in a dual-boot machine:

[INDENT]1. Just to inform other average Ubuntu Users such as myself.  I'm sure that many have had, and many will have, similar problems.   I managed to solve a few of the problems I encountered myself, and the reply to this topic suggested additional trouble-shooting.  That's what forums are for - to "Share the Bear" !

2. To high-light opportunities for improvement that Ubuntu Developers can shoot for.  I'm just an average User, and don't know the technical reasons why some things aren't as easy as I would expect.  Although users have a debt of gratitude for the people who make Ubuntu possible; they also have the right to wish for better user friendliness.
[/INDENT]


Let me offer an example from an average user's perspective.   
Drivers - namely Video Drivers.  

The software to firmware to hardware interface to get a picture on a monitor is a basic fundamental task for every PC.  For Ubuntu for Desktops (discounting professional scientific and engineering Workstations), there are only 4 possible graphic configurations:   Onboard integrated graphics (either AMD or Intel); and discrete stand alone Video Cards (either AMD or Nvidia).   So for the average user to expect Plug & Play Graphics is not an unreasonable expectation.  The Ubuntu Techies know why things aren't always that simple - but average Joe Smoes like myself have to Grin and Bear.

And although the Terminal Window is actually [COLOR=#4b0082]**Canonical Purple**[/COLOR], it sure looked **Black** to me ! 

BVR,
Johnny M!

---

### Post by kurt18947 on 2014-06-15
Just to relate personal experience, I have had black screens as you relate but only using developmental versions.  I'd see them when using the open video driver on an Nvidia card.  Once I installed the Nvidia driver the black screen went away.  And it always occured after resuming from suspend, never on a cold boot.  I don't know that this will help, just a data point.

---

### Post by pauljwells on 2014-06-15
I'm not a gamer, so I have the luxury of choosing harware that supports full OSS drivers. I have a Core i7 Quad machine with Intel graphics. Ubuntu 14.04 works perfectly!

---

### Post by poet1 on 2014-06-15
Does Ubuntu recognize all the cores in that processor, pauljwells?

---

### Post by craig10x on 2014-06-15
It does on mine...my computer has an i3 quad core (Intel graphics) and when i bring up system monitor it shows all 4 are running on Trusty Tahr :)

---

### Post by QIII on 2014-06-16
> **Johnny M! said:**
> Let me offer an example from an average user's perspective.   
Drivers - namely Video Drivers.  

The software to firmware to hardware interface to get a picture on a monitor is a basic fundamental task for every PC.  For Ubuntu for Desktops (discounting professional scientific and engineering Workstations), there are only 4 possible graphic configurations:   Onboard integrated graphics (either AMD or Intel); and discrete stand alone Video Cards (either AMD or Nvidia).   So for the average user to expect Plug & Play Graphics is not an unreasonable expectation.  The Ubuntu Techies know why things aren't always that simple - but average Joe Smoes like myself have to Grin and Bear.


Why should the Ubuntu devs write drivers for ATI, NVIDIA or Intel?  Microsoft doesn't write Windows drivers for them.  

They are only PnP on Windows because ATI, NVIDIA and Intel jump through hoops and grovel to be sure that their drivers work with Windows so they can be put in the driverbase -- which is what makes them PnP.  They do that for Windows because if they didn't they'd go bankrupt.  Linux, with a puny 2% market share, doesn't rate the effort.

TL;DR?

ATI, NVIDIA and Intel write drivers for their hardware.  OS purveyors don't.

---

### Post by help_me2 on 2014-06-17
> **QIII said:**
> Why should the Ubuntu devs write drivers for ATI, NVIDIA or Intel?  Microsoft doesn't write Windows drivers for them.  


Good point, but one that goes over a lot of people's heads. Ubuntu/Canonical is always to blame. :rolleyes:

---

### Post by cariboo on 2014-06-17
I don't understand why the op tried to install the drivers from Nvidia, when there are drivers in the Repositories for most supported video cards. If the drivers in the repository aren't new enough, there is the xorg-edgers ppa dor newer drivers.

---

