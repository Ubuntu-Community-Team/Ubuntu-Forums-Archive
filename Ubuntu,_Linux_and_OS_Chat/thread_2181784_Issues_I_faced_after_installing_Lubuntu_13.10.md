---
title: "Issues I faced after installing Lubuntu 13.10"
date: 2013-10-19
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2013-10-19
I was previously running Lubuntu 13.04, 32-bit on my Dell Inspiron 1545 laptop but this time did a clean install of Lubuntu 13.10, 64-bit.

Shutdown doesn't power off the laptop. The power light remains on. Even **sudo shutdown -P now** doesn't help. I need to pull out the power cord :(

Previously, I could install Firefox and Seamonkey from [http://www.mozilla.org/en-US/firefox/channel/](http://www.mozilla.org/en-US/firefox/channel/) and [http://www.seamonkey-project.org/](http://www.seamonkey-project.org/) but this time around I can't. See [http://ubuntuforums.org/showthread.php?t=2181474](http://ubuntuforums.org/showthread.php?t=2181474) for Seamonkey.

The plugins I used with Gedit no longer work: DoubleSave and Markdown-preview don't run, possibly they haven't been updated for Gedit 3.8.3 which is the version in 13.10. I switched to Geany which has equivalent functioning plugins.

Putting .desktop files in ~/.config/autostart doesn't make the respective programs run on startup: I need to start Dropbox myself. Not a big deal but I didn't come across any mention of ~/.config/autostart being "deprecated" in Lubuntu 13.10.

There's something called "Default applications for LXSession" but I can't find any documentation on how to use it.

Other than that, all is well ;)

---

### Post by vasa1 on 2013-10-19
> **vasa1 said:**
> ...
Putting .desktop files in ~/.config/autostart doesn't make the respective programs run on startup: I need to start Dropbox myself. Not a big deal but I didn't come across any mention of ~/.config/autostart being "deprecated" in Lubuntu 13.10.

There's something called "Default applications for LXSession" but I can't find any documentation on how to use it.
...
See [http://askubuntu.com/a/361511/25656](http://askubuntu.com/a/361511/25656)

---

