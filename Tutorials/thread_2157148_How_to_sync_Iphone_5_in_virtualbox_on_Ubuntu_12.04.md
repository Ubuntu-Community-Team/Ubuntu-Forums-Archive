---
title: "How to sync Iphone 5 in virtualbox on Ubuntu 12.04"
date: 2013-06-24
forum: Tutorials
---

### Post by c2tarun on 2013-06-24
Hi friends,

In this tutorial I am going to tell you how to sync Iphone 5 in a virtualbox in Ubuntu 12.04. First let me clear few things. There are ways to sync Iphone 5 directly with Ubuntu, I am not saying that this way is better than that or vice versa. This method is only for those who want to use iTunes to sync their Iphone and don't want to dual boot. Because dual booting is a real pain. So lets begin.

1. You need to download the latest version of **virtualbox **and **virtualbox extension pack **from [here]("https://www.virtualbox.org/wiki/Downloads").

2. Install virtualbox first (its simple, just double click and install) then install extension pack (its simple too :) double click and install).

3. Now you need to install Win XP/Vista/7 or whatever windows you want in your virtual box installation. For this tutorial I am considering that you installed XP.

[ATTACH=CONFIG]244101[/ATTACH]

4. Now you need to add your ubuntu username to "vboxusers" group. To do this execute following command:
```
sudo usermod -G vboxusers -a username
```
    replace username with your username.

5. Now after installation of XP is finished, logout from Ubuntu and log back in (this is to make usermod changes to take effect).

6. Now connect your Iphone and you can cancel all the mounting notifications and popups.

[ATTACH=CONFIG]244103[/ATTACH]

7. Make sure that XP is not running in this step. Open virtualbox, right click over your XP installation and go to settings. Select USB from left menu, click on the icon in the right to add USB filter. You'll see an option of “Apple Inc.” select that and make sure that it is checked.

[ATTACH=CONFIG]244104[/ATTACH]

8. Now we are almost done. Disconnect Iphone and start XP. Inside XP install iTunes (you can download it from Apple's site). 


9. After installation of Itunes is finished start iTunes

10. Connect Iphone :) iTunes will detect Iphone.

[ATTACH=CONFIG]244105[/ATTACH]

---

### Post by GMeister on 2013-12-15
Thanks - used, worked.

---

### Post by danielprado_0 on 2014-01-08
what version of virutalbox?¿

---

### Post by ilikecolors on 2014-01-30
Hey, lately I tried this with my iPod 5G and iTunes would not detect my iPod. Any help?

---

