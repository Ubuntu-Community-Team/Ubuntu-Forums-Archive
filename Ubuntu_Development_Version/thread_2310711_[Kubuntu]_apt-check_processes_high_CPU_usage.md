---
title: "[Kubuntu] apt-check processes high CPU usage"
date: 2016-01-21
forum: Ubuntu Development Version
---

### Post by christophe-caillet on 2016-01-21
Hi all,

I'm testing Kubuntu xenial in VBox and when I use the command "apt update", I have my CPU go to 100% and each core has the same behaviour and I've an high memory usage during the apt-check processes execution. After that memory and CPU go down to the normal level of consumption

I've also the same issues with my Wily Kubuntu desktop since the last "big update" of plasma 5.5.3.

Thanks by advance for your replies

---

### Post by ajgreeny on 2016-01-21
See [http://ubuntuforums.org/showthread.php?t=1102483](http://ubuntuforums.org/showthread.php?t=1102483) which may help with this, if it is really the same problem that you are seeing.

---

### Post by christophe-caillet on 2016-01-22
Hi all,

It's not the problem ... this issue is located on plasma-discover-updater package

Filling a bug now .. :)

UPDATE :
* Workaround : remove package plasma-discover-updater and after restart your KDE session for unloading the plasma plugin
* KDE BUG open under reference 358359

---

### Post by ellisistfroh on 2016-02-10
purrfect! Even ubuntu-forums-italia gives feedback in kub-bugbase. Just added this to my Firefox seach-bar.

---

