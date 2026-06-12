---
title: "Jabber/XMPP File Transfer Proxy Setup"
date: 2009-08-25
forum: Server Platforms
---

### Post by shoaibi on 2009-08-25
At our office we have a local Jabber setup for all the employees. Problem comes with file transfers. Files can be transfered in the same subnet/same geographic location but not abroad cities. I came to know that for that we need proxy. I tried proxy.jabber.org and it went fine, but for security reasons we dont want private files to be transfered via a public proxy server.
I asked #ubuntu and ikonida suggested that squid might do the deal else i will need to setup socks.
I tried with squid but couldnt get any results, same issues. It behaves as if the next user canceled the file transfer.

On sock, i researched a bit and found dante-server. I am looking forward to your help on what should i do next.

[EDIT]:
I have tried proxy65 and have installed it but how can i integrate in the already existing jabber server setup? what should users give in the proxy field of pidgin? etc

---

### Post by Noah0504 on 2009-10-12
I use Openfire for a Jabber server.  I know it has built in support for file transfer proxy via port 7777.  I have it enabled and the the port forwarded, however, I've never really been able to test it, so I do not know if the users have to do anything else on their end in their client.  Having said that, I assume it works!  :)

Perhaps this is something to look at.

---

