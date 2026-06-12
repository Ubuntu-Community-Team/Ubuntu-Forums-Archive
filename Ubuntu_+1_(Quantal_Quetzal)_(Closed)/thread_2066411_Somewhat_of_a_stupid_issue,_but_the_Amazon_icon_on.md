---
title: "Somewhat of a stupid issue, but the Amazon icon on the sidebar"
date: 2012-10-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by HolyMythos on 2012-10-04
With the inclusion of Amazon into Unity I find all of the new features pleasing... except Amazon appearing in the sidebar. After the fresh upgrade to 12.10 the Amazon icon was added to the sidebar. After checking it out I decided it wasn't useful to keep on the sidebar so I removed it. The problem is that whenever I navigate to any Amazon page in the browser the icon reappears, pushing everything down on the sidebar. Worse off, quitting that sidebar icon will quit the entire browser, even if it includes multiple tabs.

Is there any way to stop it from appearing other than deleting the entire Amazon addon? I know it's not a critical issue, but having it pop up and disappear multiple times is annoying. Sorry for clogging the useful board with this non-critical issue :P

---

### Post by mc4man on 2012-10-04
You could likely do a couple of things, 2 are - 
For firefox & affecting any website that has .desktop webapp support (icon), you could disable the Desktop extension - screen

While a bit of a hack - if you move the amazon .desktop to a bak (or remove), then there would be nothing to go on the launcher
(this may cause a one time crash of something, no big deal & shouldn't re-occur
```

sudo mv /usr/share/applications/ubuntu-amazon-default.desktop /usr/share/applications/ubuntu-amazon-default.desktop.bak
```
At least here closing the amazon icon does not close FF if other tabs are open.

---

