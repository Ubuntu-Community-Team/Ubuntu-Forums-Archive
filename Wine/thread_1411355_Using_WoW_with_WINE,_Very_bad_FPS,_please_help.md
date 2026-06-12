---
title: "Using WoW with WINE, Very bad FPS, please help"
date: 2010-02-19
forum: Wine
---

### Post by Like67ninjas on 2010-02-19
Ok, so first and foremost  im sorry that im possibly making a repost from something someone else has already asked, but I've been at work all day, im frustrated, I just want to get this fixed.  Please dont flame me, help me, if you dont have something useful to say in response to my post in regards to getting the issue fixed, please dont waste your time and my patience.

Ok, SO, I just put WoW on my computer, with Wine, and everything was going good, nice gameplay, seemed better than when I used to play on windows, great fps, no lag, but now, for whatever reason, im running at about 5-10 fps at all times and it makes it hard to get any sort of questing or instance healing done.  Is there something I can do via wine, or terminal to fix this, I deleted add ons, restarted ect, but still have these horrible frame rates. My video settings are low, I dont have anything running in the background, Idk what more to do.  I read that people had things running in the background, or left there computer on for some time and when they restarted it worked, but it didnt make a difference for me, please help, anything useful would be great. Thanks in advance.

---

### Post by sickly on 2010-02-19
FIRST OF All you are posting this in the wrong place. second, dont come into these forums and act like you did some searching and lol no im just kidding.

---

### Post by brian70809 on 2010-02-19
ok.. you are in the right place.. This is the WINE forum in Ubuntu...

You need to make sure you are running in OPENGL mode..   There is a WIKI on how to do this.. you are probably running in DirectX mode.. which is slow slow slow for you.

one way to do this is to put a flag at the end of your wow run line..


wine wow.exe -opengl

another is to edit you config file. so it does it on its own everytime.


Good luck!

---

### Post by Like67ninjas on 2010-02-22
> **brian70809 said:**
> ok.. you are in the right place.. This is the WINE forum in Ubuntu...

You need to make sure you are running in OPENGL mode..   There is a WIKI on how to do this.. you are probably running in DirectX mode.. which is slow slow slow for you.

one way to do this is to put a flag at the end of your wow run line..


wine wow.exe -opengl

another is to edit you config file. so it does it on its own everytime.


Good luck!

could you tell me what I would need to do to my config file?

---

### Post by hikaricore on 2010-02-22
If I'm not mistaken the opengl flag no longer works in the conf file.

Just add:

-opengl

To your wow launcher or try it from a terminal.


It's also possible that you have really crappy video hardware with next to no OpenGL support.

---

### Post by brian70809 on 2010-02-23
go here:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

in the config.wtf file in the WTF folder.. add this line

SET gxApi "opengl"

---

