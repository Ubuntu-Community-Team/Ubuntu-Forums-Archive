---
title: "Postgresql Installation help?"
date: 2006-02-19
forum: Server Platforms
---

### Post by Virogenesis on 2006-02-19
I'm trying to set up postgresql on my local machine for webdev purposes. 
I'm just wondering how I'd go about setting up postgresql in a secure manner localy.
I've done a searches on the forum but not much in the way of postgresql.
I did do a couple of google searches I've found one but wasn't sure on it.
So any help would be great.

Thanks

---

### Post by rich on 2006-02-19
Can you be more specific ?

Postgresql is well-behaved in my experience. What is going wrong for you ?


Rich

---

### Post by Virogenesis on 2006-02-19
Well I'm use to the mysql which requires you to create a password.
I'm guessing I'll need to do that aswell but how do I go about that and what will I need to edit to make it only accept local as I have only one box so basicaly how to lock it down.
I've found pgphpadmin to replace phpmyadmin for a start.
Just basicaly need to know the best way to configure it.
I'm inexperienced dealing with this and basicaly need to know the in and outs.

---

### Post by LordHunter317 on 2006-02-19
No, you don't want to do that.

Postgresql does something far superior: it looks at the owner of the process talking to it, and uses that to make a decision.

As long as the database is local, this is a superior solution.

This means that in order to do administration, you have to su/sudo to postgres.  This isn't a big deal.

It also means that in order for Apache to access databases, you need to create a 'www-data' account in PostgreSQL, and grant it the appropriate permissions,

Don't bother with a web-based tool.  IME, it's generally not needed -- postgres is really simple to work with.

---

