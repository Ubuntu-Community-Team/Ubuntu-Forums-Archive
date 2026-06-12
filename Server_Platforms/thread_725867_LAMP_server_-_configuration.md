---
title: "LAMP server - configuration"
date: 2008-03-16
forum: Server Platforms
---

### Post by Psicolonia on 2008-03-16
Hi everyone,

here's my situation:

[LIST]
[*]I've looked for this a lot but couldn't find anything
[*]I've got the lamp server working
[*]MySQL is working
[*]Apache is working
[/LIST]

but here's the problem: I've got two accounts on that machine, each one with a LAMP project. I've created two directories on /var/www and two MySQL accounts with different privileges as well as two linux users X and Y. I also included in /var/www/X and .htaccess for security (for user X).

But there is no security, the X forlder has 755 permissions that enables the user Y to peek inside. I wouldn't like this to happen! But if I increase security, apache won't be able to see the Directory. I don't want the user Y to peek or otherwise.

In an online web server we see only our folder! In my LAMP everyone has read access to the web folder that is common! Can anyone give me some guidelines on restricting the access completely from these users so that they only touch and read what is theirs?

Thanks in advance!

---

### Post by Psicolonia on 2008-03-17
i got a solution:

made the directory on /var/www chmod 770
added www-data to my group

thanks anyone

---

