---
title: "SASL postfix mysql AUTH issues"
date: 2008-10-27
forum: Server Platforms
---

### Post by FawnOfFeist on 2008-10-27
I am having an issue being able to authenticate.  I am using Ubuntu with Postfix, SASL and mysql.  Squirrelmail can send out without an issue, pop can connect with no issue, but when sending from a mail client it will never accept the username/password.

For some reason it looks like it is still trying to use the salsdb.

Below are the errors:

Oct 27 14:52:20 AlbPostFix02 postfix/smtpd[4517]: warning: SASL authentication failure: no secret in database

Oct 27 14:52:20 AlbPostFix02 postfix/smtpd[4517]: warning: static-72-10-196-48.albyny.csvoip.net[72.10.196.48]: SASL NTLM authentication failed: authentication failure

Oct 27 14:52:20 AlbPostFix02 postfix/smtpd[4517]: warning: SASL authentication failure: realm changed: authentication aborted

Oct 27 14:52:20 AlbPostFix02 postfix/smtpd[4517]: warning: static-72-10-196-48.albyny.csvoip.net[72.10.196.48]: SASL DIGEST-MD5 authentication failed: authentication failure

Oct 27 14:52:20 AlbPostFix02 postfix/smtpd[4517]: warning: static-72-10-196-48.albyny.csvoip.net[72.10.196.48]: SASL LOGIN authentication failed: authentication failure


Here is my smtpd.conf

pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: plain login cram-md5 digest-md5
sql_engine: mysql
sql_hostnames: localhost
sql_user: mail1234
sql_passwd: mail1234
sql_database: mailpostfix
sql_select: select crypt from users where id='%u@%r' and enabled = 1

Here is postconf:

root@GHTYPostFix:/home/dat# postconf -n
alias_database = hash:/etc/postfix/aliases
alias_maps = hash:/etc/postfix/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
delay_warning_time = 4h
disable_vrfy_command = yes
html_directory = /usr/share/doc/postfix/html
inet_interfaces = all
local_recipient_maps =
mailbox_size_limit = 0
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
mydestination =
myhostname = GHTYpostfix.domain.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = domain.com
readme_directory = /usr/share/doc/postfix
recipient_delimiter = +
relayhost =
smtp_helo_timeout = 60s
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject, reject_invalid_hostname, permit
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unauth_destination, permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous
smtpd_sender_restrictions = permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_soft_error_limit = 3
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf


If you need any other info to tell me what I am doing wrong here, please let me know.  I am assuming that if I have it set to auxprop it should not be asking to try the secret in database.

---

### Post by FawnOfFeist on 2008-10-28
Anyone have any ideas on this?  SASL authentication is still looking to the sasldb it seems for some reason

---

### Post by kvn290 on 2008-11-08
I've been battling some problems with SASL authentication myself, and have become fairly familiar with it....but I'm by no means an expert yet.  

My two cents....the first problem is "auxprop" instead of "saslauthd" in your smtpd.conf file.

This brings into play the saslauthd daemon.  Did you install sasl2-bin?  If yes, there is some configuration to do on that end as well.

Chroot'd postfix causes other problems as well...

Bottom line...you probably have a lot to configuring to do still.  I know it was quite a while before I had my server running.  This is not easy, but try the above and post the error logs.  Hopefully we can get you through this fairly quickly.

---

### Post by carlosgarciaq on 2008-12-15
Hi, 

 I am having exactly the same problem as you do... Did you solve this problem?

It is trying to connect to Berkeley DB... and as in your case (and many others in other forums) it also says: 

Dec 15 13:02:43 Thor postfix/smtpd[9626]: warning: SASL authentication failure: realm changed: authentication aborted

which I would like to know what it means and why it happens?? any clue?

postfix is also running chrooted (ubuntu 8..)


*** my /etc/postfix/sasl/smtpd.conf

pwcheck_method: saslauthd
auxprop_plugin: sql
mech_list: plain login cram-md5 digest-md5
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: mail
sql_passwd: MYPASSWORD
sql_database: maildb
sql_select: select clear from users where id='%u@%r' and enabled = 1

*** my /etc/postfix/main.cf


# Requirements for the HELO statement
smtpd_helo_restrictions = permit_mynetworks, reject_invalid_hostname, permit
#smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
# Requirements for the sender details
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domai
n, reject_unauth_pipelining, permit
# Requirements for the connecting server
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dn
sbl.njabl.org
# Requirement for the recipient address
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipi
ent, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit
smtpd_data_restrictions = reject_unauth_pipelining

# require proper helo at connections
smtpd_helo_required = yes
# waste spammers time before rejecting them
smtpd_delay_reject = yes
disable_vrfy_command = yes

# not sure of the difference of the next two
# but they are needed for local aliasing
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
# this specifies where the virtual mailbox folders will be located
virtual_mailbox_base = /var/spool/mail/virtual
# this is for the mailbox location for each user
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
# and their user id
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
# and group id
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
# and this is for aliases
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
# and this is for domain lookups
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
# this is how to connect to the domains (all virtual, but the option is there)
# not used yet
# transport_maps = mysql:/etc/postfix/mysql_transport.cf
#content_filter = amavis:[127.0.0.1]:10024

smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =

*** my syslog:

Dec 15 13:02:42 Thor postfix/smtpd[9626]: > 51.Red-83-58-236.dynamicIP.rima-tde.net[83.58.236.51]: 220 Thor ESMTP Postfix (Ubuntu)
Dec 15 13:02:43 Thor postfix/smtpd[9626]: < 51.Red-83-58-236.dynamicIP.rima-tde.net[83.58.236.51]: EHLO Aquiles
Dec 15 13:02:43 Thor postfix/smtpd[9626]: > 51.Red-83-58-236.dynamicIP.rima-tde.net[83.58.236.51]: 250-Thor
Dec 15 13:02:43 Thor postfix/smtpd[9626]: > 51.Red-83-58-236.dynamicIP.rima-tde.net[83.58.236.51]: 250-PIPELINING
Dec 15 13:02:43 Thor postfix/smtpd[9626]: > 51.Red-83-58-236.dynamicIP.rima-tde.net[83.58.236.51]: 250-SIZE 10240000
Dec 15 13:02:43 Thor postfix/smtpd[9626]: > 51.Red-83-58-236.dynamicIP.rima-tde.net[83.58.236.51]: 250-ETRN
Dec 15 13:02:43 Thor postfix/smtpd[9626]: > 51.Red-83-58-236.dynamicIP.rima-tde.net[83.58.236.51]: 250-AUTH PLAIN NTLM CRAM-MD5 DIGEST-MD5 LOGIN
Dec 15 13:02:43 Thor postfix/smtpd[9626]: match_list_match: 51.Red-83-58-236.dynamicIP.rima-tde.net: no match
Dec 15 13:02:43 Thor postfix/smtpd[9626]: match_list_match: 83.58.236.51: no match
Dec 15 13:02:43 Thor postfix/smtpd[9626]: > 51.Red-83-58-236.dynamicIP.rima-tde.net[83.58.236.51]: 250-AUTH=PLAIN NTLM CRAM-MD5 DIGEST-MD5 LOGIN
Dec 15 13:02:43 Thor postfix/smtpd[9626]: > 51.Red-83-58-236.dynamicIP.rima-tde.net[83.58.236.51]: 250-ENHANCEDSTATUSCODES
Dec 15 13:02:43 Thor postfix/smtpd[9626]: > 51.Red-83-58-236.dynamicIP.rima-tde.net[83.58.236.51]: 250-8BITMIME
Dec 15 13:02:43 Thor postfix/smtpd[9626]: > 51.Red-83-58-236.dynamicIP.rima-tde.net[83.58.236.51]: 250 DSN
Dec 15 13:02:43 Thor postfix/smtpd[9626]: < 51.Red-83-58-236.dynamicIP.rima-tde.net[83.58.236.51]: AUTH NTLM
Dec 15 13:02:43 Thor postfix/smtpd[9626]: xsasl_cyrus_server_first: sasl_method NTLM
Dec 15 13:02:43 Thor postfix/smtpd[9626]: xsasl_cyrus_server_auth_response: uncoded server challenge:
Dec 15 13:02:43 Thor postfix/smtpd[9626]: > 51.Red-83-58-236.dynamicIP.rima-tde.net[83.58.236.51]: 334
Dec 15 13:02:43 Thor postfix/smtpd[9626]: < 51.Red-83-58-236.dynamicIP.rima-tde.net[83.58.236.51]: TlRMTVNTUAABAAAAB4IIogAAAAAAAAAAAAAAAAAAAAAGAHEXAAAADw==
Dec 15 13:02:43 Thor postfix/smtpd[9626]: xsasl_cyrus_server_next: decoded response: NTLMSSP
Dec 15 13:02:43 Thor postfix/smtpd[9626]: xsasl_cyrus_server_auth_response: uncoded server challenge: NTLMSSP
Dec 15 13:02:43 Thor postfix/smtpd[9626]: > 51.Red-83-58-236.dynamicIP.rima-tde.net[83.58.236.51]: 334 TlRMTVNTUAACAAAACAAIADAAAAAFggIAv0hNPra54VoAAAAAAAAAAAAAAAAAAAAAVABIAE8AUgA=
Dec 15 13:02:43 Thor postfix/smtpd[9626]: < 51.Red-83-58-236.dynamicIP.rima-tde.net[83.58.236.51]: TlRMTVNTUAADAAAAGAAYAIQAAABAAEAAnAAAABIAEgBYAAAADAAMAGoAAAAOAA4AdgAAAAAAAADcAAAABYIAAgYAcRcAAAAPq6PKQOZx1nOiSmi37GgnFm0AaQBvAGMAYQAuAG4AZQB0AGMAYQByAGwAbwBzAEEAUQBVAEkATABFAFMA10gEMxntkBM+JEDX1nhahL/VOIakmWf9+NK6bSVv1VZwRZhWh63K0QEBAAAAAAAAIrEc+qxeyQG/1TiGpJln/QAAAAACAAgAVABIAE8AUgAAAAAAAAAAAA==
Dec 15 13:02:43 Thor postfix/smtpd[9626]: xsasl_cyrus_server_next: decoded response: NTLMSSP
Dec 15 13:02:43 Thor postfix/smtpd[9626]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: Permission denied
Dec 15 13:02:43 Thor postfix/smtpd[9626]: warning: SASL authentication failure: no secret in database
Dec 15 13:02:43 Thor postfix/smtpd[9626]: warning: 51.Red-83-58-236.dynamicIP.rima-tde.net[83.58.236.51]: SASL NTLM authentication failed: authentication failure
Dec 15 13:02:43 Thor postfix/smtpd[9626]: > 51.Red-83-58-236.dynamicIP.rima-tde.net[83.58.236.51]: 535 5.7.8 Error: authentication failed: authentication failure
Dec 15 13:02:43 Thor postfix/smtpd[9626]: < 51.Red-83-58-236.dynamicIP.rima-tde.net[83.58.236.51]: AUTH DIGEST-MD5
Dec 15 13:02:43 Thor postfix/smtpd[9626]: xsasl_cyrus_server_first: sasl_method DIGEST-MD5
Dec 15 13:02:43 Thor postfix/smtpd[9626]: xsasl_cyrus_server_auth_response: uncoded server challenge: nonce="wcy2DKd/hAcO9RPL9BP0q19VuJHZpttao0r7H8RCCL8=",realm="Thor",qop="auth",charset=utf-8,algorithm=md5-sess
Dec 15 13:02:43 Thor postfix/smtpd[9626]: > 51.Red-83-58-236.dynamicIP.rima-tde.net[83.58.236.51]: 334 bm9uY2U9IndjeTJES2QvaEFjTzlSUEw5QlAwcTE5VnVKSFpwdHRhbzByN0g4UkNDTDg9IixyZWFsbT0iVGhvciIscW9wPSJhdXRoIixjaGFyc2V0PXV0Zi04LGFsZ29yaXRobT1tZDUtc2Vzcw==
Dec 15 13:02:43 Thor postfix/smtpd[9626]: < 51.Red-83-58-236.dynamicIP.rima-tde.net[83.58.236.51]: dXNlcm5hbWU9ImNhcmxvcyIscmVhbG09Im1pb2NhLm5ldCIsbm9uY2U9IndjeTJES2QvaEFjTzlSUEw5QlAwcTE5VnVKSFpwdHRhbzByN0g4UkNDTDg9IixkaWdlc3QtdXJpPSJzbXRwL3NtdHAubWlvY2EubmV0Iixjbm9uY2U9IjdjNTFmN2ZmNjIwMjMyMDhkYTQ3YmU0ZmQ2MWEzNDUxIixuYz0wMDAwMDAwMSxyZXNwb25zZT0zMTlhODM1NTk5NmZkNWQ3ZjViZjliODM0NDVmNTIxYSxxb3A9YXV0aCxjaGFyc2V0PXV0Zi04
Dec 15 13:02:43 Thor postfix/smtpd[9626]: xsasl_cyrus_server_next: decoded response: username="carlos",realm="mioca.net",nonce="wcy2DKd/hAcO9RPL9BP0q19VuJHZpttao0r7H8RCCL8=",digest-uri="smtp/smtp.mioca.net",cnonce="7c51f7ff62023208da47be4fd61a3451",nc=00000001,response=319a8355996fd5d7f5bf9b83445f521a,qop=auth,charset=utf-8
Dec 15 13:02:43 Thor postfix/smtpd[9626]: warning: SASL authentication failure: realm changed: authentication aborted
Dec 15 13:02:43 Thor postfix/smtpd[9626]: warning: 51.Red-83-58-236.dynamicIP.rima-tde.net[83.58.236.51]: SASL DIGEST-MD5 authentication failed: authentication failure
Dec 15 13:02:43 Thor postfix/smtpd[9626]: > 51.Red-83-58-236.dynamicIP.rima-tde.net[83.58.236.51]: 535 5.7.8 Error: authentication failed: authentication failure
Dec 15 13:02:43 Thor postfix/smtpd[9626]: smtp_get: EOF
Dec 15 13:02:43 Thor postfix/smtpd[9626]: match_hostname: 51.Red-83-58-236.dynamicIP.rima-tde.net ~? 192.168.1.0/24
Dec 15 13:02:43 Thor postfix/smtpd[9626]: match_hostaddr: 83.58.236.51 ~? 192.168.1.0/24
Dec 15 13:02:43 Thor postfix/smtpd[9626]: match_hostname: 51.Red-83-58-236.dynamicIP.rima-tde.net ~? 127.0.0.0/8
Dec 15 13:02:43 Thor postfix/smtpd[9626]: match_hostaddr: 83.58.236.51 ~? 127.0.0.0/8
Dec 15 13:02:43 Thor postfix/smtpd[9626]: match_hostname: 51.Red-83-58-236.dynamicIP.rima-tde.net ~? [::ffff:127.0.0.0]/104
Dec 15 13:02:43 Thor postfix/smtpd[9626]: match_hostaddr: 83.58.236.51 ~? [::ffff:127.0.0.0]/104
Dec 15 13:02:43 Thor postfix/smtpd[9626]: match_hostname: 51.Red-83-58-236.dynamicIP.rima-tde.net ~? [::1]/128
Dec 15 13:02:43 Thor postfix/smtpd[9626]: match_hostaddr: 83.58.236.51 ~? [::1]/128
Dec 15 13:02:43 Thor postfix/smtpd[9626]: match_list_match: 51.Red-83-58-236.dynamicIP.rima-tde.net: no match
Dec 15 13:02:43 Thor postfix/smtpd[9626]: match_list_match: 83.58.236.51: no match
Dec 15 13:02:43 Thor postfix/smtpd[9626]: send attr request = disconnect
Dec 15 13:02:43 Thor postfix/smtpd[9626]: send attr ident = smtp:83.58.236.51
Dec 15 13:02:43 Thor postfix/smtpd[9626]: private/anvil: wanted attribute: status
Dec 15 13:02:43 Thor postfix/smtpd[9626]: input attribute name: status
Dec 15 13:02:43 Thor postfix/smtpd[9626]: input attribute value: 0
Dec 15 13:02:43 Thor postfix/smtpd[9626]: private/anvil: wanted attribute: (list terminator)
Dec 15 13:02:43 Thor postfix/smtpd[9626]: input attribute name: (end)
Dec 15 13:02:43 Thor postfix/smtpd[9626]: lost connection after AUTH from 51.Red-83-58-236.dynamicIP.rima-tde.net[83.58.236.51]
Dec 15 13:02:43 Thor postfix/smtpd[9626]: disconnect from 51.Red-83-58-236.dynamicIP.rima-tde.net[83.58.236.51]
Dec 15 13:02:43 Thor postfix/smtpd[9626]: master_notify: status 1
Dec 15 13:02:43 Thor postfix/smtpd[9626]: connection closed

---

### Post by FawnOfFeist on 2008-12-18
Never found an answer to what was not working.  Eventually followed the instructions on HowToForge.com.  Here is the 8.10 Ubuntu how to: [http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.10](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.10)

Worked very well, and the forum there can help you with any questions you do have about the howto.

---

