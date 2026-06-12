---
title: "A very simple mail server for forwarding only"
date: 2008-05-04
forum: Server Platforms
---

### Post by klaasvanschelven on 2008-05-04
Hi there,

I'd like to set up a very simple mail server.
My DNS parking / minimal account does not include mail forwarding, which is all I need. I'd like to just forward all my mail to [whatever]@mydomain.com to my gmail or whatever other account. All tutorials I've found so far go into deep detail and actually manage boxes etc.

(this is happening on a debian server - I've found the Ubuntu community very helpful though, and hope to be able to bridge the differences myself.)

Klaas

---

### Post by jimcooncat on 2008-05-04
I used to use fetchmail and getmail, packages that retrieve mail from a pop or imap server, then I'd forward the messages along. These programs came with a good amount of problems.

I'm now using retchmail, a badly-named program that does the job very simply, but only for pop servers. It's been working with no problems or further effort for a few months now.

Here's the command-line steps I took to forward a couple accounts for my coworkers after installing from synaptic or apt-get:

1. Configure retchmail:
```
nano .retchmail/retchmail.conf

[INDENT][POP Servers]
[email]boss@pop.maine.com[/email] = secretPassword2
[email]flunky@mail.midmaine.com[/email] = Super4SecretPasswd
[POP Targets]
[email]boss@pop.maine.com[/email] = [email]bigbossman@mycompany.com[/email]
[email]flunky@mail.midmaine.com[/email] = [email]superguy@yahoo.com[/email]
[/INDENT]
```

2. Set up a crontab (this fetches every five minutes):

```
crontab -e
[INDENT]# m h  dom mon dow   command
*/5 * * * * retchmail -qq -F
[/INDENT]
```

More info at:

[http://alumnit.ca/wiki/index.php?page=RetchMail](http://alumnit.ca/wiki/index.php?page=RetchMail)

---

### Post by klaasvanschelven on 2008-05-04
Do I understand correctly that these solutions presuppose a POP account? Because I don't have one... the entire point is that I don't care much for building & maintaining POP, I just want my info@whatever to point to an already existing address.

If I need to use POP, what would be the easiest way?

---

### Post by jimcooncat on 2008-05-07
Yes, I presupposed a POP server. Sorry for not understanding.

Simplest way to go about what you want is to look for a mail forwarding feature from whomever is supplying your DNS. Many do. 

If they don't have that feature, you have two options:

1. Switch to one who does. Zoneedit.com is one I use, and is free for a generous amount of usage. In order to use it, you have to set up your DNS information at their site, and change your domain registration to use Zoneedit.com's name servers.

2. Run your own mail server. This involves having an always-connected computer to use as your server. If your internet provider gives you an IP  address that changes, then you'll have to set up dynamic updates with your DNS provider (or switch to one that does, like zoneedit.com or dyndns.org). Then you set up MX records in your DNS to point to your mail server.

On your mail server, make sure you have Postfix installed, then you can put in your forwarding address in a .forward file in your home directory. You might also want to put in other addresses for yourself in the /etc/aliases file; this is great for common misspellings of your email address.

Running your own mail server can be a complicated process, but for your usage it's pretty simple. Using a good DNS service makes a big difference in how easy it is to set up.

---

### Post by leidola on 2008-05-07
On a normal Unix you can use the .forward file in the home directory of every user to forward mails to another mailbox. Please have a look at:

[http://acs.ucsd.edu/email/dotforward.shtml](http://acs.ucsd.edu/email/dotforward.shtml)

Just configure postfix or whatever as normal and use this forward files. The configuration "internet with smarthost" should be okay (--> dpkg-reconfigure postfix)

---

### Post by windependence on 2008-05-07
Two suggestions:

Transfer your domain to GoDaddy and get free forwarding (you won't lose what you paid for, they will credit you)

OR

Run a Postfix smtp server. 5 minute setup.

[http://my.opera.com/Contrid/blog/show.dml/478684](http://my.opera.com/Contrid/blog/show.dml/478684)

[http://howtoforge.com/perfect-server-ubuntu8.04-lts-p5](http://howtoforge.com/perfect-server-ubuntu8.04-lts-p5)


-Tim

---

### Post by HermanAB on 2008-05-07
You could also look at nullmailer.

---

### Post by sowobi@rclmail.com on 2009-03-16
I know this is a dated discussion, yet retchmail is still the same.
My question is as WHO does one run retchmail with this configuration file ?
Root is not a good idea, I believe, but what user (with what permissions) will have the ability to deliver the messages to these diffrent accounts ?

Thanks

---

