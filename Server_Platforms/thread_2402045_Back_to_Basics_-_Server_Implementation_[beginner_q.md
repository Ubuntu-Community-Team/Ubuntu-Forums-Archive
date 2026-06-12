---
title: "Back to Basics - Server Implementation [beginner questions]"
date: 2018-09-25
forum: Server Platforms
---

### Post by mrsixty7 on 2018-09-25
Hey guys. So, after going half-ar$ed at this for a couple of weeks, now, it's time to rewind and start to get to grips with my whole server project.

Ultimately, I am teaching myself server build, config, admin with Ubuntu Server 18.04. As a starting point I have a Lenovo T440 laptop as my hardware and it is hooked up to my home network.

Step 1...
...is to build a web server that will allow me to also continue with my PHP/mySQL development. Unless I have everything completely ar$e ended, I install Ubuntu Server, install the Apache package, install the PHP package, install the mySQL package. I think I am pretty much capable of doing this from the command line.
What I then want is a way to administer the server, in particular I like to manage mySQL through a GUI of some description; [COLOR=#800000]this I am used to doing with phpMyadmin but I believe that Webmin might be a preferred alternative[/COLOR]?

From that point, I can then start writing my php applications, which I may want to access from the WAN as well as LAN, which [COLOR=#800000]I imagine I can do with some simple port forwarding (8080) on my home modem/router (I have fixed IP)?[/COLOR]

What I would like to do is be able to build and run PHP applications that might send email notifications from my network. [COLOR=#800000]Is there a specific Ubuntu mail server package that I will need to install to be able to do this, or can I simply send using the mail(); function in PHP?[/COLOR]

Soooooo.... In my simple mind, that's how it looks as a starter for 10. Am I missing something? Have I got it horribly wrong? I try to simplify things as much as possible.

Appreciate for your input & recommendations. Be gentle, I'm new to it all (just as you were once).

---

### Post by TheFu on 2018-09-25
I don't know of any "preferred GUI" to manage mysql.  Actually, webmin is an anti-pattern and phpwebadmin is too.  Both of those systems are under continuous attacks on my public IPs - constant, continuous, attacks.  If you do end up using them, please, please, please, only allow localhost access and use an SSH proxy to get to the sites. NEVER allow access to the entire internet.  Unfortunately, the people able to securely setup access to these web-tools usually don't need it. We use shell to manage our systems.

People stopped using mysql years ago.  MariaDB has been preferred the last few years if you can't use PostgreSQL instead.  MariaDB is from the original makers of MySQL who left post Oracle.  Kinda like how OpenOffice split from Oracle into LibreOffice.

Generally, to send email from any Unix system, you need an MTA - Mail Transfer Agent.  Normally, this would be **postfix** on Ubuntu, but there are other choices.  All of them fulfill the "MTA" dependency requirement.  Sending email is a non-trivial thing if you want to use your own domain in the "from" address.  This is due to all the anti-spam addons that we all run these days.  If you want to use some other email account, say gmail or your ISP's mail server, then you can tell postfix to make an authenticated connection and send using those accounts.   There are simpler send-only MTA implementations as well.

If you allow inbound email, things get harder. That is really a whole new set of questions to be asks in a new thread. Whatever you do, never allow your IP to be considered an "open relay". The effort needed to get removed from that list or the spammers lists are more than many people will be able to apply. Don't let your system become one of the 2+M email systems in current use to spam the world.

I don't know anything about php, except that it is hacked more often than **any other** language used on the web - by far.  Be certain that you look up and follow the OWASP Php Top 10 security lists. [https://www.owasp.org/index.php/OWASP_Top_Ten_Cheat_Sheet](https://www.owasp.org/index.php/OWASP_Top_Ten_Cheat_Sheet)

If you want people to access your system(s) using names, not the IP, you'll need some other things. Keep each part separate, regardless of how easy buying them all at 1 place is.  That is a terrible, terrible, idea, unless the domain is to be thrown away.  Then it doesn't matter.  If you want to have it for decades, keep the registrar separate from the DNS. And keep the hosting separate from both of those, always.  It is best not to have your domain held hostage over something stupid.  Just ask Zoho.  [https://www.theregister.co.uk/2018/09/24/zoho_domain_snafu/](https://www.theregister.co.uk/2018/09/24/zoho_domain_snafu/) a company with 40M customers all really unhappy for over a day.  GoDaddy has done worse things to some of their customers.  Keep things separate.

---

### Post by mastablasta on 2018-09-26
> **mrsixty7 said:**
> 

What I would like to do is be able to build and run PHP applications that might send email notifications from my network. [COLOR=#800000]Is there a specific Ubuntu mail server package that I will need to install to be able to do this, or can I simply send using the mail(); function in PHP?[/COLOR]



sendmail? plus you will need some sort of mail server.

also for that type of development it is maybe easier to use virtualization (e.g. virtualbox).

---

### Post by SeijiSensei on 2018-09-26
To send mail, you first need to determine if your ISP allows outbound connections to the SMTP port (25) on remote machines.  Many residential providers block such connections to thwart spambots on their users' Windows machines.

To test this, run the following command:

```
telnet gmail-smtp-in.l.google.com 25
```

If you can connect, you'll see a response from the server like this:

```

Connected to gmail-smtp-in.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP z31-v6si5390453pgl.123 - gsmtp

```

If you can't connect, you won't be able to send mail from this machine directly to remote locations.  Some ISPs allow you to relay mail through one of their servers.  You'd need to talk with your ISP about this.

---

