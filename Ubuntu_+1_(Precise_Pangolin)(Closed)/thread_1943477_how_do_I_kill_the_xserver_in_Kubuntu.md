---
title: "how do I kill the xserver in Kubuntu ?"
date: 2012-03-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ronacc on 2012-03-19
I use a hand installed Nvidia driver , after the last update Kubuntu boots to a black screen . If I ctrl>alt> F1 to a term and try to install the driver ( already d/l'd to my /home ) it tells me an xserver is running and I need to kill it to proceed , no matter how I try to kill x it restarts and loops me back to the login screen .

---

### Post by xebian on 2012-03-19
> **ronacc said:**
> I use a hand installed Nvidia driver , after the last update Kubuntu boots to a black screen . If I ctrl>alt> F1 to a term and try to install the driver ( already d/l'd to my /home ) it tells me an xserver is running and I need to kill it to proceed , no matter how I try to kill x it restarts and loops me back to the login screen .

Once in ttyN, stop kdm and sometimes killall kdm would help. Must be sudo (forgot)

---

### Post by ronacc on 2012-03-19
thanks , I had the cmd in the wrong order ( sudo kdm stop ) instead of sudo stop kdm .

---

### Post by xebian on 2012-03-19
> **ronacc said:**
> thanks , I had the cmd in the wrong order ( sudo kdm stop ) instead of sudo stop kdm .

np.

---

