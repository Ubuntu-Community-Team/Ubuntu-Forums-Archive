---
title: "[Kubuntu] Firefox does not follow proxy settings"
date: 2012-01-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ft_ on 2012-01-23
Hi,

When I set the correct parameters for my proxy, Konqueror is ok on the web.
But Firefox isn't. I have to set the FF proxy parameters separately.

In my former Oneiric install, this point was ok.

1- happen to somebody ?
2 - workaround ?
3 - thanks !

---

### Post by JMB74 on 2012-01-23
Have you got the package [COLOR=DarkGreen]**firefox-kde-support**[/COLOR] installed?

---

### Post by stefangr1 on 2012-01-23
In Firefox, go to Firefox -> Preferences -> Network -> Settings.

Is "use system proxy" selected?

---

### Post by ft_ on 2012-01-24
Thanks for your help.

1- the firefox-kde-support is installed
2- the firefox proxy settings are correct ("use system settings")

I upgraded from Oneiric, these two points did not change after upgrade.
I noticed that Google Earth seems to suffer the same issue, so I do not think this bug to be firefox-related.
May be gtk apps related ?

---

### Post by chrisccoulson on 2012-01-24
It probably doesn't work because we dropped the huge KDE integration patches from Firefox in precise

---

### Post by lucazade on 2012-01-24
firefox in kde precise works with proxy using manual settings while chromium doesn't work.
any idea?

---

### Post by kostacooker on 2012-03-15
I got the same problems chrome, chromium, firefox not working with kde proxy settings, while e.g. konqueror, rekonq works flawless.

Workarounds are to:
for firefox) set the proxy manually in firefox settings
for chrome/chromium) start it on the commandline with google-chrome --proxy-server=host:port << more settings are available for exceptions etc.

I upgraded my System from lucid to precise. It all worked fine in before the upgrade.

Another strange thing is that proxy settings seem to have *some* effect on the browser, if i take that laptop home (no proxy) chrome etc. still won't work until I disable proxy settings in kde-systemsettings. So browsers are not ignoring, but they simply are not able to get the settings right. I guess something has been changed in kde-proxy-settings.

The workarounds mentioned above are hackish -> no real solution.

Is there a bug-ticket raised on launchpad for this issue ?

---

