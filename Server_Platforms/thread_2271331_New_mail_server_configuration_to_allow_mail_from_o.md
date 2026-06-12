---
title: "New mail server configuration to allow mail from other server"
date: 2015-03-29
forum: Server Platforms
---

### Post by perry-hart-sweetser on 2015-03-29
I have been working on setting up a mail server on Ubuntu server 15.05. This is actually my third attempt. In the first two, I followed a how-to by binarytides with dovecot and one by flurdy with courier. In both, I was able to receive mail on the server and send mail via telnet, but I could not send mail otherwise – primarily due to authentication problems with mysql. I rather liked the advice from flurdy, which said to ensure that the basic setup was working before continuing, but there were a few advanced configuration parameters in the basic setup that necessitated the use of TSL, which were hard to check, plus the aggravation of a zillion typos, so I started again…and again.
This (3[SUP]rd[/SUP]) time I installed the whole mail server package during the install process, thinking that the people who set it up knew what they were doing. (In the first two attempts, I installed and configured each package separately.)  I kept it simple, added some restrictions and just tweaked the most elementary stuff – like *mydestination* and *mynetworks* – and it worked fine. I can send and receive mail both from the server and from clients in another subnet and my logs don’t show any errors.
I set up a Linux web server on the same subnet as the mail server with the intention of sending reports to the database administrator of that server through the mail server using PHPMailer. However, that did not work as the database server was rejected by the mail server. There were no authentication errors in the auth.log or mail.log files, but that was because (I believe) the server was rejected before it could authenticate.
The mail.log shows this after running the PHPMailer script on the database sever:
smtp postfix/smtpd[2513]: match_hostname: FVS336Gv2 ~? 10.10.10.0/24
smtp postfix/smtpd[2513]: match_hostaddr: 10.10.10.1 ~? 10.10.10.0/24
smtp postfix/smtpd[2513]: > FVS336Gv2[10.10.10.1]: 220 smtp.mydomain.net ESMTP Postfix (Ubuntu)
smtp postfix/smtpd[2513]: < FVS336Gv2[10.10.10.1]: EHLO localhost
smtp postfix/smtpd[2513]: match_list_match: FVS336Gv2: no match
smtp postfix/smtpd[2513]: match_list_match: 10.10.10.1: no match
smtp postfix/smtpd[2513]: > FVS336Gv2[10.10.10.1]: 250-smtp.mydomain.net
smtp postfix/smtpd[2513]: > FVS336Gv2[10.10.10.1]: 250-PIPELINING
smtp postfix/smtpd[2513]: > FVS336Gv2[10.10.10.1]: 250-SIZE 10240000
smtp postfix/smtpd[2513]: > FVS336Gv2[10.10.10.1]: 250-VRFY
smtp postfix/smtpd[2513]: > FVS336Gv2[10.10.10.1]: 250-ETRN
smtp postfix/smtpd[2513]: > FVS336Gv2[10.10.10.1]: 250-STARTTLS
smtp postfix/smtpd[2513]: > FVS336Gv2[10.10.10.1]: 250-ENHANCEDSTATUSCODES
smtp postfix/smtpd[2513]: > FVS336Gv2[10.10.10.1]: 250-8BITMIME
smtp postfix/smtpd[2513]: > FVS336Gv2[10.10.10.1]: 250 DSN
smtp postfix/smtpd[2513]: < FVS336Gv2[10.10.10.1]: QUIT
smtp postfix/smtpd[2513]: > FVS336Gv2[10.10.10.1]: 221 2.0.0 Bye
smtp postfix/smtpd[2513]: match_hostname: FVS336Gv2 ~? 10.10.10.0/24
smtp postfix/smtpd[2513]: match_hostaddr: 10.10.10.1 ~? 10.10.10.0/24
smtp postfix/smtpd[2513]: disconnect from FVS336Gv2[10.10.10.1]
smtp postfix/smtpd[2513]: master_notify: status 1
smtp postfix/smtpd[2513]: connection closed
 
The database server has a LAN address of 10.10.10.200 and the FVS336Gv2 router’s LAN address, which shows up here, is 10.10.10.1.
It seems to me that postfix is trying to use a lookup table to find the sender’s hostname/subnet, as it says things like “match_list_match” + “no_match”, but I couldn’t find anything in the postfix documentation about lookup tables that covered this. I tried putting these addresses in the hosts file, but that didn’t help. I was thinking that as the mail request comes from the database server, perhaps I need to tell the mail sever that it is functioning as a relay – something like “relayhost =smtp.mydomain.net”, but that doesn’t sound quite right to me.
At any rate, this is my main.cf file:
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
readme_directory = no
 
# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
 
smtpd_tls_security_level = may
 
smtpd_recipient_restrictions = permit_mynetworks,reject_unauth_pipelining, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_data_restrictions = permit_mynetworks,reject_unauth_pipelining
 
smtpd_relay_restrictions = permit_mynetworks, permit_sasl_authenticated, defer_unauth_destination
myhostname = smtp.$domainname
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $domainname, localhost.$domainname, localhost
relayhost = 
 
mynetworks = 10.10.10.0/24, 127.0.0.1/32 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
 
Before anyone jumps on me about the minimal security in the above file, you have to understand that I want to get the server to work before locking it down. That way, I can monitor any change to the server in the logs that any security configuration will make. 
And, by the way, the PHPMailer test code:
 
require '../PHPMailerAutoload.php';
 
$mail = new PHPMailer;
$mail->isSMTP();
$mail->SMTPDebug = 2;
$mail->Debugoutput = 'html';
$mail->Host = "smtp.hornnes.vgs.net";
$mail->Port = 25;
$mail->SMTPAuth = true;
$mail->Username = "support@mydomain.net";
$mail->Password = "mypassword";
 
$mail->setFrom('support@mydomain.net', 'Support dept.');
$mail->addAddress('me@myworkplace', 'Perry Sweetser');
$mail->CharSet = 'ISO 8859';
$mail->ContentType = 'text/plain';
$mail->IsHTML(false);
$mail->Subject = 'PHPMailer SMTP test';
$mail->Body    = 'This is the message body ';
 
if (!$mail->send()) {
    echo "Mailer Error: " . $mail->ErrorInfo;
} else {
    echo "Message sent!";
}
 
I’d appreciate any advice on fixing this.

---

### Post by perry-hart-sweetser on 2015-03-29
I fixed this myself :p. The mistake was in the PHPMailer code:

$mail->SMTPAuth = true;

As I have not yet locked down the system, this should read "false".

At any rate, I have noticed that many others on other web sites have wondered about the "match_list_match" - "no match" pairing. I still have some of those in my mail.log, and I can guess at some (looking for matches in the main.cf file, for example); however, it WOULD be nice if the lookup procedure and its sequence -ie which files are used in the lookup process and in which order - were documented somewhere. It would seem that a "no match" is not necessarily an error - which is how I interpreted it.

---

