---
title: "Why Kubuntu contacts www.enricoros.com on login?"
date: 2009-12-05
forum: Security
---

### Post by jpv2 on 2009-12-05
Hello,

every time I log in the KDE desktop I get a pop up message telling me, that my system is downloading something from [www.enricoros.com]("http://www.enricoros.com"). This site is about Fotowall application, which I have not installed (checked in Synaptic and by searching disk). No evidence of "enricos" string in my system log files. Google doesn't point me to any other similar reports. Any thoughts what's going on and how to disable this "feature"?

---

### Post by enricoros on 2009-12-09
Hello! I'm the owner of [www.enricoros.com](www.enricoros.com), but I really don't know the answer to your question...

On my domain there is: 
 - my blog
 - the fotowall site

The only client application that checks my domain is Fotowall itself, that downloads [http://www.enricoros.com/opensource/fotowall/.meta](http://www.enricoros.com/opensource/fotowall/.meta) when checking for updates.. but this should happen once in 30 days and when you launch the application!

So I have no clue about your problem, I think it's something stuck in the KDE kioslaves or on the session resume sequence.. maybe try to check with
 grep -i enrico .kde4/share/config/session/*

And tell me about your progress.

---

