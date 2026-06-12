---
title: "Replace Microsoft Exchange"
date: 2012-01-09
forum: Server Platforms
---

### Post by Derktoon on 2012-01-09
So I work for a mid sized (about 100 employees) company that is 100% microsoft. So we have and exchange server and outlook. Well today my boss tells me that we need to try and cut costs and i suggested we look into dropping Outlook and Exchange for something that would work just as well..

we primarily use just email and calendars. So my first thought was that there has to be a free linux solution, but im not sure where to begin. Can anyone give me some pointers?

---

### Post by Habitual on 2012-01-09
Zimbra

---

### Post by Mia1990 on 2012-01-10
Outlook comes with office so you really just want to replace Exchange server I'm taking it there's thunder bird if you want to replace outlook. There are a lots of groupware servers for Linux and Ubuntu that work with outlook [Citadel]("http://www.citadel.org/doku.php") and [SOGo]("http://www.sogo.nu/english.html") are free for just email and calendars i think both should do everything that you're using ms exchange for.I like SOGo myself. [Scalix]("http://www.jumpingbean.co.za/applications/scalix-mail-server") looks like a good one but you have to buy it [Open-Xchange]("http://www.open-xchange.com/en/home.html") [Zimbra]("http://www.zimbra.com/") [Zarafa]("http://www.zarafa.com/content/home") and [EGroupware]("http://www.egroupware.org/") I think you have to buy them as well i may be wrong on that i don't know. Just google groupware servers it brings up a lot of them.

Well good luck. Linux in your company is a great way to save or cut cost and the Ubuntu server is unmatched.
Mia

---

### Post by Lars Noodén on 2012-01-10
You won't find a lot that works as well as MS Exchange, but you will find ones that work much better. ;)

The two main all-in-one groupware packages to examine would be [Kolab](http://kolab.org/) and [Citadel](http://citadel.org/).  Both are quite modular so there are parts that can be dropped or replaced.  Both are in Ubuntu's package repository.

I'm not sure how to replicate the lost or delayed messages that Exchange is famous for, but unreliable connections could be simulated with IP Tables.  ;)

---

### Post by excelinexcel on 2012-01-10
Thanks!

---

