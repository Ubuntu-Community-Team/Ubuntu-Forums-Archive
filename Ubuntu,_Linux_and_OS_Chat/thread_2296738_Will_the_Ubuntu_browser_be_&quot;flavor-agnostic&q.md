---
title: "Will the Ubuntu browser be &quot;flavor-agnostic&quot;?"
date: 2015-09-28
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2015-09-28
[Canonical's Ubuntu Web Browser Is Getting Much Better for Desktop Users]("http://news.softpedia.com/news/canonical-s-ubuntu-web-browser-is-getting-much-better-492896.shtml")> It's still too early to consider the Ubuntu web browser a contender for the likes of Google Chrome or Firefox, but it's getting there. A fresh batch of new features has just landed, and it includes novelties like an improved UI with tabs, text selection, and many others.Will it work with Kubuntu or Lubuntu?

---

### Post by night_sky2 on 2015-09-28
The lack of extension is probably what will prevent me from using this browser.

 I will stick with Firefox, which is open source and once stripped of it's needless features, is already very fast and decent for my needs.

---

### Post by grahammechanical on 2015-09-28
I think the Ubuntu Web Browser (A.K.A Browser) has been part of the default install of Ubuntu for a year there abouts. It has improved so much that I have taken to using it more than I use Firefox. I am using it now. It plays the video in that link. But I have yet to see it play a live Ubuntu On Air session. Although it will play the recorded sessions. I will try again with tommorow's session as a recent update on Wily Werewolf included code for Browser.

Anyway, it must surely be in the repositories if anyone using the flavours wants to do a test install.

Regards.

---

### Post by mystics on 2015-09-28
Tried it on Xubuntu after seeing this. It was either so slow as to be pointless or just doesn't work. My guess is it's the latter.

Doesn't take a long time to test, so if anyone else wants to try, just search for browser in Synaptic and install webbrowser-app.

---

### Post by mikodo on 2015-09-29
> **night_sky2 said:**
> The lack of extension is probably what will prevent me from using this browser.

 I will stick with Firefox, which is open source and once stripped of it's needless features, is already very fast and decent for my needs.

I intend to install Ubuntu 16.04 for the fun of watching it evolve. I'll  install Ubuntu browser then to look at it. But, because of the FF  extensions I too, probably wont use it right away.

I depend on the advice of others on these forums for tweaks to FF.

I can't find the Firefox Mega Thread that lovingliunux started. Is it still around?

If it is not updated much anymore, it would be nice if there was one for the "tweaks". I wouldn't fear so much I'll miss something like, I do now.

> **mystics said:**
> Tried it on Xubuntu after seeing this. It was either so slow as to be pointless or just doesn't work. My guess is it's the latter.

Doesn't take a long time to test, so if anyone else wants to try, just search for browser in Synaptic and install webbrowser-app.

I'll take your word for it. I just looked in Synaptic for its' dependencies  but, I didn't feel like messing with all the changes with my pristine Xubuntu 14.04.

---

### Post by vasa1 on 2015-09-29
> **mikodo said:**
> ...
I can't find the Firefox Mega Thread that lovingliunux started. Is it still around?
...
Here: [http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)

---

### Post by mikodo on 2015-09-29
Thanks, for that.

Looks like its' not too active.

Didn't it used be stickied?

---

### Post by vasa1 on 2015-09-29
> **mikodo said:**
> Thanks, for that.

Looks like its' not too active.

Didn't it used be stickied?
Welcome :)

True. In one way a mega thread is nice, but having specific threads may be more "searchable". IIRC, there was a bit of debate about another "one-stop" mega thread some years ago ;)

---

### Post by monkeybrain20122 on 2015-09-29
Actually it is not bad. Very fast and plays 1080p html5 videos on Youtube out of the box (needs to change some settings for resolution > 720p to show up for Firefox) and smoother than  Firefox. Flash doesn't work though also the url bar and control (going back etc) seem a bit buggy, but it has potential and seems very light. Is this based on Chromium?

---

### Post by mikodo on 2015-09-29
Didn't know about the debate.

I understand about the "searchable" argument though. That one of lovinglinux was huge. I do miss him greatly, none the less.

---

### Post by coffeecat on 2015-09-29
> **monkeybrain20122 said:**
> Is this based on Chromium?

It's built on WebKit, I believe, which leads to the slightly surreal experience of being told that I'm running Safari on Linux if I visit danasoft.com with my Ubuntu phone, or with the Ubuntu Web Browser in my desktop Ubuntu 15.04.

---

### Post by vasa1 on 2015-09-29
> **grahammechanical said:**
> I think the Ubuntu Web Browser (A.K.A Browser) has been part of the default install of Ubuntu for a year there abouts. ...

Anyway, it must surely be in the repositories if anyone using the flavours wants to do a test install.

Regards.
This is what I see with **apt-get install -s webbrowser-app**. A clean Lubuntu install will probably pull in more packages.
```
The following NEW packages will be installed:
  hud libcolumbus1 libcolumbus1-common libdbusmenu-qt5 libgsettings-qt1
  libhud2 liboxideqt-qmlplugin liboxideqtcore0 liboxideqtquick0
  libpocketsphinx1 libqt5feedback5 libqt5multimedia5 libqt5opengl5
  libqt5organizer5 libqt5positioning5 libqt5qml-graphicaleffects libqt5qml5
  libqt5quick5 libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5svg5
  libqt5webkit5 libqt5webkit5-qmlwebkitplugin libsphinxbase1 libthumbnailer0
  libunity-action-qt1 libunityvoice1 oxideqt-codecs
  qtdeclarative5-dialogs-plugin qtdeclarative5-privatewidgets-plugin
  qtdeclarative5-qtfeedback-plugin qtdeclarative5-qtquick2-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets
  qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-unity-action-plugin
  qtdeclarative5-window-plugin sphinx-voxforge-hmm-en sphinx-voxforge-lm-en
  ubuntu-ui-toolkit-theme unity-voice-service webbrowser-app
0 upgraded, 43 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by night_sky2 on 2015-10-01
> **mikodo said:**
> I intend to install Ubuntu 16.04 for the fun of watching it evolve. I'll  install Ubuntu browser then to look at it. But, because of the FF  extensions I too, probably wont use it right away.
Since I am using a Xfce, Midori is probably a better choice at this point for a lightweight WebKit browser. It already supports CSS 3, HTML5, Flash 11.2 and has a built-in adblocker.

I feel Christian Dywan and his team are doing a respectable job developping this small but mighty browser that can serves as a decent back up for the Big Boys.

> **monkeybrain20122 said:**
> Is this based on Chromium?

Nop. Chromium now use the Blink engine, a fork of Webkit. So that means users won't be able to tap into the Chrome Store for extensions..

Webkit was the precursor and is still maintained by Apple as well as the KDE community. 

Using a Webkit browser nowadays is reminescent of using Google Chrome in it's early days. Remember how it used to be lightning fast?

---

