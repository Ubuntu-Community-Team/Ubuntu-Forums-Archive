---
title: "firestarter issues"
date: 2009-04-16
forum: Security
---

### Post by snlnluvnit45 on 2009-04-16
I am running Ubuntu ver. 8.04.. I have installed firestarter.. when the wizard runs it detects eth1... not eth0..  I only have one ethernet (adapter)???  firestarter won't start because it says that eth0 is not ready...I use DSL.. Could someone give me some guidance/direction on the fix for this..

Thanks in advance!!
Scott

---

### Post by HermanAB on 2009-04-16
Hmm, firestarter is deprecated. Use ufw instead, then you may have better luck.

---

### Post by brian_p on 2009-04-16
> **snlnluvnit45 said:**
> 

Could someone give me some guidance/direction on the fix for this..

Have you tried any other devices listed under 'Detected Device(s)'?

---

### Post by snlnluvnit45 on 2009-04-16
it only detects the one eth1. I don't have another choice.

---

### Post by brian_p on 2009-04-16
> **snlnluvnit45 said:**
> it only detects the one eth1. I don't have another choice.

What does

```
sudo ifconfig -a
```

say? And

```
dmesg | grep eth
```

---

### Post by kibster on 2009-04-20
I am kinda new at this myself..this is only an idea.

That happened to me also...smae thing actually...I uninstalled and reloaded it... worked better than ever . Give A try. 

Russ

---

