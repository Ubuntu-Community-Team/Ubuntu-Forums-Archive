---
title: "Having trouble installing Wine on Ubuntu 10.10"
date: 2010-12-14
forum: Wine
---

### Post by GreenBowlPacker_3 on 2010-12-14
Okay, so I tried searching this before posting this thread and I haven't been able to find anything that helps, so hopefully someone out there can help.

I'm using Ubuntu 10.10 and I want to install Wine.  When I go to the WineHQ website it has detailed instructions and I kinda feel like an idiot.  But here's the problem, when I go to System -> Admin -> there's no "Software Sources".

I also saw at the end of the page that you can add the ppa through the terminal so I tried that.  All I get is an error message saying the package does not exist.

I feel like I'm missing something simple here, I would really appreciate any help.

---

### Post by Tweak42 on 2010-12-14
In 10.10 the "Software Sources" is hidden.  You can unhide it in the System>Preferences>Main Menu utility; (check box in the Administration section).  Or you can find it by running in Synaptic under Settings>Repository

---

### Post by GreenBowlPacker_3 on 2010-12-14
> **Tweak42 said:**
> In 10.10 the "Software Sources" is hidden.  You can unhide it in the System>Preferences>Main Menu utility; (check box in the Administration section).  Or you can find it by running in Synaptic under Settings>Repository

So I just did this and it worked.  Thank you!  However, it didn't help.  While I was waiting on a reply I found the thread "read before posting about Wine installs", or something similar.  It turns out you can install Wine from the Ubuntu Software Center, I think it's the same Wine.  Well when I tried this my comp froze and now it says it's installed, but it's not, and I can't remove it.  Every time I click remove I get an error message.  Now nothing seems to work.

---

### Post by Tweak42 on 2010-12-15
> **GreenBowlPacker_3 said:**
> So I just did this and it worked.  Thank you!  However, it didn't help.  While I was waiting on a reply I found the thread "read before posting about Wine installs", or something similar.  It turns out you can install Wine from the Ubuntu Software Center, I think it's the same Wine.  Well when I tried this my comp froze and now it says it's installed, but it's not, and I can't remove it.  Every time I click remove I get an error message.  Now nothing seems to work.

What is the error and are you getting using Synaptic or USC?  You'll want to use Synaptic since it is the more power user app and you can do reinstall or complete removals.  If your apt database is corrupted (crashing during a install is bad) you'll probably need to do some command line stuff to repair it.

---

### Post by GreenBowlPacker_3 on 2010-12-15
> **Tweak42 said:**
> What is the error and are you getting using Synaptic or USC?  You'll want to use Synaptic since it is the more power user app and you can do reinstall or complete removals.  If your apt database is corrupted (crashing during a install is bad) you'll probably need to do some command line stuff to repair it.

This is what happens when i try to uninstall through the Ubuntu Software Center:

The installation or removal of a software package failed.
Details:

installArchives() failed: dpkg: error processing wine1.2 (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 wine1.2

Now I get similar messages if I try to install anything through the software center.  It's really frustrating.  Should I just back everything up and start over from scratch?  Or is there an easy fix.  I've been using Ubuntu for awhile now and I've never had a problem like this.

---

### Post by GreenBowlPacker_3 on 2010-12-15
My update manager popped up and after I updated the system Wine is installed and seems to work.  Thank you for your help, I really appreciate it!

---

### Post by YokoZar on 2010-12-15
My bad, forgot to update the instructions.

Software Sources is now accessed from Software Center

---

