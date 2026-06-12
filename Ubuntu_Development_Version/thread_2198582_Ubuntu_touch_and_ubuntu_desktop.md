---
title: "Ubuntu touch and ubuntu desktop"
date: 2014-01-09
forum: Ubuntu Development Version
---

### Post by krishnan t s on 2014-01-09
Ok. First, i dont think this is a support question. So please forgive me if it is posted in the wrong forum.
On saucy, i had installed the following:
1. Ubuntu sdk(my cousin asked me to)
2. Core apps ppa
3. Unity 8 shell
4. Mir(?? I dont think there's amd support.. still running fglrx on xserver)
Yesterday, i upgraded to trusty development and ran into few minor problems which i solved. Now, when i go to the apps lens, ubuntu touch applications are showing in the more suggestions group. However, i'm unable to  install them for some reason.
My first question is: Are touch apps even supposed to show in the apps lens on the desktop?
Second question: If they are not, could it be because of core apps ppa or unity 8 or both?
Third question: If they are, why am i not able to install them? am i doing something wrong?

Thanks in advance :)

---

### Post by grahammechanical on 2014-01-09
If we have installed Unity 8 shell, then yes the apps will show in the Dash apps lens as will many of the apps that are being developed for Ubuntu Touch. At present it is not possible to install and run these as they are Click packages and the desktop does not yet have the code to install and run them. It should be possible to install and run the core apps, especially if we have the SDK installed. It brings in some necessary libraries. I am trying to remember if we install through a PPA. Things are changing all the time and I do not want to recommend an out of date method. Allow me to do some research.

Regards

I am back. I needed to load my Trusty with the SDK and the core apps. We do need a PPA.

[https://launchpad.net/~ubuntu-touch-coreapps-drivers/+archive/daily](https://launchpad.net/~ubuntu-touch-coreapps-drivers/+archive/daily)

Afterwards we will find the core apps in the Software Centre. For, example, search for ubuntu clock and we get ubuntu-clock-app. We can also install through the terminal

```
sudo apt-get install ubuntu-clock-app
```

Replace "clock" with the name of the core app you want to install using the package name as shown in the Launchpad page. Oh, remember they use swipe gestures. Use the mouse to swipe from the edges. Have fun!

---

### Post by krishnan t s on 2014-01-10
I've been using core apps ppa since 13.04. The music-app is my personal favorite.. so much that its now the default music player on my system..But i'm a little surprised that while application lens in saucy didnt show touch apps in the more suggestions in dash, trusty did. I love installing apps through dash. I prefer that over software center which is slooooow even though the actual install happens in USC only :)
I did try to install touch apps directly from the dash.. it even showed the password prompt.. but as u said, click packages are not available for the desktop so direct install is not possible.
On a slightly unrelated note, uniity 8 on my desktop runs faster than ubuntu touch on my nexus 4(trusty r116).. Is it like that by nature or can i increase its speed somehow? i'm not a programmer.. merely an enthusiast, an addict

Thanks again :)

---

