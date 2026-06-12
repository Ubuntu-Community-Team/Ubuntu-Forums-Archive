---
title: "New 9.04 System Freezes"
date: 2009-07-10
forum: System76 Support
---

### Post by Teasdale on 2009-07-10
I have a new Ratel value with Ubuntu 9.04 pre-installed. Sometimes the system locks up, but from what I'm reading, this seems to be a common problem with Jaunty 9.04. It doesn't happen often - once every few days - but some are saying that the frequency increases until they can't go ten minutes without freezing.

One theory is that it has to do with hardware - NVidia card, Intel - but since my system was built to be compatible with Ubuntu, I wouldn't think that would be an issue. Not with this computer.

I've just done the latest update. My question is - should I back up my files and do a clean install of 8.10, which has worked great with my other Ratel Value, or wait it out and assume an update will fix whatever the bug is with 9.04?

---

### Post by Chemical Imbalance on 2009-07-10
nevermind.

---

### Post by Teasdale on 2009-07-10
So many things I'm finding seem to say that the issue is with old hardware, especially the graphics card, - and my hardware is all new.

I still may install Intrepid (unless there's some reason that my new hardware would make that a bad idea?) 

In the meantime, I saw a post here that suggested installing linux-backports-modules-jaunty - which I found in the synaptic package manager, so I've installed that.

---

### Post by thomasaaron on 2009-07-13
If that doesn't work, shut your computer down the next time it freezes. Then restart it and go *immediately* to System > Administration > System76 Driver > Support (tab) > Create (button). This will create an archive called logs.tar in your home directory. Please attach that archive to this thread.

Also, please give a little more detail about the freeze.

---

### Post by Teasdale on 2009-07-15
> **thomasaaron said:**
> System > Administration > System76 Driver > Support (tab) > Create (button). This will create an archive called logs.tar in your home directory. Please attach that archive to this thread.


I've printed those instructions out and will do that if it happens again.

---

### Post by glacialfury on 2009-08-04
I think I'll head back to intrepid until the storm clears.

---

### Post by HotShotDJ on 2009-08-04
I looked at the current specs of the Ratel Value. The default Graphics Adapter is the Intel X3100 with options for various ATI cards.

There are some known issues with Jaunty (9.04) and Intel graphics adapters. If your Ratel Value came with the Intel X3100 card, perhaps [THIS]("http://ubuntuforums.org/showthread.php?t=1130582") thread may help you get your problem sorted.  I don't know if System76 has tested this fix.  Perhaps ThomasAaron may know whether the "Safe," "Optimal," or "Bleeding Edge" method is best for this particular computer.

I don't know anything about the ATI cards.  But if you have one of them, that How-To will not help you.

---

### Post by thomasaaron on 2009-08-04
That's more about performance under certain circumstances. It has nothing to do with the freezing, I don't think.

---

### Post by Teasdale on 2009-08-26
I haven't had any freezes lately, until today. I did the update a couple days ago that updated the System76 driver.

I've had the PC on for days, used leafpad, open Office, printed things, been all over the internet. Today I went on Facebook and the window locked. I was using the Epiphany browser. Facebook opened, but as I was scrolling down the page, the page stopped moving. I couldn't click on anything or close the windw, although the mouse was responsive and moved the cursor.

I restarted the PC and created the logs.tar as instructed and will attach it here.

---

### Post by Ed.Corcoran on 2009-08-26
That sounds exactly like the problem I've been having, only I have a Wild Dog.

---

### Post by reddoghimself on 2009-09-22
what is system 76?

---

### Post by Eldera on 2009-09-22
System 76 is a company, based in Denver, Colorado, USA; who manufacturers computers with Ubuntu installed.

You can see their line of computers at [http://www.system76.com/](http://www.system76.com/)

This sub forum is for people who own System76 computers, just like the Dell sub forum is for people who own Dell computers.

As a part of their continuing support for their customers, System76 maintains a driver package in their knowledge base which provides updates and patches specifically for System76 computers.

---

### Post by Teasdale on 2009-10-16
> **thomasaaron said:**
> If that doesn't work, shut your computer down the next time it freezes. Then restart it and go *immediately* to System > Administration > System76 Driver > Support (tab) > Create (button). This will create an archive called logs.tar in your home directory. Please attach that archive to this thread.

Also, please give a little more detail about the freeze.

New freeze today. I've had my PC on for days (weeks?) with no problems. I haven't turned it off or rebooted. I've been busy online, I had a couple of Firefox browser windows open and I was responding to a post on my favorite parenting message board, and the computer froze mid-sentence.

I could still move the mouse around the screen, but nothing else. I couldn't click anything, couldn't close anything. When I pushed the power button to turn the PC off, it wouldn't turn off until I held it in for a few seconds.

I'm attaching a new tars.log.

---

### Post by ExpressNature on 2009-10-16
I installed ubuntu 9.04 yesterday using Wubi installed inside XP. It worked fine till yesterday night. But today morning it undergone an update of some 400 MB and after reboot, the system operated for few minutes. I opened the firefox and tried to install plugins for Video (Adobe shockwave) in the browser. But suddenly the mouse was stucked :confused: and nothing is worked. It seems as it freezed[IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG] . What exactly the problem I don't Know.. Hope someone can find a solution for this issue!...

---

### Post by thomasaaron on 2009-10-19
I'm not seeing much in your logs. Do you have an ATI graphics card in your Ratel?

---

### Post by Teasdale on 2009-10-19
> **thomasaaron said:**
> I'm not seeing much in your logs. Do you have an ATI graphics card in your Ratel?

I did a "sudo lshw" to get a list of what's in the computer, and then I word-searched "ATI" and nothing came up. When I do a search for the word "graphic," this is what comes up:

description: VGA compatible controller
product: 82G33/G31 Express Integrated Graphics Controller

I haven't opened the tower, so whatever is in there is what came with the PC when it was shipped in June.

---

### Post by thomasaaron on 2009-10-20
OK. Let's take this one to email so I can look up your configuration. Please email me directly at support...at...system76...dot...com.

---

### Post by betrunkenaffe on 2009-10-20
I'm pretty sure there is something in 9.04 (after various updates) that broke for some people, I've heard of the freezing system glitch more as time went on. I know I had it.

9.10 has been a dream for my Pangolin, if you are willing to give a beta a try, download, burn and livecd it.

---

### Post by Eldera on 2009-10-21
To ExpressNature: Hello, I see from your profile that you are new to this forum. This forum is divided into sub-forum for people with special problems. The sub-forum where you have posted your problem is for people who own computers made by System 76. Because System76 computers come with Ubuntu pre-installed, very few of their owners would be using WUBI.

I am guessing that is why nobody has offered you any help in four days. I saw your post, but because I have never used WUBI, I could not make any suggestions.

Are you still having problems? If you are, I suggest you start a new thread in a different sub-forum.

If you go to this page of the forum [http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326) click the New Thread button near the top of the page and post your problem there. you may get some help. 

We could also help you better if you told us a little bit more about your computer. What kind of a computer is it? Did you have only XP on it before you tried to install WUBI? After the computer froze, were you still able to re-boot into XP? Did you post your problem from the same computer, or did you have to use a different computer to contact us?

---

### Post by gamerchick02 on 2009-10-21
Is anyone in this thread running Miro?

I was running the 2.0 branch, and having performance problems.  I was getting a system load of 12!  It was crazy.

If you are running Miro, try upgrading to the 2.5 version via a separate repo: [http://www.getmiro.com](http://www.getmiro.com)

Just a quick observation of mine.

Amy

---

### Post by victoral.com on 2009-10-22
It might be your graphics card. Because I run with an ati graphics card and have never gotten frozen but on my other pc it has an nvdia card and frezes all the time.

---

### Post by thomasaaron on 2009-10-23
I suspect the ATI card too, but I'm not sure if I 've received an email on it or not yet.

---

