---
title: "[SOLVED] Virtualbox 3D acceleration! But now, a networking question..."
date: 2008-12-29
forum: Virtualisation
---

### Post by Ng Oon-Ee on 2008-12-29
So, latest version of Virtualbox supports OpenGL (no DirectX yet) 3D acceleration. Which means, to me, DOTA!!!! Warcraft III with -opengl runs fast, within the Virtualbox Windows XP VM.

However, I've been trying to play on Garena, I can run the Garena client no problem, but have problems joining games, it seems my list gets refreshed very slowly, and I haven't yet managed to successfully start a game, I seem to lag out after a few seconds (no replies from anyone in the room).

Is there anyone familiar with Virtualbox networking who can help me figure out this problem? I've used Firestarter to open everything I can think of in my Ubuntu, and I've turned off Window's firewall.


EDIT:

So, after messing around, it seems that if I change my Network to 'Host Interface' and select my wlan0 device, it works fine =).

No need to dual-boot to enter Garena, then.

---

### Post by Schok on 2009-01-03
i just installed my linux and wanted to try garena on it to play dota..so virtualbox is the only way eh?

---

### Post by Ng Oon-Ee on 2009-01-03
> **Schok said:**
> i just installed my linux and wanted to try garena on it to play dota..so virtualbox is the only way eh?
For Garena 3.0, yes. The previous versions supposedly worked on Wine. You can check their 'Bug Reports' section in the forums, there's a user who has a HOWTO on Wine and Garena, but the latest Garena hasn't been working yet. Quite a few open bugs in Wine about this.

Anyway, VirtualBox is basically an installation of Windows, so of course it would work. The networking bit was the only tricky stuff. Also, the OpenGL support is still iffy, I get artifacts sometimes, and the 'fog' areas on the map don't really fog properly. Doesn't hamper my gameplay much anyway (only really look at the minimap most of the time).

However, I'd suggest keeping an eye on Wine. If and when that does work, it'll be the best way to play, faster speeds, and their OpenGL implementation is currently streets ahead of VirtualBox's one.

Another thing you can try is the DirectX capabilities (up to DX9 currently) of VMWare, but I've always preferred VirtualBox to VMWare myself.

---

### Post by jedihopeful on 2011-04-03
my dota is so laggy . help. how much space does it need to work properly ?:!::!::!:](*,)

---

### Post by himanshunegi1987 on 2011-05-19
Even my dota is so laggy.
I guess Garena is working fine, but DOTA lags like hell, any one can help ?

Acer 5745
Assigned 1Gb ram to XP,
128 video memory assigned to XP
enabled 3d.

any other settings i shld know abt ?
thnx !

---

### Post by cjprofile on 2011-06-28
> **Ng Oon-Ee said:**
> So, latest version of Virtualbox supports OpenGL (no DirectX yet) 3D acceleration. Which means, to me, DOTA!!!! Warcraft III with -opengl runs fast, within the Virtualbox Windows XP VM.

However, I've been trying to play on Garena, I can run the Garena client no problem, but have problems joining games, it seems my list gets refreshed very slowly, and I haven't yet managed to successfully start a game, I seem to lag out after a few seconds (no replies from anyone in the room).

Is there anyone familiar with Virtualbox networking who can help me figure out this problem? I've used Firestarter to open everything I can think of in my Ubuntu, and I've turned off Window's firewall.


EDIT:

So, after messing around, it seems that if I change my Network to 'Host Interface' and select my wlan0 device, it works fine =).

No need to dual-boot to enter Garena, then.
/quote
how to play warcraft on virtual box??
//quote

---

