---
title: "Preventing SPAM with postfix"
date: 2013-10-18
forum: Server Platforms
---

### Post by Mic6 on 2013-10-18
Hi' there
Currently I have quite a lot fo spam being send from my server and can't quite figure out how to get rid of it.
There is only 3 mail accounts on the server in use which requires the STMP service, so are the anyway to tighten up the security so that it only allows these 3 emails to send outgoing emails?
We are talking about emails like
[email]info@domain1.com[/email]
[email]support@domain1.com[/email]
[email]name@domain2.com[/email]

From what I could read it might be possible with /etc/postfix/access somehow, but not quite sure how to implement it as I am no expert in Ubuntu.

---

### Post by SeijiSensei on 2013-10-18
> **Mic6 said:**
> Currently I have quite a lot fo spam being send from my server and can't quite figure out how to get rid of it.

Take the server offline until you resolve this problem.  The longer it continues to send spam, the more likely it is that your server will be added to a blacklist.  If that happens, you will find you cannot send mail to remote machines that pay attention to such blacklists.  I recommend you visit [http://mxtoolbox.com/blacklists.aspx](http://mxtoolbox.com/blacklists.aspx) and enter your server's IP address into the box.  You'll see whether you have already been placed on a blacklist.

The most likely problem is that your machine is an "open relay," a machine that accepts inbound messages from anywhere and sends them on to their final destinations.  Please read [this document](http://www.postfix.org/SMTPD_ACCESS_README.html) carefully and implement the solutions it describes.

One simple way to check whether you have fixed the problem is to simulate an SMTP session with your server.  Log into the server and use the command "telnet localhost 25" to connect to Postfix.  It will reply as follows:

```

$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 servername ESMTP Postfix (Ubuntu)

```

Now it is waiting for you to give it commands:
```

helo localhost
[server replies]
mail from: joe@somewhere.net
[server replies]
rcpt to: bill@google.com
[server replies]

```

If you get OK responses to all of these, your machine is still an open relay.

Now if your server happens to be a gateway router as well, and you have client workstations connecting through it, the problem may be that one of the workstations has been compromised and turned into a spambot.  To solve that problem, add two iptables rules to your firewall ruleset like this:

```

/sbin/iptables -A INPUT -p tcp -s your.internal.ip.network/mask -d your.servers.internal.ip -j ACCEPT
/sbin/iptables -A INPUT -p tcp -s your.internal.ip.network/mask --dport 25 -j REJECT

```

For instance, if the local network has computers in 192.168.1.0/24, and the mail server's internal IP address is 192.168.1.1, you would use these rules:

```

/sbin/iptables -A INPUT -p tcp -s 192.168.1.0/24 -d 192.168.1.1 --dport 25 -j ACCEPT
/sbin/iptables -A INPUT -p tcp -s 192.168.1.0/24 --dport 25 -j REJECT

```

The first rule lets internal machines send mail to your server; the second blocks any attempts by those machines to connect to SMTP servers on the public Internet.

---

### Post by Mic6 on 2013-10-18
Thank you very much for the reply. Much appriciated. I could telnet to port 25 and got these server responses to the commands
250 server01
250 2.1.0 Ok
250 2.1.5 Ok

I don't think it's gateway router or anything like that, it's just a standard dedicated server running a webshop and a few wordpress sites.
But since there are only 3 mail adresses in use, wouldnt it be possible to whitelist those 3 and block outgoing mails from all others?

---

### Post by SeijiSensei on 2013-10-18
It depends on whether the machine also accepts inbound mail.  If so, then you have to allow mail from random senders addressed to local mailboxes.  If you restrict senders to just those addresses, then remote correspondents will not be able to send you mail.

If the server is used to send out mail, say from a web application, then just make sure that the "restrict networks" parameter only allows 127.0.0.0/8, the localhost interface.  That way remote servers cannot push mail through your machine.

If you need to accept inbound mail from remote machines, you need to read the documentation I linked to carefully.

If you just want to allow those three addresses to send mail, use a "sender_access" database.   Read this part of the Postfix documentation: [http://www.postfix.org/postconf.5.html#smtpd_sender_restrictions](http://www.postfix.org/postconf.5.html#smtpd_sender_restrictions).  I use "PCRE" tables where the key is a [Perl-compatible regular expression]("http://www.boost.org/doc/libs/1_54_0/libs/regex/doc/html/boost_regex/syntax/perl_syntax.html").  In your case, sender_access would be something like:

```

/info\@domain1\.com/        OK
/support\@domain1\.com/     OK
/name\@domain2\.com/        OK
/.*\@.*/                    REJECT

```

(I"m not sure you need to "escape" the "@" with a backslash.  I know I have to do this with PCRE's in SpamAssassin, but I don't have any Postfix rules that include that character.  If Postfix complains, remove the "\" before the "@".  You could also use a [hash table]("http://www.postfix.org/postmap.1.html") instead.)

In main.cf you would add the directive:
```
smtpd_sender_restrictions = check_sender_access pcre:/etc/postfix/sender_access
```

---

### Post by Mic6 on 2013-10-19
Thanks, nice to see this written in a way common people can understand too :)

I think I am doing something wrong or missing something. When I try to send from my own computer using the [email]info@mydomain.com[/email] email (which normally works) I get the Server responded 451 error. Even with an empty sender_access file, or with just [email]info@mydomain.com[/email] OK added in it.

Also tried running the postmap /etc/postfix/sender_access command (not sure if that is necessary)

If I comment out the line 
smtpd_sender_restrictions = check_sender_access pcre:/etc/postfix/sender_access in main.cf it works again, so seems to be something I am missing.

---

### Post by SeijiSensei on 2013-10-19
> Thanks, nice to see this written in a way common people can understand too


Thank *you!*  I taught at the university level for quite a few years which I think helps me write comprehensible instructions.

A bit of research shows that your problem is a result of how Ubuntu packages Postfix.  PCRE support is not included by default; you need to install the **postfix-pcre** package to add support for this type of map.  (I use CentOS, the free RedHat clone, on all my servers.  RH generally builds its packages to include pretty much everything while Ubuntu often distributes separate add-on packages for modules like postfix-pcre.)

If that doesn't work,  try using a hash map instead.  First, replace the contents of sender_access with:

```

info@domain1.com        OK
support@domain1.com     OK
name@domain2.com        OK
.                       REJECT

```

I think the last line should reject any address not in the list since it should match any "domain.name" string.  This method works in sendmail, but I haven't tried it with postfix.

Now create the hash database with "sudo postmap hash:sender_access".  In main.cf, replace the "pcre" entry with "hash" and restart Postfix.  Any better?

---

### Post by Mic6 on 2013-10-20
Thanks a bunch, worked perfectly. that part I would never have figured out by myself. 
Also changed the postfix port 25 to another port number, deleted the 400K mails from the mail queue.

---

