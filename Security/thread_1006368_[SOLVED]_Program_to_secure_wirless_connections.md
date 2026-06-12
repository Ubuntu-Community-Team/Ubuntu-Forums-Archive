---
title: "[SOLVED] Program to secure wirless connections"
date: 2008-12-09
forum: Security
---

### Post by Azabith on 2008-12-09
I used to use a program called ** hotspot shield ** on windows to secure my wireless connection. Any such program on Ubuntu? And any recommended programs for virus scans and firewalls.

Thanks

---

### Post by hyper_ch on 2008-12-09
(1) secure the connection? what do you mean by that?

(2) you have a firewall installed, it's called iptables... by default you shouldn't need to mess around with it

(3) generally no antivirus needed - although there are cases in which you might run one

---

### Post by iponeverything on 2008-12-09
> **hyper_ch said:**
> (1) secure the connection? what do you mean by that?

(2) you have a firewall installed, it's called iptables... by default you shouldn't need to mess around with it

(3) generally no antivirus needed - although there are cases in which you might run one

I just checked out the hotspotshield web site. What the application does is set up a VPN tunnel between your machine and the hotspotshield server so that your traffic can't be read if someone pulls it out of the ether. 

So here some basic hostspot rules:

1) Don't put anything into the ether that you don't want someone else to see.
(opening an email on your gmail account that contains sensitive information is a bad idea) 

2) Save your banking, shopping and bill paying for when you get home. Even though these are done over SSL, you might still have a shoulder suffer or a very creative hack around you.

---

### Post by hyper_ch on 2008-12-09
and then, from the hotspotshield server, what happens there?

I mean why do you want to use a vpn tunnel? how does that protect you (or how do you think it protects you and against what?)

---

### Post by cdenley on 2008-12-09
> **hyper_ch said:**
> and then, from the hotspotshield server, what happens there?

I mean why do you want to use a vpn tunnel? how does that protect you (or how do you think it protects you and against what?)

It just encrypts all your data so any wireless traffic which is captured will not contain any personal or sensitive information. Of course, whenever you send data over the internet, you should assume someone could be intercepting it since you don't know how your data gets to its destination. Unencrypted wireless hotspots make it much more likely, though.

There are a few different ways you can send your hotspot traffic through an encrypted tunnel to your home computer. The easiest would be to install an ssh server at home
```

sudo apt-get install openssh-server

```
create a connection from your laptop to your home computer
```

ssh -D 8080 user@host

```
then configure your browser/computer to use your ssh tunnel as a socks proxy (127.0.0.1:8080).

If you don't send any personal or sensitive data over the internet unless it uses a CA verified SSL certificate, and don't install any servers, then you have nothing to worry about (except someone looking over your shoulder). This goes for any location, including your home.

---

### Post by Azabith on 2008-12-09
I spend most of my time on the road and i connect to the Internet mostly through hotspots. I have been looking around the net and seems the TOR and Privoxy are a good option plus they protect a users anonymity. I have set them both up and the are not working properly. I installed them using synaptic package manager.

---

### Post by cdenley on 2008-12-09
> **Azabith said:**
> I spend most of my time on the road and i connect to the Internet mostly through hotspots. I have been looking around the net and seems the TOR and Privoxy are a good option plus they protect a users anonymity. I have set them both up and the are not working properly. I installed them using synaptic package manager.

If you want to use tor, you should configure privoxy to go through tor by adding this line to /etc/privoxy/config
```

forward-socks4a / 127.0.0.1:9050 .

```
then configure your browser to use privoxy ( 127.0.0.1:8118 ).
[http://www.torproject.org/docs/tor-doc-unix.html.en](http://www.torproject.org/docs/tor-doc-unix.html.en)
[https://check.torproject.org/](https://check.torproject.org/)
[http://www.torproject.org/download.html.en#Warning](http://www.torproject.org/download.html.en#Warning)

Tor hides where your data is coming from. It does not protect you from having your traffic intercepted. In fact, since anyone can run a tor proxy, you should expect to have your traffic occasionally analyzed by someone malicious. The exit node theoretically can't see where the traffic is coming from (there are exceptions), but they can see your unencrypted traffic when they forward it to its destination. If your traffic contains identifiable information such as your username, so much for your privacy.

So, in other words, the warning at the end of my last post would apply for tor users as well. Also, tor would be much slower than tunneling through your home computer.

---

### Post by Azabith on 2008-12-09
The idea of connecting to a home pc sounds good but not possible in my case. I live on a boat and am dependent on internet cafe's and hotspots for internet. And since TOR and privoxy are not so good an option what else is there?

---

### Post by cdenley on 2008-12-09
> **Azabith said:**
> The idea of connecting to a home pc sounds good but not possible in my case. I live on a boat and am dependent on internet cafe's and hotspots for internet. And since TOR and privoxy are not so good an option what else is there?

Nothing. Anytime you send your traffic to a third party to be forwarded, you are trusting that third party with your traffic. Maybe there is a pay service which you can trust. However, like I said, the internet can't be trusted in general. Regardless of how your traffic reaches it's destination, you should always assume there is a possibility it can be intercepted. I suggest you simply use your hotspots and be careful what data you send unencrypted. If the page you're accessing uses SSL (https) and firefox doesn't give you any warnings about the certificate, then it's safe.

---

### Post by Azabith on 2008-12-09
thanks cdenley that was really helpful

---

