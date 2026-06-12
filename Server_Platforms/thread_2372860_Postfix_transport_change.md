---
title: "Postfix transport change"
date: 2017-09-29
forum: Server Platforms
---

### Post by Icarusbop on 2017-09-29
Hello:

I have a Linux server that is running postfix, I didn't set this server up, but looking after it has fallen to me.
all email coming in is sent out via an ip address, which I now need to change.

I thought this would be set up as a relay, but config does not match up with my expectations.
```
relay_transport = relay
relayhost =
```
This seems to indicate no relayhost...
I did a search on the IP of the outgoing server and found a file called 'transport' here is the (anonymised) content
```
__esg_default__  :__esg-encoded__3A12.34.56.7825
```
In this file I can see the IP address I need to change FROM (12.34.56.78)  but the IP address is wrapped in something I don't recognise,
```
__esg_default__  :__esg-encoded__3Axx.xx.xx.xxB25
``` making me think this is not a normal file I can just change to my new address.
I then found a reference to this file in the postfix config:
```
transport_maps = obj:domain:/etc/postfix/transport
```
I can't find anywhere on the internet that explains the transport_maps being to an object  "obj:" - everything I find shows it mapping to a 'hash'

Does anyone recognise this transport setup and can advise on how to modify it correctly? At the moment I'm drawing a blank, I could just change the IP in the file, and do a test, but I'm hoping to have some kind of backup plan if that does not work as expected.
Regards:
Icarusbop

---

### Post by slickymaster on 2017-09-29
Thread moved to **Server Platforms** for a better fit

---

### Post by SeijiSensei on 2017-09-29
If it were me, I'd remove the references to transport maps and simply enter the IP address in the "relayhost" directive.  If all your outbound mail is going to the same upstream server, that makes the most sense.

---

