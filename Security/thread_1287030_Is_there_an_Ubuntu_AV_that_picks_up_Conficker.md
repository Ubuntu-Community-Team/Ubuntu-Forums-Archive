---
title: "Is there an Ubuntu AV that picks up Conficker?"
date: 2009-10-09
forum: Security
---

### Post by Roasted on 2009-10-09
This is probably a stupid question but, it's a serious one at that.

I know Conficker is a Windows virus and only effects Windows machines, but I use my flash drive really frequently between work and home, and at work we had a slight issue with the Conficker virus for some time and I got to thinking, hmm, maybe I could scan my flash drive at home through Ubuntu? 

I figured it makes sense, because if it's possible it's probably the best way to go about it since I wouldn't be infecting my Ubuntu machine to do the scan anyway.

---

### Post by update_manager on 2009-10-09
> **Roasted said:**
> This is probably a stupid question but, it's a serious one at that.

I know Conficker is a Windows virus and only effects Windows machines, but I use my flash drive really frequently between work and home, and at work we had a slight issue with the Conficker virus for some time and I got to thinking, hmm, maybe I could scan my flash drive at home through Ubuntu? 

I figured it makes sense, because if it's possible it's probably the best way to go about it since I wouldn't be infecting my Ubuntu machine to do the scan anyway.

clamav might work

[http://www.clamav.net/2009/01/29/conficker-aka-downadup/](http://www.clamav.net/2009/01/29/conficker-aka-downadup/)

---

### Post by faical117 on 2009-10-09
try this :

[http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html](http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html)

:)

---

### Post by lovinglinux on 2009-10-09
I recommend BitDefender for Unices. I don't know if it catches Conficker, but I guess it probably does, since this virus is very popular.

---

### Post by aesis05401 on 2009-10-09
This should fill the bill:[http://www.linuxjournal.com/content/detecting-conficker-linux-tools]("http://www.linuxjournal.com/content/detecting-conficker-linux-tools")

---

### Post by xdemo on 2009-10-10
Yes there are several tools capable of detecting certain variants of conficker.

From wikipedia:

> **Automated remote detection**
On 27 March 2009, Felix Leder and Tillmann Werner from the Honeynet Project discovered that Conficker-infected hosts have a detectable signature when scanned remotely.[32] The peer-to-peer command protocol used by variants D and E of the worm has since been partially reverse-engineered, allowing researchers to imitate the worm network's command packets and positively identify infected computers en-masse.[75][76]
Signature updates for a number of network scanning applications are now available including NMap[77] and Nessus.[78]
Also it can be detected in passive mode by sniffing broadcast domain for repeating ARP requests.

Full article -- [http://en.wikipedia.org/wiki/Conficker](http://en.wikipedia.org/wiki/Conficker)

---

### Post by Roasted on 2009-10-10
Awesome.

Some crazy probably non-existent idea I just had that would be ABSOLUTELY AMAZING if it would ever exist would be... since the conficker virus replicates itself, it's extremely difficult to pinpoint it and get it out of the system. Sure, you get it out of one computer, but when you have 1,500, it can replicate and jump so quickly, making scanning useless initially.

Wouldn't it be amazing if we could somehow mount an Ubuntu ISO on the DHCP server and netbook boot all of the computers (maybe 100 at a time) and use the single Ubuntu ISO controlled by the server to scan the local drives with ClamAV? Then do that 100 pc's at a time, slowly bringing each PC back online.

If only...

---

### Post by Rob_H on 2009-10-11
[PXE]("http://en.wikipedia.org/wiki/Preboot_Execution_Environment") gives you the building blocks to do this. I'm not aware of a Linux boot image that does a virus scan like you describe, but you could always make one.

---

### Post by aysiu on 2009-10-11
How about just installing Windows updates at work?

Microsoft patched this back in October of last year.

---

### Post by Roasted on 2009-10-12
> **aysiu said:**
> How about just installing Windows updates at work?

Microsoft patched this back in October of last year.

The insanely confusing part is, we have all of our machines updated...

---

### Post by aysiu on 2009-10-12
> **Roasted said:**
> The insanely confusing part is, we have all of our machines updated...
I guess disabling autoplay also helps?

More details here:
[http://technet.microsoft.com/en-us/security/dd452420.aspx](http://technet.microsoft.com/en-us/security/dd452420.aspx)

---

### Post by Roasted on 2009-10-12
> **aysiu said:**
> I guess disabling autoplay also helps?

More details here:
[http://technet.microsoft.com/en-us/security/dd452420.aspx](http://technet.microsoft.com/en-us/security/dd452420.aspx)

Yeah, that's something that was found out over the weekend and may be changing via group policy or something like that.

---

