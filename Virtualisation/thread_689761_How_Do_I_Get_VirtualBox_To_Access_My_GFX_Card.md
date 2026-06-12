---
title: "How Do I Get VirtualBox To Access My GFX Card"
date: 2008-02-06
forum: Virtualisation
---

### Post by money2themax on 2008-02-06
I need to get VirtualBox to access my GFX card and USB ports btw my GFX card is fully supported by Linux its a Nvidia one built in to my MOBO

---

### Post by money2themax on 2008-02-06
Also I'm getting this problem too

---

### Post by Levander on 2008-02-06
Well, you've done no research whatsoever on your own, so I'm kind of thinking I should just let you suffer.  But, I just did this yesterday.  Here's the instructions I eventually ended up following:

[http://ubuntuforums.org/showpost.php?p=4074968&postcount=4](http://ubuntuforums.org/showpost.php?p=4074968&postcount=4)

I played around a lot with it, and I think those instructions are in the wrong order.  I think you have to do the second part first and the first part second.

The reason I think this is because at the end of the first part you run "sudo /etc/init.d/mountdevsusbfs start".  And, I believe this script uses the information that you've configured in 40-permissions.rules in the second part.

Also, for me there I was running an XP guest, and there was a 3rd part that's not listed in the instructions.  I had to run Windows Update inside the guest one time so that Microsoft would install some "system update component" (called something like this).  Then, when I plugged in my USB device, the driver for the device was auto-downloaded from the internet using that "system update component".

Also, there's a fourth part, make sure in the VirtualBox application, you create a filter forwhatever USB device you plug in that you want VirtualBox to capture for its guests.  It's not hard to do, you can probably figure it out from the VirtualBox UI.  Or, do some reasearch, maybe read the virtualbox user manual on how to create a USB filter.

---

