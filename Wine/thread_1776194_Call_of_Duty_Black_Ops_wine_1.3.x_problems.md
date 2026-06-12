---
title: "Call of Duty: Black Ops wine 1.3.x problems"
date: 2011-06-05
forum: Wine
---

### Post by venom104 on 2011-06-05
I've been having a HUGE amount of trouble trying to play Black Ops on my computer. I had Black Ops installed on my system before, and it worked FINE; great framerate, few lag spikes, and a good FPS. Then I decided to update my system (which included a wine update), then everything went haywire. When I updated my system (including wine upgraded to wine 1.3.21) Black Ops no longer worked, whenever I would start the game, the mouse cursor would simply spin around and around; when I tried running it in a virtual desktop black ops would no longer accept keyboard input.

So after all that, I decided to go back to my original wine version (wine 1.3.7). Now the real problem starts. I kept getting this error (could not find could not find plugplay.exe) and nothing would run under wine, so I did a rm -rf ~/.wine, and reinstalled wine. Wine programs now ran, but Black Ops wouldn't even open! So after that I decided to upgrade to 1.3.8, still didn't open. Upgraded to 1.3.9, still didn't open. Upgraded to 1.3.12, still didn't open. Upgraded to 1.3.18, still didn't open. After all that, I found a version of wine that would actually run black ops again, 1.3.19, but now when I play black ops, the performance is TERRIBLE, not to mention that the game sound is messed up (I followed the directions from here **[http://appdb.winehq.org/objectManager.php?sClass=version&iId=21910](http://appdb.winehq.org/objectManager.php?sClass=version&iId=21910))** to set the dsound dll to native, and set the UseGLSL to disabled, and the performance and sound problems didn't go away. 

I tried using PlayOnLinux to allow me to install wine 1.3.8 and let me run it under that version, but it always gets stuck in installing DIRECTX. 

I'm at the end of my rope here, the only game I play is Black Ops, and this is keeping me from using Ubuntu 10.04 as my only operating system. I've been using the wine packages from here, [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html). Any advice on what to do would be greatly appreciated. I just want this stupid game to work.

---

### Post by venom104 on 2011-06-05
I forgot to say that my goal is to run black ops under 1.3.8 again. If this can't be done without a reinstall then I'll happly take another solution.

---

### Post by 8Kuula on 2011-06-06
> **venom104 said:**
> When I updated my system (including wine upgraded to wine 1.3.21) Black Ops no longer worked, whenever I would start the game, the mouse cursor would simply spin around and around; when I tried running it in a virtual desktop black ops would no longer accept keyboard input.

alt+tab some other window and back enables keyboard input.

---

