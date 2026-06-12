---
title: "unity8 hangs at login"
date: 2014-02-26
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-02-26
Installed unity8 from proposed and it hangs at login. I have to hard reboot - keyboard inoperable.

[https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1285333](https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1285333)

---

### Post by xc3RnbFO8P on 2014-02-27
I get this, dont know if this is the right way to test it?

---

### Post by ventrical on 2014-02-27
> **Ringi said:**
> I get this, dont know if this is the right way to test it?

Don't think so...

Try:

```


sudo service lightdm restart


```

---

### Post by xc3RnbFO8P on 2014-02-27
There is no problem with lightdm, it just hangs if I start it from lightdm.
I just thought it was a useful error message

---

### Post by ventrical on 2014-02-27
I am just trying this:unity-desktop-session-x11 through synaptic  or,

```

sudo apt-get install unity8-desktop-session-x11

```
Edit:
Warning :

Don't try the above with Unity. Borks the system.

---

### Post by xc3RnbFO8P on 2014-02-27
I tried this, its working with very small mobile window

---

### Post by ventrical on 2014-02-27
> **Ringi said:**
> I tried this, its working with very small mobile window

Yes ... there is a mobile screen but not functional like the unity8 shell in the Software Center. However, upon reboot it borked my system.


Are you using  an original install of [ubuntu]? or another flavour?

thanks

regards.

---

### Post by xc3RnbFO8P on 2014-02-27
> **ventrical said:**
> Yes ... there is a mobile screen but not functional like the unity8 shell in the Software Center. However, upon reboot it borked my system.


Are you using  an original install of [ubuntu]? or another flavour?

thanks

regards.

Well I started with fresh install of Ubuntu 12.04  a year ago

---

### Post by ventrical on 2014-02-27
> **Ringi said:**
> Well I started with fresh install of Ubuntu 12.04  a year ago

Nice work then :)

---

