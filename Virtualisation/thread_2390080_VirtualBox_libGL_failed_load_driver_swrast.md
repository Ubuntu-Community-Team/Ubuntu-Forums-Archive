---
title: "VirtualBox libGL failed load driver: swrast"
date: 2018-04-25
forum: Virtualisation
---

### Post by terence26 on 2018-04-25
I have done a clean install of Ubuntu and installed VirtualBox
did sudo apt update / upgrade etc
When I try to launch VirtualBox from an ssh -Y usung cygwin/X I get 

libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast

VirtualBox works fine, but the VRDP feature does not work

Can somebody help me?

---

### Post by monkeybrain20122 on 2018-04-25
cygwin?

---

### Post by terence26 on 2018-04-25
cygwin is an X/Server for Windows

---

### Post by deadflowr on 2018-04-25
*Thread moved to **Virtualization** *

---

### Post by terence26 on 2018-04-26
This isn't a virtualization problem. even running glxinfo gives same error

---

### Post by monkeybrain20122 on 2018-04-26
> **terence26 said:**
> cygwin is an X/Server for Windows

I know. tha's why the question mark. Are you running Windows or Ubuntu? Which is in VB?

---

### Post by terence26 on 2018-04-26
This isn't a virtualization problem. even running glxinfo gives same error
Ubuntu is running on the hardware
I use another computer running windows 7 to ssh -Y to Ubuntu box

---

