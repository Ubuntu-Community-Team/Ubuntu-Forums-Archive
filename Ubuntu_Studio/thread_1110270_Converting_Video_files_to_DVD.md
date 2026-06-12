---
title: "Converting Video files to DVD"
date: 2009-03-29
forum: Ubuntu Studio
---

### Post by Twilfong on 2009-03-29
I record a lot of home movies and vacation videos and upload them to my computer. My question: What is the best program for converting WMP or AVI files so that they can be burned to disc and played on a stand-alone DVD player? I previously used DVD Flick or Windows Movie Maker, but I need an Ubuntu program now.

Thanks a ton everyone!!

---

### Post by TenPlus1 on 2009-03-29
Pop into [www.getdeb.net](www.getdeb.net) and look for a program called DeVeDe...  That's what I use to convert all my movies onto Video DVD formats...

---

### Post by Stochastic on 2009-03-29
> **TenPlus1 said:**
> Pop into [www.getdeb.net](www.getdeb.net) and look for a program called DeVeDe...  That's what I use to convert all my movies onto Video DVD formats...

There's no need to go to getdeb.net for that program, it's in the official repos.  Infact the less you can visit that site, the better - those versions of the software are less tested than the official repositories, don't come with any security updates, and may conflict with other packages in the official repositories.  Furthermore, if you run into troubles with a program, then we can't really say if it's user error, official bug, or configuration issue as easily.  Only packages that aren't in the official repos should be downloaded from getdeb.net.

so to recap, the proper way to get devede is:```
sudo apt-get install devede
``` or open up add/remove programs (synaptic package manager) and do it there.

---

### Post by binbash on 2009-03-30
+1 for devede

---

