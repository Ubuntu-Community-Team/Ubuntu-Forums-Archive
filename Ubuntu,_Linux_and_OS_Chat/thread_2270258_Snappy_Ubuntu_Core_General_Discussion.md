---
title: "Snappy Ubuntu Core General Discussion"
date: 2015-03-21
forum: Ubuntu, Linux and OS Chat
---

### Post by helpee on 2015-03-21
Hello Everyone!

I just downloaded the new Snappy Ubuntu Core image and am running it as a VM for fun. Poking around, I am finding out left and right that it is a significantly different experience than using traditional server or desktop distros of Ubuntu ( no root login, multiple root partitions, no apt-get, etc ). Looking around on the web, there doesn't seem to be a lot of community shared knowledge or experience going on with this, which is surprising to me as a long time user in this community. I'm starting this thread to get the ball rolling on getting people engaged in questions, comments, knowledge or experience for Snappy.

I like the idea of Snappy. Beyond the obvious Internet of Things concept, it is also a serious attempt for a "One OS to run on them all" paradigm change, as well as a change in the way we think about creating, distributing and running software. If you are excited or curious about Snappy, then this is the thread for you. I hope that by coming here and sharing our experiences that we can build a solid place for newcomers and experienced users alike to come search for the new knowledge we all seek.

Cheers!

---

### Post by neelson2 on 2015-05-29
I also do appreciate the idea behind Snappy. I would like to test it on a raspberry pi 2 although it's not officially supported. Before i do that however, i would like to know what apps are available. Do you know some place where i can search for and browse through apps?

Best regards,
Neelson

---

### Post by Frogs Hair on 2015-05-29
Discussion Thread, moved to *Ubuntu, Linux and OS Chat *

---

### Post by craig10x on 2015-05-29
It's just getting started as far as the desktop version....they're hoping to have it ready for prime time by the release of 16.04 LTS next april...at which time they hope to offer two versions: standard ubuntu LTS and ubuntu snappy desktop stable version...Our "testing" friends in the testing forum will be working with the testing images through the 15.10 and 16.04 development cycle...If it works out well, we will have a stable but "rolling style" ubuntu available as an option...:D

---

### Post by matt_symes on 2015-06-05
Just been playing around with the Vivid image in kvm.

Looks promising. It's easy to use and, by the looks of it, easy to create snappy packages.

I need to read more of the documentation though and play with it more to get a real feel for it.

My only concern is the security aspect of it on IoT devices. 

We have already demonstrated that we can't secure our routers from vulnerabilities and most people wouldn't upgrade the firmware on their router to protect it even if a firmware update was released.

Obviously the people on these forums are more tech savvy than many and would update the firmware, however i suspect that we may agree that most of the people we know would not.

I guess my main concern is that i don't want to have to ssh into each of my IoT connected light bulbs to manually update ubuntu-core to fix a security vulnerability to stop my light bulbs becoming part of a botnet that is involved in a DDOS of Facebook :)

It'll be interesting to see how this plays out.

---

### Post by grahammechanical on 2015-06-05
I understood that one of the advantages of Snappy Ubuntu core was that the OS would be upgraded by transactional updates and so would the applications. Canonical publicity is saying that developers of Internet of Things devices can create their own software and package it as a snap package and use a transactional update to upgrade the application without needing to update the OS.

An Internet of Things device would have to be connected to the Internet. In this way the task of updating is taken away from the consumer.

[http://insights.ubuntu.com/2015/05/28/ges-first-build-is-the-future-of-smart-home-appliances/](http://insights.ubuntu.com/2015/05/28/ges-first-build-is-the-future-of-smart-home-appliances/)

The security model of Ubuntu Snappy is a strong protection. The kernel and the OS will be Snaps and the file system is read only. The applications will be Snaps and each will have an Apparmor profile to prevent them doing anything malicious. The apps run confined and will not have direct access to the file system. Requests by apps for data will go through a Content Hub and if the request is outside the app's profile it will either be denied or a user authentication request will be triggered.

[https://wiki.ubuntu.com/SecurityTeam/Specifications/SnappyConfinement](https://wiki.ubuntu.com/SecurityTeam/Specifications/SnappyConfinement)

Regards.

---

### Post by matt_symes on 2015-06-06
> **grahammechanical said:**
> I understood that one of the advantages of Snappy Ubuntu core was that the OS would be upgraded by transactional updates and so would the applications. Canonical publicity is saying that developers of Internet of Things devices can create their own software and package it as a snap package and use a transactional update to upgrade the application without needing to update the OS.

An Internet of Things device would have to be connected to the Internet. In this way the task of updating is taken away from the consumer.

[http://insights.ubuntu.com/2015/05/28/ges-first-build-is-the-future-of-smart-home-appliances/](http://insights.ubuntu.com/2015/05/28/ges-first-build-is-the-future-of-smart-home-appliances/)

The security model of Ubuntu Snappy is a strong protection. The kernel and the OS will be Snaps and the file system is read only. The applications will be Snaps and each will have an Apparmor profile to prevent them doing anything malicious. The apps run confined and will not have direct access to the file system. Requests by apps for data will go through a Content Hub and if the request is outside the app's profile it will either be denied or a user authentication request will be triggered.

[https://wiki.ubuntu.com/SecurityTeam/Specifications/SnappyConfinement](https://wiki.ubuntu.com/SecurityTeam/Specifications/SnappyConfinement)

Regards.

I understand that snappy is transactional both for the OS and for any applications. That is not my concern.

My concern is will these things ever actually be updated when vulnerabilities are found. 

Will vendors actually produce updates for these IoT connected items.

Will these updates have to be manually installed ?

If they are automatically installed, are they going to be protected from the various attacks that can and have happened against automatic updates.

All I'm saying is that based on our previous strategies for handling these issues on consumer devices we've got it wrong; badly wrong.

A paper was recently released from researchers in Spain or Italy (i forget which) detailing major vulnerabilities in over 20 consumer routers. It's an interesting read.

We know that compromised routers have been involved in DDOS against a number of large websites.

> 
An Internet of Things device would have to be connected to the Internet.  In this way the task of updating is taken away from the consumer.

So are routers.......

I understand about confinement. However there are been escapes from LX containers that allowed root privilege escalation and various vulnerabilities have been found in virtualisation, the most recent high profile one being Venom.

We need a transparent, secure, authenticated, verified update mechanism for these devices and so far we have failed woefully at that.

Open source software is the way only to go and i think that snappy as a technology is a good way forward. Open source because fixes can be developed by the community for the community and snappy as its transactional update system can make the OS and the applications far more robust after an update. ie they can protect against failed updates.

What i'm saying is that I really hope we can get this right this time. This is hard but it's not beyond the wit of humans.

It's an interesting discussion point.

---

### Post by Copper Bezel on 2015-06-06
The transactional updates aren't directly related to the security side - that's just good design to keep things from breaking, either by preventing a partial update or by allowing rollbacks for bad updates. The idea here is to automate updates, yes. The model on that front is the Chromebook OS, which updates automatically as soon as it notices it isn't the current version. But I think that even with Snappy Core, we're looking less at IoT and more at things like server deployments where administrators have new tools to roll out updates en masse, etc.

---

