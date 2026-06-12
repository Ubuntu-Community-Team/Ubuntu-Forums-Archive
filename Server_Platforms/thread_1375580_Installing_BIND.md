---
title: "Installing BIND"
date: 2010-01-08
forum: Server Platforms
---

### Post by vamega on 2010-01-08
Alright, I screwed up things completely.

I had installed a dns-server earlier using the command
```
sudo tasksel install dns-server
```and since I screwed up the configuration of BIND, i though I would re-install it, and start over. So I removed it using the command
```
sudo tasksel remove dns-server
```but when navigatinf the /etc directory i noticed that the /bind directory still existed, with all my custom configuration files. So I deleted the directory with the command
```
sudo rm -r /etc/bind
```Now I am run the installation command, I get the following output
```
$ sudo tasksel install dns-server
tasksel: aptitude failed (100)
```this appears after the package is downloaded, and towards the end of the tasksel installation process (I've read till 94% on the progress bar). I believe its something to do with the post-installation configuration because of the following.
```
$ sudo dpkg --configure -a
Setting up bind9 (1:9.6.1.dfsg.P1-3ubuntu0.2) ...
 * Starting domain name service... bind9                                [fail] 
invoke-rc.d: initscript bind9, action "start" failed.
dpkg: error processing bind9 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 bind9
```Does anyone have any ideas how I can get everything working once more?

Thanks a lot

Vamega

---

### Post by vamega on 2010-01-08
I solved the problem by running the commands
```

sudo apt-get remove --purge bind9
sudo tasksel install dns-server

```

Anyone know how I can change this to solved?

Vamega

---

### Post by pmower on 2011-11-27
> **vamega said:**
> I solved the problem by running the commands
```

sudo apt-get remove --purge bind9
sudo tasksel install dns-server

```

Anyone know how I can change this to solved?

Vamega

Thanks for that information!  I have been having that problem for a couple of weeks, you finally solved it!!!!!

---

