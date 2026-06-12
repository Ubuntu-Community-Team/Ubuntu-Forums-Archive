---
title: "Your firewall may be blocking access to port @!#*"
date: 2009-04-10
forum: Security
---

### Post by cloudbounce with LED's on 2009-04-10
I'm trying to access some poker games and i get this time out message.

Texas Hold'em Message

Connection Timeout.

The server may be down for maintenance.
 Your firewall may be blocking access to port @!#*

Please email [email]poker_customerservice@zynga.com[/email] if you cannot resolve this issue.

How do I access and change the firewall settings?

---

### Post by lovinglinux on 2009-04-10
Is not a firewall issue. See quote below:

> **bledsoe said:**
> It appears that the problems I was having with the myspace Texas Hold 'Em app are not with dansguardian/tinyproxy/firehol, but may in fact be with the app's developer, [www.zynga.com](www.zynga.com).

Since the app worked fine the first time my son tried it on Ubuntu several weeks ago, and only stopped working after I installed dansguardian/tinyproxy/firehol, I assumed the problem was with dansguardian/tinyproxy/firehol.  Apparently, however, zynga made some change that affects how the app works with Linux systems, so now it won't load at all on my system, even with dansguardian/tinyproxy/firehol disabled.  (I say apparently, because while I found some recent online posts from people complaining about the problem, I can't find anything official from zynga about it.)

Thanks again to those who offered suggestions,

---

### Post by cloudbounce with LED's on 2009-04-10
> **lovinglinux said:**
> Is not a firewall issue. See quote below:

oh that's not good sounds like a dead end.

---

### Post by shawmutt on 2009-04-10
Same issue here.  Zynga made a big announcement about an upgrade, and mine stopped working.  My friends on Windows are playing no problem.

---

### Post by caedes on 2009-04-14
Is it possible for us, linux users, to make an issue of it with Zynga? I enjoy facebook and texas hold em and would love to play with my friends.

---

### Post by hyper_ch on 2009-04-14
yet it still might be a firewall issue also as the OP didn't say it worked before. How do you connect to the internet? Through a router?

---

### Post by cloudbounce with LED's on 2009-04-14
> **hyper_ch said:**
> yet it still might be a firewall issue also as the OP didn't say it worked before. How do you connect to the internet? Through a router?
Yes I use a wireless modem/router to connect to the net.

---

### Post by cloudbounce with LED's on 2009-04-14
> **caedes said:**
> Is it possible for us, linux users, to make an issue of it with Zynga? I enjoy facebook and texas hold em and would love to play with my friends.

I think all you can do is  keep asking the same question to zynga and hope they make an allowance for it in the next major upgrade.

You can play poker at poker palace with your linux OS, of course your mates are on zynga  but at least you can fill in time and feed the addiction ;) .

---

### Post by bluecat9 on 2009-04-16
I found a craptastic work-around for Ubuntu/Zynga Texas HoldEm Players with this loading issue! (stuck at "20")

Go to Adobe's Archive of old flash players: 
[http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=2](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=2)

And download Flash Player 9: 
[http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip)

Extract "fp9_archive.zip" to a known location... (Desktop?)

Open directory "9r159"...

Extract "flashplayer9r159_linux.tar.gz" to a known location...

Extract "install_flash_player_9_linux" to a known location... (*your going to need to install it often so save it somewhere quick to get to like your Desktop)

Open directory "install_flash_player_9_linux" and double-click "flashplayer-installer" then choose "Run in Terminal"... (or install it entirely using the Terminal if you prefer)

...follow the prompts to install the flash player 9 plug-in... (ensure firefox is closed at this time)

Launch Firefox and play! :>

*Note: After you close firefox you will experience the loading issue again! :( In other words, you have to re-install the Flash plug-in every time you want to play Texas HoldEm. (at least in my case) ...and to top it off, no audio. 

Hopefully this will get all of you back in the game! :)

-Justin Oros

---

### Post by cloudbounce with LED's on 2009-04-16
> **bluecat9 said:**
> I found a craptastic work-around for Ubuntu/Zynga Texas HoldEm Players with this loading issue! (stuck at "20")

Go to Adobe's Archive of old flash players: 
[http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=2](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=2)

And download Flash Player 9: 
[http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip)

Extract "fp9_archive.zip" to a known location... (Desktop?)

Open directory "9r159"...

Extract "flashplayer9r159_linux.tar.gz" to a known location...

Extract "install_flash_player_9_linux" to a known location... (*your going to need to install it often so save it somewhere quick to get to like your Desktop)

Open directory "install_flash_player_9_linux" and double-click "flashplayer-installer" then choose "Run in Terminal"... (or install it entirely using the Terminal if you prefer)

...follow the prompts to install the flash player 9 plug-in... (ensure firefox is closed at this time)

Launch Firefox and play! :>

*Note: After you close firefox you will experience the loading issue again! :( In other words, you have to re-install the Flash plug-in every time you want to play Texas HoldEm. (at least in my case) ...and to top it off, no audio. 

Hopefully this will get all of you back in the game! :)

-Justin Oros

 YOU legend!!! 
No sound like you said that's ok.
Tomorrow might be a problem for me when i try to reactivate it. we will see.(I fumbled through it  with your directions but got there in the end)
I was a bit stumped with what a directory is.
Hey thanks for the help

---

### Post by bluecat9 on 2009-04-16
Crazy awesome.

directory = folder.

Glad I could help.

Hopefully Zynga will fix the issue soon...

---

### Post by marguitar on 2009-09-07
found this on zynga forum to get texas working, also try Seamonkey....

 Mimah  Mimah is offline
New to the Forums
	  	
Join Date: Aug 2009
Posts: 1
Mimah is on a distinguished road
Default
I had the same problem and I solved it with this firefox plugin : [http://www.sephiroth.it/firefox/flas...cher/index.php](http://www.sephiroth.it/firefox/flas...cher/index.php)

First you have to uninstall all your flash player versions. Then you install this plugin.

The flash player 10 is not listed but you can add it by copying libflashplayer.so 10 in a new directory 10.0 in $HOME/.mozilla/firefox-3.5/ibwot8ux.default/extensions/flash_switcher@sephiroth.it/plugins/linux

This plugin need to write /usr/lib/firefox-3.5.2/plugins so you have to add write access to this directory to your user.

Sorry for my poor english

---

