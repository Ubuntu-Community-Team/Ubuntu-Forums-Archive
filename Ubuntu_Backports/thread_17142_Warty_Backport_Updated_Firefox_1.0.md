---
title: "Warty Backport: Updated Firefox 1.0"
date: 2005-02-26
forum: Ubuntu Backports
---

### Post by jdong on 2005-02-26
**Synopsis**
Though not providing a fix for the IDN spoofing bug, this new Firefox does include many, many bugfixes. It's about time we replaced that backport from early Hoary...

Note that mozilla-firefox-gnome-support literally turns Firefox into a GNOME browser. That is, GNOME dialogs (Open, Save), GNOME Icons (which some may find disgusting.). Theme it yourself -- that's the flexibility of Firefox.

This is designed as an interim release...

**Backporting Process**
The source archive directly came from Hoary. I was able to meet all dependencies.

**Packaging Status:**
i386 -- Staging at revision
amd64 -- Not packaged
ppc -- Not packaged

**Beta tester notes:**

**Deps**

```

jdong@omega:~ $ sudo apt-get install mozilla-firefox mozilla-firefox-gnome-support -s
sudo: unable to lookup omega via gethostbyname()
postdrop: warning: unable to look up public/pickup: No such file or directory
Reading Package Lists... Done
Building Dependency Tree... Done
Suggested packages:
  latex-xft-fonts xprt-xprintorg
The following NEW packages will be installed:
  mozilla-firefox mozilla-firefox-gnome-support
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Inst mozilla-firefox (1.0.0+dfsg.1-6ubuntu1~4.10ubp1 Ubuntu Backports Project:warty-backports-staging)
Inst mozilla-firefox-gnome-support (1.0.0+dfsg.1-6ubuntu1~4.10ubp1 Ubuntu Backports Project:warty-backports-staging)
Conf mozilla-firefox (1.0.0+dfsg.1-6ubuntu1~4.10ubp1 Ubuntu Backports Project:warty-backports-staging)
Conf mozilla-firefox-gnome-support (1.0.0+dfsg.1-6ubuntu1~4.10ubp1 Ubuntu Backports Project:warty-backports-staging)

```
All resolve.

---

### Post by jdong on 2005-02-26
Terribly sorry, my ISP has been absolutely CRAPPY recently. I'll re-commit now.

---

### Post by ember on 2005-02-26
O.k. That explains why my firefox was dying a few moments ago ;)

---

### Post by Technoviking on 2005-02-28
I'm getting he following errors from the new package.

dbasinge@bubbahotep:/etc/apt $ sudo apt-get install mozilla-firefox mozilla-firefox-gnome-support
Reading Package Lists... Done
Building Dependency Tree... Done
The following packages will be upgraded:
  mozilla-firefox mozilla-firefox-gnome-support
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/9414kB of archives.
After unpacking 1284kB disk space will be freed.

Preconfiguring packages ...
(Reading database ... 117814 files and directories currently installed.)
Preparing to replace mozilla-firefox-gnome-support 1.0-2ubuntu4-warty99 (using .../mozilla-firefox-gnome-support_1.0.0+dfsg.1-6ubuntu1~4.10ubp1_i386.deb) ...
Unpacking replacement mozilla-firefox-gnome-support ...
Preparing to replace mozilla-firefox 1.0-2ubuntu4-warty99 (using .../mozilla-firefox_1.0.0+dfsg.1-6ubuntu1~4.10ubp1_i386.deb) ...
Unpacking replacement mozilla-firefox ...
Setting up mozilla-firefox (1.0.0+dfsg.1-6ubuntu1~4.10ubp1) ...
Installing new version of config file /etc/mozilla-firefox/pref/firefox.js ...
Updating mozilla-firefox chrome registry...E: /usr/lib/mozilla-firefox/extensions/installed-extensions.txt still present. Registration might have gone wrong.
mv: cannot stat `/usr/lib/mozilla-firefox/defaults.ini': No such file or directory
dpkg: error processing mozilla-firefox (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mozilla-firefox-gnome-support:
 mozilla-firefox-gnome-support depends on mozilla-firefox (= 1.0.0+dfsg.1-6ubuntu1~4.10ubp1); however:
  Package mozilla-firefox is not configured yet.
dpkg: error processing mozilla-firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mozilla-firefox
 mozilla-firefox-gnome-support
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dcstar on 2005-02-28
[QUOTE=Mike Basinger]I'm getting he following errors from the new package.
......./usr/lib/mozilla-firefox/extensions/installed-extensions.txt still present. Registration might have gone wrong.
mv: cannot stat `/usr/lib/mozilla-firefox/defaults.ini': No such file or directory
.......[/QUOTE]
I had the same problem.

I have the 1.0-2ubuntu4-warty99 installed (and had to roll back to that version), and that version installs successfully.

---

### Post by jdong on 2005-02-28
Remove mozilla-firefox with apt-get remove --purge mozilla-firefox mozilla-firefox-gnome-support

Then, 

sudo rm -rf /usr/lib/mozilla-firefox
sudo rm -rf /etc/mozilla-firefox


then, 

apt-get install mozilla-firefox mozilla-firefox-gnome-support



You will _NOT_ lose any personal settings.

---

### Post by ember on 2005-02-28
Does that fix problems with locale-versions, too?

---

### Post by dcstar on 2005-02-28
[QUOTE=jdong]Remove mozilla-firefox with apt-get remove --purge mozilla-firefox mozilla-firefox-gnome-support

Then, 

sudo rm -rf /usr/lib/mozilla-firefox
sudo rm -rf /etc/mozilla-firefox

then, 

apt-get install mozilla-firefox mozilla-firefox-gnome-support

You will _NOT_ lose any personal settings.[/QUOTE]
Did all of that and it seems to install (and work) ok.

All options and Plugins (bar Spellbound, which needs a re-install) still seem to be there, thanks!

---

### Post by jdong on 2005-02-28
[QUOTE=ember]Does that fix problems with locale-versions, too?[/QUOTE]

The already marked stable mozilla-firefox-locale-* should still work. If not, let me know.

---

### Post by ember on 2005-03-01
Well it doesn't work, yet it does ... if I try to install mozilla-firefox-locale-de I get:

Die folgenden Pakete haben nichterfüllte Abhängigkeiten:
  mozilla-firefox-locale-de: Kollidiert: mozilla-firefox (>= 1.0.0) aber 1.0.0+dfsg.1-6ubuntu1~4.10ubp1 soll instal liert werden
E: Kaputte Pakete

Yet I do have a german firefox, maybe because I installed the language pack seperately before.

Anyway it seems dependencies are broken for ff-locales.

---

### Post by jdong on 2005-03-01
I'll look into that.

---

### Post by jnoreiko on 2005-06-29
[QUOTE=jdong]You will _NOT_ lose any personal settings.[/QUOTE]

Actually, you will lose any extra searchplugins you've installed (the custom items for the search box in the toolbar).
That's a know problem with Firefox: those are installed in the application folder rather than the user profile.
They are stored in /usr/lib/mozilla-firefox/searchplugins/ , you can move them elsewhere and then restore them afterwards.

---

### Post by kenl on 2005-08-10
i am trying to remove and reinstall the never version of firefox but have no luck, either the lib/mozilla-firefox folder does not allow me to install to that directory or it does not update to the newer version.

im new to ubuntu by the way.

---

