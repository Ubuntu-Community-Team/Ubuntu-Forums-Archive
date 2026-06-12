---
title: "python security"
date: 2012-07-16
forum: Security
---

### Post by roimekoi on 2012-07-16
Is python process running as root privilege? 
It seems that chrooting the python folder will not work if python is running as root.

is there a proper way confine a python process?

for both apache python handler and normal python 


..............................
i just started to read sys admin stuff, so a detailed explanation  is best welcome , or please give me keyword so that i can search it on books or google for it

thank you

---

### Post by Hungry Man on 2012-07-16
You can confine root processes with AppArmor.

---

