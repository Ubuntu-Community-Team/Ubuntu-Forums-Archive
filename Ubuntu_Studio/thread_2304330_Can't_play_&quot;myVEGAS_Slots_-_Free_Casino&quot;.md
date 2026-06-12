---
title: "Can't play &quot;myVEGAS Slots - Free Casino&quot; in Firefox."
date: 2015-11-26
forum: Ubuntu Studio
---

### Post by sethanath2 on 2015-11-26
Hi,

I am using Ubuntu Studio 14.04 with the most recent version of Firefox.
However, it is a requirement to use the most recent version of Flash Player in order to play "myVEGAS Slots - Free Casino", a facebook game, in Firefox.

Chrome has a Flash Player built in, so I can play this game with no problem. I wonder if anyone knows how to fix this problem in Firefox.

Thank you.

---

### Post by ajgreeny on 2015-11-26
I don't know how you installed flash for FF but to use the latest flash version, 19.0.0.245, you need to install the **adobe-flashplugin** package from the canonical-partner repos, not the **flashplugin-installer** which gets you version 11.2.2.548 only.
You also need to enable the **nilaromogard-webupd8** ppa repos to get freshplayerplugin which allows FF to use the ppapi flash plugin
See [https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8](https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8) for all details.

Alternatively you could try using chromium instead of FF or google-chrome, which uses the flash version 19.0.0.245, like chrome, provided you have the adobe-flashplugin package installed.

---

### Post by sethanath2 on 2015-11-26
> **ajgreeny said:**
> I don't know how you installed flash for FF but to use the latest flash version, 19.0.0.245, you need to install the **adobe-flashplugin** package from the canonical-partner repos, not the **flashplugin-installer** which gets you version 11.2.2.548 only.
You also need to enable the **nilaromogard-webupd8** ppa repos to get freshplayerplugin which allows FF to use the ppapi flash plugin
See [https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8](https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8) for all details.

Alternatively you could try using chromium instead of FF or google-chrome, which uses the flash version 19.0.0.245, like chrome, provided you have the adobe-flashplugin package installed.

Hi,

Thank you very much for helping me. It works. 
Here are the steps that I found further from the internet.

The main problem in this situation is outdated version of Flash Player in Firefox.
In the same time, Google Chrome users enjoying latest version supported by Google.

  The trick is to switch  Firefox from using it's Flash Player to Pepper Flash Player from Google Chrome.
  
[LIST=1]
[*]First of all lets remove that we have:
  [INDENT]   sudo apt-get remove flashplugin-installer
  sudo apt-get remove adobe-flashplugin
 [/INDENT]
[*]Install Fresh Player Plugin by [Rinat Ibragimov]("https://github.com/i-rinat").
It is wrapper which allows Linux users to use Pepper Flash (which is  bundled with Google Chrome) in Firefox and other NPAPI-compatible web  browsers.
Latest version at this moment is 0.3.1, and everything seems working.
  [INDENT]   sudo add-apt-repository ppa:nilarimogard/webupd8
  sudo apt-get update
  sudo apt-get install freshplayerplugin
 [/INDENT]
[*]Install Pepper Flash Player itself from Google Chrome Stable:
  [INDENT]   sudo apt-get install pepperflashplugin-nonfree
  sudo update-pepperflashplugin-nonfree --install
 [/INDENT]
[/LIST]

---

### Post by ajgreeny on 2015-11-26
Great!  Good to know it is now working for you.

I am almost sure you don't need the pepperflashplugin-nonfree any more, as the adobe-flashplugin now takes its place, whereas the flashplugin-installer package did not.  I no longer have the pepperflashplugin-nonfree installed, just the adobe-flashplugin and freshplayerplugin and I have flash 19.0.0.245 in both chromium and firefox.

Please mark as SOLVED from then Thread Tools menu at the top.

---

