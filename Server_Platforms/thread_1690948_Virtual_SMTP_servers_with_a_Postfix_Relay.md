---
title: "Virtual SMTP servers with a Postfix Relay"
date: 2011-02-19
forum: Server Platforms
---

### Post by narcisgarcia on 2011-02-19
I'm trying to use different MTA servers (one for each domain) on the same public IP and port (25).
Here I attach a graphic of my idea, to have a Postfix server that receives all incoming mail from internet, and relays to different local servers.
[attach]183884[/attach]

How can be configured the "Relayer MTA" ?

---

### Post by Philio on 2011-02-19
Essentially you want several mail servers on the same WAN IP address but so that mail for different domains is routed to different internal network IP addresses?

Sounds like you need to use an SMTP proxy.

---

### Post by elico on 2011-02-19
postfix can do the trick.
you need to just select the correct relay servers.

sample on this site:
[http://beginlinux.com/index.php/server_training/mail-server/118-mail-server/1044-postfix-mail-gateway](http://beginlinux.com/index.php/server_training/mail-server/118-mail-server/1044-postfix-mail-gateway)

also you can try to look on the proxmox mail gateway settings files.

---

### Post by SeijiSensei on 2011-02-19
I know that Postfix is the approved Ubuntu MTA, but I'll just note that sendmail's [mailertable]("http://www.sendmail.org/m4/mailertables.html") feature provides exactly this sort of ability.

---

### Post by narcisgarcia on 2011-02-19
I tried with proxsmtp ([http://thewalter.net/stef/software/proxsmtp/](http://thewalter.net/stef/software/proxsmtp/)) but didn't worked (maybe I didn't configure it properly).

I've seen the same feature as mailertable in Postfix (transport_maps?), but I'm trying to Postfix resolves the destination host with DNS, not with a static table.
By this way, my local DNS can be useful as a central hosts table for different services.

---

### Post by SeijiSensei on 2011-02-19
You could use MX records if you run a private nameserver for the domains to which you are delivering mail.  Then, on your local nameserver, the MX for "example.com" would point to one internal mail server, and the MX for "domain.name" would point to another internal server.  Externally, of course, the DNS for all these domains points to your public server as primary MX.

Sendmail's mailertable is designed precisely for situations where MX queries would provide the wrong information about routing a message.  If you handle the problem in DNS, then you don't need a database of mappings like mailertable provides.  On the other hand, it's a lot easier to create a few one-line entries in /etc/mail/mailertable than it is to create zone files and maintain an internal name server.

Still, if you already have a local nameserver, then just add the domains and corresponding MX records, and you should be all set.

---

### Post by narcisgarcia on 2011-02-19
As you could see in the graphic, I'm working on the DNS way.

Now I'm having some unknown problem because the Relayer MTA is rejecting connections from other internet MTAs (port 25), but it's accepting connections from MUAs (same port 25)

---

### Post by elico on 2011-02-19
Did you try:
> relay_domains = example.com, example.net

and also something you need to know.
you dont need to set the mx record as in the same domain your want it to work for.
let say you need example.net and example.com to be relayed using 80.80.80.80
you are making an A record in the name let say smtp.relayserver-domain.com
and in the mx records of the other domains you set the *smtp.relayserver-domain.com*
as your mx record.

and second thing you must do is to permit relaying using in the **main.cf **> 
relay_domains = example.com, example.net 
transport_maps = hash:/etc/postfix/transport

in this file add the records for each domain smtp server
**/etc/postfix/transport**
> example.com smtp:[smtp.example.com]
example.net smtp:[smtp.example.net]
and run the command
> postmap hash:/etc/postfix/transport


this way the server is bound to do a dns lookup only for the smtp.example.com and not to the mx record of the domain.




what is your permit rules in the main.cf file?

---

### Post by narcisgarcia on 2011-02-21
Thanks everybody who answered.
Additional problem is POP3 & IMAP protocols to do the same with MDA local servers.

I've found the interesting severse proxy "nginx", but I don't like the way to get the target server, because requires an Apache server to authenticate users with a PHP script and response the final server address.

I think the clean way is the DNS, with a reverse proxy that queries domain names got from RCPT TO in the case of smtp, and from username with full address (pop3, imap).
Someday somewho may develop a tool to do it, before DNS SRV entries are supported by Postfix & EXIM (now I don't see) and then we can map different port for each internal server and response also with specific TLS certificates.

---

