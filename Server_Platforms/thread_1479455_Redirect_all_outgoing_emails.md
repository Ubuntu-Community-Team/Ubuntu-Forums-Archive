---
title: "Redirect all outgoing emails"
date: 2010-05-10
forum: Server Platforms
---

### Post by iDev247 on 2010-05-10
Hi everyone,

Here's what I'm trying to do to complete my rocking :guitar: development server.

I would like all outgoing email on my Ubuntu server to be redirected to one email address (internal or external). I don't have any mail server installed yet (I'll probably use postfix unless you have another suggestion).

The reason I would like this to work is because I'm a web developer working on multiple projects. When I start working on a new project I would like to be able to test some of the forms and features in the web application (PHP) without having emails sent to the email address configured in the application. I can always change configurations but having my development server forward the emails would save me lots of trouble.

Example:
If one of my php application sends an email to: user1@domain.com, user3@domain4.com... I would like all of them to forward to myemail@domain.com

Please let me know if this is possible. If you need any additional information feel free to let me know.

Thanks,
Pat

---

### Post by Bachstelze on 2010-05-10
You could do that ussing a catch-all virtual alias for all your domains:

[http://www.postfix.org/VIRTUAL_README.html#virtual_alias](http://www.postfix.org/VIRTUAL_README.html#virtual_alias)

---

### Post by iDev247 on 2010-05-17
> **Bachstelze said:**
> You could do that ussing a catch-all virtual alias for all your domains:

[http://www.postfix.org/VIRTUAL_README.html#virtual_alias](http://www.postfix.org/VIRTUAL_README.html#virtual_alias)

I'll try to experiment with this and will reply when I have an update.

Is it possible to do domain wildcard with this? The sites I'm developing  are have about 2000+ users/memberships using different  email addresses. It would be pain in the but inserting every domain  name.

Any suggestion?

---

### Post by davidcyber00 on 2010-05-17
hi just thaught ill add to it ive been on ubuntu for white some time now just wondering how do I delete the ubuntu partition??? tried it and i couldd only delete the others but one of them was looked and i dont know how to unlock it
wanted to make a new partition and install windows seven from my memory pen but it wont boot and it will go directly to the ubuntu load screen 
thanks for reading hope you reply :D

---

