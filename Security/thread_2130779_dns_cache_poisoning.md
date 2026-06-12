---
title: "dns cache poisoning?"
date: 2013-03-30
forum: Security
---

### Post by nomenkultur on 2013-03-30
So I was running netstat and everything appeared normal wih connections to canonical 91.189... and google 173.... 

then I noticed that chromium also has a couple of connections to some strange 194... and 195... ip's that when traced back go to some 'diniz avilla' corporation


really weird is this one : 195.8.11.76

that displays the google search page but when I try to trace it back there's no mention that it's a google server or any mention of that IP anywhere in the web... all other google IP's point back to google

 I'm connected to my google account bu on this [COLOR=#000000]195.8.11.76 fake google page I'm not[/COLOR]


how should I proceed?

---

### Post by mharv on 2013-03-30
Run tcpdump or Wireshark until you catch this connection starting. If you don't know what to do from there you can scrub the output of any sensitive information, post it on pastebin.com, and then reply with the link to it.

---

### Post by mharv on 2013-03-30
Run tcpdump or Wireshark until you catch this connection starting. If you don't know what to do from there you can scrub the output of any sensitive information, post it on pastebin.com, and then reply with the link to it.

Does running "dig google.com" or "nslookup google.com" list that IP address for you?

It could be this: [http://en.wikipedia.org/wiki/Content_delivery_network](http://en.wikipedia.org/wiki/Content_delivery_network)

---

### Post by cariboo on 2013-03-30
That ip address:

```
195.8.11.76
```

belongs to [PT Comunicacoes, S.A.]("http://casa.telecom.pt/ptresidencial2").

When you find an unknown ip address, make sure you have whois installed, then open a terminal and type:

```
whois <ip address>
```

That way at least you'll know where it originates.

---

