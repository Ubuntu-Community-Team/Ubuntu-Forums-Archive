---
title: "Was the problem because of wine?"
date: 2009-07-05
forum: Security
---

### Post by kewl_123 on 2009-07-05
I faced following problems:
1) Was unable to login to sites like this one
2) Was unable to search any site except using google
3) The forward and back button on firefox were grayed out
4) Download them all add-on was acting strange
5) When I clicked on manage add-ons, firefox disappeared.

I tried to uninstall firefox using synaptic manager, but firefox and all above stated problems were still there.

Then I uninstalled wine, and with it went all the problems and thats how I am able to post here. Did anyone have any such experience before?

Thank you.

---

### Post by ajgreeny on 2009-07-05
Never!

I see no reason why wine should affect your firefox installation in any way.  Can you give more information about your setup, hardware, ubuntu version, and any additional non supported software you may have added.

Are you using firefox through wine as well as direct from ubuntu in order to use any plugins that perhaps don't work in ubuntu 64bit version?

---

### Post by kewl_123 on 2009-07-05
> **ajgreeny said:**
> Never!

I see no reason why wine should affect your firefox installation in any way.  Can you give more information about your setup, hardware, ubuntu version, and any additional non supported software you may have added.

I have Lenovo N series laptop, dual core, 1 GB ram, 159 GB hd, Ubuntu 8.04
  Regarding non-supported software, i am very sorry I have no idea what it means. When I download some software I just try to get it working ignoring any messages I get. I tried to read about repositiries and stuff but was really too much for me, and couldnt understand well.

> Are you using firefox through wine as well as direct from ubuntu in order to use any plugins that perhaps don't work in ubuntu 64bit version?
No, I am not using firefox through wine.

---

### Post by cariboo on 2009-07-05
You should have researched you problem a little more. The problems you were experienced are well documented here in the forums. The problem was that your Firefox profile was corrupted, all you had to do was move your old profile to a backup:

```
mv ~/.mozilla ~/.mozilla.bak
```

Then restart firefox, then next step would be to import your bookmarks from the backup directory and problem solved.

---

