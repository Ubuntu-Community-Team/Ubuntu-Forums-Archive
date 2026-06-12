---
title: "Why are Ubuntu config files so poorly commented?"
date: 2008-08-08
forum: Server Platforms
---

### Post by moonpup on 2008-08-08
Hi all,

This is not inteneded as a flame so please bear with me, but why are config files in Ubuntu either poorly commented or not commented at all? I'm a Redhat administrator and have gotten used to their long, complete and well commented config files.

For example: I can go into /etc/postfix/main.cf on a Redhat box and see a complete config file with all the variables and supporting comments to go with it. Why does Ubuntu not do this?

Now, I can appreciate the fact that by Ubuntu not commenting these config files, they are lean and easy to view and find information but sometimes you forget what a variable is and what it does and having a nice fully commented config file comes in handy.

Does anyone know why config files in Ubuntu are so sparse? I presume this is by design but personally I really don't like it.

---

### Post by jerome1232 on 2008-08-08
Are you talking about something more like the one under /usr/share/postfix/main.cf.dist ?

---

### Post by moonpup on 2008-08-08
> **jerome1232 said:**
> Are you talking about something more like the one under /usr/share/postfix/main.cf.dist ?

No, I'm talking about the file above (/etc/postfix/main.cf) which is created and used after you install, configure and start postfix. Maybe I'm missing something, but that file is really sparse. :)

---

### Post by StickyStyle on 2008-08-08
> **moonpup said:**
> No, I'm talking about the file above (/etc/postfix/main.cf) which is created and used after you install, configure and start postfix. Maybe I'm missing something, but that file is really sparse. :)

The  /usr/share/postfix/main.cf.dist *is* the 652 line version that has every possible setting documented.  No sense in having all that cruft in the file your working on, when the end result may only be 35 lines.

---

### Post by moonpup on 2008-08-08
OK, I see your point and agree. For my own clarification and understanding of how Ubuntu does things, is common for all the config files?

What I mean, is there a default config file for all services somewhere like in the example you give above which has all the settings and comments? Is there a standard path/directory where these will be located?

---

### Post by windependence on 2008-08-08
It seems to be the way they do it. I was rather surprised myself having used RedHat, CentOS, and SuSE. It's always nice to have the explainations right there unless you do configs all day every day and most people don't. I don't consider it to be cruft at all.

-Tim

---

