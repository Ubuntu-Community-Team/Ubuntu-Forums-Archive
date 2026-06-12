---
title: "New CE user"
date: 2007-04-19
forum: Ubuntu Christian Edition
---

### Post by BrookShadow_RC on 2007-04-19
Hello all, 

I am a new CE user, and for that matter, a newcomer to Ubuntu. I am a huge FreeBSD user and Fedora/Red Hat user. So far, I have just installed CE as a test and it looks and feels nice. But, I have a few issues so far that I'm hoping that this forum and its members will be able to help me "fix". 

1. I have installed at work, which is behind a proxy server. (Bluecoat to be exact) I have been able to add the proxy URL to Firefox, but every time Firefox is closed, when I reopen, the proxy setting has been forgotten. How to fix?

2. There seems to be no ssh daemon running. Do I need to install one? Why was this not included? 

3. The DansGuardian GUI, is this the new standard across all *nix platforms, or is this a Unbuntu specialty? (I'm new to DansGuardian... and impressed!)

4. Wireless support? Anyone using with wireless cards and if so, which ones?

Thanks to all in advance. I look forward to being part of the CE community. 

Ron

---

### Post by tak1150 on 2007-04-19
> **BrookShadow_RC said:**
> Hello all, 

I am a new CE user, and for that matter, a newcomer to Ubuntu. I am a huge FreeBSD user and Fedora/Red Hat user. So far, I have just installed CE as a test and it looks and feels nice. But, I have a few issues so far that I'm hoping that this forum and its members will be able to help me "fix". 

1. I have installed at work, which is behind a proxy server. (Bluecoat to be exact) I have been able to add the proxy URL to Firefox, but every time Firefox is closed, when I reopen, the proxy setting has been forgotten. How to fix?


I bet this is because the firefox proxy is locked by DansGuardian (there is an option to turn the lock off)

> 
2. There seems to be no ssh daemon running. Do I need to install one? Why was this not included? 


See [http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy") for ssh installation.

> 
3. The DansGuardian GUI, is this the new standard across all *nix platforms, or is this a Unbuntu specialty? (I'm new to DansGuardian... and impressed!)

It's just for CE of Ubuntu.

> 
4. Wireless support? Anyone using with wireless cards and if so, which ones?

I've found that Atheros have good support for linux and my atheros card works pretty well (out-of-the-box).

> 
Thanks to all in advance. I look forward to being part of the CE community. 

Ron


I'm glad you've joined us. God bless,
Tak

---

### Post by BrookShadow_RC on 2007-04-20
Tak, 

Thanks for the responses. As far as the browser settings go, I have the browser unlocked, so I can add the company's proxy url into it and get out to the Internet. Part of my troubleshooting was to tunr off Dans Guardian as well, but the same thing happens. If I close the browser, it forgets the last setting and defaults back to "Connect directly to Internet".

Now for the network card. Is the Atheros a chip set? or is it a brand name? I'm just curious. 

Thanks again for the help!

God Bless!!!
Ron

---

### Post by tak1150 on 2007-04-20
> **BrookShadow_RC said:**
> 
Thanks for the responses. As far as the browser settings go, I have the browser unlocked, so I can add the company's proxy url into it and get out to the Internet. Part of my troubleshooting was to tunr off Dans Guardian as well, but the same thing happens. If I close the browser, it forgets the last setting and defaults back to "Connect directly to Internet".

Now for the network card. Is the Atheros a chip set? or is it a brand name? I'm just curious. 


Have you tried to set the proxy setting through "System -> Preference -> Network Proxy"? I haven't had to go through a proxy problem, so I'm not sure but that might make a difference.

Atheros is a brand name. There is a [website]("http://madwifi.org/wiki/Compatibility") that has linux drivers for wireless cards. And they have a nice page w/ all the compatibility info you want. Then you can look for the specific product / chipset in Ebay or something like that.

---

### Post by kd5gje on 2007-04-21
I am using a Netgear WG311T.  I guess Atheros makes the chip on the card because that's the driver that automatically installed.  I have no problems at all with my wireless card.

---

### Post by BrookShadow_RC on 2007-04-23
> **tak1150 said:**
> Have you tried to set the proxy setting through "System -> Preference -> Network Proxy"? I haven't had to go through a proxy problem, so I'm not sure but that might make a difference.

Yes. I have tried that. No impact on the issue.

Atheros is a brand name. There is a [website]("http://madwifi.org/wiki/Compatibility") that has linux drivers for wireless cards. And they have a nice page w/ all the compatibility info you want. Then you can look for the specific product / chipset in Ebay or something like that.

Cool. Thanks for the info. I have a Linksys wireless USB adapter that I'm working with. (It was free!)

Thanks,
Ron

---

