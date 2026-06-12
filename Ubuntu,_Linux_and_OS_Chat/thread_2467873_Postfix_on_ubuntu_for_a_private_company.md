---
title: "Postfix on ubuntu for a private company"
date: 2021-10-10
forum: Ubuntu, Linux and OS Chat
---

### Post by John_A._Nau on 2021-10-10
I have a small network that needs some help.
They have postfix running on an ubuntu server in the DMZ.  Thtey believe they need DNS configured correctly.
I dont think they do as the ISP is athorative for the Domain and the MX record point to their public ip.
Wouldnt it be best to simply use the public dns internally and perhaps a host file for the clients and the servers,
or at least serve up dns to a fictitious domain that they could buy so it never routes on the internet?
Please advise.  Their Linux servers are all 18.04 LTS.

Thank you

---

### Post by TheFu on 2021-10-10
a) they should be looking to migration off 18.04 NOW.  Normal support ends in about 6 months.
b) Should they have internal AND external names for servers?  Perhaps.  I can't tell from the information listed.
c) What are the clients, how many clients are there, are external clients allowed to connect without using a VPN?

There are no exact answers without exact information.

The way we deal with it is by having an email gateway that is on the internet, and we keep the real email server internal. All in/out SMTP goes through the email gateway.  This keeps the load down and reduces the risks to just the gateway which doesn't hold any data, just configs.  Plus, having multiple secondary gateway machines means that you don't need to worry about ISP outages - put 1 at a VPS provider for $10/month.  When the main server cannot be contacted, it will store inbound emails until it comes backup - a store and forward setup in addition to the primary/secondary MX server setup in DNS.

Then you can decide whether internal clients connect to a gateway or to an internal email server directly for sending. And it provides a clear reason to force the use of VPN to access the real email server, which is good for security corporate-wide.  More complex email servers are hard to keep secured. They have lots of moving parts integrated together that can break after any update.  If that is all on the same machine, the possibility of having external customers see any email issues is greatly increased too.

But only you know the complexity of the clients and network there. We do not.

---

