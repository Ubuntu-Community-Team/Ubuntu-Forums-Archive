---
title: "Shotwell can't find libgexiv2.so.0"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by t1497f35 on 2012-04-02
Hi,
Shotwell doesn't launch any longer, it says:

"shotwell: error while loading shared libraries: libgexiv2.so.0: cannot open shared object file: No such file or directory"

but the lib is installed. Anyone knows what's up?


Using an up to date amd64 Precise.

---

### Post by cariboo on 2012-04-02
I can confirm your problem, I see the same thing here, even after reinstalling shotwell.

---

### Post by mc4man on 2012-04-03
The lib just upgraded today ( 0.4.1-0ubuntu1),  so likely shotwell will need a rebuild
Edit: done 
[https://bugs.launchpad.net/ubuntu/+source/shotwell/+bug/971468](https://bugs.launchpad.net/ubuntu/+source/shotwell/+bug/971468)
but not available yet (dependency wait
[https://launchpad.net/ubuntu/+source/shotwell/0.12.1-0ubuntu2/+build/3377020](https://launchpad.net/ubuntu/+source/shotwell/0.12.1-0ubuntu2/+build/3377020)

---

### Post by Script Warlock on 2012-04-03
likewise here waiting for the fix..

---

### Post by macstevejb on 2012-04-03
Yes shotwell still unusable. Hoping the update and fix appears in the repos soon.

regards ;)

---

### Post by scorsagr on 2012-04-03
interim solution
```
sudo ln -s /usr/lib/libgexiv2.so.1 /usr/lib/libgexiv2.so.0
```

[[img]http://kaisman.fr/mesmots/mydossier/myimg/shotwell/Shotwell-0.12.1_Ubuntu-Precise-12.04.mini.jpg[/img]](http://kaisman.fr/mesmots/mydossier/myimg/shotwell/Shotwell-0.12.1_Ubuntu-Precise-12.04.maxi.jpg)

---

### Post by macstevejb on 2012-04-03
I can now confirm that the fixed Shotwell has found it's way into the Repos and duly installed via Update Manager.:p

---

