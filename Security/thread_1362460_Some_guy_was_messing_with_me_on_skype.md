---
title: "Some guy was messing with me on skype"
date: 2009-12-23
forum: Security
---

### Post by Nailox on 2009-12-23
I think he somehow made me reboot.. is it possible that he had deployed a file in my system and how should look for that file ?

---

### Post by 73ckn797 on 2009-12-23
> **Nailox said:**
> I think he somehow made me reboot.. is it possible that he had deployed a file in my system and how should look for that file ?


We would need more details.

---

### Post by Nailox on 2009-12-23
I cliked on skype>options and it logged me out so i had to enter the default keyring password so Im not sure if this is a reboot.. a friend of mine who was in the same chat session told me he had discovered a suspicious file in his System folder - he is on windows - so I was wondering if i got something on my machine as well.. i run crontab-e - it says its empty and offers me some editors

---

### Post by cdenley on 2009-12-23
> **Nailox said:**
> I cliked on skype>options and it logged me out so i had to enter the default keyring password so Im not sure if this is a reboot..

Logged you out of skype? Out of ubuntu? You had to enter a keyring password because of a logout? You're not sure if it rebooted?
> **Nailox said:**
> 
a friend of mine who was in the same chat session told me he had discovered a suspicious file in his System folder - he is on windows - so I was wondering if i got something on my machine as well..

I seriously doubt it.

---

### Post by User3k on 2009-12-23
Simple rule is if something is not going as it usually does, not normal to your routine or something that is not doing what it should be or what you are use to, then immediately stop and don't click on anything or enter any passwords, etc. 

If you are worried about anything then use rkhunter, chkrootkit and avast for Linux. At the very least to give you peace of mind.

Edit: If it would make you feel more secure then you could install Firestarter, a frontend to the iptables (firewall.) Works really well. And you can check your ports as well at [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

Now there is some debate on whether one should have all ports stealthed, true stealth, closed/stealthed or just closed. I choose true stealth.

---

### Post by Nailox on 2009-12-23
logged me out of ubuntu yes.. might be a false alarm idk.. thanks user3k that was helpful

---

### Post by User3k on 2009-12-23
> **Nailox said:**
> logged me out of ubuntu yes.. might be a false alarm idk.. thanks user3k that was helpful

Glad I could help. :)

---

### Post by cdenley on 2009-12-23
> **Nailox said:**
> logged me out of ubuntu yes.. might be a false alarm idk.. thanks user3k that was helpful

It you were suddenly "logged out of ubuntu", then I would suspect an X server crash, unless there was something to indicate otherwise.

---

### Post by scottuss on 2009-12-23
Did you note the application that asked you to enter your password?

---

### Post by zappal on 2009-12-28
This also just happened to me. It also happened a few days ago.
I went to click on Skype Options and the Operating System logged me out instantly.
Running updated Ubuntu 9.10 and Skype Beta 2.1.0.47
First time it occured I right click Skype icon in the System Tray
This time, the main Skype contact list window was open, and i went to options from there.

---

### Post by gradinaruvasile on 2009-12-28
It seems that Skype crashed and took X server with it...
What video card do you have? Also, do you have webcam? 
Skype crashed on me once when i clicked options but was related to my webcam setup - i now use the LD_PRELOAD trick and all is working fine.

But never crashed X. But then again, i have Nvidia vid card that is really stable. I found that the some Intel/Ati opensource driver versions made X server unstable on some hardware (i saw it on Ati X1600/1300, Dell Inspiron 530 with integrated Intel graphics card) and prone to crash when applications crash within it.

---

### Post by zappal on 2009-12-28
thanks for the fast reply, this does make sense.
to answer your question, its a Intel 82945G onboard video.

This is a new system install and I have yet to iron out some things like the web cam; right now its showing green fuzz when I test it. So I'll search around the forum to figure out how to preload it or whatever.
Webcam is Logitech QuickCam Communicate STX Plus

If you have any suggestions or links to share feel free :) thanks

---

### Post by gradinaruvasile on 2009-12-28
Try this:

Open a terminal. Type:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

See if it works.

---

### Post by zappal on 2009-12-28
It worked. thanks :)

I also found a couple interesting links regarding pre-loading web-cam:
[http://www.eoinmurphy.org/blog/2009/04/26/logitech-webcam-skype-under-ubuntu/](http://www.eoinmurphy.org/blog/2009/04/26/logitech-webcam-skype-under-ubuntu/)

[http://blog.export.be/2009/07/fixing-your-webcam-in-ubuntu-jaunty/](http://blog.export.be/2009/07/fixing-your-webcam-in-ubuntu-jaunty/)

---

### Post by zappal on 2009-12-28
actually, I just wanted to follow up and mention what im seeing. I left the terminal open after running the commpand. And im noticing these lines are being added about every 15 minutes or so..

zappal@hostname:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
X Error, request 42, minor 0, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 42, minor 0, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 42, minor 0, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 42, minor 0, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 42, minor 0, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 42, minor 0, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 42, minor 0, error code 8 BadMatch (invalid parameter attributes)

Unsure...

---

