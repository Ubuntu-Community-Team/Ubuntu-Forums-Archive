---
title: "Best way to"
date: 2009-10-04
forum: The Cafe
---

### Post by fidelandche on 2009-10-04
With the upcoming release of Karmic, I have a couple of questions
 
[LIST=1]
[*]   Should I just install it from the update manager?
[*]Will this way keep all my files?
[*]Or should I download the iso image and do a clean install and completly remove Jaunty? once I have backed up all my information.
[/LIST]

---

### Post by FuturePilot on 2009-10-04
> **fidelandche said:**
> With the upcoming release of Karmic, I have a couple of questions
 
[LIST=1]
[*]   Should I just install it from the update manager?
[*]Will this way keep all my files?
[*]Or should I download the iso image and do a clean install and completly remove Jaunty? once I have backed up all my information.
[/LIST]

Upgrading will not delete any of your files. However you won't automatically get some of the changes coming in Karmic such as Ext4 and Grub2. You'll have to manually upgrade Grub and manually convert Ext3 to Ext4, however neither are required to run Karmic. Note that manually converting Ext3 to Ext4 won't give you the full benefits of Ext4. Usually I'm a big advocate of upgrades, but I think this release is an exception to that.

---

### Post by renkinjutsu on 2009-10-04
i would go with the clean install method.. As it gets rid of any cruft that would be left behind from updating..

also, canonical servers have been hit hard by Karmic, so downloading the ISO through bittorrent would be faster than upgrading through update manager anyway

---

### Post by nowin4me on 2009-10-04
> **fidelandche said:**
> 

3. Or should I download the iso image and do a clean install and completly remove Jaunty? once I have backed up all my information.
[/LIST]

3. You should dual boot with it so you have a stable system to go back to if you get into any troubles!

---

### Post by fidelandche on 2009-10-04
> **FuturePilot said:**
> Upgrading will not delete any of your files. However you won't automatically get some of the changes coming in Karmic such as Ext4 and Grub2. You'll have to manually upgrade Grub and manually convert Ext3 to Ext4, however neither are required to run Karmic. Note that manually converting Ext3 to Ext4 won't give you the full benefits of Ext4. Usually I'm a big advocate of upgrades, but I think this release is an exception to that.
 
 
Why is this release an exception?

---

### Post by FuturePilot on 2009-10-04
> **fidelandche said:**
> Why is this release an exception?

Because of the things I mentioned in my other post, and a few other low level changes (transition to upstart), I think starting fresh would be better in this case.

---

### Post by Jesus_Valdez on 2009-10-04
I already have EXT4 and GRUB2 on my Jaunty intall, What others things will I miss by upgrading instead of a fresh Install?

Thanks

---

### Post by FuturePilot on 2009-10-04
> **Jesus_Valdez said:**
> I already have EXT4 and GRUB2 on my Jaunty intall, What others things will I miss by upgrading instead of a fresh Install?

Thanks

AFAIK, those are the only two things. And since you already have them, upgrading should not be a problem.

---

### Post by Boom!!! on 2009-10-04
Install from CD/DVD media.

---

### Post by SunnyRabbiera on 2009-10-04
The upgrade to Kamic can be done with the update manager, and it will probably be a fairly smooth update

---

### Post by fidelandche on 2009-10-05
Will there be any problems with wifi? or getting flash to play? it is just that with Jaunty I did have these problems but they now no longer exist thats to this wonderful forum.

---

