---
title: "Problem updating wow, stuck in loop"
date: 2009-08-05
forum: Wine
---

### Post by Ameneon on 2009-08-05
I've been using wow in wine for a good while now and it's always worked near flawlessly, updates and all. Minor issue with launcher but running game from the wow.exe file has worked fine all along, for patches and otherwise.

Now with patch 3.2.0 I've done what I've done at any other time which is to download the patch files manually ahead of time (but on the same day), place them in the folder and then run the game. When prompted for update I let the game run the updater which then looks for the patch files, finds them in the downloaded location and installs them.

What happens is that the patch files are found by the downloader, checked and verified, and then - nothing. At this point it should normally launch the installer found in the patch folder but this doesn't happen at all. Logs don't show anything and if I try to launch the installer myself, it says that it's waiting for files to be closed (neither wow.exe, backgrounddownloader or launcher or any other wow related file is running), and nothing happens.

This happens even if I restart ubuntu and I while I've tried a few fixes suggested elsewhere (looking for the aforementioned open files, changing windows version in winecfg etc) I've yet to see any difference at all.

So, anybody experiencing or have experienced the same, or have any suggestions?

---

### Post by Ameneon on 2009-08-05
Should add that I copied the same patch files into the windows installation and there the update process worked flawlessly, so the problem likely lies elsewhere.

---

### Post by Celexi on 2009-08-06
> **Ameneon said:**
> Should add that I copied the same patch files into the windows installation and there the update process worked flawlessly, so the problem likely lies elsewhere.

copy the updated installation from windows to linux, wow installations are not system-specific and can be copied around :)

---

### Post by Ameneon on 2009-08-06
Yeap that's the way I went when I first installed it in Windows, copied from the linux install...just seemed odd that's all, but ty :)

---

