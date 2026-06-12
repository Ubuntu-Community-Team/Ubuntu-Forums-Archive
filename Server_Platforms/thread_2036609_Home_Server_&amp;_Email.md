---
title: "Home Server &amp; Email"
date: 2012-08-02
forum: Server Platforms
---

### Post by jnichols51 on 2012-08-02
I have setup a home server so I can learn Linux and servers. Two of the programs I have setup (backuppc & CRON jobs through Webmin) send emails to users on the system. I have setup sSNP (I think that was the name) for forward emails to my real account. But I can't seem to figure out how to get other software on the server to use that to email out.

I have no interest in running an email service that is public facing. I was wondering though if it would be a good idea to setup email on the server for local accounts then set the my email to forward to my public email server. Or even how to allow access to that email box from my iPhone even if it doesn't take incomming email.

I also have a Netgear router that will mail logs. I was hoping I could point it to that same email program so I could save my logs and run scripts against it for patterns and the like.

Does anyone know of a good tutorial to do something like that for a new but learning Ubuntu Server fan?

---

### Post by LHammonds on 2012-08-02
My my scripts, I use a command-line email program called "sendemail" which can send to any email address...internal or external.

You could even set it up so that your scripts can use a real public email system such as gmail.

If you click some of the links in my sig, you can find scripts that I have written that make use of that particular email program.

LHammonds

---

### Post by jnichols51 on 2012-10-24
I decided to try and setup Postfix to trap mail from the server. It seems to work however I am still having issues knowing how to address email so it gets to the Postfix server and delivers the email correctly. I was able to get the router to email me but I can't seem to figure out how to get backuppc to correctly email me with problems.

---

