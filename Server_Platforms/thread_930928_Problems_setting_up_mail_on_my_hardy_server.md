---
title: "Problems setting up mail on my hardy server"
date: 2008-09-26
forum: Server Platforms
---

### Post by inadaze on 2008-09-26
Hello,

I had followed the install instructions for the perfect hardy server

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

I had issues with the mail portion, but I left it because it was of least importance to me at the time of installation.  Now I have everything else done and would like to fix the mail portion of the server.

I get blocked after I set up postfix.  There is a test :

telnet localhost 25

and then type

ehlo localhost

it says I am suppose to get

250-STARTTLS

and

250-AUTH LOGIN PLAIN 

but I actually get

250-sandman.inadaze.com Hello localhost.localdomain [127.0.0.1], pleased to meet you
250 ENHANCEDSTATUSCODES

could anyone help me out?
 
thanks,
Jay

---

### Post by alastair on 2008-09-26
I guess you could start by posting your :

/etc/postfix/main.cf

file.

Cheers,

Alastair

---

### Post by jamesrfla on 2008-09-26
If you are a beginner you might want to try citadel since it is easier to use and configure.

---

### Post by inadaze on 2008-09-26
Yes I am a beginner, so I will check out Citadel.  Should I worry about the two softwares conflicting?  Is so could I have advice about uninstalling the current packages to assure no further issues?

Otherwise, this is the contents of my /etc/postfix/main.cf

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
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = sandman.inadaze.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = sandman.inadaze.com, localhost.inadaze.com, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

```

---

### Post by alastair on 2008-09-28
Nothing obviously wrong in the cf file. But you say you see the banner when telneting to port 25 :

250-sandman.inadaze.com Hello localhost.localdomain [127.0.0.1], pleased to meet you

This is odd because I don't think that's Postfix (as configured by you).

Your banner should be more like :

220 sandman.inadaze.com ESMTP Postfix (Ubuntu)

As per the cf file :

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)

So ...

I don't think you are talking to Postfix - or not the Postfix you think.

If you have 2 terminals, tail the mail log in one, and restart Postfix in the other, what is in the logs? i.e.

terminal #1

sudo tail -f /var/log/mail.log

terminal #2

sudo /etc/init.d/postfix restart


What is printed when you run the above in terminal #1?

You can also check what is listening on various ports on your PC via netstat e.g.

sudo netstat -lpt

Cheers,

Alastair

---

### Post by inadaze on 2008-09-28
When I try what you suggested I get :

```
Sep 28 11:50:05 sandman postfix/master[23524]: fatal: bind 0.0.0.0 port 25: Address already in use
```

So I looked at what ports are being listened too and, although I don't fully understand the output, I do see that "sendmail" is still listed there.  when I failed to get my mail server working I tried to install sendmail to get that working.  Maybe they conflict?  I thought I removed it.  when I try and stop / start sendmail now, it tells me:

```
 * Starting Mail Transport Agent (MTA) sendmail
No make, you'll have to rebuild your databases by hand :(
 * Not configured, not started.
   ...done.
```

In the list from netstat I have 2 instances of sendmail, 4 instances of couriertcpd (imaps,pop3s,pop3,imap2) and nothing listed for postfix.

does this mean anything to you?

---

### Post by alastair on 2008-09-28
I am surprised sendmail is installed. I'd just remove it i.e.

synaptic / aptitude

and remove sendmail. It appears to be what's on port 25 ...

Alastair

---

### Post by inadaze on 2008-09-28
It is already removed.  The problem is that the software is gone, but the configuration still remains (I suppose).  That is what is interfering.  I ran aptitude remove sendmail again just to make sure and it says nothing to install, update or remove.

That is why I am a little unsure about how to continue.  I don't know where to look for things to remove (config files or other software that might have been involved with sendmail).

Any suggestions about how to completely get rid of sendmail from my server?

---

### Post by HermanAB on 2008-09-28
When you install Postfix, it installs a dummy sendmail program for compatibility with old programs that require sendmail.  So, if you have postfix installed and you see a program called sendmail - don't worry about it - it is quite useful.

---

### Post by alastair on 2008-09-28
What does the netstat command say? Yes, postfix includes a "sendmail" compatibility command - but it is only a postfix wrapper, not really sendmail, and has no startup script (init.d).

netstat -plt

What does it print?

What does "which sendmail" print? I get :

/usr/sbin/sendmail

and if I see what package gives me that :

dpkg -S /usr/sbin/sendmail

I get :

postfix: /usr/sbin/sendmail

---

### Post by inadaze on 2008-09-28
Netstat prints out the following:

```
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost.localdom:6600 *:*                     LISTEN      14704/mpd       
tcp        0      0 *:mysql                 *:*                     LISTEN      18551/mysqld    
tcp        0      0 localhost.lo:submission *:*                     LISTEN      5258/sendmail: MTA:
tcp        0      0 *:www                   *:*                     LISTEN      12207/apache2   
tcp        0      0 *:81                    *:*                     LISTEN      12207/apache2   
tcp        0      0 sandman.local:domain    *:*                     LISTEN      4873/named      
tcp        0      0 localhost.locald:domain *:*                     LISTEN      4873/named      
tcp        0      0 localhost.localdom:smtp *:*                     LISTEN      5258/sendmail: MTA:
tcp        0      0 localhost.localdoma:953 *:*                     LISTEN      4873/named      
tcp        0      0 *:https                 *:*                     LISTEN      12207/apache2   
tcp6       0      0 [::]:imaps              [::]:*                  LISTEN      20013/couriertcpd
tcp6       0      0 [::]:pop3s              [::]:*                  LISTEN      19909/couriertcpd
tcp6       0      0 [::]:pop3               [::]:*                  LISTEN      19853/couriertcpd
tcp6       0      0 [::]:imap2              [::]:*                  LISTEN      19965/couriertcpd
tcp6       0      0 [::]:ftp                [::]:*                  LISTEN      5453/proftpd: (acce
tcp6       0      0 [::]:domain             [::]:*                  LISTEN      4873/named      
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      4895/sshd       
tcp6       0      0 ip6-localhost:953       [::]:*                  LISTEN      4873/named    
```

Which sendmail prints out the same as you : /usr/sbin/sendmail
And package gives me the same thing too :postfix: /usr/sbin/sendmail

would I be better off doing an aptitude remove postfix and starting again from scratch?

cheers,
Jay

---

### Post by alastair on 2008-09-29
Sorry - meant to followup from work, but forgot! I hope you are persevering - it is good to sort this out. I don't think the Postfix reinstall will help. It is remains of sendmail that are causing a problem.

I would try :

1) Stop sendmail :

sudo /etc/init.d/sendmail stop

2) Still running?

ps ax|grep sendmail

Look for the "pid" and kill any that match sendmail e.g.

kill <pid>
or
kill -9 <pid>

ps ax|grep sendmail

3) Any sendmail installed?

dpkg -l "*sendmail"*

If any say "i" for installed - remove and purge i.e.

sudo apt-get purge <sendmail package>

4) Check netstat :

netstat -lpt 

Check for sendmail or smtp (should not be any)

5) Start Postfix

/et/init.d/postfix start

and tail the log (/var/log/mail.log) for erors/information.

Cheers,

Alastair

---

### Post by inadaze on 2008-09-29
Thank you for your devotion!  It's nice to know that there are some helpful people out there for those of us who aspire to be server folk.:D

Sendmail was still sticking around.  I purged it and killed the running processes (even though I had already stopped and removed the software...).  Now when I run

netstat -lpt 

I get :

7539 pts/0    R+     0:00 grep sendmail

And the pid keeps changing.  If I repeat the netstat command the pid increments each print out(7539, 7540,7541....)  I can't kill it because everytime I go to use the pid it says that there is no process with that id.  Very strange.  I stopped postfix and tried but I had the same result.

I think I will just go with Citadel - looks exactly like what I want.  But I would really like to get rid of sendmail so that I won't have any problems with Citadels install.

Thanks
Jay

---

### Post by alastair on 2008-09-29
> **inadaze said:**
> Now when I run

netstat -lpt 

I get :

7539 pts/0    R+     0:00 grep sendmail

And the pid keeps changing.  If I repeat the netstat command the pid increments each print out(7539, 7540,7541....)

Wait! 

That's the reply from the "ps ax|grep sendmail" Ithink (not netstat).

That's just the "grep" for sendmail! i.e. it's seeing the search process mentioning the name. Looks like sendmail is gone!

Try starting postfix i.e.

sudo /etc/init.d/postfix start

and "tail -f" the mail.log ....

Anything?

Alastair

---

### Post by inadaze on 2008-09-29
That's it!!!
Great.  And just when I was about to give up.

Thank you!

---

### Post by alastair on 2008-09-30
Happy to help. Thanks for persevering - I Knew it was something silly.

Alastair

---

