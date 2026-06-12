---
title: "Any one with Chrome Extension experience?"
date: 2010-05-09
forum: The Cafe
---

### Post by tm222 on 2010-05-09
I am working on a Chrome extension, but I can't get the Javascript right. If anyone wants to correct me, the code is attached. Thanks in advance.

---

### Post by lovinglinux on 2010-05-09
There is nothing wrong with your javascript code, so I presume you need to declare the extension permissions in the manifest.json file, like this:

```
{
  "name": "SiteAdvisor Lookup",
  "version": "0.0",
  "description": "An Extension to lookup websites on SiteAdvisor",
  "permissions": ["http://*.siteadvisor.com/sites/*"],
  "browser_action": {
    "default_icon": "siteadvisor.png",
  "popup": "popup.html"
  } 
}
```

I don't have experience with Chrome extensions, just Firefox and actually I can't even test it here, because Chrome is not working on my system. But you can find some information at [http://code.google.com/chrome/extensions/overview.html](http://code.google.com/chrome/extensions/overview.html)

---

### Post by tm222 on 2010-07-24
Thank you! Sorry for the late reply!

---

