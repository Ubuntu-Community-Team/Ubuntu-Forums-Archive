---
title: "Ubuntu automated installation"
date: 2008-07-14
forum: Ubuntu Brainstorm
---

### Post by sayakb on 2008-07-14
The idea is to include an option for totally automated ubuntu installation. The user can set his username and password after installation if he/she wishes to. The installer would autodetect keyboard layout, timezone (the computer should be plugged in to the internet, or this would be skipped), and attempt a guided partitioning. If guided partitioning isn't available, the user would be prompted for manual partitioning.

---

### Post by smartboyathome on 2008-07-14
I don't think this would be a good idea. It seems that it is getting rid of the Advanced linux user's choice in favor of helping begginning linux users. The internet timezone tool has been mentioned before, and it has been shown it can be wrong about the timezone someone is in.

Also, what do you mean "if guided partitioning isn't available"? You mean if there is more than one partition, then it asks the user to partition the hard drive for it? So that if there is only one partition, it just deletes it like Windows?

And as for setting the username and password after installation, I don't like that idea as it would require being root after you boot up, an extra step which would be more of an annoyance than help (when you reboot, you WANT to go into your operating system, not another step of install).

---

### Post by sayakb on 2008-07-14
Well, the option of normal installation will not be completely removed. Plus, detecting Keyboard layout and timezone can be done and the user can just confirm the detected settings or change them accordingly.

---

### Post by olskar on 2008-07-15
I honestly do not think it takes a lot of your time as it is now, very fast installation, and therefor I can't see the point of automated installation. If you need to install Ubuntu on several computers, there are easier solutions than to manually install each one of those.

---

### Post by songshu on 2008-07-17
The option is there already, its called preseeding.

all the questions asked by the installer (and more) can be answered by a simple file called preseed.cfg.

this file is on the cd and can be modified, i even put it on my server so i can change the config without have to remaster the cd.

its easy to make your own install cd manually as soon as you know how to, there are even tools to help you do it but these are less flexible.

to have it as a default option i'm not sure. (wasn't there something called OEM install on the alternative cd?)
to make it easier and/or better documented to do this, i think yes. it took me some time puzzling with the debian manuals to get it working on hardy.

---

