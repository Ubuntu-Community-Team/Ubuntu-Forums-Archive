---
title: "Zarafa server and Evolution"
date: 2008-07-30
forum: The Cafe
---

### Post by quinnten83 on 2008-07-30
Does anybody know if you can configure a Zarafa server to work in a native Evolution mail client? and if so how?
I know Evolution is made to work with a ms Exchange server, but my company uses Zarafa and I really want to make it work.
In windows you need to install a piece of software, which automatically gets recognized as an outlook server, but I can't find any information about Zarafa on linux with Evolution.

---

### Post by adrighem on 2009-02-02
Zarafa has no evolution-support. You can connect to the mail using the imap-gateway on the zarafa-server, that's what I'm using. The calendar should work (read-only) with the iCal-gateway service on the zarafa server.

The Evolution team is working on a real MAPI interface. Combine that with the zarafa MAPI-support and evolution should have 100% zarafa support by next summer. (*hoping*)

---

### Post by nocturn on 2009-10-28
It won't work.  Evolution is working on MAPI/RPC support, which is MS proprietary wire protocol.

Zarafa serves MAPI over SOAP, which requires a seperate library.  If the evolution backend had implemented MAPI properly, it would only be a matter of doing MAPI over SOAP, but right now, it does nothing usefull unless you run Exchange.

---

