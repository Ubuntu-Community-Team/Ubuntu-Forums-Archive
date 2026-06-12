---
title: "Postfix, SASL, and Roundcube"
date: 2011-06-12
forum: Server Platforms
---

### Post by glacebeast on 2011-06-12
Hey folks,

After spending numerous days searching up and down forums, guides, and the like trying to troubleshoot my mail server woes, I finally broke down and decided to post myself to get some insight from those with more knowledge than I. Anyway, on with it...

 I decided to run a mail server off my Ubuntu server 10.04 box, and I've been following Flurdy's guide ([http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)) closely with mixed success. Though I'm able to send and receive mails from internal and external sources fine, including from a 3rd party mail client, I'm running into issues logging in from Roundcube webmail, as well as initiating mass e-mails from my phpBB boards with proper credentials.

For example, when I initiate a login from Roundcube, I see the following hiccup:

```
Jun 12 19:46:06 smtp authdaemond: received auth request, service=imap, authtype=cram-md5
Jun 12 19:46:06 smtp authdaemond: authmysql: trying this module
Jun 12 19:46:06 smtp authdaemond: cram: challenge=PEQ4RDlDNDFGMkVBRTEwNjcwQ0IzMEJFMTM5OTA1MDY5QHNtdHAuZHJ1bmtiY
WJpZXMuY29tPg==, response=Zm9ydW1zQGRydW5rYmFiaWVzLmNvbSBiYTdkZDZjODUwMTI3MzQ2MjVlMWQ1MjhlMzQxMzEwYQ==
Jun 12 19:46:06 smtp authdaemond: cram: decoded challenge/response, username 'forums@xxxxx.com'
Jun 12 19:46:06 smtp authdaemond: authmysqllib: connected. Versions: header 50137, client 50141, server 50141
Jun 12 19:46:06 smtp authdaemond: SQL query: SELECT id, crypt, "", uid, gid, home, concat(home,'/',maildir), ""
, name, "" FROM users WHERE id = 'forums@xxxxx.com'  AND (enabled=1 )
Jun 12 19:46:06 smtp authdaemond: authmysql: REJECT - try next module
Jun 12 19:46:06 smtp authdaemond: FAIL, all modules rejected
Jun 12 19:46:06 smtp imapd-ssl: LOGIN FAILED, method=CRAM-MD5, ip=[::1]
Jun 12 19:46:11 smtp imapd-ssl: Disconnected, ip=[::1], time=5, starttls=1

```I'm 100% certain my credentials are correct, as I can login the account from Thunderbird as well as locally through telnet. 

On a similar note, when trying to initiate a mass e-mail from phpBB, I'll get the following complaints:

```
Jun 12 18:56:31 smtp postfix/master[5741]: daemon started -- version 2.7.0, configuration /etc/postfix
Jun 12 18:56:41 smtp postfix/smtpd[5744]: connect from xxxxx.com[127.0.1.1]
Jun 12 18:56:41 smtp postfix/smtpd[5744]: warning: SASL authentication failure: no secret in database
Jun 12 18:56:41 smtp postfix/smtpd[5744]: warning: xxxxx.com[127.0.1.1]: SASL CRAM-MD5 authentication fai
led: authentication failure
Jun 12 18:59:26 smtp postfix/smtpd[5751]: lost connection after AUTH from xxxx.com[127.0.1.1]
Jun 12 18:59:26 smtp postfix/smtpd[5751]: disconnect from dxxxx.com[127.0.1.1
```I'll include the relevant configuration files

postconf -n
```

alias_database = hash:/etc/postfix/aliases
alias_maps = hash:/etc/postfix/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = no
config_directory = /etc/postfix
content_filter = amavis:[127.0.0.1]:10024
delay_warning_time = 4h
disable_vrfy_command = yes
inet_interfaces = all
mailbox_size_limit = 0
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
mydestination = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mynetworks_style = host
myorigin = xxxxx.com
readme_directory = no
recipient_delimiter = +
relayhost = smtp.comcast.net
smtp_helo_timeout = 60s
smtp_sasl_password_maps = hash:/etc/postfix/saslpasswd
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = permit_sasl_authenticated, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:10023, permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = 
smtpd_sasl_security_options = noanonymous
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_soft_error_limit = 3
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = static:5000

```/etc/postfix/sasl/smptd.conf
```
pwcheck_method: saslauthd
mech_list: plain login cram-md5 digest-md5
log_level: 7
allow_plaintext: true
auxprop_plugin: mysql
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: xxxxx
sql_passw: xxxx
sql_database: maildb
sql_select: select crypt from users where id='%u@%r' and enabled = 1

```/etc/default/saslauthd
```
#
# Settings for saslauthd daemon
# Please read /usr/share/doc/sasl2-bin/README.Debian for details.
#

# Should saslauthd run automatically on startup? (default: no)
START=yes

# Description of this saslauthd instance. Recommended.
# (suggestion: SASL Authentication Daemon)
DESC="SASL Authentication Daemon"

# Short name of this saslauthd instance. Strongly recommended.
# (suggestion: saslauthd)
NAME="saslauthd"

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
MECHANISMS="pam"

# Additional options for this mechanism. (default: none)
# See the saslauthd man page for information about mech-specific options.
MECH_OPTIONS=""

# How many saslauthd processes should we run? (default: 5)
# A value of 0 will fork a new process for each connection.
THREADS=5

# Other options (default: -c -m /var/run/saslauthd)
# Note: You MUST specify the -m option or saslauthd won't run!
#
# WARNING: DO NOT SPECIFY THE -d OPTION.
# The -d option will cause saslauthd to run in the foreground instead of as
# a daemon. This will PREVENT YOUR SYSTEM FROM BOOTING PROPERLY. If you wish
# to run saslauthd in debug mode, please run it by hand to be safe.
#
# See /usr/share/doc/sasl2-bin/README.Debian for Debian-specific information.
# See the saslauthd man page and the output of 'saslauthd -h' for general
# information about these options.
#
# Example for postfix users: "-c -m /var/spool/postfix/var/run/saslauthd"
OPTIONS="-r -c -m  /var/spool/postfix/var/run/saslauthd"
```/etc/roundcube/db.inc.php
```
/*
 +-----------------------------------------------------------------------+
 | Configuration file for database access                                |
 |                                                                       |
 | This file is part of the RoundCube Webmail client                     |
 | Copyright (C) 2005-2009, RoundCube Dev. - Switzerland                 |
 | Licensed under the GNU GPL                                            |
 |                                                                       |
 +-----------------------------------------------------------------------+

*/

$rcmail_config = array();

/* Do not set db_dsnw here, use dpkg-reconfigure roundcube to configure database ! */

include_once("/etc/roundcube/debian-db.php");

switch ($dbtype) {
 case "sqlite":
   $rcmail_config['db_dsnw'] = "sqlite:///$basepath/$dbname?mode=0640";
   break;
 default:
   if ($dbport != '') $dbport=":$dbport";
   if ($dbserver == '') $dbserver="localhost";
   $rcmail_config['db_dsnw'] = "$dbtype://$dbuser:$dbpass@$dbserver$dbport/$dbname";
   break;
 }

// PEAR database DSN for read only operations (if empty write database will be used)
// useful for database replication
$rcmail_config['db_dsnr'] = '';

// maximum length of a query in bytes
$rcmail_config['db_max_length'] = 512000;  // 500K

// use persistent db-connections
// beware this will not "always" work as expected
// see: http://www.php.net/manual/en/features.persistent-connections.php
$rcmail_config['db_persistent'] = FALSE;


// you can define specific table names used to store webmail data
$rcmail_config['db_table_users'] = 'users';

$rcmail_config['db_table_identities'] = 'identities';

$rcmail_config['db_table_contacts'] = 'contacts';

$rcmail_config['db_table_session'] = 'session';

$rcmail_config['db_table_cache'] = 'cache';

$rcmail_config['db_table_messages'] = 'messages';


// you can define specific sequence names used in PostgreSQL
$rcmail_config['db_sequence_users'] = 'user_ids';

$rcmail_config['db_sequence_identities'] = 'identity_ids';

$rcmail_config['db_sequence_contacts'] = 'contact_ids';

$rcmail_config['db_sequence_cache'] = 'cache_ids';

$rcmail_config['db_sequence_messages'] = 'message_ids';

```/etc/roundcube/main.inc.php
```
<?php

/*
 +-----------------------------------------------------------------------+
 | Main configuration file                                               |
 |                                                                       |
 | This file is part of the RoundCube Webmail client                     |
 | Copyright (C) 2005-2009, RoundCube Dev. - Switzerland                 |
 | Licensed under the GNU GPL                                            |
 |                                                                       |
 +-----------------------------------------------------------------------+

*/

$rcmail_config = array();

// system error reporting: 1 = log; 2 = report (not implemented yet), 4 = show, 8 = trace
$rcmail_config['debug_level'] = 8;

// log driver:  'syslog' or 'file'.
$rcmail_config['log_driver'] = 'file';

// date format for log entries
// (read http://php.net/manual/en/function.date.php for all format characters)  
$rcmail_config['log_date_format'] = 'd-M-Y H:i:s O';

// Syslog ident string to use, if using the 'syslog' log driver.
$rcmail_config['syslog_id'] = 'roundcube';

// Syslog facility to use, if using the 'syslog' log driver.
// For possible values see installer or http://php.net/manual/en/function.openlog.php
$rcmail_config['syslog_facility'] = LOG_USER;

// use this folder to store log files (must be writeable for apache user)
// This is used by the 'file' log driver.
$rcmail_config['log_dir'] = 'logs/';

// use this folder to store temp files (must be writeable for apache user)
$rcmail_config['temp_dir'] = 'temp/';

// List of active plugins (in plugins/ directory)
$rcmail_config['plugins'] = array();

// enable caching of messages and mailbox data in the local database.
// this is recommended if the IMAP server does not run on the same machine
$rcmail_config['enable_caching'] = FALSE;

// lifetime of message cache
// possible units: s, m, h, d, w
$rcmail_config['message_cache_lifetime'] = '10d';

// enforce connections over https
// with this option enabled, all non-secure connections will be redirected.
// set the port for the ssl connection as value of this option if it differs from the default 443
$rcmail_config['force_https'] = FALSE;

// automatically create a new RoundCube user when log-in the first time.
// a new user will be created once the IMAP login succeeds.
// set to false if only registered users can use this service
$rcmail_config['auto_create_user'] = TRUE;

// the mail host chosen to perform the log-in
// leave blank to show a textbox at login, give a list of hosts
// to display a pulldown menu or set one host as string.
// To use SSL/TLS connection, enter hostname with prefix ssl:// or tls://
$rcmail_config['default_host'] = 'ssl://localhost:993';

// TCP port used for IMAP connections
$rcmail_config['default_port'] = 143;

// IMAP auth type. Can be "auth" (CRAM-MD5), "plain" (PLAIN) or "check" to auto detect.
// Optional, defaults to "check"
$rcmail_config['imap_auth_type'] = check;

// If you know your imap's root directory and its folder delimiter,
// you can specify them here. Otherwise they will be determined automatically.
$rcmail_config['imap_root'] = null;
$rcmail_config['imap_delimiter'] = null;

// Automatically add this domain to user names for login
// Only for IMAP servers that require full e-mail addresses for login
// Specify an array with 'host' => 'domain' values to support multiple hosts
$rcmail_config['username_domain'] = 'xxxx.com';

// This domain will be used to form e-mail addresses of new users
// Specify an array with 'host' => 'domain' values to support multiple hosts
$rcmail_config['mail_domain'] = 'xxxx.com';

// Path to a virtuser table file to resolve user names and e-mail addresses
$rcmail_config['virtuser_file'] = '';

// Query to resolve user names and e-mail addresses from the database
// %u will be replaced with the current username for login.
// The query should select the user's e-mail address as first column
// and optional identity name as second column
$rcmail_config['virtuser_query'] = '';

// use this host for sending mails.
// to use SSL connection, set ssl://smtp.host.com
// if left blank, the PHP mail() function is used
// Use %h variable as replacement for user's IMAP hostname
$rcmail_config['smtp_server'] = 'ssl://localhost';

// SMTP port (default is 25; 465 for SSL)
$rcmail_config['smtp_port'] = 465;

// SMTP username (if required) if you use %u as the username RoundCube
// will use the current username for login
$rcmail_config['smtp_user'] = '';

// SMTP password (if required) if you use %p as the password RoundCube
// will use the current user's password for login
$rcmail_config['smtp_pass'] = '';

// SMTP AUTH type (DIGEST-MD5, CRAM-MD5, LOGIN, PLAIN or empty to use
// best server supported one)
$rcmail_config['smtp_auth_type'] = '';

// SMTP HELO host 
// Hostname to give to the remote server for SMTP 'HELO' or 'EHLO' messages 
// Leave this blank and you will get the server variable 'server_name' or 
// localhost if that isn't defined. 
$rcmail_config['smtp_helo_host'] = 'smtp.xxxxx.com';

// Log sent messages
$rcmail_config['smtp_log'] = TRUE;

// Log SQL queries to <log_dir>/sql or to syslog
$rcmail_config['sql_debug'] = false;

// Log IMAP conversation to <log_dir>/imap or to syslog
$rcmail_config['imap_debug'] = false;

// Log LDAP conversation to <log_dir>/ldap or to syslog
$rcmail_config['ldap_debug'] = false;

// Log SMTP conversation to <log_dir>/smtp or to syslog
$rcmail_config['smtp_debug'] = true;

// How many seconds must pass between emails sent by a user
$rcmail_config['sendmail_delay'] = 0;

// These cols are shown in the message list. Available cols are:
// subject, from, to, cc, replyto, date, size, flag, attachment
$rcmail_config['list_cols'] = array('subject', 'from', 'date', 'size', 'flag', 'attachment');

// Includes should be interpreted as PHP files
$rcmail_config['skin_include_php'] = FALSE;

// Session lifetime in minutes
// must be greater than 'keep_alive'/60
$rcmail_config['session_lifetime'] = 10;

// check client IP in session athorization
$rcmail_config['ip_check'] = false;

// Use an additional frequently changing cookie to athenticate user sessions.
// There have been problems reported with this feature.
$rcmail_config['double_auth'] = false;

// this key is used to encrypt the users imap password which is stored
// in the session record (and the client cookie if remember password is enabled).
// please provide a string of exactly 24 chars.
$rcmail_config['des_key'] = 'OctQ[[f7WrePxV2GX5Ye4]4z';

// the default locale setting (leave empty for auto-detection)
// RFC1766 formatted language name like en_US, de_DE, de_CH, fr_FR, pt_BR
$rcmail_config['language'] = 'en_US';

// use this format for short date display (date or strftime format)
$rcmail_config['date_short'] = 'D H:i';

// use this format for detailed date/time formatting (date or strftime format)
$rcmail_config['date_long'] = 'd.m.Y H:i';

// use this format for today's date display (date or strftime format)
$rcmail_config['date_today'] = 'H:i';

// add this user-agent to message headers when sending
$rcmail_config['useragent'] = 'Rouncube Webmail/'.RCMAIL_VERSION;

// use this name to compose page titles
$rcmail_config['product_name'] = 'Roundcube Webmail';

// store draft message is this mailbox
// leave blank if draft messages should not be stored
$rcmail_config['drafts_mbox'] = 'Drafts';

// store spam messages in this mailbox
$rcmail_config['junk_mbox'] = 'Junk';

// store sent message is this mailbox
// leave blank if sent messages should not be stored
$rcmail_config['sent_mbox'] = 'Sent';

// move messages to this folder when deleting them
// leave blank if they should be deleted directly
$rcmail_config['trash_mbox'] = 'Trash';

// display these folders separately in the mailbox list.
// these folders will also be displayed with localized names
$rcmail_config['default_imap_folders'] = array('INBOX', 'Drafts', 'Sent', 'Junk', 'Trash');

// automatically create the above listed default folders on login
$rcmail_config['create_default_folders'] = TRUE;

// protect the default folders from renames, deletes, and subscription changes
$rcmail_config['protect_default_folders'] = TRUE;

// if in your system 0 quota means no limit set this option to TRUE 
$rcmail_config['quota_zero_as_unlimited'] = FALSE;

// Behavior if a received message requests a message delivery notification (read receipt)
// 0 = ask the user, 1 = send automatically, 2 = ignore (never send or ask)
$rcmail_config['mdn_requests'] = 0;

// Use this charset as fallback for message decoding
$rcmail_config['default_charset'] = 'ISO-8859-1';

// Make use of the built-in spell checker. It is based on GoogieSpell.
// Since Google only accepts connections over https your PHP installatation
// requires to be compiled with Open SSL support
$rcmail_config['enable_spellcheck'] = TRUE;

// Set the spell checking engine. 'googie' is the default. 'pspell' is also available,
// but requires the Pspell extensions. When using Nox Spell Server, also set 'googie' here.
$rcmail_config['spellcheck_engine'] = 'googie';

// For a locally installed Nox Spell Server, please specify the URI to call it.
// Get Nox Spell Server from http://orangoo.com/labs/?page_id=72
// Leave empty to use the Google spell checking service, what means
// that the message content will be sent to Google in order to check spelling
$rcmail_config['spellcheck_uri'] = '';

// These languages can be selected for spell checking.
// Configure as a PHP style hash array: array('en'=>'English', 'de'=>'Deutsch');
// Leave empty for default set of available language.
$rcmail_config['spellcheck_languages'] = NULL;

// path to a text file which will be added to each sent message
// paths are relative to the RoundCube root folder
$rcmail_config['generic_message_footer'] = '';

// add a received header to outgoing mails containing the creators IP and hostname
$rcmail_config['http_received_header'] = false;

// Whether or not to encrypt the IP address and the host name
// these could, in some circles, be considered as sensitive information;
// however, for the administrator, these could be invaluable help
// when tracking down issues.
$rcmail_config['http_received_header_encrypt'] = false;

// this string is used as a delimiter for message headers when sending
// leave empty for auto-detection
$rcmail_config['mail_header_delimiter'] = NULL;

// session domain: .example.org
$rcmail_config['session_domain'] = '';

// This indicates which type of address book to use. Possible choises:
// 'sql' (default) and 'ldap'.
// If set to 'ldap' then it will look at using the first writable LDAP
// address book as the primary address book and it will not display the
// SQL address book in the 'Address Book' view.
$rcmail_config['address_book_type'] = 'sql';

// In order to enable public ldap search, configure an array like the Verisign
// example further below. if you would like to test, simply uncomment the example.
$rcmail_config['ldap_public'] = array();

//
// If you are going to use LDAP for individual address books, you will need to 
// set 'user_specific' to true and use the variables to generate the appropriate DNs to access it.
//
// The recommended directory structure for LDAP is to store all the address book entries
// under the users main entry, e.g.:
//
//  o=root
//   ou=people
//    uid=user@domain
//  mail=contact@contactdomain
//
// So the base_dn would be uid=%fu,ou=people,o=root
// The bind_dn would be the same as based_dn or some super user login.
/* 
 * example config for Verisign directory
 *
$rcmail_config['ldap_public']['Verisign'] = array(
  'name'          => 'Verisign.com',
  'hosts'         => array('directory.verisign.com'),
  'port'          => 389,
  'use_tls'         => false,
  'user_specific' => false,   // If true the base_dn, bind_dn and bind_pass default to the user's IMAP login.
  // %fu - The full username provided, assumes the username is an email
  //       address, uses the username_domain value if not an email address.
  // %u  - The username prior to the '@'.
  // %d  - The domain name after the '@'.
  'base_dn'       => '',
  'bind_dn'       => '',
  'bind_pass'     => '',
  'writable'      => false,   // Indicates if we can write to the LDAP directory or not.
  // If writable is true then these fields need to be populated:
  // LDAP_Object_Classes, required_fields, LDAP_rdn
  'LDAP_Object_Classes' => array("top", "inetOrgPerson"), // To create a new contact these are the object class
es to specify (or any other classes you wish to use).
  'required_fields'     => array("cn", "sn", "mail"),     // The required fields needed to build a new contact 
as required by the object classes (can include additional fields not required by the object classes).
  'LDAP_rdn'      => 'mail', // The RDN field that is used for new entries, this field needs to be one of the s
earch_fields, the base of base_dn is appended to the RDN to insert into the LDAP directory.
  'ldap_version'  => 3,       // using LDAPv3
  'search_fields' => array('mail', 'cn'),  // fields to search in
  'name_field'    => 'cn',    // this field represents the contact's name
  'email_field'   => 'mail',  // this field represents the contact's e-mail
  'surname_field' => 'sn',    // this field represents the contact's last name
  'firstname_field' => 'gn',  // this field represents the contact's first name
  'sort'          => 'cn',    // The field to sort the listing by.
  'scope'         => 'sub',   // search mode: sub|base|list
  'filter'        => '',      // used for basic listing (if not empty) and will be &'d with search queries. exa
mple: status=act
  'fuzzy_search'  => true);   // server allows wildcard search
*/

// An ordered array of the ids of the addressbooks that should be searched
// when populating address autocomplete fields server-side. ex: array('sql','Verisign');
$rcmail_config['autocomplete_addressbooks'] = array('sql');

// don't allow these settings to be overriden by the user
$rcmail_config['dont_override'] = array();

// Set identities access level:
// 0 - many identities with possibility to edit all params
// 1 - many identities with possibility to edit all params but not email address
// 2 - one identity with possibility to edit all params
// 3 - one identity with possibility to edit all params but not email address
$rcmail_config['identities_level'] = 0;

// try to load host-specific configuration
// see http://trac.roundcube.net/wiki/Howto_Config for more details
$rcmail_config['include_host_config'] = false;

// don't let users set pagesize to more than this value if set
$rcmail_config['max_pagesize'] = 200;

// mime magic database
$rcmail_config['mime_magic'] = '/usr/share/file/magic';

// default sort col
$rcmail_config['message_sort_col'] = 'date';

// default sort order
$rcmail_config['message_sort_order'] = 'DESC';

// THIS OPTION WILL ALLOW THE INSTALLER TO RUN AND CAN EXPOSE SENSITIVE CONFIG DATA.
// ONLY ENABLE IT IF YOU'RE REALLY SURE WHAT YOU'RE DOING!
$rcmail_config['enable_installer'] = false;

// Log successful logins
$rcmail_config['log_logins'] = true;

/**
 * 'Delete always'
 * This setting reflects if mail should be always marked as deleted,
 * even if moving to "Trash" fails. This is necessary in some setups
 * because a) people may not have a Trash folder or b) they are over
 * quota (and Trash is included in the quota).
 *
 * This is a failover setting for iil_C_Move when a message is moved
 * to the Trash.
 */
$rcmail_config['delete_always'] = false;

// Minimal value of user's 'keep_alive' setting (in seconds)
// Must be less than 'session_lifetime'
$rcmail_config['min_keep_alive'] = 60;

// Enable DNS checking for e-mail address validation
$rcmail_config['email_dns_check'] = false;

/***** these settings can be overwritten by user's preferences *****/

// skin name: folder from skins/
$rcmail_config['skin'] = 'default';

// show up to X items in list view
$rcmail_config['pagesize'] = 40;

// use this timezone to display date/time
$rcmail_config['timezone'] = 'auto';

// is daylight saving On?
$rcmail_config['dst_active'] = (bool)date('I');

// prefer displaying HTML messages
$rcmail_config['prefer_html'] = TRUE;

// display remote inline images
// 0 - Never, always ask
// 1 - Ask if sender is not in address book
// 2 - Always show inline images
$rcmail_config['show_images'] = 0;

// compose html formatted messages by default
$rcmail_config['htmleditor'] = FALSE;

// show pretty dates as standard
$rcmail_config['prettydate'] = TRUE;

// save compose message every 300 seconds (5min)
$rcmail_config['draft_autosave'] = 300;

// default setting if preview pane is enabled
$rcmail_config['preview_pane'] = FALSE;

// focus new window if new message arrives
$rcmail_config['focus_on_new_message'] = true;

// Clear Trash on logout
$rcmail_config['logout_purge'] = FALSE;

// Compact INBOX on logout
$rcmail_config['logout_expunge'] = FALSE;

// Display attached images below the message body 
$rcmail_config['inline_images'] = TRUE;

// Encoding of long/non-ascii attachment names:
// 0 - Full RFC 2231 compatible
// 1 - RFC 2047 for 'name' and RFC 2231 for 'filename' parameter (Thunderbird's default)
// 2 - Full 2047 compatible
$rcmail_config['mime_param_folding'] = 1;

// Set TRUE if deleted messages should not be displayed
// This will make the application run slower
$rcmail_config['skip_deleted'] = FALSE;

// Set true to Mark deleted messages as read as well as deleted
// False means that a message's read status is not affected by marking it as deleted
$rcmail_config['read_when_deleted'] = TRUE;

// Set to TRUE to newer delete messages immediately
// Use 'Purge' to remove messages marked as deleted 
$rcmail_config['flag_for_deletion'] = FALSE;

// Default interval for keep-alive/check-recent requests (in seconds)
// Must be greater than or equal to 'min_keep_alive' and less than 'session_lifetime'
$rcmail_config['keep_alive'] = 60;

// If true all folders will be checked for recent messages
$rcmail_config['check_all_folders'] = FALSE;

// If true, after message delete/move, the next message will be displayed
$rcmail_config['display_next'] = FALSE;

// If true, messages list will be sorted by message index instead of message date
$rcmail_config['index_sort'] = TRUE;

// end of config file
?>

```/etc/pam.d/smpt
```
auth required pam_mysql.so user=xxxx passwd=xxxx host=127.0.0.1 db=maildb table=users usercolumn=id pa
sswdcolumn=crypt crypt=1
account sufficient pam_mysql.so user=xxxx passwd=xxxx host=127.0.0.1 db=maildb table=users usercolumn=
id passwdcolumn=crypt crypt=1

```I assume it's an issue with SASL/authentication but I've tried everything I can think of as well as most suggestions I've seen from others. I simply just don't know enough about it to continue a diagnosis, and I'm hoping to hear some of your thoughts?

Thanks.

---

### Post by glacebeast on 2011-06-13
Bump. Anyone have any insight? I've checked and rechecked my configuration and anything I can think of. It just doesn't make sense to me cause authentication works fine through a configured 3rd party client like Thunderbird.

---

### Post by yaddoshi on 2011-08-16
> **glacebeast said:**
> Bump. Anyone have any insight? I've checked and rechecked my configuration and anything I can think of. It just doesn't make sense to me cause authentication works fine through a configured 3rd party client like Thunderbird.

I'm not an expert but Ubuntu server does not have Cyrus SASL installed by default and typically that's the SASL you need.
```
sudo apt-get install libsasl2-2 libsasl2-modules
```

I'd start there and see what you get.  I also strongly recommend reading through the [official Postfix documentation]("http://www.postfix.org/SASL_README.html"), it helped me with [my own mailserver issues]("http://fatedtoend.com/content/how-set-postfix-send-email-ubuntu-server-lucid-lynx-1004-lts-when-using-dynamic-ip-address") when nothing else could.

That first error string in Roundcube looks like it failed when authenticating against the MySQL user database - it might be necessary to blow that away and set it up again - but try my first two recommendations before you start messing with Roundcube.

---

### Post by DIY James on 2012-06-16
I have just ran into exactly the same issue with roundcube not connecting. I believe your problem is with this statement:

**authdaemond: received auth request, service=imap, authtype=[COLOR=Red]cram-md5[/COLOR]**

In my case if found if I connect via squirrelmail or directly via openssl the *'/var/log/mail.log*' file gave me:
     **authdaemond: received auth request, service=imap, authtype=[COLOR=Red]login[/COLOR]**

Editting */etc/roundcube/main.inc.php* and changing  
**    $rcmail_config['imap_auth_type'] = null;**
to:
**    $rcmail_config['imap_auth_type'] = 'LOGIN';**
    
Meant roundcube also worked.

[Now need to work out why my IMAP server wasn't happy with cram-md5. I believe the original should have worked since within the file '*/etc/courier/imapd*' I have the '**IMAP_CAPABILITY**' item set with '**AUTH=CRAM-MD5**']

--
To connect via openssl do this:

openssl s_client -connect x.x.x.x:993
a login USERNAME PASSWORD
a examine inbox
a logout


James

---

