---
title: "setup complete mail solution"
date: 2016-09-02
forum: Server Platforms
---

### Post by i-ivanov on 2016-09-02
Hi Guys

i hope that post this in the right section :)

I want to set up complete mail solution on a google compute engine ,its easy and cheep. My research in that meter oriented me to following solution :

1.Ubuntu 14 LTS (i was always going to use ubuntu anyway.)
2.Postfix (MTA)
3.Dovecot (for po3 and imap support)
3.ViMbAdmin (for admin panel on the mail server)
4.Roundcube (for webmail client)

Can anyone provide me with working guide how to install them (i did try few with no luck) and if anyone have better solution for me i will be very grateful.

---

### Post by ajgreeny on 2016-09-02
*Thread moved to **Server Platforms**.* which I think is your situation and is more appropriate for the problem.

If I'm wrong and this is not a server query post and tell us.

---

### Post by darkod on 2016-09-02
If you only want a mail server and no other roles on the machine, maybe something like iRedMail would be better for you?
You can read more here: [http://www.iredmail.org/](http://www.iredmail.org/)

You install basic standard ubuntu server (with OpenSSH Server included of course), and without adding any packages/software you run the iredmail script which downloads and installs everything for you.

Otherwise manually you need to chase up too much SW and integrate it. For example you didn't mention mysql but usually you need some sort of DB to hold the usernames, virtual mailboxes, etc. So you would need mysql too.

There are other options around, like Zentyal, but that is more for installing in offices/networks, and if you want to set up AD.

For a simple email server, I only know of iRedMail.

---

### Post by i-ivanov on 2016-09-02
Hello darkod

Thank you replaying so fast 

Yes i did not mention MySql but its by default ,and in previews configuration as u said mysql will handle virtual mailboxes users

Your suggestion looks very promising and i will look it ,can i usee free version to set up for a few domains do u know ?

---

### Post by darkod on 2016-09-02
Yes, the free version allows multiple domains as far as I know.

---

