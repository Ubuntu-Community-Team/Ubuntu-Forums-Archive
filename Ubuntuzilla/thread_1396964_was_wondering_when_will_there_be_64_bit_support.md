---
title: "was wondering when will there be 64 bit support"
date: 2010-02-02
forum: Ubuntuzilla
---

### Post by jewfromdahood on 2010-02-02
when will there be 64 bit support for ubuntu firefox... as i'd really like to get 3.6+ firefox and thunderbird 3.0.1+ working without losing my plugins and settings and everything with little effort... I use Ubuntu 8.10

---

### Post by nanotube on 2010-02-02
> **jewfromdahood said:**
> when will there be 64 bit support for ubuntu firefox... as i'd really like to get 3.6+ firefox and thunderbird 3.0.1+ working without losing my plugins and settings and everything with little effort... I use Ubuntu 8.10

Hi
unfortunately, that will only happen when mozilla starts releasing 64bit builds of its software. At this moment, I don't know when this will be.

In the meantime, as suggested on the ubuntuzilla website, you can try the 'firefox-stable' launchpad ppa for firefox, and the 'ubuntu-mozilla-daily' ppa for thunderbird (although it's currently troublesome to make both coexist... since the firefox dailies will overwrite firefox-stable) so you could just go for the daily repo and see how that works for you...

---

### Post by beartham on 2010-02-04
Hi,

I just installed Firefox 3.6 and Seamonkey on a Jaunty 64bit laptop using the manual command line procedure on your website. Both browsers seem to be operating but neither will browse the internet (no proxy).  Could this be a 64bit problem?

I have another Jaunty 64bit desktop box that I used Ubuntuzilla to install Firefox (v 3.0.11) and Seamonkey on last year. They both browse ok.

Any recommendation of how to get them to browse on the laptop?:confused:

Thanks

---

### Post by nanotube on 2010-02-04
> **beartham said:**
> Hi,

I just installed Firefox 3.6 and Seamonkey on a Jaunty 64bit laptop using the manual command line procedure on your website. 

by 'manual commandline procedure', do you mean the ubuntuzilla installer script?

> 
Both browsers seem to be operating but neither will browse the internet (no proxy).  Could this be a 64bit problem?



try installing package 'lib32nss-mdns'. if that doesn't work, try going into about:config, and setting 'network.dns.disableIPv6' to true.

---

### Post by beartham on 2010-02-05
Thank you nanotube ;)

Installing 'lib32nss-mdns' seemed to work fine for Firefox. But then I added an add-on extension 'Gmarks', which I have on all my other Firefox versions. When it said to restart Firefox to finish Gmarks install, Firefox would not execute. I tried it from the icon and the command line. No response from command line at all.:shock:

Should I re-install Firefox with the Ubuntuzilla script?

Regarding Seamonkey, installing lib32nss-mdns was not enough. But when I set network.dns.disableIPv6 to true, it did work fine.

Thanks again.

---

### Post by nanotube on 2010-02-05
> **beartham said:**
> Thank you nanotube ;)


you're welcome :)

> 
Installing 'lib32nss-mdns' seemed to work fine for Firefox. But then I added an add-on extension 'Gmarks', which I have on all my other Firefox versions. When it said to restart Firefox to finish Gmarks install, Firefox would not execute. I tried it from the icon and the command line. No response from command line at all.:shock:

Should I re-install Firefox with the Ubuntuzilla script?


that probably won't help, as the problem is likely in your profile that gmarks has somehow borked up. i would instead suggest starting with a fresh profile to see if the problem resolves itself (likely).

---

