---
title: "Unable to redirect mail from account to account with Postfix"
date: 2016-11-30
forum: Ubuntu Cloud and Juju
---

### Post by fabioescabrita on 2016-11-30
I have read a lot of tutorials on how to do this but still nothing trying just to redirect from A to B.

Right now i am using at main.cf:

> #virtual_alias_domains = $virtual_alias_maps
virtual_alias_domains = X.pt
#virtual_alias_maps = $virtual_maps
virtual_alias_maps = hash:/Library/Server/Mail/Config/postfix/virtual_maps/virtual

And in virtual i have:

> [EMAIL="teste@X.pt"]teste@X.pt[/EMAIL] [EMAIL="teste2@X.pt"]teste2@X.pt[/EMAIL]

After doing changes at this file i do,

> postmap virtual
postfix reload

and nothing, all mails continues to go to A and not being forward to B.

I already was able to redirect one mail, but i just notice after changing both files several times.

Anyone know what i am doing wrong?

---

### Post by TheFu on 2016-11-30
Always check the log files first. A-L-W-A-Y-S.  Issues with the config will likely be seen there.

Post **postconf -n** please. Use "code tags" so things line up, not "quote tags." We can't tell about issues with 2 lines snipped from a file that is highly dependent on everything in the file.

Do the exact locations exist as specified in the config?   /Library/Server/Mail/Config/postfix/virtual_maps/virtual  is NOT standard.

Or just use /etc/aliases.

---

### Post by fabioescabrita on 2016-11-30
Thanks for the reply TheFu

I know, i have check my mail.log but i didnt find anything relevant for this problem =/ And since is something so simple that i was wondering if could be from a syntax error, or a left entry.

Also i didnt find any code tags in this forum edit bar.

remote:~ root# postconf -n
biff = no
command_directory = /usr/sbin
config_directory = /Library/Server/Mail/Config/postfix
daemon_directory = /usr/libexec/postfix
data_directory = /Library/Server/Mail/Data/mta
debug_peer_level = 2
debugger_command = PATH=/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin xxgdb $daemon_directory/$process_name $process_id & sleep 5
dovecot_destination_recipient_limit = 1
html_directory = /usr/share/doc/postfix/html
imap_submit_cred_file = /Library/Server/Mail/Config/postfix/submit.cred
inet_interfaces = all
inet_protocols = all
mail_owner = _postfix
mailbox_size_limit = 0
mailq_path = /usr/bin/mailq
manpage_directory = /usr/share/man
message_size_limit = 10485760
mydomain_fallback = localhost
mynetworks = 127.0.0.0/8, [::1]/128
newaliases_path = /usr/bin/newaliases
queue_directory = /Library/Server/Mail/Data/spool
readme_directory = /usr/share/doc/postfix
recipient_delimiter = +
sample_directory = /usr/share/doc/postfix/examples
sendmail_path = /usr/sbin/sendmail
setgid_group = _postdrop
smtpd_client_restrictions = permit_mynetworks permit_sasl_authenticated permit
smtpd_tls_ciphers = medium
smtpd_tls_exclude_ciphers = SSLv2, aNULL, ADH, eNULL
tls_random_source = dev:/dev/urandom
unknown_local_recipient_reject_code = 550
use_sacl_cache = yes

That location is where i have all my config files is not a standard path but i have a smart host set there working perfectly, as you can see here in the main.cf from the default location:

config_directory = /Library/Server/Mail/Config/postfix

If you need any further data just say it.

---

### Post by TheFu on 2016-11-30
"Adv Reply"

That postconf -n output doesn't show **any** virtual* in it. Not being picked up or am I just missing something basic?

---

### Post by fabioescabrita on 2016-11-30
Thanks TheFu.

I totally forgot that one is the default main.cf, sorry, in the one where i had the configurations i have this:

```
# dovecot
dovecot_destination_recipient_limit = 1


# default mailbox size limit set to no limit
mailbox_size_limit = 0


# List of ciphers or cipher types to exclude from the SMTP server cipher
# list at all TLS security levels.
smtpd_tls_exclude_ciphers = SSLv2, aNULL, ADH, eNULL


# Protect SSL/TLS encryption keys
tls_random_source = dev:/dev/urandom


# Credentials for using URLAUTH with IMAP servers.
imap_submit_cred_file = /Library/Server/Mail/Config/postfix/submit.cred


# The SACL cache caches the results of Mail Service ACL lookups.
# Tune these to make the cache more responsive to changes in the SACL.
# The cache is only in memory, so bouncing the sacl-cache service clears it.
use_sacl_cache = yes
# sacl_cache_positive_expire_time = 7d
# sacl_cache_negative_expire_time = 1d
# sacl_cache_disabled_expire_time = 1m


# Reject messages having any MIME body part (attachment, etc.)
# larger than this number of bytes.  0, the default, means no limit.
# mime_max_body_size = 0
#======================================================================
mydomain_fallback = localhost
message_size_limit = 0
biff = no
mynetworks_style = subnet # was only seen by localhost


mynetworks = 127.0.0.0/8, [::1]/128
#mynetworks = 127.0.0.0/8, 192.168.1.0/24 
#mynetworks = 127.0.0.0/8, a.b.c.d/e
# To receive mail from all addresses
#mynetworks = 0.0.0.0/0 


smtpd_client_restrictions = permit_mynetworks permit_sasl_authenticated permit
recipient_delimiter = +
smtpd_tls_ciphers = medium
inet_protocols = all
inet_interfaces = all
config_directory = /Library/Server/Mail/Config/postfix


#virtual_alias_domains = $virtual_alias_maps
virtual_alias_domains = X.pt  
#virtual_alias_maps = $virtual_maps
virtual_alias_maps = hash:/Library/Server/Mail/Config/postfix/virtual_maps/virtual


recipient_canonical_maps = hash:/Library/Server/Mail/Config/postfix/system_user_maps
smtpd_enforce_tls = no
smtpd_use_pw_server = yes


relayhost = [mail.X.pt]:25
smtp_fallback_relay = [cpanel.X.pt]:25


smtpd_tls_cert_file = /etc/certificates/remote.X.pt.C95BB01447DFD2F06F3EBA88DCB9E0D66DFB6D40.cert.pem
mydomain = X.pt
smtpd_pw_server_security_options = cram-md5,digest-md5,gssapi,plain
smtpd_sasl_auth_enable = yes
smtpd_helo_required = yes
smtpd_tls_CAfile = /etc/certificates/remote.X.pt.C95BB01447DFD2F06F3EBA88DCB9E0D66DFB6D40.chain.pem
content_filter = smtp-amavis:[127.0.0.1]:10024
smtpd_recipient_restrictions = permit_sasl_authenticated permit_mynetworks reject_unauth_destination
header_checks = pcre:/Library/Server/Mail/Config/postfix/custom_header_checks
myhostname = remote.X.pt
#smtpd_helo_restrictions = reject_non_fqdn_helo_hostname reject_invalid_helo_hostname
smtpd_helo_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_invalid_hostname, permit
smtpd_use_tls = yes
smtpd_tls_key_file = /etc/certificates/remote.X.pt.C95BB01447DFD2F06F3EBA88DCB9E0D66DFB6D40.key.pem
enable_server_options = yes
mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain, X.pt
mailbox_transport = dovecot


######Edit######


smtp_sasl_security_options =
smtp_sasl_auth_enable = yes


smtp_sender_dependent_authentication = yes


#Per-sender authentication
smtp_sasl_password_maps = hash:/Library/Server/Mail/Config/postfix/sasl/passwd


#Per-sender provider
sender_dependent_relayhost_maps = hash:/Library/Server/Mail/Config/postfix/relayhost/maps

```

---

### Post by SeijiSensei on 2016-11-30
Another vote for /etc/aliases.

---

### Post by TheFu on 2016-11-30
Er ... read that you shouldn't have the same values in mydestination and virtual_alias_domains. There should be a warning in the log files about that. [https://www.mind-it.info/2013/10/23/setting-virtual-alias-domains-correctly-postfix/](https://www.mind-it.info/2013/10/23/setting-virtual-alias-domains-correctly-postfix/)

If that isn't it, need to find a way to get postconf to merge all the config files and post those. Seeing partial files just doesn't work for me and we really need to see what postfix actually sees, not source files.  That was the point of asking for postconf output. Sorry, I don't know how to merge them.

---

### Post by fabioescabrita on 2016-12-02
I was finally able to know what was the problem that was causing this, and it was not easy because it was as i expected before a syntax error. So without a compiler this just turn a big nightmare .... and since i have not read this anywhere i will let here how i have managed that.

Till now i was using just spaces between input arguments in all files within postfix, and i discover in virtual_alias_maps file that i was using, that i should use TABs instead of spaces. And it was one day lost because of this ... i hope that my thread could help any one who may need.

Thanks for the help TheFu and SeijiSensei!

---

### Post by TheFu on 2016-12-02
Thanks for the resolution. Please mark this thread as SOLVED to help others. See thread tools button near the top.

---

### Post by fabioescabrita on 2016-12-06
To anyone who may read this thread:

Just to be clear, those accounts where local mail users, not virtual mail users, but virtual_alias_maps can handle with both. 

To use just with local mail users, it can be done with file *aliases*, and then *newaliases. *But here you must see where your alias_maps is pointing. By default is in /etc/aliases.The syntax that must be used there is:user1: [email]user2@domainX.com[/email] [email]user3@domainX.com[/email]

---

