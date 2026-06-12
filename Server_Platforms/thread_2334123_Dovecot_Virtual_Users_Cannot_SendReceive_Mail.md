---
title: "Dovecot Virtual Users Cannot Send/Receive Mail"
date: 2016-08-16
forum: Server Platforms
---

### Post by Elijah_Duffy on 2016-08-16
I'm not sure if this is the right sub-forum in which to ask this, but oh well.

I got Dovecot + Postfix running a few days ago in conjunction with Squirrelmail. Soon after, I got tired of "Mail for nuts," and switched to RainLoop. It seems to be working fine however, only with literal users. Virtual users can login, but cannot send OR receive mail. I've looked around, but can't figure anything out. One post indicated that this was caused by having destinations other than "localhost" in the Postfix config, but I still had the same issue.

I think I've created all the needed accounts. The userDB is under the vmail account.

Postfix (main.cf):
```
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
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = server1.endev.xyz
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
mailbox_command = 
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = encrypt
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
```

Dovecot (dovecot.conf):
```
## Dovecot configuration file

# If you're in a hurry, see http://wiki2.dovecot.org/QuickConfiguration

# "doveconf -n" command gives a clean output of the changed settings. Use it
# instead of copy&pasting files when posting to the Dovecot mailing list.

# '#' character and everything after it is treated as comments. Extra spaces
# and tabs are ignored. If you want to use either of these explicitly, put the
# value inside quotes, eg.: key = "# char and trailing whitespace  "

# Most (but not all) settings can be overridden by different protocols and/or
# source/destination IPs by placing the settings inside sections, for example:
# protocol imap { }, local 127.0.0.1 { }, remote 10.0.0.0/8 { }

# Default values are shown for each setting, it's not required to uncomment
# those. These are exceptions to this though: No sections (e.g. namespace {})
# or plugin settings are added by default, they're listed only as examples.
# Paths are also just examples with the real defaults being based on configure
# options. The paths listed here are for configure --prefix=/usr
# --sysconfdir=/etc --localstatedir=/var

# Enable installed protocols
!include_try /usr/share/dovecot/protocols.d/*.protocol

# A comma separated list of IPs or hosts where to listen in for connections. 
# "*" listens in all IPv4 interfaces, "::" listens in all IPv6 interfaces.
# If you want to specify non-default ports or anything more complex,
# edit conf.d/master.conf.
#listen = *, ::

# Base directory where to store runtime data.
#base_dir = /var/run/dovecot/

# Name of this instance. In multi-instance setup doveadm and other commands
# can use -i <instance_name> to select which instance is used (an alternative
# to -c <config_path>). The instance name is also added to Dovecot processes
# in ps output.
#instance_name = dovecot

# Greeting message for clients.
#login_greeting = Dovecot ready.

# Space separated list of trusted network ranges. Connections from these
# IPs are allowed to override their IP addresses and ports (for logging and
# for authentication checks). disable_plaintext_auth is also ignored for
# these networks. Typically you'd specify your IMAP proxy servers here.
#login_trusted_networks =

# Space separated list of login access check sockets (e.g. tcpwrap)
#login_access_sockets = 

# With proxy_maybe=yes if proxy destination matches any of these IPs, don't do
# proxying. This isn't necessary normally, but may be useful if the destination
# IP is e.g. a load balancer's IP.
#auth_proxy_self =

# Show more verbose process titles (in ps). Currently shows user name and
# IP address. Useful for seeing who are actually using the IMAP processes
# (eg. shared mailboxes or if same uid is used for multiple accounts).
#verbose_proctitle = no

# Should all processes be killed when Dovecot master process shuts down.
# Setting this to "no" means that Dovecot can be upgraded without
# forcing existing client connections to close (although that could also be
# a problem if the upgrade is e.g. because of a security fix).
#shutdown_clients = yes

# If non-zero, run mail commands via this many connections to doveadm server,
# instead of running them directly in the same process.
#doveadm_worker_count = 0
# UNIX socket or host:port used for connecting to doveadm server
#doveadm_socket_path = doveadm-server

# Space separated list of environment variables that are preserved on Dovecot
# startup and passed down to all of its child processes. You can also give
# key=value pairs to always set specific settings.
#import_environment = TZ

##
## Dictionary server settings
##

# Dictionary can be used to store key=value lists. This is used by several
# plugins. The dictionary can be accessed either directly or though a
# dictionary server. The following dict block maps dictionary names to URIs
# when the server is used. These can then be referenced using URIs in format
# "proxy::<name>".

dict {
  #quota = mysql:/etc/dovecot/dovecot-dict-sql.conf.ext
  #expire = sqlite:/etc/dovecot/dovecot-dict-sql.conf.ext
}

# Most of the actual configuration gets included below. The filenames are
# first sorted by their ASCII value and parsed in that order. The 00-prefixes
# in filenames are intended to make it easier to understand the ordering.
!include conf.d/*.conf

# A config file can also tried to be included without giving an error if
# it's not found:
!include_try local.conf


# CUSTOM CONFIG #

# Enabled Protocols
protocols = pop3 imap
pop3_uidl_format = %08Xu%08Xv

# Plugins
mail_plugins = $mail_plugins quota

# IMAP Protocol
protocol imap {
    listen = *:143
    ssl_listen = *:993
    imap_client_workarounds = tb-extra-mailbox-sep
    mail_plugins = $mail_plugins imap_quota
}

# POP3 Protocol
protocol pop3 {
    listen = *:110
    ssl_listen = *:995
}

plugin {
    quota = maildir
}

# SSL
ssl = yes
ssl_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
ssl_key_file = /etc/ssl/private/ssl-cert-snakeoil.key


# logs
log_path = /var/log/dovecot.log
info_log_path = /var/log/dovecot-info.log

# Authentication configuration:
auth_verbose = yes
auth_mechanisms = plain

passdb {
  driver = passwd-file
  args = scheme=plain-md5 username_format=%n /home/vmail/dovedb
}
userdb {
  driver = passwd-file
  args = username_format=%n /home/vmail/dovedb
  default_fields = uid=vmail gid=vmail home=/home/vmail/%u
}

protocol lda {
  postmaster_address = postmaster@endev.xyz
}


```

RainLoop (application.ini):
```
; RainLoop Webmail configuration file
; Please don't add custom parameters here, those will be overwritten

[webmail]
; Text displayed as page title
title = "Mail | enDEV"

; Text displayed on startup
loading_description = "enDEV"
favicon_url = ""

; Theme used by default
theme = "Default"

; Allow theme selection on settings screen
allow_themes = On
allow_user_background = On

; Language used by default
language = "en"

; Admin Panel interface language
language_admin = "en"

; Allow language selection on settings screen
allow_languages_on_settings = On
allow_additional_accounts = On
allow_additional_identities = On

;  Number of messages displayed on page by default
messages_per_page = 20

; File size limit (MB) for file upload on compose screen
; 0 for unlimited.
attachment_size_limit = 25

[interface]
show_attachment_thumbnail = On
use_native_scrollbars = Off

[branding]
login_logo = ""
login_background = ""
login_desc = ""
login_css = ""
login_powered = On
user_css = ""
user_logo = ""
user_logo_title = ""
user_logo_message = ""
user_iframe_message = ""
welcome_page_url = ""
welcome_page_display = "none"

[contacts]
; Enable contacts
enable = On
allow_sharing = On
allow_sync = On
sync_interval = 20
type = "mysql"
pdo_dsn = "mysql:host=127.0.0.1;port=3306;dbname=rainloop"
pdo_user = "rainloop"
pdo_password = "db29r!"
suggestions_limit = 30

[security]
; Enable CSRF protection (http://en.wikipedia.org/wiki/Cross-site_request_forgery)
csrf_protection = On
custom_server_signature = "RainLoop"
x_frame_options_header = ""
openpgp = On
openpgp_public_key_server = ""
use_rsa_encryption = Off

; Login and password for web admin panel
admin_login = "octacian"
admin_password = "f2a937755870d2895f5aa87a60904bc6"

; Access settings
allow_admin_panel = On
allow_two_factor_auth = On
force_two_factor_auth = Off
admin_panel_host = ""
admin_panel_key = "admin"
content_security_policy = ""
core_install_access_domain = ""

[ssl]
; Require verification of SSL certificate used.
verify_certificate = Off

; Allow self-signed certificates. Requires verify_certificate.
allow_self_signed = On

; Location of Certificate Authority file on local filesystem (/etc/ssl/certs/ca-certificates.crt)
cafile = ""

; capath must be a correctly hashed certificate directory. (/etc/ssl/certs/)
capath = ""

[capa]
folders = On
composer = On
contacts = On
settings = On
quota = On
help = On
reload = On
search = On
search_adv = On
filters = On
x-templates = Off
dangerous_actions = On
message_actions = On
messagelist_actions = On
attachments_actions = On

[login]
default_domain = "endev.xyz"

; Allow language selection on webmail login screen
allow_languages_on_login = On
determine_user_language = On
determine_user_domain = Off
welcome_page = Off
forgot_password_link_url = ""
registration_link_url = ""

; This option allows webmail to remember the logged in user
; once they closed the browser window.
; 
; Values:
;   "DefaultOff" - can be used, disabled by default;
;   "DefaultOn"  - can be used, enabled by default;
;   "Unused"     - cannot be used
sign_me_auto = "DefaultOff"

[plugins]
; Enable plugin support
enable = Off

; List of enabled plugins
enabled_list = ""

[defaults]
; Editor mode used by default (Plain, Html, HtmlForced or PlainForced)
view_editor_type = "Html"

; layout: 0 - no preview, 1 - side preview, 2 - bottom preview
view_layout = 1
view_use_checkboxes = On
autologout = 30
show_images = Off
contacts_autosave = On
mail_use_threads = Off
mail_reply_same_folder = Off

[logs]
; Enable logging
enable = Off

; Logs entire request only if error occured (php requred)
write_on_error_only = Off

; Logs entire request only if php error occured
write_on_php_error_only = Off

; Logs entire request only if request timeout (in seconds) occured.
write_on_timeout_only = 0

; Required for development purposes only.
; Disabling this option is not recommended.
hide_passwords = On
time_offset = 0
session_filter = ""

; Log filename.
; For security reasons, some characters are removed from filename.
; Allows for pattern-based folder creation (see examples below).
; 
; Patterns:
;   {date:Y-m-d}  - Replaced by pattern-based date
;                   Detailed info: http://www.php.net/manual/en/function.date.php
;   {user:email}  - Replaced by user's email address
;                   If user is not logged in, value is set to "unknown"
;   {user:login}  - Replaced by user's login (the user part of an email)
;                   If user is not logged in, value is set to "unknown"
;   {user:domain} - Replaced by user's domain name (the domain part of an email)
;                   If user is not logged in, value is set to "unknown"
;   {user:uid}    - Replaced by user's UID regardless of account currently used
; 
;   {user:ip}
;   {request:ip}  - Replaced by user's IP address
; 
; Others:
;   {imap:login} {imap:host} {imap:port}
;   {smtp:login} {smtp:host} {smtp:port}
; 
; Examples:
;   filename = "log-{date:Y-m-d}.txt"
;   filename = "{date:Y-m-d}/{user:domain}/{user:email}_{user:uid}.log"
;   filename = "{user:email}-{date:Y-m-d}.txt"
filename = "log-{date:Y-m-d}.txt"

; Enable auth logging in a separate file (for fail2ban)
auth_logging = Off
auth_logging_filename = "fail2ban/auth-{date:Y-m-d}.txt"
auth_logging_format = "[{date:Y-m-d H:i:s}] Auth failed: ip={request:ip} user={imap:login} host={imap:host} port={imap:port}"

[debug]
; Special option required for development purposes
enable = Off

[social]
; Google
google_enable = Off
google_enable_auth = Off
google_enable_auth_fast = Off
google_enable_drive = Off
google_enable_preview = Off
google_client_id = ""
google_client_secret = ""
google_api_key = ""

; Facebook
fb_enable = Off
fb_app_id = ""
fb_app_secret = ""

; Twitter
twitter_enable = Off
twitter_consumer_key = ""
twitter_consumer_secret = ""

; Dropbox
dropbox_enable = Off
dropbox_api_key = ""

[cache]
; The section controls caching of the entire application.
; 
; Enables caching in the system
enable = On

; Additional caching key. If changed, cache is purged
index = "v1"

; Can be: files, APC, memcache, redis (beta)
fast_cache_driver = "files"

; Additional caching key. If changed, fast cache is purged
fast_cache_index = "v1"

; Browser-level cache. If enabled, caching is maintainted without using files
http = On

; Caching message UIDs when searching and sorting (threading)
server_uids = On

[labs]
; Experimental settings. Handle with care.
; 
allow_mobile_version = On
ignore_folders_subscription = Off
check_new_password_strength = On
update_channel = "stable"
allow_gravatar = On
allow_prefetch = On
allow_smart_html_links = On
cache_system_data = On
date_from_headers = Off
autocreate_system_folders = On
allow_message_append = Off
disable_iconv_if_mbstring_supported = Off
login_fault_delay = 1
log_ajax_response_write_limit = 300
allow_html_editor_source_button = Off
allow_html_editor_biti_buttons = Off
allow_ctrl_enter_on_compose = Off
try_to_detect_hidden_images = Off
hide_dangerous_actions = Off
use_app_debug_js = Off
use_app_debug_css = Off
use_imap_sort = On
use_imap_force_selection = Off
use_imap_list_subscribe = On
use_imap_thread = On
use_imap_move = Off
use_imap_expunge_all_on_delete = Off
imap_forwarded_flag = "$Forwarded"
imap_read_receipt_flag = "$ReadReceipt"
imap_body_text_limit = 555000
imap_message_list_fast_simple_search = On
imap_message_list_count_limit_trigger = 0
imap_message_list_date_filter = 0
imap_message_list_permanent_filter = ""
imap_message_all_headers = Off
imap_large_thread_limit = 50
imap_folder_list_limit = 200
imap_show_login_alert = On
imap_use_auth_plain = On
imap_use_auth_cram_md5 = Off
smtp_show_server_errors = Off
smtp_use_auth_plain = On
smtp_use_auth_cram_md5 = Off
sieve_allow_raw_script = Off
sieve_utf8_folder_name = On
imap_timeout = 300
smtp_timeout = 60
sieve_timeout = 10
domain_list_limit = 99
mail_func_clear_headers = On
mail_func_additional_parameters = Off
favicon_status = On
folders_spec_limit = 50
owncloud_save_folder = "Attachments"
owncloud_suggestions = On
curl_proxy = ""
curl_proxy_auth = ""
in_iframe = Off
force_https = Off
custom_login_link = ""
custom_logout_link = ""
allow_external_login = Off
allow_external_sso = Off
external_sso_key = ""
http_client_ip_check_proxy = Off
fast_cache_memcache_host = "127.0.0.1"
fast_cache_memcache_port = 11211
fast_cache_redis_host = "127.0.0.1"
fast_cache_redis_port = 6379
use_local_proxy_for_external_images = Off
detect_image_exif_orientation = On
cookie_default_path = ""
cookie_default_secure = Off
replace_env_in_configuration = ""
startup_url = ""
nice_social_redirect = On
strict_html_parser = Off
dev_email = ""
dev_password = ""

[version]
current = "1.10.2.145"
saved = "Mon, 15 Aug 2016 21:06:30 +0000"
```

VirtualUserDB (dovedb):
```
oct:{SSHA}*removed*::::::userdb_quota_rule=*:storage=128M
pf:{SSHA}*removed*::::::userdb_quota_rule=*:storage=128M
```

---

### Post by QIII on 2016-08-16
Moved to Server Platforms.

Hopefully you'll draw the right crowd here.

Cheers!

---

