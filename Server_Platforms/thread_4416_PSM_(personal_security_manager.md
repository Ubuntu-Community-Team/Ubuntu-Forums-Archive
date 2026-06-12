---
title: "PSM (personal security manager"
date: 2004-11-15
forum: Server Platforms
---

### Post by Dadeeo on 2004-11-15
This is my first attempt to run Linux. I had very good success installing Ubuntu by downloading and burning it toas  an ISO image on CD. I'm having trouble trying to sign in to my verizon.net account and also my hotmail.com account. Attemping to log on to either generates an error prompting me to install PSM. I can't find any step by step instructions on how to do the install.

I also face a problem trying to install Enemy Territory, I click on the ET .run file that I downloaded and I get a huge text file (script?). I tried to run it using the run  command dialog menu and that failed to.

Could someone point me to where I might find step by step instuctions for install new software. This is why I hesitate to run Linux. Windows you just double click the exe file and it loads where ever I point it. I am clueless as Linux seems to NOT use a directory stucture.... :confused:  :confused:  :confused: 

Thanks, Dadeeo

---

### Post by HungSquirrel on 2004-11-15
> **Dadeeo]I'm having trouble trying to sign in to my verizon.net account and also my hotmail.com account. Attemping to log on to either generates an error prompting me to install PSM. I can't find any step by step instructions on how to do the install.[/quote]
Funny, I have had no problems using Firefox with Hotmail.  Anyway, open up the Synaptic Package Manager by clicking the Computer menu and going to System Configuration -> Synaptic Package Manager.  It will ask for your account's password.  Click the Search icon, and enter *mozilla-psm*.  You will get one hit.  Click the checkbox next to the entry, then click the Apply button.  It will tell you that it also needs to install *mozilla-browser*.  Proceed.  The program will download and install two packages.  Once it is finished, it will inform you you can close the window.  Close Synaptic.  Open your Applications menu and go to Internet -> Mozilla Web Browser anytime you need to browse a site that requires PSM.

Note: I don't know for sure if this will fix your problem because I've never had a problem like that.  I am making a few guesses based on a search.  :)

> I also face a problem trying to install Enemy Territory, I click on the ET .run file that I downloaded and I get a huge text file (script?). I tried to run it using the run  command dialog menu and that failed to.
I've never tried to run this installer so I don't know if these instructions are accurate, but I will again make some educated guesses.  :)

Open the Computer menu and click on Home.  A file browser window will pop up.  Browse to wherever you downloaded the .run file (I assume it will be in that folder).  Right-click on the .run file and choose Properties.  Click the Permissions tab.  Make sure the Execute checkbox next to Owner: is checked.  Then try double-clicking on it again.

Edit: it is better to run this installer with root privileges.  To run it as root, right-click on the file, select Open with Other Application..., enter *gksudo*, and press Enter.  When asked for a password, enter your account's password.  (If you couldn't tell, I downloaded ET, and am about to go play.   said:**
> Could someone point me to where I might find step by step instuctions for install new software. This is why I hesitate to run Linux. Windows you just double click the exe file and it loads where ever I point it. I am clueless as Linux seems to NOT use a directory stucture....
One of the problems/features of Linux is there are many different ways to install software, depending on the distribution you use and depending on the software you want to install.  Certain software like Enemy Territory may have its own custom install methods.  However most software you will need in Ubuntu can be installed by searching for it in Synaptic.  To get the most available software, you will have to enable Universe, a larger collection of software.  There are [instructions](http://www.ubuntuforums.org/showthread.php?t=179) for doing so.  After doing that Synaptic will have even more software for you to download.

As far as directory structure goes, you probably don't see the directory structure because your file browser is still in spatial mode.  [Here](http://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-10-07.0184507726) are instructions for turning off this annoying behavior.

I hope I've been a help.  Any more questions, don't hesitate to ask.  It's what we're here for.  :)

Edit: By the way, to play ET you will of course need to enable your 3D drivers.  Follow the instructions depending on your video card manufacturer.

[This page](http://www.ubuntuforums.org/showthread.php?t=3713&highlight=nvidia) has many post-install tasks you might want to do, including enabling Nvidia and ATI drivers.
[This page](http://www.ubuntuforums.org/showthread.php?t=3567) has more detailed ATI instructions.

---

### Post by HiddenWolf on 2004-11-15
Weird problem. I use FF on all kinds of secured sites, and never got asked for PSM, Didn't know it existed, even.

---

### Post by Dadeeo on 2004-11-15
Thanks for the help, found PSM and installed without trouble. Next up, that dang ET install, wish me luck.......

Dad

---

