---
title: "Openlina: making linux apps run in Mac, Win and even on other/all Linux distros?"
date: 2008-03-24
forum: The Cafe
---

### Post by madjr on 2008-03-24
Yes, linux apps on win, mac and...... lin ?

downloading and installing linux apps fast and easy in any distro? is it possible?

here is a typical linux problem of an user not finding pre-compile apps in his favorite distro or the distro that came with his PC/laptop :

> #  Ba-Na-Na | March 11th, 2008 at 6:13 pm

I have the same computer (**eeePC with xandros**), and I
was wondering [B]how the hell do you
download programs on it[/B]? I&#8217;ve
read so many manuals and instruc-
tions on the web, and [B]I don&#8217;t get
it, how to compile programs in the
&#8220;tar.gz&#8221; format or anything[/B].
Is there a step-by-step instruction
things for how to download?

Thankss

[original here]("http://www.fsckin.com/2008/03/04/unboxing-the-asus-eee-pc-and-first-impressions/")








Linux is currently divided up for each vendor

(**lenovo and HP** with suse, **asus** with xandros, **shuttle** with foresight, **dell** with ubuntu, etc.)

Ubuntu has the **most** pre-compile apps (but some of these are not updated fast enough)

Other distros lack a good amount of the apps in the repos and are updated even less often, so could Openlina be a solution to the "too many distro" problem developers face. Could it bring some needed relief ?

we can't **force** everyone to use the same distro so this might be of help

**pre-compile in OpenLina and run everywhere?**


Note: is not another Java clone, you are not coding for it. Code in any language you want.


[http://www.downloadsquad.com/2008/03/23/lina-run-linux-aps-on-windows-or-os-x-or-at-least-one-linux-ap/](http://www.downloadsquad.com/2008/03/23/lina-run-linux-aps-on-windows-or-os-x-or-at-least-one-linux-ap/)

[http://dailyapps.net/2008/03/hack-attack-run-linux-apps-natively-on-windows-osx/](http://dailyapps.net/2008/03/hack-attack-run-linux-apps-natively-on-windows-osx/)

[http://www.openlina.org/wiki/index.php/LINA_on_Linux](http://www.openlina.org/wiki/index.php/LINA_on_Linux)

---

### Post by Game_boy on 2008-03-24
No. The basic Linux tools and libraries change so fast and are so diverse that binary compatibility is undesirable as it halts progress. Compile your own applications and they will work on any platform if you bundle/depend on all the dependencies.

---

### Post by Barrucadu on 2008-03-24
It's a nice idea, but as Game_boy said, things change too fast for it to really work.

---

### Post by madjr on 2008-03-24
> **Barrucadu said:**
> It's a nice idea, but as Game_boy said, things change too fast for it to really work.

**Openlina** is like a virtual machine working independently of the OS.

It could be the **solution** of software installation between distros (and probably other OS's). It would be a big relief for software developers also.

**compile on openlina and run everywhere.**

you would just install openlina run your app and it works.


making novice users **compile from source would be a thing of the past** rather than the only option for some distros or for each new ubuntu release...

It would close that big gap.

This would be key for mass linux adoption while keeping the freedom.

---

### Post by MasterSushi on 2008-04-06
This sounds like a very clever solution to the many different Linux distributions. I also like the idea of decentralized packaging, rather than having repositories being maintained for each distribution.

Does anyone know if LINA uses a significant amount of system resources since it is an additional layer running on top of the OS ?

---

### Post by Railsbuntu on 2008-09-10
Does anyone know how to run applications under LINA?

I have a closed source little app that is compiled to work under Linux, and I would like to make it work on a Mac.

---

### Post by cardinals_fan on 2008-09-10
The reason Eee users have trouble with installing software is because Xandros didn't provide the Debian-based package management system built into their distro to the users.  Why, I don't know, but the fault lies with that particular distro, not with the system.

LINA is just a virtualization system that hides itself **visually**.  It may be "invisible to the end user" and may "enable native look and feel", but it still requires running multiple OSs at the same time.

---

