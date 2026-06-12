---
title: "Will .net application run on Ubuntu Server?"
date: 2011-05-05
forum: Server Platforms
---

### Post by clay7 on 2011-05-05
Hello,

In a client-server environment, will a server app developed in .net (either VB.net or C#) run on Ubuntu Server? This app would need to handle multiple instances. And would it run well?

---

### Post by terwase on 2011-05-05
NOPE!!

WIndows is totally dependent and built on the dot Net framework.

all c# apps and vb.Net apps depend on this windows' native platform

---

### Post by lykwydchykyn on 2011-05-05
It depends on what libraries were used.  On Linux there is Mono, which is a dotnet implementation.  It supports a lot of the .net libraries, but a few of them are windows-specific and won't work.

Best thing you can do is try it and see.

---

### Post by clay7 on 2011-05-05
Ok...follow up question. Let's say I develop the server-side app in Code::Blocks in C++. Would it be able to interact via Sockets with client apps built in .net?

---

### Post by directhex on 2011-05-05
> **clay7 said:**
> Hello,

In a client-server environment, will a server app developed in .net (either VB.net or C#) run on Ubuntu Server? This app would need to handle multiple instances. And would it run well?

Yes, if it's a truly managed app, it will likely run. Ubuntu's desktop version ships with multiple .NET apps out of the box, which work fine.

It largely depends on which namespaces you've made use of (e.g. Windows-centric things might not be available), and programming errors in your code (e.g. using path1+'\'+path2 not System.IO.Path.Combine(path1,path2))

---

### Post by clay7 on 2011-05-06
Thanks for your answers!

---

