---
title: "Internet banking setup"
date: 2010-02-05
forum: Security
---

### Post by jochem on 2010-02-05
I'm a Linux newbe, but I'm worried. My parents are using the same (windows) laptop for internet banking, as my little brother does for doing all sorts of dangerous things. 

So I thought I'd create a persistent bootable linux usb stick just for internet banking.

(1)Is Ubuntu suited for this?
(2)Should I use firefox or chrome, or any other browser?
(3)Should I use apparmor? This is enabled by default in Ubuntu right?
(4)Should I use a firewall like iptables? How easy is this to set up?
(5)Should I disable unneeded services? Or doesn't this make my Ubuntu more secure?
(6)I've heard things about encrypting home. Should I do this?

Links to simple newbe guides to Linux security are appreciated.

---

### Post by ajgreeny on 2010-02-05
> **jochem said:**
> I'm a Linux newbe, but I'm worried. My parents are using the same (windows) laptop for internet banking, as my little brother does for doing all sorts of dangerous things. 

So I thought I'd create a persistent bootable linux usb stick just for internet banking.

(1)Is Ubuntu suited for this?
(2)Should I use firefox or chrome, or any other browser?
(3)Should I use apparmor? This is enabled by default in Ubuntu right?
(4)Should I use a firewall like iptables? How easy is this to set up?
(5)Should I disable unneeded services? Or doesn't this make my Ubuntu more secure?
(6)I've heard things about encrypting home. Should I do this?

Links to simple newbe guides to Linux security are appreciated.

Here are answers to your questions.

1]  Yes.
2]  Either browser is fine, it really doesn't matter, use whichever you prefer.
3]  No need to specifically use this, just use the browser as normal.
4]  When you use Ubuntu it will already be using iptables and you will not need to configure it any more.
5]  No real need to do this as they will not really make a scrap of difference to security.
6]  Again no real need to do this unless you are totally paranoid about security. It can also make life a bit more difficult if things go wrong and you need to retrieve your home files with a live CD system.

For a general discussion on Ubuntu security see [https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

---

### Post by jochem on 2010-02-05
> **ajgreeny said:**
> Here are answers to your questions.

1]  Yes.
2]  Either browser is fine, it really doesn't matter, use whichever you prefer.
3]  No need to specifically use this, just use the browser as normal.
4]  When you use Ubuntu it will already be using iptables and you will not need to configure it any more.
5]  No real need to do this as they will not really make a scrap of difference to security.
6]  Again no real need to do this unless you are totally paranoid about security. It can also make life a bit more difficult if things go wrong and you need to retrieve your home files with a live CD system.

For a general discussion on Ubuntu security see [https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

Thanks! Not having to do all those things will save some time :)

---

### Post by Bachstelze on 2010-02-05
I agree with all of the above except:

2) I personally don't trust anything Google, so Chrome is a no-no for me
6) Encrypted home directories are totally transparent to the user. Especially on an USB stick, which is easily lost/stolen, it would be a good idea.

---

### Post by doas777 on 2010-02-05
some clarification on firewalls and services:

in order for anyone to contact your machine, they need a service on your pc that is listening for commands recieved on a port.

in ubuntu _by default_, there are no network services installed, so there are no open ports that will take a command. as a result iptables is there but not doing anything (which si fine, you don't have any ports that need protecting.)
if you start opening network ports and/or installing network services, then some firewall configuration may be required, but it is still minimal. 

for local services, you don't need to worry about them from a banking security perspective, but it may be useful for prevent privilege escalation expolits if someone ever gets access to your box physically. disk encryption is the same way. it protects you against someone stealing your laptop, not against a hacker mining your data while you are logged in.

---

### Post by jochem on 2010-02-05
Thanks for clearing things up everyone!

---

