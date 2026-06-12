---
title: "SASL in Hardy"
date: 2008-06-12
forum: Server Platforms
---

### Post by graylion on 2008-06-12
Hi guys

I have just migrated a perfectly well working mailserver from Gutsy to Hardy and it is misbehaving rather badly:

I cannot login to my IMAP server (cyrus with saslauthd via ldap)

auth.log gives me:

Jun 12 19:05:02 collab cyrus/imap[9304]: auxpropfunc error invalid parameter supplied
Jun 12 19:05:02 collab cyrus/imap[9304]: _sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: ldapdb
Jun 12 19:06:10 collab postfix/smtpd[9306]: auxpropfunc error invalid parameter supplied
Jun 12 19:06:10 collab postfix/smtpd[9306]: _sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: ldapdb
Jun 12 19:06:21 collab postfix/smtpd[9309]: auxpropfunc error invalid parameter supplied
Jun 12 19:06:21 collab postfix/smtpd[9309]: _sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: ldapdb
Jun 12 19:06:22 collab cyrus/lmtpunix[9312]: auxpropfunc error invalid parameter supplied
Jun 12 19:06:22 collab cyrus/lmtpunix[9312]: _sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: ldapdb

now the stoopid thing is that I have auxprop defined nowhere! I did a grep across all relevant parts of the FS (/etc and /usr) which confirmed that.

/etc/default/saslauthd looks like this:

#
# Settings for saslauthd daemon
#

# Should saslauthd run automatically on startup? (default: no)
START=yes

# Which authentication mechanisms should saslauthd use? (default: pam)
#
# Available options in this Debian package:
# getpwent  -- use the getpwent() library function
# kerberos5 -- use Kerberos 5
# pam       -- use PAM
# rimap     -- use a remote IMAP server
# shadow    -- use the local shadow password file
# sasldb    -- use the local sasldb database file
# ldap      -- use LDAP (configuration is in /etc/saslauthd.conf)
#
# Only one option may be used at a time. See the saslauthd man page
# for more information.
#
# Example: MECHANISMS="pam"
MECHANISMS="ldap"

# Additional options for this mechanism. (default: none)
# See the saslauthd man page for information about mech-specific options.
MECH_OPTIONS=""

# How many saslauthd processes should we run? (default: 5)
# A value of 0 will fork a new process for each connection.
THREADS=5

# Other options (default: -c)
# See the saslauthd man page for information about these options.
#
# Example for postfix users: "-c -m /var/spool/postfix/var/run/saslauthd"
# Note: See /usr/share/doc/sasl2-bin/README.Debian
OPTIONS="-c -m /var/spool/postfix/var/run/saslauthd"
NAME="saslauthd-postfix"
DESC="der fuer postfix"

/etc/saslauthd.conf looks like this:

ldap_servers: ldap://localhost:389/
ldap_search_base: ou=dddddddd,dc=fffffffffff,dc=ssssssssss
ldap_version: 3
ldap_timeout: 10
ldap_time_limit: 10
ldap_cache_ttl: 30
ldap_cache_mem: 32768
ldap_scope: sub
ldap_auth_method: bind
ldap_bind_dn: cn=aaaaaa,dc=ccccccc,dc=ffffffff
ldap_password: xxxxxxxxxxx
ldap_filter: uid=%U
ldap_mech: PLAIN DIGEST-MD5


/etc/postfix/sasl/smtpd.conf

pwcheck_method: saslauthd
saslauthd_path: /var/run/saslauthd
mech_list: plain login
allow_plaintext: true
ldap_sasl: 1
ldap_servers: ldap://localhost/
ldap_base: dc=graylion,dc=net
ldap_group_base: ou=groups,dc=graylion,dc=net
ldap_group_filter: cn=%U
ldap_member_filter: dn=%U
ldap_group_scope: sub
ldap_member_method: filter

the next thing is that these error messages nonwithstanding postfix and lmtp can clearly connect to ldap and lookup the aliases, only for lmtp then to define every message as duplicate and to delete it:

Jun 12 19:14:31 collab postgrey[5257]: action=pass, reason=triplet found, client_name=russian-caravan.cloud9.net, client_address=168$
Jun 12 19:14:31 collab postfix/smtpd[9360]: connect from localhost[127.0.0.1]
Jun 12 19:14:31 collab postfix/smtpd[9371]: NOQUEUE: client=russian-caravan.cloud9.net[168.100.1.4]
Jun 12 19:14:31 collab postfix/smtpd[9360]: C13F4180C53: client=russian-caravan.cloud9.net[168.100.1.4]:61309
Jun 12 19:14:32 collab dkimproxy.in[5147]: DKIM verify - invalid (no public key available); message-id=<48516738.2020108@megan.vbhcs$
Jun 12 19:14:32 collab postfix/cleanup[9361]: C13F4180C53: message-id=<48516738.2020108@megan.vbhcs.org>
Jun 12 19:14:32 collab postfix/qmgr[5461]: C13F4180C53: from=<owner-postfix-users@postfix.org>, size=4841, nrcpt=1 (queue active)
Jun 12 19:14:32 collab postfix/smtpd[9360]: disconnect from localhost[127.0.0.1]
Jun 12 19:14:32 collab postfix/smtpd[9371]: disconnect from russian-caravan.cloud9.net[168.100.1.4]
Jun 12 19:14:32 collab cyrus/lmtpunix[9363]: accepted connection
Jun 12 19:14:32 collab cyrus/lmtpunix[9363]: lmtp connection preauth'd as postman
Jun 12 19:14:32 collab cyrus/lmtpunix[9363]: WARNING: sieve script /var/spool/sieve/h/houselion/defaultbc doesn't exist: No such fil$
Jun 12 19:14:32 collab cyrus/lmtpunix[9363]: duplicate_check: <48516738.2020108@megan.vbhcs.org>       user.mailbox1       0
Jun 12 19:14:32 collab cyrus/lmtpunix[9363]: duplicate_check: <48516738.2020108@megan.vbhcs.org>       user.mailbox1       0
Jun 12 19:14:32 collab cyrus/lmtpunix[9363]: mystore: starting txn 2147483956
Jun 12 19:14:32 collab cyrus/lmtpunix[9363]: mystore: committing txn 2147483956
Jun 12 19:14:32 collab cyrus/lmtpunix[9363]: duplicate_mark: <48516738.2020108@megan.vbhcs.org>       user.mailbox1       121329447$
Jun 12 19:14:32 collab cyrus/lmtpunix[9363]: Delivered: <48516738.2020108@megan.vbhcs.org> to mailbox: user.mailbox1
Jun 12 19:14:32 collab cyrus/lmtpunix[9363]: unable to sendto() notify socket: No such file or directory
Jun 12 19:14:32 collab postfix/lmtp[9362]: C13F4180C53: to=<mailbox1@domain1.tld>, orig_to=<alias1@domain1.tld>, relay=collab.sm-wg.n$
Jun 12 19:14:32 collab postfix/qmgr[5461]: C13F4180C53: removed

so I am stumped

what _is_ going on here?

any help appreciated

Bernhard

---

### Post by j03j03 on 2008-08-06
Hi, 

You may try this:

sudo /etc/init.d/saslauthd stop 

sudo dpkg-statoverride --add root sasl 710 /var/spool/postfix/var/run/saslauthd

sudo rm -rf /var/run/saslauthd

sudo ln -s /var/spool/postfix/var/run/saslauthd  /var/run/saslauthd

sudo /etc/init.d/saslauthd start

---

