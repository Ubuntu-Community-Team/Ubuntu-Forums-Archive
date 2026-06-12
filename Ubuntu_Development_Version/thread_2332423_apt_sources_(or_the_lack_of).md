---
title: "apt sources (or the lack of)"
date: 2016-07-31
forum: Ubuntu Development Version
---

### Post by izznogooood on 2016-07-31
#1 (Shotwell) Developer repo
```
Reading package lists... Done E: The repository 'http://ppa.launchpad.net/yg-jensge/shotwell/ubuntu yakkety Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.

```

Does this simply mean that they haven't made a yakkety package yet?
Is there a way to force installation of the Xenial package?

#2
I always switch default file-browser to nemo. (Exept handling the desktop which brakes unity handling backgrounds etc).

Well this isnt exactly a problem because it seems nemo is no longer dependant on the entire cinnamon desktop being installed. But i usually use this source: [http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html](http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html)

I did not notice the "apt release error" when i updated and simply "[COLOR=#000000][FONT=&amp]sudo apt-get install nemo nemo-fileroller".
[/FONT][/COLOR]This worked fine with the yakkety repositories.

---

### Post by Bashing-om on 2016-07-31
izznogooood; Yepper;

You got it. See:
[http://ppa.launchpad.net/yg-jensge/shotwell/ubuntu/dists/](http://ppa.launchpad.net/yg-jensge/shotwell/ubuntu/dists/)
shotwell has not made it to yakkety to this time.

Disable the source and await what might happen .. or ping the originator and see what the future may hold.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

