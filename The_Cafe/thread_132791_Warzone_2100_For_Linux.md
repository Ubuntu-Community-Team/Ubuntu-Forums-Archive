---
title: "Warzone 2100 For Linux"
date: 2006-02-19
forum: The Cafe
---

### Post by TechSonic on 2006-02-19
Awesome game isn't it? I'm sure that many of you who used Windows in the past remember Warzone 2100.

The game that puts Netpanzer to shame.

[http://www.linux-gamers.net/modules/news/article.php?storyid=816](http://www.linux-gamers.net/modules/news/article.php?storyid=816)


Make sure you run the game using the Sudo command, or else you can't use multiplayer or save your game in single player.

No full screen option, or at least I couldn't find it.  Apparently most sites TODO lists are talking about screen resolution detection.. This will help for those who don't want to use 24 bit color depth, right now you have to use it (Configure xorg.conf).  In the future, I hope to see full screen.

---

### Post by -Rick- on 2006-02-19
Warzone is indeed pretty cool.

> Make sure you run the game using the Sudo command, or else you can't use multiplayer or save your game in single player.
Why? How did you installed it? I never run it as root...

> No full screen option, or at least I couldn't find it. Apparently most sites TODO lists are talking about screen resolution detection.. This will help for those who don't want to use 24 bit color depth, right now you have to use it (Configure xorg.conf). In the future, I hope to see full screen.
Press ALT+ENTER

---

### Post by TechSonic on 2006-02-20
[QUOTE=-Rick-]Warzone is indeed pretty cool.


Why? How did you installed it? I never run it as root...


Press ALT+ENTER[/QUOTE]



ALT + ENTER = No Effect
home\.warzone file permissions need to be changed or else you use sudo.

---

### Post by -Rick- on 2006-02-20
hmm...ALT+enter always worked fine for me(on ubuntu, gentoo and freebsd). Anyway reading the readme you can also start it with a few commandline parameters:
```

NOTES
======
	- some useful command line parameters:
		-window
		-fullscreen
		-widthxheight (e.g. -640x480, -800x600, -1024x768 ...)

```

So starting it with '-fullscreen' should also work.

As for the permissions, did you run it with sudo for the first time? AFAIK sudo doesn't change the $HOME variable, so programs think that (even when you run as root) your home dir is still the same. That way when warzone creates the settings dir it will create it as root and thus you cannot use it as a non-root user. Simple fix:
```

sudo chown usernamahere ~/.warzone

```

---

