---
title: "Upnp"
date: 2008-07-28
forum: The Cafe
---

### Post by coreyxjessica on 2008-07-28
Is Upnp that insecure? It's the only way I've ever been able to get a port to open to bittorrent. I've searched many forums and none of them have been successful. Forwarding ports only worked in xp, even when I disabled the firewall in ubuntu. Is it going to kill me using it? Btw - I have a wireless router with 128 bit wep in an apartment. I might change it to WPA, but my DS doesn't support it. Any suggesstions?

---

### Post by jpeddicord on 2008-07-28
UPnP is only enabled on your own network, so unless you've got troublesome users at your home, there's no problem with enabling it provided your router supports it.

Malicious programs can take advantage of UPnP to maybe run a spam server with the port open, but the chance of that happening (especially in Ubuntu) is slim to none as long as you are careful.

---

### Post by coreyxjessica on 2008-07-28
> **jacobmp92 said:**
> UPnP is only enabled on your own network, so unless you've got troublesome users at your home, there's no problem with enabling it provided your router supports it.

Malicious programs can take advantage of UPnP to maybe run a spam server with the port open, but the chance of that happening (especially in Ubuntu) is slim to none as long as you are careful.

That's what I was thinking, to update my original post I decided to buy a DS adapter, so I set my router to WPA2 Personal using TKIP+AES Algorithms. I also locked down the firewall in the router. I mostly use OS X and Ubuntu anyways so I hope I should be fine.

---

### Post by coreyxjessica on 2008-07-28
If there's any other comments I'd appreciate it.

---

### Post by coreyxjessica on 2008-07-28
I switched my algorithm to AES for better security. How long of a hex key should I use with WPA2 Personal? I currently have a 26 character long hex key.

---

### Post by original_jamingrit on 2008-07-29
[http://www.gnucitizen.org/blog/hacking-the-interwebs/](http://www.gnucitizen.org/blog/hacking-the-interwebs/)
[http://www.gnucitizen.org/blog/hacking-with-upnp-universal-plug-and-play/](http://www.gnucitizen.org/blog/hacking-with-upnp-universal-plug-and-play/)
[http://www.gnucitizen.org/blog/more-upnp-hacking-fun-with-google-media-server/](http://www.gnucitizen.org/blog/more-upnp-hacking-fun-with-google-media-server/)

UPnP is an attack vector, and it's really an unnecessary feature to have.  It's not going to provide many problems on a Linux environment, but on a Windows platform where virus may want to phone home, it can be a big deal.  UPnP can basically work without your acknowledgment.

Why can't you use port forwarding normally?  Are you behind a router?

---

### Post by coreyxjessica on 2008-07-29
> **original_jamingrit said:**
> [http://www.gnucitizen.org/blog/hacking-the-interwebs/](http://www.gnucitizen.org/blog/hacking-the-interwebs/)
[http://www.gnucitizen.org/blog/hacking-with-upnp-universal-plug-and-play/](http://www.gnucitizen.org/blog/hacking-with-upnp-universal-plug-and-play/)
[http://www.gnucitizen.org/blog/more-upnp-hacking-fun-with-google-media-server/](http://www.gnucitizen.org/blog/more-upnp-hacking-fun-with-google-media-server/)

UPnP is an attack vector, and it's really an unnecessary feature to have.  It's not going to provide many problems on a Linux environment, but on a Windows platform where virus may want to phone home, it can be a big deal.  UPnP can basically work without your acknowledgment.

Why can't you use port forwarding normally?  Are you behind a router?

I've followed every single tutorial imaginable and been to many forums, my router doesn't wanna port forward.

EDIT - Scratch that it was just a problem with my router not correctly rebooting in DD WRT. I've disabled UPnP.

---

