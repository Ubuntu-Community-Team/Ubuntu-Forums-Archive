---
title: "On knoppix and noticed something very remarkable."
date: 2014-10-09
forum: Ubuntu/Debian BASED
---

### Post by Jaym29 on 2014-10-09
I just burned myself a copy of KNOPPIX and I just booted it up.  
Knoppix supports my GPU.
I've always wanted those fancy compiz effects like the cube and such and pretty much every ubuntu distro I've tried always says my GPU is crap and I can't do it. Also, I've always wanted to play Minecraft without GPU issues on linux. And, I think KNOPPIX is based off debian not ubuntu so does that have anything to do with the GPU?  KNOPPIX apparrently supports my GPU flawlessly.  Please, could somebody tell me what driver or such KNOPPIX is using so I can paste it into Linux Mint and enjoy this benefits :D.  The system information report is in the attachment.  Please respond as soon as possible :)

---

### Post by Bashing-om on 2014-10-09
Jaym29; Hello ;

I would suspect it is "also" in relation to the version of x-server.
Compare the 2 distros:
```

X -version

```  As 'buntu keeps moving on; supporting new hardware and the software required to support it.

[INDENT][INDENT]one size does not fit all
[/INDENT][/INDENT]

---

### Post by tgalati4 on 2014-10-09
You are using standard Intel graphics with the i915 module.  This is important:

> OpenGL Renderer	Mesa DRI Intel(R) 865G x86/MMX/SSE2

You can get the same effects in Mint, but you may have to use the same resolution (you are currently using 1024x768) and increase the Video RAM in BIOS.

---

