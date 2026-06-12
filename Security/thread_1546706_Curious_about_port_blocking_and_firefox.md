---
title: "Curious about port blocking and firefox"
date: 2010-08-05
forum: Security
---

### Post by espressobeanie on 2010-08-05
So, I was kind of noticing that firefox will only become completely blocked if all outbound traffic in ufw is blocked. But I don't understand how firefox continues to work if all outbound traffic is allowed and all inbound traffic is blocked.       

How does, for ex, google.com send information that renders on my firefox build if I blocked all incoming traffic?

---

### Post by OpSecShellshock on 2010-08-05
It's not really denying incoming traffic; it's actually denying incoming connections being initiated from the web. When you run, for example, Firefox, the initiation of the connection to the web is happening on the client side, in other words from your local machine. Since the connection was established by your local machine, responses from the external sites are allowed. However, an external site can't connect to your computer out of the blue without you initiating it.

---

### Post by lovinglinux on 2010-08-06
> **OpSecShellshock said:**
> It's not really denying incoming traffic; it's actually denying incoming connections being initiated from the web. When you run, for example, Firefox, the initiation of the connection to the web is happening on the client side, in other words from your local machine. Since the connection was established by your local machine, responses from the external sites are allowed. However, an external site can't connect to your computer out of the blue without you initiating it.

Well said.

I just want to add that, even if you don't block incoming connections, a web site cannot connect to your Firefox browser out of the blue without you initiating it. That's because Firefox is not a server and does not listen to incoming connection requests on any port. All incoming data that reaches your browser belongs to a connection that was once initiated by your browser. These connections have also a "short" lifetime and once they die, Firefox rejects any data coming from the remote site.

This is the reason why Ubuntu doesn't even come with the firewall enabled by default, because any connection originated from the web that tries to reach your machine will be rejected anyway, since there are no relevant servers running by default and thus all ports are already closed.

This changes if you install a server, like a BitTorrent client, which can accept unrequested connections, by listening to a specific port. Nevertheless, a firewall is most likely to be ineffective on this situation, because you would need to allow those connections to increase your torrent speed. So, you would be using the firewall to block ports that are already closed and allowing the only port that can accept unrequested connections. Not much useful, don't you agree?

A firewall is useful if you need to limit who can access a server. For instance, I use a firewall to block access to my ssh server from the web, while allowing full access from other machines in my local network.

---

### Post by espressobeanie on 2010-08-06
Ahh, I see. So, Firefox is creating an outbound session started by me through the TCP protocol. Makes sense. But if the firewall is denying all incoming requests, how come I still get ip blocks from moblock? Does moblock sit outside the ufw firewall or have higher precedence with the iptables?

---

### Post by lovinglinux on 2010-08-06
> **espressobeanie said:**
> Ahh, I see. So, Firefox is creating an outbound session started by me through the TCP protocol. Makes sense. But if the firewall is denying all incoming requests, how come I still get ip blocks from moblock? Does moblock sit outside the ufw firewall or have higher precedence with the iptables?

Both moblock and ufw create iptables rules. Moblock rules comes first. If the packet is not blocked by moblock rules, then they go through the rest of the iptables chain.

BTW, moblock can also handle your regular iptables rules, since it has the ability to run custom scripts. Therefore, you don't need ufw if you know how to create iptables rules. This is what I do. Moblock is my only iptables manager.

---

### Post by OpSecShellshock on 2010-08-06
> **espressobeanie said:**
> Ahh, I see. So, Firefox is creating an outbound session started by me through the TCP protocol. Makes sense. But if the firewall is denying all incoming requests, how come I still get ip blocks from moblock? Does moblock sit outside the ufw firewall or have higher precedence with the iptables?


Well, you're not allowing the connections to be initiated, but some external hosts will go ahead and try anyway, just in case. It's normal, and won't succeed.

---

### Post by bodhi.zazen on 2010-08-06
> **espressobeanie said:**
> Ahh, I see. So, Firefox is creating an outbound session started by me through the TCP protocol. Makes sense. But if the firewall is denying all incoming requests, how come I still get ip blocks from moblock? Does moblock sit outside the ufw firewall or have higher precedence with the iptables?


UFW is a configuration tool for iptables. Your firewall is iptables (which is a front end for netfilter).

If you wish to understand what is happening, you really need to read up on iptables.

In a nutshell, when you set the default to deny in UFW you are denying all NEW connections, but ESTABLISHED and RELATED traffic is allowed.

If that did not make sense to you, see:

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

---

