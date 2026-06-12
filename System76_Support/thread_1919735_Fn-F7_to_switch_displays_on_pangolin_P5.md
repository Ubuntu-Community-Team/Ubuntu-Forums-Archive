---
title: "Fn-F7 to switch displays on pangolin P5"
date: 2012-02-03
forum: System76 Support
---

### Post by jtappin on 2012-02-03
It's been a while since I used an external monitor on my Pangolin P5. But I'm sure that in the past, the Fn-F7 combination switched between available monitors. Now however, the only way to do that seems to be to use the nvidia-settings tool.

Is this correct?

---

### Post by isantop on 2012-02-06
What version of Ubuntu are you using? Also, do you have the proprietary Nvidia driver installed?

---

### Post by jtappin on 2012-02-06
> **isantop said:**
> What version of Ubuntu are you using? Also, do you have the proprietary Nvidia driver installed?

I'm running Oneiric (with KDE 4.8 from the PPA, but I don't think that should affect this level). 

I do have the proprietary driver installed and /var/log/Xorg.0.log shows that is is being used [I don't think that nvidia-settings would work otherwise apart from asking to enable the proprietary driver].

---

### Post by isantop on 2012-02-06
To my knowledge, the proprietary driver currently does not support monitor switching using Fn+F7.

---

### Post by jtappin on 2012-02-06
Thank you. So the answer to my original question is "Yes".

---

