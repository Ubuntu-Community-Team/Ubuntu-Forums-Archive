---
title: "Wine and WC3 Install."
date: 2009-07-12
forum: Wine
---

### Post by Linuxperiment on 2009-07-12
Hi everyone. I am using Ubuntu 9.04. I tried to install Wine using this method below from a website I found:

[I]III. Using the WineHQ Ubuntu repositories
This is yet another method of getting the latest Wine on Ubuntu. It is similar with the first method, but instead of adding a PPA repository we'll add the WineHQ repositories. Follow the steps below:

1. Add the repositories to /etc/apt/sources.list
Add the following repositories to your sources.list file:

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main

2. Update the sources lists
To update the sources lists use:

sudo apt-get update

With your user password.

3. Install Wine
To install Wine, just type:

sudo apt-get install wine

And this should be all.[/I]

I did exactly what it said, and I even when as far as to get the Launchpad PPA key and import it etc. I think I did this install correct, right?

Now, if that's completely correct, now I have questions about installing WC3. I am following this guide:

[http://www.tipsfor.us/2009/06/04/install-warcraft-3-on-ubuntu-linux-a-visual-guide/](http://www.tipsfor.us/2009/06/04/install-warcraft-3-on-ubuntu-linux-a-visual-guide/)

But this guide says a CD is required. I have my CD keys and I have them available online but I don't get my WC3 CDs (ROC/TFT). Blizzard allows you to download the installer online, but I tried using Wine to run the installers and it wouldn't work and gave me an error. Does anyone have any idea what I can do? Step by step guide would be appreciated as I'm pretty new to Linux/Wine/etc.

Thanks for the help!

---

### Post by pedro_orange on 2009-07-13
Use this guide:

[http://appdb.winehq.org/appview.php?iVersionId=1177](http://appdb.winehq.org/appview.php?iVersionId=1177)

Quote from that page:

> HOWTO: Blizzard Downloader

you need a native mshtml.dll and wininet.dll from ie6sp1 in ~/.wine/drive_c/system32

dont forget to set them as native in winecfg 

---

