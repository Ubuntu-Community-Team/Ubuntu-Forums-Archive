---
title: "Ubuntu Server LAMP (Apache) / VMWare / Edge Browser / NAT"
date: 2016-10-01
forum: Virtualisation
---

### Post by BruceFulton on 2016-10-01
There appears to be an issue with the new Win 10 Edge Browser connecting to the Apache Web server when installed in VMWare running in NAT mode (but not bridged). See attached. 
[IMG]http://www.u.arizona.edu/~bfulton/edgebug.jpg[/IMG]

---

### Post by yancek on 2016-10-01
You could try the suggestions at the link below.

[http://superuser.com/questions/245156/how-can-i-connect-to-a-web-server-running-in-a-vm-when-the-vm-is-in-nat-mode](http://superuser.com/questions/245156/how-can-i-connect-to-a-web-server-running-in-a-vm-when-the-vm-is-in-nat-mode)

---

### Post by BruceFulton on 2016-10-01
Thanks, this is an issue just with the new Edge browser. Chrome, firefox, Safari all work fine. 

> **yancek said:**
> You could try the suggestions at the link below.

[http://superuser.com/questions/245156/how-can-i-connect-to-a-web-server-running-in-a-vm-when-the-vm-is-in-nat-mode](http://superuser.com/questions/245156/how-can-i-connect-to-a-web-server-running-in-a-vm-when-the-vm-is-in-nat-mode)

---

### Post by SeijiSensei on 2016-10-02
Does it matter if you explicitly use a URL like [http://192.168.25.130](http://192.168.25.130) instead of just the IP address? What if you add a hostname and the address to the [Windows hosts file]("https://en.wikipedia.org/wiki/Hosts_(file)") and use that name instead?

---

