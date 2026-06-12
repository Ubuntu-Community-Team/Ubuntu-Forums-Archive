---
title: "Remastering Ubuntu (Editing Gnome)"
date: 2007-03-29
forum: Ubuntu Customization Guide
---

### Post by shuaibe on 2007-03-29
Hi

I have found a nice HowTo on Remastering Ubuntu [[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization) ]. But Iam still very unsure that how shall I customize the usplash, theme, menus,logos,etc such that installing from the new CD would have my customize enviroment. any suggestions ?

Thanks

---

### Post by MarlonNelson on 2007-04-25
I think you may find [Reconstructor]("http://reconstructor.aperantis.com/") useful.
[INDENT][http://reconstructor.aperantis.com/]("http://reconstructor.aperantis.com/")[/INDENT]
I tried it out and it worked pretty good.  It was a bit scary, though, running the product as root.

I'm trying to do something similar.  I want to create a custom version of Ubuntu that has a link to a video on the desktop.  So I used [Reconstructor]("http://reconstructor.aperantis.com/") to free up a bunch of space (the video is 100+MB) and then copied the video into /usr/share but I can't figure out how to add a link to it from the user's desktop, like the examples folder that normally shows up.

I've been searching & googling and doing a lot of investigation and learned a bit about the Ubuntu CD and other Live CDs.  But I haven't been able figure out how add the link.  There's probably some dpkg command I need to run or some package I need to tinker with.

Anyways, [Reconstructor]("http://reconstructor.aperantis.com/") is the best thing I've found so far.  It seems to automate the steps you find in the various HOWTOs (e.g. [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)).

I hope this helps. Good Luck... I'm gonna keep looking for my solution.

Update:
The Reconstructor [forums]("http://reconstructor.aperantis.com/index.php?option=com_joomlaboard&Itemid=44") have been very helpful.  I just need to add the link to /etc/skel.

---

