---
title: "SC2 Multi-Player Crash Problem"
date: 2011-06-14
forum: Wine
---

### Post by sir.sargento on 2011-06-14
Hola,

Before I say anything a little info about what I'm running. I am using natty 11.04, wine 1.2.3, and my video card is a ATI Radeon HD 3450, (I am using the proprietary drivers). The game runs great for the most part except for some times when I join a multi-player game. Sometimes after all of the people in the game have loaded the maps instead of taking me to the game it will just crash and go straight back to my desktop. However it doesn't do this on all games I join. Id say I get in every 4 out of 5 games successfully.

I am starting to wonder if it is certain maps that conflict with my computer or what. Anybody else had this problem? Any ideas how to fix it? If you need additional information just let me know.

Thank you

---

### Post by desktorp on 2011-06-14
Do you notice any consistency with player counts on the games which crash?  Like, is it always the biggest games that do it?  Some people have noted general performance issues with multiplayer games, when "lots of people start joining" ..

At any rate, terminal output is probably one of the best bets to narrow down the problem(s) since it's just shooting you straight back to the desktop, with no dialogs.

You could also try Wine 1.3 as a knee-jerk reaction.

---

### Post by sir.sargento on 2011-06-15
Thanks for the reply. Anyways I have tried using 1.3 and for some reason I have sound issues using it so I have been stuck with 1.2.3. Usually the games are small games with no more than 4 people involved as I only play 1v1 or 2v2. And where can I see the terminal output as you suggest? or what do you mean? Should I try launching from terminal? Ive been using a launcher I have made on the unity sidebar.

Thanks again.

---

### Post by desktorp on 2011-06-15
Yes when you launch from the terminal, it should stay open in the background.  This way, when it crashes, you should get some sort of output, instead of just finding yourself suddenly back at the desktop.  It's also sometimes revealing to see how many errors are happening, *without* crashing.  I'll admit though, I have a rotten time making sense of crash logs.  May end up needing a wine expert.  (a wino!)

---

### Post by sir.sargento on 2011-06-16
Thanks for the tip. I will now start launching the game from terminal so I can post some errors here. I can see what you said about terminal revealing how many errors are happening without crashing. It seems I was getting a lot of these last time I played 

fixme:d3d_shader: print_glsl_info_log     Vertex shader(s) linked, fragment shader(s) linked.
fixme:d3d_shader: print_glsl_info_log Error received from GLSL shader #472:
fixme:d3d_shader: print_glsl_info_log     Vertex shader(s) linked, fragment shader(s) linked.

Anyways, next time it crashes I will post some information here and hopefully I can get it solved.

Thanks again

---

### Post by desktorp on 2011-06-16
More guessing on my part, but this may be a problem with your ATi card and GLSL.  You might try disabling GLSL and see if this helps or hurts anything.  (I think you have to do it through the registry, but give it a glance and see what you can dig up)

---

### Post by sir.sargento on 2011-06-17
> **desktorp said:**
> More guessing on my part, but this may be a problem with your ATi card and GLSL.  You might try disabling GLSL and see if this helps or hurts anything.  (I think you have to do it through the registry, but give it a glance and see what you can dig up)

hrmmm.. I am unaware of how to do this. Time to google it I guess :)

P.S. I am a wine noob. The only other game I've tried playing through wine is WoW and that pretty much worked perfectly without any tweaks.

---

### Post by desktorp on 2011-06-18
It would be in Wine's registry..
from wiki.winehq.org:
**HKEY_CURRENT_USER\Software\Wine\Direct3D\UseGLSL  ->  "disabled"**   (it is case sensitive) 

If you're a noob, I'm a boob. ;) ..so don't be surprised if it does not work.  (be prepared to re-enable it right away :D )

---

### Post by sir.sargento on 2011-06-20
Awesome, havent been able to play any SC until today but I will try disabling that and see if it helps any. Just a few minutes ago I was playing a single player challenge mission and when it went to load the mission I crashed. These are the last few lines from the errors in terminal.

fixme:d3d_shader: print_glsl_info_log Error received from GLSL shader #890:
fixme:d3d_shader: print_glsl_info_log     Vertex shader(s) linked, fragment shader(s) linked.
fixme: process:GetProcessWorkingSetSize (0xffffffff,0x382cd60,0x382cd64): stub
fixme: process:GetProcessWorkingSetSize (0xffffffff,0x382c9ec,0x382c9f0): stub
fixme:ntdll:NtPowerInformation semi-stub: SystemPowerCapabilities
err:mmdevapi:ACR_ReleaseBuffer Starting from 1014
err:mmdevapi:ACR_ReleaseBuffer Starting from 1014
err:mmdevapi:ACR_ReleaseBuffer Starting from 1014
err:mmdevapi:ACR_ReleaseBuffer Starting from 1014
AL lib: ALc.c:1879: exit(): closing 2 Devices
AL lib: ALc.c:1808: alcCloseDevice(): destroying 1 Context(s)
AL lib: ALc.c:1420: alcDestroyContext(): deleting 2 Source(s)
AL lib: ALc.c:1818: alcCloseDevice(): deleting 6 Buffer(s)

---

### Post by sir.sargento on 2011-06-21
Going under regedit and disabling the d3d GLSL seemed to have fixed my problem for the most part. I am now able to load missions that previously crashed before. I am still having a quite a bit of errors but at least now I think the crashing problem is solved. Thank you very much for the info.

---

