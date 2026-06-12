---
title: "will Chromium will be available in the coming Gnome Software center?"
date: 2016-02-23
forum: Ubuntu Development Version
---

### Post by davehenson on 2016-02-23
Did a fresh install of 16.04 daily build and found that the Gnome Software Center is replacing the Ubuntu Software Center. While that in itself wasn't a surprise as we've heard it was coming, I was surprised to see how few applications were in the new Gnome software Center. A big one (for me) that's missing is Chromium. Anyone know if chromium will be in the new software center? (I started the process of doing a build install but admit it was over my head.)

---

### Post by sammiev on 2016-02-23
You can install it from terminal or from Synaptic Package Manager.

---

### Post by buzzingrobot on 2016-02-24
Individual packages often need to be adjusted to assure they are displayed in Gnome Software. It's no surprise that, in this testing phase, that packages aren't showing up. 

Even if all packages are not transitioned before release, they'll be in the repositories for installation with another tool.

Fedora went through this transition when it rolled out Gnome Software Center a few releases ago.

More here: [URL="https://lists.ubuntu.com/archives/ubuntu-devel-announce/2016-February/001169.html"]https://lists.ubuntu.com/archives/ubuntu-devel-announce/2016-February/001169.html
[/URL]

---

### Post by corradoventu on 2016-02-24
In Ubuntu 16.04 the new software center seems know only already installed applications. I have Chromium installed with the old Ubuntu software center and the new Gnome software recognises it

---

### Post by jerrylamos on 2016-02-27
I've had a bunch of problems/deficiencies with Ubuntu Chromium, video's, etc.
Google-Chrome runs just fine, thanks.  
Crank up Firefox, search on Google-Chrome, download & terminal command line sudo dpkg -i Downloads/*deb  Then sudo apt-get -f install
Command line start with google-chrome then pin the icon to the launcher.
Even shares bookmarks with Google-chrome on XP and iPad.

Oh, clean up, remove the deb file from Downloads.

---

