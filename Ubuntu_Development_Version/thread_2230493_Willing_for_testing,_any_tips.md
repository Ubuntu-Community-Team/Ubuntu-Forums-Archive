---
title: "Willing for testing, any tips?"
date: 2014-06-19
forum: Ubuntu Development Version
---

### Post by LastDino on 2014-06-19
So, I'm willing to do testing for Xubuntu and Unity (but that would be half hearted as my system is old). 

However, I would like to know few things as I'm only recent Windows migrant. 
Is there any particular format or ''how to'' I need to follow for testing or just installing and using it is enough?
Where to report bugs?
Is there any list of commands or things I might need to know for this?
Is testing in VM fine or you need HD install?

Any other tips coming to mind?

---

### Post by sudodus on 2014-06-19
Welcome to testing :-)

One good way to test is to work with the ***testing tracker***
[URL="http://iso.qa.ubuntu.com/"]
http://iso.qa.ubuntu.com/[/URL]

where you can download the daily build of Xubuntu, test according to a list and report the result. When you find bugs, please report them at [Launchpad]("https://launchpad.net/"). You need an account at Launchpad for this (maybe you have one already).

You can also engage in discussions at mailing lists and IRC.

---

### Post by deadflowr on 2014-06-19
I would say number 1 thing to do is create a launchpad account.
Then read [cariboo907's sticky]("http://ubuntuforums.org/showthread.php?t=2221153")

In terms of reporting bugs, it helps to be fully accurate on which packages are affected.
If you need help figuring such packages out, post about it here, and others will help on that.

---

### Post by rrnbtter on 2014-06-19
Greetings,
[http://cdimage.ubuntu.com/daily-live/20140619/](http://cdimage.ubuntu.com/daily-live/20140619/), this image is installing perfectly on my machine. No updates after install. Just increment the date before you use the link. Also I suggest you use EXT4 for both Root, USR and Home. I use a separate Boot partition usually 1Gig EXT2. This Dev has been pretty active so don't use it for your main install unless you know your stuff. Good luck!

---

### Post by LastDino on 2014-06-20
Sorry for late reply but reading that much took some time and I'm not used to reading that much on computer screen in one seating >.>

I didn't have a launchpad account, but I got one now.
So, I need to run it on HD to be more useful? Fine. 
My MOBO vendor site says that my last BIOS update is the last released one. So, I should probably be ok on that.
I've downloaded Ubuntu unity 14.10 ISO. I'll have it installed over this weekend. Thank you for your help!

I might need some help on this later though, so I'll keep the thread open just in case.
Thanks again ^^

---

### Post by sudodus on 2014-06-20
Good luck, and welcome back with questions if you need help or someone to discuss with :-)

---

### Post by deadflowr on 2014-06-20
> **LastDino said:**
> Sorry for late reply but reading that much took some time and I'm not used to reading that much in on computer screen in one seating >.>

You'll get extremely used to it.:p

> 
I might need some help on this later though, so I'll keep the thread open just in case.
Thanks again ^^

I'm sure on the way other, more experienced, testers will be more than happy to throw out a tip or two for you.
(Whether you want those tips or not)

---

### Post by LastDino on 2014-06-20
I've got the 14.10 Ubuntu unity installed and it is doing better than what I was expecting. 

One thing is odd though, I'm not able to drag and drop program windows from one workspace  to another. When I try to do this computer screen just hangs as shown in attachment. This is not hardware crash as I'm able to take screen shot in even that situation and when I tried to reproduce the problem, my resources were well below where I would expect a crash.

[ATTACH=CONFIG]254110[/ATTACH]

Or is it not possible and I'm doing something which it is not meant to? I can do this on other Distro's I've right now, like Manjaro and Fedora. If this is indeed a bug, lets get me started on how to track the source and maybe report it if it hasn't been already, shall we? :o

Any and all help is appreciated.

---

### Post by slickymaster on 2014-06-20
> **LastDino said:**
> So, I'm willing to do testing for Xubuntu and Unity (but that would be half hearted as my system is old). 

However, I would like to know few things as I'm only recent Windows migrant. 
Is there any particular format or ''how to'' I need to follow for testing or just installing and using it is enough?
Where to report bugs?
Is there any list of commands or things I might need to know for this?
Is testing in VM fine or you need HD install?

Any other tips coming to mind?

Regarding Xubuntu testing, please go through these links:
[http://xubuntu.org/contribute/qa/](http://xubuntu.org/contribute/qa/)
[Testcases for Xubuntu Desktop i386 in Utopic Daily]("http://iso.qa.ubuntu.com/qatracker/milestones/315/builds/70324/testcases")
[Testcases for Xubuntu Desktop amd64 in Utopic Daily]("http://iso.qa.ubuntu.com/qatracker/milestones/315/builds/70323/testcases")
[Xubuntu Package Testing]("http://packages.qa.ubuntu.com/qatracker/milestones/316/builds/67147/testcases")

---

### Post by LastDino on 2014-06-20
> **slickymaster said:**
> Regarding Xubuntu testing, please go through these links: [http://xubuntu.org/contribute/qa/](http://xubuntu.org/contribute/qa/) [Testcases for Xubuntu Desktop i386 in Utopic Daily]("http://iso.qa.ubuntu.com/qatracker/milestones/315/builds/70324/testcases") [Testcases for Xubuntu Desktop amd64 in Utopic Daily]("http://iso.qa.ubuntu.com/qatracker/milestones/315/builds/70323/testcases") [Xubuntu Package Testing]("http://packages.qa.ubuntu.com/qatracker/milestones/316/builds/67147/testcases")  Thanks! Will have a look at them soon.

---

