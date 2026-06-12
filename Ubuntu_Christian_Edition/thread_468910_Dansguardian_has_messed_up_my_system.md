---
title: "Dansguardian has messed up my system"
date: 2007-06-09
forum: Ubuntu Christian Edition
---

### Post by lsharkey on 2007-06-09
Hi

I've been having nothing bur problems with dansguardian, and now my system is all messed up.  I am using Ubuntu 7.04 amd64, which I converted into Christian Edition using the script.  I then found on use that dansguardian blocked all sorts of things I need to do including changing firefox proxy settings.

When I tried to disable it using "Configure Parental Controls", the GUI would not work.  I tried starting from terminal, and the error message, from memory, was something to do with a CLASS size 256 and a segmentation fault.

I then tried to remove dansguardian using intructions I found on this forum:
> apt-get --purge remove --assume-yes "dansguardian"
    apt-get --purge remove --assume-yes "tinyproxy"
    apt-get --purge remove --assume-yes "clamav"
    apt-get --purge remove --assume-yes "firehol"
    apt-get --purge remove --assume-yes "dansguardian-gui-ubuntu"

However, in doing so dansguardian was not removed properly.  Again, I wish I'd noted down the error message.  I then used the --force-all tag to get rid of it and the other packages.  That sort of worked, because at any rate dpkg -l | grep dans no longer listed dansguardian.  

I then started firefox, which unfortunately will not let me onto the internet, saying it cannot connect to the server.  I then tried reinstalling dansguardian to at least see if I could get back to *some* internet, if not all.  However, it will now not run, giving the error message of:
> Error connecting to parent proxy

So last of all I tried to run the convert_me script all over again to reinstall all the CE packages, and this failed with:
> Ubuntu CE Convert Me Script WILL NOT run because a connection to the server could not be made. Try again later.

The only way I am now able to connect to the internet, curiously, is in terminal logging in as root (with su) and then starting firefox from command line.  I don't know why this works.

I am very unhappy with all of this and would just like to have everything back to normal, get rid of dansguardian, and have my interent back. I am not afraid of CLI fixes.

Thanks


Oh, here is the error message for  sudo apt-get --purge remove dansguardian:
> Removing dansguardian ...
Stopping DansGuardian: dansguardian.
/etc/init.d/dansguardian: 71: /usr/local/apps/parental-control/./dansguardian_log.pl: not found
invoke-rc.d: initscript dansguardian, action "stop" failed.
dpkg: error processing dansguardian (--purge):
 subprocess pre-removal script returned error exit status 127

---

### Post by mysticrider92 on 2007-06-11
This is a problem I found when I converted my Feisty 64bit to CE. I did not have any proxy to configure, but Dansguardian blocks all kinds of .tgz and .zip files I tried to download. 

All of the programs Jereme has written were done in Gambas, which will not work properly on Feisty 64bit, along with all of the programs written in the language. My solution at the moment is to use the scripts in /usr/local/apps from a teminal to disable/enable/change dansguardian (obviously this won't solve your problem as your dansguardian has messed itself up). 

I think the su firefox works because dansguardian is not set up to block the root user (pretty useless with the way Ubuntu is set up). One thing you might try is sudo killall dansguardian (do the same for the other programs you listed). Then run sudo apt-get --purge remove dansguardian. That should be a forceful way to get apt to remove it. If all of the other programs (mostly tinyproxy) are not removed properly, your internet will still not work (as you have probably noticed). Well, I hope that helps and isn't things you already tried.

---

### Post by shane2peru on 2007-06-13
> **mysticrider92 said:**
> This is a problem I found when I converted my Feisty 64bit to CE. I did not have any proxy to configure, but Dansguardian blocks all kinds of .tgz and .zip files I tried to download. 

All of the programs Jereme has written were done in Gambas, which will not work properly on Feisty 64bit, along with all of the programs written in the language. My solution at the moment is to use the scripts in /usr/local/apps from a teminal to disable/enable/change dansguardian (obviously this won't solve your problem as your dansguardian has messed itself up). 

I think the su firefox works because dansguardian is not set up to block the root user (pretty useless with the way Ubuntu is set up). One thing you might try is sudo killall dansguardian (do the same for the other programs you listed). Then run sudo apt-get --purge remove dansguardian. That should be a forceful way to get apt to remove it. If all of the other programs (mostly tinyproxy) are not removed properly, your internet will still not work (as you have probably noticed). Well, I hope that helps and isn't things you already tried.

The only thing I would add to that is to use aptitude remove -p instead of apt-get, it is a little more comprehensive to get rid of it.  Although I don't know that it has a force option, it may.  I try to assume nothing, so of course after removing all of that you will probably need to reboot the computer as well.  And then double check the firefox settings and make sure that the proxy is turned off in the options. Just thinking out loud here.

Shane

---

