---
title: "Installed GUFW firewall, lost shh in vps"
date: 2014-07-20
forum: Security
---

### Post by nadadro on 2014-07-20
Hi.

I have a VPS running Ubuntu, installed Gufw firewall and set it to active (nothing more)...but now i cant access the VPS neither with SSH, TightVNC.
I restarted the VPS, but no luck. Supposedly i had to set some rules..

What can i do? (reinstalling the VPS is the last option, because i want to recover some data from it).

Best Regards.

---

### Post by ubudog on 2014-07-20
Do you have a web console you can use to get to a shell on the VPS?

By default, when UFW is activated, all ports are closed until you open them.

If you do have a console, you can run:
```
sudo ufw allow 22/tcp
```
to open ssh, and:
```
sudo ufw allow 5800/tcp && sudo ufw allow 5900/tcp
```
for TightVNC (not sure about the port numbers, that is what I remember).

---

### Post by nadadro on 2014-07-20
Hi.

Apart from a type of "recovery mode" i have nothing more. 

But i figured out by:
-Entering in "recovery mode" 
-Access to my partition 
-Disable UFW by editing the file "etc/ufw/ufw.conf" and changed to "ENABLED=no".
-Restarted VPS in normal mode and i got access by SSH.

Just in case i remove GUFW and UFW, reinstalled..followed your commands to allow SSH, and everything is running smoothly :)

Thanks.

---

### Post by ubudog on 2014-07-20
Good to hear that you got back into your machine!  :-)

---

