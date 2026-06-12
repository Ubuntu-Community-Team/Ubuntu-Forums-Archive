---
title: "OpenDNS considers UbuntuOne a P2P site"
date: 2013-06-11
forum: Ubuntu One (CLOSED)
---

### Post by SheamusPatt on 2013-06-11
Hi. I noticed Ubuntu One was not syncing recently, and discovered that my DNS server, OpenDNS, was blocking it. I have a filter set up to block P2P sites (actually, it's "P2P/File Share"), and recently someone has added one.ubuntu.com to that category, so the domain was effectively blocked on my network. Fortunately, I can add the site to a "whitelist" for my account, but it's quite annoying. I wanted to post the issue here, in case others have encountered it.

[OpenDNS]("http://www.opendns.com/") seems to be a bit discriminatory in making this assessment, as various other cloud storage sites (e.g. DropBox, SkyDrive) are not put in this category. The intention of this particular filter category is supposedly to block peer-to-peer sites that host documents which the poster does not have rights to (i.e. which are infringing someone's copyright). That's of course possible on any such service by its very nature, so there's an assumed caveat, I expect, that (a) the files are also made publicly accessible, and (b) the site does not respond in a timely fashion to takedown requests.

I'm going to follow up with OpenDNS support to see why they've flagged UbuntuOne this way, and whether they'll reconsider. I wanted to ask here though if others have been affected by this (perhaps with other DNS-based filter services besides OpenDNS), and if anyone has knowledge of why UbuntuOne is being blocked as a P2P site when others don't seem to be treated this way.

Thanks.

---

### Post by SheamusPatt on 2013-06-12
Just a follow up. After my complaint to OpenDNS, they've reconsidered, and one.ubuntu.com is no longer categorized as P2P/File Sharing site. So, users of OpenDNS who set up their network to filter out P2P sites will no longer find that site blocked. Good news, I guess, though they haven't yet refined the category definition so that it doesn't apparently include cloud storage sites.

---

### Post by GrimJa on 2013-06-26
That was a good bit of advocacy on your part. I enjoy the service of opendns.

Thanks.

---

### Post by PJSingh5000 on 2013-08-01
Thank you for this.  Just to confirm, if you navigate to [http://one.ubuntu.com](http://one.ubuntu.com), you would get a site blocked message?  I hadn't noticed, but I presume this would have also blocked the Ubuntu One cloud sotrage from working.

---

