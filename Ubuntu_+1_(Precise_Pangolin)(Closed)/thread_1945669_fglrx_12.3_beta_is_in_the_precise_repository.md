---
title: "fglrx 12.3 beta is in the precise repository"
date: 2012-03-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Procrustes on 2012-03-23
I've never seen the fglrx driver available in the Update Manager before. I've always upgraded by downloading from AMD. About to test...

---

### Post by Gregory Lee on 2012-03-23
Is that this?  (Seen this morning during regular "aptitude safe-upgrade".)
```
Preparing to replace fglrx-amdcccle-updates 2:8.911-0ubuntu1 (using .../fglrx-amdcccle-updates_2%3a8.960-0ubuntu1_amd64.deb) ...

```

---

### Post by ft_ on 2012-03-23
no issue (seems to...) with HD6730M.
Playing videos is now ok.
See Phoronix to get more infos !

---

### Post by Procrustes on 2012-03-23
Yep.

Worked for me. I did have to manually restart after. Bonus for me is opencl 1.2

---

### Post by Sarvatt on 2012-03-23
It's actually 12.4 btw.

---

### Post by Gregory Lee on 2012-03-23
I managed to play a video for the first time on 12.04!  (I had to reboot once before it worked.)

---

### Post by larrypg on 2012-03-23
what is the driver version it is showing?

---

### Post by Gregory Lee on 2012-03-23
> **larrypg said:**
> what is the driver version it is showing?
8.96, perhaps, though I'm not clear whether that number is the driver version.  The update I mentioned above said "8.960".

---

### Post by Procrustes on 2012-03-23
> **larrypg said:**
> what is the driver version it is showing?


it is fglrx 8.96 which is apparently a Catalyst 12.**4** release

It was assumed by many including me, to be 12.3 but apparently that will still be a fglrx 8.95.x version.

This is the first time I have seen AMD hand a beta driver to Canonical and it go straight into the package management (for Precise only). Maybe 8.96 will be finalized for Precise Pangolin release.

---

### Post by ratcheer on 2012-03-23
Got it, thanks for the thread. I now have Unity 3D, again!

Tim

---

### Post by Vrroom on 2012-03-24
I upgraded to this fglrx package but catalyst control center still says:

catalyst version: 11.11

Also can someone explain OpenCL? Can it make your system run fast and improve performance?

Thanks !

---

### Post by ft_ on 2012-03-24
I got the same version number issue (as usual for me).
So : *purge* the the two fglrx packages (driver+amdcccle) and install them again (they wont reload since they are in apt cache).
The catalyst version number displayed should be right.

---

### Post by QIII on 2012-03-24
> **Vrroom said:**
> 
Also can someone explain OpenCL? Can it make your system run fast and improve performance?

Thanks !

[http://www.khronos.org/opencl/](http://www.khronos.org/opencl/)

---

### Post by Vrroom on 2012-03-24
Still showing 11.11

[IMG]http://i.imgur.com/QefhC.png[/IMG]

---

### Post by ft_ on 2012-03-24
I did a :
sudo aticonfig --initial -f
too

And i've got the 8.96 blablabla version of catalyst.
Maybe is it necessary ?

---

### Post by SheamusPatt on 2012-03-26
Because fglrx is proprietary / closed source, it's not the default video driver. The "standard" way to get it is to go to System Settings / Additional Drivers, and you should be able to activate it there. I think Update Manager will keep it up to date once you've enabled it, though.

---

