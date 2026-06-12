---
title: "vmware server don't work"
date: 2008-07-09
forum: Virtualisation
---

### Post by kelinu on 2008-07-09
Hi,
I managed to install VMware Server through the terminal on my Ubuntu 8.04, and it does show under Applications>> System Tools>> VMware Server Console.
But, when i click it, on the bottom it says "Starting VMware Server Console..." and then after some time that disappears, and nothing loads up.  What to do?!

Thanks in advance

---

### Post by kelinu on 2008-07-09
ok guys i managed to fix it myself no problems now =):)

---

### Post by Aiello on 2008-07-09
How did you fix it? I am having trouble getting mine to work too.

---

### Post by dushkal on 2008-07-10
Hi,

you can try this...

sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0

Cheers,
Dushkal

---

