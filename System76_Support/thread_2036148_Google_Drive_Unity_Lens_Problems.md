---
title: "Google Drive Unity Lens Problems"
date: 2012-08-01
forum: System76 Support
---

### Post by Ubun2to on 2012-08-01
I noticed that there was a Unity Lens for Google Drive included with my laptop. Works great-except I have to reauthorize it every day. Is there a workaround for this besides removing my Google account?

---

### Post by isantop on 2012-08-01
> **Ubun2to said:**
> I noticed that there was a Unity Lens for Google Drive included with my laptop. Works great-except I have to reauthorize it every day. Is there a workaround for this besides removing my Google account?

I wasn't aware there was a Google Drive Lens. Did it come preinstalled, or did you install it yourself? Also, did you install the Unity Webapps preview?

---

### Post by Ubun2to on 2012-08-01
> **isantop said:**
> I wasn't aware there was a Google Drive Lens. Did it come preinstalled, or did you install it yourself? Also, did you install the Unity Webapps preview?

Oh-it must be the Unity Webapps preview. I tried removing it, but it never deleted all of the files. So annoying, as my Unity launcher gets clogged whenever I visit a site that supports it even though I removed it.

---

### Post by Ubun2to on 2012-08-02
I have figured out what the package is for the Unity Google Docs lens is. I have marked unity-lens-gdocs (weird to mark it as Google Docs, when the logo of the lense is that of Google Drive) for removal.
However, I can't find the Facebook or Youtube webapp packages to remove (even though I marked unity-webapps-preview for complete removal and removed the Chromium extension via the Settings menu). When I click on one of the Webapp icons, it launches it like a webapp, not like a regular link.
Although I have real icons on the Webapps now, I find them annoying just sitting there. How do I remove them?

---

### Post by pete04 on 2012-08-02
I tried the webapps preview, too (though not on my System76, but my lucky test Dell) and it didn't go well. It treated my system as requiring several partial upgrades and I had some other difficulties. I think I'll wait until those come official in October.

---

### Post by znorris on 2012-08-07
I really like the idea of a Google Drive lens however the webapps preview was far to buggy. I used this guide for both installation and removal of the webapps preview:
[http://www.webupd8.org/2012/07/install-new-ubuntu-webapps-technology.html](http://www.webupd8.org/2012/07/install-new-ubuntu-webapps-technology.html)

Those instructions did not account for:
unity-webapps
unity-webapps-service
webaccounts-extension-common

After uninstalling those you will find the launcher shortcuts in ~/.local/share/applications/

Perhaps this will help.

---

### Post by Ubun2to on 2012-08-08
> **znorris said:**
> I really like the idea of a Google Drive lens however the webapps preview was far to buggy. I used this guide for both installation and removal of the webapps preview:
[http://www.webupd8.org/2012/07/install-new-ubuntu-webapps-technology.html](http://www.webupd8.org/2012/07/install-new-ubuntu-webapps-technology.html)

Those instructions did not account for:
unity-webapps
unity-webapps-service
webaccounts-extension-common

After uninstalling those you will find the launcher shortcuts in ~/.local/share/applications/

Perhaps this will help.

Can't remove unity-webapps-service without removing unity, unity-2d, ubuntu-desktop, and about 15 more packages. I think it's probably a bug, but I don't want to risk destroying my laptop.

---

