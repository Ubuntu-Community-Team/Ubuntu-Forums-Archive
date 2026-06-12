---
title: "Quick Firestarter Question"
date: 2010-01-12
forum: Security
---

### Post by ngrieb on 2010-01-12
I was just checking out the security sticky on the main page. In it there is of course a link to Firestarter. In the link it shows you how to disable the password and enable auto-startup of Firestarter, but it seems to enable Firestarter with sudo permission. 

Correct me if I'm wrong, but I thought I saw a post about this allowing for attacks because of the sudo permissions, is this the case? Is there any way around this or to make it more secure to autorun a firewall?

Thanks.

---

### Post by xpod on 2010-01-12
> **ngrieb said:**
> I was just checking out the security sticky on the main page. In it there is of course a link to Firestarter. In the link it shows you how to disable the password and enable auto-startup of Firestarter, but it seems to enable Firestarter with sudo permission. 

Correct me if I'm wrong, but I thought I saw a post about this allowing for attacks because of the sudo permissions, is this the case? Is there any way around this or to make it more secure to autorun a firewall?

Thanks.

Firestarter is not in fact a firewall but instead just a GUI tool for configuring your actual firewall....Iptables.
You can configure Iptables directly from the terminal although there`s also a few other GUI tools for getting the job done.
There`s absolutely no need for Firestarter to be running at startup though and once you`ve done any "configuring" with Firestarter you should then close it......unless you like to sit back and watch all the blocked connctions.;)

If you really *need* to create Firewall rules on your Ubuntu box though the general advice here nowadays is to use the default [Uncomplicated Firewall](https://help.ubuntu.com/8.04/serverguide/C/firewall.html).There`s even a GUI tool for that too if you prefer.You`ll find it in your package manager if you do a search for "GUFW".

I used to use Firestarter(for the simple ICS ability) myself without issue but that was before the collection of dedicated Routers began.

---

### Post by bodhi.zazen on 2010-01-12
> **ngrieb said:**
> I was just checking out the security sticky on the main page. In it there is of course a link to Firestarter. In the link it shows you how to disable the password and enable auto-startup of Firestarter, but it seems to enable Firestarter with sudo permission. 

Correct me if I'm wrong, but I thought I saw a post about this allowing for attacks because of the sudo permissions, is this the case? Is there any way around this or to make it more secure to autorun a firewall?

Thanks.

use ufw or gufw

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

---

