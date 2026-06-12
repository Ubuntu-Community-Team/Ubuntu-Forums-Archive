---
title: "Proxy settings during installation."
date: 2011-11-04
forum: Server Platforms
---

### Post by balkrishna on 2011-11-04
Hello ,

I wish to run Ubuntu Server on an HP Proliant Blade server. The HP site shows that Ubuntu 10.04 is compliant on the blade server. The internet here is through a proxy. On asking for the proxy during the installation the format in which I specify the proxy is as follows: 

"http://username: password@host: port" with the quotes. (I have included the space as they are transformed into smileys.)

Further, the installation fails as the installer is unable to configure the package manager.

Is the format in which I am writing the proxy correct ? Can anyone suggest a workaround ?

---

### Post by Jonathan L on 2011-11-04
> **balkrishna said:**
>  Can anyone suggest a workaround ?

Hi Balkrishna

One way to deal with this is simply don't set a proxy during installation; get your server running and then tell it about the proxy afterwards.  I've done all my installatinos without using the network, from CD-ROM or USB stick, so perhaps it's possible you have another problem when your installation fails?

The only thing I notice about what you wrote is that the installation screen has a trailing slash, but I can't tell you if that matters as I've never used it.

Any use?

Kind regards,
Jonathan.

---

### Post by vasile002 on 2011-11-04
try removing the http:// thing

---

