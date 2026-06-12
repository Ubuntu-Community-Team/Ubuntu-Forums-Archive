---
title: "Ubuntu on A VM:  Seg Faultin' Like Crazy"
date: 2007-12-12
forum: Virtualisation
---

### Post by NielTown on 2007-12-12
Hey, Folks.

So this morning I was trying to chmod a file and it started segfaulting. Then the whole system started to inexplicably crap out. I restarted and suddenly my network interface fails to initialize; I was able to re-activate it in order to surf the web, but I can't ssh into, ftp to it, and worst of all Apache is shot. I can, however, ping the machine.

I then decided to do a slew of package upgrades through Synaptic. That went fine until I looked at the terminal window: segfaults everywhere! Now it's been hung up for the past 15 minutes or so; the state Synaptic is in right now is "Preparing to configure libsmbclient." Yes, it's said that for about 15 minutes. I'm afraid to touch anything.

Anyone have any ideas? I must note that this install is running on a virtual machine.

---

