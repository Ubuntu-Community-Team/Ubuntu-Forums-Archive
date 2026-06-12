---
title: "Postfix Dovecot, No External Emails Coming In"
date: 2009-10-03
forum: Server Platforms
---

### Post by Lukas1 on 2009-10-03
Hi I am working on a project that I have been for a while. Its an Ubuntu Jaunty Server on a Dell Poweredge. 

My current problem is that I cannot get emails to come into the system from the outside. I installed postfix and dovecot through tasksel and followed up with the recommended spam software, which I have since disabled. I can access my local email through Thunderbird client and from there can send emails locally and outside the network, but nothing can come in. I can telnet to my server , but not via the mailserver's FQDN (I can telnet globalcapeesh.com on port 25 but not mail.globalcapeesh.com).

My DNS is hosted through everydns.org and my mx record calls the server at mail.globalcapeesh.com. This might be the issue? Idunno but thanks for looking.

Here's my main.cf:
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
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls = no
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

mydomain = globalcapeesh.com
myhostname = mail.globalcapeesh.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $mydomain
mydestination = mail.globalcapeesh.com, localhost.localdomain, localhost, globalcapeesh.com
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 10.0.1.0/24
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_authenticated_header = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = globalcapeesh.com
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sender_restrictions = reject_unknown_sender_domain
smtp_use_tls = yes
smtpd_tls_received_header = yes
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium, high
smtpd_tls_auth_only = no
tls_random_source = dev:/dev/urandom
content_filter = smtp-amavis:[127.0.0.1]:10024
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_session_cache_timeout = 3600s

---

### Post by kustomjs on 2009-10-04
who is your domain register? did you update your mx records to point to your IP address?

---

### Post by Lukas1 on 2009-10-05
My domain registrar is GLobat.com, my website is up and running fine. I made an MX record a week or two ago. I have my DNS hosted by this company that does it for free called everydns.net. I don't think that my record was right. I just changed it and may need 3 hours for changes to propogate. Does this look right?

mail.globalcapeesh.com MX 10 globalcapeesh.com.

Thank you for the reply

EDIT:
ok that previous DNS entry is erroneous. I made it as follows, which I think is right because I can telnet in to mail.globalcapeesh.com on port 25 now.

mail.globalcapeesh.com. IN A 72.54.150.146
globalcapeesh.com. MX 10 mail.globalcapeesh.com. 

Again I think its right because I can telnet in, but now mail does not seem to be working at all. I have my email client set to mail.globalcapeesh.com and when I send a mail through mailx from another user to the one I created, I can access it in my email client, but I cannot mail out from that email client. Also If I send an email from outside the network (.ie gmail) it still does not arrive to my user. any ideas?

Thank you

---

### Post by Lukas1 on 2009-10-06
OK Making progress here; I uninstalled postfix and dovecot 'apt-get remove postfix dovecot' then restarted my machine. I used the tasksel command to pull up my nifty server menu and unchecked mail server. I had to 'dpkg --configure -a' and then I did 'sudo apt-get install dovecot-postfix.' SOme how it seems that it knew what to install because most of my configurations were there, maybe my main.cf file was not changed? I don't know. 

After all that I was able to email in from outside, like my gmail account. YESAHH. and pop it into my thunderbird email client. 

Now I am stuck on sending mails from my client, it says:
An error occurred while sending mail. The server responded: 5.7.1 <emailaddress>:
Relay access denied. Please check the message recipients and try again.

ANy ideas?

---

### Post by Lukas1 on 2009-10-07
main.cf smtpd_tls_auth_only = no

That allowed me to telnet in and see:
ehlo mail.globalcapeesh.com

**250**-**AUTH** **PLAIN** **LOGIN** 
**250**-**AUTH**=**PLAIN** **LOGIN** 

Then I looked over dovecot.conf, looked ok. I restarted everything and it worked yo.

---

### Post by SoftwareExplorer on 2009-10-10
Sorry it took me so long to reply, I was quite busy with colledge math. 
Here's my main.cf (without all the comments)
```
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
readme_directory = no
smtpd_tls_cert_file = /etc/ssl/certs/ssl-mail.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-mail.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
myhostname = bjorn-desktop
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = erikbandersen.com, bjorn-desktop, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/dovecot-postfix.conf -n -m "${EXTENSION}"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/
smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_authenticated_header = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sender_restrictions = reject_unknown_sender_domain
smtp_use_tls = yes
smtpd_tls_received_header = yes
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium, high
smtpd_tls_auth_only = no
tls_random_source = dev:/dev/urandom
```

And my dovecot-postfix.conf (replaces dovecot.conf when it exists.) (without comments)
```
protocols = imap pop3 imaps pop3s managesieve
disable_plaintext_auth = yes
log_timestamp = "%Y-%m-%d %H:%M:%S "
ssl_disable = no
ssl_cert_file = /etc/ssl/certs/ssl-mail.pem
ssl_key_file = /etc/ssl/private/ssl-mail.key
ssl_cipher_list = ALL:!LOW:!SSLv2:ALL:!aNULL:!ADH:!eNULL:!EXP:RC4+RSA:+HIGH:+MEDIUM
mail_location = maildir:~/Maildir
mail_privileged_group = mail

protocol imap {
  mail_max_userip_connections = 10
  login_greeting_capability = yes
  imap_client_workarounds = outlook-idle delay-newmail
}
protocol pop3 {
  pop3_uidl_format = %08Xu%08Xv
  mail_max_userip_connections = 3
  pop3_client_workarounds = outlook-no-nuls oe-ns-eoh
}
protocol managesieve {
  sieve=~/.dovecot.sieve
  sieve_storage=~/sieve
}
protocol lda {
  postmaster_address = postmaster
  mail_plugins = cmusieve
  quota_full_tempfail = yes
  deliver_log_format = msgid=%m: %$
  rejection_reason = Your message to <%t> was automatically rejected:%n%r
}
auth_username_chars = abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ01234567890.-_@
auth default {
  mechanisms = plain login
  passdb pam {
  }
  userdb passwd {
  }
  user = root
  socket listen {
      client {
      path = /var/spool/postfix/private/dovecot-auth
      mode = 0660
      user = postfix
      group = postfix
    }
  }
}
dict {
}
plugin {
}
```

---

### Post by Lukas1 on 2009-10-14
Try this:
# telnet mail.erikbanderson.com 25

That should get you into a different style of command prompt. Then

ehlo mail.erikbanderson.com

If you see the following among other lines, you should be good to go otherwise post what you see:

**250**-**AUTH** **PLAIN** **LOGIN** 
**250**-**AUTH**=**PLAIN** **LOGIN** 

I am assuming of course that your DNS says your mail server is mail.erikbanderson.com and not something else.

---

### Post by SoftwareExplorer on 2009-10-14
I think the problem is my isp, I asked them and they said that they block port 25 outgoing. However, I asked them if I could have it opened for my connection, and they didn't sound to adverse to that, all they needed to do was to consult their guru who had left for the day and see if it was possible to open the port for just one connection.

On another note, here's what I got from following your instuctions:
```
[bjorn@bjorn-desktop:~]$ telnet mail.erikbandersen.com 25      (10-14 10:44:28)
Trying 127.0.0.1...
Connected to mail.erikbandersen.com.
Escape character is '^]'.
220 bjorn-desktop ESMTP Postfix (Ubuntu)
ehlo mail.erikbandersen.com
250-bjorn-desktop
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME

```

And as far as dns, I think it is working because I receive mail just fine. To do the test you had me do I put the domain name in my hosts file because the computer is behind a nat router that doesn't like to talk to itself using the outside address.

---

### Post by Lukas1 on 2009-10-14
Maybe try your dovecot file with:
disable_plaintext_auth = no

If that doesn't do it here are some other ideas:

Try these changes in your main.cf

mydomain = erikbanderson.com
myhostname = mail.erikbanderson.com
myorigin = $mydomain
mydestination = mail.erikbanderson.com, localhost.localdomain, localhost, erikbanderson.com

smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks

Let me know how it goes.

---

### Post by SoftwareExplorer on 2009-10-15
So I talked to my ISP and they said they could open 25 if I had a static IP. They offered to let me use their server with smarthost, so I googled setting that up, and tried sending a message. I'll see if it comes back to me, or if it works.

One question I have is where postfix keeps its logs.

Thanks.

---

### Post by rnodal on 2009-10-15
> **SoftwareExplorer said:**
> 

One question I have is where postfix keeps its logs.

Thanks.

> /var/log/mail.{log|err|info|warn}

-r

---

### Post by SoftwareExplorer on 2009-10-16
My isp let my use their email server as a smart host and it works. :)

---

### Post by Lukas1 on 2009-10-17
Great glad to hear!

---

