---
title: "World of Warcraft, NVIDIA, and my angst."
date: 2010-12-03
forum: Wine
---

### Post by Czarcasmo on 2010-12-03
Hello!

I followed the guide found over [here]("https://help.ubuntu.com/community/WorldofWarcraft") to install World of Warcraft on my Ubuntu 10.10 box. I activated the propriety drivers for my video card (9800GTX+) and I'm able to play just fine. The issue I am having is that the video settings in WoW won't let me move anything above the very lowest setting. Is there anything that can be done to remedy that? 

I've tried looking through the forums, but didn't see anything directly addressing this problem. If there is, please call me an idiot and direct me in the proper direction. 

Thanks!
Cz.

---

### Post by Cavillis on 2010-12-03
You can change the graphics settings via text commands in the chat window:
[http://www.wowwiki.com/Console_variables#Graphics](http://www.wowwiki.com/Console_variables#Graphics)

to use these commands in game:
/console <command> <value>[FONT=monospace]
[/FONT]/console extShadowQuality *5*

---

### Post by cwwilson721 on 2010-12-03
> **Czarcasmo said:**
> Hello!

I followed the guide found over [here]("https://help.ubuntu.com/community/WorldofWarcraft") to install World of Warcraft on my Ubuntu 10.10 box. I activated the propriety drivers for my video card (9800GTX+) and I'm able to play just fine. The issue I am having is that the video settings in WoW won't let me move anything above the very lowest setting. Is there anything that can be done to remedy that? 

I've tried looking through the forums, but didn't see anything directly addressing this problem. If there is, please call me an idiot and direct me in the proper direction. 

Thanks!
Cz.
Unfortunately, since we use the opengl driver, most of the eye-candy doesn't work.

Personally, I don't care if it does. I'd rather have the screen look 'ugly' (with some effects for aoe, etc), and have better FPS than Windows, than look real pretty, and have lower FPS.

Which would you rather have happen:
[LIST]
[*]Lich King looks GORGEOUS, sparkly, neat shadows, and get the raid wiped because your framerate was so low you didn't see the puddle o' goo you were standing in, or
[*]OK graphics, nothing too cool, but busting 100+FPS ?
[/LIST]Gimme the FPS

Until Blizzard does a better job with their opengl drivers, we OWN Windows FPS. And Windows OWNS 'pretty pictures'.

Nothing you can do for now. Except try to run in D3D, and get crappy video issues (black areas, ripping, tearing, streaks, LOW FPS, etc)

---

