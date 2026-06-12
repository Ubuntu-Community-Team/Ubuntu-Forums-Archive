---
title: "Google Chrome Error"
date: 2016-04-20
forum: Virtualisation
---

### Post by crayzteknician on 2016-04-20
After a fresh install of Lubuntu and upgrades in Virtual Box I installed Google Chrome without a hitch. When I try to start it I get the following error in terminal. I'm running Virtual Box 5.0.18 with Guest Additions installed.


```
[2419:2419:0420/195210:ERROR:sandbox_linux.cc(334)] InitializeSandbox() called with multiple threads in process gpu-process
[2419:2419:0420/195210:ERROR:texture_manager.cc(2421)] [.CommandBufferContext.Compositor-0x2943dcff5000]GL ERROR :GL_INVALID_ENUM : glTexImage2D: <- error from previous GL command
```

---

### Post by DuckHook on 2016-04-21
**Thread moved**

You will have better luck with this question in the virtualisation forum.

---

### Post by MAFoElffen on 2016-04-21
Looking up the errors ... Snap. Open bug at VirtualBox on this. They haven't fixed it yet. (Electron Process) Not just on Linux.

One of the participants found that disabling 3D Acceleration in the VM and Google runs in hs VM. Enable it and it crashes. 

Not a fix = just a work-around. Other workaround is to unistall and install a previous release.

re: Affects VirtualBox 5.0.18. Problems running OpenGL and Compiz. Affects Windows and Linux vbox versions.

---

