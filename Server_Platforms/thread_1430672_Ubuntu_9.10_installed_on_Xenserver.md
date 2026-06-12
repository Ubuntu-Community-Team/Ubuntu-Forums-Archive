---
title: "Ubuntu 9.10 installed on Xenserver"
date: 2010-03-15
forum: Server Platforms
---

### Post by felcore5 on 2010-03-15
Hi,

Does anyone know if there is a xenified kernel for Karmic Koala, I am trying to get the xs-tools installed but need a pv kernel to be able to do this.

If this is not possible what are others using to provide a vm environment using Karmic servers.

Thanks.

Felcore5

---

### Post by L0neRanger on 2010-03-15
> **felcore5 said:**
> Hi,

Does anyone know if there is a xenified kernel for Karmic Koala, I am trying to get the xs-tools installed but need a pv kernel to be able to do this.

If this is not possible what are others using to provide a vm environment using Karmic servers.

Thanks.

Felcore5
I was interested in the same thing but couldn't get a definitive answer. Is there someone with more experience in this area?

---

### Post by Gerrath on 2010-04-22
> **L0neRanger said:**
> I was interested in the same thing but couldn't get a definitive answer. Is there someone with more experience in this area?

Did either of you find the answer to this question?  I'm also looking to do this.
Regards,
Shane

---

### Post by iissmart on 2010-04-22
Looks like you can apt-get install linux-image-2.6.24-27-xen for 8.04...try **apt-cache search xen** to see if you can find one for your release.

---

### Post by ludger666 on 2010-04-28
maybe this guide will help you if not already found? [http://www.isaaczarb.com/installing-ubuntu-9-04-pv-on-citrix-xenserver/](http://www.isaaczarb.com/installing-ubuntu-9-04-pv-on-citrix-xenserver/)

---

