---
title: "Win 7 is faster than Ubuntu 11.04 VBOX"
date: 2011-04-26
forum: Virtualisation
---

### Post by emoguitarist06 on 2011-04-26
I am running Ubuntu 10.10 32bit and I have Ubuntu 11.04 Beta 2 installed into VBOX & Windows 7 Home premium installed in VBOX

However Ubuntu is SUPER SLOW inside VBOX and Windows 7 is way faster!!
I've actually noticed this since trying to virtual Ubuntu since I was running 9.10 but I didn't care too much then. The only reason now is because I really wanted to test the Unity desktop before the 28th.

Both Ubuntu & Windows in the virtual box show almost a 100% CPU usage however Windows is running great regardless

IDK I think it's odd.

---

### Post by Jagoly on 2011-04-26
Unity and Virtual box DO NOT MIX

---

### Post by emoguitarist06 on 2011-04-26
screenshot with windows

---

### Post by emoguitarist06 on 2011-04-26
> **Jagoly said:**
> Unity and Virtual box DO NOT MIX

However I thought that Virtual box 4.06 fixed this problem.

So you're saying if I tried 10.10 in VBOX I wouldn't have this experience?

---

### Post by Jagoly on 2011-04-26
Yep. I've got a Win7 box and several Ubuntu 10.10 box. They both run fine, bar decent hardware acceleration. Unity is a lot like Windows Areo. Neither work in virtualbox.

---

### Post by prshah on 2011-04-26
> **emoguitarist06 said:**
> However Ubuntu is SUPER SLOW inside VBOX and Windows 7 is way faster!!

Please enable 2D video acceleration for Ubuntu, and install Unity2D from the repos. Unity by default uses OpenGL, not really optimized for a VM.

---

### Post by emoguitarist06 on 2011-04-26
> **prshah said:**
> Please enable 2D video acceleration for Ubuntu, and install Unity2D from the repos. Unity by default uses OpenGL, not really optimized for a VM.

Okay great I'll give that a try tonight!
So before I start Ubuntu again enable 2D and then startup and install Unity 2D?

That's cool that you mention that because I just read this article that a user has made a 2D tweaking tool to get it to act more like 3D
[http://marianochavero.wordpress.com/2011/04/20/a-simple-gui-for-unity-2d-settings-ubuntu-11-04/]("http://marianochavero.wordpress.com/2011/04/20/a-simple-gui-for-unity-2d-settings-ubuntu-11-04/")

---

### Post by psusi on 2011-04-26
What process is hogging the CPU?  Sitting at 100% is definitely not normal.

---

### Post by emoguitarist06 on 2011-04-26
> **psusi said:**
> What process is hogging the CPU?  Sitting at 100% is definitely not normal.

Yeah I wasn't sure if that was normal or not. But good point I'll look at it tonight and post what I find

---

### Post by Jagoly on 2011-04-27
Are you sure it's actually at 100%? it could just be a false readout. Is you computer making alot of noise?

---

### Post by prshah on 2011-04-27
> **emoguitarist06 said:**
> 
So before I start Ubuntu again enable 2D and then startup and install Unity 2D?

Yes, and please also install guest extensions if not already installed in the Ubuntu VM.

---

