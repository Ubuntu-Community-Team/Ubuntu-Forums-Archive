---
title: "POSTFIX sending html messages"
date: 2009-02-15
forum: Server Platforms
---

### Post by csergec on 2009-02-15
Hi everybody!


Is there a way to send html messages with postfix?
I googled a lot but did not find any solution.

I configured postfix to relay to my Windows Exchange server.
I can open and read the messages through outlook.
But all the messages are text/plain

I added > MIME-Version:1.0
Content-Type: text/HTML; Charset=UTF-8

But it did not change anything.

BTW the change is made through PHP.

In other words, is it possible to change the headers of postfix, because even if adding [trying to modify] the content-type, the line  > Content-Type: text/plain always remains in the headers and then appear the lines I added? It seems that Postfix considers them as part of the message but not as the indications I want...

Thank you for your help.

Serge

---

