---
title: "Can't start Funambol for Ubuntu One"
date: 2010-06-14
forum: Ubuntu One (CLOSED)
---

### Post by Ronin51 on 2010-06-14
I recently installed ubuntu 10.04 on two laptops. I am just beginning to get familiar with the OS. Having been a long time Windows user, I'm not familiar with command line functions -- my days of working with DOS commands are far in the past. I say this because I would appreciate any related directions to be very explicit.

My problem: I set up an ubuntu one account and I am trying to use it to sync my contacts using my BB phone. This seemed to be a cool thing to do. I downloaded the 'sync2.jad' for my phone. No apparent problem. Then, following the instructions I downloaded Funambol (8.5.3 for GNU/Linux). Now things got dicey.

Funambol was a bin file and I had no idea what to do with it. (I've become acclimated to just double clicking the file and have it install itself with a little icon on the desktop to launch it - I know, I've gotten soft). Anyway I found enough info to, after a number of tries, get Funambol to apparently install. At least the installation ran in the terminal window and ended with "web demo 8.5.3 installed successfully". 

The instructions on the ubuntu one site are to 'start Funambol' from wherever it is and then adjust the settings etc. I can find no way to 'start' Funamblol. There are no icons, no start menu, .. I'm at a loss. The files are all in a Funambol folder - I just can't make them do anything.

Any help would be appreciated.

---

### Post by smaffulli on 2010-06-14
You don't need to run Funambol server in order to use UbuntuOne sync services: they're two totally unrelated things. You can (and should) remove the Funambol server you just installed (it's in /opt unless you modified the default).

You just need to install the BlackBerry client on your phone and setup your UbuntuOne account on the phone client. That's it. You'll find the instructions to setup your phone here: 
[https://one.ubuntu.com/phones/](https://one.ubuntu.com/phones/)

hth
stef

---

