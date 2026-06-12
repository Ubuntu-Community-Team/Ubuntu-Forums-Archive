---
title: "searchnu.com/421 chromium hijack"
date: 2012-05-31
forum: Security
---

### Post by kristersaurus on 2012-05-31
Hey guys. Looks like my start page has been hijacked in chromium. Not sure how that happened.

I just tried to update my realtek NIC driver using the driver here: [http://r8168.googlecode.com/files/r8168-8.025.00.tar.bz2](http://r8168.googlecode.com/files/r8168-8.025.00.tar.bz2)

It looks like its old. It wouldn't compile. I then tried it using the newer version here: [https://r8168.googlecode.com/files/r8168-8.030.00.tar.bz2](https://r8168.googlecode.com/files/r8168-8.030.00.tar.bz2) ...I rebooted and my chromium default page is now searchnu.com/421. What the crap did I do? When i look up this searchnu business, I get mostly hits for windows viruses. Anyone heard of this in linux? How do I begin to check for damage? This is a clean install (I think the only other things I have installed are xpad and ruby1.9.3 and the official rails gem).

---

### Post by Hungry Man on 2012-05-31
I don't think it's that driver that did it. Do you use Windows? Like any time do you use Windows and Chrome/Chromium?

There's a sync feature in Chromium that'll take the start page from one OS and apply it to all of them.

So, perhaps your Windows is infected and the start page has just synced?

---

### Post by OpSecShellshock on 2012-06-01
Looks like what happened is that you downloaded a driver for network hardware from somewhere other than the hardware vendor's official site, installed it, and now traffic is being hijacked. There's a lot of that sort of stuff out there. No telling what else it might have been written to do. I would recommend re-installing and not using that driver next time.

---

### Post by unspawn on 2012-06-01
> **OpSecShellshock said:**
> Looks like what happened is that you downloaded a driver for network hardware from somewhere other than the hardware vendor's official site, installed it, and now traffic is being hijacked.
Did you actually D/L the sources and check it before suggesting this? At least the .030 driver matches the hash of the tarball the maintainer uploaded to Launchpad...

---

### Post by OpSecShellshock on 2012-06-01
Oh, does it? Eek, my mistake. Kind of made an assumption there based on the timing of the redirection relative to the installation of the driver. The redirection of search results or setting of a different browser homepage is consistent with the installation of non-official, but still legitimate software in other (Windows) contexts. Like, sometimes legitimate open source software will be wrapped in an installer that also contains additional "features" like toolbars and search engines and things. However, if it's also on Launchpad I would think that's less likely.

Next most likely thing would probably be a browser extension for Chromium then, but there hasn't been any mention of that yet.

---

### Post by kdrainey on 2012-07-19
I have had the searchnu problem in Windows 7, but I don´t think it has infected my Ubuntu browsers or can.  It seems to be connected to an .exe download.  I found useful help at:

 [http://forum.precisesecurity.com/computer-security/remove-searchnu-com406-redirect](http://forum.precisesecurity.com/computer-security/remove-searchnu-com406-redirect)

The following site includes was referenced in a post from someone who says he is connected to the iLlivid/Searchnu support team and that it is not malware and can easily be removed.

[http://www.ilivid.com/faq.htm](http://www.ilivid.com/faq.htm)

However, I found it hard to remove in Firefox and very persistent in other forms and manifestations in Windows and ended up re-installing Chrome, eliminating Firefox, mothballing Explorer and hoping I don´t need Windows for anything but Netflix.:(

---

