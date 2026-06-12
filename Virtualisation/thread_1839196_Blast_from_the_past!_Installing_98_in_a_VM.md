---
title: "Blast from the past! Installing 98 in a VM?"
date: 2011-09-05
forum: Virtualisation
---

### Post by jfed on 2011-09-05
Hello. Was going through my old stuff and found tons of old cool computer games I used to play when I was younger, among them I also found a Windows 98 install disk, in the original factory packaging. So I have decided what must be done. I must install Windows 98 in a virtual machine. Although I have no idea at all how to do this, as Windows 98 is quite ancient. Here are the main questions I have:

I have absolutely no knowledge of running a virtual machine, how do I do it in general? Do I use some sort of program?

Will the fact that I'm trying to install such an old operating system cause any conflicts that a normal VM OS install wouldn't? If so, how do I mitigate them?

I have two computers available. One with 6gb of ram and a 3.4ghz processor, another with a 2.0ghz processor and 4bg of ram. The first computer, the most powerful, doesn't have a CD drive. So if I install it on this one, I'd need to mount the .iso some how, which I'm not sure if that will cause issues. The second computer I am not sure if it has two physical cores, I heard you need to physical cores not hyperthreaded to run a VM?

Will the lack of CD drive cause any problems? If so, how do I find out if my second computer has two physical cores or not?

Any answers to any of these questions would be appreciated, as well as any helpful links to guides. Thanks in advance!

---

### Post by haqking on 2011-09-05
> **jfed said:**
> Hello. Was going through my old stuff and found tons of old cool computer games I used to play when I was younger, among them I also found a Windows 98 install disk, in the original factory packaging. So I have decided what must be done. I must install Windows 98 in a virtual machine. Although I have no idea at all how to do this, as Windows 98 is quite ancient. Here are the main questions I have:

I have absolutely no knowledge of running a virtual machine, how do I do it in general? Do I use some sort of program?

Will the fact that I'm trying to install such an old operating system cause any conflicts that a normal VM OS install wouldn't? If so, how do I mitigate them?

I have two computers available. One with 6gb of ram and a 3.4ghz processor, another with a 2.0ghz processor and 4bg of ram. The first computer, the most powerful, doesn't have a CD drive. So if I install it on this one, I'd need to mount the .iso some how, which I'm not sure if that will cause issues. The second computer I am not sure if it has two physical cores, I heard you need to physical cores not hyperthreaded to run a VM?

Will the lack of CD drive cause any problems? If so, how do I find out if my second computer has two physical cores or not?

Any answers to any of these questions would be appreciated, as well as any helpful links to guides. Thanks in advance!

Shouldnt be too hard though WHY ? LOL

anyways head over to [www.virtualbox.org]("http://www.virtualbox.org") and download and also download the extension pack.

when installed make sure you add yourself to the vboxusers group as folows:

[I]sudo usermod -a -G vboxusers username              

[/I]replacing username with your name, thought USB support wont be great in Windows 98...LOL

Then you are all set pretty much.  As for a CD drive no worries,as you can use .iso 

 so get yourself a windows 98 .iso and you are good to go.

then read here about 95/98 in virtual box [http://forums.virtualbox.org/viewtopic.php?t=9918](http://forums.virtualbox.org/viewtopic.php?t=9918)

enjoy

Check out the virtualistaion sub-forum here for more inforamtion, especially read the mega thread sticky. [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

enjoy

---

### Post by jfed on 2011-09-05
Wow its really that simple? For some reason I thought that VMs were like super crazy hard. Like Inception, lol.

And haha the reason I want to install 98 is because I found all the old classics like Oregon Trail! How can I pass that up??

Although why I had an install disk still in the factory packaging I have no clue...haha.

Well thanks a bunch, I'll try that out and let you know how everything goes.

---

### Post by haqking on 2011-09-05
> **jfed said:**
> Wow its really that simple? For some reason I thought that VMs were like super crazy hard. Like Inception, lol.

And haha the reason I want to install 98 is because I found all the old classics like Oregon Trail! How can I pass that up??

Although why I had an install disk still in the factory packaging I have no clue...haha.

Well thanks a bunch, I'll try that out and let you know how everything goes.


no problem.  post back if you have issues, keep it in the same thread.

If you get it sorted then mark the thread as solved using thread tools.

have fun

regards

haqking

---

