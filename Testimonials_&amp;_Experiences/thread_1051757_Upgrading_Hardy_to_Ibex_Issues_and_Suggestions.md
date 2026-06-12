---
title: "Upgrading Hardy to Ibex: Issues and Suggestions"
date: 2009-01-27
forum: Testimonials &amp; Experiences
---

### Post by SharkSkinMan on 2009-01-27
So I upgraded from Hardy to Intrepid last night.  I hadn't gotten round to the upgrade for a number of reasons, so it had been a while since my last upgrade.  I experienced a number of issues, which I'll cover below for the purposes of constructive criticism.  Not sure if there's a better place for this, so let me know if I've posted in the wrong area:

[LIST]
[*]Due to bandwidth restrictions at my ISP, I mainly use their repository (downloading from them is not counted towards my monthly quota).  I downloaded the ISO from them, and burnt it to DVD for the installation process.  As Ubuntu sees their repository as a third party repository, it comments it out in my sources.list.  This then means that I have to tell the installer not to download further updates, and I need to do it myself afterwards.  

It'd be better if the installer asked me if I wanted to use my own repository in this situation.


[*]I'm using Ubuntu rather than Kubuntu.  The upgrader doesn't appear to be able to deal with the idea that I might be using KDE-based programs (eg, Amarok).  These were all uninstalled during the upgrade process, forcing me to go back and reinstall all of them afterwards.  

If no upgraded version is available, shouldn't the old version be left alone?  And if it's out of date, is there any way the package could be marked for upgrade automatically the next time I open Synaptic?


[*]Updating menu.lst is a pain: Firstly, I'm asked about it multiple times during the upgrade process - this seems a bit unnecessary.  Secondly, the options given are not very clear.  The first option (use the version from the package) doesn't indicate whether or not it will keep any settings that the user may have put there themselves.  My machine is dual-boot, and I had no idea what was going to happen to my Windows boot settings.  (yes, there is a diff option - but this isn't great when what I really wanted to see was what the new file was going to look like).  

To be honest, what this really needs are slightly clearer menu options, and the chance to preview the new version of the file.


[*]Nvidia drivers didn't work after the upgrade.  I found this listed as a known issue, so I'll leave this one.  The error message given seemed to be pretty clear, and it was easy for me to fix on my own anyway.


[*]Apt-get and Synaptic are working a bit strangely after updating.  This may be a problem that was happening previously, so I'm not sure if it's due to the upgrade, my repository, or something else.  I'm finding that some packages are not listed in Synaptic, even though they're available.  For example, I wanted to install Blender after the upgrade.  Not listed in Synaptic.  I figured, maybe it's my repository, so I switched to the main Australian mirror, and reloaded the package lists in Synaptic.  Still not there.  I then tried apt-get install... it worked.  Even though Blender's not listed by Synaptic (and it's not the only package in that situation).  

This is still confusing me, and I'll need to have a look to see if anyone else has encountered the same issues previously.

[/LIST]
Having said all that, everything seems to be working pretty well now (barring apt), so I'm just offering a bit of constructive criticism, hoping the process can go a bit better next time.

---

### Post by wolfen69 on 2009-01-27
upgrading can be hit or miss. that's why i always recommend a fresh install no matter what OS. if downloading ubuntu cuts into your monthly quota, you can always request a free cd from canonical.

---

### Post by stchman on 2009-01-27
I cannot find a compelling reason to upgrade from Hardy to Intrepid.  I have intrepid installed on my Acer Aspire One as it supports the AA1 hardware a little better.  If your PC is running Hardy just fine then I recommend leave it alone.

---

### Post by solwic on 2009-01-27
> **wolfen69 said:**
> upgrading can be hit or miss. that's why i always recommend a fresh install no matter what OS. if downloading ubuntu cuts into your monthly quota, you can always request a free cd from canonical.

Ouch.  The monthly quota thing has started?  I've got Time Warner for my cable, and I read they were testing it in Texas or something.  Fortunately they haven't pulled the crap here *yet*.  

Are the quotas hard to deal with?  I mean, do you have to watch what web sites you load, or how many videos on youtube you watch?  

I tried the CD thing from Canonical, too.  It had errors.  :(

---

### Post by 3rdalbum on 2009-01-28
> **SharkSkinMan said:**
> So I upgraded from Hardy to Intrepid last night. 

[LIST]
[*]Due to bandwidth restrictions at my ISP, I mainly use their repository (downloading from them is not counted towards my monthly quota).  I downloaded the ISO from them, and burnt it to DVD for the installation process.

I'm using Ubuntu rather than Kubuntu.  The upgrader doesn't appear to be able to deal with the idea that I might be using KDE-based programs (eg, Amarok).  These were all uninstalled during the upgrade process, forcing me to go back and reinstall all of them afterwards.  

If no upgraded version is available, shouldn't the old version be left alone?  And if it's out of date, is there any way the package could be marked for upgrade automatically the next time I open Synaptic?

You know what? You're absolutely right. I actually encountered that problem when upgrading my workmate's machine last night. In the process of trying to fix her wireless, I ended off destroying it and had to upgrade her to Intrepid using an alternative CD. Using the "cdromupgrade" script with no internet connection resulted in the removal of every package that's not on the CD!

I'm pretty sure the installer used to do what you're suggesting - install the updated packages and leave the old packages alone, but I can see why the Apt system might want to remove the old packages. Heck, Ubuntu used to offer to add the alternate CD as a software source as soon as you inserted it; remember that? I was trying to use apt-cdrom initially, but it didn't work.

---

### Post by SharkSkinMan on 2009-01-29
> **jrock612 said:**
> Ouch.  The monthly quota thing has started?  I've got Time Warner for my cable, and I read they were testing it in Texas or something.  Fortunately they haven't pulled the crap here *yet*.  

Are the quotas hard to deal with?  I mean, do you have to watch what web sites you load, or how many videos on youtube you watch?  

I tried the CD thing from Canonical, too.  It had errors.  :(

Quotas are pretty much standard here in Australia, and have been for a long time.  Fortunately, my quota works on the basis that it slows down when I reach my limit, so it doesn't cost me too much.

It's not too hard to deal with - I simply check how I'm going from time to time, and if I see I'm past where I should be, then I cut back a bit.  It's just a case of choosing the right quota for what you want to do.  I'm on youtube a bit, and normally download some music or games, and have no problems.  It helps that they mirror the Ubuntu repositories - unfortunately, they're not the official Australian mirror.

---

### Post by SharkSkinMan on 2009-01-29
> **wolfen69 said:**
> if downloading ubuntu cuts into your monthly quota, you can always request a free cd from canonical.

Not really the issue, I'm afraid.  My ISP has their own mirror of the repository, and if I download from there, it doesn't count towards my quota.  Even better, they also mirror the ISO images, so I can grab that and burn it to DVD with no problems.

My problem was that despite all this, the installer removed my ISP's repository from my sources.list, so that I first had to upgrade to everything that was on the DVD, then restore my sources.list, and run a second upgrade process in Synaptic to upgrade everything else.

I assume I would've had exactly the same problem if I'd requested a DVD from Canonical - or are those updated after the initial release?

---

### Post by solwic on 2009-01-29
> **SharkSkinMan said:**
> 
I assume I would've had exactly the same problem if I'd requested a DVD from Canonical - or are those updated after the initial release?

The CD I ordered from Canonical was full of errors; wouldn't even pass the pre-install error check.  I wound up burning my own copy.  

May just have been a bad disk, or something to do with my hardware (though I don't see how; all other disks I use work), but I wouldn't base anything important on that disk.  :P

---

### Post by wolfen69 on 2009-01-29
> **SharkSkinMan said:**
> Not really the issue, I'm afraid.  My ISP has their own mirror of the repository, and if I download from there, it doesn't count towards my quota.  Even better, they also mirror the ISO images, so I can grab that and burn it to DVD with no problems.

My problem was that despite all this, the installer removed my ISP's repository from my sources.list, so that I first had to upgrade to everything that was on the DVD, then restore my sources.list, and run a second upgrade process in Synaptic to upgrade everything else.

I assume I would've had exactly the same problem if I'd requested a DVD from Canonical - or are those updated after the initial release?

sounds like a clean install would have been easier. hope you got it sorted.

---

