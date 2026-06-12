---
title: "Qsampler don't run"
date: 2010-02-06
forum: Ubuntu Studio
---

### Post by Becker-BR on 2010-02-06
22:35:39.705 Client connecting...
22:35:39.707 Server is starting...
22:35:39.709 linuxsampler
22:35:39.714 Could not start server. Sorry.
lscp_client_create: cmd: connect: ConexÃ£o recusada
22:35:41.860 Server was stopped with exit status 0.

Help

---

### Post by AutoStatic on 2010-02-07
Hello Becker-BR,

Are you using JACK? Which version of Ubuntu and LinuxSampler? And did you try something like Fantasia (a [jSampler]("http://jsampler.sourceforge.net/") frontend for LinuxSampler)?

---

### Post by seydou on 2011-03-14
> **Becker-BR said:**
> 22:35:39.705 Client connecting...
22:35:39.707 Server is starting...
22:35:39.709 linuxsampler
22:35:39.714 Could not start server. Sorry.
lscp_client_create: cmd: connect: ConexÃ£o recusada
22:35:41.860 Server was stopped with exit status 0.

Help

This is where Ubuntu hits you under the belt - qsampler is available in the repo, but linuxsampler is not. Since The former is mere fronted to the latter, it is a mess.

You need to visit linuxsampler home, or have a look at my other posting [http://ubuntuforums.org/showthread.php?t=1634289]("http://ubuntuforums.org/showthread.php?t=1634289"). Anyway, the only path is tedious manual compilation. On the other hand linuxsampler appears to be a great tool, and pays back the effort. Still do not get why it receives so little attention.

---

### Post by eamner on 2011-03-14
Man, I had a problem like this when testing Qsampler. In my case, when installing the version in the repos, it wouldn't start. It just crashed... this is what I did: I installed the DEB files from the linuxsampler website. It worked fine. Well, the only problem is that sometimes I notice some "clicks and pops" when playing many notes... but this is probably because I'm using an onboard soundcard and not a good interface.

---

### Post by seydou on 2011-03-15
> **eamner said:**
> Man, I had a problem like this when testing Qsampler. In my case, when installing the version in the repos, it wouldn't start. It just crashed... this is what I did: I installed the DEB files from the linuxsampler website. It worked fine. Well, the only problem is that sometimes I notice some "clicks and pops" when playing many notes... but this is probably because I'm using an onboard soundcard and not a good interface.

Yes, the card could be the likely culprit. Also, if you are using jack, check out the logs and try to play with jackd settings, it can help as well.

BTW, there is an Ubuntu clone KXStudio,  [http://kxstudio.sourceforge.net](http://kxstudio.sourceforge.net), it appears to come with full linuxsampler suite and all the audio goodies, so should be easier to maintain. It features KDE, though (which I do not fancy at all), but you can easily add gnome desktop from Ubuntu repos.

---

### Post by AutoStatic on 2011-03-16
> **seydou said:**
> Anyway, the only path is tedious manual compilation.Or install it from a PPA (AutoStatic, KXStudio Team) or external repository (Tango Studio).

> **seydou said:**
> Still do not get why it receives so little attention.Because the LS people have added an extra clausule to the GPL license which violates the GPL license itself so it cannot be distributed by Ubuntu.

Best,

Jeremy

---

### Post by AutoStatic on 2011-03-16
> **seydou said:**
> BTW, there is an Ubuntu clone KXStudio,  [http://kxstudio.sourceforge.net](http://kxstudio.sourceforge.net), it appears to come with full linuxsampler suite and all the audio goodies, so should be easier to maintain. It features KDE, though (which I do not fancy at all), but you can easily add gnome desktop from Ubuntu repos.You could also add the KXStudio PPA to your existing Ubuntu install and install LinuxSampler from that PPA. And there are also Gnome counterparts around like Dream Studio and Tango Studio. BTW, these are not clones but Ubuntu 'remasters'.

Best,

Jeremy

---

