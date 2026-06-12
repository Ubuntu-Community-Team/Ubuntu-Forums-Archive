---
title: "Secondary mail server and a mail gateway/relay"
date: 2011-08-03
forum: Server Platforms
---

### Post by c0d3sl1ng3r on 2011-08-03
Our primary mail server is Exchange 2003 Standard on Windows Server 2003 Standard - don't shout at me; I inherited it already set up this way.

I have a couple of hardware identical redundant servers (HP ML350 boxes), all with very fast 2 or 4 disk arrays, multiple core CPUs and plenty of memory, and I am looking at two potential new additions to the infrastructure.

A secondary mail server is high on my list of priories. I've been well and truly bitten by Exchange in the past and given that this particular box has been running four years straight and that it's mail store is dangerously large, having a secondary mail server in place suddenly makes a lot of sense.

A new Exchange 2010 box is currently being set up, but the secondary mail server will remain in place even when the new Exchange server is brought online, so this won't be a wasted exercise....

I also want a gateway box in place to filter and relay mail to the primary server, or to the secondary server if the primary is unavailable.

Currently our outer perimeter is:

ISP supplied CISCO router

Draytek VigorPro 5510 UTM

Untangle running in bridged mode (primarily used for SPAM filtering, URL blacklisting, and very little else)

Exchange 2003 sits behind the Untangle box.

This is how I want to end up:

CISCO >> Draytek >> Ubuntu gateway >> Exchange/secondary mail server

I know I could replace/remove the Draytek but I want it to remain for several reasons, including lots of VPN dial-in users already configured and that it offers us an additional layer of email antivirus scanning before things hit the Exchange box. No point switching all of our remote workers over to new tunnels unnecessarily...

I have done some research and have started testing a pilot secondary mail server using Ubuntu/postfix

DNS is properly set up and MX records and reverse PTR records are all present and correct, and things are looking encouraging so far.

Before I go out over deep waters and start to flounder, has anyone who has done something like this got any obvious howlers I should be looking to avoid ?

Any pointers appreciated, and I will document my trials and share the results as and when time allows.

Thanks in advance.

---

### Post by WhiteHorse on 2011-08-04
Log into the Exhcange server as Administrator and run this in a browser:
[Exchange with Ubuntu]("http://www.ubuntu.com/download/ubuntu/windows-installer")

---

### Post by SeijiSensei on 2011-08-06
I recommend considering [MailScanner]("http://www.mailscanner.info/") for your relay box.  It's a very powerful virus and spam scanner that works with free tools like SpamAssassin and ClamAV and commercial virus scanning products as well.

It uses two instances of sendmail, one to receive messages, and the other to deliver them after scanning.  (It can also use Postfix, but I'm a lot more familiar with sendmail.)  Create a sendmail [mailertable]("http://www.sendmail.org/m4/mailertables.html") entry to forward all mail for your domain to Exchange like this:

```

sudo su
[Enter your password]
cd /etc/mail
echo 'example.com    relay:[ip.of.exch.svr]' >> mailertable
makemap -v hash mailertable < mailertable
exit

```

This will create a file called /etc/mail/mailertable.db that sendmail will consult before delivering messages.  Inbound messages addressed to your domain will be forwarded to the Exchange server for delivery.  Mail for other domains will be sent out over the Internet using DNS.

On the Exchange server, make the Linux box the "smart" or "relay" host so that all outbound traffic is sent to the Linux server for scanning and final delivery.

---

