---
title: "Ubuntu As A Pop Server Routed From Exchange"
date: 2009-04-06
forum: Server Platforms
---

### Post by EEK2112 on 2009-04-06
We would like to use Ubuntu Server 8.1 as a "pass through" or "Interface" of sorts to retrieve mail via POP. Better explained below.

_**What We Would Like To Do:**_
Users have Outlook somewhere outside our network
Outlook connects to Ubuntu via POP looking for mail 
Ubuntu gets mail from exchange mailboxes sitting on the server.

We need the mailboxes to stay on the exchange server.

Is this possible? Has anyone done this? What software did you need/use?

Any help would be great.

---

### Post by TwiceOver on 2009-04-06
Any reason you don't want to use Outlook via RPC over HTTPS directly to your Exchange?  Or even turning on POP3 in Exchange?

---

### Post by EEK2112 on 2009-04-06
want to separate the roles, I have OWA running on another server. 

We are under new management that is basically demanding POP access. We are also taking control of another domain and pointing it here, the mail users are already using POP.

So we are going to replace the OWA with POP.

---

