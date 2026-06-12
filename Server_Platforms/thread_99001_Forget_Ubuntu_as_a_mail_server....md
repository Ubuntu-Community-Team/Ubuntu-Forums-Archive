---
title: "Forget Ubuntu as a mail server..."
date: 2005-12-04
forum: Server Platforms
---

### Post by darkpixel on 2005-12-04
I have been fighting to get Breezy setup as a mail server for several days now and I am about ready to give up.

I started off with postfix and courier.
I set everything up to handle virtual domains through mysql.
After two days of dorking around and trying to get maildrop to work, I find out the latest maildrop package doesn't support mysql...or the courier auth daemon.

So I debated compiling from sources vs switching to a different mailer.

I decided to give exim a shot.

Wow.
What's with the exim4 configuration process under ubuntu?
Under every other distro I've used, there a /etc/exim/exim.conf file which is easy to configure.  Under ubuntu there's a confusing system of editing files under conf.d and playing with macros and finally compiling that data into a config file.

I really can't see an advantage to that configuration style.  Am I missing something?

So after another two days of not getting exim4 to work, I am almost ready to ditch ubuntu on my server.

Am I missing something with postfix / courier?  Has anyone else set them up to use virtual domains on Ubuntu?

Is anyone using a different configuration for virtual mail domains under Ubuntu?  (sendmail maybe?)

If anyone has it, I would really appreciate a pointer to an explination of Ubuntu's exim4 configuration.  I'm totally lost.

---

### Post by dutchie on 2005-12-04
Dont know if this is of any help, but I just read the following howto, which also explains how to setup postfix and courier on Ubuntu:

[http://www.howtoforge.com/perfect_setup_ubuntu_5.10](http://www.howtoforge.com/perfect_setup_ubuntu_5.10)

---

### Post by darkpixel on 2005-12-04
[QUOTE=dutchie]Dont know if this is of any help, but I just read the following howto, which also explains how to setup postfix and courier on Ubuntu:

[http://www.howtoforge.com/perfect_setup_ubuntu_5.10](http://www.howtoforge.com/perfect_setup_ubuntu_5.10)[/QUOTE]
Thank you for the pointer, but that howto doesn't address virtual domains.

---

### Post by dutchie on 2005-12-04
Sorry, I posted the wrong link. Been reading too many howto's in preparation for my server install...

This one covers the postfix virtual domain side using mysql as well:

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

---

### Post by darkpixel on 2005-12-04
From what I understood about the setup, you had to use maildrop to actually transport the message into the virtual domain's folder.

I guess this way postfix does it by itself...without maildrop?

Anyways--you rock.  I can't believe after 5 days of beating my head against the wall I finally got it working.

Thank you.

I love Ubuntu--I've been using it for just over a year now, and this was the first time I had a doubt about it working for me.

---

### Post by Daveo on 2005-12-05
You know VHCS would probably work great for what your trying to do. 
I have it installed on breezy and I love it.

If you need some help setting it up let me know as i am making a how to.

(For breezy, I know there is one for hoary on here)

---

### Post by nagilum on 2005-12-05
You can have exim4 with one monolithic config-file, just run 'dpkg-reconfigure exim4-config' and watch for the question regarding the splitup config files.

---

### Post by Jimzilla on 2005-12-08
This is a good one for virtual domains and users [http://www.howtoforge.com/virtual_postfix_mysql_quota_courier]("http://www.howtoforge.com/virtual_postfix_mysql_quota_courier")

---

### Post by caraboy on 2005-12-22
I have some problems setting a mail server too. I`ve switched from rpm based distributions to ubuntu, and from sendmail to postfix. There are a few things that are not clear to me. Can you setup a mail server without mysql to keep the aliases, users and virtual domains? Most of the guides I found on the internet use mysql to store data.... I need to know this, because I am thinking of remaining to the good old sendmail. :)

---

### Post by admlv on 2006-01-04
of course it's posible. try a litle deeper google research. some time ago i had postfix setup with aliases and multiplay domains without mysql. but in general i beter like config with mysql.

---

### Post by ejms07 on 2006-01-05
If you want, you can try [http://www.syscp.de]("http://www.syscp.de"), it works with Postfix, Courier, Bind, Mysql, etc.  You just need to add their deb repository to your sources.list and all ubuntu reps. to install it through synaptics. It has a nice web-based control panel to configure the server, domains , and users.

---

### Post by Soleil-Raid on 2006-01-05
[QUOTE=admlv]of course it's posible. try a litle deeper google research. some time ago i had postfix setup with aliases and multiplay domains without mysql. but in general i beter like config with mysql.[/QUOTE]

If you don't want to use text files for handling virtual domains, and want to be able to do dynamic updates of the domains and users, you'd be much better of to use LDAP rather than MySQL for handling users and accounts. This is the sort of thing it's built for.

---

