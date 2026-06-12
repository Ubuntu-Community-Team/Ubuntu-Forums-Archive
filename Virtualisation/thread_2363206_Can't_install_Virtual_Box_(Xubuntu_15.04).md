---
title: "Can't install Virtual Box? (Xubuntu 15.04)"
date: 2017-06-07
forum: Virtualisation
---

### Post by oliviavictoria on 2017-06-07
Hi! I've been going in circles trying to get this over with for the past hour.. though this might be an easy fix and I've been worrying over all this for nothing x')

Long story short, if I download VB straight from the Ubuntu Software Center, I get an older version. I didn't realize that until I saw I couldn't connect via USB and decided to go download the extension pack. Then realized, man I need to update, this is for the newest version and isn't compatible with mine. Though, when I go into file and into the settings I saw no option to update. This is version 4.3.36. So I go ahead and uninstall the older version and download 5.1.22 directly from VB's website (64 bit, 15.10). Here's my problem. I'm prompted with "Dependency is not satisefiable: libdevmapper1.02.1 (>=2:1.02.99)" What do I do from here? Should I just download the version 4.3.36 of the extension pack and call it a night?

Also, might this be because I'm running Xubuntu 15.04 and I'm trying to download something for 15.10?

Thank you so much for any and all help!

Info: 
Dell Latitude D830
Xubuntu 15.04


[RIGHT][/RIGHT]

---

### Post by howefield on 2017-06-07
Thread moved to the "*Virtualisation*" forum.

You may have a bigger problem that Virtualbox given that Xubuntu version 15.04 is end of life and no longer supported, is there any reason that you couldn't to a supported release ?

---

### Post by oliviavictoria on 2017-06-07
> **howefield said:**
> Thread moved to the "*Virtualisation*" forum.

You may have a bigger problem that Virtualbox given that Xubuntu version 15.04 is end of life and no longer supported, is there any reason that you couldn't to a supported release ?

Ah it's no longer supported? Is there any way I can upgrade to 15.10? 

I'm not too knowledgeable on Linux, so as my father passed away, I used the Xubuntu disks he had to do a sweep on my computer to regain administrative privileges. Though I hadn't known that 15.04 was obsolete?  I have another disk for 14.04 but it'd be such a pain to go ahead and wipe my computer out again :1
Thank you for your reply!

Edit: I used the command > [COLOR=#111111][FONT=Consolas]update-manager -d[/FONT][/COLOR] into my terminal to try and see if I could upgrade and I was prompted with > ** (update-manager:3041): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-CCntffjzZp: Connection refusedWARNING:root:can not import unity GI cannot import name Dbusmenu, introspection typelib not found

Although, a "Software Updater" window has popped up and is currently checking for updates.

---

### Post by howefield on 2017-06-07
> **oliviavictoria said:**
> Ah it's no longer supported? Is there any way I can upgrade to 15.10? 

I'm not too knowledgeable on Linux, so as my father passed away, I used the Xubuntu disks he had to do a sweep on my computer to regain administrative privileges. Though I hadn't known that 15.04 was obsolete?  I have another disk for 14.04 but it'd be such a pain to go ahead and wipe my computer out again :1
Thank you for your reply!

15.10 is also beyond end of life as is 14.04 if it is a Xubuntu disk that you have.

Realistically you would be looking at getting to 16.04 which is supported till April 2019 for Xubuntu and April 2021 for Ubuntu.

For info, April releases on the even years are Long Term Support releases, ie 14.04, 16.04 get 3 years support. That is for Xubuntu, straight Ubuntu gets 5 years of support.

The interim releases such as 15.04, 15.10, 16.10 and the current 17.04 get 9 months of support. Hope that makes some sort of sense.

So, getting back to your issue you could probably install the version that you already had and match the Extensions version to that but of course you are still running an unsupported operating system with all the risks that accompany it.

I believe that you could upgrade to 16.04 directly from 15.04 (it used to be the case that one had to upgrade through each and every release). I'm not completely sure about the current state of play on upgrades.

---

