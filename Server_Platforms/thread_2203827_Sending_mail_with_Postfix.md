---
title: "Sending mail with Postfix"
date: 2014-02-05
forum: Server Platforms
---

### Post by thnewguy on 2014-02-05
I recently set up an e-mail server using Postfix. Most of the initial install/configuration went well. I can receive e-mails at my address and retrieve them over IMAP using Dovecot. My problem is that I can only send e-mails to outside addresses (like [EMAIL="someone@gmail.com"]someone@gmail.com[/EMAIL]) if I am logged into the mail server locally. If I try to connect to the server remotely or via a e-mail client (Thunderbird in this case) the server tells me it cannot relay my e-mail.

As I understand it allowing all e-mails to be relayed through my server would be very bad and cause an open relay for spammers. So what I am looking for is a way to

A) Force remote users/clients to login to the e-mail server in order to send emails.

B) Allow e-mails to be sent to any outside domain from anywhere, not just on my local machine/network.

Here is what happens when I am logged into the server and use telnet to connect to Postfix to send a message. Note everything goes well:

```

Trying 127.0.0.1...                                                                                                                                          
Connected to localhost.localdomain.                                                                                                                          
Escape character is '^]'.                                                                                                                                    
220 mydomain.com ESMTP Postfix                                                                                                                            
ehlo localhost                                                                                                                                               
250-PIPELINING                                                                                                                                              
250-SIZE 10240000                                                                                                                                            
250-VRFY                                                                                                                                                     
250-ETRN                                                                                                                                                     
250-STARTTLS                                                                                                                                                 
250-ENHANCEDSTATUSCODES                                                                                                                                      
250-8BITMIME                                                                                                                                                 
250 DSN                                                                                                                                                      
mail from: me@localhost                                                                                                                                  
250 2.1.0 Ok                                                                                                                                                 
rcpt to: someone@gmail.com                                                                                                                              
250 2.1.5 Ok                                                                                                                                                 
data                                                                                                                                                         
354 End data with <CR><LF>.<CR><LF> 

```

And here is what happens when I telnet into the mail server from home, relaying e-mail is denied.

```

Connected to myhost.com.
Escape character is '^]'.
220 myhost.com ESMTP Postfix
ehlo myremotemachine.com
250-welovemetal.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: me@localhost
250 2.1.0 Ok
rcpt to: someone@gmail.com
554 5.7.1 <someone@gmail.com>: Relay access denied

```


And, finally, here is my Postfix configuration file.

```

myorigin = /etc/mailname
 smtpd_banner = $myhostname ESMTP $mail_name 
biff = no
 # appending .domain is the MUA's job.
append_dot_mydomain = no
 readme_directory = no


# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

myhostname = myhost.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = myhost.com, mail.myhost.com, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128, 74.121.150.63
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 500000000
recipient_delimiter = +
inet_interfaces = all

 home_mailbox = Maildir/
mailbox_command = 


```




At the moment I'm not so worried about encryption and such, I just want to get Postfix to let me login and then forwad my e-mails to outside domains. Thoughts?

---

### Post by thnewguy on 2014-02-05
I found the issue and it seems to be working okay now. This guide was very helpful: [https://help.ubuntu.com/10.04/serverguide/postfix.html](https://help.ubuntu.com/10.04/serverguide/postfix.html)

The key part I was missing was the[FONT=monospace]"dovecot-postfix" package which is available in Ubuntu's repositories. Once that was installed and my "[/FONT][FONT=monospace]smtpd_recipient_restrictions" line in /etc/postfix/main.cf was altered to match the line in the above guide, everything worked on the server-side. I had to tell my e-mail client to use STARTTLS and send a username/password too on the client side. Hope this helps anyone else setting up an e-mail server.

[/FONT]

---

