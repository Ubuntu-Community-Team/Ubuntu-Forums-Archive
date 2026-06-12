---
title: "Issues with Windows XP on Sun VirtualBox"
date: 2009-07-11
forum: Virtualisation
---

### Post by Cadeyrn on 2009-07-11
I'm on x64 Jaunty using VirtualBox 3.0.2 for a x32 Windows XP VM. It seems to work fine, but so far out of the games I've tested, it does not do what I made it to do.

All Steam games (Source engine or a different engine) will try to launch, and the launch window will disappear as if the game is launching, but then it never launches. I checked for the process, but there isn't one. Also, when I tell them to launch, VirtualBox tells me the virtual computer automatically switched to 16-bit colors, even though it is still in 32-bit colors.

S.T.A.L.K.E.R. Clear Sky as well as Call of Duty World at War Single/Co-op both tell me there is no DVD inserted, even though the same DVD I used to install is inserted in my computer and the VM reads it just fine. CoD WaW Multiplayer says there was a DirectX error before launching and doesn't finish launching. I suspect this has something to do with TAGES, but I did install the TAGES drivers through STALKER. Yes, I know that DRM is no different from a virus, but who cares when I'm endangering an easily-replaceable .vdi file and not my entire computer?

STALKER with a no-DVD patch will every time either become an invisible window with an invisible error message or cause the blue error screen of death, followed by a restart.

I have the guest additions installed and plenty of specs devoted to the VM for running. I personally installed all of the .NET framework, the newest Windows XP compatible DirectX version, and service pack 3. But I can't get these games working.

---

