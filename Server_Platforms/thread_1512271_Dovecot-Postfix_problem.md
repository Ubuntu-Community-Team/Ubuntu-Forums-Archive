---
title: "Dovecot-Postfix problem"
date: 2010-06-17
forum: Server Platforms
---

### Post by sbin on 2010-06-17
I have a fresh install of Ubuntu 10.04 server (amd64), with Postfix and dovecot-postfix configured as per this Ubuntu/Postfix documentation: [https://help.ubuntu.com/10.04/serverguide/C/postfix.html](https://help.ubuntu.com/10.04/serverguide/C/postfix.html)  
I can receive email from a remote MTA, but cannot reply. Using Evolution to send an email from the client, "mail.menardsystems.com" to the new server "white.menardsystems.com," gives me the following:

[COLOR=Blue]**root@white:/var/log# tail -f  mail.log**
[/COLOR][COLOR=Blue]Jun 17 19:31:52 white postfix/smtpd[7038]: connect from mail.menardsystems.com[99.2.135.19]
[/COLOR][COLOR=Blue]Jun 17 19:31:52 white postfix/smtpd[7038]: lost connection after STARTTLS from mail.menardsystems.com[99.2.135.19]
[/COLOR][COLOR=Blue]Jun 17 19:31:52 white postfix/cleanup[7037]: CDA20B01214: message-id=<20100618023152.CDA20B01214@white.menardsystems.com>
[/COLOR][COLOR=Blue]Jun 17 19:31:52 white postfix/smtpd[7038]: disconnect from mail.menardsystems.com[99.2.135.19]
[/COLOR][COLOR=Blue]Jun 17 19:31:52 white postfix/qmgr[6787]: CDA20B01214: from=<double-bounce@white.menardsystems.com>, size=895, nrcpt=1 (queue active)
[/COLOR][COLOR=Blue]Jun 17 19:31:52 white dovecot: deliver(root): chdir(/root) failed: Permission denied
[/COLOR][COLOR=Blue]Jun 17 19:31:52 white dovecot: deliver(root): sieve: stat(/root/.dovecot.sieve) failed: Permission denied (using global script path in stead)
[/COLOR][COLOR=Blue]Jun 17 19:31:52 white dovecot: deliver(root): stat(/root/Maildir) failed: Permission denied
[/COLOR][COLOR=Blue]Jun 17 19:31:52 white dovecot: deliver(root): stat(/root/Maildir/tmp) failed: Permission denied (euid=65534(nobody) egid=65534(nogroup) missing +x perm: /root)
[/COLOR][COLOR=Blue]Jun 17 19:31:52 white dovecot: deliver(root): msgid=<20100618023152.CDA20B01214@white.menardsystems.com>: save failed to INBOX: Internal error occurred. Refer to server log for more information. [2010-06-17 19:31:52]
[/COLOR][COLOR=Blue]Jun 17 19:31:52 white postfix/local[7039]: CDA20B01214: to=<root@menardsystems.com>, orig_to=<postmaster>, relay=local, delay=0.09, delays=0.04/0/0/0.05, dsn=4.3.0, status=deferred (temporary failure)
[/COLOR]
[COLOR=Black]I'm guessing that the problem may be related to the default for Postfix to run chrooted, but I don't really understand why a default installation would be problematic. Any help here or a recommendation[/COLOR] for a more suitable forum will be appreciated.

Thanks in advance, Mark

---

### Post by Bachstelze on 2010-06-18
> **sbin said:**
> 
[/COLOR][COLOR=Blue]Jun 17 19:31:52 white dovecot: deliver(root): chdir(/root) failed: Permission denied
[/COLOR][COLOR=Blue]Jun 17 19:31:52 white dovecot: deliver(root): sieve: stat(/root/.dovecot.sieve) failed: Permission denied (using global script path in stead)
[/COLOR][COLOR=Blue]Jun 17 19:31:52 white dovecot: deliver(root): stat(/root/Maildir) failed: Permission denied
[/COLOR][COLOR=Blue]Jun 17 19:31:52 white dovecot: deliver(root): stat(/root/Maildir/tmp) failed: Permission denied (euid=65534(nobody) egid=65534(nogroup) missing +x perm: /root)

The problem is that you're sending mail to root, and dovecot doesn't have permission to access root's home directory, which is why it is unable to deliver your mail. Fix: setup an alias to have mail sent to root delivered to your normal user account. *Do not* open root's home dir permissions.

---

### Post by sbin on 2010-06-18
Bachstelze: Thank you. I created an alias for root's mail and it is now being delivered. Now I just need to address the problem of sending email:

   [SIZE=2]**root@white:/var/log# tail -n 2 mail.log |less**[/SIZE]
  [SIZE=2][COLOR=Blue]Jun 18 09:25:21 white postfix/smtpd[4281]: NOQUEUE: reject: RCPT from .....<mark.menard@sbcglobal.net>: Relay access denied; from=<mark@menardsystems.com> to=<mark.menard@sbcglobal.net> proto=ESMTP helo=<[129.65.198.114]>[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]Jun 18 09:25:21 white postfix/smtpd[4281]: disconnect from ......[/COLOR][/SIZE]
  
[COLOR=Black]Here is my Postfix configuration:

[/COLOR]    [SIZE=2][COLOR=Blue]**[COLOR=Black]root@white:/var/log# postconf -n[/COLOR]**[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]alias_database = hash:/etc/aliases[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]alias_maps = hash:/etc/aliases[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]append_dot_mydomain = no[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]biff = no[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]broken_sasl_auth_clients = yes[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]config_directory = /etc/postfix[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]home_mailbox = Maildir/[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]inet_interfaces = all[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]inet_protocols = all[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-dovecot-postfix.conf -n -m "${EXTENSION}"[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]mailbox_size_limit = 0[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]mydestination = menardsystems.com, white.menardsystems.com, localhost.menardsystems.com, localhost[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]myhostname = white.menardsystems.com[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.0.0/24[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]myorigin = /etc/mailname[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]readme_directory = no[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]recipient_delimiter = +[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]relayhost =[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]smtp_tls_note_starttls_offer = yes[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]smtp_use_tls = yes[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]smtpd_sasl_auth_enable = yes[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]smtpd_sasl_authenticated_header = yes[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]smtpd_sasl_local_domain = $myhostname[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]smtpd_sasl_path = private/dovecot-auth[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]smtpd_sasl_security_options = noanonymous[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]smtpd_sasl_type = dovecot[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]smtpd_sender_restrictions = reject_unknown_sender_domain[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]smtpd_tls_auth_only = yes[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]smtpd_tls_cert_file = /etc/ssl/certs/ssl-mail.pem[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]smtpd_tls_key_file = /etc/ssl/private/ssl-mail.key[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]smtpd_tls_loglevel = 1[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]smtpd_tls_mandatory_ciphers = medium[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]smtpd_tls_mandatory_protocols = SSLv3, TLSv1[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]smtpd_tls_received_header = yes[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]smtpd_tls_session_cache_timeout = 3600s[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]smtpd_use_tls = yes[/COLOR][/SIZE]
  [SIZE=2][COLOR=Blue]tls_random_source = dev:/dev/urandom[/COLOR][/SIZE]
  
[COLOR=Black]Any suggestions?

Thanks, Mark
[/COLOR]

---

### Post by noway2 on 2010-06-18
You appear to have an authentication issue.  The message "reject: RCPT from .....<mark.menard@sbcglobal.net>" provides a clue.

The login or identification of FROM was [email]mark.menard@sbcglobal.net[/email], however your email server thinks it is:white.menardsystems.com, with localhost and 192.168.x.x for its networks.  Since the originating mail was from outside the network (sbcglobal.net) AND the recipient is not one of the local destinations, it thinks you are trying to use it as a relay which you DO want to avoid because this is one technique used by spammers.

I assume that you don't want to host mail for sbcglobal.net, so you need to use a user that is authenticated on the system as the from.

---

### Post by sbin on 2010-06-18
:pMy email client wasn't properly configured. Now it is and everything works. Many thanks!

---

