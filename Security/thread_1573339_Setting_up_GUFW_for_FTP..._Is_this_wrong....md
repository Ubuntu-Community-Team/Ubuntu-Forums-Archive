---
title: "Setting up GUFW for FTP... Is this wrong?..."
date: 2010-09-12
forum: Security
---

### Post by locoHost on 2010-09-12
Click here to see an image of my GUFW screen...

[GUFW Main Screen]("http://picasaweb.google.com/lh/photo/-pU7vu8QLxATFsX3aP5OUA?feat=directlink")

I -can- connect to the FTP server and upload/download files so long as I have GUFW either disabled or allow all traffic in/out. So something must be wrong with my rules.

I really appreciate your help :-)

---

### Post by bodhi.zazen on 2010-09-12
> **locoHost said:**
> Click here to see an image of my GUFW screen...

[GUFW Main Screen]("http://picasaweb.google.com/lh/photo/-pU7vu8QLxATFsX3aP5OUA?feat=directlink")

I -can- connect to the FTP server and upload/download files so long as I have GUFW either disabled or allow all traffic in/out. So something must be wrong with my rules.

I really appreciate your help :-)

What makes you say that ? A firewall will block traffic unless you allow it. What is it you are wanting to do exactly ?

---

### Post by locoHost on 2010-09-12
> **bodhi.zazen said:**
> What makes you say that ? A firewall will block traffic unless you allow it. What is it you are wanting to do exactly ?

I want the FTP server in the DMZ so we need the firewall. I'm trying setup GUFW so that it will allow -only FTP- traffic in and out. Since it blocks the FTP traffic when it's enabled with my current rules (see the link to the image), I can deduce that there is a problem with my rules. Follow?

---

### Post by locoHost on 2010-09-12
There is next to zero documentation for GUFW. What do I set the main incoming and outgoing settings? Then what are the rules so that only FTP will get thru? Thanks :-)

---

### Post by bodhi.zazen on 2010-09-12
> **locoHost said:**
> There is next to zero documentation for GUFW. What do I set the main incoming and outgoing settings? Then what are the rules so that only FTP will get thru? Thanks :-)


[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

Your problem may be that you are blocking outbound traffic, why would you do that ?

[https://help.ubuntu.com/10.04/serverguide/C/firewall.html](https://help.ubuntu.com/10.04/serverguide/C/firewall.html)

---

### Post by locoHost on 2010-09-13
Yeah, that was the problem. I set it to block incoming, but left the rules to allow 20 and 21 coming in, then allow all out. That worked.

Thanks!!!!! :-)

---

