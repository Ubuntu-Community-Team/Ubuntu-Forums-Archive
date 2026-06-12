---
title: "[SOLVED] tor not changing ip address"
date: 2009-01-01
forum: Security
---

### Post by oneadvent on 2009-01-01
I cannot seem to get tor to change my ip address. I installed tor, privoxy and vidalia, and it all says it is working right.

Can anyone help me figure out what I did wrong?

---

### Post by Vantrax on 2009-01-01
From memory TOR doesn't change your IP.

Tor routes your connection through a group of servers so that the connection at the end sees the server as the point of origin not you. If they tried to trace the connection they would have to get logs for so many servers in so many countries that they would spend years digging through and eventually hit a country that doesnt require the logs to be surrendered.

So You -> Tor -> Server

The problem with TOR is Javascript and Flash can still get your originating IP even using TOR, so if you do use it run NoScript in Firefox to disable them.

---

### Post by Dr Small on 2009-01-01
Did you setup Firefox correctly to use privoxy? If I recall, the settings are "localhost" and "8118".

---

### Post by oneadvent on 2009-01-01
>  Did you setup Firefox correctly to use privoxy? If I recall, the settings are "localhost" and "8118". 

I did not do that, where do those settings go?

---

### Post by Dr Small on 2009-01-01
> **oneadvent said:**
> I did not do that, where do those settings go?
Most everyone uses the TorButton addon for Firefox, but you can manually change the network settings under Edit>Preferences>Advanced>Network>Settings button and change the SOCKS host to use "localhost" and port "8118"

---

### Post by oneadvent on 2009-01-01
Ah thank you. I got it working. I used FoxyProxy, because torbutton kept getting an "internal error."

Thanks for the help. I didn't realize it was a two fold solution.

---

