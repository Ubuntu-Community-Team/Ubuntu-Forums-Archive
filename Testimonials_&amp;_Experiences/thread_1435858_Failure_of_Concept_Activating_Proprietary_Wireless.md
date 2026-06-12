---
title: "Failure of Concept: Activating Proprietary Wireless Drivers"
date: 2010-03-22
forum: Testimonials &amp; Experiences
---

### Post by pihbar on 2010-03-22
Due to a combination of Ubuntu's unyielding commitment to open source software and a complicated and suppressive legal situation, installing third-party hosted, proprietary drivers can be a huge hassle.

Most of the time, a user can simply go to System > Administration > Hardware Drivers, select the appropriate driver there, click Enable and enjoy the fully functional non-GPL drivers on his/her computer. However, activation of said drivers may require a download from the developer's website, and this is where things get tricky. If you are enabling proprietary network card drivers through this method and don't have any alternate internet access, you're in trouble. 

In this case, the drivers simply fail to be enabled, there is no announcement about why they haven't been enabled, and finally, no instructions on how to do it manually. This should *really* be taken care of, because it is an embarrassing oversight casting a dark shadow on the quest for a completely open operating system and frustrating many users of Ubuntu. Don't believe me? Search these forums for BCM43xx or Broadcom STA driver, and you'll see.

---

### Post by aysiu on 2010-03-22
Yeah, I've already filed a bug on this:
[Lucid Alpha 3: hardware drivers can't fetch STA drivers for Broadcom](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/534824)

---

### Post by pihbar on 2010-03-22
Ah, but the problem isn't so much a bug as much as a limitation: you may have to use -blank- in order to get -blank- to work. There simply has to be a new approach.

---

### Post by aysiu on 2010-03-22
> **pihbar said:**
> Ah, but the problem isn't so much a bug as much as a limitation: you may have to use -blank- in order to get -blank- to work. There simply has to be a new approach.
I disagree. It's definitely a bug.

If they can't fetch it, instead of getting some cryptic message about how some repository can't be reached, it should let you know you need a wired connection or it should give you instructions for how to get and how to install the appropriate packages from another computer.

Really, though, the real solution should be to include the drivers on the disk. They don't take up that much space, and they are usually necessary to get internet working.

---

### Post by PRC09 on 2010-03-22
I think that the biggest problem with people installing Ubuntu for the first time is lack of reading the documentation for the install.In the case of the Broadcom drivers it does list the info on how to install them with or without internet right in the Ubuntu documentation and I have done it both ways and it works fine for all the Broadcom drivers that I have used.


[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by aysiu on 2010-03-22
> **PRC09 said:**
> I think that the biggest problem with people installing Ubuntu for the first time is lack of reading the documentation for the install.In the case of the Broadcom drivers it does list the info on how to install them with or without internet right in the Ubuntu documentation and I have done it both ways and it works fine for all the Broadcom drivers that I have used.


[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
I don't understand.

So someone, before installing Ubuntu, is supposed to know 1) she has a Broadcom wireless card, 2) Broadcom won't work with Ubuntu out of the box, and 3) she should look up on the community site documentation how to do Broadcom with Ubuntu?

I don't think so. The whole point of *jockey-gtk* is to make it easy for people to install proprietary drivers.

---

### Post by PRC09 on 2010-03-22
I dont know about anyone else but to just pop a cd in the machine without knowing anything about said machine and expecting everything to magically work is a bit of a stretch even for Ubuntu.If you are referring to the fact that it doesnt tell you when it doesnt work then thats different.Even so you should at least know what hardware is in your machine.....

---

### Post by uRock on 2010-03-22
> **PRC09 said:**
> I dont know about anyone else but to just pop a cd in the machine without knowing anything about said machine and expecting everything to magically work is a bit of a stretch even for Ubuntu.If you are referring to the fact that it doesnt tell you when it doesnt work then thats different.Even so you should at least know what hardware is in your machine.....

People do that with install disks all the time. I have tried to install stuff on Windows just to find there is no support for the hardware with the version of Windows being used.(HP ScanJet 2200 vs Windows 7)

I have had 2 Windows OSes and 6 different distros of Linux on my system and working and until today I did not know exactly which version of nVidia was on my motherboard. Every OS except Debian automatically pointed me in the right direction for a driver. And I would expect that from any user friendly OS I install.

---

### Post by aysiu on 2010-03-22
> **PRC09 said:**
> I dont know about anyone else but to just pop a cd in the machine without knowing anything about said machine and expecting everything to magically work is a bit of a stretch even for Ubuntu. Actually, I think that's what a lot of people expect. I'd highly recommend you visit the Ubuntu Testimonials and Experiences subforum some time.

Or maybe take a look at some arguments in Recurring Discussions in which Linux evangelists continually repeat that Linux supports more hardware than Windows does (technically true but extremely misleading to most computer users who do not want to use an ARM or SPARC processor for their main laptop or desktop... they just want their Lexmark printer or ATI graphics card to work).

---

### Post by TBABill on 2010-03-22
Another concept could be to have a LiveCD (or LiveUSB), but to also have a driver disk if space is an issue with the distros filling up the space on a CD. That way, after install you would have another CD dedicated to carrying drivers for those instances where you need a proprietary driver but cannot access the Internet to fetch them.

I am imagining a dual download when I describe this. Download the .iso and use it for live or install, but download the driver files that reside on a separate CD, accessible by Ubuntu after install to pull in those proprietary drivers. Make that an option during the install....(e.g., "Allow Ubuntu to install proprietary drivers from a CD after installation completes?").

If you downloaded the latest drivers files when you downloaded your Ubuntu iso, you'd have the latest available drivers at install. I just had this issue with my Broadcom wireless, and saw several posts today with the same problem. For those with more than 1 desktop and one of them far from the router, plugging into the router is not feasible (or easy). This would help eliminate this issue right up front.

Thoughts?

---

### Post by aysiu on 2010-03-22
> **TBABill said:**
> 
Thoughts? Well, it's better than some unhelpful error message about being unable to fetch the wireless driver because you aren't connected to the internet.

---

### Post by TBABill on 2010-03-22
True. Only problem is most people won't want to have to use 2 CD's for one install.

---

### Post by pihbar on 2010-03-22
At the very least, a clear explanation of the problem should stay on the screen: "You need to download proprietary software from a third-party website. We cannot ship this software with Ubuntu because of legal reasons. Please find alternate internet access or obtain the software manually at -link to site-."

A bug means something unexpected happened. In this case, the application's behavior was expected -- but, simply, bad. Anyway, hope to see improvements. They're happening.

---

### Post by uRock on 2010-03-22
Nope, it is a [bug]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/534824").

---

### Post by donovan1983 on 2010-03-23
> **aysiu said:**
> I disagree. It's definitely a bug.

If they can't fetch it, instead of getting some cryptic message about how some repository can't be reached, it should let you know you need a wired connection or it should give you instructions for how to get and how to install the appropriate packages from another computer.

Really, though, the real solution should be to include the drivers on the disk. They don't take up that much space, and they are usually necessary to get internet working.

I have to agree that this is a bug. I knew the Broadcom drivers weren't included on the CD so I had to download them from Broadcom and put them on a flash drive. Just so I could install them, connect to the internet, and have Ubuntu download its own version of the driver! Seems a little absurd. I could be wrong, but I could have sworn that before the Atheros drivers were open sourced that Ubuntu would still load them if needed on the live CD and just let you know that restricted drivers were in use. Given how common Broadcom cards are and how essential internet connectivity is, there's no reason not to include the driver.

---

### Post by 3rdalbum on 2010-03-23
If Jockey's error message is unhelpful, then it's a bug.

The solution is to make the error message helpful:

"The selected driver could not be downloaded. Please check your internet connection and that you are not behind a proxy. If necessarily, you should use a supported mobile broadband device, or plug your computer into a broadband router, in order to obtain an internet connection."

---

### Post by mastablasta on 2010-03-23
> **TBABill said:**
> True. Only problem is most people won't want to have to use 2 CD's for one install.
 ¸
 
There is also an Ubuntu LiveDVD. What does it do in this case? i have it but i still used CD to install.

---

### Post by TBABill on 2010-03-23
The driver for my Broadcom was on the LiveCD. The problem is that most users do not know how, nor is it made very evident, how to add that CD to the repositories list so they can grab the driver off the CD after installing the OS. Otherwise they have no means other than plugging into their router to download that driver from the repositories. It's not extremely difficult, but if you are new to the OS and looking forward to getting up and running, this is a step that could prevent most new users from enabling wireless if they are unable to hard-wire to a connection until the first update.
 
I don't think I'd call it a bug because the system does work (allows you to get the driver), but HOW you get that driver is so hidden that I'd bet someone on their first Ubuntu install would never figure it out without help. And they could be in a position where they wiped a hard drive instead of partitioning correctly, leaving them without an easy way to get online to get answers via the forums.
 
Probably worth submitting as an improvement idea for making installs more simple.

---

### Post by armandh on 2010-03-23
I define a software bug as code that needs to be fixed
no amount of code fixing will solve this problem
a problem that should be obvious when checking out hardware compatability with the live disk.

my wife's lap top was trathered to a lan until the closed BCM-4311 wifi drivers became available.

for those who install ubuntu on to hardware with such a lan problem a usb nic might be handy.

but since a nic does not have the problem of possible adverse control of RF emitters, BCM should help out here, without the reservations they had on the wifi.

---

### Post by uRock on 2010-03-23
> **TBABill said:**
> True. Only problem is most people won't want to have to use 2 CD's for one install.

They threw out Gimp from the LiveCD, so there may be room for a few things.

---

