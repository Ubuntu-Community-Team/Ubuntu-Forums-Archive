---
title: "Some Usability Issues of Ubuntu 8.04.1--Updated Regularly"
date: 2008-12-03
forum: Testimonials &amp; Experiences
---

### Post by Zahidul_Alam on 2008-12-03
Hello All,
I start this thread to get your feedback on the following usability issues that i have find during my usability testing on Ubunut 8.04.1.


**UsabilityTestCase-001**

**Name:** Mixed Content CD's are only mounted as Audio CD.

**Use cases:** Insert a CD which contain both audio file (in .mp3, .wmv or any other audio format) and data file (some text file or some pictures); now insert this to your CDROM. Observe what happen? Does Ubuntu consider as an audio CD by default?

**Problem:** If a CD contains both audio and data then Ubuntu auto mounted it as an audio CD, it doesn’t consider the data part as default.

**UsabilityTestCase-002**

**Name:** Playing music files with Rhythmbox. 

**Use Case:** Open the Rhythmbox and select some .mp3 files to play on rhythmbox. Does rhythmbox play those files properly?

**Problem:** Though rhythmbox is the default multimedia application for Ubuntu 8.04 but it cannot play .mp3 format files without installing the appropriate codecs istalled. But why Ubuntu developer team has not install the proper codecs on their default application for the most common music files that people should use.

**UsabilityTestCase-003**
**Name:** Switching external monitors in laptops.

**Use Case:** Attach an external monitor with your laptop and turn off your laptop’s LCD screen and try to turn on your external monitor only.

**Problem:** If an external monitor is attached with the laptop and if user wants to activate one monitor at a time, that process is not user friendly at all. For example I tested it in Toshiba laptop which is single booting into Ubuntu 8.04. I attached an external monitor with the laptop. The laptop BIOS has 2 options”Auto select” and “Simultaneous”. When option 1 is selected it should turn off the laptop’s LCD monitor when an external monitor is detected and when option 2 is selected both external and laptop’s screen are activated. Now when I boot up the laptop with selected the option 1, first the external monitor is ON and the laptops screen is off but when the login GUI appears the LCD screen of the laptop is on automatically even if the option “Auto select” is selected.

**UsabilityTestCase-004**
**Name:** Using the application” Tracker”.

**Use Case:** In Ubuntu’s application menu choose the application “Tracker” and try to search with that something in your desktop.
Problem:  If we say in theoretically Tracker is an indexing system for text files enabling users to perform fast-full text searching. But in practical it is really different issue. In my testing I find nothing searching with “Tracker” and another thing I want to mention that for the new Ubuntu/Linux users there is no hints about how to use, why to use the “Tracker” application. One new user only search to Google to know detail about “Tracker”. So there should be a help button or some guideline should be provided so that novice user could get a proper idea about Tracker. The following link will provide some others opinion about “Trcaker”
[http://ubuntuforums.org/showthread.php?t=758180](http://ubuntuforums.org/showthread.php?t=758180)

**UsabilityTestCase-005**
**Name:** Problem with the “NetworkManager”.
**Problem:** “NetworkManager” is unable to install and connect to wireless networks in my testing. I have tried different laptops like HP Pavilion dv6000, ThinkPad X61s.

**UsabilityTestCase-006**
**Name:** Problem with “Totem”, Ubuntu’s default multimedia application for playing video files.
**Problem:** When any DVD is inserted and it opens with the default player “Totem” it only shows the first item on the menu, but the other items are absent from the menu. A user has to manually do “Play Disc” option to run the DVD menu.
Bug Report:  Already reported as a bug. Bug # 293508 [https://bugs.launchpad.net/bugs/293508](https://bugs.launchpad.net/bugs/293508)


More Test Cases updated regularly....

---

### Post by kjb34 on 2008-12-03
[QUOTE=Zahidul_Alam;6300280]Hello All,

**UsabilityTestCase-002**

**Name:** Playing music files with Rhythmbox. 

**Use Case:** Open the Rhythmbox and select some .mp3 files to play on rhythmbox. Does rhythmbox play those files properly?

**Problem:** Though rhythmbox is the default multimedia application for Ubuntu 8.04 but it cannot play .mp3 format files without installing the appropriate codecs istalled. But why Ubuntu developer team has not install the proper codecs on their default application for the most common music files that people should use.

They don't include the codecs for legal reasons.

---

### Post by Zahidul_Alam on 2008-12-05
> **kjb34 said:**
> [QUOTE=Zahidul_Alam;6300280]Hello All,

**UsabilityTestCase-002**

**Name:** Playing music files with Rhythmbox. 

**Use Case:** Open the Rhythmbox and select some .mp3 files to play on rhythmbox. Does rhythmbox play those files properly?

**Problem:** Though rhythmbox is the default multimedia application for Ubuntu 8.04 but it cannot play .mp3 format files without installing the appropriate codecs istalled. But why Ubuntu developer team has not install the proper codecs on their default application for the most common music files that people should use.

They don't include the codecs for legal reasons.

Thanks for your reply.Can you write in details about those reasons.

---

### Post by snowpine on 2008-12-05
> **Zahidul_Alam said:**
> [QUOTE=kjb34;6304208]

Thanks for your reply.Can you write in details about those reasons.

[http://en.wikipedia.org/wiki/Mp3#Licensing_and_patent_issues](http://en.wikipedia.org/wiki/Mp3#Licensing_and_patent_issues)

mp3 and other non-free codecs (like Flash) can be easily installed in Ubuntu with the following terminal command:

```
sudo apt-get install ubuntu-restricted-extras
```

Theoretically, this makes the end user, rather than Canonical, responsible for any legal issues that may arise in his/her home country.

---

### Post by 3rdalbum on 2008-12-06
> **Zahidul_Alam said:**
> **UsabilityTestCase-001**

**Name:** Mixed Content CD's are only mounted as Audio CD.

**Use cases:** Insert a CD which contain both audio file (in .mp3, .wmv or any other audio format) and data file (some text file or some pictures); now insert this to your CDROM. Observe what happen? Does Ubuntu consider as an audio CD by default?

**Problem:** If a CD contains both audio and data then Ubuntu auto mounted it as an audio CD, it doesn’t consider the data part as default.

I noticed this bug in Ubuntu 5.10 and forgot to report it. You could still get to the mountpoint, which was my workaround. Later on I stopped using the mixed-mode CDs. 

install the proper codecs on their default application for the most common music files that people should use.

> **UsabilityTestCase-004**
**Name:** Using the application” Tracker”.

**Use Case:** In Ubuntu’s application menu choose the application “Tracker” and try to search with that something in your desktop.
Problem:  If we say in theoretically Tracker is an indexing system for text files enabling users to perform fast-full text searching. But in practical it is really different issue. In my testing I find nothing searching with “Tracker”

What do people give up their CPU cycles for?

Content indexers don't work and because of this, nobody uses them. So nobody submits bug reports telling the developers that their programs don't work.

> **UsabilityTestCase-005**
**Name:** Problem with the “NetworkManager”.
**Problem:** “NetworkManager” is unable to install and connect to wireless networks in my testing. I have tried different laptops like HP Pavilion dv6000, ThinkPad X61s.

You need driver software in order to use wireless. If you find out what wireless chipset is inside those computers, then you can find what driver to install.

This is a usability issue, but you should be addressing this to wireless chipset manufacturers and/or the International Standards Organisation. If there was a standard wireless driver that would run any standards-compliant wireless card, this would make everybody's life easier no matter if they were on Windows, Mac, or Linux. Think how ridiculous it would be if you needed to install a drivers CD in order to use a USB flash drive, and you needed one driver for Sandisk, another driver for Toshiba, another driver for Kingston, etc.

Are you a professional usability tester?

---

### Post by Zahidul_Alam on 2008-12-06
Thanks **3rdalbum **for your reply. first of all i am not a professional usability tester i am doing these testing as a part of my Masters thesis. I only trying to finding out the week points regarding usability issues of Ubuntu 8..

Any Cooperation is appreciated.

---

