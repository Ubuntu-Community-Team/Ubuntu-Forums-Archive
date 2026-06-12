---
title: "Swapping Ctrl and Fn keys"
date: 2011-06-29
forum: System76 Support
---

### Post by jdnier on 2011-06-29
Hello,

I have a new Gazelle Professional laptop (June 2011) with 11.04 preinstalled and have several usability questions I'm hoping someone my have some suggestions for.

1. My last two Linux laptops were ThinkPads. I am finding it awkward adjusting to the position of the Fn and Ctrl keys, which are reversed compared to a ThinkPad. Is it possible to swap the behavior of the Ctrl and Fn keys? If so, what's the best circa-2011, Gnome-friendly solution to remapping the keys? I have read that ThinkPads now have an option in their BIOS to swap Fn & Ctrl but don't see anything similar in my Gazelle's BIOS. I should mention that I have gone back to using the Gnome 2 desktop rather than Unity.

The remaining questions are all touchpad-related.

2. I'm finding it difficult to type with my trackpad activated. Hovering my thumb/palm even 1-2mm above the trackpad often inadvertently moves the pointer -- even with the Disable touchpad while typing checked. Adjusting the mouse sensitivity seems to have no effect on the trackpad. Is there any way to get more control over the trackpad behavior? How do people deal with this?

3. I like using two-finger scroll with the trackpad but have found it works very erratically (poorly, actually) on my Gazelle trackpad. It seems to help only if I carefully align my two fingertips (the line formed between the two points touching the trackpad needs to be nearly parallel to the keyboard). Problem is, my index finger is quite a bit longer -- the line between the two points is more like a 45-degree angle, unless I rotate my whole had 45 degrees clockwise to compensate. I've never run into this kind of fussiness with a trackpad before (no problems on my large Mac trackpad or my two ThinkPads). Is there any way to make this trackpad behave better? Alternate driver? Magic conf incantations?

4. Shouldn't I be able to tap-tap-drag the touchpad to move windows/files/scroll bars around? This just doesn't work consistently and I often, in exasperation, resort to using the trackpad buttons. The issue seems to be that the drag fails to work if the second tap happens in the same exact spot as the first tap. If I tap-tap in a sort of a glancing/swiping action so the taps are slightly offset, it works -- but even then maybe only 75% of the time, I'd estimate. Sorry to be complaining but every aspect of this trackpad seems really awkward. You just shouldn't have to think about it so hard. ;)

Finally, for future models, I'd like to suggest that a Linux laptop without a middle mouse button is just a bad idea (i.e., having to emulate middle-click by clicking left and right trackpad buttons simultaneously is going to feel alien to many users).

Thanks for any suggestions,

--David

---

### Post by jdnier on 2011-06-29
Quick followup:

> 4. Shouldn't I be able to tap-tap-drag the touchpad to move 
> windows/files/scroll bars around?

I've realized now that the problem is happening when my index finger or thumb are hovering too close above the trackpad when I'm clicking -- not touching the trackpad, mind you, but hovering several millimeters above. If I tap carefully, with one finger outstretched, it works reliably.

If there's a way to reduce the sensitivity of the trackpad surface so you actually have to touch it to activate it, I think that would help a lot. Thanks again for any suggestions.

--David

---

### Post by isantop on 2011-06-30
> **jdnier said:**
> Hello,

I have a new Gazelle Professional laptop (June 2011) with 11.04 preinstalled and have several usability questions I'm hoping someone my have some suggestions for.

1. My last two Linux laptops were ThinkPads. I am finding it awkward adjusting to the position of the Fn and Ctrl keys, which are reversed compared to a ThinkPad. Is it possible to swap the behavior of the Ctrl and Fn keys? If so, what's the best circa-2011, Gnome-friendly solution to remapping the keys? I have read that ThinkPads now have an option in their BIOS to swap Fn & Ctrl but don't see anything similar in my Gazelle's BIOS. I should mention that I have gone back to using the Gnome 2 desktop rather than Unity.

The Fn key actually modifies the hardware directly, and causes a different signal to be sent from the keyboard. I'm afraid it isn't something that can be changed in software.

> The remaining questions are all touchpad-related.

2. I'm finding it difficult to type with my trackpad activated. Hovering my thumb/palm even 1-2mm above the trackpad often inadvertently moves the pointer -- even with the Disable touchpad while typing checked. Adjusting the mouse sensitivity seems to have no effect on the trackpad. Is there any way to get more control over the trackpad behavior? How do people deal with this?

There are a few driver issues with the trackpads in 11.04. Three- or higher finger multitouch for example. One of the features affected is the palm check function that handles the disable while typing feature. There are many driver improvements in 11.10, and we expect these features to work flawlessly then. Until then, many customers use the physical hardware switch (Fn+F1) to temporarily toggle it off and on.

> 3. I like using two-finger scroll with the trackpad but have found it works very erratically (poorly, actually) on my Gazelle trackpad. It seems to help only if I carefully align my two fingertips (the line formed between the two points touching the trackpad needs to be nearly parallel to the keyboard). Problem is, my index finger is quite a bit longer -- the line between the two points is more like a 45-degree angle, unless I rotate my whole had 45 degrees clockwise to compensate. I've never run into this kind of fussiness with a trackpad before (no problems on my large Mac trackpad or my two ThinkPads). Is there any way to make this trackpad behave better? Alternate driver? Magic conf incantations?

4. Shouldn't I be able to tap-tap-drag the touchpad to move windows/files/scroll bars around? This just doesn't work consistently and I often, in exasperation, resort to using the trackpad buttons. The issue seems to be that the drag fails to work if the second tap happens in the same exact spot as the first tap. If I tap-tap in a sort of a glancing/swiping action so the taps are slightly offset, it works -- but even then maybe only 75% of the time, I'd estimate. Sorry to be complaining but every aspect of this trackpad seems really awkward. You just shouldn't have to think about it so hard. ;)

I think these issues are related to trackpad sensitivity. Gnome 2 does not have a separate trackpad sensitivity setting like Gnome3 does, but you can turn the general cursor sensitivity down by going to System > Preferences > Mouse. 

> Finally, for future models, I'd like to suggest that a Linux laptop without a middle mouse button is just a bad idea (i.e., having to emulate middle-click by clicking left and right trackpad buttons simultaneously is going to feel alien to many users).

Actually, I think you're the first customer I've seen that's mentioned it. There just isn't enough demand on the consumer side of things, and it's becoming less prevalent in Linux, particularly in Ubuntu.

---

### Post by jdnier on 2011-07-01
> The Fn key actually modifies the hardware directly, and causes a 
> different signal to be sent from the keyboard. I'm afraid it 
> isn't something that can be changed in software.

I figured that would be the case but thanks for confirming.

> There are a few driver issues with the trackpads in 11.04. 
> Three- or higher finger multitouch for example. One of the 
> features affected is the palm check function that handles the
> disable while typing feature.

Yes, although it does seem to work briefly. When I hit a key, trackpad control returns about a second later.

> There are many driver improvements in 11.10, and we expect 
> these features to work flawlessly then. Until then, many 
> customers use the physical hardware switch (Fn+F1) to 
> temporarily toggle it off and on.

I hadn't noticed the Fn+F1 function before. That will help.

As for drivers, can you tell me what trackpad driver I'm looking for? Is it something I can track a development version for? or are you talking about System76 modifications?


> I think these issues are related to trackpad sensitivity. 
> Gnome 2 does not have a separate trackpad sensitivity setting
> like Gnome3 does, but you can turn the general cursor 
> sensitivity down by going to System > Preferences > Mouse.

Adjusting cursor sensitivity seems to have no effect on the trackpad. But thanks for mentioning the Gnome 3 sensitivity setting.


> Actually, I think you're the first customer I've seen that's
> mentioned it. There just isn't enough demand on the consumer
> side of things, and it's becoming less prevalent in Linux,
> particularly in Ubuntu.

Sorry, I would have guessed people like me -- people who have used Unix for years -- would be buying many of your laptops. But I guess you're probably not designing the hardware, like say Lenovo, and that the consumer market constrains what's available.

Thanks for all your comments; they're helpful and much appreciated!

--David

---

### Post by isantop on 2011-07-11
The name of the package the driver is in is xorg-input-synaptics. I couldn't tell you if there was a development version compatible with Natty, but checking the bleeding edge Xorg PPAs would be a good place to start.

[https://launchpad.net/~xorg-edgers](https://launchpad.net/~xorg-edgers)

---

### Post by zwirb on 2011-08-24
> **isantop said:**
> Actually, I think you're the first customer I've seen that's mentioned it. There just isn't enough demand on the consumer side of things, and it's becoming less prevalent in Linux, particularly in Ubuntu.

Make that two customers. I've just acquired a Gazelle, and I love it, but I also find the lack of a middle button on the trackpad frustrating.

Cheers!

---

