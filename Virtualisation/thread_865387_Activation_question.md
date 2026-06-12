---
title: "Activation question"
date: 2008-07-20
forum: Virtualisation
---

### Post by Lori700698 on 2008-07-20
I just got my virtualbox running and got windows XP all loaded up but I'm have an issue with the activation, the keys show up in the icon try and tell me I have 30 days to activate then I select them and the activation window pops up and says windows is already activated but I didn't enter the activation key code (which I do have)then it dissapears.  Next reboot, same thing happens again.  Can this be fixed, will it go away, will it freeze up in 30 days, is there a way to force it to give me the boxes to enter the code?  Anybody have a clue?  And I did install it twice to be sure it wasn't just a fluke install.

---

### Post by HotShotDJ on 2008-07-20
When you installed, did the installer ask for the product key at any time?  If not, it is possible that you are dealing with a manufacturer's volume license.  See [http://forums.virtualbox.org/viewtopic.php?t=3224](http://forums.virtualbox.org/viewtopic.php?t=3224) for more information regarding this problem.

---

### Post by Lori700698 on 2008-07-20
No, it never asked me for anything.  I looked at the link you gave me and I don't know how or where to get in to change the bios line.  Sorry I'm still pretty new at this.

---

### Post by HotShotDJ on 2008-07-20
> **Lori700698 said:**
> No, it never asked me for anything.  I looked at the link you gave me and I don't know how or where to get in to change the bios line.  Sorry I'm still pretty new at this.I fear you may not be able to correct the problem on you system as it requires the editing of source files and recompiling VirtualBox.  Unless you have experience working with C++ files and compiling source code, this may not be something you will want to attempt.  Its very frustrating that Microsoft, in concert with some P.C. vendors, created this problem for people.

---

### Post by Lori700698 on 2008-07-27
Update, you were right about the full version cd I was using, that was the problem, I used an XP ugrade CD I hade and the problem is now fixed.  I don't know enough about programming to mess with that solution, but I'm glad I found something else that worked.  I was wondering can I make a ghost immage of a currently running windows system?  The plan is to eventually move all of our computers to Ubuntu as long as the virtual box works (and it seems to be)I would like to make exact copies of their exisiting windows to use on the virtual box.

---

### Post by HotShotDJ on 2008-07-27
> **Lori700698 said:**
> I was wondering can I make a ghost immage of a currently running windows system?  The plan is to eventually move all of our computers to Ubuntu as long as the virtual box works (and it seems to be)I would like to make exact copies of their exisiting windows to use on the virtual box.Hmmmm.... I've never tried to do something like that... but I wonder what would happen if you used PartImage to make a backup image of your current Windows installations, and then restore those images in a VirtualBox VM??

I can't think of any reason why this WOULDN'T work....  I wish I had a system on which to test my hypothesis.

---

### Post by Lori700698 on 2008-07-27
I do, and I want to try it! where can I get some good directions on how to make the back up?

---

### Post by HotShotDJ on 2008-07-27
> **Lori700698 said:**
> I do, and I want to try it! where can I get some good directions on how to make the back up?I found the following tutorial: [http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522)

It includes both backup and restore instructions.  Good luck with this!  Let me know if it works.

---

