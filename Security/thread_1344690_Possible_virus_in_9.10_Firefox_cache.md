---
title: "Possible virus in 9.10 Firefox cache"
date: 2009-12-03
forum: Security
---

### Post by bwallum on 2009-12-03
Hi

I've just had my first ever virus alert in Ubuntu. It appears to be a Firefox exploit that comes via a spoof email through evolution.

Virus Scanner detects a PUA virus in /home/.mozilla/firefox/cache

Remevoal is easy, just delete the cache file (it will regenerate when FF is loaded again). Make sure to empty your deleted items folder afterwards.

What may be interesting is that the infection comes via a spoof email, in my case from BT, and connection to the spoof website pops a virus into the FF cache.

Any body else getting these? Any other effects I should be aware of?

---

### Post by Grenage on 2009-12-03
If evolution is rendering html data through firefox, then that's not surprising.  The file won't be able to do anything, however.

---

### Post by rookcifer on 2009-12-04
> **bwallum said:**
> Hi

I've just had my first ever virus alert in Ubuntu. It appears to be a Firefox exploit that comes via a spoof email through evolution.

Virus Scanner detects a PUA virus in /home/.mozilla/firefox/cache

Remevoal is easy, just delete the cache file (it will regenerate when FF is loaded again). Make sure to empty your deleted items folder afterwards.

What may be interesting is that the infection comes via a spoof email, in my case from BT, and connection to the spoof website pops a virus into the FF cache.

Any body else getting these? Any other effects I should be aware of?

It's most likely a Windows virus that is being picked up by ClamAV (or whatever virus scanner you are using).  Remember these virus scanners are really only good for picking up Windows viruses, which is why I think they are worthless on Linux (unless you are running a mail server or something of that sort).  

So what you are seeing is probably a Windows virus attacking Firefox, as they will attempt the same exploit no matter the OS.  However, as the above poster said, it wont be able to do anything to Firefox on Linux.

---

### Post by bwallum on 2009-12-04
Thanks guys,

It was ClamAV that picked it up and I'm pretty sure it is a Windows virus. Always best to stay alert...It did appear to make FF hesitate a bit until I removed it. No other effects noticed. All running fine, quite exciting really, my very first virus running Ubuntu, albeit a neutered Windows virus in Firefox.

Have there ever been any real linux viruses?

---

### Post by cariboo on 2009-12-04
There are quite a few Linux viruses, but none in the wild so far. Have a look at this Wikipedia [article]("http://en.wikipedia.org/wiki/Linux_malware").

---

### Post by bodhi.zazen on 2009-12-04
> **bwallum said:**
> Have there ever been any real linux viruses?

To date the Linux viruses have been "proof of concept" and your system has been patched long ago so you are not vulnerable to any of the known Linux viruses.

See : [Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by OpSecShellshock on 2009-12-04
Also, "PUA" stands for potentially-unwanted application. It's a category that is used to describe things that you might not want, like adware, that you have nonetheless agreed to a EULA for. It also sometimes describes remote administration utilities. The reason these get flagged as "potentially" unwanted is because sometimes users do, in fact, want them, and also because the AV companies are afraid of legal consequences that might arise from outright calling something malware when the user is the one who installed it and the people who made it are trying to pass it off as legitimate (regardless of how shady its behavior is).

---

### Post by bwallum on 2009-12-07
> **OpSecShellshock said:**
> Also, "PUA" stands for potentially-unwanted application. It's a category that is used to describe things that you might not want, like adware, that you have nonetheless agreed to a EULA for. It also sometimes describes remote administration utilities. The reason these get flagged as "potentially" unwanted is because sometimes users do, in fact, want them, and also because the AV companies are afraid of legal consequences that might arise from outright calling something malware when the user is the one who installed it and the people who made it are trying to pass it off as legitimate (regardless of how shady its behavior is).

Thanks for that, nice to know what a PUA is. In my case the PUA loaded itself into the FF cache when I browsed to the infected web site, without any alerts or requests. The spoof email showed a link to [http://www.bt.com/email/login](http://www.bt.com/email/login) , a link that on the face of it looks legit. However it linked to 

[http://wsxzaq.1tbhost.info/bettupdtahghshnfg/bbttinde.html](http://wsxzaq.1tbhost.info/bettupdtahghshnfg/bbttinde.html) THE VIRUS INFECTED WEBSITE

Please don't click on the above unless you are confident that you can handle viruses, it may or may not still be alive. BT have been alerted.

Fifefox displays the actual address (bottom left) when hovering the mouse pointer over the visible link. It would be good to do this as a tool tip (as well) in Evolution to make it more visible and better alert to a spoof link IMO.

Thanks also to cariboo907 for the excellent Linux virus link:
[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

I'm convinced that linux is so much safer in a virus ridden cyber world. Thanks for all the contributions.

---

