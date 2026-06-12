---
title: "WC3/Wine problems"
date: 2007-07-28
forum: Ubuntu Gamers Arena
---

### Post by Reneagde222 on 2007-07-28
So I got Warcraft III: The Frozen Throne going in wine...

However it goes at about 1FPS...

My PCs specs are

2.13GHz Dual Core

2GB RAM

7900GT

I get 100% smooth framerates in huge battles on windows.

I have tried OpenGL mode to increase framerate, but it crashes Ubuntu (no error).

Turning graphics settings down does nothing...

I use this command to run it:

wine explorer /desktop=tft,800x600 "Z:\media\XP\Program Files\Warcraft III\Frozen Throne.exe"

Please help!

---

### Post by zeller on 2007-07-28
I just tried the Warcraft III (original) with Wine and it was quite a bit sluggish for me too, at first.

Then I went into the settings and put my resolution to 1024x768. Immediately it ran smoothly. Try that.

My native desktop res is 1440x990 Widscreen. But the above res allowed it to work at full speed.

---

### Post by Sindwiller on 2007-07-31
What Wine version are you running?  (output it with 'wine --version')

You're probably running an old Wine release. I suggest you try the latest first. WC3/TFT works for me.

Add this to your /etc/apt/sources.list :

```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
```

(if you're running Feisty of course...)

And make a ```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

