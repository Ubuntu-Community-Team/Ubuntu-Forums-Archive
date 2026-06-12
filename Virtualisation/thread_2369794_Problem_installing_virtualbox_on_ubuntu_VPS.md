---
title: "Problem installing virtualbox on ubuntu VPS"
date: 2017-08-26
forum: Virtualisation
---

### Post by budiman123 on 2017-08-26
sorry for my bad english
Hello i'm new to ubuntu
Recently i just purchased ubuntu 16.04 VPS from digitalocean and i want to install virtualbox on it
I have followed the step written on this website : [https://www.ostechnix.com/install-oracle-virtualbox-ubuntu-16-04-headless-server/](https://www.ostechnix.com/install-oracle-virtualbox-ubuntu-16-04-headless-server/)
When i type on putty : sudo apt-get install build-essential dkms unzip wget
I got : E : unable to locate package dmks
I have tried searching the answer on google but still couldn't solve it
Please help me

---

### Post by deadflowr on 2017-08-27
*Thread moved to** Virtualization***

---

### Post by SeijiSensei on 2017-08-27
Follow the instructions here 

[https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

to add the Oracle repository to your system and install VB from there.  It will automatically install any needed dependencies like dkms or gcc.

---

### Post by budiman123 on 2017-08-28
I have followed the step from link above and got this error when using sudo apt-get update

E: The method driver /usr/lib/apt/methods/gttp could not be found.
E: Failed to fetch gttp://download.virtualbox.org/virtualbox/debian/dists/S0lsb_release/InRelease
E: Some index files failed to download. they have been ignored, or old ones used instead

---

### Post by SeijiSensei on 2017-08-28
Perhaps it's a typo.  The link should begin with http, not gttp.  Take a look at /etc/apt/sources.list.d/virtualbox-xxxxxx.list where xxxxxx is replaced by the name of the release you are using, Trusty in my case.  You should see a line like
```
deb http://download.virtualbox.org/virtualbox/debian trusty contrib
```

---

### Post by TheFu on 2017-08-28
> 
It may be possible but it is not a planned or supported feature. In general nested virtualization provides poor performance and is not recommended. I do know that solutions like virtualbox will function on a droplet but again with poor performance.
From [https://www.digitalocean.com/community/questions/does-digitalocean-support-nested-kvm-now](https://www.digitalocean.com/community/questions/does-digitalocean-support-nested-kvm-now)

---

### Post by budiman123 on 2017-08-29
> **SeijiSensei said:**
> Perhaps it's a typo.  The link should begin with http, not gttp.  Take a look at /etc/apt/sources.list.d/virtualbox-xxxxxx.list where xxxxxx is replaced by the name of the release you are using, Trusty in my case.  You should see a line like
```
deb http://download.virtualbox.org/virtualbox/debian trusty contrib
```

sudo nano /etc/apt/sources.list.d/virtualbox-xenial.list:
it shows : deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) xenial contrib
but when i run sudo apt-get update, still got the same error E: The method driver /usr/lib/apt/methods/gttp could not be found.
any other way to change the E?

---

### Post by SeijiSensei on 2017-08-29
Do you have an equivalent file ending in .save?  Is that one correct, too?  

There is a protocol called [GTTP](https://tools.ietf.org/html/draft-ietf-ccamp-tunproto-01), but it's totally unrelated to downloading files.

---

