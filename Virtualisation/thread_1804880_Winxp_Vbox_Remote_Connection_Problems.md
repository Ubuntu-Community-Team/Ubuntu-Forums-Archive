---
title: "Winxp Vbox Remote Connection Problems"
date: 2011-07-15
forum: Virtualisation
---

### Post by Jake.Debord on 2011-07-15
Hey gang, I have a problem with my VMs loosing connection or something during sessions. I run into this issue more so at the login screen. Sometimes the screen goes black, and sometimes the screen just quits refreshing and it looks like the VM is frozen. When I preview the VM in phpvbox I can see what the screen should look like, and when I connect through its portal it fixes it temporarily. Can anybody tell me what kind of issue I'm having? Any ideas on how to resolve it?

---

### Post by Jake.Debord on 2011-07-15
Pending possible solution... I realized I only had 32mb of video ram and  the resolution that it was auto adjusting to at the login screen when I  RDP connected was causing issues because 32mb does not support screen  resolutions that high. That may be why when I connect through the  phpvbox console with a lower resolution it unfreezes it.

I'll give it a little bit, and if it seems to have worked I will update as solved.

---

### Post by CharlesA on 2011-07-15
Were you connecting via VRDP or regular RDP?

---

