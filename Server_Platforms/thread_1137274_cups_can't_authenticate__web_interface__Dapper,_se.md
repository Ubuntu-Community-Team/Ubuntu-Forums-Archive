---
title: "cups: can't authenticate / web interface / Dapper, server"
date: 2009-04-25
forum: Server Platforms
---

### Post by Matyy on 2009-04-25
Hej

I have a server that should manage the printing, too. It has no gui, so I want to use the the web access to control it.

So I want to add a printer - but when it asks me for the user/password I can't authenticate.

I added cupsys to shadow, added my username to lpadmin, added 
User cupsys
group lpadmin 
to the cupsd.conf, restarted cups. But it doesn't help.
I access the web interface from the computer I am using to work, but I tried it with links2, too (I access the server with ssh).

It is Ubuntu 6.04 - can't upgrade right now since it is beyond my control. 

I googled and looked in forums, but all they write is that I should add cupsys to shadow, and my user to lpadmin and those couple of lines in the cupsd.conf. I read that I should add a root account, but I won't do that - is that the only option? I read often, that the webinterface of cups is "crippled" and I should use gnomes cups manager, but without gnome that's no option.

Any ideas?

---

### Post by cariboo on 2009-04-25
In a default cups setup, you can only access it from the computer it is running on. When it asks for a username/password use you user name for that computer. I not sure how it works on older version, but since 8.04, it only asks for a username/password when installing a printer.

---

### Post by Matyy on 2009-04-26
So, not even with ssh? That can't be can it? I use links2 in a shell with ssh... 

It's only when installing a printer (or deleting). 

I use a user with sudo rights who is in the lpadmin group.

---

