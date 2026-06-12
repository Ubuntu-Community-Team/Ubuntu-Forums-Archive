---
title: "How do I make exim on my server only relay mail from my home IP?"
date: 2010-09-09
forum: Security
---

### Post by ayqazi on 2010-09-09
Hi,

I have set up a server to act as a mail server for my domain.  It is running dovecot to allow me IMAP access to my Maildir, and exim to receive and relay mail for me.

I want to be able to send mail through it, but when the connection is either localhost or my home IP.

I'm running the latest version of lucid.

I have not modified any config files from their defaults.

So I followed these steps:

1. sudo dpkg-reconfigure exim4-config

2. I select the following options:

- General type of mail configuration: internet site; mail is sent and received directly using SMTP
- System mail name: qadicorp.com
- IP-addresses to listen on for incoming SMTP connections: <blank>
- Other destinations for which mail is accepted: qadicorp.com
- Domains to relay mail for: *
- Machines to relay mail for: <my home IP>/32
- Dial-on-Demand? No
- Delivery method for local mail: Maildir
- Split configuration into small files?: No

Yet when I test using [http://www.spamhelp.org/shopenrelay/shopenrelaytest.php](http://www.spamhelp.org/shopenrelay/shopenrelaytest.php) I'm open!  And recently I had to clear my exim mail queue because a botnet had found me and had relayed tons of mail through me!

So I want to be able to relay from localhost and <my home IP>, but not from anyone else...... how can I do this?

Any help would be appreciated.  Thanks

Edit: I'm mentioning the term 'open relay' here so that if anyone searches for what I did (close exim open relay), they find this post.

---

### Post by CharlesA on 2010-09-09
I've got mine set to relay mail, and it only listens on localhost. I didn't need to open port 25 in my firewall. Is that port open for you?

You could try closing it, since all outbound mail should pass thru it fine.

---

### Post by ayqazi on 2010-09-09
I need mine to listen on all interfaces, since exim is running on a server and I am connecting from home.  Hence I need exim to be the one that stops any IP other than mine from not being able to relay.

---

### Post by BkkBonanza on 2010-09-09
It should only relay mail when you've authenticated and when the from address is known as a valid user in a valid domain. Most mail packages try to make it hard to mis-configure that aspect so I'm kinda surprised you did it. However, I don't use exim and can't tell you the right options to set.

The IP address isn't usually the limiting factor because users often want to check and send mail from various places. However, you could add some rules to limit IP exposure.

Nowadays, ideally you would setup SSL/TLS mail anyway as who wants their mail being read all over the net.

Edit: Ummm, just looked at your post again. See the option where it says "Domains to relay mail for" - that MUST be set to indicate only YOUR domains. That is one factor that it uses to close the relay. It only relays when the sender is a valid user in YOUR domain.

ALSO, usually you want to add an [SPF record]("http://www.openspf.org/") to your DNS records as well so that other sites can check and verify which IP is a valid mail relay.

---

### Post by ayqazi on 2010-09-10
> **BkkBonaza said:**
> Edit: Ummm, just looked at your post again. See the option where it says "Domains to relay mail for" - that MUST be set to indicate only YOUR domains. That is one factor that it uses to close the relay. It only relays when the sender is a valid user in YOUR domain.

Ahh..... I thought that option meant 'only relay when the TARGET domain is one of these', hence the '*'.  OK going to look at it again - thanks.

And my SPF record is already set, but thanks anyway for that too.

Edit: I don't get it....... The description to "Domains to relay mail for" says "do not list local domains here"... and yet, having set my local domain for which I receive email (qadicorp.com), AND set "Machines to relay mail for:" to my IP address, I now have the required behaviour!  Thanks!

I must say however, that the 'Machines to relay mail for:' not having an effect until I set the 'domains to relay mail for' is very misleading... I didn't know the machines to relay for option would effectively be overridden by the domains to relay mail for option.  Again, many thanks.

---

### Post by BkkBonanza on 2010-09-10
They probably mean "local domains" literally as for the local machine, localhost and names on your LAN (being local). Your domain name is recognized in a public name space.

Cheers :)

---

