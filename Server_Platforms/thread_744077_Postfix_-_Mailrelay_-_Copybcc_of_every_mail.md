---
title: "Postfix - Mailrelay - Copy/bcc of every mail"
date: 2008-04-03
forum: Server Platforms
---

### Post by chewbakka on 2008-04-03
Hi forum,

i want to set up a new postfix mailrelay in front of our exchange server.
The part where i´m stuck is, that according to company policy (which by the wa is acceptet by the employes), from every outgoing mail there has to go a copy in the publicfolder outgoing (outgoing@company.tld) and the same with incoming. 

I assume the best way is to add a bcc to every mail, but how. if i use always_bcc, there will be no posibility to have an incoming and and outgoig archive mailbox?

Any suggestions are appreciated..

or if you know another good mta as a mail relay that can do the trick easily please let me know.

---

### Post by zazuge on 2008-04-30
postconf -e 'always_bcc = spy'
that's all i know

---

