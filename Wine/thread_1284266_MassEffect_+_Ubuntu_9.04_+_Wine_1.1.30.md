---
title: "MassEffect + Ubuntu 9.04 + Wine 1.1.30"
date: 2009-10-06
forum: Wine
---

### Post by Lordest on 2009-10-06
Hi there,

I've successfully installed Mass Effect with wine version written in thread name.

But when I started to play, I've got this problems:

1) Mouse is functionless 

- on wine webpage i've read that people fixed it with this patch:
[http://bugs.winehq.org/attachment.cgi?id=21554](http://bugs.winehq.org/attachment.cgi?id=21554)

but I'm really don't know what can I do with that :confused:,
I'm typing that it's something to add to some file. But problem is that there isn't written where can I add it (if is it, i'm so sorry, can you warn me for that pls?).

2) Game in graphic page are very slowly, and bad. People wrote that to play this game is needly Virtual C++ and DirectX 9.0. DirectX is OK but when I'm trying to install VC, setup is always failing and I don't know why. So do you have some tutorial to how install the VC? 

( 
set wine libraries:
"d3d10"="native,builtin"
"d3d8"="native,builtin"
"d3d9"="native,builtin"
"d3dx10"="native,builtin"
"d3dx8"="native,builtin"
"d3dx9"="native,builtin"
"ddrawex"="native,builtin"
"devenum"="native,builtin"
"dinput8"="native,builtin"
"dmband"="native,builtin"
"dmusic"="native,builtin"
"dplay"="native,builtin"
"dplayx"="native,builtin"
"mscoree"="native,builtin"
"streamci"="native,builtin"
)

If isn't problem in VC, in hardware problem surely isn't you can check it xD:

Intel Core Duo 2.33 ghz - cpu
Gigabyte NVIDIA GTX 260 - gpu
A-Data 2x1 gb kit - ram

.. 

something more about that game in wine you can find it on wine page of it here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12301&iTestingId=44468](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12301&iTestingId=44468)

thank you so much

---

### Post by asdfoo on 2009-10-06
> **Lordest said:**
> Hi there,

I've successfully installed Mass Effect with wine version written in thread name.

But when I started to play, I've got this problems:

1) Mouse is functionless 

- on wine webpage i've read that people fixed it with this patch:
[http://bugs.winehq.org/attachment.cgi?id=21554](http://bugs.winehq.org/attachment.cgi?id=21554)

but I'm really don't know what can I do with that :confused:,
I'm typing that it's something to add to some file. But problem is that there isn't written where can I add it (if is it, i'm so sorry, can you warn me for that?).

2) Game in graphic page are very slowly, and bad. People wrote that to play this game is needly Virtual C++ and DirectX 9.0. DirectX is OK but when I'm trying to install VC, setup is always failing and I don't know why. So do you have some tutorial to how install the VC? 

( 
set wine libraries:
"d3d10"="native,builtin"
"d3d8"="native,builtin"
"d3d9"="native,builtin"
"d3dx10"="native,builtin"
"d3dx8"="native,builtin"
"d3dx9"="native,builtin"
"ddrawex"="native,builtin"
"devenum"="native,builtin"
"dinput8"="native,builtin"
"dmband"="native,builtin"
"dmusic"="native,builtin"
"dplay"="native,builtin"
"dplayx"="native,builtin"
"mscoree"="native,builtin"
"streamci"="native,builtin"
)

If isn't problem in VC, in hardware problem surely isn't you can check it xD:

Intel Core Duo 2.33 ghz - cpu
Gigabyte NVIDIA GTX 260 - gpu
A-Data 2x1 gb kit - ram

.. 

something more about that game in wine you can find it on wine page of it here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12301&iTestingId=44468](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12301&iTestingId=44468)

thank you so much


Don't set those libraries to native...

No need to install visual C++ runtime unless you are getting an error (the game would likely not start at all).

You don't mention which version of Wine you use or the video card and drivers?  Upgrade to Wine 1.1.30 and retest if not already.

---

### Post by Lordest on 2009-10-07
> **asdfoo said:**
> Don't set those libraries to native...

No need to install visual C++ runtime unless you are getting an error (the game would likely not start at all).

You don't mention which version of Wine you use or the video card and drivers?  Upgrade to Wine 1.1.30 and retest if not already.

ok I'll set it for bulletin only, but by me isn't problem in that.

I'm using version 1.1.30, the video card / gpu / graphic card I've written (NVIDIA GFX 260, used nvidia default driver version 180 found by Hardware Drivers software in Ubuntu)

I don't understand it cuz other games are going OK. For sure it's and it'll go little bit slower than on win, but it's just for game developers what I understand, but why it's really so slowly (in first movie is like a 1 block, 10 sec. pause, 1 block, 10 sec. pause) ? It's not okay.

btw.: some types for mouse problem aren't :/, cuz if I fix the problem of the graphics, it'll be uselessly cuz mouse won't working :(..? 

thx

---

### Post by Lordest on 2009-10-13
any ideas? I really wanna play this game :(

---

### Post by maaddog on 2009-10-28
Hiya Lordest,

Still need help ? I just fixed the texture issue, got the mouse clicks working and working on getting the mouse turning working..

For the texture issue, if you have a nvidia card use 190.42

For the "i cant click anything issue" use:

[Software\\Wine\\DllOverrides]
"dinput"="native,builtin"
"dinput8"="native,builtin"

And be sure to have the DLL loaded

For the cant unable to turn properly, its supposed to help if you use:
WINEFORCEMOUSEWARP=yes wine "program"

Game runs and looks perfect now, just still have issues turning.. trying to sort it now. msg me if you need more help :)

---

### Post by maaddog on 2009-11-12
If anyone is interested, using wine 1.31.1 with the mousfix patch and mousewarp enabled, I finished MassEffect and it was great.

What a great game, which now runs almost perfectly under Wine, like me anyone who missed this should pick it up. It takes a little while to get everything right, then the game plays smoothly all the way through.

---

