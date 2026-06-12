---
title: "any idea"
date: 2011-07-10
forum: Virtualisation
---

### Post by mujahied on 2011-07-10
hi all

i need to make a a virtaul machine that connects to my clients platform 

the host is ubuntu and the  platform of the client is windows vista 

the only problem is i  need a vm software where i can emulate a certain bios

---

### Post by sanderd17 on 2011-07-10
What do you mean with "connect to the client platform"?

Normally, you have a host OS, in that host (server) OS you run a virtual machine which runs a guest (client) OS. So you want that client OS be shown on another computer? 

And

Is there a specific reason why you want to emulate a certain BIOS?

---

### Post by mujahied on 2011-07-10
yes the reason why i whant to emulaate a bios is that the customer hs a custom cd that only works on one type of machines

---

### Post by sanderd17 on 2011-07-10
Normally, the BIOS is proprietary software, so you can't just emulate that. You can emulate certain features of it (and try to get as close as possible), but not the complete BIOS as it is.

For accessing a virtual os from another computer, the most virtual machines can do this. Including Virtualbox: [http://www.virtualbox.org/manual/ch07.html](http://www.virtualbox.org/manual/ch07.html)

---

