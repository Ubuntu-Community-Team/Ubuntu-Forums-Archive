---
title: "Firefox about:config settings"
date: 2014-03-01
forum: Ubuntu, Linux and OS Chat
---

### Post by Tristan_Williams on 2014-03-01
I would like to know what kind of about:config setting you guys use. 

Here are the ones I use:

network.http.pipelining = True
network.http.pipelining.max-optimistic-requests = 8
network.http.pipelining.maxrequests = 64
network.http.max-persistent-connections-per-proxy = 64
network.http.max-persistent-connections-per-server = 8
network.dns.disableIPv6 = True
nglayout.initialpaint.delay = 0
browser.newtab.url = [www.google.com](www.google.com)

So, what are the settings you guys use?

---

### Post by vasa1 on 2014-03-02
> **Tristan_Williams said:**
> 

network.http.pipelining = True
network.http.pipelining.max-optimistic-requests = 8
network.http.pipelining.maxrequests = 64
network.http.max-persistent-connections-per-proxy = 64
network.http.max-persistent-connections-per-server = 8
network.dns.disableIPv6 = True
nglayout.initialpaint.delay = 0
browser.newtab.url = [www.google.com](www.google.com)
...
I haven't changed any network.* settings.
My "browser.newtab.url" points to a local file.
I need to figure out what "nglayout.initialpaint.delay" is all about.

Re. "nglayout.initialpaint.delay", I found [http://forums.mozillazine.org/viewtopic.php?f=23&t=634081&start=0](http://forums.mozillazine.org/viewtopic.php?f=23&t=634081&start=0) from way back. I'm not going to bother setting it.

---

### Post by Tristan_Williams on 2014-03-02
nglayout.initialpaint.delay changes the time that any one element of a page can delay being shown.
For example:
By default, facebook loads everything, and then shows it.
with nglayout.initialpaint.delay = 0, it will show elements as they load.

---

### Post by Jonor on 2014-03-02
Intending to save overuse of any SSDs, probably a bit out of date by now though :

browser.cache.disk.enable  false 
browser.cache.memory.max_entry_size 51200

---

### Post by philinux on 2014-03-02
Moved to Ubuntu Linux and OS Chat.

---

### Post by vasa1 on 2014-03-04
I think this would be a useful thread if posters provide a reason for each change away from the default. 

Meanwhile,there is this: [Which about:config tweaks do you deem useful/necessary?]("http://forums.mozillazine.org/viewtopic.php?f=7&t=2786453")

---

### Post by vasa1 on 2014-03-04
**browser.pagethumbnails.capturing_disabled** with a value of **true**  prevents thumbnails from appearing on the New Tab page grid and from being saved in *~/.cache/mozilla/firefox/profile_name/thumbnails*.

This setting doesn't exist by default and is to be created.

Reference: [https://developer.mozilla.org/en-US/docs/Mozilla/Preferences/Preference_reference/browser.pagethumbnails.capturing_disabled](https://developer.mozilla.org/en-US/docs/Mozilla/Preferences/Preference_reference/browser.pagethumbnails.capturing_disabled)

---

### Post by vasa1 on 2014-03-04
And one more link: [http://kb.mozillazine.org/Firefox_:_FAQs_:_About%3Aconfig_Entries](http://kb.mozillazine.org/Firefox_:_FAQs_:_About%3Aconfig_Entries)

---

### Post by Jonor on 2014-03-16
I found your first link to a thread containing a poster who essentially appears to have done a lot of disabling very useful.
Although there is no obvious difference after making (most of) the changes i would imagine there are slight privacy/memory/cpu/speed benefits.
But the changes took at least half an hour to implement, it would be nice to automate that somehow.

---

