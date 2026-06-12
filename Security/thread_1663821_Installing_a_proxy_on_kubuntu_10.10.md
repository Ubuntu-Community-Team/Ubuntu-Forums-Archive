---
title: "Installing a proxy on kubuntu 10.10"
date: 2011-01-10
forum: Security
---

### Post by Lillitou on 2011-01-10
Hello everybody,

I am trying to install a proxy on my Kubuntu 10.10, since I live in a country that blocks access to almost everything. I tried to install squid, anon, socks.. both with command-line and KPackageKit, but every time, I have this error message:

```
subprocess installed post-installation script returned error exit status 1
```

Does anyone have a clue?

Thanks in advance.

---

### Post by HermanAB on 2011-01-10
OK, so you are in a difficult spot, but you need a server in a friendly spot to connect to.

See this:
[http://www.aeronetworks.ca/howtos/skype-ssh-tunnel-howto.html](http://www.aeronetworks.ca/howtos/skype-ssh-tunnel-howto.html)

---

### Post by nemesis056 on 2011-01-10
Does Hotspot shield work with UBUNTU 10.04???

---

### Post by Lillitou on 2011-01-10
> **HermanAB said:**
> OK, so you are in a difficult spot, but you need a server in a friendly spot to connect to.

See this:
[http://www.aeronetworks.ca/howtos/skype-ssh-tunnel-howto.html](http://www.aeronetworks.ca/howtos/skype-ssh-tunnel-howto.html)

Thanks a lot for your reply.
I'm trying to follow the instructions... Just a little question (and excuse my ignorance :???:): with which domain name shall I replace example.com in the script you gave?

---

### Post by HermanAB on 2011-01-10
Howdy,

You need a server in a friendly place.  If it has a domain name, use that.  If it is only an IP address, use the address.  The bottom line is that you need to own/rent a server from Godaddy/Rackspace/CiHost/whatever.

Otherwise, there are VPN services that you can sign up for, but then you need to use their software to connect.

You could also look into peer to peer systems like Tor.

---

### Post by Lillitou on 2011-01-10
Thank you, 

I have already tried to use tor, same problem. 

I was more interested in something as simple as hotspot shield, that works only on windows/macos. I'm frankly not interested in renting a server, and not even sure I can pay for it online even if I wanted to.. 

I tried to google for VPN services, but almost all available links are censored :(

thank you anyway.

---

### Post by HermanAB on 2011-01-11
So, your problem is that you are already behind the internet filter and you don't have a way out.  

You can search anonymously via Google using [https://google.com](https://google.com), and you can probably also reach many more places by going via the google translate service, which works like a proxy: [http://translate.google.com](http://translate.google.com)

I ran a socks proxy search for you:
[http://uniqueinternetservices.com/](http://uniqueinternetservices.com/)
[http://proxy.insorg.org/en/](http://proxy.insorg.org/en/)
[http://www.bpsocks.com/](http://www.bpsocks.com/)
[http://secondwww.com/](http://secondwww.com/)

See whether you can access one of them.

---

### Post by HtmlGifted on 2012-03-29
I found Tor works really good if you can get it to install... I am using it and finding nice but slow at times.. I was looking for a way to set my services to use the tor network when I cam across this thread.. 

I have 10.4 (lucid) gnome.

I have tried looking for the settings for connection to proxy in system network but that settings is not available..

---

