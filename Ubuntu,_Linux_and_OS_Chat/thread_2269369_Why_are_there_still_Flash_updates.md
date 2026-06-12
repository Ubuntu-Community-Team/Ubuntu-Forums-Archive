---
title: "Why are there still Flash updates?"
date: 2015-03-15
forum: Ubuntu, Linux and OS Chat
---

### Post by mtfr on 2015-03-15
As far as I know, Flash on Linux has been abandoned for quite some time now by Adobe. But I regularly get updates for the package, although the main version seems to stay 11.2. I'm just curious, if it's just a binary blob, what do the frequent updates do?

---

### Post by buzzingrobot on 2015-03-15
Adobe releases security patches for its Flash-for-Linux version. It's not abandoned, but gets no new features, just security fixes. You'll notice that the version number does change.

---

### Post by craig10x on 2015-03-15
Flash on Linux isn't dead if you use Google Chrome as your browser on linux since they have an agreement with adobe to provide the latest flash versions for their pepper flash plug in...
The very old version of flash, which is what ubuntu restricted extras installs (the last general flash adobe supplied for linux) only get security updates...not new versions...
Flash is hardly dead yet as many sites still use it and you couldn't listen to stream radio without it, for example...

---

### Post by monkeybrain20122 on 2015-03-15
> **craig10x said:**
> 
Flash is hardly dead yet as many sites still use it and you couldn't listen to stream radio without it, for example...

But you you don't need the latest flash for that. 11.2 is usually good.

---

### Post by thiebaude on 2015-03-16
+1

---

### Post by rose61 on 2015-03-18
[COLOR=#000000]The very old version of flash, which is what ubuntu restricted extras installs (the last general flash adobe supplied for linux) only get security updates...





_______________________________
[/COLOR][TABLE="width: 64"]
[TR]
  [TD="width: 64"]:*RosE*:[/TD]
[/TR]
[/TABLE]

---

### Post by mattharris4 on 2015-03-20
> **craig10x said:**
> Flash on Linux isn't dead if you use Google Chrome as your browser on linux since they have an agreement with adobe to provide the latest flash versions for their pepper flash plug in...
The very old version of flash, which is what ubuntu restricted extras installs (the last general flash adobe supplied for linux) only get security updates...not new versions...
Flash is hardly dead yet as many sites still use it and you couldn't listen to stream radio without it, for example...

Some Linux programmers keep up a Flash-like program called Pepper Flash that works in Chromium and Firefox.  Either install at the terminal or search for Pepper Flash in the Ubuntu Software Center and install it.  Update it once a month or so, Update instructions are here (please note that Pepper Flash now works in Firefox no matter what the article claims):  [http://www.howtogeek.com/193876/using-firefox-on-linux-your-flash-player-is-old-and-outdated/](http://www.howtogeek.com/193876/using-firefox-on-linux-your-flash-player-is-old-and-outdated/)

---

### Post by mattharris4 on 2015-03-20
^ Please note that you must be root to update or install Pepper Flash.  Here are the commands from a terminal:  

Check for update:  **sudo update-pepperflashplugin-nonfree --status**
Install update:  **sudo update-pepperflashplugin-nonfree --install**
Install for first time:  Search for and install Pepper Flash from Ubuntu Software Center, do not use the terminal.

Please type in sudo commands exactly, even one dash missing will cause it to not install although it may cause a list of commands to appear on the screen to put sudo in front of and then copy/paste.  Word misspellings may crash your system and ruin your Ubuntu installation.

---

### Post by deadflowr on 2015-03-20
> **mattharris4 said:**
> Some Linux programmers keep up a Flash-like program called Pepper Flash that works in Chromium and Firefox.  Either install at the terminal or search for Pepper Flash in the Ubuntu Software Center and install it.  Update it once a month or so, Update instructions are here (please note that Pepper Flash now works in Firefox no matter what the article claims):  [http://www.howtogeek.com/193876/using-firefox-on-linux-your-flash-player-is-old-and-outdated/](http://www.howtogeek.com/193876/using-firefox-on-linux-your-flash-player-is-old-and-outdated/)

Pepperflash IS flash.
It is not flash-like.
pepperflash refers to the pepper plugin api(ppapi) Google-Chrome/chromium use, versus the old netscape plugin api(npapi), mozilla and others use/used.

It's a proprietary set-up between google (Per Google-Chrome, and not chromium) and adobe.
Google-Chrome comes with the pepperflash plugin built in.
Chromium does not.
But...
Ubuntu developers created a method where it downloads the chrome package and then only extracts the pepperflash plugin to install on your system.
Thus letting non-Google-Chrome apps, like chromium, to use it.

Last I remember firefox developers(or *a* firefox developer) developed an extention/add-on called freshplayer that allowed you to run the pepperflash plugin, which would otherwise not run, because firefox did not have ppapi support, natively. (I still think it doesn't have native ppapi support, but I sometimes feel out of the loop when ever I blink)

---

### Post by craig10x on 2015-03-21
@deadflowr: Exactly. pepperflash is simply adobe flash that works in a plug in on Google Chrome...Google has a deal with adobe to provide the latest versions of flash for ALL versions of Chrome (including the linux one) and it gets all the updates too (usually in newer versions of Chrome which is frequently updated anyway)... When one uses firefox, you are using the old adobe flash plug in that ubuntu restricted extras installs...which only gets security updates in linux but no new versions...that version is over 2 years old now...

And as you said, Chrome has it already built in...no need to add it like in Chromium! ;)

---

### Post by monkeybrain20122 on 2015-03-22
> **deadflowr said:**
> 

Last I remember firefox developers(or *a* firefox developer) developed an extention/add-on called freshplayer that allowed you to run the pepperflash plugin, which would otherwise not run, because firefox did not have ppapi support, natively. (I still think it doesn't have native ppapi support, but I sometimes feel out of the loop when ever I blink)

Not a Firefox developer. He is the guy who made libvdpau-va-gl (lets you use vdpau on intel machines, an outdated version is available in the repo as libvdpau-va-gl1) [https://github.com/i-rinat/freshplayerplugin](https://github.com/i-rinat/freshplayerplugin) Freshplayerplugin is a wrapper for pepper flash, which you can get by either installing Chrome or the version of pepper flash in the Software Centre meant for Chromium (which is not up to date I think) I am using it on Fedora. It actually works rather seamlessly for  normal  videos and audios streaming, can't tell the difference from native flash 11.2.

It is quite easy to compile from source but on Ubuntu you can install from webupd8's ppa [http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html](http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html)

---

### Post by Tar_Ni on 2015-03-23
> **craig10x said:**
> Flash on Linux isn't dead if you use Google Chrome as your browser on linux since they have an agreement with adobe to provide the latest flash versions for their pepper flash plug in...
The very old version of flash, which is what ubuntu restricted extras installs (the last general flash adobe supplied for linux) only get security updates...not new versions...
Flash is hardly dead yet as many sites still use it and you couldn't listen to stream radio without it, for example...

But not everyone wants to use Google Chrome. The fact that we are almost been held in hostage to use a Google's sponsored browser in order to use flash on Linux is quite concerning. Firefox has always been my browser of choice and that's not about to change.

That being said, the Flash 11.2 plugin still works well on the majority of websites. It is still updated with security up to 2017. Until then, chances are HTML5 will be standard for most streaming services (it's already the case on Youtube, Dailymotion, Vimeo and soon on Netflix) and at that point Mozilla might be very close to deploy Shumway, which would put the final nail on the Adobe flash coffin.

There is always the peperflash wrapper that can be used, I've never tried it yet but this looks like good alternative if Flash 11.2 should become obsolete in too many places before 2017.

---

### Post by mattharris4 on 2015-03-23
> **deadflowr said:**
> Pepperflash IS flash.
It is not flash-like.
pepperflash refers to the pepper plugin api(ppapi) Google-Chrome/chromium use, versus the old netscape plugin api(npapi), mozilla and others use/used.

It's a proprietary set-up between google (Per Google-Chrome, and not chromium) and adobe.
Google-Chrome comes with the pepperflash plugin built in.
Chromium does not.
But...
Ubuntu developers created a method where it downloads the chrome package and then only extracts the pepperflash plugin to install on your system.
Thus letting non-Google-Chrome apps, like chromium, to use it.

Last I remember firefox developers(or *a* firefox developer) developed an extention/add-on called freshplayer that allowed you to run the pepperflash plugin, which would otherwise not run, because firefox did not have ppapi support, natively. (I still think it doesn't have native ppapi support, but I sometimes feel out of the loop when ever I blink)

Thank you for the explanation.  As I am not a computer programmer I don't know all of the nuances of programming.  Also, I don't recall installing anything called Freshplayer but I suppose it is possible the Ubuntu or Firefox programmers have set it up so it installs along with Pepper Flash if it detects a Firefox installation.  I also do not have Freshplayer listed in the list of plug-ins on my computer but again it might be bundled with Pepper Flash, I don't know -- that is probably a question for a programmer working at Canonical, Mozilla or otherwise involved in its maintenance (I am sure deadflowr knows this but for others reading not all Ubuntu developers are on the Canonical payroll and the same is true for Firefox developers and Mozilla payroll, many people around the world volunteer their time helping maintain the OS, Firefox and Linux in general).  I am not doubting you, I am just stating what I have found since reading your post and maybe me posting that info here will help someone along the way.

---

### Post by monkeybrain20122 on 2015-03-24
> **mattharris4 said:**
> Thank you for the explanation.  As I am not a computer programmer I don't know all of the nuances of programming.  Also, I don't recall installing anything called Freshplayer but I suppose it is possible the Ubuntu or Firefox programmers have set it up so it installs along with Pepper Flash if it detects a Firefox installation.  I also do not have Freshplayer listed in the list of plug-ins on my computer but again it might be bundled with Pepper Flash, I don't know -- that is probably a question for a programmer working at Canonical, Mozilla or otherwise involved in its maintenance (I am sure deadflowr knows this but for others reading not all Ubuntu developers are on the Canonical payroll and the same is true for Firefox developers and Mozilla payroll, many people around the world volunteer their time helping maintain the OS, Firefox and Linux in general).  I am not doubting you, I am just stating what I have found since reading your post and maybe me posting that info here will help someone along the way.


Freshplayer is not in the repository and it is not installed along with pepper flash. You have to install it from a ppa. [http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html](http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html) 

Your flash update is just security update and if you check its version it is still 11.2. If you have freshplayer Firefox's addons > plugins tab should show flash 17

---

