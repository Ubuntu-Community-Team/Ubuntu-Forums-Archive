---
title: "Konqueror Vs Firefox 3.5.5"
date: 2009-12-11
forum: Security
---

### Post by jessiebrownjr on 2009-12-11
I got bored so I figured I would go from 32bit gnome jaunty to 64 bit KDE jaunty, and I guess I was unaware of all the differences.. I don't really like the Konqueror browser and am debating installing the 3.5.5 from the mozilla site.. How safe/unsafe is this action?

I haven't look yet to see if there is a firefox in the repos because I was upgrading other stuff and the internet at work is like 100k slow :-(

---

### Post by lovinglinux on 2009-12-11
KDE has a Firefox installation link in the Internet menu, but you can also install via command:

```
sudo apt-get install firefox
```

Installing Firefox from Mozilla is safe. Lots of people do that, when a new major release is not available in the repositories. Nevertheless, since you are running KDE, it might need some dependencies. So I recommend installing from the repositories.

---

### Post by FuturePilot on 2009-12-11
> **lovinglinux said:**
> KDE has a Firefox installation link in the Internet menu,

That's new in Karmic. OP is talking about Jaunty.

---

### Post by jessiebrownjr on 2009-12-12
I did sudo apt-get install firefox 3.5, and it installed/downloaded alot of crap, but the browser that got installed was 3.0... bleh
im tired of KDE anyway...

---

### Post by lovinglinux on 2009-12-12
> **FuturePilot said:**
> That's new in Karmic. OP is talking about Jaunty.

:oops: Sorry for the total lack of attention

> **jessiebrownjr said:**
> I did sudo apt-get install firefox 3.5, and it installed/downloaded alot of crap, but the browser that got installed was 3.0... bleh
im tired of KDE anyway...

See the **Installing Other Versions** section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

You could also give Ubuntu 9.10 Karmic Koala a try. I have installed kde-minimal over a command-line only installation of Ubuntu from the alternate CD and it works great.

---

### Post by judge jankum on 2009-12-12
We had some bugs with 3.5.5 so we went back to 3.0.15 and it works fantastic... People always say if it ain't broke don't fix it, we listen close these days...

---

### Post by lovinglinux on 2009-12-12
> **judge jankum said:**
> We had some bugs with 3.5.5 so we went back to 3.0.15 and it works fantastic... People always say if it ain't broke don't fix it, we listen close these days...

I agree with "if it ain't broke don't fix it", but in fact Firefox 3.5 is much faster and better than 3.0. Check it out my browser benchmark chart (higher is better):

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=124167&stc=1&d=1249840668[/IMG]

> Note: "Firefox 3.5 optimized" is the official final version from Mozilla, compiled from source with optimization flags for my processor family. PGO (Profile-Guided Optimization) is also used since July 5th tests. The **w/ext** means "with extensions installed"

These benchmarks were made since Jaunty install. The increased benchmark values for each version are due to Ubuntu and Firefox optimizations.

I'm currently using Karmic with a new dual core processor (tests were made on a Pentium 4 3.06 GHz HT), so I'm not updating that chart. Nevertheless, my score of a vanilla Firefox 3.5.5 with more than 40 extensions installed is now about 1800 points.

---

### Post by judge jankum on 2009-12-12
It was faster on ours but kept freezing (old hardware I guess) But for some reason it just wouldn't work...But the good thing about Ubuntu, if one version of something dosn't work another usually will....

---

### Post by SuperSonic4 on 2009-12-12
Have you tried **Arora** or **ReKonq**? Both are designed in Qt and IMO have better functionality than konqueror.

You can download firefox from mozilla and it's perfectly safe as, in windows, mozilla handle the updates.

---

### Post by judge jankum on 2009-12-12
How is the security on these? I'm always open minded"  > **SuperSonic4 said:**
> Have you tried **Arora** or **ReKonq**? Both are designed in Qt and IMO have better functionality than konqueror.

You can download firefox from mozilla and it's perfectly safe as, in windows, mozilla handle the updates.

---

### Post by SuperSonic4 on 2009-12-12
I've not tried Rekonq so I cannot tell you about that

Arora has security at least equivalent to firefox as far as I know. It has an adblock and flashblock built in but as of yet addons are lacking

---

### Post by jessiebrownjr on 2009-12-12
karmic is out of the question for me, both of my PCs are allergic to it it seems. I will most likely just go back to gnome :-(

---

### Post by nortexoid on 2010-01-06
Konquerer's a very nice browser actually, and I like the fact that it uses KDE Wallet instead of its own crappy/insecure password management system (pointing at Firefox). And it's far better than any GTK-native browser (like Midori or Epiphany)! Whether or not it's better than Firefox is another matter. (I don't think it is. But it's still nice!)

You could add the mozilla daily PPAs to get the latest unstable builds of Firefox, or just download it using KPackageKit. Don't install gnome support, obviously.

---

### Post by lovinglinux on 2010-01-07
> **nortexoid said:**
> Konquerer's a very nice browser actually, and I like the fact that it uses KDE Wallet instead of its own crappy/insecure password management system (pointing at Firefox). 

You can integrate Firefox with Kwallet using [KDE Wallet password integration](https://addons.mozilla.org/en-US/firefox/addon/49357) extension. Works like a charm.

---

### Post by doublewitt on 2010-01-21
Actually, I prefer the Konqueror/File Manager over Firefox. I don't need the endless addons but you can configure Konqueror to use Firefox addons as well. Another point about Konqueror that I like is that I can configure my home page to show all my bookmark folders. That's handy, and I like the quick access it offers.

---

