---
title: "64 bit Can't install Firefox 3.6.2"
date: 2010-04-03
forum: Ubuntuzilla
---

### Post by Sale on 2010-04-03
Hi, I'm running 64 bit Karmic and I've had mozillateam repositories in my sources.list for some time. last 2 (i think) upgrades went fine, but today, after I tried to upgrade to firefox 3.6.2 (via Update manager) I've encountered a problem.

Here is the output from the teminal window after I run sudo apt-get install firefox:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up firefox (3.6.2+nobinonly-0ubuntu1~mfs~karmic1) ...
update-alternatives: error: alternative path /usr/bin/firefox doesn't exist.
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on firefox | abrowser | firefox-3.0 | firefox-2; however:
  Package firefox is not configured yet.
  Package abrowser is not installed.
  Package firefox-3.0 is not installed.
  Package firefox which provides firefox-3.0 is not configured yet.
  Package firefox-2 is not installed.
  Package firefox which provides firefox-2 is not configured yet.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 firefox
 ubufox
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Firefox icon appears in panel, but when I click on it, I get an error message that says:

"Failed to execute child process "firefox" (No such file or directory)"

Any help, please?

---

### Post by Wiebelhaus on 2010-04-03
First purge everything about that app

```
sudo apt-get --purge remove yourapp
```

Then:

```
sudo apt-get install yourapp
```


Which should pull in all dependencies and the app. 

Cheers.

---

### Post by Sale on 2010-04-03
Unfortunatelly, it doesn't work :(

here is the new terminal output (it seems slightly different to me):

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  firefox-branding ubufox
Suggested packages:
  firefox-gnome-support kmozillahelper
The following NEW packages will be installed:
  firefox firefox-branding ubufox
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/12.3MB of archives.
After this operation, 36.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package firefox-branding.
(Reading database ... 239547 files and directories currently installed.)
Unpacking firefox-branding (from .../firefox-branding_3.6.2+nobinonly-0ubuntu1~mfs~karmic1_amd64.deb) ...
Selecting previously deselected package firefox.
Unpacking firefox (from .../firefox_3.6.2+nobinonly-0ubuntu1~mfs~karmic1_amd64.deb) ...
Selecting previously deselected package ubufox.
Unpacking ubufox (from .../ubufox_0.8-0ubuntu1_all.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Setting up firefox-branding (3.6.2+nobinonly-0ubuntu1~mfs~karmic1) ...
Setting up firefox (3.6.2+nobinonly-0ubuntu1~mfs~karmic1) ...
update-alternatives: error: alternative path /usr/bin/firefox doesn't exist.
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on firefox | abrowser | firefox-3.0 | firefox-2; however:
  Package firefox is not configured yet.
  Package abrowser is not installed.
  Package firefox-3.0 is not installed.
  Package firefox which provides firefox-3.0 is not configured yet.
  Package firefox-2 is not installed.
  Package firefox which provides firefox-2 is not configured yet.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 firefox
 ubufox
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Sale on 2010-04-03
hmmm...

After retrying what was suggested here (with unchanged results) and some googling, I decided to have  a look at what I have in /usr/bin/ regarding "firefox".

There were two symlinks. One named "firefox" and the other named "firefox.ubuntu". Clicking on the first one produced an "no such file or directory" error so I deleted it. Clicking on the other one, however, started a full working 64bit Mozilla Team version of Firefox 3.6.2. I'm using it to post this message. After this I just changed the Firefox icon (in the panel) properties to point to "/usr/bin/firefox.ubuntu" instead of the "firefox %s".

Maybe this will help someone.

Still, I'm not sure what he problem was, so if anyone is interested in commenting, they are welcome :)

---

### Post by nanotube on 2010-04-03
it appears you had the ubuntuzilla version installed previously, which did the firefox.ubuntu diversion. then apparently you decided to try the mozillateam's daily repository, but without doing a proper uninstall of the ubuntuzilla (which would have removed the divert and saved you some confusion). so... to remove the divert, run:
```
sudo dpkg-divert --rename --remove /usr/bin/firefox
```

---

### Post by Sale on 2010-04-05
> **nanotube said:**
> it appears you had the ubuntuzilla version installed previously, which did the firefox.ubuntu diversion. then apparently you decided to try the mozillateam's daily repository, but without doing a proper uninstall of the ubuntuzilla (which would have removed the divert and saved you some confusion). so... to remove the divert, run:
```
sudo dpkg-divert --rename --remove /usr/bin/firefox
```

Thanks for the explanation nanotube.I did have ubuntuzilla installed. I did as you said, as I assume that this will prevent any future confusion. I've changed the ff launcher path back to "firefox %s" and it works.

Still...as much as I remember, I did at least one upgrade from the mozillateam repo (i.e. installed a ff version from a mozillateam repo and later on upgraded it to a newer version), before this one, and I didn't have these problems...I guess there was a step somewhere along the line that I forgot about... :)

---

### Post by M0GEJ on 2010-05-14
I was having the same problem after upgrading to lucid.  After purging firefox from the system I was able to use nanotube's tip and now everything works.  Cheers to all of you guys...

---

### Post by cejack on 2010-09-04
I tried the below:

charles@charles-laptop:/usr/bin$ sudo dpkg-divert --rename --remove /usr/bin/firefox
Removing `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
dpkg-divert: rename involves overwriting `/usr/bin/firefox' with
  different file `/usr/bin/firefox.ubuntu', not allowed

My problem is I am stuck on Firefox 3.5.3.  I cannot seem to get the system to update to any more recent version in the 3.6.X releases.  What gives here?  I'm running X64 version of Ubuntu 10.04 on my laptop.

---

### Post by nanotube on 2010-09-04
Hi,
I take it you have used the ubuntuzilla.py script to install earlier?

if so, run "ubuntuzilla.py -a remove -p firefox" - that will remove all the ubuntuzilla stuff and let you get back to ubuntu repos.

---

### Post by C64HCS on 2011-01-24
> **nanotube said:**
> it appears you had the ubuntuzilla version installed previously, which did the firefox.ubuntu diversion. then apparently you decided to try the mozillateam's daily repository, but without doing a proper uninstall of the ubuntuzilla (which would have removed the divert and saved you some confusion). so... to remove the divert, run:
```
sudo dpkg-divert --rename --remove /usr/bin/firefox
```

Thanks, that works ! Still, people that need to change this diversion, you have to change the divert with **firefox uninstalled**. Then re-install. 

That is why cejack got his error msg.

Thanks nanotube. ;)

---

