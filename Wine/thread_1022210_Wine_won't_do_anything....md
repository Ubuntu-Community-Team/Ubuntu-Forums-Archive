---
title: "Wine won't do anything..."
date: 2008-12-26
forum: Wine
---

### Post by mr.vanker on 2008-12-26
Alright, I'm pretty new to linux. I can use the terminal effectively, install/uninstall applications, etc. But there is still a lot that I do not know.

So, I installed Wine, to see if I could get PSO running on it. It opened the installer, ran the installer, opened a few other .exe files, it worked fine. But all of the sudden, it stopped opening anything. I cannot even open the Wine Notepad, or the Wine Configuration applet. Any suggestions?

I uninstalled, deleted the .wine directory, and reinstalled (with Synaptic), and I just uninstalled and reinstalled with the terminal. I/the terminal installed version 1.0.1, and I am running Intrepid.

---

### Post by HotShotDJ on 2008-12-26
I can't imagine what might have happened to cause your problem.  However, it is often recommended that people use the software maintained by WineHQ rather than the versions available through the Ubuntu repositories.

What I would do is completely remove WINE from your system using the command line (Applications --> Accessories --> Terminal):```
sudo apt-get autoremove wine --purge
```Next, remove the wine directory(ies) found in your home directory.

Now, follow the instructions to add the WineHQ repository to your system here: [http://winehq.org/download/deb](http://winehq.org/download/deb)

Let us know how it works out for you!

EDIT:  When installing applications under Wine, install and test one at a time.  Not only testing the newly installed application, but all the other software.  If breakage occurs, this will help you isolate the probable cause.

---

### Post by cogadh on 2008-12-26
> **HotShotDJ said:**
> I can't imagine what might have happened to cause your problem.  However, it is often recommended that people use the software maintained by WineHQ rather than the versions available through the Ubuntu repositories.
Considering that the Wine packages in the Ubuntu repositories and the WineHQ repositories are created and maintained by the same person *and* the WineHQ packages are the unstable development version of Wine, that is not true at all (at least it shouldn't be). 

The packages are identical, in terms of how they are built and what the require, regardless of which repository you use. However, when you use the WineHQ repository, you run the risk of updating to a Wine version that has severe new bugs and/or regressions that the stable Wine version does not have. Of course with the unstable version, you also gain the possibility of greater software compatibility over the package in the Ubuntu repository. Whether or not you use the WineHQ repository is really a matter of the individual user's needs, and should not be automatically recommended.

---

