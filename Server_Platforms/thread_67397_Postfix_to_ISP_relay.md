---
title: "Postfix to ISP relay"
date: 2005-09-20
forum: Server Platforms
---

### Post by nocturn on 2005-09-20
How can I configure Postfix to only relay outbound mail to my ISP?  It has to masquerade as an existing domain do work (I have my own).

I have tried with relayhost and myorigin, but that just sends everyting outbound.

---

### Post by kivu on 2005-09-20
Take a look at: [http://www.postfix.org/SASL_README.html#client_sasl](http://www.postfix.org/SASL_README.html#client_sasl)

Don't forget to sudo postmap /etc/postfix/sasl_passwd 
and sudo postfix reload. Although sasl is named you don't need to install it yourself for this.

---

### Post by LordHunter317 on 2005-09-20
You use mydestination to set what postfix should recieve for.  That's probably your only problem.

---

### Post by nocturn on 2005-09-21
Yes, mydestination is set to localhost.localdomain, localhost.localdomain, localhost and my local DNS domain.

What should I use instead?

---

### Post by LordHunter317 on 2005-09-21
Posting your whole main.cf would be eaiser, as that sounds right, but obviously, something is wrong.  /etc/hosts too.

---

### Post by pietro_spina on 2005-09-25
Here is my experience with using my ISP as a relay ... I use verizon, so you would have to replace "outgoing.verizon.net" with your ISP's outgoing mail server.

RE: Postfix smtp_auth

A helpful page from [SUSE](http://portal.suse.com/sdb/en/2002/12/rsimai_slox_smtp_auth.html)  It worked on my ClarkConnect box.

Make the following entries in /etc/postfix/main.cf:
```
    smtp_sasl_auth_enable = yes
    smtp_sasl_security_options = noanonymous
    smtp_sasl_password_maps = hash:/etc/postfix/saslpasswd
```
Create the file /etc/postfix/saslpasswd with the following content:
```
    outgoing.verizon.net     YOURusername:YOURpassword
```
Generate the new map and reload the configuration:
```
    postmap /etc/postfix/saslpasswd
    postfix reload
```
I had to add this part also….(from the potential problems area)
```
    smtp_always_send_ehlo = yes
```
And I set the relay to outgoing.verizon.net

And oh, I'm not sure why, but I've seen people be asked to not post their main.cf but to instead post the output of
```
    postconf -n
```

---

### Post by nocturn on 2005-09-27
[QUOTE=LordHunter317]Posting your whole main.cf would be eaiser, as that sounds right, but obviously, something is wrong.  /etc/hosts too.[/QUOTE]

This is my main.cf file:
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = mail.home.vsb
mydomain = home.vsb
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost.localdomain, localhost.localdomain, localhost, home.vsb
relayhost =
mynetworks = 127.0.0.0/8,192.168.0.0/8
mailbox_size_limit = 0
#mailbox_transport = cyrus
mailbox_transport = lmtp:unix:/var/run/cyrus/socket/lmtp
recipient_delimiter = +
#inet_interfaces = loopback-only

# Pandora relay
# relayhost = mail-out.pandora.be

```

relayhost is uncommented when I tried, but I turned it off again.

This is my host file:

```

127.0.0.1       nocturnus       nocturnus.home.vsb      localhost.localdomain   localhost

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by pietro_spina on 2005-09-27
postconf -n 
will output all the non-default settings in your postfix configuration (it really is pretty handy for situations like this...)

In your main.cf I don't see a way for your smtp to authorize with the relay. My previous post outlines one way. I doubt your ISP will allow you to use that relay without auth.

In fact, here is a little test using telnet without auth....
```
Connecting to mail-out.pandora.be ...
<<< 220 hoboe2bl1.telenet-ops.be ESMTP Postfix
>>> HELO ####.####.#### (ip obfuscated)
<<< 250 hoboe2bl1.telenet-ops.be
>>> MAIL FROM:
<<< 250 Ok
>>> RCPT TO:
<<< 554 : Relay access denied

```> **nocturn]```

mydestination = localhost.localdomain, localhost.localdomain, localhost, home.vsb

```[/QUOTE]
I'm no expert, but I don't think you will recieve much mail without a FQDN in this list.   said:**
> 
relayhost is uncommented when I tried, but I turned it off again.

you will need to put your ISP's relay host in there and uncomment it. And comment out the empty one here...
> mydestination = localhost.localdomain, localhost.localdomain, localhost, home.vsb
#relayhost =
mynetworks = 127.0.0.0/8,192.168.0.0/8

-P

---

### Post by nocturn on 2005-09-29
> **pietro_spina]postconf -n 
will output all the non-default settings in your postfix configuration (it really is pretty handy for situations like this...)
In your main.cf I don't see a way for your smtp to authorize with the relay. My previous post outlines one way. I doubt your ISP will allow you to use that relay without auth.
In fact, here is a little test using telnet without auth....
[/quote]

Thanks for your answer Pietro

In fact, they do accept the relaying without auth if you are coming from an IP in their range and if the FROM address is a valid domain.  It actually works with relaying on, what is my problem is that everything gets relayed instead of non-local mail only.

[quote]
I'm no expert, but I don't think you will recieve much mail without a FQDN in this list.   said:**
> 

What do you mean by this?  My local domain is home.vsb (only internal).  So it should deliver everything for *@home.vsb locally.

[quote]
you will need to put your ISP's relay host in there and uncomment it. And comment out the empty one here...
-P

I did (when the config was active) and it works, but sends out everything.

---

### Post by pietro_spina on 2005-09-29
[QUOTE=nocturn]What do you mean by this?  My local domain is home.vsb (only internal).  So it should deliver everything for *@home.vsb locally.
[/QUOTE]
Oh, I just meant that if I tried to send mail to [email]nocturn@home.vsb[/email] I'm not going to have much success... home.vsb doesn't resolve. Internal will work fine of course.
[QUOTE=nocturn]
In fact, they do accept the relaying without auth if you are coming from an IP in their range and if the FROM address is a valid domain.  It actually works with relaying on, what is my problem is that everything gets relayed instead of non-local mail only.
[/QUOTE]
ahh, I was being a a bit stupid... but what it sounds like you might need are address classes...
[http://www.postfix.org/ADDRESS_CLASS_README.html]("http://www.postfix.org/ADDRESS_CLASS_README.html")
> The local  domain class.
The mail delivery transport is specified with the local_transport parameter. The default value is local:$myhostname for delivery with the local(8) delivery agent
The relay  domain class 
The mail delivery transport is specified with the relay_transport parameter. The default value is relay which is a clone of the smtp(8) delivery agent.
However, this is geting a bit beyond my skill level and I have no experience with these classes... I'm happy to throw ideas at you, but sorry I don't have an absolute "this is how you fix your problem" answer.
-p

---

### Post by dcostelloe on 2005-10-01
Using ISP:

Good sample of how to do it: [http://www.wormbytes.ca/articles/postfix-with-sympatico-relay](http://www.wormbytes.ca/articles/postfix-with-sympatico-relay)

---

### Post by nocturn on 2005-10-03
[QUOTE=dcostelloe]Using ISP:
Good sample of how to do it: [http://www.wormbytes.ca/articles/postfix-with-sympatico-relay](http://www.wormbytes.ca/articles/postfix-with-sympatico-relay)[/QUOTE]

Thank you, but this is what I did (without SASL because it is not needed at my ISP).  It results in all mail going through the relay while local mail should stay local.

---

### Post by pietro_spina on 2005-10-09
hey nocturn,
> myorigin = /etc/mailname

just taking another look at this thread and I noticed your myorigin setting... What is in that file? /etc/mailname

-p

---

### Post by nocturn on 2005-10-10
[QUOTE=pietro_spina]hey nocturn,


just taking another look at this thread and I noticed your myorigin setting... What is in that file? /etc/mailname

-p[/QUOTE]

This file is quite common on Debian systems and set the origin of your outgoing mail.

Say you put example.com in there, all mail send from your users will get @example.com appended.

This was actually part of my problem, I had to override this with muttrc file.

---

