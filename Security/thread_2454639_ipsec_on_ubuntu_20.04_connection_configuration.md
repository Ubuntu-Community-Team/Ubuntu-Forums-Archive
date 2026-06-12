---
title: "ipsec on ubuntu 20.04 connection configuration"
date: 2020-12-03
forum: Security
---

### Post by tomeksup on 2020-12-03
Hello everyone


I wanto change system on ubuntu 20.04 at work but main problem is setting up vpn ipsec  with servers. 

I tried many tutorials from web and i am too dumb to do this. 
Please guide me how to do that. 

Thank you for you attention

---

### Post by EuclideanCoffee on 2020-12-03
Unfortunately you'll have to speak to your system administrator. Typically the vendor of the VPN will configure your desktop with a client.

---

### Post by tomeksup on 2020-12-04
> **EuclideanCoffee said:**
> Unfortunately you'll have to speak to your system administrator. Typically the vendor of the VPN will configure your desktop with a client.

No, i have configured server, everything works on win10 with multiple clients. Forticlient have an option to choose good kind of connection. On ubuntu is a mess, hundred of not working tuttorials in a web, no option in forticlient.

On MacOS everything works too.

---

### Post by CelticWarrior on 2020-12-04
[https://kifarunix.com/install-forticlient-vpn-client-on-ubuntu-20-04-ubuntu-18-04/](https://kifarunix.com/install-forticlient-vpn-client-on-ubuntu-20-04-ubuntu-18-04/)

The above should just work.
Keep in mind they don't officially support Ubuntu 20.04 yet but according to the link above you can just download and install the .deb file. I strongly recommend you use the new feature 'sudo apt install ./<.deb file>' as it deals with all the dependencies.

If this method doesn't work please post all the error messages you got so we can take a look at it.

---

### Post by EuclideanCoffee on 2020-12-04
Here is the source for downloads. [https://www.forticlient.com/repoinfo](https://www.forticlient.com/repoinfo)

As a former Fortinet sys admin, I can confirm that it works for Ubuntu.

---

### Post by tomeksup on 2020-12-04
hello 

Thank you for advice. I installed forticlient on ubuntu 20.04. There is no problem to install it. Problem is in configuration. There is no ipsec connection. So this program dont support it.

---

### Post by tomeksup on 2021-01-07
Anyone will help me to resolve problem ?

---

