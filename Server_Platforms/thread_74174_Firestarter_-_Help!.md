---
title: "Firestarter - Help!"
date: 2005-10-11
forum: Server Platforms
---

### Post by philpot on 2005-10-11
I have Firestarter installed and working. I also use Apache 2 to serve virtual hosts. If I connect to any one of the websites I am hosting via my local network, everything works fine. If I try to connect via any other computer, then just the first page (e.g. index.html) will open, anything on that page will not download (images etc.). The page just seems to get "stuck". The problem goes away if I switch off Firestarter. 

Any ideas anyone?

---

### Post by mlomker on 2005-10-11
I assume you've looked at the events tab in the firestarter GUI to see what is being blocked?

They have a great [website.]("http://www.fs-security.com/docs.php")

---

### Post by philpot on 2005-10-11
Well that's the weird thing. The incoming IP address shows up in the status tab, as HTTP port 80, but nothing shows up in the events tab (well, nothing to do with that incoming connection anyway).

Like I say, if I disable the firewall, that problem goes away (only to be replaced by much worse things no doubt!).:???:

---

### Post by yorick on 2005-10-12
Hi!
I seem to be having a similar problem with Firestarter. It seems to be blocking sone of the inbound connections on ports it shows to be open for everyone.  Some connections on the same port get through.
I don't know why it does this.
Anyone has any insight?
Thanks.

Edit: After some more searching I found my answer in [this]("http://www.ubuntuforums.org/showthread.php?t=61944&highlight=firestarter") thread
Hope it helps you too.

---

### Post by [pl]ice on 2005-10-13
don't know if that helps but i got similar 'things' with firestarter, but with 2 network cards,
try clicking 'on' to 'share' the internet connection, as this will actually change the iptables for allowing connections incoming, i have tried adding rules via firestarter for ip access w/o luck.
iptables -nL and the Chain FORWARD (policy DROP) actually added my submasks, thus things started to work, try adding it manually ....

---

