---
title: "Upgrade to 7.10 . . . Howzitgoing?"
date: 2007-10-22
forum: Tennessee Team - US
---

### Post by klhoard on 2007-10-22
How has everyone's upgrade experience gone?  After several tries,my upgrade kept freezing at one point, so I did some checking on the forums.  Well, like several things Ubuntu so far; I switched a server here, another check box there, and BAM the upgrade proceeded as advertised.  22 minutes left. . . sweet!!  Off I go around the house doing laundry and keeping one eye on the computer screen and clicking on the occasional OK button.  About 3/4 of the way thru I realize that I didn't back up my system - OOOPS!!  Too late now, the upgrader is currently rearranging the intestines of my computer.  Gotta forge ahead. . 

Well, luckily everything worked out well, the reboot was successful and the machine is working perfectly.  Yeah, me!! (Disney Channel)  

I'm digging the Comp-Fusion screen.  I've finally found a use for the Windows keys on my computer. . . I've set them up to rotate the workspace cube!!

---

### Post by radovan01 on 2007-10-22
upgrade to 7.10 was successfull, even one day before official release :D

---

### Post by NonaWeisbaum on 2007-10-22
> **klhoard said:**
> 22 minutes left. . . sweet!!  


really? :confused:

---

### Post by matthewcraig on 2007-10-22
Download was at 20 kbps.  When it finished, the install program had a critical failure when it filled up /boot.  Fixed by expanding to 3x the space, but Ubuntu would no longer boot under any grub setting, as it stopped at a BusyBox prompt.  Feisty reinstalled from disk, then performed a Gutsy upgrade after ensuring /home was secure.  Gutsy upgrade finally worked.  Only problem after the upgrade was the xorg.conf in Gutsy.  I finally found the right settings in **displayconfig-gtk** (Screen and Graphics tool), by trial and error.  I had to select generic monitors and select a specific resolution for the monitors that didn't cause scrolling.  Compiz Fusion seems to now be unhappy on two monitors, but, at least, I see some bugs open on the issue.

I am happy with the direction Gutsy went in this newest release, but there are a few things that could have been improved.  Checking for sufficient space in /boot would have saved me a re-install, and better auto-detection in the new X configuration tool would have been great.  I will be helping to get these issues raised to the right people, once the excitement wanes from the big upgrade.

Many websites are recommending **envy**, **automatix**, and other unsupported methods of working around these problems.  I am concerned there will be many users who choose to follow these paths instead of patiently waiting for the Ubuntu team to find a supported solution.  It may have been better for those people to stay with Feisty, rather than introduce a slew of new problems for themselves and people in the #ubuntu support channels.

---

### Post by klhoard on 2007-10-25
> **NonaWeisbaum said:**
> really? :confused:
.
.
Couldn't take XP anymore on my laptop, so I took my 7.04 disk with me on a trip to install U.  Currently upgrading to 7.10 in the hotel room - 8 HOURS to go.  Ugh!!  Must be the DSL. . . didn't know how good I have it at home!!
.
.

---

