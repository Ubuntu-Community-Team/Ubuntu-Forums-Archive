---
title: "why my instances sometime could run well but sometiem it couldnt"
date: 2011-01-23
forum: Ubuntu Cloud and Juju
---

### Post by indrasuryatama on 2011-01-23
,. My Windows/linux instances sometime could run well, but sometime  (mostly) it goes terminated after pending state..
  When I run on my hybrid fox the reason is "Instances no longer reported as existing"... 
  What can I do ? 
  Just for your information I use 100 Mbps switch, and all of the computer (front-end and node) is Dual core Processor E5400 @2.70 Ghz with 2 GB RAM

---

### Post by ubudog on 2011-01-23
What service are you using?  Amazon?

---

### Post by indrasuryatama on 2011-01-25
> **ubudog said:**
> What service are you using?  Amazon?

i use eucalyptus from the ubuntu enterprise cloud.....
have some idea?

---

### Post by ubudog on 2011-01-25
> **indrasuryatama said:**
> i use eucalyptus from the ubuntu enterprise cloud.....
have some idea?

Sorry, but I don't think I can help.  :-(

Maybe someone else here can help you.

This link may be of some use, I'm not sure.

[http://open.eucalyptus.com/wiki/EucalyptusTroubleshooting_v1.5](http://open.eucalyptus.com/wiki/EucalyptusTroubleshooting_v1.5)

---

### Post by indrasuryatama on 2011-01-25
> **ubudog said:**
> Sorry, but I don't think I can help.  :-(

Maybe someone else here can help you.

This link may be of some use, I'm not sure.

[http://open.eucalyptus.com/wiki/EucalyptusTroubleshooting_v1.5](http://open.eucalyptus.com/wiki/EucalyptusTroubleshooting_v1.5)

any way tx for your respon :) ill try to fix it and i will keep informed 

it makes me crazy because sometime the instance run well on my system

---

### Post by ubudog on 2011-01-25
Hmm... someone here can probably help...

---

### Post by indrasuryatama on 2011-01-26
> **ubudog said:**
> Hmm... someone here can probably help...

hope so... is the problem is with ubuntu 9.10

---

### Post by ubudog on 2011-01-26
Have you tried using newer versions of Ubuntu?  Like 10.04, 10.10?

---

### Post by indrasuryatama on 2011-01-26
> **ubudog said:**
> Have you tried using newer versions of Ubuntu?  Like 10.04, 10.10?

i have different problem when running on 10.04
my windows image can go to the running state... but i cant access , i cant ping the VM and i cant access it through RDP
i also have tried to change gen_kvm_libvirt .. but still cant access my VM

---

