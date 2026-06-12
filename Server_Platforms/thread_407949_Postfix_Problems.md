---
title: "Postfix Problems"
date: 2007-04-12
forum: Server Platforms
---

### Post by BitHosts on 2007-04-12
Hey all, thanks in advance for any help!

Im trying to set up a mail server and so far all thats happened is my brain has started to bleed.

The machine im using is on a VM LAMP install of 6.06, it has bridged networking - its own external static IP.

I followed this "How To" up until the end of page 5 where I ran the command:

```
telnet localhost 25
```

and all that happens here is:

```
root@sol:~# telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.

```

I was expecting to at least see:

```
220 server1.example.com ESMTP Postfix
```

but nothing happens, I even left it for 5 minutes waiting but literally nothing happens.

While trying to fix the issue ive seen a few other people with similar sorts of problems and they were all asked to post the contents of the /etc/postfix/main.cf, so heres mine:

```
root@sol:~# nano /etc/postfix/main.cf
  GNU nano 1.3.10                 File: /etc/postfix/main.cf

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.bithosts.co.uk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.bithosts.co.uk, localhost, localhost.localdomain
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-$
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over their quote."
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps$virtual_alias)domains $vir$
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings
```

As far as i can work out, ive followed the guide to the letter - with the exception of my system being 6.06 not 6.10 (i can never remember the names).  Im afraid im a little bit of a noob still, learning curve has been absolutely massive over the past few months but im certainly a little green around the edges still.

If anyone out there can help me I would be incredibly happy!

Felix

---

### Post by kooseefoo on 2007-04-13
Hmmm... seems to be working fine when I telnetted in...

Did you find the problem?

---

### Post by BitHosts on 2007-04-13
Im presuming youve tried telnetting to mail.bithosts.co.uk?

If so - thats because thats on my old server (ill be transferring DNS once the confi is complete), try:

sol.bithosts.co.uk

Have to say aswell - I feel very nervous about people logging in - is it safe/is there anything i should be doing to make thismore secure?

---

### Post by BitHosts on 2007-04-13
Hmm - ive just tried both and cant get it to respond to either host...

---

### Post by baastie on 2007-04-13
Hi,

Do you see a connect in your mail.info log ? If so, does that give you more details...

Cheers,

---

### Post by bmathis on 2007-04-13
I had the same problem when I first tried install Postfix and it turned out to be a DNS problem... when you install Postfix, one of the dependencies is resolvconf. Use nano, or your favority text editor, to edit **/etc/resolvconf/resolv.conf.d/base** and add the following, save, and exit the file

```
   search yourdomain.com
   nameserver xxx.xxx.xxx.xxx
   nameserver xxx.xxx.xxx.xxx
```

Use the following command to update resolv.conf 
```
sudo resolvconf -u
```

Now, just restart networking and test it out again.
```
sudo /etc/init.d/networking restart
```

I hope that helps you!

---

### Post by BitHosts on 2007-04-13
I would quite happily kiss you both....

No seriously guys I checked the log...why i didnt think of that I dont know.

I had made a spelling mistake - vitual instead of virtual...

and theres was nothing in the resolve.../base file.

Thankyou all - i can now continue to break something else...

:D

---

### Post by baastie on 2007-04-13
Njoy :D

Cheers,

---

### Post by bmathis on 2007-04-13
Glad i could help ya...!   :D

---

### Post by BitHosts on 2007-04-13
Im willing to accept that once again its 0205h and im once again sat at a terminal watching the green cursor blink...but:

Postfix seems to be my nemesis.  (Hopefully only for now)

Once id done the suggestions above (thankyou again) I finished off the last page of the tutorial, which basically consists of adding users.  This complete I change my DNS entries and wait a while for it to propagate.  This done I start my mail client and it refuses my login, i puzzle over this for ages wondering why - changing entries in databases, checking logs (see im learning ;) ) etc etc.  Read the error message closer and realise the error returned by the server is actually more detailed than i was giving it credit for:

"-ERR Maildir: No such file or directory"

Immediately i check the permissions for the mail users home directory - seems fine.  Again I check logs and cant see anything.  

Anybody know which file its referring to?

The mail users home directory is empty - so i would guess that its the actual mailbox files themselves, except i dont know where to find the missing files or how to make a file that fits the format and more importantly what ive missed out to make this problem in the first place.

Now its time to follow the white rabbit...

---

### Post by BitHosts on 2007-04-13
Weirdly enough - while trying to fix something else, it started working....

Now im going to work out how to lock down outgoing emails - currently not set up to validate...

---

