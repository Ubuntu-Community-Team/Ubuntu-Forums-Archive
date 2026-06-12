---
title: "HELP! CE convert script messed up my internet"
date: 2006-10-13
forum: Ubuntu Christian Edition
---

### Post by The Digital Pioneer on 2006-10-13
OK, this is REALLY bad. I used the converter script on Kubuntu, and now my internet is VERY weird. Something is blocking my web connections, but selectively. For example: I can get to Gmail (only it I open Firefox to that URL) but not Google. I have found two sites I can get to, which is not good. There's a lot of web out there that needs surfing! ;) Anyways, I've uninstalled dansguardian and tinyproxy, but there's still more in my way. Please help, I REALLY don't want to have to reinstall Kubuntu....

For all those out there who want to use the script on Kubuntu: don't. It does weird stuff with your web.

Thanks in advance,

The Digital Pioneer

---

### Post by meng on 2006-10-14
Please, please let the dev/maintainer know about this if you haven't done so already. It's important for them to understand these issues. I share your concerns regarding the maturity of this product, which is just one reason why I have no interest in using it. Sorry I can't help you solve your problem though...

---

### Post by Iandefor on 2006-10-14
I would talk to a moderator and see about getting this moved to the Ubuntu Christian Edition forum; It's much more likely you'll be able to get help there.

Oh, and I believe that Ubuntu CE is primarily for Ubuntu (Not Kubuntu). If you're interested in a Kubuntu-based alternative, I would recommend [Icthux.]("http://www.ichthux.com/")

Good luck.

---

### Post by The Digital Pioneer on 2006-10-14
Hey, folks, not that I don't appreciate the advice and all, but it's too late to tell me it was designed for Ubuntu and not Kubuntu. I'm a  little past that point. ;)

Also, I've been looking for a way to contact the devs for days. Where is it???? I'd love to get them, but *how?*

---

### Post by meng on 2006-10-14
You could post in the Ubuntu Christian Edition subforum on this site, or else go to
[http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/about-ubuntu-christian-edition.html](http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/about-ubuntu-christian-edition.html)
although I couldn't find an email address here. The main dude here is mhancoc7, I guess you could try PM also.
Although I have nothing to do with it, I'm really sorry to hear you had trouble getting in touch with the developer on this. The project really needs more support and better communications if it's going to bill itself as a proper distro.

---

### Post by The Digital Pioneer on 2006-10-14
OK, I don't suppose there's any mods here who would like to move this topic...?

---

### Post by meng on 2006-10-14
As you know (although many others don't seem to know it), double posting is generally frowned upon. However, if the mods haven't moved it by now, I can't see there would be any objection if you re-posted in the appropriate forum ...

---

### Post by PriceChild on 2006-10-14
*moved to Christian Edition forum*

Don't be afraid to pm an online staff member if you would like threads moved or renamed :)

---

### Post by The Digital Pioneer on 2006-10-14
PriceChild: Thanks.
Meng: Obviously I have no clue what double-posting is.
Regulars to this forum: HELP!!!

---

### Post by mysticrider92 on 2006-10-14
I don't know what to tell you about the internet, but you should tell mhancoc7 about it.

---

### Post by tonhou on 2006-10-14
I suggest you do this to get internet functioning:

1.Open a terminal (System --> Konsole)

2. Type in:

*sudo apt-get --purge remove dansguardian *
(will prompt for password)
*sudo apt-get --purge remove firehol*
*sudo apt-get --purge remove tinyproxy*
*sudo apt-get --purge remove clamav*

Which script did you use - there are a few options?
As pointed out above these are only for Ubuntu.

Hope you get things straightened out.

--Tony

---

### Post by The Digital Pioneer on 2006-10-14
HALLELUJAH!!!!

Tonhou, I cannot thank you enough! You have saved my internet!!! I was pretty sure a firewall got installed, but couldn't find its name. Firehol was the culprit. A purge and reboot later, MOST of my internet is back...

Odd though, I can browse any site (as far as I've seen, haven't tried all of them) but a plugin I use called Google Browser Sync (Firefox) cannot connect. Any time it tries, I see a connection error. Think this might be related to CE?...

Other than that, I think everything gets internet just fine. Thanks again! :D

---

### Post by tonhou on 2006-10-14
If you continue to have issues with firefox I would remove it:

*sudo apt-get --purge remove firefox*

The "--purge" will take out the configuration files which are locked with the Ubuntu CE script which may be causing the problems. It may also take out your plugins!

Then reinstall:

*sudo apt-get install firefox*

--Tony

---

### Post by montgoej on 2006-10-15
Ok, I've had this happen after removing clamAV, firehol, and tinyproxy.  what it was for me was the locked proxy settings in firefox. I did an apt-get remove firefox and then an apt-get install firefox, then just changed the proxy settings, which weren't locked after the re-install, and all of my bookmarks, plugins, etc were there when it re-installed. 
~Jordan Montgomery

---

### Post by mhancoc7 on 2006-10-15
> **The Digital Pioneer said:**
> HALLELUJAH!!!!

Tonhou, I cannot thank you enough! You have saved my internet!!! I was pretty sure a firewall got installed, but couldn't find its name. Firehol was the culprit. A purge and reboot later, MOST of my internet is back...

Odd though, I can browse any site (as far as I've seen, haven't tried all of them) but a plugin I use called Google Browser Sync (Firefox) cannot connect. Any time it tries, I see a connection error. Think this might be related to CE?...

Other than that, I think everything gets internet just fine. Thanks again! :D

I sincerly apologize that I did not see this post sooner. I try very hard to keep up with posts about Ubuntu CE that are outside our subforum, but it can be quite challenging. I do a daily check of the "official" Ubuntu CE forums. 

I am sorry that you had trouble with the script. It was designed primarily for Ubuntu. You may have noticed that on the download page. There have been reports of getting the scripts to work on Kubuntu as well as Mepis, but these are untested and unsupported. I am glad to hear that Tony was able to help you.

Again, I am very sorry that I did not see this sooner.

God Bless, Jereme

---

### Post by mhancoc7 on 2006-10-15
> **meng said:**
> The project really needs more support and better communications if it's going to bill itself as a proper distro.

Well, I am sorry that you feel that we are not offering enough support. However, I think most would disagree. I try very hard, but when things get posted outside of this sub-forum or the [Ubuntu CE Development Forum]("http://forums.churchforge.net/index.php?c=7"), it can be hard to catch. This one slipped past me, but that is not the norm.

God Bless, Jereme

---

