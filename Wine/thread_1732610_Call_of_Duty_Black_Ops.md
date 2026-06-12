---
title: "Call of Duty: Black Ops"
date: 2011-04-18
forum: Wine
---

### Post by kvarley on 2011-04-18
Despite the appdb page reporting mainly Gold ratings I can't seem to get it to work! :(

wine-1.3.17

Black Ops installation from DVD goes fine but I can't launch the game.

I'm running 64-bit which I think is causing problems with winetricks.

Does anybody know what packages are required to run Black Ops with wine? (e.g. packages that I need to get with winetricks)

---

### Post by 8Kuula on 2011-04-18
Im asuming you are using 32-bit wine in 64-bit ubuntu, like it is default.

Use default wine prefix as base.
Install directx from CODBO's Redist directory

wine registery change: UseGLSL = disabled (for better fps)

---

### Post by lxwcn840709 on 2011-04-19
These things looked pretty good, and some that I can learn, and I hope to learn more on it!

---

### Post by kvarley on 2011-04-19
> **8Kuula said:**
> Install directx from CODBO's Redist directory

Where is that, do you mean install it from the disc?

---

### Post by 8Kuula on 2011-04-19
Steam/steamapps/common/call of duty black ops/Redist/DirectX

There it is when installed with steam.

---

### Post by kvarley on 2011-04-19
> **8Kuula said:**
> Steam/steamapps/common/call of duty black ops/Redist/DirectX

There it is when installed with steam.

Doing that makes the game run :D

However, I can't play the game as I get shader errors which mean I have like 0.5 fps, really bad performance.

---

### Post by 8Kuula on 2011-04-19
UseGLSL setting may help.

I have nvidia gpu, for me with that setting game works with playable fps.

---

### Post by kvarley on 2011-04-20
> **8Kuula said:**
> UseGLSL setting may help.

I have nvidia gpu, for me with that setting game works with playable fps.

I have an ATI card which isn't supported with Wine for Shader 2.0, only 1.X so Black Ops won't run if I turn it off aparently.

Plus, I can't find the registry entry for Direct3D?

---

### Post by 8Kuula on 2011-04-20
It need to be created if it do not exist.

[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)
That helps.

---

### Post by kvarley on 2011-04-20
> **8Kuula said:**
> It need to be created if it do not exist.

[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)
That helps.

Did that and now it says Shader Model 3.0 not available.

I have an Ati HD Radeon 5830

---

