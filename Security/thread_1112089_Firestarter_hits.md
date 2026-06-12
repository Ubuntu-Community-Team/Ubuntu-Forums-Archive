---
title: "Firestarter hits"
date: 2009-03-31
forum: Security
---

### Post by Porto143 on 2009-03-31
Hi, Im a ubuntu newbie :(

My firestarter very often indicates various hits and network activity is always 0.1kB/s...
Something like this:
```
www.upload.rastlinka.com/file/firestarter.png
```
Should I be worried about my security?

---

### Post by hyper_ch on 2009-03-31
are you sure you need firestarter at all?

---

### Post by Porto143 on 2009-03-31
no, but read somewhere on this forum that its good to have, just in case ...

---

### Post by hyper_ch on 2009-03-31
why is it good to have it?

---

### Post by Porto143 on 2009-03-31
strange question, try to google "why firewall"

---

### Post by lovinglinux on 2009-03-31
You should be worried about your security, but not because of this situation. 

Those connections were blocked, so there is nothing to worry about. Besides, it is pretty common to get those hits, specially if you have a dynamic IP. This happens  because when you connect to your ISP they provide an address that is not yours all the time. So, depending on what the previous "owner" of the IP was doing, you might get connections attempts from machines that still think you are him. They are called ghost packets and they tend to stop after a while.

Additionally, connection attempts are only a security risk if you have an application listening to the port the connection is trying to reach and if this application has security flaws. If you don't run any application that listen to incoming connections, than a firewall is not even necessary, because even if those connections can reach your machine, they will do nothing.

If you have a router, then you can use it's firewall and forget about Firestarter.

Looking at your log, it seems that you are not using a router or you have several ports opened, otherwise you wouldn't get so many connections on different ports. What were you doing during these logs?

Firestarter is not actually a firewall, it is simply tool that allow you to create rules for the real firewall (iptables+netfilter) without knowing the necessary commands. Firestarter is not recommended anymore, specially for connection monitoring. The current recommended firewall manager is ufw (gufw for gui). If you still want to use Firestarter, then you should configure it and close the GUI, otherwise you could be putting your machine at risk, because Firestarter needs root privileges to run. Don't worry, once you configure the rules you can close it because the real firewall will do his job in the background.

As hyper_ch said, you probably don't need a firewall. Nevertheless, if this will bring you some peace of mind, then use it anyway. I don't use a firewall manager like Firestarter, but I do create my own firewall rules using iptables commands, I have a firewall in the router and I also use moblock ip blocker. But I'm kind of paranoid, specially when torrenting. Either way, you should understand Ubuntu security and make your own decision based on knowledge and on what you need, instead of using a security tool just because you needed when using Windows.

A good place to start - [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by lovinglinux on 2009-03-31
> **Porto143 said:**
> strange question, try to google "why firewall"

He knows the answer. He just want to make you think about it, instead of using it without understanding it.

---

### Post by bodhi.zazen on 2009-03-31
> **Porto143 said:**
> strange question, try to google "why firewall"

:lolflag:

hyper_ch is asking you so we may help you. If yo do not know how you are wanting to use a tool such as a firewall it is hard to advise you.

I suggest you read : [Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by Porto143 on 2009-03-31
thx for answer lovinglinux

I dont have a router and i have a static ip adress.
That time I was just browsing web (gmail, youtube, few forums).
Im really paranoic about it coz Ive got few serious events too and Im using paypal etc so Im afraid...

---

### Post by bodhi.zazen on 2009-03-31
> **Porto143 said:**
> thx for answer lovinglinux

I dont have a router and i have a static ip adress.
That time I was just browsing web (gmail, youtube, few forums).
Im really paranoic about it coz Ive got few serious events too and Im using paypal etc so Im afraid...

Well, that is why we are asking what you are wanting.

A firewall will not help with those things.

Only you can control what shady sites you choose to visit (or not) and your firewall will permit such traffic as you initiated the contact.

As far as on line banking, you need to make sure you are using https (ssl) to connect and beware of Phishing. Again a firewall will not help with this either.

IMO responding to a ping is not a security risk, your millage or opinion may vary.

You need to close any open ports, open port are the (potential) problem, although that too is secondary to properly configuring your servers.

Since none of your examples involved a server, and since a default install of Ubuntu has no significant open port, you are fine.

See : [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/) and run lsof to see if you have any listening servers.

---

### Post by lovinglinux on 2009-03-31
To protect your web activity you should use [AdBlock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865") and [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722") Firefox extensions.

---

### Post by bodhi.zazen on 2009-03-31
> **lovinglinux said:**
> To protect your web activity you should use [AdBlock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865") and [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722") Firefox extensions.

And apparmor :

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-8.10/usr.lib.firefox-3.0.8.firefox.sh](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-8.10/usr.lib.firefox-3.0.8.firefox.sh)

---

### Post by Porto143 on 2009-04-01
Thank you, guys, for the help ... Ive already uninstalled Firestarter and discovered my open ports.

---

