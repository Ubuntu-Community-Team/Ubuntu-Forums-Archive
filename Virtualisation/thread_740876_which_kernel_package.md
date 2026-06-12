---
title: "which kernel package?"
date: 2008-03-31
forum: Virtualisation
---

### Post by benner on 2008-03-31
i used to have a problem with random freezes on my machine.  after a billion posts, piles of reading, one guy suggested t hat i try the server kernel instead of the generic one.  suddenly, there were nomore random freezes.  i was happy as a clam.  

i just upgraded to the hardy beta.  it runs beautifully.  can't find a thing wrong.  then i started playing with virtualbox and seamless virtualization.  now, i am getting the freezing up problem again.  i was wondering if i might get lucky and solve the probelm again with a different kernel package.  

it may be a hardware problem but i am not ready to buy a new motherboard or video card to find out just yet.  could the kernel have something to do with it?

---

### Post by dcstar on 2008-04-01
> **benner said:**
> i used to have a problem with random freezes on my machine.  after a billion posts, piles of reading, one guy suggested t hat i try the server kernel instead of the generic one.  suddenly, there were nomore random freezes.  i was happy as a clam.  

i just upgraded to the hardy beta.  it runs beautifully.  can't find a thing wrong.  then i started playing with virtualbox and seamless virtualization.  now, i am getting the freezing up problem again.  i was wondering if i might get lucky and solve the probelm again with a different kernel package.  

it may be a hardware problem but i am not ready to buy a new motherboard or video card to find out just yet.  could the kernel have something to do with it?

One difference betwenn the server and generic kernels is that the server runs 100Hz interrupts versus 1000Hz (the higher rate gives better desktop response, not required for servers).

If you install other OSs in VMs they may well be using 1000Hz kernels, so it could be that you hardware just cannot reliably be pushed that hard in this area.

---

### Post by benner on 2008-04-02
thanks.  once i switched to the server kernel, my freeze problem seemed to be solved.  but now that i have installed virtualbox, they have returned.  when i first installed it, it was fine.  i was able to use the seamless mode.  fine.  then, i started installing software onto the windows xp guest.  the freeze problem returned.  

now, the system freezes up as soon as windows starts.  the caps and num lock lights on the keyboard start flashing.  the mouse cursor locks up.  i have to reboot.  the old freeze problem was intermittent but the same things happened.  now, it happens immediately every time the windows guest boots.  any suggestions?

64 bit amd 4200+ with ati video card.

---

