---
title: "postfix configuration help"
date: 2009-07-18
forum: Server Platforms
---

### Post by jwferk on 2009-07-18
Does someone have a simple set of instructions, or better yet, example postfix configuration files they would be willing to share?  The postfix configuration manual is a nightmare for me.

All I want to do is have Nagios.3 (with ndoutils, pnp, etc) forward alert notifications to me.  

I've install the latest version of postfix and mailx.

I use comcast as a cable service.  I want things to go to my gmail account.  

That would seem to be a simple task.  

Any help would be appreciated.

Thank you.
jwf

---

### Post by windependence on 2009-07-19
OK so you just need to set up for SMTP. You don't need to change much for that.

This is right from the manual but these are the only parameters you have to change to do what you want:

> **Postfix on a null client**

   A null client is a machine that can only send mail. It receives no mail from the network, and it does not deliver any mail locally. A null client typically uses POP, IMAP or NFS for mailbox access. 
   In this example we assume that the Internet domain name is "example.com" and that the machine is named "nullclient.example.com". As usual, the examples show only parameters that are not left at their default settings. 
  [INDENT] 1 /etc/postfix/[main.cf]("http://www.postfix.org/postconf.5.html"):
2     [myorigin]("http://www.postfix.org/postconf.5.html#myorigin") = $[mydomain]("http://www.postfix.org/postconf.5.html#mydomain")
3     [relayhost]("http://www.postfix.org/postconf.5.html#relayhost") = $[mydomain]("http://www.postfix.org/postconf.5.html#mydomain")
4     [inet_interfaces]("http://www.postfix.org/postconf.5.html#inet_interfaces") = loopback-only
5     [local_transport]("http://www.postfix.org/postconf.5.html#local_transport") = [error]("http://www.postfix.org/error.8.html"):local delivery is disabled
6 
7 /etc/postfix/[master.cf]("http://www.postfix.org/master.5.html"):
8     Comment out the local delivery agent entry
[/INDENT]   Translation: 
  
[LIST]
[*]  Line 2: Send mail as "user@example.com" (instead of "user@nullclient.example.com"), so that nothing ever has a reason to send mail to "user@nullclient.example.com". 
[*]  Line 3: Forward all mail to the mail server that is responsible for the "example.com" domain. This prevents mail from getting stuck on the null client if it is turned off while some remote destination is unreachable. 
[*]  Line 4: Do not accept mail from the network. 
[*]  Lines 5-8: Disable local mail delivery. All mail goes to the mail server as specified in line 3.  
[/LIST]


[http://www.postfix.org/STANDARD_CONFIGURATION_README.html#null_client](http://www.postfix.org/STANDARD_CONFIGURATION_README.html#null_client)

-Tim

---

### Post by ArchCast on 2009-07-19
This tutorial helped me set up Postfix with Gmail:  [http://behindmyscreen.newsvine.com/_news/2006/12/31/501615-configuringubuntu-postfix-and-gmail-in-101-easy-steps](http://behindmyscreen.newsvine.com/_news/2006/12/31/501615-configuringubuntu-postfix-and-gmail-in-101-easy-steps)

---

### Post by jwferk on 2009-07-19
Tim/ArchCast,

Many thanks to both of you for the help.  I really appreciate it.

Best regards,
jwf

---

### Post by tcarneal on 2010-01-30
I am having a difficult time setting up my postfix installation as a null client. It sends out to other domains fine but the locally hosted domain emails are never delivered.

I've followed the instructions several times to no avail:

1 /etc/postfix/[main.cf]("http://www.postfix.org/postconf.5.html"):
2     [myorigin]("http://www.postfix.org/postconf.5.html#myorigin") = $[mydomain]("http://www.postfix.org/postconf.5.html#mydomain")
3     [relayhost]("http://www.postfix.org/postconf.5.html#relayhost") = $[mydomain]("http://www.postfix.org/postconf.5.html#mydomain")
4     [inet_interfaces]("http://www.postfix.org/postconf.5.html#inet_interfaces") = loopback-only
5     [local_transport]("http://www.postfix.org/postconf.5.html#local_transport") = [error]("http://www.postfix.org/error.8.html"):local delivery is disabled
6 
7 /etc/postfix/[master.cf]("http://www.postfix.org/master.5.html"):
8     Comment out the local delivery agent entry

The relayhost entry appears to be where the problem occurs i can change everything else and mail continues to be delivered to non-local domains. Any help would be much appreciated.

---

### Post by lisati on 2010-01-30
> **tcarneal said:**
> I am having a difficult time setting up my postfix installation as a null client. It sends out to other domains fine but the locally hosted domain emails are never delivered.

I've followed the instructions several times to no avail:

1 /etc/postfix/[main.cf]("http://www.postfix.org/postconf.5.html"):
2     [myorigin]("http://www.postfix.org/postconf.5.html#myorigin") = $[mydomain]("http://www.postfix.org/postconf.5.html#mydomain")
3     [relayhost]("http://www.postfix.org/postconf.5.html#relayhost") = $[mydomain]("http://www.postfix.org/postconf.5.html#mydomain")
4     [inet_interfaces]("http://www.postfix.org/postconf.5.html#inet_interfaces") = loopback-only
5     [local_transport]("http://www.postfix.org/postconf.5.html#local_transport") = [error]("http://www.postfix.org/error.8.html"):local delivery is disabled
6 
7 /etc/postfix/[master.cf]("http://www.postfix.org/master.5.html"):
8     Comment out the local delivery agent entry

The relayhost entry appears to be where the problem occurs i can change everything else and mail continues to be delivered to non-local domains. Any help would be much appreciated.

I'm unclear if you've posted the contents of your main.cf file, or you are outlining the steps you've taken. 

If that's the contents of the file, I'd be worried! I'm a beginner to running a mail server, but that doesn't look right.

---

### Post by tcarneal on 2010-01-30
Yeah those are the instructions off of postfix. Here are the contents of my main.cf

--------------------------------------------------------------------------------
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

myhostname = slice100000
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $mydomain
mydestination = example.com, slice100000, localhost.localdomain, localhost
relayhost = $mydomain
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only
local_transport = error:local delivery is disabled

--------------------------------------------------------------------------------

I also have the local line commented out in my master.cf file

---

### Post by lisati on 2010-01-30
I'm nearing the edge of how much I can help, and I'm a bit baffled by the line:
> local_transport = error:local delivery is disabled
My "main.cf" doesn't have any line quite like that. 
Which "how to" have you been following?

---

### Post by tcarneal on 2010-01-30
I'm using the how-to for creating a null client on the postfix site:

[http://www.postfix.org/STANDARD_CONFIGURATION_README.html#null_client](http://www.postfix.org/STANDARD_CONFIGURATION_README.html#null_client)

I've seen this referenced all over but I just cannot seem to get it to work. I can send to other domains just fine. Just not the one hosted on this server.

---

### Post by lisati on 2010-01-30
> **tcarneal said:**
> I am having a difficult time setting up my postfix installation as a null client. It sends out to other domains fine but the locally hosted domain emails are never delivered.


> **tcarneal said:**
> I'm using the how-to for creating a null client on the postfix site:

[http://www.postfix.org/STANDARD_CONFIGURATION_README.html#null_client](http://www.postfix.org/STANDARD_CONFIGURATION_README.html#null_client)


I think I see a clue. In the "how to", I found:
> A null client is a machine that can only send mail. It receives no mail from the network, **and it does not deliver any mail locally**. A null client typically uses POP, IMAP or NFS for mailbox access. 

Have a look here: [https://help.ubuntu.com/9.04/serverguide/C/postfix.html](https://help.ubuntu.com/9.04/serverguide/C/postfix.html)

---

### Post by tcarneal on 2010-01-30
You rock! I ran :
**sudo dpkg-reconfigure postfix**

Filled in all the values and voila it works! Thanks so much.

---

