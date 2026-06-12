---
title: "postfix email server wont send mail from PHP form"
date: 2017-11-21
forum: Server Platforms
---

### Post by elsheepo on 2017-11-21
Good morning forum!
So, apart from this particular server being my first use of Ubuntu, it is also my first attempt at installing/configuring an email server. I will try to provide as much detailed information as my experience allows me to. So without further adue...

I installed Ubuntu Server 17.10 onto my [LIVA Bay-Trail SoC]("https://www.links.co.jp/item/liva-w10/"). I configured ufw to allow traffic on port 80 for apache2, and port 29000 for ssh (yes I edited /etc/ssh/sshd_config)
```

beatzz@LIVA:~$ sudo ufw default deny incoming
beatzz@LIVA:~$ sudo ufw default allow outgoing
beatzz@LIVA:~$ sudo ufw allow 80
beatzz@LIVA:~$ sudo ufw allow 29000

```
```

beatzz@LIVA:~$ sudo ufw status
Status: active


To                         Action      From
--                         ------      ----
80/tcp                     ALLOW       Anywhere
29000                      ALLOW       Anywhere
80/tcp (v6)                ALLOW       Anywhere (v6)
29000 (v6)                 ALLOW       Anywhere (v6)

```
my apache2 server is functioning just fine, you should be able to access it [beatzz.co]("http://www.beatzz.co")
Following [this tutorial]("https://www.linux.com/learn/how-build-email-server-ubuntu-linux") I installed postfix, dovecot-imapd, and dovecot-pop3d.  I also made changes to /etc/postfix/main.cf and /etc/dovecot/dovecot.conf
```
beatzz@LIVA:~$ less /etc/postfix/main.cf


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


# See http://www.postfix.org/COMPATIBILITY_README.html -- default to 2 on
# fresh installs.
compatibility_level = 2


# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = LIVA
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myhostname, LIVA.beatzz.co, LIVA, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all


# Stuff I added from the tutorial


mail_spool_directory = /var/mail
home_mailbox = .Mail/

```
```

beatzz@LIVA:~$ less /etc/dovecot/dovecot.conf

# Revised dovecot.conf as per the tutorial

disable_plaintext_auth = no
mail_location = maildir:~/.Mail
namespace inbox {
  inbox = yes
  mailbox Drafts {
    special_use = \Drafts
  }
  mailbox Sent {
    special_use = \Sent
  }
  mailbox Trash {
    special_use = \Trash
  }
}
passdb {
  driver = pam
}
protocols = " imap pop3"
ssl = no
userdb {
  driver = passwd
}

```
after reloading all three services apache2, postfix, and dovecot I tested the email service via telnet on the localhost as per the tutorial, and it had successfully sent an email to my /home/beatzz/.Mail/
but when I send a message from the PHP form located in /var/www/html/ nothing is sent. here is the HTML and PHP for said form.
```

            <form name="sentMessage" id="contactForm" novalidate>
              <div class="control-group">
                <div class="form-group floating-label-form-group controls">
                  <label>Name</label>
                  <input name="name" class="form-control" id="name" type="text" placeholder="Name" required data-validation-required-message="Please enter your name.">
                  <p class="help-block text-danger"></p>
                </div>
              </div>
              <div class="control-group">
                <div class="form-group floating-label-form-group controls">
                  <label>Email Address</label>
                  <input name="email" class="form-control" id="email" type="email" placeholder="Email Address" required data-validation-required-message="Please enter your email address.">
                  <p class="help-block text-danger"></p>
                </div>
              </div>
              <div class="control-group">
                <div class="form-group floating-label-form-group controls">
                  <label>Message</label>
                  <textarea name="message" class="form-control" id="message" rows="5" placeholder="Message" required data-validation-required-message="Please enter a message."></textarea>
                  <p class="help-block text-danger"></p>
                </div>
              </div>
              <br>
              <div id="success"></div>
              <div class="form-group">
                <button type="submit" class="btn btn-success btn-lg" id="sendMessageButton">Send</button>
              </div>
            </form>

```
```

<?php
if(empty($_POST['name'])      ||
   empty($_POST['email'])     ||
   empty($_POST['message'])   ||
   !filter_var($_POST['email'],FILTER_VALIDATE_EMAIL))
   {
   echo "No arguments Provided!";
   return false;
   }
   
$name = strip_tags(htmlspecialchars($_POST['name']));
$email_address = strip_tags(htmlspecialchars($_POST['email']));
$message = strip_tags(htmlspecialchars($_POST['message']));


$to = 'linux.beatzz@gmail.com';
$email_subject = "Website Contact Form:  $name";
$email_body = "You have received a new message from your website contact form.\n\n
               Here are the details:\n\n
               Name: $name\n\n
               Email: $email_address\n\n
               Message:\n
               $message";
$headers = "From: noreply@beatzz.co\n";
$headers .= "Reply-To: $email_address";   
mail($to,$email_subject,$email_body,$headers);
return true;         
?>

```
I'm not sure what to do at this point. I've read maybe the problem is in /etc/php/7.1/apache2/php.ini but I'm unfamiliar with PHP in general. Any insight as to why the PHP form is not sending mail would be greatly appreciated.

---

### Post by SeijiSensei on 2017-11-22
What do you see in /var/log/apache2/error.log?  PHP will log its errors there.

If you're on a residential Internet connections, the chances are good that you cannot send any mail to remote machines.  Most ISPs block outbound port 25 (SMTP) connections to thwart spamming from infected Windows computers.  You need to check with your ISP.

Try sending a test message to your gmail account using
```
telnet gmail-smtp-in.l.google.com 25
```
Since my provider blocks outbound SMTP, running this command on my home computer results in a hung connection and no banner from GMail.  Running it from one of my virtual servers in the cloud connects instantly.

---

