---
title: "Server fonts"
date: 2010-12-05
forum: Server Platforms
---

### Post by JasonFWard on 2010-12-05
I am attempting to get [GeniusTrader](http://www.geniustrader.org/) working on Ubuntu server.

A bit of a tall order partly because the installation instructions are both sparse and out of date and because the installation instructions presume you installing on a desktop machine, however, there is no fundamental reason (that I know of) that means [GeniusTrader](http://www.geniustrader.org/) cannot run on a headless server.

But the latest problem I have run into is [GeniusTrader](http://www.geniustrader.org/) expects the msttcorefonts to be installed so that it can include them in the graphic images it generates.

But I don't seem to be able to install them :-( attempting to install them as per the [help](https://help.ubuntu.com/community/RestrictedFormats)

```
root@lamp /home/gt# apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras
```

[These instructions](http://en.kioskea.net/faq/1140-installing-truetype-fonts-under-ubuntu) don't seem to make any logical sense to me.  [The wiki](https://wiki.ubuntu.com/Fonts) just eventually me back to the [help](https://help.ubuntu.com/community/RestrictedFormats).  [These instructions](http://www.cyberciti.biz/tips/linux-howto-install-truetype-freetype-and-msttcorefonts-fonts.html) which are referred to be the [GeniusTrader](http://www.geniustrader.org/wiki/geniustrader:configfile) don't work either.

Any other ideas?  Anyone can help me?

---

### Post by SeijiSensei on 2010-12-05
Try running "sudo apt-get update" then try again.

---

