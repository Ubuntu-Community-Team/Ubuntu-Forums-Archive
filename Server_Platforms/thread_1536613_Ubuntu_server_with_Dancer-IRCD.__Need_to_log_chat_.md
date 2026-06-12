---
title: "Ubuntu server with Dancer-IRCD.  Need to log chat (server side if possible)"
date: 2010-07-22
forum: Server Platforms
---

### Post by xrazzicaz on 2010-07-22
Hi,

Just set up a 10.04 server today, running with dancer-ircd and dancer-services packages to create a private IRC server.  However, there's a requirement to log chats against users/host/IP address for future reference.

I was wondering if there was a built in server side approach (rather than separate bots per channel) to log chats in such a way?

Many thanks for reading - here's hoping someone's already done this!

---

### Post by sfr on 2010-07-22
It is usually considered very bad to log the chat on irc servers, the question of privacy arises. I haven't seen an irc server that lets you log the chat globally and hope to never see one. If you need to log the chat in a specific channel the easiest thing to do is to have a bot (eggdrop or alike) babysit it.
If you really want to log every bit of chat you probably have to take up programming as a hobby.

---

