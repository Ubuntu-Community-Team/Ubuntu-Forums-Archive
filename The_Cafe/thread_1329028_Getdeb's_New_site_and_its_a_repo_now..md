---
title: "Getdeb's New site and its a repo now."
date: 2009-11-17
forum: The Cafe
---

### Post by MasterNetra on 2009-11-17
Awesome, just wonder what took them. :p Anywho as many of you may or may not have noticed getdeb.net has been redone and part of their renivations extend to them having the stuff in repo form! Finally no more needing to pluck a new version of gimp from a .deb and reinstall it myself. +1 for laziness. :p **Correction that should be the case once its added to the repo..probably will be when the next version is released x.x **

For those who want the repo and are lazy too: [http://www.getdeb.net/updates/#how_to_install](http://www.getdeb.net/updates/#how_to_install) 

Downloading the .deb and installing is probably the fastest and easiest way to setup the their repo.

---

### Post by earthpigg on 2009-11-17
yay getdeb!

soo, if i enable this repo... will my system always be updated to include the latest and greatest of stuff included in getdeb.net?

i think the result of that would be great:

i could keep the OS itself at Ubuntu LTS, but still have a rolling-release type experience when it comes to userland apps, without needing to use a bunch of different PPAs and whatnot.

my sources.list would be 3 or 4 lines, i would only need to have one or two gpg keys enabled, and the system itself would be stable, and userland apps would be automatically kept super up to date.

:D

---

### Post by phrostbyte on 2009-11-17
Finally a working backports repo. :p

---

### Post by Old Marcus on 2009-11-17
Yet I still have issues connecting to the bleeding site. :(

---

### Post by earthpigg on 2009-11-17
> **Old Marcus said:**
> Yet I still have issues connecting to the bleeding site. :(

i was going to suggest trying to skip the middle man and put the ip address of the website (94.126.144.44) directly in your web browser's address bar... 

...but that doesn't work for that site. odd. just gives a plain white webpage that says "It works!" in large black letters.

same thing when using a different ISP at a different physical location.

---

### Post by SunnyRabbiera on 2009-11-17
Is there still a way to access the .debs outside of the repos though?
GetDeb has a few useful packages I like but I still like the option of manual download if it ever needs to happen.
Like when I want to repackage a .deb into a .rpm

---

### Post by Paqman on 2009-11-17
> **SunnyRabbiera said:**
> Is there still a way to access the .debs outside of the repos though?
GetDeb has a few useful packages I like but I still like the option of manual download if it ever needs to happen.
Like when I want to repackage a .deb into a .rpm

Even if they didn't offer links, you could just grab the .deb from your APT cache.

---

### Post by Naiki Muliaina on 2009-11-17
Cool, thanks for the link! I might stick with an LTS this time round :)

---

### Post by -grubby on 2009-11-17
> **earthpigg said:**
> i was going to suggest trying to skip the middle man and put the ip address of the website (94.126.144.44) directly in your web browser's address bar... 

...but that doesn't work for that site. odd. just gives a plain white webpage that says "It works!" in large black letters.

same thing when using a different ISP at a different physical location.

They're probably using a VirtualHost for getdeb.net, and thus accessing it from the IP just gives the web server's default "there's no virtualhost assigned to this access point!" page (In this case, it seems they're using Apache.)

---

### Post by Nevon on 2009-11-17
Wow, the new design is incredibly ugly. The previous one wasn't the prettiest thing I've ever seen either, but it wasn't nearly as bad as this. :S

---

### Post by jarrah-95 on 2009-11-17
how do i get it to work in 9.10's software center
ive installed the sources.lst line what else do i need to do

---

### Post by Paqman on 2009-11-17
> **jarrah-95 said:**
> how do i get it to work in 9.10's software center
ive installed the sources.lst line what else do i need to do

If you reloaded your sources then you're good to go. If you used Software Sources then it would have prompted you to reload.

---

### Post by aktiwers on 2009-11-17
> **Nevon said:**
> Wow, the new design is incredibly ugly. The previous one wasn't the prettiest thing I've ever seen either, but it wasn't nearly as bad as this. :S

I agree

---

### Post by SunnyRabbiera on 2009-11-17
> **Paqman said:**
> Even if they didn't offer links, you could just grab the .deb from your APT cache.

Yes but thats only useful when you are using a system that uses apt.

---

### Post by The Funkbomb on 2009-11-17
How safe are packages from getdeb?

---

### Post by SunnyRabbiera on 2009-11-17
> **The Funkbomb said:**
> How safe are packages from getdeb?

Pretty safe, never had issues with it.

---

### Post by MasterNetra on 2009-11-17
Sadly it seems a lot of the lastest stuff that was in the old one hasn't been imported (such as gimp) but luckly you can still access the old site. They have a link to it somewhere. Hopefully it will fill out more before Lucid is out.

---

### Post by Praxicoide on 2009-11-17
This is for Karmic only, correct?

---

### Post by Excedio on 2009-11-17
> **MasterNetra said:**
> *snip*They have a link to it somewhere.*snip*
 
[http://old.getdeb.net/](http://old.getdeb.net/)
 
> **Praxicoide said:**
> This is for Karmic only, correct?
 
Karmic & Jaunty

---

### Post by MasterNetra on 2009-11-17
> **excedio said:**
> [http://old.getdeb.net/](http://old.getdeb.net/)
 

 
karmic & jaunty

+1

---

### Post by Excedio on 2009-11-17
Is anyone else noticing that the new site is broken in IE? The tables are all off.

---

### Post by MasterNetra on 2009-11-17
> **Excedio said:**
> Is anyone else noticing that the new site is broken in IE? The tables are all off.

The designers probably didn't even consider IE and why should they its a site meant strictly for Linux and why would anyone using Linux want to use IE other then for testing?

---

### Post by Excedio on 2009-11-17
> **MasterNetra said:**
> The designers probably didn't even consider IE and why should they its a site meant strictly for Linux and why would anyone using Linux want to use IE other then for testing?
 
Maybe because there are people like me that want to search for an application while at work (where I am locked in to using Windows - Not complaining, just stating fact) and then email myself at home with the direct link instead of searching for it again. :-D

---

### Post by Old Marcus on 2009-11-17
Both url and ip address don't work for me. This is seriously weird. time to check router settings for any weird settings. Any other advice would be good. :)

---

### Post by MasterNetra on 2009-11-17
> **Excedio said:**
> Maybe because there are people like me that want to search for an application while at work (where I am locked in to using Windows - Not complaining, just stating fact) and then email myself at home with the direct link instead of searching for it again. :-D

Use firefox :p Or try to get the boss to allow you to install firefox or something.

---

### Post by earthpigg on 2009-11-18
> **MasterNetra said:**
> Use firefox :p Or try to get the boss to allow you to install firefox or something.

better question than that...

what version of IE are you forced to be using at work?

if IE 6, then it is known to intentionally ***not*** to be standards compliant. it would be ridiculous amounts of extra work on the part of getdeb.net's people to make the website render properly on non-standards-compliant web browsers.

---

### Post by Excedio on 2009-11-18
> **MasterNetra said:**
> Use firefox :p Or try to get the boss to allow you to install firefox or something.
 
Not going to happen (as much as I would like it to). I've fought for months to get Firefox back on my work station but the engineering department has officially banned it on any workstation that runs our "platform."
 
Mirial PSE Video Contact Center. I do Technical Support for deaf customer's that use our Video Relay Services for phone calls. Engineering has tested the "platform" in Firefox (All Versions :-( ) and the stress test was too great for them to allow us to use it.
 
Believe me when I say that our engineering team is not against Firefox in any way. They are the ones that turned me on to Open Source Software and on to Ubuntu. All of our servers run Linux except for the Exchange Server...oh and one Apple Server for the marketing department. :-)
 
> **earthpigg said:**
> better question than that...
 
what version of IE are you forced to be using at work?
*snip*
 
IE 7

---

### Post by MasterNetra on 2009-11-18
> **Excedio said:**
> Not going to happen (as much as I would like it to). I've fought for months to get Firefox back on my work station but the engineering department has officially banned it on any workstation that runs our "platform."
 
Mirial PSE Video Contact Center. I do Technical Support for deaf customer's that use our Video Relay Services for phone calls. Engineering has tested the "platform" in Firefox (All Versions :-( ) and the stress test was too great for them to allow us to use it.
 
Believe me when I say that our engineering team is not against Firefox in any way. They are the ones that turned me on to Open Source Software and on to Ubuntu. All of our servers run Linux except for the Exchange Server...oh and one Apple Server for the marketing department. :-)
 

 
IE 7

hmm I see what you mean about the tables in the apps. I have IE7 installed via PlayonLinux and IE7 doesn't seem to like that area too much. Idk how it fares under IE8 though.

---

### Post by Excedio on 2009-11-18
Couldn't tell you either. Not allowed to get that either since it has not been tested with the platform.

---

### Post by aktiwers on 2009-11-18
Everythings broken i IE

---

### Post by steeleyuk on 2009-11-18
Another small issue with the site... the dropdown menus to filter by distribution and genre don't work if JavaScript is disabled. Might be worth adding a 'Go' button next to them, similar to these forums.

<small point>I'll send them a message if they don't see this.</small point> :)

---

### Post by MasterNetra on 2009-11-18
> **steeleyuk said:**
> Another small issue with the site... the dropdown menus to filter by distribution and genre don't work if JavaScript is disabled. Might be worth adding a 'Go' button next to them, similar to these forums.

<small point>I'll send them a message if they don't see this.</small point> :)

And they probably won't see this. :/

---

