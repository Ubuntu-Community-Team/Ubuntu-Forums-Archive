---
title: "software center block package removal/update"
date: 2010-10-04
forum: Security
---

### Post by sebas929 on 2010-10-04
Hi all

First off I'm not sure if this is the right place to put this so please move it if neccesary. 

I have two packages on my computer (dansguardian,firehol)  and I want to prevent users with admin rights (normal default sudo setup for ubuntu) from  removing/updating these packages.

I have edited the sudoers file to block apt-get purge/remove which works for the terminal. However this does not work for synaptic or the ubuntu software center

Does anyone know if/how I can block sudo users from adding/removing dansguardian and firehol packages with the software center and/or synaptic?

I am using ubuntu 10.10 RC and software center version 3.02.

Thanks

---

### Post by searchfgold6789 on 2010-10-05
Hello and welcome to the forums.
A workaround for this is to remove its source from etc/apt/sources.list

---

### Post by cariboo on 2010-10-05
The quick fix would be to take admin rights away from the other users. If they have the ability to install packages, they also have the ability to remove them.

---

### Post by bodhi.zazen on 2010-10-05
> **sebas929 said:**
> Hi all

First off I'm not sure if this is the right place to put this so please move it if neccesary. 

I have two packages on my computer (dansguardian,firehol)  and I want to prevent users with admin rights (normal default sudo setup for ubuntu) from  removing/updating these packages.

I have edited the sudoers file to block apt-get purge/remove which works for the terminal. However this does not work for synaptic or the ubuntu software center

Does anyone know if/how I can block sudo users from adding/removing dansguardian and firehol packages with the software center and/or synaptic?

I am using ubuntu 10.10 RC and software center version 3.02.

Thanks

If your users have root access or physical access they can for the most part do what they want.

You will have to limit what users have root access or accept the possibility they can remove or disable dansguardian and firehol.

Your best option would probably be to build a router, and install those apps or similar functionality you the router (as a transparent proxy). All you would need is an old box with 2 network cards.

---

### Post by sebas929 on 2010-10-06
Hi

Thanks for all the help everyone. I think I will just get an old pc and use it as the proxy, that seems like the best solution at the moment.

---

