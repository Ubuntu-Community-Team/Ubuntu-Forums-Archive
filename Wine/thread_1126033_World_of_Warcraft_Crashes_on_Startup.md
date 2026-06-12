---
title: "World of Warcraft Crashes on Startup"
date: 2009-04-15
forum: Wine
---

### Post by Mandraix on 2009-04-15
I get to the launcher, everything's fine. Hit play and it starts to run WoW, but then it crashes and the WoW error box comes up asking me to send a log of my error to Blizzard. I can hear the WoW cinematic running in the background while this occurs. Keep in mind I just now installed WoW on Linux, and I'm not sure if I did something wrong during installation or if it's related to the recent 3.1 patch.

---

### Post by x001 on 2009-04-15
I am having the same problem with WoW. Running 9.04 on a Dell XPS 1530. Currently running the repair utility in WoW to restore everything to its defaults.

---

### Post by x001 on 2009-04-15
Got it to work. I created the Config.wtf file in the WTF folder in the wine World of Warcraft installation folder then added the following to the Config.wtf file:

```

SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "OpenGL"

```

See [http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378) for more help.

---

### Post by Mandraix on 2009-04-15
Thanks, this fixed it for me as well.

---

### Post by jnana on 2009-04-15
> **x001 said:**
> Got it to work. I created the Config.wtf file in the WTF folder in the wine World of Warcraft installation folder then added the following to the Config.wtf file:

```

SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "OpenGL"

```See [http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378) for more help.


just wanted to say thank you for this. initially 150 buffer didn't do the trick so i tried 500 which seemed to work but only for a time. 

i eventually came across this:

```
SET SoundMemoryCache "X"
```i reverted back to 150 buffer and chose a hefty 50mb cache. which reads as:

```
SET SoundMemoryCache "50"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
```this worked well for about 3 minutes then another crash. now when i restart with the same settings it immediately crashes when i log into my character.

can anyone shed any light on what may be causing my crashes?

btw [here's an excellent]("http://www.wowwiki.com/Config.wtf_defaults"), though partially outdated, reference for config file settings.

---

### Post by x001 on 2009-04-15
Have you tried the "Reg tweak" from [http://ubuntuforums.org/showthread.php?t=579378?](http://ubuntuforums.org/showthread.php?t=579378?)

---

