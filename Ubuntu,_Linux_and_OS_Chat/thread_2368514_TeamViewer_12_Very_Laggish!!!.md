---
title: "TeamViewer 12 Very Laggish!!!"
date: 2017-08-11
forum: Ubuntu, Linux and OS Chat
---

### Post by mphaars on 2017-08-11
I just installed TeamViewer 12 on my new PC running Ubuntu 17.04.  It is very slow, beyond using - cannot determine why.  PC specs and internet at both ends are high-end.  Just wondering if anyone has run into this issue before?  I have TeamViewer on a couple machines and those work perfectly fine, including on a Raspberry Pi 3.  Any help or references would be greatly appreciated!  

Thanks in advance!
Mike

---

### Post by ClickXT on 2017-08-14
Interesting. It's working flawlessly for me on 17.04.

How did you install it? Any differently from the other machines? Have you tried reinstalling it completely?

---

### Post by mphaars on 2017-08-14
I installed via CLI.  I have reinstalled.  I assume just using integrated graphics - no graphics card as this is primarily used for Plex - is sufficient since I have no problem on Pi?

---

### Post by ClickXT on 2017-08-14
Most likely.

I installed it with:
***Open up a terminal window and download the TeamViewer 12 beta deb package with the following command:   ******wget [https://downloadus2.teamviewer.com/download/version_12x/teamviewer_12.0.71510_i386.deb](https://downloadus2.teamviewer.com/download/version_12x/teamviewer_12.0.71510_i386.deb)***[I][B]
This deb package requires many dependency packages. Manually finding  and installing dependency packages is a tedious task. We can use the gdebi package installer to automatically handle all required dependencies for us.[/B][/I]
[I][B]
Install gdebi command line package installer with the following command:
[/B][/I]sudo apt install gdebi-core
[I][B]Then install the TeamViewer 12 deb package with:
[/B][/I]sudo gdebi teamviewer*.deb
[I][B]The above command will list all required dependencies to you. Press Y to continue the installation.
[/B][/I]
I wouldn't think it should matter though....very odd.

---

### Post by mphaars on 2017-08-14
I will try this method tonight and see if it helps.  Thanks for the help!

---

