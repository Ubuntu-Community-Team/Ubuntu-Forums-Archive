---
title: "Flash playback and Firefox tabs"
date: 2009-08-27
forum: System76 Support
---

### Post by bakelitedoorbell on 2009-08-27
My Serval (Serp5) running up-to-date Ubuntu 9.04 has an annoying problem with Flash in Firefox, and I'm wondering if other people have this or know of an adjustment I can make to fix it.

It happens when I have multiple tabs open in Firefox and there is a flash video or audio stream playing.  If I switch to another tab while it's playing, sometimes the flash video stops and turns into a blank white rectangle.  Reloading the page doesn't restart it.  Flash becomes non-functional in all tabs after this happens.  To fix it I have to close Firefox, open it again, go back to the web page and then start the video playing again from the beginning.

If I watch a video without clicking on anything then it will play to the end.  The problem only happens when I open a new tab or switch to another tab.

Any ideas?  If I have to reinstall the flash player, how would I do that?

Thanks
Robert

---

### Post by Ed.Corcoran on 2009-08-27
This is also happening to me.

---

### Post by thomasaaron on 2009-08-28
This is probably caused by 32-bit flash segfaulting. It's wrapped with nsplugin wrapper and still has some bugs in it.

The fix is to install the 64-bit flash plugin. However, my procedure for this doesn't seem to be working anymore. I'm researching it to see what I can figure out.

---

### Post by gila_monster on 2009-08-28
> **thomasaaron said:**
> This is probably caused by 32-bit flash segfaulting. It's wrapped with nsplugin wrapper and still has some bugs in it.

The fix is to install the 64-bit flash plugin. However, my procedure for this doesn't seem to be working anymore. I'm researching it to see what I can figure out.

In what way? What version of 64-bit Flash is it downloading? 22 seemed to work the best for me. Sometimes their earlier versions were less buggy than the shiny, new ones.

---

### Post by thomasaaron on 2009-08-28
The current version is 10.0.32.18. Youtube keeps telling me I'm using an older version. I'll try lifting the older version from another machine -- if I can find one here in the shop running it.

---

### Post by gila_monster on 2009-08-28
> **thomasaaron said:**
> The current version is 10.0.32.18. Youtube keeps telling me I'm using an older version. I'll try lifting the older version from another machine -- if I can find one here in the shop running it.

I can send you the .so I'm using if you need it by email.

---

### Post by bakelitedoorbell on 2009-08-29
I think the Flash plugin was installed with the "Ubuntu restricted extras" package.

Synaptic tells me the version on my system is 10.0.32.18

Hope that helps,
Robert

---

### Post by thomasaaron on 2009-08-31
Thanks, gila_monster.

That would be great.

bakelitedoorbell, the version installed by u-r-e is a nspluggin-wrapped 32-bit plugin. We're trying to get the 64-bit version going.

---

### Post by jtimbr7546 on 2009-09-02
Actually I just download the 64-bit plugin from Adobe's website and then copy the .SO into the firefox plugins folder. Rebooted (for good measure) and it seemed to be happy.

---

### Post by thomasaaron on 2009-09-03
You may still be running on the nspluginwrapper / 32-bit version. To test...

1. Shut down Firefox

2. Run the following commands from a terminal...

sudo apt-get remove flashplugin-*
sudo apt-get remove nspluginwrapper

3. Restart Firefox

If flash works, you're running on the 64-bit version.

If it doesn't, you can re-install the 32-bit version by running...

sudo apt-get install flashplugin-installer

Then restart firefox.

---

### Post by bakelitedoorbell on 2009-09-05
Okay, I did 1 2 3 as you suggested.  Flash plugin was no longer installed.

Then I did the apt-get install command, and it's working.  I have been trying for a while to trigger the blank screen with multiple tabs and a few streaming videos, and have not been able to get the error.  So maybe that wrapper was the problem?

Anyway, many thanks as it seems to be working fine now.

Robert

---

