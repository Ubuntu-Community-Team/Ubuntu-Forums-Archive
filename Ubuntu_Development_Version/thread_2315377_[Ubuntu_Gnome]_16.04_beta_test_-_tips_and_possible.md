---
title: "[Ubuntu Gnome] 16.04 beta test - tips and possible bugs"
date: 2016-02-28
forum: Ubuntu Development Version
---

### Post by stupendos on 2016-02-28
I'm not familiar with launchpad, so I would like to report here some possible bugs.

1. I didn't find the way to close "Scree Reader"
2. Both Rhythmbox and Videos are unable to open the folders in my NAS.
3. ImageMagick does not start (not a great loss...).

Ubuntu Gnome is sleek, but i feel really uncomfortable with most part of the application provided, I love menus and options to open, configure and so on, instead those applications were arranged for the maximum simplicity of use.
I do not think that is the best choice, my guess is that most part of Linux user do not like application as simple (or "silly") as the apps for phones...

---

### Post by howefield on 2016-02-28
Reporting bugs here is fine if that is what you want to do, however nothing will be done about them.

If you really want to run the development release, it is almost beholden on you to report bugs otherwise you can have no complaint.

---

### Post by Frogs Hair on 2016-02-28
Here's a guide to help with reporting. [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by kansasnoob on 2016-02-28
> I love menus

Then maybe you'd prefer GNOME Flashback:

[http://ubuntuforums.org/showthread.php?t=2302432](http://ubuntuforums.org/showthread.php?t=2302432)

The flashback w/metacity session is used by Edubuntu for its LTSP installs so it's officially supported for the full 5 years of the LTS cycles. You can learn a bit about the history of the flashback session by following the links here:

[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)

---

### Post by grahammechanical on 2016-02-28
> I do not think that is the best choice, my guess is that most part of  Linux user do not like application as simple (or "silly") as the apps  for phones...

Be careful what you say. Ubuntu Gnome is based on Gnome 3 shell which Ubuntu does not use. As far as I know Gnome.org is not working towards Gnome apps for phones. If that comment is a reference to Canonical producing a Ubuntu phone OS, then you are barking up the wrong tree and you are doing it twice.

1) Criticism of the UI in Ubuntu Gnome should be directed towards Gnome.org
2) Canonical's idea of convergence is for phone style apps on a phone device, tablet style apps on a tablet device and desktop style apps on a laptop and desktop. App developers for the Ubuntu for devices OS are required to design the apps so that they scale and add functions according to the device that they are running on.

You will find that Gnome.org has been making all kinds of changes to its standard Gnome apps for some time. And there are users who do not like the changes. Both Ubuntu and Ubuntu Gnome make use of many Gnome apps and there is not much that the Ubuntu Gnome & Ubuntu devs can do about the changes.

Regards.

---

### Post by stupendos on 2016-02-28
Hallo,
first let me clarify that I just wanted to write my quiet opinion, and not in any case a criticism to Ubuntu. The UI of Ubuntu Gnome is really nice and I'm keeping using it. Only a few applications seems to me too simplified (e.g. Rhythmbox compared to VLC), with gaunt menus - no complaints, my opinion only.

Unfortunately I am not able to develop anything, I can not even check the bugs, so the purpose of this post was to put a message in the bottle, just in case. I did not mean to digress.

---

### Post by $yl9pAR%t on 2016-02-28
There is a problem in Nautilus, when I click twice on the button "Location options" (upper right corner), almost everything on the desktop is getting unresponsive for 10-20 seconds. It happens both on Ubuntu GNOME 16.04 and Ubuntu 16.04 gnome-session-flashback w/Metacity.

---

### Post by sgage on 2016-02-28
> **mefisto888 said:**
> There is a problem in Nautilus, when I click twice on the button "Location options" (upper right corner), almost everything on the desktop is getting unresponsive for 10-20 seconds. It happens both on Ubuntu GNOME 16.04 and Ubuntu 16.04 gnome-session-flashback w/Metacity.

In my installation, it's called 'Enter Location' under the hamburger menu, and a single click suffices to make Nautilus unresponsive for 10-20 seconds. Where are you seeing 'location options'?

[Edit: it looks like gvfsd-smb-browse is pretty much pegging my CPU...]

---

### Post by $yl9pAR%t on 2016-02-28
From the right the next button after "close" button. You are right about single click, but after single click I can choose quit or close (I do not remember now) from menu and in this case no freeze happens.

---

### Post by sgage on 2016-02-28
> **mefisto888 said:**
> From the right the next button after "close" button. You are right about single click, but after single click I can choose quit or close (I do not remember now) from menu and in this case no freeze happens.

I don't seem to be seeing what you are seeing. What version of Nautilus are you running?

---

### Post by $yl9pAR%t on 2016-02-28
Nautilus 3.14.3. Clicking once on this "Location options" ("Enter location" in your case) gives me drop down menu. In this menu I can choose "close" and nothing bad happens, but choosing for example "show in terminal" and a few others makes desktop unresponsive for 10-20 seconds as I said before.

Ok, I have checked english version again and now I understand our misunderstandings. Your "hamburger" is my "Location option", hover over it and you will see.

---

### Post by sgage on 2016-02-29
> **mefisto888 said:**
> Nautilus 3.14.3. Clicking once on this "Location options" ("Enter location" in your case) gives me drop down menu. In this menu I can choose "close" and nothing bad happens, but choosing for example "show in terminal" and a few others makes desktop unresponsive for 10-20 seconds as I said before.

Ok, I have checked english version again and now I understand our misunderstandings. Your "hamburger" is my "Location option", hover over it and you will see.

Ah yes, I see 'Location option' if I hover over it. 

I'm seeing the same behavior as you are. If I click 'close', it closes. If I click anything else, the system goes unresponsive for 10 seconds or so. Though if I click "New Folder", after those unresponsive 10-20 seconds, it does create a new 'Untitled Folder'.

---

