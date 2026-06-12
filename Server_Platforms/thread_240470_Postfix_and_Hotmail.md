---
title: "Postfix and Hotmail"
date: 2006-08-20
forum: Server Platforms
---

### Post by tattoo7 on 2006-08-20
I have put together a postfix and dovecot pop3 email server. My confusion is i can get emails from hotmail great but unless i send an email to hotmail with a file attached or reply back to an email sent from hotmail it will never get there. Can anyone shed some light on what may be going on as this very confusing to me.
Thanks
:confused:

---

### Post by chrisfay on 2006-08-21
I'm assuming you are running your mail server on a dynamic IP like most. Hotmail blocks users who are listed in the RBL and run servers on dynamic IP's. This is not to say that just because you run your mailserver on a dynamic IP that you can't send mail to Hotmail. You have to check here:

[http://www.robtex.com/rbls.html](http://www.robtex.com/rbls.html)

If after you run the check using your IP and it comes up red stating:  Dynamic IP Address ranges (NOT a Dial Up list!) you are listed and will most likely be unable to send mail to Hotmail users. 

This is the roadblock I have come to in using my postfix mailserver as many of my contacts still use hotmail. If there is a workaround someone please post...

---

### Post by robert_pectol on 2006-08-21
Use your ISP's smarthost.  You can do this by using the, 'relayhost' directive in your postfix configuration.  Simply specify the IP of your ISP's SMTP server and postfix will then deliver all outbound mail via your ISP's SMTP server.

---

### Post by chrisfay on 2006-08-22
That doesn't do me any good... Comcast will only relay mail for comcast.net accounts. I can't add smtp.comcast.net and just expect them to send my mail. They would never allow that.

If I call them and ask to be able to relay, they'll know I'm running a mail server which, unfortunately, is against there TOS. 

I have found some other fee based services that relay mail using your domain through their mail servers. If anyone's interested:

[Dyndns]("http://www.dyndns.com/services/mailhop/outbound.html") 
[AuthSMTP]("http://www.authsmtp.com/") 
[SMTP.COM]("http://www.smtp.com/") 
[DNS Park]("http://www.dnspark.com/services/mailPassage.php") 
[Kryptonite Hosting]("http://www.spamblocked.com/modules/smallstore/product4.php")

---

### Post by chrisfay on 2006-08-22
Disregard my previous post!!

After an hour of talking to 3 different Comcast reps who said it was impossible and forbidden I finally figured out how to relay mail through their mail servers using postfix:

1. In /etc/postfix/main.cf add the lines:

```
relayhost = smtp.comcast.net
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options=
```

Optionally, also add the lines:

```
smtp_use_tls = yes
smtp_tls_CAfile = /etc/postfix/cert.pem
smtp_tls_session_cache_database = btree:/var/run/smtp_tls_session_cache
```

to enable SSL/TLS when sending outgoing mail. Note that the path info in the second command may be different depending on your system and where you have installed your certificates. The last line may be omitted, but should help reduce CPU cycles verifying the certificate chain when sending outgoing E-Mail. 

2. Create a file /etc/postfix/sasl_passwd with the contents:

  ```
smtp.comcast.net userid:password
```
where userid and password are your comcast.net username and password.

3. Next, change the ownership and permissions on the sasl_passwd file to protect it from unauthorized access.

  ```
sudo chown root:root /etc/postfix/sasl_passwd 
```
  ```
sudo chmod 600 /etc/postfix/sasl_passwd
```

4. Finally, create a database file from the contents of the sasl_passwd file:

  ```
postmap hash:/etc/postfix/sasl_passwd
```

I assume this would work with other ISP's that you have a username and password for email access.

Thanks robert_pectol for pointing me in the right direction...Too bad I just spent $20 at dnspark...guhhh

Here's a direct link to the howto on configuring the smtp auth:
[http://postfix.state-of-mind.de/patrick.koetter/smtpauth/smtp_auth_mailservers.html](http://postfix.state-of-mind.de/patrick.koetter/smtpauth/smtp_auth_mailservers.html)

---

### Post by MJN on 2006-08-22
I was about to say - Comcast may well not allow you to run your own mail server however that has nothing to do with whether you can relay outgoing mail via their mail servers. Even your mail *client* has a requirement to be able to do that.
 
Mathew

---

### Post by chrisfay on 2006-08-22
Comcast reps told me that mail relaying through their servers was only allowed using @comcast.net email addresses. They even said that any other domain would be blocked. 

I dug a bit more after talking to the reps and found how to relay mail from smtp server to another smtp server using smtp auth. Just so happens that Comcast 'does' allow relaying for alternate domains but they actively tell you otherwise. Strange....

---

### Post by MJN on 2006-08-22
Quite probably a misunderstanding on their part (by some and not others). I do hate it when the person you're talking to gives you any old answer even if they don't really know - I'd rather they admitted they didn't know and passed me onto someone else (or even suggest I call back to get someone else if need be).

Anyway, enough of my off-at-a-tangent ranting, good to hear you got it sorted.

Mathew

---

### Post by jrcproduct on 2006-08-22
I have had the same problem, but I have a static IP from a local dsl provider who are ok with me hosting a server. what should I look for and change.

---

### Post by MJN on 2006-08-23
Firstly, simply try **relayhost = [#.#.#.#] **(keep the square brackets and replace #.#.#.# with the name/address of your ISP's mail server).
 
Often (usually?) this is sufficient as they are authenticating you via your IP address.
 
Mathew

---

