---
title: "all my Compiz&amp;desktop settings ripped after n.n.n-9 update"
date: 2012-01-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2012-01-16
I just updated on my SATA machine with Intel Board and it ripped all my  compiz and desktop setting (in some users) . Im chekcing it out now.

---

### Post by ventrical on 2012-01-16
ok.. that was Unity 3D that got ripped.

---

### Post by ventrical on 2012-01-16
I went back to kernel 3.2.0-8 and all is restored . Appears to be a kernel regression??

---

### Post by effenberg0x0 on 2012-01-16
Were you running nvidia-proprietary (installer from nvidia website)?
I use it and always have to run sudo NVidia_Something_290.Something.run -K to rebuid the kernel module when I update kernel releases... otherwise Unity is really gone.

---

### Post by grahammechanical on 2012-01-16
It did not happen to me. Kernel 3.2.0-9 from about an hour ago and Nvidia 290.10 from an update a couple of days ago.

Regards.

---

### Post by ventrical on 2012-01-17
> **effenberg0x0 said:**
> Were you running nvidia-proprietary (installer from nvidia website)?
I use it and always have to run sudo NVidia_Something_290.Something.run -K to rebuid the kernel module when I update kernel releases... otherwise Unity is really gone.


ahhhh....thanks...

---

### Post by ventrical on 2012-01-17
I used <additional drivers> tool. Worked great. A big surprise to me as I have been running this install since Oneiric Alpha1 transitioned to Precise and it never burped up the nVidia driver before.

---

