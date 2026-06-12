---
title: "Heads up: 12.04, the Anywhere MX Mouse (&amp; other Darkfield Mice?)"
date: 2012-04-27
forum: The Cafe
---

### Post by neu5eeCh on 2012-04-27
This is just a heads up. Several users, including me, have noticed that their Mouse hardware has failed when using 12.04 (I've been testing Ubuntu's 12.04 Beta up to now). The failure could be purely coincidental, but it could also signal that 12.04 (perhaps at the kernel level) is somehow damaging the hardware of these mice. The bug report is here:

[https://bugs.launchpad.net/ubuntu/+bug/958174](https://bugs.launchpad.net/ubuntu/+bug/958174)

What worries me are the following symptoms: 

1.) I started testing 12.04 with a fully functional Anywhere Mouse. Gradually, the mouse began to fail. At first, it wasn't recognized at boot up, then it began to fail during normal usage. Eventually it didn't work on any OS, Ubuntu (any version), or Windows.

2.) Logitech replaced my mouse. I've been using it on Xubuntu 11.10 with no troubles (as with the old mouse). The last time I used the _new_ mouse on the 12.04 partition, the _**new**_ mouse _failed_ at boot up. Had to unplug it and plug it back in. This is precisely the behavior that led to the eventual hardware failure of the old mouse. Again, this could be purely coincidence, but if you have one of these mice and it begins to show the same symptoms with 12.04, visit the bug report and let the devs know. Also, you might want to stop using it with 12.04 _anything_. It could be nothing, or it could be very serious.

---

### Post by nankura on 2012-04-27
> Eventually it didn't work on any OS, Ubuntu (any version), or Windows.

I noticed you menchoned "windows" typo?, because if thats the case then id be looking at the mouse itself and hardware issues rather than a bug in ubuntu or ubuntu's software

Ive used a Sharkoon FireGlider and a Microsoft Intellipoint 2.1 ( i think its 2.1 , the black one with side buttons ) and i highly doubt that using a mouse in ubuntu could cause a windows issue, unless theres a secret virus out there sending firmware to a mouse? idk, just doesnt sound right 

And ive had no problems whatsoever, yea there not logitech, but frankly sharkoon isnt the most widely supported brand. as long as the mouse plugs into a USB port, detection and functionality usually isnt a problem. you just cant use the "included" software from vendors usually

So i find your situation abit odd

Now thats not to say that its not a problem. but if anything its a kernel issue rather than ubuntu itself possably with that specific mouse brand

Like i said, i find it extremely odd how using a USB mouse in ubuntu could cause functionality issues in windows.

---

### Post by neu5eeCh on 2012-04-27
> **nankura said:**
> I noticed you menchoned "windows" typo?, because if thats the case then id be looking at the mouse itself and hardware issues rather than a bug in ubuntu or ubuntu's software...

The situation is very odd. But the mention of windows isn't a typo. The fact that the mouse stopped working in windows *definitively* argues that the mouse failed. But -- the question isn't *where is the problem*? -- but *what caused it*. I find it odd that others (who are using mice with Darkfield technology) are also experiencing hardware failure when their mouse is used with 12.04. Like I said, it could be sheer coincidence. The purpose of my post is to raise awareness. If others use these mice and have no problems with 12.04, then we can chalk it up to coincidence.

---

### Post by nankura on 2012-04-27
im assuming your talking about this mouse 

[http://www.logitech.com/en-gb/mice-pointers/mice/devices/5846](http://www.logitech.com/en-gb/mice-pointers/mice/devices/5846)

i did notice its wireless. im not trying to say your foolish with this. but did you check the batterys?

Though, on a small note, i did some researching and found people in windows, who id imagine dont use linux. are having consistant issues with this specific mouse. a phew people have RMA'd the product due to issues

also in the review section on the main website, there is multiple bad user reviews about the mouse's hardware issues

heres some links
[http://reviews.cnet.com/mice/logitech-anywhere-mouse-mx/4864-3148_7-33767206.html](http://reviews.cnet.com/mice/logitech-anywhere-mouse-mx/4864-3148_7-33767206.html)
[http://forums.techarena.in/hardware-peripherals/1446993.htm](http://forums.techarena.in/hardware-peripherals/1446993.htm)

and heres an old post with ubuntu
[http://ubuntuforums.org/showthread.php?t=1895331](http://ubuntuforums.org/showthread.php?t=1895331)

Seems it might just be another poor release by logitech, they have released a phew mice brands that had major issues and are well known for the odd "great mouse" and a bunch of buggy mice

Thats why i steer clear of them in my competitive gaming scene

[http://forums.logitech.com/t5/Mice-and-Pointing-Devices/Anywhere-Mouse-MX-not-working/td-p/812965](http://forums.logitech.com/t5/Mice-and-Pointing-Devices/Anywhere-Mouse-MX-not-working/td-p/812965)

Id say its just that the mouse isnt to well supported on both operating systems. seems its having issues on both, even with general windows users

Though Considering that the mouse seems to have general functionality issues with multiple people on multiple operating systems, its good to help people become aware before they go off and purchase it =D

---

### Post by neu5eeCh on 2012-04-27
> **nankura said:**
> i did notice its wireless. im not trying to say your foolish with this. but did you check the batterys?

Well, yes, it's always wise not to underestimate ones own fathomless stupidity, especially mine. :| I did, this time, think to put in fresh batteries.

> **nankura said:**
> Though, on a small note, i did some researching and found people in windows, who id imagine dont use linux. are having consistant issues with this specific mouse. a phew people have RMA'd the product due to issues

Thanks for the links. I find it hard to believe that an "OS" could damage mouse hardware, but the coincidental nature of it was disturbing. On the other hand, correlation does not equal causation. Case in point: My dog, four days ago, bit down on a baby porcupine. I pulled out as many quills as I could. Two days later my dog could barely walk. I figured it was an infection caused by the quills and took her to the vet. The vet pulled out another 100 tiny quills from her mouth and asked to do a heart worm and Lyme Disease test. The cause of the symptoms seemed obvious to me, but I agreed to the test because correlation does not equal causation and I tend to be ruthlessly scientific about these things. Turns out my dog has Lyme Disease. She's in a world of hurt right now but improving. I'm sure she's convinced that the porcupine caused her Lyme disease.

---

### Post by SemiExpert on 2012-04-27
In my case, the fault is intermittent, and hasn't been an issue in Windows, at least not yet.  At one point, I thought that the issue was tied to allowing Grub to time-out, or perhaps was a kernel issue.  Currently, I haven't had an issue in the last half dozen reboots, but I wouldn't want to venture a guess as to why?  As far as the operation of the mouse itself, when the adapter is recognized, the mouse is absolute fine, with all buttons recognized and functional.  It's a great little mouse, probably the best of its kind.

---

### Post by SemiExpert on 2012-04-28
And the mouse isn't recognized after boot-up.  It seems as though this is happening when it takes more than a couple of seconds to connect to WiFi.  Odd.

---

### Post by SemiExpert on 2012-05-01
Bug report:  Confirmed/Undecided/Unassigned  [https://bugs.launchpad.net/ubuntu/+bug/958174](https://bugs.launchpad.net/ubuntu/+bug/958174)

---

