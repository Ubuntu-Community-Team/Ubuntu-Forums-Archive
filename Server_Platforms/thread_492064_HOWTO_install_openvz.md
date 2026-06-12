---
title: "HOWTO: install openvz"
date: 2007-07-04
forum: Server Platforms
---

### Post by eterps on 2007-07-04
I had to perform the following steps to get openvz running on Ubuntu (Feisty in this case):

**Installation:**

Add the following line to /etc/apt/sources.list
    deb [http://debian.systs.org/](http://debian.systs.org/) stable openvz

sudo wget [http://debian.systs.org/dso_archiv_signing_key.asc](http://debian.systs.org/dso_archiv_signing_key.asc)
sudo apt-key add dso_archiv_signing_key.asc
sudo apt-get update

apt-cache search ovzkernel-
sudo apt-get install ovzkernel-<version>
sudo apt-get install vzctl vzquota

**Adding an Ubuntu guest:**

cd /var/lib/vz/template/cache/
wget [http://download.openvz.org/contrib/template/precreated/ubuntu-6.06-i386-minimal.tar.gz](http://download.openvz.org/contrib/template/precreated/ubuntu-6.06-i386-minimal.tar.gz)
sudo cp /etc/vz/dists/debian.conf /etc/vz/dists/ubuntu.conf

sudo vzctl create 101 --ostemplate ubuntu-6.06-i386-minimal
sudo vzctl set 101 --onboot yes --save
sudo vzctl set 101 --ipadd 192.168.1.210 --save
sudo vzctl set 101 --nameserver 192.168.1.2 --save
sudo vzctl set 101 --hostname host.name.com --save
sudo vzctl start 101

sudo vzctl exec 101 passwd
sudo vzctl exec 101 ps fauwx

**See which VEs are running:**

sudo vzlist -a

**Get status:**

sudo vzctl status 101

**Connecting to your VE:**

ssh root@192.168.1.210

---

### Post by draga on 2007-07-08
Great. Short but complete. Thank you

---

### Post by boufleur on 2007-08-02
I follow the steps but network is not working. I can log in the VE, but I can't ping the outside world. What I did wrong?

---

### Post by Barzille on 2007-08-23
Hi there,
Feisty comes with kernel 2.6.20. How did you get the correct version for ovzkernel. The only stable ones I found, are 2.6.18...

---

### Post by wiflye81 on 2007-10-15
Because this repo is a debian and the last kernel version of debian stable is 2.6.18 if I'm not mistaken.
The only solution is take the src rpm package on the openvz wiki, extract it and compile it...

I am currently trying it, the patch work but I can't compile it because I don't have the time for it.

We need a true Ubuntu repository, with the lastest kernel for each versions, anybody to do it :biggrin:?

---

### Post by edmnc on 2007-11-14
> **boufleur said:**
> I follow the steps but network is not working. I can log in the VE, but I can't ping the outside world. What I did wrong?

Actually I have arrived at the same problem (on gutsy) :(

I can ping VE from the HW node and vice versa, but cant't ping anything else from the VE

@Barzille I simply installed 2.6.18 anyway. Then again maybe thats why networking is not working ...

---

### Post by aggelos on 2007-11-14
> **edmnc said:**
> Actually I have arrived at the same problem (on gutsy) :(

I can ping VE from the HW node and vice versa, but cant't ping anything else from the VE

@Barzille I simply installed 2.6.18 anyway. Then again maybe thats why networking is not working ...

Try edit your VE /etc/interfaces :

auto eth0 (your VE interface)
iface eth0 inet static
  address VE IP  (10.1.1.10)
  gateway  your gateway IP (10.1.1.1)
  netmask VE netmask (255.0.0.0)

---

### Post by Bite_me_Bill on 2007-11-14
Have you enabled IPV4 forwarding?

[https://help.ubuntu.com/community/OpenVZ#head-8e98eb3e80c1e3e542a8b7ea157d05a70bc65fd0](https://help.ubuntu.com/community/OpenVZ#head-8e98eb3e80c1e3e542a8b7ea157d05a70bc65fd0)

---

### Post by edmnc on 2007-11-15
Ahh, networking didn't work actually because of this bug:
[https://bugs.launchpad.net/ubuntu/+source/procps/+bug/84537](https://bugs.launchpad.net/ubuntu/+source/procps/+bug/84537)

Now everything works fine. Thanks!

---

### Post by bodhi.zazen on 2007-11-19
I posted a longer How-to :

[http://ubuntuforums.org/showthread.php?t=617225](http://ubuntuforums.org/showthread.php?t=617225)

---

