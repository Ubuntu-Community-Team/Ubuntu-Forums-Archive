---
title: "Upgrade Server to RAID 1 After Install / DMRAID Necessary?"
date: 2010-11-27
forum: Server Platforms
---

### Post by bsntech on 2010-11-27
Hello all,

I have two Ubuntu 8.04 servers currently.

I've purchased some 500 GB hard drives and a RAID cage just yesterday and plan to change my current servers to using RAID1 with the hard drives.

Much like everyone else, I have the nVidia RAID built onto the motherboard that I plan to use.

There are many how-to's out there on how to setup RAID using dmraid during the install process - but what would a person do if they are simply changing over to a RAId system?

I installed dmraid a few days ago on the server.  It seems that even though I have RAID shut off in the BIOS, it saw the one and only drive as a mirrored array.  When I rebooted today, the server would not start; it had ERROR:  degraded disks.. bla bla.  Then Grub tried to start the partition based off the UUID of the drive (which was not changed) and it said "device or resource busy" and would not boot.

This problem was corrected by going into the BIOS and turning on RAID.  When I rebooted, the nVidia RAID firmware started and said degraded.  I went in there and deleted the so-called mirror keeping the data intact.  Rebooted, disabled the RAID feature in the BIOS and then the server loaded normally with a message "NO RAID DISKS" - but at lest it did boot!

So this leads me to believe that trying to turn on a RAID-1 array (just mirror between two disks) may be a challenge since I already have the system installed.  I will be using Partimage to make an image of the current hard drive and then restore it to one of the new drives.

The next question is - is it a requirement that dmraid is even installed?  While I understand that the nVidia RAID is fake-raid - if I go into the nVidia RAID controller and setup the mirroring between the two disks before I even restore the files to the new disk, will both drives be mirrored?  However, I do think that I'd probably have to have dmraid installed to check the integrity of the array.

So, I'm just a bit lost on this subject.  I definitely do not want to start this server over from scratch - so curious to know if anyone has any guidance on simply making a mirrored array after the install procedure, what kind of Grub changes will be needed (because of the previous resource is busy message), and whether installing dmraid is even a requirement.

---

### Post by windependence on 2010-11-27
You don't need (and probably shouldn't) to install dmraid if you are going tio use hardware RAID. You simply set up your RAID in the BIOS and install your OS on top of that. The big IF is if Ubuntu will see the RAID array. With most, not all fake RAID, Ubuntu may not see the array and will just treat the drives as individual drives.
 
I am a fan of hardware RAID, but that is just my opinion. I just like the convenience of hardware RAID and the fact that I can boot off the array. YMMV.
 
-Tim

---

### Post by bsntech on 2010-11-27
I know that it should be bootable.  Before I had two servers, I had two 80 GB drives in one machine using nVidia RAID in RAID-1 mode in Windows without any troubles.

But, nVidia RAID is not hardware raid.  If it was, I know that dmraid would not be needed - but since this is a fakeraid, it is different.

---

### Post by windependence on 2010-11-27
You're still confused I think. Have you tried the nVidia RAID with Ubuntu? 
 
You might be interested in this:
 
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
 
-Tim

---

### Post by bsntech on 2010-11-27
The more research I am doing on these sofware arrays - even dmraid - the more I believe these are not very good redundant solutions.

It seems that dmraid cannot - at least from the posts I've found - rebuilt an array if it is degraded or fails.  Well that certainly takes the functionality out!

I've also read others about using Linux sofware raid and that seems to also have it's own problems.

Looks like getting an actual hardware-RAID controller is the way anyone should go if you want a RAID-array in Linux.  Even getting one of these controllers though - begs the question - how can you tell in Ubuntu when one of the drives fail/is degraded without rebooting and going into the BIOS utility?  Maybe I'm too used to the controllers in HP and Dell servers where the lights on the front of the RAID cages blink or are red if one of the drives fails.  And in those cases - you just pope the drive out, put a new one in - and it rebuilds with zero intervention.

Anyone have an inexpensive hardware-RAID board they would recommend?  Looking on NewEgg, it seems pretty hard to decipher which ones are FakeRAID or actual real hardware controllers.

---

### Post by windependence on 2010-11-27
If you are just going to use RAID 1 then I recommend any card based on the Silicon Image 3512 chip. There are tons of brands out there that have that chip and they are super cheap, usually less than $20. If you can't find one, I can send you one, just let me know.
 
-Tim

---

### Post by bsntech on 2010-11-27
Thank you, Tim.

I see NewEgg does have a lot of those based on the Silicon Image chipset - but I thought I read that it is a software-based RAID and not hardware.

Can you confirm whether those are indeed hardware-based RAID cards?

Also - if the array fails when using those boards - how can you tell within Ubuntu that the array is degraded /failed so that one of the drives can be replaced?

What about the procedure for rebuilding?  But yes, RAID-1 is all I am after.  I've purchased a hot-pluggable RAID cage and would really like to be able to pull out the bad disk and just plug in the new one and it automatically rebuild.  Is that a feature of these cheaper cards?

---

### Post by bsntech on 2010-11-27
Research on the Silicon Image 3512 also shows that it is a software raid controller and dmraid is required to use it.

So that goes back to the problem of taking a current Ubuntu server image and restoring it to a RAID-1 array.. then what happens if one of the drives fail and how easy is the rebuilding process?

Just want to ensure I cover all of the bases here from the install procedure all the way to a potential failure and a rebuild procedure.

---

### Post by windependence on 2010-11-27
Do not automatically assume that every software controller needs dmraid, they don't. I use this card extensively on my Linux and Unix machines and they work just fine. Rebuilding and replacing drives is not a problem at all.
 
-Tim

---

### Post by bsntech on 2010-11-27
Do you believe this is the case with the built-in nVidia raid controllers?

Both motherboards I have do have this built-in nVidia raid controller with four ports on it.  While I would only use maybe three (two in a RAID-1 and use another for doing nightly backups), this would prevent me from purchasing additional add-in cards if not necessary.

---

### Post by bsntech on 2010-11-27
And Tim -

One more question.  With your use of those RAID cards, how does Linux alert you when the mirror is degraded or one of your drives fail?  To me, it is all nice and dandy to have a RAID-1 array for the redundancy - but if you don't know when the mirror fails, both could potentially go bad within a period of time.  I do a lot of unattended reboots on the 'servers' without being in front of a monitor to tell if the RAID BIOS shows a problem.

---

### Post by windependence on 2010-11-27
Well, I usually build all my RAID arrays in hot swappable cages with indicator lights but I think there are actually some software utilities you can use to monitor the drive status. You'll have to search around or maybe someone will suggest a way to do it without an enclosure.
 
Let me look around and see what I can find. I don't use RAID 1 much, for me is usually RAID 5.
 
-Tim

---

### Post by bsntech on 2010-11-27
I do appreciate all the help you are providing, Tim.

I looked on some nVidia Forums to try to see if the array can be rebuilt from the BIOS utility, but there are differing reports whether you can do so or not.

Like you said, I just ordered a 4-bay RAID cage with indicator lights - but there isn't any status LEDs on it - just if the drive has power and it will flash if there is hard drive activity.

Two other questions for you.  The reading I did about the Silicon Image 3512 chipset turned up that even if you have RAID-1 set, it still shows two completely separate drives in Linux without using dmraid.  Is this the same thing you experience as well?  Surely I would think you have some kind of software installed on your machine that takes care of your RAID array.

And lastly - I actually do a full shutdown on the servers once every quarter and use partimage - which is run from a bootable external hard drive - to do a full backup of the server disk - which is then saved to the external drive.  A thread I came across was sort of similar to this - saying that if they booted off of a Live CD to access their RAID array, it would degrade the RAID array because the Live CD may access one of the two drives in the array.  Again, that is because dmraid or any other software raid is not installed in the Live CD.  Have you had any issues like this?  Even though I want to move to a RAID array, I still will do quarterly backups of the disk that can be stored offsite.

Sure would be much easier if this RAID technology just worked without any of this mess.  Windows has the upper-hand when it comes to the FakeRAID stuff because all of the manufacturers write the drivers for it - and it just works.

---

### Post by bsntech on 2010-11-28
Upgraded one of the servers to 10.04 today - should have done it a long time ago but opted to do so today with the new hardware coming in on Wednesday.

10.04 includes dmraid 1.0.0 rc16.  Does anyone know if this version works with rebuilds if a RAID-1 array degrades - and whether it will still allow the array to boot even if it is degraded - so it can be rebuilt while running (like in Windows)?

---

### Post by olithered on 2011-01-02
> **bsntech said:**
> 
10.04 includes dmraid 1.0.0 rc16.  Does anyone know if this version works with rebuilds if a RAID-1 array degrades - and whether it will still allow the array to boot even if it is degraded - so it can be rebuilt while running (like in Windows)?

You can see the docs and changelog by downloading the source file archive from here:
  [http://people.redhat.com/heinzm/sw/dmraid/src/](http://people.redhat.com/heinzm/sw/dmraid/src/)

---

