---
title: "Firefox broke today!"
date: 2012-08-12
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by xeizo on 2012-08-12
With todays updates so doesn't Unity 3D work anymore, Unity 2D and XFCE works. And when trying to start Firefox I'm thrown back to the login-screen. Chromium works fine. Nvidia-settings indicates I'm running the proprietary Nvidia driver allright, but I'm suspecting some Xorg ABI-problem anyway. Mabe Firefox uses 3D-acceleration for 2D and that's why it crashes? Anyway, it's the first major problem I've had with 12.10 for a couple of weeks. Glxgears works, so 3D doesn't seem to be the problem, but who knows?

Yesterday everything worked.

edit. I played Skyrim for a while now with good framerates, so 3D is definitely not the problem, rather Unity or Compiz or something or Firefox itself ...

---

### Post by ventrical on 2012-08-12
We just had a big forum on that. Sorry .. can't find it right off but it is here ! :)

You have to downgrade xserver-xorg-core to 1.12.1.902

regards.

Go into synaptic and just use force version and pick the above.

---

### Post by xeizo on 2012-08-12
> **ventrical said:**
> We just had a big forum on that. Sorry .. can't find it right off but it is here ! :)

You have to downgrade xserver-xorg-core to 1.12.1.902

regards.

Go into synaptic and just use force version and pick the above.

Thanks! That's just what i needed! Great forum here  =)

---

### Post by ventrical on 2012-08-12
You may want to skim this as it is a little bit more detail. There may be some minor recoverable breakage after  the downgrade - ie; you may have to :
sudo apt-get install ubuntu-desktop

etc..

[http://ubuntuforums.org/showthread.php?t=2036770](http://ubuntuforums.org/showthread.php?t=2036770)

---

### Post by xeizo on 2012-08-12
> **ventrical said:**
> You may want to skim this as it is a little bit more detail. There may be some minor recoverable breakage after  the downgrade - ie; you may have to :
sudo apt-get install ubuntu-desktop

etc..

[http://ubuntuforums.org/showthread.php?t=2036770](http://ubuntuforums.org/showthread.php?t=2036770)

Yes, that's the case, thank's!

edit. but that didn't help, Ubuntu 3D and Firefox is still crashing back to login screen ....
and of course Thunderbird does the same thing! All other programs, and 3D, works. So it's must be a Mozilla problem, I tried the latest nightly build of Firefox and it behaved exactly the same.

---

### Post by ventrical on 2012-08-12
> **xeizo said:**
> Yes, that's the case, thank's!

edit. but that didn't help, Ubuntu 3D and Firefox is still crashing back to login screen ....
and of course Thunderbird does the same thing! All other programs, and 3D, works. So it's must be a Mozilla problem, I tried the latest nightly build of Firefox and it behaved exactly the same.

No .. it's not firefox because I filed a bug on that already. Ronacc or paul_in_London will probably pop-in soon here :)

I just stand on the shoulders of giants like harry33 and mac4man because they found the fix.:)

---

### Post by ventrical on 2012-08-12
here it is .. start here :

[http://ubuntuforums.org/showthread.php?t=2038969&page=4](http://ubuntuforums.org/showthread.php?t=2038969&page=4)

---

### Post by xeizo on 2012-08-12
Well, well, I didn't reinstall nvidia-current after downgrading. That may be the problem. Mabe I'll try that too, or just wait out the issue, at least Chromium is working and gaming under Wine works just fine. I'm back on the new Xorg as the downgrade didn't work earlier.

edit. it wasn't possible to downgrade anymore, the matching debs seem to have been removed from the repositories and even ubuntu-desktop now depends on the new xorg-version, so no Unity 3D for a while then ...

---

### Post by ventrical on 2012-08-12
> **xeizo said:**
> Well, well, I didn't reinstall nvidia-current after downgrading. That may be the problem. Mabe I'll try that too, or just wait out the issue, at least Chromium is working and gaming under Wine works just fine. I'm back on the new Xorg as the downgrade didn't work earlier.

edit. it wasn't possible to downgrade anymore, the matching debs seem to have been removed from the repositories and even ubuntu-desktop now depends on the new xorg-version, so no Unity 3D for a while then ...

Did you make sure  you disabled the 'proposed' repositories before you updated ubuntu-desktop/nvidia-current?

---

### Post by kuvanito on 2012-08-12
never had a problem but nvidia is out of my life so is ati
i have never ever ever had an issue with any alpha,beta or rc releases with intel computers,either be it a desktop or laptop,my soul is cured....quantal looks like ready for delivery 2 me....

---

