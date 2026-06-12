---
title: "Combine Ndiswrapper into the resttricted driver manager (easy wifi)"
date: 2007-10-18
forum: Ubuntu Brainstorm
---

### Post by climatewarrior on 2007-10-18
I don't know if this is just impossible or something. Im not a Linux expert. But here it goes.


Well I was thinking that it would be cool that for wireless cards that don't have any free or open source drivers available that the restricted driver manager took care of everything, just like with the broadcom ones. I have known of people that were willing to switch but were scared away by wireless issues. It would also be great if the restricted driver manager fetched the wifi drivers it needs from your windows partition instead of the internet because some people don't have any internet access except wifi. And if their wireless card doesn't work well they obviously wont be able to fetch them online.

Bye! Just an idea i wanted to share.

---

### Post by Zdravko on 2007-10-19
Nice idea. Thanks!

---

### Post by Prometheum on 2007-10-19
Great idea. Most of the people I've convinced to switch have been laptop users and unfortunately, broadcom is prevalent. This would make switching a lot easier and would just be a good feature.

---

### Post by Zdravko on 2007-10-19
Yes. I am a laptop user!

---

### Post by Next.Step on 2007-10-20
+1

---

### Post by teasum on 2007-10-23
This is a fantastic idea.  I like the way the restricted drivers are now handled in Ubuntu, and ndiswrapper for wireless cards would be al ogical addition.  I just tried to install Ubuntu on a friend's laptop, and I couldn't get his wireless to work.  If this option came up as seamlessly as the restricted drivers, there's a good chance he would have stuck with Ubuntu.

---

### Post by Lozz on 2007-10-23
I like it. I like it a lot. If ubuntu could make WiFi that easy then it'd really stand out from the crowd as far as Linux distros go.

---

### Post by whitewizardcoder on 2007-10-23
+1

Gutsy installed fwcutter and the broadcom firmware on my laptop using the restricted manager, but this driver has issues (11mbps max and you need to be really close to the access point).  I immediately replaced it with ndiswrapper.  It would be good if there was a choice between the two in this case.

---

### Post by Pierre Lourens on 2007-10-23
Awesome idea.  Theoretically, I'd hope that the restricted drivers manager managed everything out of the box -- wifi included, as you say -- for the new user who has no idea what they are doing.  The less the end user has to worry about fiddling, the better for Ubuntu as a whole.

---

### Post by jethro10 on 2007-10-24
I've been using ubuntu for 2 years, and my wifi card now appears, but dont work.

So i go for this as well, being a relatively experienced user who is still stuck (i've tried NDIS wrapper manually and failed)

J

---

### Post by amlucent23 on 2007-10-24
+1 (For me)
+1 (For my wife who cant get her wifi to work with ubuntu)
+2 (For each of my 2 dogs.. because they are always complaining about linux wifi support)

---

### Post by AegisTalons on 2007-10-24
Now that would be nice. And with my card it could actually be a better install than in Windows if Ubuntu gets it off the ground. I have a USR5410, and to install in Windows, you need to install the drivers and application first and then reboot with the card inserted then. Else everything breaks. How lovely. I'm still having issues with it taking sometime before I can get on the Internet in Windows also.

---

### Post by LodeRunner on 2007-10-24
+1

Driver issues are by far the biggest disadvantage one sees when switching to Linux--in my experience, the ONLY disadvantage.

---

### Post by Nirro on 2007-10-25
The problem is that the restricted drivers manager will need to download the appropriate Windows driver from the internet, you cannot integrate all Windows drivers because there are houndreds of them, and there might be legal problems. Also it might be impossible to download from the internet if the only interface you have is wireless.

Most of the people have the original disk of drivers from the Wifi card manufacturer. maybe the restricted drivers manager should be able to search for appropriate driver in the disk, (something like "add new hardware" in Windows).

---

### Post by Nirro on 2007-10-25
Or it's better if Canonical will standardize a format that packages the windows drivers in a special package that the Restricted driver manager will be able to identify, read and install,
and convinces all wifi cards manufactures to add it to their download section in their websites and also add it to their driver disk that comes with the hardware.

---

### Post by mysticmatrix on 2007-10-25
Well I would hate to break it to all of you that ability of Linux to use Windows device driver should be taken more as awe inspiring than a regular feature. Anyone would agree that it's better to have original drivers, native to system, than to use hacks/emulation layers to make them work.

Then comes the point of usability. Perhaps ndiswrapper is good, but it still provides incentive to Linux hating companies not to provide True Linux drivers. 

DISCLAIMER: I decided not to by a laptop with unsupported wireless, and know how much pain it is to use any unsupported hardware on any OS, but sincerely don't think workarounds should be integrated in main system.

---

