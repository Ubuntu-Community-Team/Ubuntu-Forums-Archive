---
title: "Relay Issue With Exchange 2019 Receive Connector"
date: 2019-12-20
forum: Server Platforms
---

### Post by yuljk2 on 2019-12-20
Hi guys - Up until recently I was able to relay mail from my Ubuntu 18.04 server through an Exchange 2019 receive connector.  The connector is setup with the correct IP address for the Ubuntu server and authentication is set to 'Anonymous'  When testing if relay works correctly on the Ubuntu server I get '550 5.7.54 SMTP; Unable to relay recipient in non-accepted domain'

If I attempt to relay from a Windows machine it works fine.

Any ideas why this has stopped working?

Many thanks

---

### Post by darkod on 2019-12-20
When saying "relay mail from my Ubuntu server", what does it mean exactly?

1. Is an application on the Ubuntu server using the Exch2019 directly as mail server?

2. Or the application is using the postfix on the Ubuntu server which then relays messages to the Exch2019?

If it's the second, maybe the domain is not listed as accepted in postfix?

That message is pretty descriptive, the domain is not accepted either in one or the other server. Or both. :)

Also, if you are using postfix on the ubuntu machine, did you check its logs?

---

### Post by yuljk2 on 2019-12-20
Nevermind - Got this working, was related to my DNS configuration.

---

