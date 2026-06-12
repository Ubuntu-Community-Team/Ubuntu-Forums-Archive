---
title: "Postfix : users and interface"
date: 2006-12-06
forum: Server Platforms
---

### Post by Koybe on 2006-12-06
Hello,

I would like to set up postfix on a server with 2 conditions :

- I must be able to send an email to a group of person trough a single mail address. Something like [email]financial@domaine.org[/email] sends a mail to all the people in that group.
- I'dlike to have a simple webinterface to manage this.

Any ideas?


Thank you!

---

### Post by Koybe on 2006-12-07
No one can help on this one?

---

### Post by NewbieUser on 2006-12-07
Koybe:

I am far from an expert on Postfix, but I do use it on my corporate server.  I would think that you could set up an alias map to handle what you want to do.  I forward several different accounts into an administrator mail box so it should be doable.  Or, thinking as i type, you could also use a recipient bcc map and copy the incoming mail to a list of senders in a hash file.  Does that sound close to what you are trying to do?

---

### Post by Koybe on 2006-12-08
Yes I can do an alias, but in a very small structure i want my boss being able to do this easily. And as far as I know (not too much :P) i need to open the aliases file to do this?

---

### Post by chrisfay on 2006-12-08
You might receive better help if you stated a bit more info. Installing and managing a Postfix server can be very complicated and without some details regarding your network structure, software that you will be combining with Postfix (POP/IMAP, MySQL, Auth), knowlege history in relation to server setup and management etc.. its difficult to give direction.

As far as web management for a Postfix based server, you can use [Postfixadmin]("http://high5.net/page9.html") but it requires a good understanding of Postfix's configuration to get the software up and running. I belive the configuration of Postfixadmin is based on a MySQL backed Postfix setup which is way beyond any explination here. There are a bunch of howto's written specifically for configuring a Postfix MySQL system.


> Yes I can do an alias, but in a very small structure i want my boss being able to do this easily

An 'easily' maintained Postfix server will be relative to his knowledge and required management within the setup. I personally run and manage my own Postfix, MySQL, Dovecot, SASL setup for a large user base and can assure you it is anything but 'easy' to maintain let alone install without a strong uderstanding of the working parts. I would start by checking out the Postfix website for information then progress to some howtos to gain an idea of what is possible. 

Just some thoughts....Good luck

---

### Post by Koybe on 2006-12-10
I tried Postfixadmin some times ago and didn't really find what I need. Anyway, I was not asking for a full config... but an orientation to do what I want to do. It would be a simple smtp server with pop mailboxes.

But if there is no simple way to do it, i'll have to manage it by myself. I just want someone with a knowledge of what smtp/pop is can manage it without command line. Maybe not possible...

---

