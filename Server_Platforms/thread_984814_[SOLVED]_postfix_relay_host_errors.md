---
title: "[SOLVED] postfix relay host errors"
date: 2008-11-17
forum: Server Platforms
---

### Post by genesimmons4201 on 2008-11-17
myorigin = example.ca
myhostname = example.ca
biff = no
append_dot_mydomain = no
home_mailbox = Maildir/
#unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
mydomain = thoughtforge.ca
smtp_helo_timeout = 60s
smtpd_recipient_limit = 32
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject, reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, check_policy_service inet:127.0.0.1:60000 permit permit_inet_interfaces
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
disable_vrfy_command = yes
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
mailbox_size_limit = 0
recipient_delimiter = +
local_recipient_maps =
delay_warning_time = 4h
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
local_recipient_maps =
mydestination = persephone.thoughtforge.ca
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


tls_random_source = dev:/dev/urandom 

smtpd_sasl_security_options = 
smtpd_recipient_restrictions = permit_mynetworks check_relay_domains reject_unauth_destination relay_ok
#nov 16th added relay_ok
smtpd_reciepient_restrictions = permint_mynetworks check_relay domains relay_ok

#doesn't matter
#smtpd_recipient_restrictions = reject_unauth_pipelining #permit_mynetworks permit_sasl_authenticated reject_non_fqdn_recipient #reject_unknown_recipient_domain permit_inet_interfaces #reject_unauth_destination


broken_sasl_auth_clients = yes
relay_recipient_maps = hash:/etc/postfix/relay_recipients
#transport_maps = hash:/etc/postfix/relay_recipients
allow_untrusted_routing = yes
smtp_skip_4xx_greeting = yes
ignore_mx_lookup_error = yes



thanks in advance

---

### Post by MJN on 2008-11-17
Come on - at least put the effort in to describe what you were doing, what you expected to happen, and a snippet from the log (/var/log/mail.log) showing what actually happened.
 
Mathew

---

### Post by genesimmons4201 on 2008-11-17
Sorry. and thanks but was cut off. I can sent mail to local domains with no problems but when going to external domains it just gives myself refused rejection errors when trying to send to a different domain.

Log


Nov 17 06:14:19 persephone postfix/smtpd[20572]: setting up TLS connection from LONDON14-1279657910.sdsl.bell.ca[76.70.7.182]
Nov 17 06:14:21 persephone postfix/smtpd[20572]: Anonymous TLS connection established from LONDON14-1279657910.sdsl.bell.ca[76.70.7.182]: TLSv1 with cipher DHE-RSA-AES256-SHA (256/256 bits)
Nov 17 06:14:21 persephone postfix/smtpd[20572]: NOQUEUE: reject: RCPT from LONDON14-1279657910.sdsl.bell.ca[76.70.7.182]: 554 5.7.1 <cswebserver@gmail.com>: Relay access denied; from=<webmaster@thoughtforge.ca> to=<cswebserver@gmail.com> proto=ESMTP helo=<[192.168.2.32]>
Nov 17 06:14:22 persephone postfix/smtpd[20572]: disconnect from LONDON14-1279657910.sdsl.bell.ca[76.70.7.182]

---

### Post by MJN on 2008-11-17
Given you are connecting from a remote location (i.e. not somewhere listed in $mynetworks) then the only way you are going to be able to relay is by satisfying the 'permit_sasl_authenticated' directive.
 
Hence, your client needs to authenticate with the server - usually using a username and password. Have you set it to do so?
 
Mathew

---

### Post by genesimmons4201 on 2008-11-17
Yea I have it logs in and verifies the username and password if sending to someone inside my domain if the email is going to a third party I get the error above. 

I thought it was todo with local reciept mappings  but that didn't seem to correct the issue.

Thank
CHris

---

### Post by MJN on 2008-11-17
> **genesimmons4201 said:**
> Yea I have it logs in and verifies the username and password if sending to someone inside my domain if the email is going to a third party I get the error above.If the recipient address is inside your domain then there is no need for client authentication. Can you post the log snippet that shows authentication taking place?
 
> I thought it was todo with local reciept mappings but that didn't seem to correct the issue.No, local recipient mappings are not consulted for relayed external mail.
 
Mathew

---

### Post by genesimmons4201 on 2008-11-17
with that addition the log has..

Nov 17 22:27:52 persephone imapd-ssl: LOGIN, user=webmaster@thoughforge.ca, ip=[::ffff:76.70.7.182], port=[1095], protocol=IMAP
Nov 17 22:28:20 persephone postfix/smtpd[24201]: fatal: parameter "smtpd_recipient_restrictions": specify at least one working instance of: check_relay_domains, reject_unauth_destination, reject, defer or defer_if_permit

---

### Post by MJN on 2008-11-18
What addition? I didn't suggest adding anything.
 
It looks like you have removed the smptd_recipient_restrictions directive but, as the log says, this directive is required (and must be valid).
 
Your problem is that your mail client is not successfully authenticating with your server and hence is not 'trusted' to the extent that it is allowed to relay mail off-site. You need to double-check that your client is configured to authenticate.
 
Open up /etc/postfix/master.cf and add -v to the end of the smtpd.....smtp line (most likely the first line) and restart Postfix. This will add a high level of verbose logging to the smtpd process - send a message with your client (to an external recipient) and post the output. We can then see if the client if attempting to authenticate or not.
 
Mathew

---

### Post by tqzxzjhu on 2008-11-18
[&#31649;&#36947;&#30095;&#36890;](http://classad.dahangzhou.com/223685.html)[&#30095;&#36890;&#31649;&#36947;](http://classad.dahangzhou.com/223685.html)[&#31649;&#36947;&#30095;&#36890;&#20844;&#21496;](http://classad.dahangzhou.com/223685.html)[&#39532;&#26742;&#30095;&#36890;](http://classad.dahangzhou.com/223685.html)[&#36466;&#22353;&#30095;&#36890;](http://classad.dahangzhou.com/223685.html)

---

### Post by genesimmons4201 on 2008-11-18
Still more issues thanks for the help guys and I help this helps more


myorigin = xxxxx.xxxxx.ca
myhostname = xxxxx.xxxxx.ca
biff = no
append_dot_mydomain = no
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
home_mailbox = Maildir/
#unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
mydomain = thoughtforge.ca
smtp_helo_timeout = 60s
smtpd_recipient_limit = 32
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject, reject_non_fqdn_hostname, reject_invalid_hostname, permit
#smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, check_policy_service inet:127.0.0.1:60000 permit permit_inet_interfaces
#smtpd_data_restrictions = reject_unauth_pipelining
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_sender_restrictions = permit_sasl_authenticated, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_helo_required = no
disable_vrfy_command = yes
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
mailbox_size_limit = 0
recipient_delimiter = +
delay_warning_time = 4h
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
local_recipient_maps =
mydomain = xxxxx.ca
mydestination = xxxx.xxxxx.ca
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


tls_random_source = dev:/dev/urandom 

smtpd_sasl_security_options = 
smtpd_recipient_restrictions =  reject_unauth_destination permit_mynetworks permit_sasl_authenticated
#smtpd_recipient_restrictions = reject_unauth_pipelining permit_mynetworks permit_sasl_authenticated reject_non_fqdn_recipient reject_unknown_recipient_domain permit_inet_interfaces reject_unauth_destination
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes


-----------------------------
Log 
_----------------------------
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: resolve_clnt: `' -> `xxxxxxx@xxxxxxx.com' -> transp=`smtp' host=`gmail.com' rcpt=`xxxxxxx@xxxxxxx.com' flags= class=default
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: ctable_locate: install entry key [email]xxxxxxx@xxxxxxx.com[/email]
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: extract_addr: in: <xxxxxxx@xxxxxxx.com>, result: [email]xxxxxxx@xxxxxxx.com[/email]
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: send attr request = rewrite
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: send attr rule = local
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: send attr address = double-bounce
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: private/rewrite socket: wanted attribute: flags
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: input attribute name: flags
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: input attribute value: 0
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: private/rewrite socket: wanted attribute: address
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: input attribute name: address
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: input attribute value: [email]double-bounce@xxxxxxx.ca[/email]
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: private/rewrite socket: wanted attribute: (list terminator)
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: input attribute name: (end)
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: rewrite_clnt: local: double-bounce -> double-bounce@xxxxxxx
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: >>> START Helo command RESTRICTIONS <<<
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: generic_checks: name=permit_mynetworks
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: permit_mynetworks: xxxxxxx
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: match_hostname: xxxxxxx ~? 127.0.0.0/8
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: match_hostaddr: xxxxxxx ~? 127.0.0.0/8
Nov 18 21:33:03 persephone postfix/smtpd[1391]: match_hostname: xxxxxxx ~? xxxxxxxlocal ip/24
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: match_hostaddr: internet ip ~? local ip 173/24
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: match_list_match: "domain name of client pc" no match
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: match_list_match: ip client: no match
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: generic_checks: name=permit_mynetworks status=0
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: generic_checks: name=warn_if_reject
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: generic_checks: name=reject_non_fqdn_hostname
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: reject_invalid_hostaddr: [192.168.2.248]
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: generic_checks: name=reject_non_fqdn_hostname status=0
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: generic_checks: name=reject_invalid_hostname
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: reject_invalid_hostaddr: [192.168.2.248]
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: generic_checks: name=reject_invalid_hostname status=0
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: generic_checks: name=permit
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: generic_checks: name=permit status=1
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: >>> START Sender address RESTRICTIONS <<<
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: generic_checks: name=permit_sasl_authenticated
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: generic_checks: name=permit_sasl_authenticated status=0
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: generic_checks: name=reject_non_fqdn_sender
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: reject_non_fqdn_address: [email]webmaster@xxxxxxx.ca[/email]
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: generic_checks: name=reject_non_fqdn_sender status=0
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: generic_checks: name=reject_unknown_sender_domain
Nov 18 21:33:03 persephone postfix/smtpd[1391]: reject_unknown_address: [email]webmaster@xxxxxxx.ca[/email]
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: ctable_locate: move existing entry key [email]webmaster@xxxxxxx.ca[/email]
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: generic_checks: name=reject_unknown_sender_domain status=0
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: generic_checks: name=reject_unauth_pipelining
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: reject_unauth_pipelining: RCPT
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: generic_checks: name=reject_unauth_pipelining status=0
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: generic_checks: name=permit
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: generic_checks: name=permit status=1
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: >>> START Recipient address RESTRICTIONS <<<
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: generic_checks: name=reject_unauth_destination
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: reject_unauth_destination: [email]xxxxxxx@xxxxxxx.com[/email]
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: permit_auth_destination: [email]xxxxxxx@xxxxxxx.com[/email]
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: ctable_locate: move existing entry key xxxxxxx#xxxxxxx.com
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: NOQUEUE: reject: RCPT from xxxxxxx.bell.ca[76.70.7.182]: 554 5.7.1 <xxxxxxx@gmail.com>: Relay access denied; from=<webmaster@xxxxxxx.ca> to=<xxxxxxx@gmail.com> proto=ESMTP helo=<[192.168.2.248]>
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: generic_checks: name=reject_unauth_destination status=2
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: > xxxxxxx.bell.ca[xx.xx.xx.xx]: 554 5.7.1 <xxxxxxx@gmail.com>: Relay access denied
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: < xxxxxxx[xx.xx.xx.xx]: QUIT
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: > xxxxxxx.bell.ca[xx.xx.xx.xx]: 221 2.0.0 Bye
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: match_hostname: xxxxxxx.bell.ca ~? 127.0.0.0/8
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: match_hostaddr: xx.xx.xx.xx ~? 127.0.0.0/8
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: match_hostname: xxxxxxx.bell.ca ~? 173.45.226.0/24
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: match_hostaddr: xxxxxxx ~? 173.45.226.0/24
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: match_list_match: xxxxxxx.bell.ca: no match
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: match_list_match: 76.70.7.182: no match
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: send attr request = disconnect
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: send attr ident = smtp:76.70.7.182
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: private/anvil: wanted attribute: status
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: input attribute name: status
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: input attribute value: 0
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: private/anvil: wanted attribute: (list terminator)
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: input attribute name: (end)
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: disconnect from xxxxxxx.bell.ca[xxxxxxx]
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: master_notify: status 1
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1391]: connection closed
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1394]: connect from xxxxxxx[xxxxxxx]
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1394]: setting up TLS connection from xxxxxxx.bell.ca[xxxxxxx]
Nov 18 21:33:03 xxxxxxx postfix/smtpd[1394]: Anonymous TLS connection established from xxxxxxx.bell.ca[xxxxxxx]: SSLv3 with cipher DHE-RSA-AES256-SHA (256/256 bits)
Nov 18 21:33:08 xxxxxxx postfix/smtpd[1391]: auto_clnt_close: disconnect private/tlsmgr stream
Nov 18 21:33:08 xxxxxxx postfix/smtpd[1391]: rewrite stream disconnect
Nov 18 21:33:10 xxxxxxx postfix/smtpd[1394]: warning: SASL authentication failure: Password verification failed
Nov 18 21:33:10 xxxxxxx postfix/smtpd[1394]: warning: xxxxxxx.bell.ca[xxxxxxx]: SASL PLAIN authentication failed: authentication failure
Nov 18 21:33:15 xxxxxxx postfix/smtpd[1394]: warning: SASL authentication failure: Password verification failed
Nov 18 21:33:15 xxxxxxx postfix/smtpd[1394]: warning: xxxxxxx[xxxxxxx]: SASL PLAIN authentication failed: authentication failure
Nov 18 21:33:19 xxxxxxx postfix/smtpd[1394]: warning: SASL authentication failure: Password verification failed
Nov 18 21:33:19 xxxxxxx postfix/smtpd[1394]: warning: rogers-network.ca[xxxxxxx]: SASL PLAIN authentication failed: authentication failure
Nov 18 21:33:25 xxxxxxx imapd-ssl: Connection, ip=[::ffff:127.0.0.1]
Nov 18 21:33:25 xxxxxxx authdaemond: received auth request, service=imaps, authtype=login
Nov 18 21:33:25 persephone authdaemond: authmysql: trying this module
Nov 18 21:33:25 persephone authdaemond: SQL query: SELECT id, crypt, "", uid, gid, home, concat(home,'/',maildir), "", name, "" FROM users WHERE id = "webmaster@xxxxxxx.ca" AND (enabled=1)
Nov 18 21:33:25 xxxxxxx authdaemond: password matches successfully
Nov 18 21:33:25 xxxxxxx authdaemond: authmysql: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/var/spool/mail/virtual, address=webmaster@xxxxxxx.ca, fullname=webmaster, maildir=/var/spool/mail/virtual/webmaster/, quota=<null>, options=<null>
Nov 18 21:33:25 xxxxxxx authdaemond: authmysql: clearpasswd=<null>, passwd=xxxxxxx
Nov 18 21:33:25 xxxxxxx authdaemond: Authenticated: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/var/spool/mail/virtual, address=webmaster@xxxxxxx.ca, fullname=webmaster, maildir=/var/spool/mail/virtual/webmaster/, quota=<null>, options=<null>
Nov 18 21:33:25 xxxxxxxxx authdaemond: Authenticated: clearpasswd=xxxxxxx, passwd=xxxxxxxx
Nov 18 21:33:25 xxxxxxx imapd-ssl: LOGIN, user=webmaster@xxxxxxx.ca, ip=[::ffff:127.0.0.1], port=[36257], protocol=IMAP
Nov 18 21:33:25 xxxxxxxx imapd-ssl: LOGOUT, user=webmaster@xxxxxxx.ca, ip=[::ffff:127.0.0.1], headers=0, body=0, rcvd=87, sent=392, time=0, starttls=1

---

### Post by MJN on 2008-11-19
> **genesimmons4201 said:**
> 
Nov 18 21:33:10 xxxxxxx postfix/smtpd[1394]: warning: SASL authentication failure: Password verification failed
Nov 18 21:33:10 xxxxxxx postfix/smtpd[1394]: warning: xxxxxxx.bell.ca[xxxxxxx]: SASL PLAIN authentication failed: authentication failure
Nov 18 21:33:15 xxxxxxx postfix/smtpd[1394]: warning: SASL authentication failure: Password verification failed
Nov 18 21:33:15 xxxxxxx postfix/smtpd[1394]: warning: xxxxxxx[xxxxxxx]: SASL PLAIN authentication failed: authentication failure
Nov 18 21:33:19 xxxxxxx postfix/smtpd[1394]: warning: SASL authentication failure: Password verification failed
Nov 18 21:33:19 xxxxxxx postfix/smtpd[1394]: warning: rogers-network.ca[xxxxxxx]: SASL PLAIN authentication failed: authentication failureOkay, so the authentication is definitely failing (as suspected).

Presumably you didn't build this yourself from scratch - did you follow a HowTo? If so, which one? And have you double-checked every step from it? Were there are testing procedures in it?

Mathew

P.S. Please don't obfuscate your log files - you risk hiding the cause of the problem and we're not paid to run around in the dark.

---

### Post by genesimmons4201 on 2008-11-19
kinda of given or ask to complete this project for a client. I have setup a few ubuntu servers 7.10 and one 8.04 using

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p6](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p6)

The 7.10 servers where similar setup's using 

[http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10-p3](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10-p3)

I was considering removing all the mail packages on the server and starting over but they are currently using it since I corrected squirrelmail issues and https so they have secure login that way.

Thanks for the help.....inspiration to give back to the community since I'm currently in the middle of my ubuntu training online and a few other unix courses.

Chris

---

