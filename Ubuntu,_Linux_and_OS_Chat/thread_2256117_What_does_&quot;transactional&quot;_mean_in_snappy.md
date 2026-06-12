---
title: "What does &quot;transactional&quot; mean in snappy ubuntu?"
date: 2014-12-10
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2014-12-10
I just watched Mark Shuttleworth introducing "snappy" ([https://www.youtube.com/watch?v=BlcTDz9ogug](https://www.youtube.com/watch?v=BlcTDz9ogug)). He used the word "transactional(ly)" quite often. What does it mean in the context of the video?

---

### Post by mikodo on 2014-12-10
Well, I guess this is it. Looked it up of course.

[(Computer Science) (in general computing) the transmission and processing of an item of data]("http://www.thefreedictionary.com/transactionally")

I think Mark is talking about images being uploaded/downloaded and read by distributed applications using Docker containment and Ubuntu OS compartmentalization.

[URL="http://www.thefreedictionary.com/transactionally"]


[/URL]

---

### Post by vasa1 on 2014-12-10
> Furthermore, snappy uses a "transactional" (or "image-based") update mechanism (for both the system and applications), which means that each update can either completely succeed or completely fail, without "partial failures". Before each update, snappy backs up the data and rolls back if the update fails, so the system is never in a broken / incomplete state.
[http://www.webupd8.org/2014/12/canonical-announces-snappy-ubuntu-core.html](http://www.webupd8.org/2014/12/canonical-announces-snappy-ubuntu-core.html)
and
[http://www.markshuttleworth.com/archives/1434](http://www.markshuttleworth.com/archives/1434)

No mention of click packages?

Edit: > One or more &#8220;frameworks&#8221; can be installed through the snappy command, which is an adaptation of the **click packaging system** we developed for the Ubuntu Phone.from [http://blog.dustinkirkland.com/2014/12/its-a-snap.html](http://blog.dustinkirkland.com/2014/12/its-a-snap.html)

---

### Post by vasa1 on 2014-12-11
More snappy news here> A smartphone-inspired version of Ubuntu Server for Docker minimalists has been revealed with initial backing from Microsoft.[http://www.theregister.co.uk/2014/12/09/ubuntu_core_snappy/](http://www.theregister.co.uk/2014/12/09/ubuntu_core_snappy/)

And another way of looking at *transactional*:>  As such, Ubuntu Core, and its applications and their Docker containers are designed to be upgraded atomically and rolled back if needed. So with "transactional" or "image-based" systems, when you upgrade a server **or app you don't patch it, you replace it.**[http://www.zdnet.com/article/snappy-ubuntu-challenges-coreos-and-project-atomic-on-lightweight-cloud-servers/](http://www.zdnet.com/article/snappy-ubuntu-challenges-coreos-and-project-atomic-on-lightweight-cloud-servers/)
So now I'm back to being confused. Hasn't Ubuntu traditionally replaced apps rather than "patch" them by means of delta (differential) updates?

Maybe [this is what transactional]("http://siliconangle.com/blog/2014/12/09/canonical-restructures-ubuntu-in-mobile-mode-enlists-microsoft-as-first-partner/?") means:> Transactional updating is a software distribution technique that should be familiar to any smart phone user. Instead of requiring users to download and install dozens of individual packages each time an application is updated, integration is done at the server level and downloaded as an entire image. The process makes it easier to distribute updates automatically across multiple platforms and provides for rollback if needed.

---

### Post by grahammechanical on 2014-12-11
They have taken this from the phone/tablet method of updating. On the desktop apt-get is used to update individual packages. That method is not used on the Ubuntu phone OS. The phone gets image updates. As I understand things it is only the code difference between the present image and the updated image that is downloaded. There is a separation between the system image and the applications. As each app developer upgrades their apps and moves them into the app store the app will be updated when the phone user updates the phone. It is a separate action from updating the phone OS.

[http://blog.dustinkirkland.com/2014/12/its-a-snap.html](http://blog.dustinkirkland.com/2014/12/its-a-snap.html)

[https://en.wikipedia.org/wiki/Transaction_processing_system](https://en.wikipedia.org/wiki/Transaction_processing_system)

Now, to confuse us even more, Snappy comes with _atomic_ workflows. No more black screen with a flashing cursor. Just a very large mushroom shaped cloud where the server used to be. :)

[https://en.wikipedia.org/wiki/Atomicity_%28database_systems%29](https://en.wikipedia.org/wiki/Atomicity_%28database_systems%29)

> [COLOR=#000000]No mention of click packages?[/COLOR]

> [COLOR=#333333][FONT=Ubuntu]One or more &#8220;frameworks&#8221; can be installed through the [/FONT][/COLOR]*snappy command, which is an adaptation of the [I][click]("http://developer.ubuntu.com/publish/apps/packaging-click-apps/") packaging system we developed for the Ubuntu Phone.  *[/I]

> [COLOR=#333333][FONT=Ubuntu]Perhaps the best sample framework is [/FONT][/COLOR][Docker]("http://docker.il/")[COLOR=#333333][FONT=Ubuntu].  Applications are also packaged and installed using snappy, but apps run within frameworks.  This means that any of the thousands of Docker images available in DockerHub are trivially installable as snap packages, running on the Docker framework in Snappy Ubuntu.[/FONT][/COLOR]


The video in Dustin Kirkland's blog shows it doing a roll back. Now imagine that on the desktop.

Regards.

---

