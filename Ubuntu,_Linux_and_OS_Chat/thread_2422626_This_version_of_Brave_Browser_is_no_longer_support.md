---
title: "This version of Brave Browser is no longer supported - 7-10-2019"
date: 2019-07-10
forum: Ubuntu, Linux and OS Chat
---

### Post by DanPerecky on 2019-07-10
This msg appears when I start the browser now:
This version of Brave is no longer supported and will not be updated.

   When I run Software Updater, Brave is not listed there.

:(

   Thanks.

---

### Post by wildmanne39 on 2019-07-10
From here:
[https://www.ubuntuupdates.org/ppa/brave](https://www.ubuntuupdates.org/ppa/brave)

There is a ppa to install bravo, but it also says the ppa is "discontinued because the Oracle Java download site now requires an Oracle account even for latest Java", so it looks like the maintainer has stopped supporting it, I have never used it so I do not know if it was ever included in the Ubuntu Repositories or not but if it was it is the responsibility of the maintainer to keep it updated and make sure it meets the requirements to stay in the repository so I would not automatically assume Canonical dropped it and for no good reason.

Not a support request so moved to Ubuntu, Linux and OS Chat.

---

### Post by DanPerecky on 2019-07-10
Just to let you know... it was in the Ubuntu Repositories.... I just downloaded it from the Software Boutique tonight.

Oh well..  win some / lose some.

---

### Post by wildmanne39 on 2019-07-10
What version of Ubuntu can you not install it using the repositories then? because all flavors of Ubuntu use the same repositories so you probably need to enable multiverse repository or one of the other ones, then reload the package list.

---

### Post by DanPerecky on 2019-07-10
Wildemanne,
This is ubuntu 18.04.2

Well what happened was that I went to the Software Boutique again.. actually to uninstall it. But Brave wasn't listed there as installed. But it was listed there as an application that I can install. I installed it, and the installation went fine.... I don't get that message any more. Brave is now vrs: [COLOR=#000000][FONT=Muli]Version 0.66.99 Chromium: 75.0.3770.100 (Official Build) (64-bit)

[/FONT][/COLOR]So I guess that something's hokey with the installer?  Dunno... 

But I'm happy that it installed and seems to be working fine now...

---

### Post by wildmanne39 on 2019-07-10
I am to, it could be, I am not currently using ubuntu mate which I like very much, I believe that is the one that has the Software Boutique if I am remembering correctly, enjoy.

---

### Post by deadflowr on 2019-07-10
Brave has it's own archive you can add following the guidance here:
[https://brave-browser.readthedocs.io/en/latest/installing-brave.html#linux]("https://brave-browser.readthedocs.io/en/latest/installing-brave.html#linux")

What you might have is the brave snap package which is community maintained
[https://snapcraft.io/brave]("https://snapcraft.io/brave"))

I'd just remove the snap version and add the brave repo and install that version.

---

