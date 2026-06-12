---
title: "Lockup or possible sleeping new 14.04LTS server on DigitalOcean"
date: 2014-07-02
forum: Virtualisation
---

### Post by 6-ubu3tu-b on 2014-07-02
Hi,

I'm not getting very far with this one myself or with Digital Ocean.

I have a very basic LAMP stack running one site not in general use.
It's a config I've used many times on 12.04LTS and thought I'd give 14.04LTS a go.

My problem is that the machine seems to either lock up or possibly hibernate at random times. Everything stops. No SSH/web/MySQL or even PING. It's as if the machine is turned off.

Occasionally it'll start working after 30/40 mins by itself, a couple of times I got it to respond by waking up a prompt on the virtual console (after 6 hours downtime last night), a couple of other times I had to hard reset.

Everytime I look through /var/logs and see nothing suspect.
It's monitored by New Relic and that shows resources are well inline with availability.

I'd looked around and saw suggestions to disable AppArmor, check for time drifting (NTP is fine), power management (I've not enabled anything)


My question is - has something changed in 14.04 with regards to power management? Surely it would be disabled by default on a server install?

I'm really running out of things to look for on the client and starting to think it could be the vHost.

Any ideas would be greatly appreciated, thanks.

---

### Post by 6-ubu3tu-b on 2014-07-02
:/# apt-cache policy linux-image-generic
linux-image-generic:
  Installed: 3.13.0.30.36
  Candidate: 3.13.0.30.36
  Version table:
 *** 3.13.0.30.36 0
        500 [http://mirrors.digitalocean.com/ubuntu/](http://mirrors.digitalocean.com/ubuntu/) trusty-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     3.13.0.24.28 0
        500 [http://mirrors.digitalocean.com/ubuntu/](http://mirrors.digitalocean.com/ubuntu/) trusty/main amd64 Packages

:/# lsb_release -rd
Description:	Ubuntu 14.04 LTS
Release:	14.04

---

### Post by 6-ubu3tu-b on 2014-07-18
Turned out to be a bad vHost as I thought.

---

