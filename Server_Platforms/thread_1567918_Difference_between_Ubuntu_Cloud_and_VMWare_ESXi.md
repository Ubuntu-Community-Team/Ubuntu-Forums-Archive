---
title: "Difference between Ubuntu Cloud and VMWare ESXi"
date: 2010-09-04
forum: Server Platforms
---

### Post by spynappels on 2010-09-04
Howdy,

Could somebody please point me to some reading material which explains the differences between Ubuntu Cloud and other virtualisation systems such as VMWare ESXi, and why one would be used in preference to another?

---

### Post by scorp123 on 2010-09-04
[www.wikipedia.org](www.wikipedia.org)

search for "VMware" and "Ubuntu Enterprise Cloud".

---

### Post by de0xyrib0se on 2010-09-04
Apples to oranges, Ubuntu EC is an OS that is tweaked to support virtualization to a "satisfying extend".

ESXi is built to be a hypervisor, far more scalable, easier to administer nodes, scaling resources and etc.

Cloud is just a fancy marketing name.

So to summ it up, what is the difference between a modded Honda Civic and a Subaru Impreza WRX when it comes to racing :)

---

### Post by scorp123 on 2010-09-04
> **de0xyrib0se said:**
> Cloud is just a fancy marketing name. Totally. Cloud this, cloud that. Everything is "cloud-something" these days ...

---

### Post by an0dos on 2010-09-04
Makes me miss the days when everything was on the 'information superhighway'. Then again, not really. I'm looking forward to the next marketing buzzword.

---

### Post by scorp123 on 2010-09-05
> **an0dos said:**
>  I'm looking forward to the next marketing buzzword. Heard one the other day: "**Hyper Cloud**" .... 'cloud' alone is not good enough, now it has to be 'hyper' too ...

---

### Post by koenn on 2010-09-05
@OP

"Cloud" is a product; Virtualization is a technology.

"Cloud" is about delivering applications and storage to customers.
In order to provide this product, cloud providers would typically use combinations of several kinds of virtualization alongside other technologies for server-based computing.

Cloud also aims to deliver computer resources (CPU cycles, storage capacity, ... "as needed", and bill the customers accordingly. So "cloud software" would also include mechanisms to accomplish that, whereas a hypervisor as such does not.

---

### Post by spynappels on 2010-09-06
Ok people. Thank you for that, it confirmed what I thought. Looks like I will be staying with my ESXi setups while continuing to read up on Cloud services.

Thanks for your input.

---

