---
title: "Postfix authentication"
date: 2008-04-27
forum: Server Platforms
---

### Post by freebeer on 2008-04-27
I'm having trouble understanding and implementing authentication to my ISP's mail server.

I've set up Postfix, and I'm receiving emails just fine. I can't reply back to those test emails due to a 530 error requiring authentication.  I followed [this]("http://freelock.com/kb/Postfix_relayhost") without any errors/complaints from postfix but I'm still getting the error.

I had outgoing mail working at one point, when I was using 6.06 and sendmail.  (I set it up a while ago, understood it even less ;) but I did get it working.)  Now that I'm on 8.04, I figured that I might as well set it up with Postfix.  Postfix is a lot easier to set up, but then I ran into this little glitch that no amount of googling has helped.  :oops:

If it's of any additional help:  My ultimate goal is to have forms filled out on my website to send the form data to a specific email address outside of my domain.  That all worked under sendmail.

---

### Post by craylim on 2008-04-27
Does 'postmap -q mailrelay.example.com /etc/postfix/sasl_passwd' return your username and password?  it should, if the relayhost is done properly.

Also try adding a "smtp_sasl_security_options = noanonymous" in your main.cf

To test the comfig, do an 'echo "postfix works" | mail <your outside email>' from a command line to see if the email gets out.

> **freebeer said:**
> I'm having trouble understanding and implementing authentication to my ISP's mail server.

I've set up Postfix, and I'm receiving emails just fine. I can't reply back to those test emails due to a 530 error requiring authentication.  I followed [this]("http://freelock.com/kb/Postfix_dding relayhost") without any errors/complaints from postfix but I'm still getting the error.

I had outgoing mail working at one point, when I was using 6.06 and sendmail.  (I set it up a while ago, understood it even less ;) but I did get it working.)  Now that I'm on 8.04, I figured that I might as well set it up with Postfix.  Postfix is a lot easier to set up, but then I ran into this little glitch that no amount of googling has helped.  :oops:

If it's of any additional help:  My ultimate goal is to have forms filled out on my website to send the form data to a specific email address outside of my domain.  That all worked under sendmail.

---

### Post by craylim on 2008-04-27
just saw your link to the postfix config page

I normally for my postmap hash this way:

postmap hash:/etc/postfix/sasl_passwd

Just make sure the sasl_passwd.db file is created after your run the postmap....

> **freebeer said:**
> I'm having trouble understanding and implementing authentication to my ISP's mail server.

I've set up Postfix, and I'm receiving emails just fine. I can't reply back to those test emails due to a 530 error requiring authentication.  I followed [this]("http://freelock.com/kb/Postfix_relayhost") without any errors/complaints from postfix but I'm still getting the error.

I had outgoing mail working at one point, when I was using 6.06 and sendmail.  (I set it up a while ago, understood it even less ;) but I did get it working.)  Now that I'm on 8.04, I figured that I might as well set it up with Postfix.  Postfix is a lot easier to set up, but then I ran into this little glitch that no amount of googling has helped.  :oops:

If it's of any additional help:  My ultimate goal is to have forms filled out on my website to send the form data to a specific email address outside of my domain.  That all worked under sendmail.

---

### Post by freebeer on 2008-04-28
Thanks for the ideas!

I think my sasl_password.db is ok.  It's as current as the sasl_password file.  (I run postmap /etc/postfix/sasl_password after editing it.)  I do notice that you (and other docs) spelled it sasl_passwd (not "password").  As long as I'm consistent within mail.cf it shouldn't matter, should it?  This particular spelling was the default in 8.04 so I stuck with it.

> 
try adding a "smtp_sasl_security_options = noanonymous" in your main.cf


Gave that a try.  No difference.

> 
To test the comfig, do an 'echo "postfix works" | mail <your outside email>'
I gave that a try.  No joy.  The command was accepted without error, but in the user mailbox I get the mail returned with an authorization error (same as all my other tests).

> 
Does 'postmap -q mailrelay.example.com /etc/postfix/sasl_passwd' return your username and password

hmm... interesting test.  And yes, it returns my username and password. :-k

Again, thanks for your help.

---

### Post by craylim on 2008-04-28
the sasl_password file can be named anything you like.  It is, well, just a txt file....anyway, coming from an administrator background I have this habit of shortening "password" to "passwd".  sorry for the confusion caused.

Something interesting to try out.  I once had a problem with my relayhost also using postfix.  I finally solved the problem when i used the IP address of the SMTP server instead of the FQDN (even though pinging the FQDN resolves nicely to the IP address) in the main.cf and the sasl_password. From then, I have always used IPs when I setup a server.

You might wanna try using IP instead.  see if it helps.... remember to re-postmap the sasl_password file again.

---

### Post by MJN on 2008-04-28
> **craylim said:**
> Something interesting to try out.  I once had a problem with my relayhost also using postfix.  I finally solved the problem when i used the IP address of the SMTP server instead of the FQDN (even though pinging the FQDN resolves nicely to the IP address) in the main.cf and the sasl_password. From then, I have always used IPs when I setup a server.

The problem you had there could well have been down to not wrapping the server name in brackets, e.g. [smtp.yourisp.com], as if you don't do this then an MX query is made against the name as opposed to an A record query as most likely required.

Freebeer, post your config (**postconf -n**) so we can take a look.

Mathew

---

### Post by cdtech on 2008-04-28
Always use your logs:

```
sendmail -bv username@somewhere.com
```
This will tests to see if it WOULD send. You wont get an email.

Check the log file:
```
cat /var/log/mail.log | tail
```

---

### Post by freebeer on 2008-04-28
Thanks for your help, guys.

I'll give all those a go when I get home.  I'll report back the results.  *crosses fingers*

Re: the "password" vs "passwd" thingy... I thought as much, but just wanted to make sure... I've run into bizarre things like that in the past and I just wanted to check that off my list of potential miscues.

---

### Post by freebeer on 2008-04-28
> **MJN said:**
> 
Freebeer, post your config (**postconf -n**) so we can take a look.


here it be:

```

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
html_directory = /usr/share/doc/postfix/html
inet_interfaces = all
inet_protocols = all
mailbox_size_limit = 0
mydestination = linux1, localhost.localdomain, , localhost, freebeer.is-a-geek.org
mydomain = freebeer.is-a-geek.org
myhostname = mail.freebeer.is-a-geek.org
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = /usr/share/doc/postfix
recipient_delimiter = +
relayhost = [smtp.broadband.rogers.com]
smtp_sasl_security_options = noanonymous
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_mynetworks permit_sasl_authenticated reject_unauth_destination permit_inet_interfaces
smtpd_sasl_auth_enable = yes
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes

```

I also played with the various configurations of relayhost with and without [] as well as my username.  (It's not clear if my ISP requires the full "name@isp.com" or just the "name".

Also the results of sendmail -bv [email]username@somewhere.com[/email] are:

```

myuser@linux1:/etc/postfix$ sendmail -bv username@somewhere.com
Mail Delivery Status Report will be mailed to <myuser>.
```

---

### Post by cdtech on 2008-04-28
Most ISP's block the outbound e-mail (Port 25), but I'm sure your aware of that. I use gmail smtp for my server outbound email. From the server I only receive warnings and log information. What are you going to use your server outbound email for, just curious.

---

### Post by freebeer on 2008-04-28
The outbound traffic is generated by a web-form.  People fill out the form and the data is emailed to a couple of addresses outside my network.

Yeah, a blocked port would result in a time out error, though, as opposed to a 530 error authentication required, right?

Also I had this working with sendmail a week ago, and I'm pretty sure I didn't have to use an alternate port.  Although I have tied a couple of other ports (465, I think?) when playing with this.

My ISP seems to farm out some of the mail processing to yahoo.com (some kind of cross-marketing/servicing agreement).  I send my mail to my ISP's smtp server, but the error coming back implies that it's from yahoo. (well, it references a page that is actually yahoo's page, to be precise.) My ISP's help pages aren't updated very often and so could be completely out of date.

Maybe I'll try another smtp server.  My company uses a web-host and email provider, so maybe I should try them.  I don't hold much chance for that, though - I gave it a shot once, but I may not have had postfix set up to the level that I have it now.  I've tried so many different configurations that it's all a blur right now.  :)

---

### Post by freebeer on 2008-04-28
update: trying the other server didn't help.  I get a time out error and I can't telnet to it.  I can telnet to the other server that I was using, however.  I don't don't if that's of any help in diagnosing the problem.

---

### Post by craylim on 2008-04-28
Is my eyes playing tricks or are you missing out the :

smtp_sasl_password_maps = hash:/etc/postfix/sasl_password

line....


> **freebeer said:**
> here it be:

```

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
html_directory = /usr/share/doc/postfix/html
inet_interfaces = all
inet_protocols = all
mailbox_size_limit = 0
mydestination = linux1, localhost.localdomain, , localhost, freebeer.is-a-geek.org
mydomain = freebeer.is-a-geek.org
myhostname = mail.freebeer.is-a-geek.org
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = /usr/share/doc/postfix
recipient_delimiter = +
relayhost = [smtp.broadband.rogers.com]
smtp_sasl_security_options = noanonymous
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_mynetworks permit_sasl_authenticated reject_unauth_destination permit_inet_interfaces
smtpd_sasl_auth_enable = yes
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes

```

I also played with the various configurations of relayhost with and without [] as well as my username.  (It's not clear if my ISP requires the full "name@isp.com" or just the "name".

Also the results of sendmail -bv [email]username@somewhere.com[/email] are:

```

myuser@linux1:/etc/postfix$ sendmail -bv username@somewhere.com
Mail Delivery Status Report will be mailed to <myuser>.
```

---

### Post by craylim on 2008-04-28
Thanks Mathew....will give the bracket thingy a try on my next server set up.

> **MJN said:**
> The problem you had there could well have been down to not wrapping the server name in brackets, e.g. [smtp.yourisp.com], as if you don't do this then an MX query is made against the name as opposed to an A record query as most likely required.

Freebeer, post your config (**postconf -n**) so we can take a look.

Mathew

---

### Post by MJN on 2008-04-29
> **craylim said:**
> Is my eyes playing tricks or are you missing out the :

smtp_sasl_password_maps = hash:/etc/postfix/sasl_password

line....

That's right, and SMTP authentication isn't enabled either (smtp_sasl_auth_enable = yes).

Mathew

---

### Post by freebeer on 2008-04-29
ahh.. fresh eyes are always helpful. :D

I had the smtp**d**_sasl versions of those directives running, but not the smtp_sasl ones. ](*,)

I'm giving it a shot now.  The test email seems to be stuck in the outgoing cue right now, but that might be due to another issue... my ISP has recently started delaying acceptance of emails coming from a different email address in an effort to cut down on spam.  When I read the notification it didn't seem to quite apply to me.  I guess I'll have to look at it again.

I'll report my findings.  Thanks again!

---

### Post by freebeer on 2008-04-29
> **cdtech said:**
> I use gmail smtp for my server outbound email. 

I wonder if I shouldn't just get a gmail account and use their servers?

---

### Post by freebeer on 2008-04-29
Here's a little background on my ISP's "email security enhancement" [http://www.rogershelp.com/yahoo/article.php?id=10H-F](http://www.rogershelp.com/yahoo/article.php?id=10H-F)

I'm thinking that it doesn't apply to me because I was getting an authentication error (530) and not 553.  Also, the second clause states that it must be from an email client and I'm using postfix.  Would you concur that I'm correct on this point?

I'm at work now, so I can't check to see if the latest attempt worked or not.  I'll report back when I check it.

---

### Post by MJN on 2008-04-29
Postfix *is* an e-mail client as far as the ISP's mail server is concerned. I think the guide makes specific mention of clients to differentiate it from using their webmail service.

Have you followed the instructions with regards to getting your desired From: addresses verified/confirmed?

Mathew

---

### Post by freebeer on 2008-04-29
> **MJN said:**
> Postfix *is* an e-mail client as far as the ISP's mail server is concerned. I think the guide makes specific mention of clients to differentiate it from using their webmail service.


Fair enough.  Thanks for the clarification.  

> 
Have you followed the instructions with regards to getting your desired From: addresses verified/confirmed?


Nope, not yet.  I was really hoping to avoid that.  I haven't mentioned it before, but I'd like to have the email go out with the form-filler-outer's email address.  ie [email]fredsmith@mydomain.com[/email] fills out the form, supplying his email address.  The form processes the data, and sends an email out with the "From:" field as [email]fredsmith@mydomain.com[/email].  That way one of the recipients of the email can use an autoresponder at their end to confirm directly back to the fredsmith.  

(Background: There's a game called Allegiance that has a steep learning curve.  The Allegiance community runs a series of "classes" to educate the newbie in how to play the game.  This greatly helps the learning curve and increases the game's retention rate.  Anyway, the form, which I'm hosting, is an application form to these classes.  They fill out the form, I email it off to the folks who administer the course.  They get the application and an autoresponder email is sent out to the applicant confirming the application was recieved and some additional information about start dates, etc.)

If I send out the email with the "From:" field as me, then that breaks the autoresponder (I'd get the confirmations, not the applicant.)

---

### Post by MJN on 2008-04-29
I don't think you'll be able to that with your provider.

You'll have to either find another provider/server or restrict outgoing mail to verified From: addresses.

Mathew

---

### Post by freebeer on 2008-04-29
Results of previous test:

After adding the smtp_sasl directive, the test emails just sit in the outgoing queue.  No error messages, no 530 error like before (a bit of progress :D) but no error 553 suggested by the link.  But I'm getting a new error now in my log file.  I'll go have a look at that and see what I can figure out.

I've set up a gmail account.  I'll have to dig up their addy and give that a try, too.

---

### Post by freebeer on 2008-04-29
Well, I figured out what the new error was... a typo in the main.cf file.  :oops:  Got that corrected.

I did the verify thing with my isp but that doesn't seem to be working right.  Maybe it needs a bit of time to kick in.  (Was reading on another forum about mail issues with this ISP and there are plenty, it seems.)  

I've got some more digging to do now.  Thanks again for all your help and acting as a sounding/sanity board. It's appreciated!  [IMG]http://www.freebeer.is-a-geek.org/graphics/thumbsup.gif[/IMG]

---

### Post by einstein on 2008-04-29
I had postfix working with smtp.broadband.rogers.com - then Rogers broke it by requiring outgoing e-mails to be from my rogers e-mail address - same kind of f---up as with gmail, except that gmail just rewrites the From header and sends the message along.

By the way folks, it will take a long time to convince me that this kind of hooliganism is a means to limiting spam on an authenticated smtp connection (unless some fool is running an open relay... in which case he should be disconnected permanently).

Regards,
   Dennis

Hey, just tried playing around with Postfix and Rogers and it works once again.  Okay, I take it all back.

freebeer, if you are trying to use smtp.broadband.rogers.com as your relay, let me know and I can send you my postfix config.  It's uglier than sin and there is probably stuff in there that doesn't need to be but, it this moment, it works.

Dennis

Edit (2008-05-07) - Nope, I should have stuck to my guns.  Rogers has indeed broken their smtp relay service for authenticated users.  They now require From address authentication too although it seems hit and miss.  I have to keep my Rogers account for portable internet on the road but I am dumping Sympatico in favour of a local ISP - I can go holler at them over the counter if necessary (although I have never found it necessary in nearly five years of using their services) and they don't block port 25.  If you can authenticate as a valid user on their system, you're good to go.

---

### Post by freebeer on 2008-04-29
> **einstein said:**
> 
freebeer, if you are trying to use smtp.broadband.rogers.com as your relay, let me know and I can send you my postfix config.  It's uglier than sin and there is probably stuff in there that doesn't need to be but, it this moment, it works.


Sure!  That'd be great!  I'd learn something from it at any rate.  (And that's part of the whole reason why I'm doing this.)  ;)

...and yes, I'm trying to go through smtp.broadband.rogers.com

---

### Post by Zidaps on 2011-11-07
Hi folks...

I've been having similar issues.. here is the thread I had opened.

[http://ubuntuforums.org/showthread.php?t=1850727]("http://ubuntuforums.org/showthread.php?t=1850727")

Really happy to have found this post, can you please post your config file or send it to me. I think it may help me solve my issues.

Thanks.

---

### Post by einstein on 2011-11-07
Sorry Zidaps.  I have not used the GMail config in ages (and, unfortunately do not have a copy) - I finally searched about for an ISP that doesn't mess with port 25 and went that route.

Best regards,
   Dennis

---

### Post by Zidaps on 2011-11-07
Hi Einstein, 

No worries.. I will keep on searching.. If you have the time can you please take a look at my post and my config that I posted and see if you can identify any potential errors I should check on.. I don't want to hijack this post so here is that URL again:

[http://ubuntuforums.org/showthread.php?t=1850727]("http://ubuntuforums.org/showthread.php?t=1850727")

Thanks

---

