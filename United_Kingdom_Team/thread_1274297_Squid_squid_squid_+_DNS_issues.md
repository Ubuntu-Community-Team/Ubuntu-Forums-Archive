---
title: "Squid squid squid + DNS issues"
date: 2009-09-24
forum: United Kingdom Team
---

### Post by The Umanga on 2009-09-24
Good morning!...
I need urgent help. When I try to browse from the proxy server I am able to but when I try from the client PCs on the LAN I cannot access the internet. I can resolve addresses from my PCs but can't get the page to display, getting DNS error.
 
I don't know that would have something to do with iptables not being present on the machine? 
 
Cheers Umanga!....

---

### Post by gillespiea on 2009-09-24
does your squid proxy server have the linux firewall installed? could be the problem. Are you using the correct port to connect to your proxy? default is 3128.

The reason you can use the internet on when using the computer with the proxy installed is because it doesn't actually use the proxy (unless you have specifically told it to).

Just sounds to me like the ports aren't open on the proxy. i am using squid myself and i need to find out how to open some ports myself for my email, pidgin, ssh etc. etc. If i find out how to i will let you know.

---

### Post by The Umanga on 2009-09-24
I decided to keep the default port. When I specify the proxy in the internet explorer I get the error "the requested url could not be displayed" There is no firewall running right now, I am not yet sure about the files that I need to edit to get the walls running. So far I know I know squid is running right I had errors earlier which I managed to fix, the server is browsing using lynx no problem. When I remove the proxy settings I am getting dns error.

---

