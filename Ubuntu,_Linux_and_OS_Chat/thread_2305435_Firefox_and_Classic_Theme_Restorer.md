---
title: "Firefox and Classic Theme Restorer"
date: 2015-12-06
forum: Ubuntu, Linux and OS Chat
---

### Post by Dennis N on 2015-12-06
On two new installations today this morning (Dec 5) and this afternoon, I find Firefox 42 would no longer install Classic Theme Restorer (it fails to download). Another add-on did install, so it is not a general problem. This could be temporary, and may be resolved, but I found this recent remark within the comments on Classic Theme Restorer's page:

> When Firefox switches to the new engine and removes xul which Classic Theme Restorer depends on, This Add-On will be unusable.

Perhaps they are now stopping new installs of this addon?

[https://addons.mozilla.org/en-uS/firefox/addon/classicthemerestorer/](https://addons.mozilla.org/en-uS/firefox/addon/classicthemerestorer/)

---

### Post by vasa1 on 2015-12-06
The bit you've quoted is sometime in the future. And it won't be just CTR that would be affected.

For now, CTR should install and work just fine.

The dev provides support here: [http://forums.mozillazine.org/viewtopic.php?f=48&t=2827985](http://forums.mozillazine.org/viewtopic.php?f=48&t=2827985) (but you'll need to sign in).

---

### Post by vasa1 on 2015-12-06
I just tried with another profile:> 1449401163508	addons.xpi	WARN	Download of [https://addons.mozilla.org/firefox/downloads/file/369708/classic_theme_restorer-1.4.3-fx.xpi?src=api](https://addons.mozilla.org/firefox/downloads/file/369708/classic_theme_restorer-1.4.3-fx.xpi?src=api) **failed:** **Downloaded file hash** (dfe27b2ff881ae5a16401364147166bb6d8bb2865f2460d11120c45cd89ce0e0) **did not match provided hash** (3a92f147bfc47bf0d80cae0f98b86d4b7018b8feddde67486080ce8f7994dcaf)After googling for "did not match provided hash", I feel it maybe some temporary glitch related to AMO and the whole "signing" of extensions business.

For some reason, this link works!
[https://addons.mozilla.org/en-US/firefox/addon/classicthemerestorer/versions/1.4.4](https://addons.mozilla.org/en-US/firefox/addon/classicthemerestorer/versions/1.4.4) when I clicked on "Add to Firefox".

---

### Post by Dennis N on 2015-12-06
It seemed unusual because it involved two different homes and separated by 6 hours time. I'll have to inquire if there has been any change. From your error message, it looks like a temporary thing. Thanks for the information on the timing. When this change happens, I would miss the nice tweaks CTR provided, unless someone comes up with a similar tool.

Edit: thanks for info on the other link too. I will suggest that.

---

### Post by Dennis N on 2015-12-06
Attempting to install from Menu > Tools > Add-ons still fails one day later, but the web page source you give works. Note - a new version was released two days ago (Dec 4). 

[https://addons.mozilla.org/en-US/firefox/addon/classicthemerestorer/](https://addons.mozilla.org/en-US/firefox/addon/classicthemerestorer/)

So the job is done. Thanks vasa1, for the link.

---

### Post by vasa1 on 2015-12-06
> **Dennis N said:**
> Attempting to install from Menu > Tools > Add-ons still fails one day later, but the web page source you give works. Note - a new version was released two days ago (Dec 4). 

[https://addons.mozilla.org/en-US/firefox/addon/classicthemerestorer/](https://addons.mozilla.org/en-US/firefox/addon/classicthemerestorer/)

So the job is done. Thanks vasa1, for the link.
You're welcome. I have version 1.4.4 (the stable version) via auto-update.

---

