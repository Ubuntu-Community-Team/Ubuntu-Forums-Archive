---
title: "Can't log into squirrelmail on my server"
date: 2006-11-13
forum: Server Platforms
---

### Post by svehex on 2006-11-13
I can't login via telnet or squirrelmail. Can anyone help me?
I followed the howto on this page: [http://www.urbanpuddle.com/articles/2006/10/12/setup-postfix-in-about-1-hour](http://www.urbanpuddle.com/articles/2006/10/12/setup-postfix-in-about-1-hour)

Here are the files I can think of right now thath may be useful. (domain name, user and passwords have been edited out)

syslog: 
Nov 13 12:15:20 hostname imaplogin: Connection, ip=[::ffff:127.0.0.1]
Nov 13 12:15:25 hostname imaplogin: LOGIN FAILED, ip=[::ffff:127.0.0.1]
Nov 13 12:15:25 hostname imaplogin: LOGOUT, ip=[::ffff:127.0.0.1]

mail.log:
Nov 13 13:40:11 hostname imaplogin: Connection, ip=[::ffff:127.0.0.1]
Nov 13 13:40:16 hostname imaplogin: LOGIN FAILED, ip=[::ffff:127.0.0.1]
Nov 13 13:40:16 hostname imaplogin: LOGOUT, ip=[::ffff:127.0.0.1]

mysql.log
9 Connect     mail_admin@localhost on 
9 Init DB     mail
9 Query       SELECT email, password, "", 5000, 5000, /home/vmail, "", "", "", "" FROM users WHERE email = "user@domain.com"
9 Quit  

Postfix-main.cf:
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

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.domain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.domain.com, localhost, localhost.localdomain
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
virtual_alias_domains =
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000
transport_maps = mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota."
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps 

Courier-authdaemonrc:
##VERSION: $Id: authdaemonrc.in,v 1.8 2001/10/07 02:16:22 mrsam Exp $
#
# Copyright 2000-2001 Double Precision, Inc.  See COPYING for
# distribution information.
#
# authdaemonrc created from authdaemonrc.dist by sysconftool
#
# Do not alter lines that begin with ##, they are used when upgrading
# this configuration.
#
# This file configures authdaemond, the resident authentication daemon.
#
# Comments in this file are ignored.  Although this file is intended to
# be sourced as a shell script, authdaemond parses it manually, so
# the acceptable syntax is a bit limited.  Multiline variable contents,
# with the \ continuation character, are not allowed.  Everything must
# fit on one line.  Do not use any additional whitespace for indentation,
# or anything else.

##NAME: authmodulelist:0
#
# The authentication modules that are linked into authdaemond.  The
# default list is installed.  You may selectively disable modules simply
# by removing them from the following list.  The available modules you
# can use are: authcustom authcram authuserdb authldap authpgsql authmysql authpam

authmodulelist="authmysql"

##NAME: authmodulelistorig:1
#
# This setting is used by Courier's webadmin module, and should be left
# alone

authmodulelistorig="authcustom authcram authuserdb authldap authpgsql authmysql authpam"

##NAME: daemons:0
#
# The number of daemon processes that are started.  authdaemon is typically
# installed where authentication modules are relatively expensive: such
# as authldap, or authmysql, so it's better to have a number of them running.
# PLEASE NOTE:  Some platforms may experience a problem if there's more than
# one daemon.  Specifically, SystemV derived platforms that use TLI with
# socket emulation.  I'm suspicious of TLI's ability to handle multiple
# processes accepting connections on the same filesystem domain socket.
#
# You may need to increase daemons if as your system load increases.  Symptoms
# include sporadic authentication failures.  If you start getting
# authentication failures, increase daemons.  However, the default of 5
# SHOULD be sufficient.  Bumping up daemon count is only a short-term
# solution.  The permanent solution is to add more resources: RAM, faster
# disks, faster CPUs...

daemons=5

##NAME: version:0
#
# When you have multiple versions of authdaemond.* installed, authdaemond
# just picks the first one it finds.  Set "version" to override that.
# For example:  version=authdaemond.plain

version=""

##NAME: authdaemonvar:0
#
# authdaemonvar is here, but is not used directly by authdaemond.  It's
# used by various configuration and build scripts, so don't touch it!

authdaemonvar=/var/run/courier/authdaemon

Courier-authmysqlrc:
##VERSION: $Id: authmysqlrc,v 1.17 2004/04/20 01:38:17 mrsam Exp $
#
# Copyright 2000-2004 Double Precision, Inc.  See COPYING for
# distribution information.
#
# Do not alter lines that begin with ##, they are used when upgrading
# this configuration.
#
# authmysqlrc created from authmysqlrc.dist by sysconftool
#
# DO NOT INSTALL THIS FILE with world read permissions.  This file
# might contain the MySQL admin password!
#
# Each line in this file must follow the following format:
#
# field[spaces|tabs]value
#
# That is, the name of the field, followed by spaces or tabs, followed by
# field value.  Trailing spaces are prohibited.


##NAME: LOCATION:0
#
# The server name, userid, and password used to log in.

MYSQL_SERVER            localhost
MYSQL_USERNAME          mail_admin
MYSQL_PASSWORD          ********

##NAME: MYSQL_SOCKET:0
#
# MYSQL_SOCKET can be used with MySQL version 3.22 or later, it specifies the
# filesystem pipe used for the connection
#
# MYSQL_SOCKET          /var/run/mysqld/mysqld.sock

##NAME: MYSQL_PORT:0
#
# MYSQL_PORT can be used with MySQL version 3.22 or later to specify a port to
# connect to.

MYSQL_PORT              0

##NAME: MYSQL_OPT:0
#
# Leave MYSQL_OPT as 0, unless you know what you're doing.

MYSQL_OPT               0

##NAME: MYSQL_DATABASE:0
#
# The name of the MySQL database we will open:

MYSQL_DATABASE          mail

##NAME: MYSQL_USER_TABLE:0
#
# The name of the table containing your user data.  See README.authmysqlrc
# for the required fields in this table.

MYSQL_USER_TABLE        users

##NAME: MYSQL_CRYPT_PWFIELD:0
#
# Either MYSQL_CRYPT_PWFIELD or MYSQL_CLEAR_PWFIELD must be defined.  Both
# are OK too. crypted passwords go into MYSQL_CRYPT_PWFIELD, cleartext
# passwords go into MYSQL_CLEAR_PWFIELD.  Cleartext passwords allow
# CRAM-MD5 authentication to be implemented.

MYSQL_CRYPT_PWFIELD     password

##NAME: MYSQL_CLEAR_PWFIELD:0
#
#
# MYSQL_CLEAR_PWFIELD   password

##NAME: MYSQL_DEFAULT_DOMAIN:0
#
# If DEFAULT_DOMAIN is defined, and someone tries to log in as 'user',
# we will look up 'user@DEFAULT_DOMAIN' instead.
#
#
# DEFAULT_DOMAIN                example.com

##NAME: MYSQL_UID_FIELD:0
#
# Other fields in the mysql table:
#
# MYSQL_UID_FIELD - contains the numerical userid of the account
#
MYSQL_UID_FIELD         5000

##NAME: MYSQL_GID_FIELD:0
#
# Numerical groupid of the account

MYSQL_GID_FIELD         5000

##NAME: MYSQL_LOGIN_FIELD:0
#
# The login id, default is id.  Basically the query is:
#
#  SELECT MYSQL_UID_FIELD, MYSQL_GID_FIELD, ... WHERE id='loginid'
#

MYSQL_LOGIN_FIELD       email

##NAME: MYSQL_HOME_FIELD:0
#

MYSQL_HOME_FIELD        /home/vmail

##NAME: MYSQL_NAME_FIELD:0
#
# The user's name (optional)

#MYSQL_NAME_FIELD       name

##NAME: MYSQL_MAILDIR_FIELD:0
#
# This is an optional field, and can be used to specify an arbitrary 
# location of the maildir for the account, which normally defaults to
# $HOME/Maildir (where $HOME is read from MYSQL_HOME_FIELD).
#
# You still need to provide a MYSQL_HOME_FIELD, even if you uncomment this
# out.
#
# MYSQL_MAILDIR_FIELD   maildir
MYSQL_MAILDIR_FIELD
CONCAT(SUBSTRING_INDEX(email,'@',-1),'/',SUBSTRING_INDEX(email,'@',1),'/')

##NAME: MYSQL_DEFAULTDELIVERY:0
#
# Courier mail server only: optional field specifies custom mail delivery
# instructions for this account (if defined) -- essentially overrides
# DEFAULTDELIVERY from ${sysconfdir}/courierd
#
# MYSQL_DEFAULTDELIVERY defaultdelivery

##NAME: MYSQL_QUOTA_FIELD:0
#
# Define MYSQL_QUOTA_FIELD to be the name of the field that can optionally
# specify a maildir quota.  See README.maildirquota for more information
#
# MYSQL_QUOTA_FIELD     quota

##NAME: MYSQL_AUXOPTIONS:0
#
# Auxiliary options.  The MYSQL_AUXOPTIONS field should be a char field that
# contains a single string consisting of comma-separated "ATTRIBUTE=NAME"
# pairs.  These names are additional attributes that define various per-account
# "options", as given in INSTALL's description of the "Account OPTIONS"
# setting.
#
# MYSQL_AUXOPTIONS_FIELD        auxoptions
#
# You might want to try something like this, if you'd like to use a bunch
# of individual fields, instead of a single text blob:
#
# MYSQL_AUXOPTIONS_FIELD        CONCAT("disableimap=",disableimap,",disablepop3=",disablepop3,",disablewebmail=",disablewebmail,",sharedgroup=",sharedgroup)
#
# This will let you define fields called "disableimap", etc, with the end result
# being something that the OPTIONS parser understands.
 

##NAME: MYSQL_WHERE_CLAUSE:0
#
# This is optional, MYSQL_WHERE_CLAUSE can be basically set to an arbitrary
# fixed string that is appended to the WHERE clause of our query
#
# MYSQL_WHERE_CLAUSE    server='mailhost.example.com'

##NAME: MYSQL_SELECT_CLAUSE:0
#
# (EXPERIMENTAL)
# This is optional, MYSQL_SELECT_CLAUSE can be set when you have a database,
# which is structuraly different from proposed. The fixed string will
# be used to do a SELECT operation on database, which should return fields
# in order specified bellow:
#
# username, cryptpw, clearpw, uid, gid, home, maildir, quota, fullname, options
#
# The username field should include the domain (see example below).
#
# Enabling this option causes ignorance of any other field-related
# options, excluding default domain.
#
# There are two variables, which you can use. Substitution will be made 
# for them, so you can put entered username (local part) and domain name
# in the right place of your query. These variables are:
#               $(local_part), $(domain), $(service)
#
# If a $(domain) is empty (not given by the remote user) the default domain
# name is used in its place.
#
# $(service) will expand out to the service being authenticated: imap, imaps,
# pop3 or pop3s.  Courier mail server only: service will also expand out to  
# "courier", when searching for local mail account's location.  In this case,
# if the "maildir" field is not empty it will be used in place of
# DEFAULTDELIVERY.  Courier mail server will also use esmtp when doing
# authenticated ESMTP.
#
# This example is a little bit modified adaptation of vmail-sql
# database scheme:
#
# MYSQL_SELECT_CLAUSE   SELECT CONCAT(popbox.local_part, '@', popbox.domain_name),                      \
#                       CONCAT('{MD5}', popbox.password_hash),          \
#                       popbox.clearpw,                                 \
#                       domain.uid,                                     \
#                       domain.gid,                                     \
#                       CONCAT(domain.path, '/', popbox.mbox_name),     \
#                       '',                                             \
#                       domain.quota,                                   \
#                       '',                                             \
#                       CONCAT("disableimap=",disableimap,",disablepop3=",    \
#                              disablepop3,",disablewebmail=",disablewebmail, \
#                              ",sharedgroup=",sharedgroup)             \
#                       FROM popbox, domain                             \
#                       WHERE popbox.local_part = '$(local_part)'       \
#                       AND popbox.domain_name = '$(domain)'            \
#                       AND popbox.domain_name = domain.domain_name


##NAME: MYSQL_ENUMERATE_CLAUSE:0
#
# {EXPERIMENTAL}
# Optional custom SQL query used to enumerate accounts for authenumerate,
# in order to compile a list of accounts for shared folders.  The query
# should return the following fields: name, uid, gid, homedir, maildir
#
# Example:
# MYSQL_ENUMERATE_CLAUSE        SELECT CONCAT(popbox.local_part, '@', popbox.domain_name),                      \
#                       domain.uid,                                     \
#                       domain.gid,                                     \
#                       CONCAT(domain.path, '/', popbox.mbox_name),     \
#                       ''                                              \
#                       FROM popbox, domain                             \
#                       WHERE popbox.local_part = '$(local_part)'       \
#                       AND popbox.domain_name = '$(domain)'            \
#                       AND popbox.domain_name = domain.domain_name



##NAME: MYSQL_CHPASS_CLAUSE:0
#
# (EXPERIMENTAL)
# This is optional, MYSQL_CHPASS_CLAUSE can be set when you have a database,
# which is structuraly different from proposed. The fixed string will 
# be used to do an UPDATE operation on database. In other words, it is
# used, when changing password.
#
# There are four variables, which you can use. Substitution will be made
# for them, so you can put entered username (local part) and domain name
# in the right place of your query. There variables are:
#       $(local_part) , $(domain) , $(newpass) , $(newpass_crypt)
#
# If a $(domain) is empty (not given by the remote user) the default domain
# name is used in its place.
# $(newpass) contains plain password
# $(newpass_crypt) contains its crypted form
#
# MYSQL_CHPASS_CLAUSE   UPDATE  popbox                                  \
#                       SET     clearpw='$(newpass)',                   \
#                               password_hash='$(newpass_crypt)'        \
#                       WHERE   local_part='$(local_part)'              \  
#                       AND     domain_name='$(domain)'
#

Courier-imapd.cnf:
RANDFILE = /usr/lib/courier/imapd.rand

[ req ]
default_bits = 1024
encrypt_key = yes
distinguished_name = req_dn
x509_extensions = cert_type
prompt = no

[ req_dn ]
C=US
ST=NY
L=New York
O=Courier Mail Server
OU=Automatically-generated IMAP SSL key
CN=localhost
emailAddress=postmaster@example.com


[ cert_type ]
nsCertType = server

Squirrelmail-config.php
<?php

/**
 * SquirrelMail Configuration File
 * Created using the configure script, conf.pl
 */

global $version;
$config_version = '1.4.0';
$config_use_color = 2;

$org_name      = "Domain";
$org_logo      = SM_PATH . 'images/sm_logo.png';
$org_logo_width  = '308';
$org_logo_height = '111';
$org_title     = "SquirrelMail $version";
$signout_page  = '';
$frame_top     = '_top';

$provider_uri     = 'http://www.squirrelmail.org/';

$provider_name     = 'SquirrelMail';

$motd = "";

$squirrelmail_default_language = 'en_US';
$default_charset       = 'iso-8859-1';
$lossy_encoding        = false;

$domain                 = 'domain.com';
$imapServerAddress      = 'localhost';
$imapPort               = 143;
$useSendmail            = false;
$smtpServerAddress      = 'localhost';
$smtpPort               = 25;
$sendmail_path          = '/usr/sbin/sendmail';
$pop_before_smtp        = false;
$imap_server_type       = 'courier';
$invert_time            = false;
$optional_delimiter     = '.';
$encode_header_key      = '';

$default_folder_prefix          = 'INBOX.';
$trash_folder                   = 'Trash';
$sent_folder                    = 'Sent';
$draft_folder                   = 'Drafts';
$default_move_to_trash          = true;
$default_move_to_sent           = true;
$default_save_as_draft          = true;
$show_prefix_option             = false;
$list_special_folders_first     = true;
$use_special_folder_color       = true;
$auto_expunge                   = true;
$default_sub_of_inbox           = false;
$show_contain_subfolders_option = false;
$default_unseen_notify          = 2;     
$default_unseen_type            = 1;   
$auto_create_special            = true; 
$delete_folder                  = true; 
$noselect_fix_enable            = false;

$data_dir                 = '/var/lib/squirrelmail/data/';
$attachment_dir           = '/var/spool/squirrelmail/attach/';
$dir_hash_level           = 0;
$default_left_size        = '150';
$force_username_lowercase = false;
$default_use_priority     = true; 
$hide_sm_attributions     = false;
$default_use_mdn          = true;
$edit_identity            = true; 
$edit_name                = true; 
$hide_auth_header         = false;
$allow_thread_sort        = false;
$allow_server_sort        = false;
$allow_charset_search     = true;
$uid_support              = true;


$theme_css = '';   
$theme_default = 0;
$theme[0]['PATH'] = SM_PATH . 'themes/default_theme.php';
$theme[0]['NAME'] = 'Default';
$theme[1]['PATH'] = SM_PATH . 'themes/plain_blue_theme.php';
$theme[1]['NAME'] = 'Plain Blue';
$theme[2]['PATH'] = SM_PATH . 'themes/sandstorm_theme.php';
$theme[2]['NAME'] = 'Sand Storm';
$theme[3]['PATH'] = SM_PATH . 'themes/deepocean_theme.php';
$theme[3]['NAME'] = 'Deep Ocean';
$theme[4]['PATH'] = SM_PATH . 'themes/slashdot_theme.php';
$theme[4]['NAME'] = 'Slashdot';
$theme[5]['PATH'] = SM_PATH . 'themes/purple_theme.php';
$theme[5]['NAME'] = 'Purple';
$theme[6]['PATH'] = SM_PATH . 'themes/forest_theme.php';
$theme[6]['NAME'] = 'Forest';
$theme[7]['PATH'] = SM_PATH . 'themes/ice_theme.php';
$theme[7]['NAME'] = 'Ice';
$theme[8]['PATH'] = SM_PATH . 'themes/seaspray_theme.php';
$theme[8]['NAME'] = 'Sea Spray';
$theme[9]['PATH'] = SM_PATH . 'themes/bluesteel_theme.php';
$theme[9]['NAME'] = 'Blue Steel';
$theme[10]['PATH'] = SM_PATH . 'themes/dark_grey_theme.php';
$theme[10]['NAME'] = 'Dark Grey';
$theme[11]['PATH'] = SM_PATH . 'themes/high_contrast_theme.php';
$theme[11]['NAME'] = 'High Contrast';
$theme[12]['PATH'] = SM_PATH . 'themes/black_bean_burrito_theme.php';
$theme[12]['NAME'] = 'Black Bean Burrito';
$theme[13]['PATH'] = SM_PATH . 'themes/servery_theme.php';
$theme[13]['NAME'] = 'Servery';
$theme[14]['PATH'] = SM_PATH . 'themes/maize_theme.php';
$theme[14]['NAME'] = 'Maize';
$theme[15]['PATH'] = SM_PATH . 'themes/bluesnews_theme.php';
$theme[15]['NAME'] = 'BluesNews';
$theme[16]['PATH'] = SM_PATH . 'themes/deepocean2_theme.php';
$theme[16]['NAME'] = 'Deep Ocean 2';
$theme[17]['PATH'] = SM_PATH . 'themes/blue_grey_theme.php';
$theme[17]['NAME'] = 'Blue Grey';
$theme[18]['PATH'] = SM_PATH . 'themes/dompie_theme.php'; 
$theme[18]['NAME'] = 'Dompie'; 
$theme[19]['PATH'] = SM_PATH . 'themes/methodical_theme.php';
$theme[19]['NAME'] = 'Methodical';
$theme[20]['PATH'] = SM_PATH . 'themes/greenhouse_effect.php';
$theme[20]['NAME'] = 'Greenhouse Effect (Changes)';
$theme[21]['PATH'] = SM_PATH . 'themes/in_the_pink.php';
$theme[21]['NAME'] = 'In The Pink (Changes)';
$theme[22]['PATH'] = SM_PATH . 'themes/kind_of_blue.php'; 
$theme[22]['NAME'] = 'Kind of Blue (Changes)';
$theme[23]['PATH'] = SM_PATH . 'themes/monostochastic.php';
$theme[23]['NAME'] = 'Monostochastic (Changes)';
$theme[24]['PATH'] = SM_PATH . 'themes/shades_of_grey.php'; 
$theme[24]['NAME'] = 'Shades of Grey (Changes)';
$theme[25]['PATH'] = SM_PATH . 'themes/spice_of_life.php';
$theme[25]['NAME'] = 'Spice of Life (Changes)';
$theme[26]['PATH'] = SM_PATH . 'themes/spice_of_life_lite.php';
$theme[26]['NAME'] = 'Spice of Life - Lite (Changes)';
$theme[27]['PATH'] = SM_PATH . 'themes/spice_of_life_dark.php';
$theme[27]['NAME'] = 'Spice of Life - Dark (Changes)';
$theme[28]['PATH'] = SM_PATH . 'themes/christmas.php';  
$theme[28]['NAME'] = 'Holiday - Christmas';
$theme[29]['PATH'] = SM_PATH . 'themes/darkness.php';
$theme[29]['NAME'] = 'Darkness (Changes)';
$theme[30]['PATH'] = SM_PATH . 'themes/random.php';
$theme[30]['NAME'] = 'Random (Changes every login)';
$theme[31]['PATH'] = SM_PATH . 'themes/midnight.php';
$theme[31]['NAME'] = 'Midnight'; 
$theme[32]['PATH'] = SM_PATH . 'themes/alien_glow.php';  
$theme[32]['NAME'] = 'Alien Glow';
$theme[33]['PATH'] = SM_PATH . 'themes/dark_green.php';
$theme[33]['NAME'] = 'Dark Green';
$theme[34]['PATH'] = SM_PATH . 'themes/penguin.php';
$theme[34]['NAME'] = 'Penguin';
$theme[35]['PATH'] = SM_PATH . 'themes/minimal_bw.php'; 
$theme[35]['NAME'] = 'Minimal BW';
$theme[36]['PATH'] = SM_PATH . 'themes/redmond.php';
$theme[36]['NAME'] = 'Redmond';
$theme[37]['PATH'] = SM_PATH . 'themes/netstyle_theme.php';
$theme[37]['NAME'] = 'Net Style';
$theme[38]['PATH'] = SM_PATH . 'themes/silver_steel_theme.php';
$theme[38]['NAME'] = 'Silver Steel';
$theme[39]['PATH'] = SM_PATH . 'themes/simple_green_theme.php';
$theme[39]['NAME'] = 'Simple Green';
$theme[40]['PATH'] = SM_PATH . 'themes/wood_theme.php';
$theme[40]['NAME'] = 'Wood';
$theme[41]['PATH'] = SM_PATH . 'themes/bluesome.php';
$theme[41]['NAME'] = 'Bluesome';
$theme[42]['PATH'] = SM_PATH . 'themes/simple_green2.php';
$theme[42]['NAME'] = 'Simple Green 2';
$theme[43]['PATH'] = SM_PATH . 'themes/simple_purple.php';
$theme[43]['NAME'] = 'Simple Purple';

$default_use_javascript_addr_book = false;
$abook_global_file = '';
$abook_global_file_writeable = false;

$addrbook_dsn = '';
$addrbook_table = 'address';

$prefs_dsn = '';
$prefs_table = 'userprefs';
$prefs_user_field = 'user';
$prefs_key_field = 'prefkey';
$prefs_val_field = 'prefval';
$addrbook_global_dsn = '';   
$addrbook_global_table = 'global_abook';
$addrbook_global_writeable = false;
$addrbook_global_listing = false;  

$no_list_for_subscribe = false;
$smtp_auth_mech = 'none';
$imap_auth_mech = 'login';
$use_imap_tls = false;
$use_smtp_tls = false;
$session_name = 'SQMSESSID';

@include SM_PATH . 'config/config_local.php';


If you need any more information please say so. I need help!
/**
 * Make sure there are no characters after the PHP closing
 * tag below (including newline characters and whitespace).
 * Otherwise, that character will cause the headers to be  
 * sent and regular output to begin, which will majorly screw
 * things up when we try to send more headers later.
 */
?>

---

### Post by svehex on 2006-11-16
Nevermind...I fixed it myself

Kubuntu seems to have a limited dovecot package: dovecot-common
So this is what I had to do:

sudo apt-get install dovecot-pop3d
sudo apt-get install dovecot-imapd
sudo /etc/init.d/dovecot restart
sudo joe /etc/shorewall/rules
	ACCEPT   net            fw              tcp     25
sudo /etc/init.d/shorewall restart
Set path in dovecot to /var/mail under ~mail
Set path in postfix to default (var/something)

Now it works just fine :)

---

### Post by svehex on 2006-11-16
Well, maybe I should mention thath I threw out courier and installed dovecot. That makes the post above a bit clearer.

---

