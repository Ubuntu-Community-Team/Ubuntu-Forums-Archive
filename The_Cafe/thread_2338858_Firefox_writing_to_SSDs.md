---
title: "Firefox writing to SSDs"
date: 2016-10-02
forum: The Cafe
---

### Post by vasa1 on 2016-10-02
> a Firefox browser in its default configuration can write between 10GB and 30GB per day to SSD drives, depending on the number of opened tabs and windows.Source: [Adjust This Setting Before Firefox Wears Down Your SSD Drive]("http://news.softpedia.com/news/adjust-this-setting-before-firefox-wears-off-your-ssd-drive-508665.shtml")

---

### Post by TheFu on 2016-10-02
Good info.

Or run FF inside **firejail --private** so a virtual file system is used. Nothing is written to disk that way.

---

### Post by mikodo on 2016-10-02
Thank you, vasa1!

---

### Post by frostschutz on 2016-10-03
I have firefox and browser cache on SSD, box runs all day, usage is very normal. I don't see what the fuss (fud) is all about.

Also if you set this to 30 minutes you can just as well turn it off altogether. Restoring a session from 30 minutes ago is not useful.

Like any other storage media, SSD is supposed to be written to. That's its purpose in the first place. Even if Firefox wrote 20G per day (which I doubt, you'd have to be a firefox workaholic) the SSD would still be fine with it.

---

### Post by Bucky Ball on 2016-10-03
How can you set it to 'never'? I use session manager and don't think I need this at all unless session manager is somehow linked to the firefox.js file.

---

### Post by TheFu on 2016-10-03
> **Bucky Ball said:**
> How can you set it to 'never'? I use session manager and don't think I need this at all unless session manager is somehow linked to the firefox.js file.

Seems that any value longer than FF is running would work. If you shutdown FF daily, then ... you can do the math, 86400000? I usually only shut it off at reboot, post-patching and only if a reboot is needed, so ... 6 weeks could work for me, but I doubt every few hours would matter.

---

### Post by mastablasta on 2016-10-04
so for normal hard drives this could also be an issue and slowing it all down with all the writes and rewrites. i wonder why it would need 1 GB per hour. that's more than all the websites combined. :-O it might as wlel just save a state and leave it at that.

---

### Post by T2uiYKb7 on 2016-10-04
I set Chromium to write to RAM. On boot I make Xubuntu make a 100MB RAM disk then I added something to the Chromium launcher. I don't have a SSD but it makes browsing faster.

Is that what **firejail --private** does too?

---

### Post by bearlake on 2016-10-04
> **Bucky Ball said:**
> How can you set it to 'never'? I use session manager and don't think I need this at all unless session manager is somehow linked to the firefox.js file.

This works.

---

### Post by Bucky Ball on 2016-10-04
> **bearlake said:**
> This works.

Nice ... and so simple and obvious I missed it! :)

Cheers.

---

### Post by CantankRus on 2016-10-04
If you use firefox (or chrome) with an SSD you may like to have a read of this and
change your browser.sessionstore.interval in about:config.
[**_[COLOR="#B22222"]Firefox is eating your ssd[/COLOR]_**]("https://www.servethehome.com/firefox-is-eating-your-ssd-here-is-how-to-fix-it/")

---

### Post by Bucky Ball on 2016-10-04
*Threads merged*.

Because this conversation has been going on for awhile now and your comments would be more suitable here than in a new thread. :)

---

