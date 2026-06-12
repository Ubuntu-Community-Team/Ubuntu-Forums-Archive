---
title: "Amazon/youtube using the Ubuntu web browser by default?"
date: 2014-02-10
forum: Ubuntu Development Version
---

### Post by prana on 2014-02-10
These webapps used to use the default web browser installed before and have recently started using the Ubuntu web browser. Seems like a wierd decision considering that using the default web browser allows for better control (like using the adblock extension - especially on Youtube).

Any reason why or better yet, any way to revert to these webapps using the default browser?

I am using Ubuntu 14.04 fully updated.

---

### Post by Mateusz Stachowski on 2014-02-11
I like it that webapps are finally apps on their own and they don't open in a tab of my browser. Also this was always the desired behavior.

[https://bugs.launchpad.net/unity-webapps-qml/+bug/1207515](https://bugs.launchpad.net/unity-webapps-qml/+bug/1207515)

> For S, in order to simplify the maintenance and have more control over the chromeless runtime environment, we will deprecate most of the browser integration (tabs) and let the webapps run directly using the webbrowser-app as a container.

If you want the integration with default browser maybe try installing unity-firefox-extension or unity-chromium-extension.

---

### Post by prana on 2014-02-11
I agree that using the ubuntu web browser is a good thing (including from a convergence perspective) but some sort of adblock software needs to be added to the ubuntu browser. I am just not used to looking at ads on amazon or youtube.

---

### Post by mc4man on 2014-02-11
Not sure how it *currently* can be considered a good thing on non touch Desktop installs..
(at least here webbrowser app is nowhere ready for use other than an occasional curiosity.

Also it seems this commit 2 months ago was either a bit premature or wishful thinking, (though they still have 8 weeks or so to make something useful - 
> libunity-webapps (2.5.0~+14.04.20131108.2-0ubuntu1) trusty; urgency=low

  [ Robert Bruce Park ]
  * Depend on webbrowser-app so it can become the default in Trusty.
....
- Ubuntu daily release <ps-jenkins@lists.canonical.com>  Fri, 08 Nov 2013 20:04:41 +0000


---

### Post by grahammechanical on 2014-02-11
Is Ubuntu Web Browser now able to play videos? I have never been able to get it to do that. Have I missed something?

If Browser proves to be lighter on resources than other browsers then it might be a good idea for it to be default for playing audio and video content from online. Otherwise I agree that there is a lot of work to do to bring some of these phone apps up the same specification as the desktop rivals. I have seen google hangouts where the design team have discussed what needs to be done with these phone apps for convergence.

Based upon something that Jono Bacon said in his Q & A this evening, matters like this are up for discussion but decisions will be taken at the appropriate time based upon the quality of the applications. In other words, the usual decision making process.

Regards.

---

### Post by mc4man on 2014-02-11
> **grahammechanical said:**
> Is Ubuntu Web Browser now able to play videos? I have never been able to get it to do that. Have I missed something?

I can get it to easily  play 1 online video per 'instance', then run into some  issues due to no real l. click/keyboard support
(some keys 'do' things, like q seems to go backwards in a vid, r forward, ect.
Edit : backspace also seems to work though somewhat limited in value though it does allow one to select another link/vid

---

### Post by vasa1 on 2014-02-11
> **prana said:**
> ... but some sort of adblock software needs to be added to the ubuntu browser. I am just not used to looking at ads on amazon or youtube.
If that isn't done, there's going to be muck flying ...

---

### Post by Mateusz Stachowski on 2014-02-12
I found a way to launch webapps in default web browser. You have two options launching from terminal using the command to specify running with default browser or editing the desktop shortcut and adding that parameter.

```
unity-webapps-runner -c 'webbrowser-app' -n 'RGVlemVy' -d 'deezer.com' %u
```

This will launch Deezer in my default browser which is Chrome.

```
$ unity-webapps-runner --help
Usage:
  unity-webapps-runner [OPTION...] - Activate Unity WebApps


Launches a standalone webapp given a domain and a name (e.g. "unity-webapps-runner -n 'VHdpdHRlcgA=' -d 'twitter.com'").


Help Options:
  -?, --help         Show help options


Application Options:
  -n, --name         Application name (base64 encoded)
  -d, --domain       Application domain
  -a, --amazon       Launch amazon (with geoclue store selection)
  -h, --homepage     Launch a webapp directly from its homepage
  -i, --app-id       Launch a webapp with a specific APP_ID
  -c, --chrome       Launch a webapp in default browser

```

The desktop shortcuts are in /usr/share/applications they can be edited with text editor but of course only with root privileges.

Also does anyone have this file enable-webapp-container in ~/.local/share/unity-webapps hidden directory in your home folder.

[https://bugs.launchpad.net/libunity-webapps/+bug/1036726/comments/10](https://bugs.launchpad.net/libunity-webapps/+bug/1036726/comments/10)

> If you enable the new container mode, you will get a dedicated browserinstance per webapp. Each instance has its own set of
cookie/password/history databases. So you should be able to read
professional emails when logged as user A, and still be able to read
news (or other emails) when logged as user B, without having to use 2 or
3 different browsers.


To enable the new container mode, do:


apt-get install webbrowser-app
touch ~/.local/share/unity-webapps/enable-webapp-container


You will have to re-create your .desktop shortcuts, as the new mode
requires an extra property in it (the StartupWMClass paramater).


Then, each webapp will run in its own browser container.


To get back to using the default browser, just remove the configuration
file.

---

