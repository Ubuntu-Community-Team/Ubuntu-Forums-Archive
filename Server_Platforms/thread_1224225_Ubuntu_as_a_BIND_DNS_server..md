---
title: "Ubuntu as a BIND DNS server."
date: 2009-07-27
forum: Server Platforms
---

### Post by markcaetano@gmail.com on 2009-07-27
Evening.

I'm looking into running my own DNS for web hosting. I'm familiar with Ubuntu, I've used it since 5.10 and recently found CentOS.

What I'd like to know is should I use CentOS 5.3 or Ubuntu to serve as the BIND 9.6 DNS server and maybe some additional tasks like POP/IMAP etc.

They're both options when ordering the VPS so there's no drama there.

On a side note, what is the advantage of not installing X?

Regards,
Mark

---

### Post by jhannah on 2009-07-27
Frankly, either OS will get the job done just fine. It is really a matter of what you are most comfortable with. Unless you are expecting to see a very considerable amount of DNS traffic, I think a VPS will also suit your needs well. The only other concern that would come to mind is if you had a large number of zone files you needed to serve. Depending on the VPS platform, you might be artificially limited to a small number of file descriptors (though this isn't usually an issue). I would say if you are serving more than 100 zones, you might want to talk to whomever you purchase the VPS to make sure it won't be an issue. The same goes for POP3/IMAP, provided you aren't maxing out your VPS either OS should work just fine.

Lastly, not installing X doesn't really buy you too much now-a-days. The only real advantage is that you won't have the overhead of installing all of the supporting libraries and packages that X would pull in. Unless you are really tight on space, it isn't a very big difference. It's also worth keepign in mind that it can sometimes be nice to use something like FreeNX or X11 forwarding to accomplish some GUI tasks remotely.

---

