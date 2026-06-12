---
title: "Gufw / Firestarter / general firewall question"
date: 2009-02-01
forum: Security
---

### Post by frankwakeman on 2009-02-01
A bit basic this I suppose, but anyway:  I have had the Gufw firewall going since I resumed using Ubuntu (8.10) and also had it on Mint.  I just tried Firestarter and it seems there's more to it than Gufw.  Or are they just differing levels of front end to the same innards?  Should I get rid of one of them?

If I don't configure any rules is the firewall essentially not doing anything?  I just use Firefox for normal browsing, no stupid risk sites, and on the now rare occasions I use Limewire I can tell a dodgy file from a legitimate one.  I use a credit card online about once every six weeks.

I mostly use Vodafone Mobile Broadband, with a USB 3G dongle modem, no home network and wireless is off 99% of the time, except when I use a Wetherspoons pub's free wireless.

So, have I got anything to be concerned about?  I'm not going to be too delighted if I have to learn a load of technical stuff but I thought I'd enquire in case I've nothing to worry about here.

---

### Post by lswb on 2009-02-01
firestarter, ufw/gufw, lokkit, and similar programs are all front ends to the linux "iptables" command. iptables can be used directly but the syntax is not very friendly.

---

### Post by HermanAB on 2009-02-01
Ubuntu is secure out of the box.  If you haven't installed any servers such as Apache, Postfix, FTP and what not, then it is still secure and you need not do anything.

Relax and enjoy it!

Cheers,

Herman

---

### Post by hyper_ch on 2009-02-04
are you sure you need to play around with iptables? how do you connect to the net?

---

### Post by Sorivenul on 2009-02-04
Unless you have a server installed, no ports are actively "listening" by default. A firewall is not really needed unless you have services running that are listening to various ports. And, I certainly wouldn't muck around with iptables, in any way shape or form. I've got a friend who has been running Ubuntu since Breezy and hasn't had an issue - no Firestarter/Gufw or fiddling with iptables.

---

