---
title: "Ubuntu goes MS way???"
date: 2009-09-15
forum: Testimonials &amp; Experiences
---

### Post by AnatolyR on 2009-09-15
Today I applied updates in batch for my Ubuntu installation (cause I had some trust to them)and after that realized that all my Java projects not working due to missing dir  /usr/lib/jvm/java-1.5.0-sun-1.5.0.18. There is new  /usr/lib/jvm/java-1.5.0-sun-1.5.0.19 dir created. Someone would say that I should use /usr/lib/jvm/java-1.5.0-sun simlink, but the question is not in how to use java (and in my case I want to know what version of java is used). The question is how it is possible that _non-temporary_ files have been deleted from my machine? I guess these data were deleted during update and if this is the case, it is absolutly MS way of doing things. And ofcourse, this is absolutly unacceptable, because I don't want someone somewhere to decide what non-temporary data to delete on my machine.

---

### Post by PilotJLR on 2009-09-15
I can't tell if this is a real question or a troll, but I'll assume you really are asking about this...

The version number changed because you applied updates. That's what an update is. This is also the reason using the symlink to call java is preferred.

Think about it... if an update didn't remove previous versions, then your system would have duplicate copies of everything, most of which would be outdated. That wouldn't make any sense at all.

If you don't want to use the java symlink, then you either need to stop updating the system, or pay attention to what is being updated. What you're basically doing is complaining that Ubuntu gave you a security update or bugfix.

---

### Post by running_rabbit07 on 2009-09-15
If old program files are left there will be issues. If you don't want certain programs making changes during updates, then read and unmark the the programs you don't want updating. I read the updates for Windows and Ubuntu and both are self explanatory as to what they are going to do.

---

### Post by AnatolyR on 2009-09-15
> **PilotJLR said:**
> 
I can't tell if this is a real question or a troll, but I'll assume you really are asking about this...

I'm not a troll, I'm just upset about current situation that on it's way to ultimate user-friendliness Ubuntu becomes clone of Windows. Kinda, kill a dragon - become a dragon.

> **PilotJLR said:**
> 

Think about it... if an update didn't remove previous versions, then your system would have duplicate copies of everything, most of which would be outdated. That wouldn't make any sense at all.

If it doesn't make sense for YOU, why data on MY machine should be deleted? And in my specific case, it really makes sense to have different versions of jvm.
That's what I call MS way, someone somewhere makes decision that certain non-temporary data is not needed for me without asking my opinion. And now I'm, concerned about granting  root privileges to app that deletes not-temporary data on my machine. 

> **PilotJLR said:**
> 
If you don't want to use the java symlink, then you either need to stop updating the system, or pay attention to what is being updated. What you're basically doing is complaining that Ubuntu gave you a security update or bugfix.

I'm complaining not about installing new version, but deleting old one. In my specific case I want to test my code against specific environment and java is part of it. That's why I was surprised that old version was deleted.

---

### Post by AnatolyR on 2009-09-15
> **running_rabbit07 said:**
> If old program files are left there will be issues. If you don't want certain programs making changes during updates, then read and unmark the the programs you don't want updating. I read the updates for Windows and Ubuntu and both are self explanatory as to what they are going to do.
What issues are you writing about? No disk space? Let me solve this issue myself. In case of Windows you have no option to choose what it install or update(they even can install updates with updater turned off) and it seems Ubuntu goes same direction.

---

### Post by the.dark.lord on 2009-09-15
Deleting old versions is turned on by default, since most people wouldn't want them. If you want to retain old versions, I'm sure there is some way to do that - I'm too lazy to look that up now.

No doubt some enlightened person will drop by, and tell you how.

---

### Post by 3rdalbum on 2009-09-15
> **AnatolyR said:**
> 
That's what I call MS way, someone somewhere makes decision that certain non-temporary data is not needed for me without asking my opinion.

You ran the Update Manager or gave it permission to install updates without your notification. Everyone knows that new versions replace old versions when you run an update. That's what separates updates from new repository packages!

> I'm complaining not about installing new version, but deleting old one. In my specific case I want to test my code against specific environment and java is part of it. That's why I was surprised that old version was deleted.

If the old version was 1.5 and the new version was 2.0, then yes. Even if the old was 2.0 and the new was 2.1, you might have a case. But this is a minor release - 1.5.0.18 to 1.5.0.19.  Bug fixes, security fixes, no API or languages changes and no behavioral changes. Unless your code is written with the assumption that Java is broken, and they fix the problem in the new update, there will be no change to your program.

You really are making a mountain out of a mole-hill.

---

### Post by HappyFeet on 2009-09-15
> **AnatolyR said:**
> this is absolutly unacceptable

Your attitude is totally unacceptable. If keeping the same version of java was that important to you, you should have exercised more control over what was being updated. 

And if you did not know that older versions of apps get replaced after an update, then it is *your* fault, not ubuntu's. And I agree that you are probably making way too much stink about nothing. Have a nice day.

---

### Post by Ms_Angel_D on 2009-09-15
> **AnatolyR said:**
> If it doesn't make sense for YOU, why data on MY machine should be deleted? And in my specific case, it really makes sense to have different versions of jvm.
No it doesn't make sense that you would be upset about when you gave it permission to delete the files by accepting the update. These are the way updates work, out with the old and in with new. If you didn't want this update you should have pinned the version. To prevent it from being updated.

> **AnatolyR said:**
> That's what I call MS way, someone somewhere makes decision that certain non-temporary data is not needed for me without asking my opinion. And now I'm, concerned about granting  root privileges to app that deletes not-temporary data on my machine.

old versions are not needed when they have bugs, Updating means getting rid of old versions and replacing them with new ones. This is not a microsft thing this is an update thing.

> **AnatolyR said:**
> I'm complaining not about installing new version, but deleting old one. In my specific case I want to test my code against specific environment and java is part of it. That's why I was surprised that old version was deleted.

Well if you didn't want this to happen you should have done some research before hitting that update button. Ubuntu doesn't make you update you decided to do it.

---

### Post by running_rabbit07 on 2009-09-15
> **AnatolyR said:**
> What issues are you writing about? The issues of clashing programs when Firefox tries to implement Java end starts two versions at the same time because you didn't get rid of the old version. If you have your updates set to automatically upgrade to Ubuntu 9.10 when it is released, would you want it to keep 9.04 stored for you? 
If you replace an engine in a truck, would you expect the mechanics to run lines to the old engine and mount it in the bed so that it can run at the same time as the new one which actually moves you vehicle? It is the same concept.

> **AnatolyR said:**
> No disk space?

Obvious problem over time.

> **AnatolyR said:**
> Let me solve this issue myself.

You can easily do that by not allowing the Update Manager do updates or axcept that it is going to throw away the old versions.

> **AnatolyR said:**
> In case of Windows you have no option to choose what it install or update(they even can install updates with updater turned off) and it seems Ubuntu goes same direction.

Whenever I did my updates with MS, I read every update to see what it did, or at least I had the option and if it were something I did not want I, could check the little box and never see it again. You can run Wireshark on your system and see if MS is really installing anything or find out how much you have read about MS is just anti-MS FUD.

Ubuntu does no update unless you tell it to. Go to System>Administration>Software Sources and turn off automatic updates.

This is a simple problem with an easy fix. In the future *please* do not bash any operating systems just because you do not understand what is happening. Explain the problem and someone will explain a fix.

---

### Post by OgreProgrammer on 2009-09-16
To me the MS way of doing things is to retain a bunch of DLLs and other files of various version numbers. This would be much like what the OP wishes. 

I would rather have a clean update process and then program in a way that accounts for new versions.

---

### Post by Tamlynmac on 2009-09-16
One other thing to keep in mind is that potentially a file may contain a security issue. By updating and replacing/removing said file, a security flaw may be removed.

See this section: [http://ubuntuforums.org/forumdisplay.php?f=13](http://ubuntuforums.org/forumdisplay.php?f=13)

As others have noted - updates are optional. However, IMHO security updates should be considered critical.

---

### Post by Slorg on 2009-09-17
Oh my God, I just upgraded from Ubuntu 8.10 to Ubuntu 9.04 and they deleted Ubuntu 8.10 :shock:
I didn't give any permissions to remove Ubuntu 9.10, I just wanted to update to Ubuntu 9.04..
I think this is pretty evil, Ubuntu is clearly going the Micro$oft way!

--

And now you know how ridicilous it sounds :wink:

---

### Post by SuperSonic4 on 2009-09-17
To think, when I first joined it was possible to refute a point on the grounds of the point made - not launch derisive attacks on the person making them...

---

### Post by Tamlynmac on 2009-09-17
> SuperSonic4
To think, when I first joined it was possible to refute a point on the grounds of the point made - not launch derisive attacks on the person making them...

I think one of the problems, is many tire of those that have an incessant need to constantly compare Ubuntu to Windows. For some, Windows represents computing and its all they know. They try and flaunt their knowledge and opinions by using comparisons. For without a comparrison they have no fundamental argument. They lack basic comprehension of Ubuntu/Linux and thus their arguments must rely solely on comparisons. How sad is that?

IMHO one of the only reason people compare Windows to Ubuntu/Linux is out of ignorance. A true comparison (including benchmarks) is hard to perform (not to mention costly) and humans tend to add complexity, based on bias. I would suggest to anyone posting in this section, that they question Ubuntu/Linux on it's own merit and not feel the need to draw comparisons to MS.

Some come to this forum with the priority of disrupting it. It's often hard to identify them and based on history in this section the odds are in favor of the individual posting comparisons (especially with only three posts under their belt).

If one wishes to observe this type of behavior, might I suggest they review the number of individuals that have posted in this section, with the very intent of attempting to demean Ubuntu based on Windows. It gets old and one would think those individuals could display more creativity. Perhaps, that's why they use Windows. :-k

---

