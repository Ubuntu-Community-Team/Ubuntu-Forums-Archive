---
title: "Problems running Kubuntu 9.04 in VMWare WorkStation"
date: 2009-07-25
forum: Virtualisation
---

### Post by coolen on 2009-07-25
I'm trying to get Kubuntu running in VMWare WorkStation on Windows XP. All's going fine, then I tried installing VMWare Tools.

I used the script [here]("http://chrysaor.info/?page=faq#ubuntu904_tools"). It's supposed to be a one stop solution to installing it in Jaunty. I assumed it would work fine in Kubuntu, too...

Anyway, the install went just fine. I restarted the machine, and I got a massive resolution (I selected 1024x768, this seemed far bigger to me). I logged in, and the screen reduced to what I'd previously selected (640x480, for usability). Then, the shell disappeared. Konsole showed up, with tiny fonts, and behind it was the login background. I can close Konsole, but the shell's unresponsive. I can switch to another VT and restart KDM, but it just keeps happening.

Has anyone had luck using this script? I'd rather not start over.

---

### Post by ktechkio on 2009-07-26
Why don't you use virtualbox 3.0 (has 3d and everything). Then use install guest additions instead of messing around with that script!

---

### Post by coolen on 2009-07-26
I have it. I'm trying out VMWare, you know, to compare?

---

