---
title: "os choice"
date: 2010-11-01
forum: Server Platforms
---

### Post by mdojka on 2010-11-01
Hi All,

I'm a redhat/solaris admin at work and run a centos 5.5 fileserver at home.  I'm thinking of switching it to ubuntu as I need to do a reinstall anyway.  I haven't used debian or ubuntu before, so there will be a learning curve but that doesn't bother me.  My question here is why should I switch.  I've seen a lot of opinions, but not too much in the way of facts.  The server setup is a quad core amd phenom II (so 64 bit) and a 4Tb raid 6 array for the data.  The reason that I'm reinstalling, and thinking of switching, is that the stock centos kernel is to old for mdadm to convert a raid 5 to raid 6 array.  Also, as this will be a dedicated server and I don't really care about a ui I'm assuming I should go with the ubuntu server distribution.  Thanks.

---

### Post by HermanAB on 2010-11-01
Howdy,

Linux is Linux is Linux...

The only diff between Debian and RHEL is the initialization system, which only runs at start-up.  So if you consider that a server could run 5 years without a reboot, the difference amounts to about 30 seconds / 5 years = 0.00005 percent.

So, yes, you will learn something, which is good, but don't expect your server to work any better, since ultimately, there is no real difference.

---

### Post by eric_1982 on 2010-11-01
Three reason i prefer Debian based systems

1.) Large repo of software

2.) With CentOS the kernel is pretty old. Ubuntu offers a pretty cutting edge kernel while still being very stable. 

3.)I love how fast apt-get is compared to yum and in my experience seems to do a better job at resolving dependencies.

---

