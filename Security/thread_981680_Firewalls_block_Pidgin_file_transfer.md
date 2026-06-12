---
title: "Firewalls block Pidgin file transfer"
date: 2008-11-13
forum: Security
---

### Post by Totenglocke on 2008-11-13
Every firewall I've used in Ubuntu ends up blocking file transfers in Pidgin, even ones I initiate.  Does anyone know of a way to 1)stop this or 2)a firewall that doesn't do this and is easy to use?  I'm currently running Firestarter.

---

### Post by randy78 on 2008-11-13
Pidgin might be randomizing the port it's using to send data on... you could go to the Policy tab in Firestarter, select Outbound from the dropdown menu and set to permissive by default... or you could use the preferred firewall app, UFW, and type: sudo ufw disable in a terminal and then re-enable it (sudo ufw enable) when you're done.

Also, if you're behind a NAT router that has a firewall enabled, this could be a problem as well.
Then again, if you're using a NAT router with a firewall, you don't need a software firewall installed in the first place, since Ubuntu has no open ports by default.

---

### Post by Totenglocke on 2008-11-14
I've got a linksys router, and never had issues with it when using windows and sending files (as long as I make sure my firewall in windows isn't blocking it).  Also, since as soon as I turned off Firestarter I could send the file, I'm sure it's Firestarter causing it.  Oh, I went do follow your instructions, but that was already selected.  Too bad there's no "set this program as safe" or some such option.

---

### Post by randy78 on 2008-11-14
Yeah, Firestarter is blocking your inbound connections, so you'd have to open up some ports... really though, give UFW a shot... especially with GUFW... you can't beat it!

Take Care:popcorn:

---

### Post by kevdog on 2008-11-14
Im not sure by default what port file transfers occur on, and if it is random.  You could attempt to transfer a file while using wireshark to packet sniff and glean the port number possibly.

---

### Post by hyper_ch on 2008-11-14
are you sure you even need a firewall?

---

### Post by Mardoct909 on 2008-11-14
Got a router?

If you have a half-decent router, it is already running a firewall. You can check your router's setting by going to a browser address bar and entering the default gateway. You can find this by finding your network icon on the desktop or wherever and going to properties/information or something.

---

### Post by Dr Small on 2008-11-14
I never run a firewall behind a router/firewall. It causes chaos.
The reason it worked fine in Windows, is because it doesn't have a firewall (or it was disabled).

---

