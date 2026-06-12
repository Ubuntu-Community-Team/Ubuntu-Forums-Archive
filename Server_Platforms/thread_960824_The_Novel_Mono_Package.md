---
title: "The Novel Mono Package"
date: 2008-10-27
forum: Server Platforms
---

### Post by Vegan on 2008-10-27
Anyone try the Novel sponsored mono package that provides the .NET framework for Linux?

---

### Post by directhex on 2008-10-27
You know Mono's been part of the default Ubuntu desktop install for years, right?

---

### Post by Vegan on 2008-10-27
I run server, so I have not noticed? No GUI on my box, none zilch nada.

Is the package installed on the server too?

what is the package called?

---

### Post by directhex on 2008-10-27
> **Vegan said:**
> I run server, so I have not noticed? No GUI on my box, none zilch nada.

Then you wouldn't have seen it.

> Is the package installed on the server too?

No. Not by default.

> what is the package called?

It's 79 distinct packages, and that's just from one source package. "mono-runtime" should pull in the bare minimum libraries, although not enough to do more than run a text-mode "hello world". "mono-2.0-devel" is a bit plumper. .NET libraries have "-cil" at the end of the name, e.g. libmono-system2.0-cil. When installing packaged apps, the library dependencies are handled for you. Only when working with your own apps should you need to worry about installing assemblies one by one.

---

### Post by Vegan on 2008-10-27
Only 79, hmmm. Is that enough to run ASP web pages on Apache?

---

### Post by directhex on 2008-10-27
> **Vegan said:**
> Only 79, hmmm. Is that enough to run ASP web pages on Apache?

libapache2-mod-mono and mono-apache-server2 packages.

---

### Post by Vegan on 2008-10-27
OK I installed mono-runtime and the other 2 packages, and rebooted the server. So is apache2 ready to go now?

---

### Post by directhex on 2008-10-28
> **Vegan said:**
> OK I installed mono-runtime and the other 2 packages, and rebooted the server. So is apache2 ready to go now?

You tell me. Did you install & configure Apache2 to your liking? Have you enabled mod_mono? It requires an equivalent amount of setup and config as mod_php5

---

