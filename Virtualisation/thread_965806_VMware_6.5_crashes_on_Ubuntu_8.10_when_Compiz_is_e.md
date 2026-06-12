---
title: "VMware 6.5 crashes on Ubuntu 8.10 when Compiz is enabled"
date: 2008-10-31
forum: Virtualisation
---

### Post by sunside on 2008-10-31
Hi there.

I have VMware Workstation 6.5 (with key mapping problems) running on Ubuntu 8.10, on a Thinkpad notebook, GNOME with Compiz desktop effects enabled. I can start VMware once without a problem. When I close it, however (keeping the VM running) and try to open VMware again, the screen freezes. The system is still working and I can switch to a console (I also can still move and resize windows, but the screen won't get updated, so I'm running blind here) - however I won't get back to a normal desktop unless I kill compiz.

I had a look in the syslog but found nothing - I'm somewhat new to linux, so this doesn't have to mean anything.

Can you help me out here? Where can or should I look for error messages, should I ask this question elsewhere? How can I determine wheter this is a GNOME, Compiz or VMware problem? If this is could be a bug, where should I file it?

Any help is appreciated!
Best regards,
Markus


edit: Nevermind, gone back to qemu/kvm. Still, where should I have looked for the error?

---

### Post by kalmi on 2009-02-07
up (same proplem)

---

### Post by arad85 on 2009-02-13
Same problem here....

---

### Post by natros on 2009-02-13
... and here

---

### Post by arad85 on 2009-02-14
I've downloaded Suns virtualbox ([http://www.virtualbox.org](http://www.virtualbox.org)) and that seems to work very nicely and is free. So far, it's looking good - it even has a nice screen size that zooms the client desktop to fit the full screen. The only problem I've had with it is that it BSoD'd when trying to install daemon-lite (the same application on the OS install under VMware was OK). You can mount virtual disks outside of virtualbox, so you can mount stuff on the linux host...

So far, so good... and no screen freezes or other weird behaviour...

---

