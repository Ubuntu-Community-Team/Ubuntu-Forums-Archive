---
title: "Ultra 5 /etc/rc.local hang"
date: 2007-07-12
forum: Sun Sparc Users
---

### Post by jtombre on 2007-07-12
I just upgraded all my patches and did a reboot. It loads the kernel, but hangs at 
* Running local boot scripts (/etc/rc.local)

I do get an error about my X failiing which I received before the upgrade, but it would continue with a non X console.

Silo 1.4.13
Kernel = 2.6.20

Is there a way to boot into 'single user mode' where I can look at /etc/rc.local. I really do not want to rebuild the server. Any help would be appreciated

---

### Post by DiGiTY on 2007-07-13
i just had that same hanging problem, but i simply restarted the machine it booted up fine

---

### Post by DiGiTY on 2007-07-13
scratch that, it's still hanging at rc.local

anyone know how to resolve it?

p.s. - i'm running 7.04 server on Sparc, fresh install

---

### Post by RazerDad on 2007-07-16
Is it actually hanging. Have you tried pressing enter.

WHen I boot my 7.04 server, the login prompt doesn't appear until I press enter.

I suspect it's a getty issue.

M.

---

### Post by moore.bryan on 2007-07-16
*has anyone found a resolution for this issue?*

---

### Post by DiGiTY on 2007-07-17
it's apparently a known issue. you can either hit enter to big up the prompt or Ctrl-C

a bit of an annoyance, but you get what you pay for

---

### Post by moore.bryan on 2007-07-17
*yeah... i've read over all the bug reports.  it seems the issue is with getty loading before rc.local.  if that's they case, this should be an EASY bug to fix.  most are blaming upstart, since this issue didn't arise with init.  i finally was able to gerry-rig my laptop to autologin regardless of a hung rc.local script.*

---

### Post by sameer.iitg on 2007-08-14
please can anyone tell me in layman's terms :KS what do I need to do to solve this problem

---

### Post by RedSquirrel on 2007-09-02
I had the problem of having to press 'Enter' to get the prompt. Not a big deal, but mildly annoying. The suggestion posted [here]("https://answers.launchpad.net/upstart/+question/9887") seems to work very nicely.

---

