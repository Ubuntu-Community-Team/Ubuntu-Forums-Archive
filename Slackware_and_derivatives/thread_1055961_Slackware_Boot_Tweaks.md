---
title: "Slackware Boot Tweaks"
date: 2009-01-31
forum: Slackware and derivatives
---

### Post by Vince4Amy on 2009-01-31
Does anybody know any tweaks on Slackware that they use to make it boot quicker. I've installed it, customised the kernel and updated it, now I'd like to know it can be made to boot faster. Also is it possible to add a splash screen because the machine I've installed it on isn't just used by me and it would be nice to have a boot splash screen.

---

### Post by disturbed1 on 2009-02-02
Can't say I've never really had the need to watch my machines start up often enough to let it bother me. Once after the first installation, and after compiling a new kernel. I like the scrolling text. It tells other people **THIS IS NOT A TOY**

You can patch the kernel for a splash screen if you want. Google should yield a few thousands links. Try Slackware bootsplash, Slackware kernel splash ..... something along those lines.

How long is it taking your machine to boot? I compiled a new kernel 4 or 5 days ago, and I know it took 25 seconds or less from post to  log in prompt. Try to chmod -x any services in /etc/rc.d/ your not using (pcmcia? wireless? ssh? ntp? bluetooth? ...) If you know what you're doing, you can edit rc.M as well to background, or completely remove some items. How often do you install new fonts? new GTK themes/icons? Those tasks are handled in rc.M as well.

Try asking some questions at Linuxquestions.org, which is where most of the slackers hang out.

---

### Post by Vince4Amy on 2009-02-03
> How long is it taking your machine to boot? I compiled a new kernel 4 or 5 days ago, and I know it took 25 seconds or less from post to log in prompt. Try to chmod -x any services in /etc/rc.d/ your not using (pcmcia? wireless? ssh? ntp? bluetooth? ...) If you know what you're doing, you can edit rc.M as well to background, or completely remove some items. How often do you install new fonts? new GTK themes/icons? Those tasks are handled in rc.M as well.

Oh of course, I completely ignored editing rc.M things are a lot better now, thanks for the heads up. Manually Marked as Solved.

---

### Post by kevCast on 2009-02-07
Do you guys know how to disable the BIOS data check at boot? It takes about 30 seconds to go through and is very annoying.

Also, is it safe to just comment things out of rc.M?

---

### Post by disturbed1 on 2009-02-10
Not sure about the bios check. I'd imagine you would have to recompile the kernel if you're using the huge.smp or generic.smp to take some of the built in things out. These are kitchen sink kernels so that 99.999% of the hardware out there will get you in effectively enough to compile your own.

About rc.M if you have to ask if you should, don't ;)

---

