---
title: "Postfix display name settings"
date: 2020-02-11
forum: Server Platforms
---

### Post by NotQuiteSU on 2020-02-11
I set up postfix to relay emails via Gmail. Everything seems to working, except when the emails end out, they will come from accountname <myaddress@gmail.com>, rather than FirstName Last <myaddress@gmail.com>.

I know I can specify a from header when sending a message, but is there a way to set that so it applies automatically? I think aliases? But I'm not familiar

---

### Post by SeijiSensei on 2020-02-11
It's usually easiest to configure this in your email client and send your mail as "FirstName Last <myaddress@gmail.com>".  There are probably ways to do this at the server, but it's much easier on the mail client.

---

