---
title: "Help, internet not working"
date: 2011-04-08
forum: Security
---

### Post by ChuckT on 2011-04-08
Hi there

A few days ago, I somehow managed to install tor and vidalia with privoxy and polipo, following various instructions found on the web (yes, I'm a noob). So it was running fairly well, I could change my settings to use localhost 8118 when I wanted to browse through tor and change them back to direct internet connection when I wanted to browse normally.

Earlier today, I restarted my computer, and I found I could not access the internet the normal way, and vidalia would not start tor for some reason. So I uninstalled tor, vidalia and all the other stuff, using apt-get remove, but I still couldn't access the internet. So... I reinstalled everything again, and then I managed to connect to the internet via tor, but still no luck without it.

Is there a program running in the background that prevents me from connecting directly to the internet (polipo? privoxy?) that I can kill, stop, configure, whatever? And how can I do that? 

I need help connecting to the internet the normal way...

Thanks!

---

### Post by Carterclan on 2011-04-09
Pretty sure of 1 thing only and that is that you should not be using both polipo and privoxy together as they are both set to use the same port ( 8118 ). Whether that is what is causing your problems I don't know needs some one more knowledgable than me

---

### Post by wacky_sung on 2011-04-09
First of all, check the menu under System -> Network Proxy that is it direct connected to the internet.

FYI : Polipo cannot handle too many tabs / difference browsers open at the same times beside that lately i discovered Privoxy always tend to slow and often having conflict with proxy server. :(

---

### Post by SofiaBrown on 2011-04-19
Internet is not working due to following reasons:
    * Internet or network problem after removing adware, spyware, virus, worm, Trojan horse, etc.
    * Loss network connection after installing/uninstalling adware, spyware, antispam, vpn, firewall or other networking programs.
    * Unable to access any webpage or can only access some webpages.
    * Pop-up error window with network related problem description.
    * No network connectivity due to registry errors.
    * DNS lookup problem.
    * Fail to renew the network adapter’s IP address or other DHCP errors.
    * Network connectivity issue with limited or no connections message.
    * Windows update does not work
    * You are having problems connecting to secured websites (ex. Banking).
    * Internet Explorer stopped working or crashes all the time.
    * Other networking problems.

---

