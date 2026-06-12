---
title: "Establishing a SOCKS proxy connection at an internet café"
date: 2011-08-07
forum: Security
---

### Post by Irihapeti on 2011-08-07
I've got my netbook set up so that I can run a SOCKS proxy via my desktop machine. This works fine at home, but I'm wondering what happens at an internet café with public wifi.

Specifically, the connection needs initially to be set up with an ordinary direct internet connection so that I can log in to the café's router. I'm concerned that when I then set the network proxy to SOCKS host, the router will cease to recognise me and will disconnect me.

This particular detail doesn't seem to have been covered in any instructions that I've seen (maybe I haven't looked hard enough). Can anyone tell me from personal experience how one deals with this issue?

---

### Post by HermanAB on 2011-08-07
Howdy,

I use two browsers:
Konqueror with a direct connection, used to make the Cafe system happy and log in.
Firefox with a SSH socks 5 proxy to one of my servers.

One could also use a proxy switching utility in Firefox, but using two separate browsers is easier.

---

### Post by Irihapeti on 2011-08-07
> **HermanAB said:**
> Howdy,

I use two browsers:
Konqueror with a direct connection, used to make the Cafe system happy and log in.
Firefox with a SSH socks 5 proxy to one of my servers.

One could also use a proxy switching utility in Firefox, but using two separate browsers is easier.

Right, so using a system-wide proxy won't work.

Except, if I do and I say that I want it to ignore hosts 10.0.0.0/24 (or whatever the router is using), would that work, too?

I'd prefer not to have to install another browser on the netbook.

---

### Post by HermanAB on 2011-08-07
That should work, or you can use the Foxyproxy add-on to switch.

---

### Post by Irihapeti on 2011-08-07
Thanks. I'll need to find a friendly, local café with wifi and do some testing. :)

---

### Post by bodhi.zazen on 2011-08-07
> **Irihapeti said:**
> Thanks. I'll need to find a friendly, local café with wifi and do some testing. :)

See also : [https://calomel.org/firefox_ssh_proxy.html](https://calomel.org/firefox_ssh_proxy.html)

---

