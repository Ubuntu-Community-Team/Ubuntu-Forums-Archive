---
title: "Super key not passed to vitual machine"
date: 2008-03-11
forum: Virtualisation
---

### Post by Hero of Time on 2008-03-11
I'm having some problems with the Super/Win key to get working in my Virtual Machine. I don't know if I'm at the right place, because it used to work just fine, but I recently installed Compiz-Fusion and it stopped working after that. The Super key does work, as I can use it for the key shortcuts set in Compiz. But my VM doesn't pick it up anymore. It seems that Compiz has taken over that key completely. If I stop Compiz, it still won't work.

Setup:
Xubuntu 7.10 with Hardy kernel (2.6.24-5)
Compiz-Fusion
VirtualBox 1.5.6 cs

---

### Post by Hero of Time on 2008-03-13
Ok, I just noticed something strange. The Super key is recognised as the Alt key. This means I have 2 alt keys now, Super and Alt. Alt Gr doesn't respond like a normal Alt, so I don't count that one.

Doesn't have anyone an idea how to fix this problem? It used to work, and the Super key works in Ubuntu just as it should.

---

### Post by HermanAB on 2008-03-14
Hmmm, the only real solution is to pick a different super key.  Both VMware and Virtualbox has the option to redefine the super key, but to make it take effect, you have to restart the VMs.  

Pick something like Alt-Shift.

Cheers,

Herman

---

### Post by Hero of Time on 2008-03-15
Not a real solution, as it DID work and the only change I made was installing Compiz. Somehow, that made the VM see the super key as the alt key. I will look into your 'workaround', as I use the super key a lot (run, explorer, that stuff).

---

### Post by Hero of Time on 2008-03-17
Herman, do you know how to map these keys? I can't seem to find it in the manual or the forums.

---

### Post by Hero of Time on 2008-05-04
Never mind this topic. After a clean install of my system, the key works again. Installed 8.04 with a fresh install, works again.

---

