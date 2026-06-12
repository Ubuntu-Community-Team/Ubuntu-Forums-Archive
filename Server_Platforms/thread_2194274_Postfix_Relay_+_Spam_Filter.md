---
title: "Postfix Relay + Spam Filter"
date: 2013-12-17
forum: Server Platforms
---

### Post by doctorruckus on 2013-12-17
Hi

I'm looking to set up an Ubuntu 12.04 virtual machine I'm calling smtp01.mydomain.com - this will act as inbound SMTP relay to our existing Exchange server. Primarily this is to act as spam filter - the reason I'm doing this over using Exchange's spam filters is that I want to abstract functions from Exchange so it'll be easier to swap to something else in future.

What I want to achieve is all mail going from the internet to mydomain.com coming to this virtual machine - it'll then be checked against a whitelist of "known good sender" domains. Assuming it passes that whitelist, SpamAssassin, and maybe SpamCop/SpamHaus's blacklists, mail is then forwarded onto mail.mydomain.com which is our Exchange server.

What I've done so far - 
- Installed smtp01.mydomain.com with the latest version of Ubuntu 12.04
- Set up postfix as a satellite server, receiving for mydomain.com and forwarding to mail.mydomain.com
- Opened up postfix to receive mail on all interfaces, not just local

When I do this, I can't send mail through smtp01.mydomain.com - I get an error message of "550 5.1.1 <user@mydomain.com>: Recipient address rejected: User unknown in local recipient table". 

This is where I'm stuck - as I understand it, I have to set local_recipient_maps to equal either nothing so it passes through properly (but this is bad as it turns you into a backscatter monster), or to point to a manually-curated list of aliases. Is it possible to have it a map that's just *@mydomain.com? Exchange can deal with nonexistant addresses for now. Or is there a better solution?

---

### Post by lisati on 2013-12-17
Good call about trying to avoid becoming a backscatter monster. I'm wondering if postfix's [virtual domain hosting]("http://www.postfix.org/VIRTUAL_README.html") options include something that might be of help to you you here.

---

### Post by SeijiSensei on 2013-12-17
It sounds like Postfix is trying to deliver to local mailboxes rather than forwarding the mail to Exchange.  

Do you have a "relayhost" directive in /etc/postfix/main.cf that points to the Exchange server, either by name or as a bracketed IP address?  Something like this:

```
relayhost = exchange.example.com
```

or

```
relayhost = [10.10.10.10]
```

You shouldn't need any user accounts on this server; all the user management should be handled by Exchange.

I recommend you take a look at [MailScanner]("http://www.mailscanner.info/"), a terrific all-in-one mail scanning program that does virus and spam scanning of all messages.  We run it in front of an Exchange server at a client's site.  It invokes SpamAssassin and knows all about DNS-based services like Spamhaus.  We use sendmail rather than Postfix as the MTA, though, but MailScanner can work with either.

---

### Post by CharlesA on 2013-12-17
Huh. I've looked into creating a secondary MX server, but from what I've read about it, it requires setting relayhost and other stuff.
[http://www.cyberciti.biz/faq/postfix-backup-mx-server-anti-spam/](http://www.cyberciti.biz/faq/postfix-backup-mx-server-anti-spam/)

Dunno if that helps at all but I never actually got around to testing it.

---

### Post by SeijiSensei on 2013-12-17
We run a secondary MX for the server I described in the earlier posting.  It runs Postfix with some pretty stringent anti-spam rules.  My experience is that 99% or more of mail sent to secondaries is spam.  It includes a relayhost directive that points to the main mail server, the one running MailScanner.  

Here's its main.cf:

```

queue_directory = /var/spool/postfix
command_directory = /usr/sbin
daemon_directory = /usr/libexec/postfix
data_directory = /var/lib/postfix
mail_owner = postfix
myhostname = mail2.example.com
mydomain = example.com
myorigin = mail2.example.com
inet_interfaces = all
inet_protocols = all
mydestination = $myhostname, localhost.$mydomain, localhost
unknown_local_recipient_reject_code = 550
mynetworks = 10.100.0.0/16
relay_domains = $mydestination, $mydomain
relayhost = [10.100.1.6]
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
 
mail_spool_directory = /var/spool/mail
debug_peer_level = 2
debugger_command =
	 PATH=/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin
	 ddd $daemon_directory/$process_name $process_id & sleep 5
sendmail_path = /usr/sbin/sendmail.postfix
newaliases_path = /usr/bin/newaliases.postfix
mailq_path = /usr/bin/mailq.postfix
setgid_group = postdrop
html_directory = no
manpage_directory = /usr/share/man
sample_directory = /usr/share/doc/postfix-2.6.6/samples
readme_directory = /usr/share/doc/postfix-2.6.6/README_FILES

smtpd_client_restrictions = reject_unknown_client_hostname,
			    #reject_unknown_reverse_client_hostname,
			    check_sender_access pcre:/etc/postfix/sender_access,
			    sleep 3, reject_unauth_pipelining
smtpd_delay_reject = no
smtpd_sender_restrictions = reject_unknown_sender_domain,
			    check_sender_access pcre:/etc/postfix/sender_access
smtpd_helo_required = yes
smtpd_helo_restrictions =   check_helo_access pcre:/etc/postfix/helo_access

```

Most of this is pretty vanilla, with the exception of the relayhost directive and the various anti-spam items at the bottom of the file.  I use some access controls that rely on (Perl-compatible) regexes.  For instance, my /etc/postfix/sender_access file looks like this:

```

# no mail from outsiders claiming to be us
/\.example\.com$/	REJECT

# no two-letter country-code domains except us/ca
/\.us$/			OK
/\.ca$/			OK
/\.[a-z][a-z]$/		REJECT US senders only

# various blacklists
/\.hostnoc\.net$/       REJECT
/\.pawlitenews\.com$/   REJECT

```

---

### Post by doctorruckus on 2013-12-18
Thanks for the help guys - it looks a bit like it might be my inability to correctly RTFM that was the first problem. I had entered the relay host without square brackets.

That didn't fix everything (in fact, at first it didn't fix anything - I had to run dpkg-reconfigure to get the settings to take). But it did mean that relaying worked- for all email. Nothing was being blocked, and shoddy mail addresses were instead being blocked by Exchange rather than the VM. A bit more staring at the postfix docs found the remaining steps.

relay_domains = mydomain.com was set up during the configuration, but that alone isn't any use. The other setting I needed was "smtp_recipient_restrictions = reject_unauth_destination", which tells postfix to reject anything that's not in relay_domains.

reject_unauth_destination does also check in $mydestination, but I've commented out $mydestination to ensure that nothing gets stuck in this VM by accident. Is that an OK thing to do, or am I making a horrific mistake?

---

### Post by SeijiSensei on 2013-12-18
Looking at the configuration I'm using, I think that for a backup MX, relaydomains=$mydomain should be the correct entry.  Mail for, say, "root@localhost" ought to be delivered to the local root account not forwarded to another server.  I would leave $mydestination uncommented with the standard list of local addresses like $myhostname and localhost.$mydomain but omit it from the relaydomains item.

If you want to block spam, I suggest including at a minimum

```
smtpd_client_restrictions=sleep 3, reject_unauth_pipelining
```

This tells Postfix to wait three seconds before displaying its initial banner to the remote client.  Automated spam programs start spewing their garbage as soon as connection is made.  That triggers the "[reject_unauth_pipelining]("http://www.postfix.org/postconf.5.html#reject_unauth_pipelining")" item which drops the connection.  Well-behaved SMTP servers wait until the banner appears before starting an SMTP session.

---

### Post by SeijiSensei on 2013-12-18
> **SeijiSensei said:**
> Looking at the configuration I'm using, I think that for a backup MX, relaydomains=$mydomain should be the correct entry.

No, I'm wrong.  After re-reading the comments in main.cf, I think $mydestination needs to be in relaydomains as well as $mydomain.  Otherwise Postfix will reject mail sent to, e.g., [email]root@mail2.example.com[/email].

---

### Post by SeijiSensei on 2013-12-19
Looking at the logs on this backup MX shows that 

```
smtpd_client_restrictions = [reject_unknown_client_hostname]("http://www.postfix.org/postconf.5.html#reject_unknown_client_hostname")
```

is pulling most of the anti-spam weight.  It's up to you whether you accept mail from a machine whose DNS hostname does not match the PTR record for its IP address.  Here, for instance, is a representative SMTP sending server for gmail.com:

```

$ host 209.85.216.179
179.216.85.209.in-addr.arpa domain name pointer mail-qc0-f179.google.com.

$ host mail-qc0-f179.google.com
mail-qc0-f179.google.com has address 209.85.216.179

```

Both forward and reverse DNS resolution provide the same name<=>IP pairing.  Nowadays any knowledgeable mail administrator ensures that forward and reverse resolution match on mail servers.  Otherwise some locations on the Internet will refuse to accept mail from that machine.  I don't impose this requirement on the primary MX, but the backup gets so much junk that I do enforce it there.  (Besides if a legitimate SMTP server is rejected when connecting to the backup, it will try the primary again.)

---

### Post by CharlesA on 2013-12-19
+1. I have my mail server set up like that.

---

