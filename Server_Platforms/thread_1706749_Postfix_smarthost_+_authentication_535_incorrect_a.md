---
title: "Postfix smarthost + authentication: 535 incorrect authentication data"
date: 2011-03-14
forum: Server Platforms
---

### Post by Demented ZA on 2011-03-14
On Ubuntu server 10.10, with a relay smtp server with authentication via postfix; I keep getting 535: Incorrect authentication data. I'm sure my username and password is correct.

Heres how I set up postfix:

I created a file called smarthosts.conf in my /etc/postfix/ directory that contains the following:
```
smtp.myisp.com username:password
```I ran the following after creation of the file:
```
sudo chown root:root /etc/postfix/
sudo chmod 600 /etc/postfix/smarthosts.conf
sudo postmap hash:/etc/postfix/smarthosts.conf

```My /etc/postfix/main.cf file:
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost
relayhost = smtp.myisp.com
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/smarthosts.conf
smtp_sasl_security_options =
mailbox_size_limit = 0
recipient_delimiter = +
home_mailbox = /Maildir/

```When I send an e-mail, it gets stuck in the mail que. Here's the output from my mail.log file:
```
[SIZE=1]SASL authentication failed; server smtp.myisp.com[*.*.*.*] said: 535 Incorrect authentication data[/SIZE]
```I'm sure my username/password combination is correct, but I get the feeling the settings related to security is wrong.

my server uses plain text authentication on port 25. I would like to use security like SSL , but this particular server is unsecured.

Any advice would be appreciated.

---

### Post by rubylaser on 2011-03-14
In the past when I've hashed for SASL, I've never done it the way you tried. I normally just call postmap on my file.
postmap /etc/postfix/smarthosts.conf, instead of adding hash: in front of it.  What do the contents of /etc/postfix/smarthosts.conf look like?
```
cat /etc/postfix/smarthosts.conf
```

---

### Post by Demented ZA on 2011-03-14
```
smtp.audca.co.za user@audca.co.za 12345
```

I edited the above, as is an actual user e-mail and password, along with its server.

I basically followed numerous guides like [this one]("http://systems.takizo.com/2010/03/26/configure-smarthost-smtp-authentication-on-postfix/").

How would you have done it? I tried it without the hash bit in front. Didn't seem to make a difference.

---

### Post by Demented ZA on 2011-03-14
If I try setting up Thunderbird with that exact same smtp, username and pass, I can send e-mails to my gmail and other domain e-mails without a problem. That is if I use port 25, unencrypted password.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=186056&stc=1&d=1300133725[/IMG]

---

### Post by Demented ZA on 2011-03-14
I have a hunch that my password is getting mangled from that file and is not sent to the server as I expect it to be sent, thus the invalid authentication data.

I just don't know how to debug, and what to change?

Btw, what is the actual message if I were to login to a server with the wrong username and password? Wouldn't it be a different error like invalid username/password?

---

### Post by rubylaser on 2011-03-14
The reason why I asked, is this is how a correctly hashed file looks...
```
[smtp.gmail.com]:587 me@gmail.com:password
```
The smtp part above should match your relayhost...
And I normally add transport_maps into my main.cf
```
transport_maps = hash:/etc/postfix/transport
```
This is what I have in mine
```
root@fileserver:~# cat /etc/postfix/transport
# This sends mail to Gmail
gmail.com smtp:[smtp.gmail.com]:587

```
Finally, your error is telling your auth info is bad, either user or password for the host you've specified.

---

### Post by Demented ZA on 2011-03-17
Thanks for your reply.

Your file looks way different than mine. Since the how-to I worked of wasn't focussed on Ubuntu, or any debian-based distribution, and I'm absolutely sure mu username+password is correct, I think my configfile is just not set up as postfix expects, and I'm sure the info that reaches the server is not what I would expect to see as my username and password.

I'm going change my information to the format of your file and see what that does, and then post back.

On a seperate note, what does transport_maps do? Googling it now...

---

### Post by Demented ZA on 2011-03-17
Hmmm, according to [Postfix.org]("http://www.postfix.org/postconf.5.html#transport_maps") tranpost maps are additional parameters to tell postfix what to do with certain addresses etc.

I could be wrong, but this isn't something I need, is it? Did you configure your own transport maps, or is it a generic configuration?

---

### Post by Demented ZA on 2011-03-17
Brilliant, it works!

Its just the syntax/formatting that was the problem. The moment I changed it to your layout, it worked!

This is what it looks like now:
```
$ cat /etc/postfix/smarthosts.conf
[smtp.audca.co.za]:25 user@audca.co.za:password
```Also, removing or prepending the "hash:" portion in postfix configuration doesn't seem to make a difference to functionality.

From what I gather on the internet, defining hash: in the configuration like
```
smtp_sasl_password_maps = hash:/etc/postfix/smarthosts.conf
```, tells postfix to hash the file before reading it, cuircumventing the need to do a
```
postmap /etc/postfix/smarthosts.conf
```This means you can edit the postfix file directly, and not have to worry about forgetting to issue postmap command.


Now I would like to telnet into my smtp server, see what capabilities it has, and try SSL instead of plain text.

---

### Post by rubylaser on 2011-03-17
Great, glad you got it sorted out.

---

### Post by sasa.tomic on 2012-10-25
Hi,  I made a small user-friendly script for a no-questions-asked  installation and configuration of postfix with Gmail.

The script configures postfix to relay mail to smtp.gmail.com (which will send your emails to the world).
Check out the [https://gist.github.com/3952294](https://gist.github.com/3952294)
and please tell me if it works for you (or not)

P.S. I checked the script on Ubuntu 12.04, but it should work on previous versions as well.
Also, you should consider purging all postfix configuration with
```

sudo apt-get purge postfix

```

---

