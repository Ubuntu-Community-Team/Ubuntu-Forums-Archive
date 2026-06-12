---
title: "Difficult system to install and poor forum support.."
date: 2011-06-03
forum: Testimonials &amp; Experiences
---

### Post by ishueli on 2011-06-03
It is getting to a point where I am seriously thinking of removing linux system from my iMac. This system is not for people who are not computer geeks. I guess Windows 7 and OSX are good enough for people like me.

Even after 7-8 reinstallations I have struggled to get the system working to its full potential. Cant even play any DVD's on the system as plugins don't get loaded. Unable to install VLC , XMBC, RESTRICTED EXTRAS and have to change to wired mouse to work in LINUX while I use wireless mouse in windows & OSX.

It is also difficult to get any support from experts as I believe they are overloaded to fix and respond to the threads. 

It was interesting but quite frustrating time with LINUX.

BYE....

---

### Post by mastablasta on 2011-06-03
well iMac is a closed computer system. you would have more luck running open OS on open hardware system such as a PC for example. it's also being tested more extensivelly on such systems. as a result the install takes about 15 minutes and usually everythign works out of the box or after applying the proprietary drivers.
 
for iMac it would be an interesitng experiment to try one of the FreeBSD distributions as macOS is based on FreeBSD or just BSD i forgot...
 
EDIT: i forgot to say that for faster support you can:
 
1. use IRC channel (FREE)
2. buy yearly support from Canonnical (NOT FREE).

---

### Post by 3rdalbum on 2011-06-03
Your problem is actually quite unique. I think it's got something to do with the Ubuntu mirror you are using. Possibly the mirror is having some troubles at the moment. It's trivially easy to change, fortunately: Go to Ubuntu Software Center and go to Edit > Software Sources.

The popup menu that says "Download From" should be changed to "Main Server", or use the Other... box to find a different mirror.

Close the program. You'll be asked if you want to reload the package list; you do, so click Okay.

And then hey presto, your software installations should work perfectly now.

It's not an Ubuntu problem. It's a problem with the mirror you were using.

---

### Post by jtarin on 2011-06-03
> Difficult system to install and poor forum support..
I guess you could try the other Ubuntu Forum. How about listing your problems one at a tie with details if you seriously want help. Be patient or learn it.

---

### Post by ishueli on 2011-06-03
Dear 3rdalbum,

I did change the source server to " Main Server" however it showed following error 

W:Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/team-xmbc/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/team-xmbc/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/team-xmbc/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/team-xmbc/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Now the source is main server. But still no luck with RESTRICTED EXTRAS & VLC

Regards

---

### Post by ishueli on 2011-06-03
Dear Jtarin,

I did list the issues in the following thread in detail. Somehow I was dumped midway with no further solutions. Hence the decision to go back to the comfort zone. 

[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG] 	 	      		 		 			 			 			 			 			                         [COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[Ubuntu 11.04 on iMac problems...]("http://ubuntuforums.org/showthread.php?t=1773426")

I cant afford to spend hours trying to fix these things as I am a working professional with fairly busy schedule. Trying out new systems is a hobby and hence tried out Linux. I request you to go thru the thread and see if you can propose any solutions.

Regards

---

### Post by Baumbart on 2011-06-03
And why do you not browse the [xbmc directory]("http://ppa.launchpad.net/team-xbmc/") to see which directories are there and which are not?

---

### Post by alphacrucis2 on 2011-06-03
> **ishueli said:**
> Dear 3rdalbum,

I did change the source server to " Main Server" however it showed following error 

W:Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/team-xmbc/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/team-xmbc/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/team-xmbc/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/team-xmbc/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Now the source is main server. But still no luck with RESTRICTED EXTRAS & VLC

Regards

That PPA doesn't have any Natty packages built. You will have to use the Maverick ones until the person maintaining that PPA adds packages for Natty. APT won't install anything as long as those errors exist in your sources.

---

### Post by spynappels on 2011-06-03
> **ishueli said:**
> It is also difficult to get any support from experts as I believe they are overloaded to fix and respond to the threads. 

It was interesting but quite frustrating time with LINUX.

BYE....

We are all volunteering our time here, many of us are also busy professionals who give some of their time to help others, but as Mastablasta pointed out, there is PAID support available from Canonical......

But if Linux is not for you, that's fine too.

---

### Post by collisionystm on 2011-06-03
> **ishueli said:**
> It is getting to a point where I am seriously thinking of removing linux system from my iMac. This system is not for people who are not computer geeks. I guess Windows 7 and OSX are good enough for people like me.

Even after 7-8 reinstallations I have struggled to get the system working to its full potential. Cant even play any DVD's on the system as plugins don't get loaded. Unable to install VLC , XMBC, RESTRICTED EXTRAS and have to change to wired mouse to work in LINUX while I use wireless mouse in windows & OSX.

It is also difficult to get any support from experts as I believe they are overloaded to fix and respond to the threads. 

It was interesting but quite frustrating time with LINUX.

BYE....


May I ask what version of ubuntu you tried to install?

---

### Post by ishueli on 2011-06-03
Ubuntu 11.04

---

### Post by collisionystm on 2011-06-03
When you installed, did you make sure to check the box for install updates and mp3 ? Do that and once the system is up, run update manager to install all of the updates that were downloaded.

---

### Post by ishueli on 2011-06-03
Changing mirror source in software centre did not help much. Instead followed the advise given in the thread below - 

[SOLVED] 			 			[RESTRICTED EXTRAS problem...]("http://ubuntuforums.org/showthread.php?t=1774405")

Resolved issues with Restricted extras and VLC

Bluetooth issue will remain until a solution is found.

---

### Post by pbpersson on 2011-06-03
> **spynappels said:**
> We are all volunteering our time here, many of us are also busy professionals who give some of their time to help others.

Add to that the fact that very few of us have tried to run Ubuntu on Macintosh hardware.

---

### Post by collisionystm on 2011-06-03
> **ishueli said:**
> Changing mirror source in software centre did not help much. Instead followed the advise given in the thread below - 

[SOLVED]                          [RESTRICTED EXTRAS problem...]("http://ubuntuforums.org/showthread.php?t=1774405")

Resolved issues with Restricted extras and VLC

Bluetooth issue will remain until a solution is found.


Install Ubuntu Tweak. Best thing ever.

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by cariboo on 2011-06-04
You may have better luck getting your questions answered in the [Apple Users]("http://ubuntuforums.org/forumdisplay.php?f=328") sub-forum instead of ABT

---

