---
title: "Roundcube + dovecot dont work together"
date: 2014-08-01
forum: Server Platforms
---

### Post by finni on 2014-08-01
My OS is Ubuntu server 14.04 LTS and it has roundcube and dovecot from the ubuntu repos. Logging in to local dovecot mailbox works with roundcube. If roundcube session remains open and it checks email for over than 15min (can be even 2-3hours) it gives an error like:
"Connection to IMAP server failed" (localized to my language though)
AND
"Server error: AUTHENTICATE PLAIN: Authentication failed."

Only thing that repairs this is restarting dovecot server.

I have tried various fixes proposed in various threads, but no luck.

---

### Post by nerdtron on 2014-08-01
Why not try an easy-to-use installer which installs a complete email platform. [http://www.iredmail.org/install_iredmail_on_ubuntu.html](http://www.iredmail.org/install_iredmail_on_ubuntu.html)
Contains postfix, dovecot, iredmail etc.

---

### Post by ljbade2 on 2014-08-03
Can you look at /var/log/mail.err and mail.log log for error messages and post any here.

Also post the Dovecot and Roundcube configuration you are using.

Make sure to delete any sensitive info first.

I managed to get a working Dovecot and Roundcube using the default settings and packages in 15mins on 14.04.

So it should be working unless you did something wrong in the configuration somewhere.

---

### Post by finni on 2014-08-04
> **ljbade2 said:**
> Can you look at /var/log/mail.err and mail.log log for error messages and post any here.

Also post the Dovecot and Roundcube configuration you are using.

Make sure to delete any sensitive info first.

I managed to get a working Dovecot and Roundcube using the default settings and packages in 15mins on 14.04.

So it should be working unless you did something wrong in the configuration somewhere.

Here are logs and configuration files:

/var/log/mail.log
```

Aug  4 10:09:21 beatrix dovecot: auth-worker: Error: no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Aug  4 10:09:21 beatrix dovecot: imap-login: Login: user=<user_renamed>, method=PLAIN, rip=::1, lip=::1, mpid=12362, secured, session=<71gNa8j/YgAAAAAAAAAAAAAAAAAAAAAB>
Aug  4 10:09:21 beatrix dovecot: imap(user_renamed): Disconnected: Logged out in=50 out=469
Aug  4 10:09:22 beatrix dovecot: auth-worker: Error: no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Aug  4 10:09:23 beatrix dovecot: imap-login: Login: user=<user_renamed>, method=PLAIN, rip=::1, lip=::1, mpid=12364, secured, session=<ZGUia8j/YwAAAAAAAAAAAAAAAAAAAAAB>
Aug  4 10:09:23 beatrix dovecot: imap(user_renamed): Disconnected: Logged out in=347 out=26246
Aug  4 10:09:51 beatrix dovecot: imap-login: Disconnected (auth failed, 1 attempts in 6 secs): user=<user_renamed>, method=PLAIN, rip=::1, lip=::1, secured, session=<SPN6bMj/ZAAAAAAAAAAAAAAAAAAAAAAB>
Aug  4 10:10:02 beatrix dovecot: imap-login: Disconnected (auth failed, 1 attempts in 10 secs): user=<user_renamed>, method=PLAIN, rip=::1, lip=::1, secured, session=<K5zpbMj/ZQAAAAAAAAAAAAAAAAAAAAAB>

```
/var/log/mail.err
```

Aug  4 11:06:07 beatrix dovecot: auth-worker: Error: no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Aug  4 11:07:07 beatrix dovecot: auth-worker: Error: no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Aug  4 11:08:08 beatrix dovecot: auth-worker: Error: no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Aug  4 11:09:07 beatrix dovecot: auth-worker: Error: no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Aug  4 11:10:07 beatrix dovecot: auth-worker: Error: no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory

```
/var/log/syslog
```

Aug  4 10:09:21 beatrix dovecot: auth-worker: Error: no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Aug  4 10:09:21 beatrix dovecot: imap-login: Login: user=<user_renamed>, method=PLAIN, rip=::1, lip=::1, mpid=12362, secured, session=<71gNa8j/YgAAAAAAAAAAAAAAAAAAAAAB>
Aug  4 10:09:21 beatrix dovecot: imap(user_renamed): Disconnected: Logged out in=50 out=469
Aug  4 10:09:22 beatrix dovecot: auth-worker: Error: no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Aug  4 10:09:23 beatrix dovecot: imap-login: Login: user=<user_renamed>, method=PLAIN, rip=::1, lip=::1, mpid=12364, secured, session=<ZGUia8j/YwAAAAAAAAAAAAAAAAAAAAAB>
Aug  4 10:09:23 beatrix dovecot: imap(user_renamed): Disconnected: Logged out in=347 out=26246
Aug  4 10:09:51 beatrix dovecot: imap-login: Disconnected (auth failed, 1 attempts in 6 secs): user=<user_renamed>, method=PLAIN, rip=::1, lip=::1, secured, session=<SP
N6bMj/ZAAAAAAAAAAAAAAAAAAAAAAB>
Aug  4 10:10:02 beatrix dovecot: imap-login: Disconnected (auth failed, 1 attempts in 10 secs): user=<user_renamed>, method=PLAIN, rip=::1, lip=::1, secured, session=<K
5zpbMj/ZQAAAAAAAAAAAAAAAAAAAAAB>
Aug  4 10:10:50 beatrix dovecot: imap-login: Disconnected (auth failed, 1 attempts in 5 secs): user=<user_renamed>, method=PLAIN, rip=::1, lip=::1, secured, session=<2b
gNcMj/agAAAAAAAAAAAAAAAAAAAAAB>

```
/var/log/roundcube/errors: (There is no errors here, nothing, just empty)
```


```
/var/log/roundcube/imap:
```

[04-Aug-2014 10:09:23 +0300]: [E0E7] C: A0008 LOGOUT
[04-Aug-2014 10:09:23 +0300]: [E0E7] S: * BYE Logging out
[04-Aug-2014 10:09:23 +0300]: [E0E7] S: A0008 OK Logout completed.
[04-Aug-2014 10:09:45 +0300]: [5C5E] S: * OK [CAPABILITY IMAP4rev1 LITERAL+ SASL-IR LOGIN-REFERRALS ID ENABLE IDLE STARTTLS AUTH=PLAIN] Dovecot (Ubuntu) ready.
[04-Aug-2014 10:09:45 +0300]: [5C5E] C: A0001 ID ("name" "Roundcube" "version" "0.9.5" "php" "5.5.9-1ubuntu4.3" "os" "Linux" "command" "/mail/?_task=mail&_mbox=nic&_folderlist=1&_list=1&_action=refresh&_remote=1&_unlock=loading1407136183737&_=1407136183769")
[04-Aug-2014 10:09:45 +0300]: [5C5E] S: * ID ("name" "Dovecot")
[04-Aug-2014 10:09:45 +0300]: [5C5E] S: A0001 OK ID completed.
[04-Aug-2014 10:09:45 +0300]: [5C5E] C: A0002 AUTHENTICATE PLAIN {base64_encoded_user_password_combination_removed}
[04-Aug-2014 10:09:51 +0300]: [5C5E] S: A0002 NO [AUTHENTICATIONFAILED] Authentication failed.
[04-Aug-2014 10:09:52 +0300]: [FD82] S: * OK [CAPABILITY IMAP4rev1 LITERAL+ SASL-IR LOGIN-REFERRALS ID ENABLE IDLE STARTTLS AUTH=PLAIN] Dovecot (Ubuntu) ready.
[04-Aug-2014 10:09:52 +0300]: [FD82] C: A0001 ID ("name" "Roundcube" "version" "0.9.5" "php" "5.5.9-1ubuntu4.3" "os" "Linux" "command" "/mail/?_task=mail&_refresh=1&_mbox=Drafts&_page=1&_action=list&_remote=1&_unlock=loading1407136191090&_=1407136191093")
[04-Aug-2014 10:09:52 +0300]: [FD82] S: * ID ("name" "Dovecot")
[04-Aug-2014 10:09:52 +0300]: [FD82] S: A0001 OK ID completed.
[04-Aug-2014 10:09:52 +0300]: [FD82] C: A0002 AUTHENTICATE PLAIN {base64_encoded_user_password_combination_removed}
[04-Aug-2014 10:10:02 +0300]: [FD82] S: A0002 NO [AUTHENTICATIONFAILED] Authentication failed.
[04-Aug-2014 10:10:45 +0300]: [9E87] S: * OK [CAPABILITY IMAP4rev1 LITERAL+ SASL-IR LOGIN-REFERRALS ID ENABLE IDLE STARTTLS AUTH=PLAIN] Dovecot (Ubuntu) ready.
[04-Aug-2014 10:10:45 +0300]: [9E87] C: A0001 ID ("name" "Roundcube" "version" "0.9.5" "php" "5.5.9-1ubuntu4.3" "os" "Linux" "command" "/mail/?_task=mail&_mbox=Drafts&_folderlist=1&_list=1&_action=refresh&_remote=1&_unlock=loading1407136243736&_=1407136243743")
[04-Aug-2014 10:10:45 +0300]: [9E87] S: * ID ("name" "Dovecot")
[04-Aug-2014 10:10:45 +0300]: [9E87] S: A0001 OK ID completed.
[04-Aug-2014 10:10:45 +0300]: [9E87] C: A0002 AUTHENTICATE PLAIN {base64_encoded_user_password_combination_removed}
[04-Aug-2014 10:10:50 +0300]: [9E87] S: A0002 NO [AUTHENTICATIONFAILED] Authentication failed.

```

/etc/dovecot/dovecot.conf
```

## Dovecot configuration file

# If you're in a hurry, see http://wiki.dovecot.org/QuickConfiguration

# "dovecot -n" command gives a clean output of the changed settings. Use it
# instead of copy&pasting this file when posting to the Dovecot mailing list.

# '#' character and everything after it is treated as comments. Extra spaces
# and tabs are ignored. If you want to use either of these explicitly, put the
# value inside quotes, eg.: key = "# char and trailing whitespace  "

# Default values are shown for each setting, it's not required to uncomment
# those. These are exceptions to this though: No sections (e.g. namespace {})
# or plugin settings are added by default, they're listed only as examples.
# Paths are also just examples with the real defaults being based on configure
# options. The paths listed here are for configure --prefix=/usr
# --sysconfdir=/etc --localstatedir=/var --with-ssldir=/etc/ssl

# Base directory where to store runtime data.
#base_dir = /var/run/dovecot

# Protocols we want to be serving: imap imaps pop3 pop3s managesieve
# If you only want to use dovecot-auth, you can set this to "none".
#protocols = imap imaps
protocols = imap

# A space separated list of IP or host addresses where to listen in for
# connections. "*" listens in all IPv4 interfaces. "[::]" listens in all IPv6
# interfaces. Use "*, [::]" for listening both IPv4 and IPv6.
#
# If you want to specify ports for each service, you will need to configure
# these settings inside the protocol imap/pop3/managesieve { ... } section, 
# so you can specify different ports for IMAP/POP3/MANAGESIEVE. For example:
#   protocol imap {
#     listen = *:10143
#     ssl_listen = *:10943
#     ..
#   }
#   protocol pop3 {
#     listen = *:10100
#     ..
#   }
#   protocol managesieve {
#     listen = *:12000
#     ..
#   }
#listen = *

# Disable LOGIN command and all other plaintext authentications unless
# SSL/TLS is used (LOGINDISABLED capability). Note that if the remote IP
# matches the local IP (ie. you're connecting from the same computer), the
# connection is considered secure and plaintext authentication is allowed.
#disable_plaintext_auth = yes

# Should all IMAP and POP3 processes be killed when Dovecot master process
# shuts down. Setting this to "no" means that Dovecot can be upgraded without
# forcing existing client connections to close (although that could also be
# a problem if the upgrade is eg. because of a security fix). This however
# means that after master process has died, the client processes can't write
# to log files anymore.
#shutdown_clients = yes

##
## Logging
##

# Log file to use for error messages, instead of sending them to syslog.
# /dev/stderr can be used to log into stderr.
#log_path = 

# Log file to use for informational and debug messages.
# Default is the same as log_path.
#info_log_path = 

# Prefix for each line written to log file. % codes are in strftime(3)
# format.
#log_timestamp = "%b %d %H:%M:%S "
log_timestamp = "%Y-%m-%d %H:%M:%S "

# Syslog facility to use if you're logging to syslog. Usually if you don't
# want to use "mail", you'll use local0..local7. Also other standard
# facilities are supported.
#syslog_facility = mail

##
## SSL settings
##

# IP or host address where to listen in for SSL connections. Remember to also
# add imaps and/or pop3s to protocols setting. Defaults to same as "listen"
# setting if not specified.
#ssl_listen =

# SSL/TLS support: yes, no, required. </usr/share/doc/dovecot-common/wiki/SSL.txt>
#ssl = yes

# PEM encoded X.509 SSL/TLS certificate and private key. They're opened before
# dropping root privileges, so keep the key file unreadable by anyone but
# root.
#ssl_cert_file = /etc/ssl/certs/dovecot.pem
#ssl_key_file = /etc/ssl/private/dovecot.pem

# If key file is password protected, give the password here. Alternatively
# give it when starting dovecot with -p parameter. Since this file is often
# world-readable, you may want to place this setting instead to a different
# root owned 0600 file by using !include_try <path>.
#ssl_key_password =

# File containing trusted SSL certificate authorities. Set this only if you
# intend to use ssl_verify_client_cert=yes. The CAfile should contain the
# CA-certificate(s) followed by the matching CRL(s).
#ssl_ca_file = 

# Request client to send a certificate. If you also want to require it, set
# ssl_require_client_cert=yes in auth section.
#ssl_verify_client_cert = no

# Which field from certificate to use for username. commonName and
# x500UniqueIdentifier are the usual choices. You'll also need to set
# ssl_username_from_cert=yes.
#ssl_cert_username_field = commonName

# How often to regenerate the SSL parameters file. Generation is quite CPU
# intensive operation. The value is in hours, 0 disables regeneration
# entirely.
#ssl_parameters_regenerate = 168

# SSL ciphers to use
#ssl_cipher_list = ALL:!LOW:!SSLv2

# Show protocol level SSL errors.
#verbose_ssl = no

##
## Login processes
##

# </usr/share/doc/dovecot-common/wiki/LoginProcess.txt>

# Directory where authentication process places authentication UNIX sockets
# which login needs to be able to connect to. The sockets are created when
# running as root, so you don't have to worry about permissions. Note that
# everything in this directory is deleted when Dovecot is started.
#login_dir = /var/run/dovecot/login

# chroot login process to the login_dir. Only reason not to do this is if you
# wish to run the whole Dovecot without roots. </usr/share/doc/dovecot-common/wiki/Rootless.txt>
#login_chroot = yes

# User to use for the login process. Create a completely new user for this,
# and don't use it anywhere else. The user must also belong to a group where
# only it has access, it's used to control access for authentication process.
# Note that this user is NOT used to access mails. </usr/share/doc/dovecot-common/wiki/UserIds.txt>
#login_user = dovecot

# Set max. process size in megabytes. If you don't use
# login_process_per_connection you might need to grow this.
#login_process_size = 64

# Should each login be processed in it's own process (yes), or should one
# login process be allowed to process multiple connections (no)? Yes is more
# secure, espcially with SSL/TLS enabled. No is faster since there's no need
# to create processes all the time.
#login_process_per_connection = yes

# Number of login processes to keep for listening new connections.
#login_processes_count = 3

# Maximum number of login processes to create. The listening process count
# usually stays at login_processes_count, but when multiple users start logging
# in at the same time more extra processes are created. To prevent fork-bombing
# we check only once in a second if new processes should be created - if all
# of them are used at the time, we double their amount until the limit set by
# this setting is reached.
#login_max_processes_count = 128

# Maximum number of connections allowed per each login process. This setting
# is used only if login_process_per_connection=no. Once the limit is reached,
# the process notifies master so that it can create a new login process.
#login_max_connections = 256

# Greeting message for clients.
#login_greeting = Dovecot ready.

# Space separated list of trusted network ranges. Connections from these
# IPs are allowed to override their IP addresses and ports (for logging and
# for authentication checks). disable_plaintext_auth is also ignored for
# these networks. Typically you'd specify your IMAP proxy servers here.
#login_trusted_networks =

# Space-separated list of elements we want to log. The elements which have
# a non-empty variable value are joined together to form a comma-separated
# string.
#login_log_format_elements = user=<%u> method=%m rip=%r lip=%l %c

# Login log format. %$ contains login_log_format_elements string, %s contains
# the data we want to log.
#login_log_format = %$: %s

##
## Mailbox locations and namespaces
##

# Location for users' mailboxes. This is the same as the old default_mail_env
# setting. The default is empty, which means that Dovecot tries to find the
# mailboxes automatically. This won't work if the user doesn't have any mail
# yet, so you should explicitly tell Dovecot the full location.
#
# If you're using mbox, giving a path to the INBOX file (eg. /var/mail/%u)
# isn't enough. You'll also need to tell Dovecot where the other mailboxes are
# kept. This is called the "root mail directory", and it must be the first
# path given in the mail_location setting.
#
# There are a few special variables you can use, eg.:
#
#   %u - username
#   %n - user part in user@domain, same as %u if there's no domain
#   %d - domain part in user@domain, empty if there's no domain
#   %h - home directory
#
# See </usr/share/doc/dovecot-common/wiki/Variables.txt> for full list.
# Some examples:
#
#   mail_location = maildir:~/Maildir
#   mail_location = mbox:~/mail:INBOX=/var/mail/%u
#   mail_location = mbox:/var/mail/%d/%1n/%n:INDEX=/var/indexes/%d/%1n/%n
#
# </usr/share/doc/dovecot-common/wiki/MailLocation.txt>
#
#mail_location = 
mail_location = maildir:~/Maildir

# If you need to set multiple mailbox locations or want to change default
# namespace settings, you can do it by defining namespace sections.
#
# You can have private, shared and public namespaces. Private namespaces
# are for user's personal mails. Shared namespaces are for accessing other
# users' mailboxes that have been shared. Public namespaces are for shared
# mailboxes that are managed by sysadmin. If you create any shared or public
# namespaces you'll typically want to enable ACL plugin also, otherwise all
# users can access all the shared mailboxes, assuming they have permissions
# on filesystem level to do so.
#
# REMEMBER: If you add any namespaces, the default namespace must be added
# explicitly, ie. mail_location does nothing unless you have a namespace
# without a location setting. Default namespace is simply done by having a
# namespace with empty prefix.
#namespace private {
   # Hierarchy separator to use. You should use the same separator for all
   # namespaces or some clients get confused. '/' is usually a good one.
   # The default however depends on the underlying mail storage format.
   #separator = 

   # Prefix required to access this namespace. This needs to be different for
   # all namespaces. For example "Public/".
   #prefix = 

   # Physical location of the mailbox. This is in same format as
   # mail_location, which is also the default for it.
   #location =

   # There can be only one INBOX, and this setting defines which namespace
   # has it.
   #inbox = no

   # If namespace is hidden, it's not advertised to clients via NAMESPACE
   # extension. You'll most likely also want to set list=no. This is mostly
   # useful when converting from another server with different namespaces which
   # you want to deprecate but still keep working. For example you can create
   # hidden namespaces with prefixes "~/mail/", "~%u/mail/" and "mail/".
   #hidden = yes

   # Show the mailboxes under this namespace with LIST command. This makes the
   # namespace visible for clients that don't support NAMESPACE extension.
   # "children" value lists child mailboxes, but hides the namespace prefix.
   #list = yes

   # Namespace handles its own subscriptions. If set to "no", the parent
   # namespace handles them (empty prefix should always have this as "yes")
   #subscriptions = yes
#}

# Example shared namespace configuration
#namespace shared {
   #separator = /

   # Mailboxes are visible under "shared/user@domain/"
   # %%n, %%d and %%u are expanded to the destination user.
   #prefix = shared/%%u/

   # Mail location for other users' mailboxes. Note that %variables and ~/
   # expands to the logged in user's data. %%n, %%d, %%u and %%h expand to the
   # destination user's data.
   #location = maildir:%%h/Maildir:INDEX=~/Maildir/shared/%%u

   # Use the default namespace for saving subscriptions.
   #subscriptions = no

   # List the shared/ namespace only if there are visible shared mailboxes.
   #list = children
#}

# System user and group used to access mails. If you use multiple, userdb
# can override these by returning uid or gid fields. You can use either numbers
# or names. </usr/share/doc/dovecot-common/wiki/UserIds.txt>
#mail_uid =
#mail_gid =

# Group to enable temporarily for privileged operations. Currently this is
# used only with INBOX when either its initial creation or dotlocking fails.
# Typically this is set to "mail" to give access to /var/mail.
#mail_privileged_group =
mail_privileged_group = mail

# Grant access to these supplementary groups for mail processes. Typically
# these are used to set up access to shared mailboxes. Note that it may be
# dangerous to set these if users can create symlinks (e.g. if "mail" group is
# set here, ln -s /var/mail ~/mail/var could allow a user to delete others'
# mailboxes, or ln -s /secret/shared/box ~/mail/mybox would allow reading it).
#mail_access_groups =

# Allow full filesystem access to clients. There's no access checks other than
# what the operating system does for the active UID/GID. It works with both
# maildir and mboxes, allowing you to prefix mailboxes names with eg. /path/
# or ~user/.
#mail_full_filesystem_access = no

##
## Mail processes
##

# Enable mail process debugging. This can help you figure out why Dovecot
# isn't finding your mails.
#mail_debug = no

# Log prefix for mail processes. See </usr/share/doc/dovecot-common/wiki/Variables.txt>
# for list of possible variables you can use.
#mail_log_prefix = "%Us(%u): "

# Max. number of lines a mail process is allowed to log per second before it's
# throttled. 0 means unlimited. Typically there's no need to change this
# unless you're using mail_log plugin, which may log a lot. This setting is
# ignored while mail_debug=yes to avoid pointless throttling.
#mail_log_max_lines_per_sec = 10

# Don't use mmap() at all. This is required if you store indexes to shared
# filesystems (NFS or clustered filesystem).
#mmap_disable = no

# Rely on O_EXCL to work when creating dotlock files. NFS supports O_EXCL
# since version 3, so this should be safe to use nowadays by default.
#dotlock_use_excl = yes

# Don't use fsync() or fdatasync() calls. This makes the performance better
# at the cost of potential data loss if the server (or the file server)
# goes down.
#fsync_disable = no

# Mail storage exists in NFS. Set this to yes to make Dovecot flush NFS caches
# whenever needed. If you're using only a single mail server this isn't needed.
#mail_nfs_storage = no
# Mail index files also exist in NFS. Setting this to yes requires
# mmap_disable=yes and fsync_disable=no.
#mail_nfs_index = no

# Locking method for index files. Alternatives are fcntl, flock and dotlock.
# Dotlocking uses some tricks which may create more disk I/O than other locking
# methods. NFS users: flock doesn't work, remember to change mmap_disable.
#lock_method = fcntl

# Drop all privileges before exec()ing the mail process. This is mostly
# meant for debugging, otherwise you don't get core dumps. It could be a small
# security risk if you use single UID for multiple users, as the users could
# ptrace() each others processes then.
#mail_drop_priv_before_exec = no

# Show more verbose process titles (in ps). Currently shows user name and
# IP address. Useful for seeing who are actually using the IMAP processes
# (eg. shared mailboxes or if same uid is used for multiple accounts).
#verbose_proctitle = no

# Valid UID range for users, defaults to 500 and above. This is mostly
# to make sure that users can't log in as daemons or other system users.
# Note that denying root logins is hardcoded to dovecot binary and can't
# be done even if first_valid_uid is set to 0.
#first_valid_uid = 500
#last_valid_uid = 0

# Valid GID range for users, defaults to non-root/wheel. Users having
# non-valid GID as primary group ID aren't allowed to log in. If user
# belongs to supplementary groups with non-valid GIDs, those groups are
# not set.
#first_valid_gid = 1
#last_valid_gid = 0

# Maximum number of running mail processes. When this limit is reached,
# new users aren't allowed to log in.
#max_mail_processes = 512

# Set max. process size in megabytes. Most of the memory goes to mmap()ing
# files, so it shouldn't harm much even if this limit is set pretty high.
#mail_process_size = 256

# Maximum allowed length for mail keyword name. It's only forced when trying
# to create new keywords.
#mail_max_keyword_length = 50

# ':' separated list of directories under which chrooting is allowed for mail
# processes (ie. /var/mail will allow chrooting to /var/mail/foo/bar too).
# This setting doesn't affect login_chroot, mail_chroot or auth chroot
# settings. If this setting is empty, "/./" in home dirs are ignored.
# WARNING: Never add directories here which local users can modify, that
# may lead to root exploit. Usually this should be done only if you don't
# allow shell access for users. </usr/share/doc/dovecot-common/wiki/Chrooting.txt>
#valid_chroot_dirs = 

# Default chroot directory for mail processes. This can be overridden for
# specific users in user database by giving /./ in user's home directory
# (eg. /home/./user chroots into /home). Note that usually there is no real
# need to do chrooting, Dovecot doesn't allow users to access files outside
# their mail directory anyway. If your home directories are prefixed with
# the chroot directory, append "/." to mail_chroot. </usr/share/doc/dovecot-common/wiki/Chrooting.txt>
#mail_chroot = 

##
## Mailbox handling optimizations
##

# The minimum number of mails in a mailbox before updates are done to cache
# file. This allows optimizing Dovecot's behavior to do less disk writes at
# the cost of more disk reads.
#mail_cache_min_mail_count = 0

# When IDLE command is running, mailbox is checked once in a while to see if
# there are any new mails or other changes. This setting defines the minimum
# time in seconds to wait between those checks. Dovecot can also use dnotify,
# inotify and kqueue to find out immediately when changes occur.
#mailbox_idle_check_interval = 30

# Save mails with CR+LF instead of plain LF. This makes sending those mails
# take less CPU, especially with sendfile() syscall with Linux and FreeBSD.
# But it also creates a bit more disk I/O which may just make it slower.
# Also note that if other software reads the mboxes/maildirs, they may handle
# the extra CRs wrong and cause problems.
#mail_save_crlf = no

##
## Maildir-specific settings
##

# By default LIST command returns all entries in maildir beginning with a dot.
# Enabling this option makes Dovecot return only entries which are directories.
# This is done by stat()ing each entry, so it causes more disk I/O.
# (For systems setting struct dirent->d_type, this check is free and it's
# done always regardless of this setting)
#maildir_stat_dirs = no

# When copying a message, do it with hard links whenever possible. This makes
# the performance much better, and it's unlikely to have any side effects.
#maildir_copy_with_hardlinks = yes

# When copying a message, try to preserve the base filename. Only if the
# destination mailbox already contains the same name (ie. the mail is being
# copied there twice), a new name is given. The destination filename check is
# done only by looking at dovecot-uidlist file, so if something outside
# Dovecot does similar filename preserving copies, you may run into problems.
# NOTE: This setting requires maildir_copy_with_hardlinks = yes to work.
#maildir_copy_preserve_filename = no

# Assume Dovecot is the only MUA accessing Maildir: Scan cur/ directory only
# when its mtime changes unexpectedly or when we can't find the mail otherwise.
#maildir_very_dirty_syncs = no

##
## mbox-specific settings
##

# Which locking methods to use for locking mbox. There are four available:
#  dotlock: Create <mailbox>.lock file. This is the oldest and most NFS-safe
#           solution. If you want to use /var/mail/ like directory, the users
#           will need write access to that directory.
#  dotlock_try: Same as dotlock, but if it fails because of permissions or
#               because there isn't enough disk space, just skip it.
#  fcntl  : Use this if possible. Works with NFS too if lockd is used.
#  flock  : May not exist in all systems. Doesn't work with NFS.
#  lockf  : May not exist in all systems. Doesn't work with NFS.
#
# You can use multiple locking methods; if you do the order they're declared
# in is important to avoid deadlocks if other MTAs/MUAs are using multiple
# locking methods as well. Some operating systems don't allow using some of
# them simultaneously.
#
# The Debian value for mbox_write_locks differs from upstream Dovecot. It is
# changed to be compliant with Debian Policy (section 11.6) for NFS safety.
#       Dovecot: mbox_write_locks = dotlock fcntl
#       Debian:  mbox_write_locks = fcntl dotlock
#
#mbox_read_locks = fcntl
#mbox_write_locks = fcntl dotlock

# Maximum time in seconds to wait for lock (all of them) before aborting.
#mbox_lock_timeout = 300

# If dotlock exists but the mailbox isn't modified in any way, override the
# lock file after this many seconds.
#mbox_dotlock_change_timeout = 120

# When mbox changes unexpectedly we have to fully read it to find out what
# changed. If the mbox is large this can take a long time. Since the change
# is usually just a newly appended mail, it'd be faster to simply read the
# new mails. If this setting is enabled, Dovecot does this but still safely
# fallbacks to re-reading the whole mbox file whenever something in mbox isn't
# how it's expected to be. The only real downside to this setting is that if
# some other MUA changes message flags, Dovecot doesn't notice it immediately.
# Note that a full sync is done with SELECT, EXAMINE, EXPUNGE and CHECK 
# commands.
#mbox_dirty_syncs = yes

# Like mbox_dirty_syncs, but don't do full syncs even with SELECT, EXAMINE,
# EXPUNGE or CHECK commands. If this is set, mbox_dirty_syncs is ignored.
#mbox_very_dirty_syncs = no

# Delay writing mbox headers until doing a full write sync (EXPUNGE and CHECK
# commands and when closing the mailbox). This is especially useful for POP3
# where clients often delete all mails. The downside is that our changes
# aren't immediately visible to other MUAs.
#mbox_lazy_writes = yes

# If mbox size is smaller than this (in kilobytes), don't write index files.
# If an index file already exists it's still read, just not updated.
#mbox_min_index_size = 0

##
## dbox-specific settings
##

# Maximum dbox file size in kilobytes until it's rotated.
#dbox_rotate_size = 2048

# Minimum dbox file size in kilobytes before it's rotated
# (overrides dbox_rotate_days)
#dbox_rotate_min_size = 16

# Maximum dbox file age in days until it's rotated. Day always begins from
# midnight, so 1 = today, 2 = yesterday, etc. 0 = check disabled.
#dbox_rotate_days = 0

##
## IMAP specific settings
##

protocol imap {
  # Login executable location.
  #login_executable = /usr/lib/dovecot/imap-login

  # IMAP executable location. Changing this allows you to execute other
  # binaries before the imap process is executed.
  #
  # This would write rawlogs into user's ~/dovecot.rawlog/, if it exists:
  #   mail_executable = /usr/lib/dovecot/rawlog /usr/lib/dovecot/imap
  # </usr/doc/dovecot-common/wiki/Debugging.Rawlog.txt>
  #
  # This would attach gdb into the imap process and write backtraces into
  # /tmp/gdbhelper.* files:
  #   mail_executable = /usr/lib/dovecot/gdbhelper /usr/lib/dovecot/imap
  #
  #mail_executable = /usr/lib/dovecot/imap

  # Maximum IMAP command line length in bytes. Some clients generate very long
  # command lines with huge mailboxes, so you may need to raise this if you get
  # "Too long argument" or "IMAP command line too large" errors often.
  #imap_max_line_length = 65536

  # Maximum number of IMAP connections allowed for a user from each IP address.
  # NOTE: The username is compared case-sensitively.
  mail_max_userip_connections = 500

  # Support for dynamically loadable plugins. mail_plugins is a space separated
  # list of plugins to load.
  #mail_plugins = 
  #mail_plugin_dir = /usr/lib/dovecot/modules/imap

  # IMAP logout format string:
  #  %i - total number of bytes read from client
  #  %o - total number of bytes sent to client
  #imap_logout_format = bytes=%i/%o

  # Override the IMAP CAPABILITY response.
  #imap_capability = 

  # How many seconds to wait between "OK Still here" notifications when
  # client is IDLEing.
  #imap_idle_notify_interval = 120

  # ID field names and values to send to clients. Using * as the value makes
  # Dovecot use the default value. The following fields have default values
  # currently: name, version, os, os-version, support-url, support-email.
  #imap_id_send = 

  # ID fields sent by client to log. * means everything.
  #imap_id_log =

  # Workarounds for various client bugs:
  #   delay-newmail:
  #     Send EXISTS/RECENT new mail notifications only when replying to NOOP
  #     and CHECK commands. Some clients ignore them otherwise, for example OSX
  #     Mail (<v2.1). Outlook Express breaks more badly though, without this it
  #     may show user "Message no longer in server" errors. Note that OE6 still
  #     breaks even with this workaround if synchronization is set to
  #     "Headers Only".
  #   netscape-eoh:
  #     Netscape 4.x breaks if message headers don't end with the empty "end of
  #     headers" line. Normally all messages have this, but setting this
  #     workaround makes sure that Netscape never breaks by adding the line if
  #     it doesn't exist. This is done only for FETCH BODY[HEADER.FIELDS..]
  #     commands. Note that RFC says this shouldn't be done.
  #   tb-extra-mailbox-sep:
  #     With mbox storage a mailbox can contain either mails or submailboxes,
  #     but not both. Thunderbird separates these two by forcing server to
  #     accept '/' suffix in mailbox names in subscriptions list.
  # The list is space-separated.
  #imap_client_workarounds = 
}
  
##
## POP3 specific settings
##

protocol pop3 {
  # Login executable location.
  #login_executable = /usr/lib/dovecot/pop3-login

  # POP3 executable location. See IMAP's mail_executable above for examples
  # how this could be changed.
  #mail_executable = /usr/lib/dovecot/pop3

  # Don't try to set mails non-recent or seen with POP3 sessions. This is
  # mostly intended to reduce disk I/O. With maildir it doesn't move files
  # from new/ to cur/, with mbox it doesn't write Status-header.
  #pop3_no_flag_updates = no

  # Support LAST command which exists in old POP3 specs, but has been removed
  # from new ones. Some clients still wish to use this though. Enabling this
  # makes RSET command clear all \Seen flags from messages.
  #pop3_enable_last = no

  # If mail has X-UIDL header, use it as the mail's UIDL.
  #pop3_reuse_xuidl = no

  # Keep the mailbox locked for the entire POP3 session.
  #pop3_lock_session = no

  # POP3 UIDL (unique mail identifier) format to use. You can use following
  # variables, along with the variable modifiers described in
  # </usr/share/doc/dovecot-common/wiki/Variables.txt> (e.g. %Uf for the
  # filename in uppercase)
  #
  #  %v - Mailbox's IMAP UIDVALIDITY
  #  %u - Mail's IMAP UID
  #  %m - MD5 sum of the mailbox headers in hex (mbox only)
  #  %f - filename (maildir only)
  #
  # If you want UIDL compatibility with other POP3 servers, use:
  #  UW's ipop3d         : %08Xv%08Xu
  #  Courier             : %f or %v-%u (both might be used simultaneosly)
  #  Cyrus (<= 2.1.3)    : %u
  #  Cyrus (>= 2.1.4)    : %v.%u
  #  Dovecot v0.99.x     : %v.%u
  #  tpop3d              : %Mf
  #
  # Note that Outlook 2003 seems to have problems with %v.%u format which was
  # Dovecot's default, so if you're building a new server it would be a good
  # idea to change this. %08Xu%08Xv should be pretty fail-safe.
  #
pop3_uidl_format = %08Xu%08Xv

  # Permanently save UIDLs sent to POP3 clients, so pop3_uidl_format changes
  # won't change those UIDLs. Currently this works only with Maildir.
  #pop3_save_uidl = no

  # POP3 logout format string:
  #  %i - total number of bytes read from client
  #  %o - total number of bytes sent to client
  #  %t - number of TOP commands
  #  %p - number of bytes sent to client as a result of TOP command
  #  %r - number of RETR commands
  #  %b - number of bytes sent to client as a result of RETR command
  #  %d - number of deleted messages
  #  %m - number of messages (before deletion)
  #  %s - mailbox size in bytes (before deletion)
  #pop3_logout_format = top=%t/%p, retr=%r/%b, del=%d/%m, size=%s

  # Maximum number of POP3 connections allowed for a user from each IP address.
  # NOTE: The username is compared case-sensitively.
  mail_max_userip_connections = 100

  # Support for dynamically loadable plugins. mail_plugins is a space separated
  # list of plugins to load.
  #mail_plugins = 
  #mail_plugin_dir = /usr/lib/dovecot/modules/pop3

  # Workarounds for various client bugs:
  #   outlook-no-nuls:
  #     Outlook and Outlook Express hang if mails contain NUL characters.
  #     This setting replaces them with 0x80 character.
  #   oe-ns-eoh:
  #     Outlook Express and Netscape Mail breaks if end of headers-line is
  #     missing. This option simply sends it if it's missing.
  # The list is space-separated.
  #pop3_client_workarounds = 
}

##
## ManageSieve specific settings
##

protocol managesieve {
  # Login executable location.
  #login_executable = /usr/lib/dovecot/managesieve-login

  # ManageSieve executable location. See IMAP's mail_executable above for 
  # examples how this could be changed.
  #mail_executable = /usr/lib/dovecot/managesieve

  # Maximum ManageSieve command line length in bytes. This setting is 
  # directly borrowed from IMAP. But, since long command lines are very
  # unlikely with ManageSieve, changing this will not be very useful.  
  #managesieve_max_line_length = 65536

  # ManageSieve logout format string:
  #  %i - total number of bytes read from client
  #  %o - total number of bytes sent to client
  #managesieve_logout_format = bytes=%i/%o

  # To fool ManageSieve clients that are focused on timesieved you can
  # specify the IMPLEMENTATION capability that the dovecot reports to clients 
  # (default: "dovecot").
  #managesieve_implementation_string = Cyrus timsieved v2.2.13

  # The ManageSieve service also uses the sieve and sieve_dir settings
  # of the Sieve plugin. These are configured in the plugin {} section of
  # this config file. 
}

##
## LDA specific settings
##

#protocol lda {
  # Address to use when sending rejection mails.
  #postmaster_address = postmaster@example.com

  # Hostname to use in various parts of sent mails, eg. in Message-Id.
  # Default is the system's real hostname.
  #hostname = 

  # Support for dynamically loadable plugins. mail_plugins is a space separated
  # list of plugins to load.
  #mail_plugins = 
  #mail_plugin_dir = /usr/lib/dovecot/modules/lda

  # If user is over quota, return with temporary failure instead of
  # bouncing the mail.
  #quota_full_tempfail = no

  # Format to use for logging mail deliveries. You can use variables:
  #  %$ - Delivery status message (e.g. "saved to INBOX")
  #  %m - Message-ID
  #  %s - Subject
  #  %f - From address
  #deliver_log_format = msgid=%m: %$

  # Binary to use for sending mails.
  #sendmail_path = /usr/lib/sendmail

  # Subject: header to use for rejection mails. You can use the same variables
  # as for rejection_reason below.
  #rejection_subject = Rejected: %s

  # Human readable error message for rejection mails. You can use variables:
  #  %n = CRLF, %r = reason, %s = original subject, %t = recipient
  #rejection_reason = Your message to <%t> was automatically rejected:%n%r

  # UNIX socket path to master authentication server to find users.
  #auth_socket_path = /var/run/dovecot/auth-master
#}

##
## Authentication processes
##

# Executable location
#auth_executable = /usr/lib/dovecot/dovecot-auth

# Set max. process size in megabytes.
#auth_process_size = 256

# Authentication cache size in kilobytes. 0 means it's disabled.
# Note that bsdauth, PAM and vpopmail require cache_key to be set for caching
# to be used.
#auth_cache_size = 0
# Time to live in seconds for cached data. After this many seconds the cached
# record is no longer used, *except* if the main database lookup returns
# internal failure. We also try to handle password changes automatically: If
# user's previous authentication was successful, but this one wasn't, the
# cache isn't used. For now this works only with plaintext authentication.
#auth_cache_ttl = 3600
# TTL for negative hits (user not found, password mismatch).
# 0 disables caching them completely.
#auth_cache_negative_ttl = 3600

# Space separated list of realms for SASL authentication mechanisms that need
# them. You can leave it empty if you don't want to support multiple realms.
# Many clients simply use the first one listed here, so keep the default realm
# first.
#auth_realms =

# Default realm/domain to use if none was specified. This is used for both
# SASL realms and appending @domain to username in plaintext logins.
#auth_default_realm = 

# List of allowed characters in username. If the user-given username contains
# a character not listed in here, the login automatically fails. This is just
# an extra check to make sure user can't exploit any potential quote escaping
# vulnerabilities with SQL/LDAP databases. If you want to allow all characters,
# set this value to empty.
#auth_username_chars = abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ01234567890.-_@

# Username character translations before it's looked up from databases. The
# value contains series of from -> to characters. For example "#@/@" means
# that '#' and '/' characters are translated to '@'.
#auth_username_translation =

# Username formatting before it's looked up from databases. You can use
# the standard variables here, eg. %Lu would lowercase the username, %n would
# drop away the domain if it was given, or "%n-AT-%d" would change the '@' into
# "-AT-". This translation is done after auth_username_translation changes.
#auth_username_format =

# If you want to allow master users to log in by specifying the master
# username within the normal username string (ie. not using SASL mechanism's
# support for it), you can specify the separator character here. The format
# is then <username><separator><master username>. UW-IMAP uses "*" as the
# separator, so that could be a good choice.
#auth_master_user_separator =

# Username to use for users logging in with ANONYMOUS SASL mechanism
#auth_anonymous_username = anonymous

# Log unsuccessful authentication attempts and the reasons why they failed.
#auth_verbose = no

# Even more verbose logging for debugging purposes. Shows for example SQL
# queries.
#auth_debug = no

# In case of password mismatches, log the passwords and used scheme so the
# problem can be debugged. Enabling this also enables auth_debug.
#auth_debug_passwords = no

# Maximum number of dovecot-auth worker processes. They're used to execute
# blocking passdb and userdb queries (eg. MySQL and PAM). They're
# automatically created and destroyed as needed.
#auth_worker_max_count = 30

# Host name to use in GSSAPI principal names. The default is to use the
# name returned by gethostname(). Use "$ALL" to allow all keytab entries.
#auth_gssapi_hostname =

# Kerberos keytab to use for the GSSAPI mechanism. Will use the system 
# default (usually /etc/krb5.keytab) if not specified.
#auth_krb5_keytab = 

# Do NTLM and GSS-SPNEGO authentication using Samba's winbind daemon and
# ntlm_auth helper.
# </usr/share/doc/dovecot-common/wiki/Authentication.Mechanisms.Winbind.txt>
#auth_use_winbind = no

# Path for Samba's ntlm_auth helper binary.
#auth_winbind_helper_path = /usr/bin/ntlm_auth

# Number of seconds to delay before replying to failed authentications.
#auth_failure_delay = 2

auth default {
  # Space separated list of wanted authentication mechanisms:
  #   plain login digest-md5 cram-md5 ntlm rpa apop anonymous gssapi otp skey
  #   gss-spnego
  # NOTE: See also disable_plaintext_auth setting.
  mechanisms = plain

  #
  # Password database is used to verify user's password (and nothing more).
  # You can have multiple passdbs and userdbs. This is useful if you want to
  # allow both system users (/etc/passwd) and virtual users to login without
  # duplicating the system users into virtual database.
  #
  # </usr/share/doc/dovecot-common/wiki/PasswordDatabase.txt>
  #
  # By adding master=yes setting inside a passdb you make the passdb a list
  # of "master users", who can log in as anyone else. Unless you're using PAM,
  # you probably still want the destination user to be looked up from passdb
  # that it really exists. This can be done by adding pass=yes setting to the
  # master passdb. </usr/share/doc/dovecot-common/wiki/Authentication.MasterUsers.txt>

  # Users can be temporarily disabled by adding a passdb with deny=yes.
  # If the user is found from that database, authentication will fail.
  # The deny passdb should always be specified before others, so it gets
  # checked first. Here's an example:

  #passdb passwd-file {
    # File contains a list of usernames, one per line
    #args = /etc/dovecot/dovecot.deny
    #deny = yes
  #}

  # PAM authentication. Preferred nowadays by most systems. 
  # Note that PAM can only be used to verify if user's password is correct,
  # so it can't be used as userdb. If you don't want to use a separate user
  # database (passwd usually), you can use static userdb.
  # REMEMBER: You'll need /etc/pam.d/dovecot file created for PAM
  # authentication to actually work. </usr/share/doc/dovecot-common/wiki/PasswordDatabase.PAM.txt>
  passdb pam {
    # [session=yes] [setcred=yes] [failure_show_msg=yes] [max_requests=<n>]
    # [cache_key=<key>] [<service name>]
    #
    # session=yes makes Dovecot open and immediately close PAM session. Some
    # PAM plugins need this to work, such as pam_mkhomedir.
    #
    # setcred=yes makes Dovecot establish PAM credentials if some PAM plugins
    # need that. They aren't ever deleted though, so this isn't enabled by
    # default.
    #
    # max_requests specifies how many PAM lookups to do in one process before
    # recreating the process. The default is 100, because many PAM plugins
    # leak memory.
    #
    # cache_key can be used to enable authentication caching for PAM
    # (auth_cache_size also needs to be set). It isn't enabled by default
    # because PAM modules can do all kinds of checks besides checking password,
    # such as checking IP address. Dovecot can't know about these checks
    # without some help. cache_key is simply a list of variables (see
    # /usr/share/doc/dovecot-common/wiki/Variables.txt) which must match
    # for the cached data to be used.
    # Here are some examples:
    #   %u - Username must match. Probably sufficient for most uses.
    #   %u%r - Username and remote IP address must match.
    #   %u%s - Username and service (ie. IMAP, POP3) must match.
    # 
    # The service name can contain variables, for example %Ls expands to
    # pop3 or imap.
    #
    # Some examples:
    #   args = session=yes %Ls
    #   args = cache_key=%u dovecot
    #args = dovecot
  }

  # System users (NSS, /etc/passwd, or similiar)
  # In many systems nowadays this uses Name Service Switch, which is
  # configured in /etc/nsswitch.conf. </usr/share/doc/dovecot-common/wiki/AuthDatabase.Passwd.txt>
  #passdb passwd {
    # [blocking=yes] - See userdb passwd for explanation
    #args = 
  #}

  # Shadow passwords for system users (NSS, /etc/shadow or similiar).
  # Deprecated by PAM nowadays.
  # </usr/share/doc/dovecot-common/wiki/PasswordDatabase.Shadow.txt>
  #passdb shadow {
    # [blocking=yes] - See userdb passwd for explanation
    #args = 
  #}

  # PAM-like authentication for OpenBSD.
  # </usr/share/doc/dovecot-common/wiki/PasswordDatabase.BSDAuth.txt>
  #passdb bsdauth {
    # [cache_key=<key>] - See cache_key in PAM for explanation.
    #args =
  #}

  # passwd-like file with specified location
  # </usr/share/doc/dovecot-common/wiki/AuthDatabase.PasswdFile.txt>
  #passdb passwd-file {
    # [scheme=<default password scheme>] [username_format=<format>]
    # <Path for passwd-file>
    #args = 
  #}

  # checkpassword executable authentication
  # NOTE: You will probably want to use "userdb prefetch" with this.
  # </usr/share/doc/dovecot-common/wiki/AuthDatabase.CheckPassword.txt>
  #passdb checkpassword {
    # Path for checkpassword binary
    #args = 
  #}

  # SQL database </usr/share/doc/dovecot-common/wiki/AuthDatabase.SQL.txt>
  #passdb sql {
    # Path for SQL configuration file
    #args = /etc/dovecot/dovecot-sql.conf
  #}

  # LDAP database </usr/share/doc/dovecot-common/wiki/AuthDatabase.LDAP.txt>
  #passdb ldap {
    # Path for LDAP configuration file
    #args = /etc/dovecot/dovecot-ldap.conf
  #}

  # vpopmail authentication </usr/share/doc/dovecot-common/wiki/AuthDatabase.VPopMail.txt>
  #passdb vpopmail {
    # [cache_key=<key>] - See cache_key in PAM for explanation.
    # [quota_template=<template>] - %q expands to Maildir++ quota
    #   (eg. quota_template=quota_rule=*:backend=%q)
    #args =
  #}

  #
  # User database specifies where mails are located and what user/group IDs
  # own them. For single-UID configuration use "static".
  #
  # </usr/share/doc/dovecot-common/wiki/UserDatabase.txt>
  #

  # "prefetch" user database means that the passdb already provided the
  # needed information and there's no need to do a separate userdb lookup.
  # This can be made to work with SQL and LDAP databases, see their example
  # configuration files for more information how to do it.
  # </usr/share/doc/dovecot-common/wiki/UserDatabase.Prefetch.txt>
  #userdb prefetch {
  #}

  # System users (NSS, /etc/passwd, or similiar). In many systems nowadays this
  # uses Name Service Switch, which is configured in /etc/nsswitch.conf.
  # </usr/share/doc/dovecot-common/wiki/AuthDatabase.Passwd.txt>
  userdb passwd {
    # [blocking=yes] - By default the lookups are done in the main dovecot-auth
    # process. This setting causes the lookups to be done in auth worker
    # proceses. Useful with remote NSS lookups that may block.
    # NOTE: Be sure to use this setting with nss_ldap or users might get
    # logged in as each others!
    #args = 
  }

  # passwd-like file with specified location
  # </usr/share/doc/dovecot-common/wiki/AuthDatabase.PasswdFile.txt>
  #userdb passwd-file {
    # [username_format=<format>] <Path for passwd-file>
    #args =
  #}

  # checkpassword executable user database lookup
  # </usr/share/doc/dovecot-common/wiki/AuthDatabase.CheckPassword.txt>
  #userdb checkpassword {
    # Path for checkpassword binary
    #args = 
  #}

  # static settings generated from template </usr/share/doc/dovecot-common/wiki/UserDatabase.Static.txt>
  #userdb static {
    # Template for the fields. Can return anything a userdb could normally
    # return. For example:
    #
    #  args = uid=500 gid=500 home=/var/mail/%u
    #
    # If you use deliver, it needs to look up users only from the userdb. This
    # of course doesn't work with static because there is no list of users.
    # Normally static userdb handles this by doing a passdb lookup. This works
    # with most passdbs, with PAM being the most notable exception. If you do
    # the user verification another way, you can add allow_all_users=yes to
    # the args in which case the passdb lookup is skipped.
    #
    #args =
  #}

  # SQL database </usr/share/doc/dovecot-common/wiki/AuthDatabase.SQL.txt>
  #userdb sql {
    # Path for SQL configuration file
    #args = /etc/dovecot/dovecot-sql.conf
  #}

  # LDAP database </usr/share/doc/dovecot-common/wiki/AuthDatabase.LDAP.txt>
  #userdb ldap {
    # Path for LDAP configuration file
    #args = /etc/dovecot/dovecot-ldap.conf
  #}

  # vpopmail </usr/share/doc/dovecot-common/wiki/AuthDatabase.VPopMail.txt>
  #userdb vpopmail {
  #}

  # User to use for the process. This user needs access to only user and
  # password databases, nothing else. Only shadow and pam authentication
  # requires roots, so use something else if possible. Note that passwd
  # authentication with BSDs internally accesses shadow files, which also
  # requires roots. Note that this user is NOT used to access mails.
  # That user is specified by userdb above.
  user = root

  # Directory where to chroot the process. Most authentication backends don't
  # work if this is set, and there's no point chrooting if auth_user is root.
  # Note that valid_chroot_dirs isn't needed to use this setting.
  #chroot = 

  # Number of authentication processes to create
  #count = 1

  # Require a valid SSL client certificate or the authentication fails.
  #ssl_require_client_cert = no

  # Take the username from client's SSL certificate, using 
  # X509_NAME_get_text_by_NID() which returns the subject's DN's
  # CommonName. 
  #ssl_username_from_cert = no

  # It's possible to export the authentication interface to other programs:
  #socket listen {
    #master {
      # Master socket provides access to userdb information. It's typically
      # used to give Dovecot's local delivery agent access to userdb so it
      # can find mailbox locations.
      #path = /var/run/dovecot/auth-master
      #mode = 0600
      # Default user/group is the one who started dovecot-auth (root)
      #user = 
      #group = 
    #}
    #client {
      # The client socket is generally safe to export to everyone. Typical use
      # is to export it to your SMTP server so it can do SMTP AUTH lookups
      # using it.
      #path = /var/run/dovecot/auth-client
      #mode = 0660
    #}
  #}
  !include_try /etc/dovecot/auth.d/*.auth
}

# If you wish to use another authentication server than dovecot-auth, you can
# use connect sockets. They are assumed to be already running, Dovecot's master
# process only tries to connect to them. They don't need any other settings
# than the path for the master socket, as the configuration is done elsewhere.
# Note that the client sockets must exist in the login_dir.
#auth external {
#  socket connect {
#    master {
#      path = /var/run/dovecot/auth-master
#    }
#  }
#}

##
## Dictionary server settings
##

# Dictionary can be used by some plugins to store key=value lists, such as
# quota, expire and acl plugins. The dictionary can be used either directly or
# though a dictionary server. The following dict block maps dictionary names to
# URIs when the server is used. These can then be referenced using URIs in
# format "proxy::<name>".

dict {
  #quota = mysql:/etc/dovecot/dovecot-dict-quota.conf
  #expire = db:/var/lib/dovecot/expire.db
}

# Path to Berkeley DB's configuration file. See doc/dovecot-db-example.conf
#dict_db_config = 

##
## Plugin settings
##

plugin {
  # Here you can give some extra environment variables to mail processes.
  # This is mostly meant for passing parameters to plugins. %variable
  # expansion is done for all values.

  # Quota plugin. Multiple backends are supported:
  #   dirsize: Find and sum all the files found from mail directory.
  #            Extremely SLOW with Maildir. It'll eat your CPU and disk I/O.
  #   dict: Keep quota stored in dictionary (eg. SQL)
  #   maildir: Maildir++ quota
  #   fs: Read-only support for filesystem quota
  #
  # Quota limits are set using "quota_rule" parameters, either in here or in
  # userdb. It's also possible to give mailbox-specific limits, for example:
  #   quota_rule = *:storage=1048576
  #   quota_rule2 = Trash:storage=102400
  # User has now 1GB quota, but when saving to Trash mailbox the user gets
  # additional 100MB.
  #
  # Multiple quota roots are also possible, for example:
  #   quota = dict:user::proxy::quota
  #   quota2 = dict:domain:%d:proxy::quota_domain
  #   quota_rule = *:storage=102400
  #   quota2_rule = *:storage=1048576
  # Gives each user their own 100MB quota and one shared 1GB quota within
  # the domain.
  #
  # You can execute a given command when user exceeds a specified quota limit.
  # Each quota root has separate limits. Only the command for the first
  # exceeded limit is excecuted, so put the highest limit first.
  # Note that % needs to be escaped as %%, otherwise "% " expands to empty.
  #   quota_warning = storage=95%% /usr/local/bin/quota-warning.sh 95
  #   quota_warning2 = storage=80%% /usr/local/bin/quota-warning.sh 80
  #quota = maildir

  # ACL plugin. vfile backend reads ACLs from "dovecot-acl" file from maildir
  # directory. You can also optionally give a global ACL directory path where
  # ACLs are applied to all users' mailboxes. The global ACL directory contains
  # one file for each mailbox, eg. INBOX or sub.mailbox. cache_secs parameter
  # specifies how many seconds to wait between stat()ing dovecot-acl file
  # to see if it changed.
  #acl = vfile:/etc/dovecot/dovecot-acls:cache_secs=300

  # To let users LIST mailboxes shared by other users, Dovecot needs a
  # shared mailbox dictionary. For example:
  #acl_shared_dict = file:/var/lib/dovecot/shared-mailboxes

  # Convert plugin. If set, specifies the source storage path which is
  # converted to destination storage (mail_location) when the user logs in.
  # The existing mail directory is renamed to <dir>-converted.
  #convert_mail = mbox:%h/mail
  # Skip mailboxes which we can't open successfully instead of aborting.
  #convert_skip_broken_mailboxes = no
  # Skip directories beginning with '.'
  #convert_skip_dotdirs = no
  # If source storage has mailbox names with destination storage's hierarchy
  # separators, replace them with this character.
  #convert_alt_hierarchy_char = _

  # Trash plugin. When saving a message would make user go over quota, this
  # plugin automatically deletes the oldest mails from configured mailboxes
  # until the message can be saved within quota limits. The configuration file
  # is a text file where each line is in format: <priority> <mailbox name>
  # Mails are first deleted in lowest -> highest priority number order
  #trash = /etc/dovecot/dovecot-trash.conf

  # Expire plugin. Mails are expunged from mailboxes after being there the
  # configurable time. The first expiration date for each mailbox is stored in
  # a dictionary so it can be quickly determined which mailboxes contain
  # expired mails. The actual expunging is done in a nightly cronjob, which
  # you must set up:
  #   dovecot --exec-mail ext /usr/lib/dovecot/expire-tool
  #expire = Trash 7 Spam 30
  #expire_dict = proxy::expire

  # Lazy expunge plugin. Currently works only with maildirs. When a user
  # expunges mails, the mails are moved to a mailbox in another namespace
  # (1st). When a mailbox is deleted, the mailbox is moved to another namespace
  # (2nd) as well. Also if the deleted mailbox had any expunged messages,
  # they're moved to a 3rd namespace. The mails won't be counted in quota,
  # and they're not deleted automatically (use a cronjob or something).
  #lazy_expunge = .EXPUNGED/ .DELETED/ .DELETED/.EXPUNGED/

  # Events to log. Also available: flag_change append
  #mail_log_events = delete undelete expunge copy mailbox_delete mailbox_rename
  # Group events within a transaction to one line.
  #mail_log_group_events = no
  # Available fields: uid, box, msgid, from, subject, size, vsize, flags
  # size and vsize are available only for expunge and copy events.
  #mail_log_fields = uid box msgid size

  # Sieve plugin (http://wiki.dovecot.org/LDA/Sieve) and ManageSieve service
  # 
  # Location of the active script. When ManageSieve is used this is actually 
  # a symlink pointing to the active script in the sieve storage directory. 
  #sieve=~/.dovecot.sieve
  #
  # The path to the directory where the personal Sieve scripts are stored. For 
  # ManageSieve this is where the uploaded scripts are stored.
  #sieve_dir=~/sieve
}

# Config files can also be included. deliver doesn't support them currently.
#!include /etc/dovecot/conf.d/*.conf
# Optional configurations, don't give an error if it's not found:
!include_try /etc/dovecot/conf.d/*.conf
#!include_try /etc/dovecot/extra.conf

```

/etc/dovecot/conf.d/10-auth.conf
```

##
## Authentication processes
##

# Disable LOGIN command and all other plaintext authentications unless
# SSL/TLS is used (LOGINDISABLED capability). Note that if the remote IP
# matches the local IP (ie. you're connecting from the same computer), the
# connection is considered secure and plaintext authentication is allowed.
# See also ssl=required setting.
#disable_plaintext_auth = yes

# Authentication cache size (e.g. 10M). 0 means it's disabled. Note that
# bsdauth, PAM and vpopmail require cache_key to be set for caching to be used.
#auth_cache_size = 0
# Time to live for cached data. After TTL expires the cached record is no
# longer used, *except* if the main database lookup returns internal failure.
# We also try to handle password changes automatically: If user's previous
# authentication was successful, but this one wasn't, the cache isn't used.
# For now this works only with plaintext authentication.
#auth_cache_ttl = 1 hour
# TTL for negative hits (user not found, password mismatch).
# 0 disables caching them completely.
#auth_cache_negative_ttl = 1 hour

# Space separated list of realms for SASL authentication mechanisms that need
# them. You can leave it empty if you don't want to support multiple realms.
# Many clients simply use the first one listed here, so keep the default realm
# first.
#auth_realms =

# Default realm/domain to use if none was specified. This is used for both
# SASL realms and appending @domain to username in plaintext logins.
#auth_default_realm = 

# List of allowed characters in username. If the user-given username contains
# a character not listed in here, the login automatically fails. This is just
# an extra check to make sure user can't exploit any potential quote escaping
# vulnerabilities with SQL/LDAP databases. If you want to allow all characters,
# set this value to empty.
#auth_username_chars = abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ01234567890.-_@

# Username character translations before it's looked up from databases. The
# value contains series of from -> to characters. For example "#@/@" means
# that '#' and '/' characters are translated to '@'.
#auth_username_translation =

# Username formatting before it's looked up from databases. You can use
# the standard variables here, eg. %Lu would lowercase the username, %n would
# drop away the domain if it was given, or "%n-AT-%d" would change the '@' into
# "-AT-". This translation is done after auth_username_translation changes.
#auth_username_format = %Lu

# If you want to allow master users to log in by specifying the master
# username within the normal username string (ie. not using SASL mechanism's
# support for it), you can specify the separator character here. The format
# is then <username><separator><master username>. UW-IMAP uses "*" as the
# separator, so that could be a good choice.
#auth_master_user_separator =

# Username to use for users logging in with ANONYMOUS SASL mechanism
#auth_anonymous_username = anonymous

# Maximum number of dovecot-auth worker processes. They're used to execute
# blocking passdb and userdb queries (eg. MySQL and PAM). They're
# automatically created and destroyed as needed.
#auth_worker_max_count = 30

# Host name to use in GSSAPI principal names. The default is to use the
# name returned by gethostname(). Use "$ALL" (with quotes) to allow all keytab
# entries.
#auth_gssapi_hostname =

# Kerberos keytab to use for the GSSAPI mechanism. Will use the system
# default (usually /etc/krb5.keytab) if not specified. You may need to change
# the auth service to run as root to be able to read this file.
#auth_krb5_keytab = 

# Do NTLM and GSS-SPNEGO authentication using Samba's winbind daemon and
# ntlm_auth helper. <doc/wiki/Authentication/Mechanisms/Winbind.txt>
#auth_use_winbind = no

# Path for Samba's ntlm_auth helper binary.
#auth_winbind_helper_path = /usr/bin/ntlm_auth

# Time to delay before replying to failed authentications.
#auth_failure_delay = 2 secs

# Require a valid SSL client certificate or the authentication fails.
#auth_ssl_require_client_cert = no

# Take the username from client's SSL certificate, using 
# X509_NAME_get_text_by_NID() which returns the subject's DN's
# CommonName. 
#auth_ssl_username_from_cert = no

# Space separated list of wanted authentication mechanisms:
#   plain login digest-md5 cram-md5 ntlm rpa apop anonymous gssapi otp skey
#   gss-spnego
# NOTE: See also disable_plaintext_auth setting.
auth_mechanisms = plain

##
## Password and user databases
##

#
# Password database is used to verify user's password (and nothing more).
# You can have multiple passdbs and userdbs. This is useful if you want to
# allow both system users (/etc/passwd) and virtual users to login without
# duplicating the system users into virtual database.
#
# <doc/wiki/PasswordDatabase.txt>
#
# User database specifies where mails are located and what user/group IDs
# own them. For single-UID configuration use "static" userdb.
#
# <doc/wiki/UserDatabase.txt>

#!include auth-deny.conf.ext
#!include auth-master.conf.ext

!include auth-system.conf.ext
#!include auth-sql.conf.ext
#!include auth-ldap.conf.ext
#!include auth-passwdfile.conf.ext
#!include auth-checkpassword.conf.ext
#!include auth-vpopmail.conf.ext
#!include auth-static.conf.ext

```

/etc/dovecot/conf.d/10-mail.conf
```

##
## Mailbox locations and namespaces
##

# Location for users' mailboxes. The default is empty, which means that Dovecot
# tries to find the mailboxes automatically. This won't work if the user
# doesn't yet have any mail, so you should explicitly tell Dovecot the full
# location.
#
# If you're using mbox, giving a path to the INBOX file (eg. /var/mail/%u)
# isn't enough. You'll also need to tell Dovecot where the other mailboxes are
# kept. This is called the "root mail directory", and it must be the first
# path given in the mail_location setting.
#
# There are a few special variables you can use, eg.:
#
#   %u - username
#   %n - user part in user@domain, same as %u if there's no domain
#   %d - domain part in user@domain, empty if there's no domain
#   %h - home directory
#
# See doc/wiki/Variables.txt for full list. Some examples:
#
#   mail_location = maildir:~/Maildir
#   mail_location = mbox:~/mail:INBOX=/var/mail/%u
#   mail_location = mbox:/var/mail/%d/%1n/%n:INDEX=/var/indexes/%d/%1n/%n
#
# <doc/wiki/MailLocation.txt>
#

# If you need to set multiple mailbox locations or want to change default
# namespace settings, you can do it by defining namespace sections.
#
# You can have private, shared and public namespaces. Private namespaces
# are for user's personal mails. Shared namespaces are for accessing other
# users' mailboxes that have been shared. Public namespaces are for shared
# mailboxes that are managed by sysadmin. If you create any shared or public
# namespaces you'll typically want to enable ACL plugin also, otherwise all
# users can access all the shared mailboxes, assuming they have permissions
# on filesystem level to do so.
namespace inbox {
  # Namespace type: private, shared or public
  #type = private

  # Hierarchy separator to use. You should use the same separator for all
  # namespaces or some clients get confused. '/' is usually a good one.
  # The default however depends on the underlying mail storage format.
  #separator = 

  # Prefix required to access this namespace. This needs to be different for
  # all namespaces. For example "Public/".
  #prefix = 

  # Physical location of the mailbox. This is in same format as
  # mail_location, which is also the default for it.
  #location =

  # There can be only one INBOX, and this setting defines which namespace
  # has it.
  inbox = yes

  # If namespace is hidden, it's not advertised to clients via NAMESPACE
  # extension. You'll most likely also want to set list=no. This is mostly
  # useful when converting from another server with different namespaces which
  # you want to deprecate but still keep working. For example you can create
  # hidden namespaces with prefixes "~/mail/", "~%u/mail/" and "mail/".
  #hidden = no

  # Show the mailboxes under this namespace with LIST command. This makes the
  # namespace visible for clients that don't support NAMESPACE extension.
  # "children" value lists child mailboxes, but hides the namespace prefix.
  #list = yes

  # Namespace handles its own subscriptions. If set to "no", the parent
  # namespace handles them (empty prefix should always have this as "yes")
  #subscriptions = yes
}

# Example shared namespace configuration
#namespace {
  #type = shared
  #separator = /

  # Mailboxes are visible under "shared/user@domain/"
  # %%n, %%d and %%u are expanded to the destination user.
  #prefix = shared/%%u/

  # Mail location for other users' mailboxes. Note that %variables and ~/
  # expands to the logged in user's data. %%n, %%d, %%u and %%h expand to the
  # destination user's data.
  #location = maildir:%%h/Maildir:INDEX=~/Maildir/shared/%%u

  # Use the default namespace for saving subscriptions.
  #subscriptions = no

  # List the shared/ namespace only if there are visible shared mailboxes.
  #list = children
#}
# Should shared INBOX be visible as "shared/user" or "shared/user/INBOX"?
#mail_shared_explicit_inbox = no

# System user and group used to access mails. If you use multiple, userdb
# can override these by returning uid or gid fields. You can use either numbers
# or names. <doc/wiki/UserIds.txt>
#mail_uid =
#mail_gid =

# Group to enable temporarily for privileged operations. Currently this is
# used only with INBOX when either its initial creation or dotlocking fails.
# Typically this is set to "mail" to give access to /var/mail.
#mail_privileged_group =

# Grant access to these supplementary groups for mail processes. Typically
# these are used to set up access to shared mailboxes. Note that it may be
# dangerous to set these if users can create symlinks (e.g. if "mail" group is
# set here, ln -s /var/mail ~/mail/var could allow a user to delete others'
# mailboxes, or ln -s /secret/shared/box ~/mail/mybox would allow reading it).
#mail_access_groups =

# Allow full filesystem access to clients. There's no access checks other than
# what the operating system does for the active UID/GID. It works with both
# maildir and mboxes, allowing you to prefix mailboxes names with eg. /path/
# or ~user/.
#mail_full_filesystem_access = no

# Dictionary for key=value mailbox attributes. Currently used by URLAUTH, but
# soon intended to be used by METADATA as well.
#mail_attribute_dict =

##
## Mail processes
##

# Don't use mmap() at all. This is required if you store indexes to shared
# filesystems (NFS or clustered filesystem).
#mmap_disable = no

# Rely on O_EXCL to work when creating dotlock files. NFS supports O_EXCL
# since version 3, so this should be safe to use nowadays by default.
#dotlock_use_excl = yes

# When to use fsync() or fdatasync() calls:
#   optimized (default): Whenever necessary to avoid losing important data
#   always: Useful with e.g. NFS when write()s are delayed
#   never: Never use it (best performance, but crashes can lose data)
#mail_fsync = optimized

# Mail storage exists in NFS. Set this to yes to make Dovecot flush NFS caches
# whenever needed. If you're using only a single mail server this isn't needed.
#mail_nfs_storage = no
# Mail index files also exist in NFS. Setting this to yes requires
# mmap_disable=yes and fsync_disable=no.
#mail_nfs_index = no

# Locking method for index files. Alternatives are fcntl, flock and dotlock.
# Dotlocking uses some tricks which may create more disk I/O than other locking
# methods. NFS users: flock doesn't work, remember to change mmap_disable.
#lock_method = fcntl

# Directory in which LDA/LMTP temporarily stores incoming mails >128 kB.
#mail_temp_dir = /tmp

# Valid UID range for users, defaults to 500 and above. This is mostly
# to make sure that users can't log in as daemons or other system users.
# Note that denying root logins is hardcoded to dovecot binary and can't
# be done even if first_valid_uid is set to 0.
#first_valid_uid = 500
#last_valid_uid = 0

# Valid GID range for users, defaults to non-root/wheel. Users having
# non-valid GID as primary group ID aren't allowed to log in. If user
# belongs to supplementary groups with non-valid GIDs, those groups are
# not set.
#first_valid_gid = 1
#last_valid_gid = 0

# Maximum allowed length for mail keyword name. It's only forced when trying
# to create new keywords.
#mail_max_keyword_length = 50

# ':' separated list of directories under which chrooting is allowed for mail
# processes (ie. /var/mail will allow chrooting to /var/mail/foo/bar too).
# This setting doesn't affect login_chroot, mail_chroot or auth chroot
# settings. If this setting is empty, "/./" in home dirs are ignored.
# WARNING: Never add directories here which local users can modify, that
# may lead to root exploit. Usually this should be done only if you don't
# allow shell access for users. <doc/wiki/Chrooting.txt>
#valid_chroot_dirs = 

# Default chroot directory for mail processes. This can be overridden for
# specific users in user database by giving /./ in user's home directory
# (eg. /home/./user chroots into /home). Note that usually there is no real
# need to do chrooting, Dovecot doesn't allow users to access files outside
# their mail directory anyway. If your home directories are prefixed with
# the chroot directory, append "/." to mail_chroot. <doc/wiki/Chrooting.txt>
#mail_chroot = 

# UNIX socket path to master authentication server to find users.
# This is used by imap (for shared users) and lda.
#auth_socket_path = /var/run/dovecot/auth-userdb

# Directory where to look up mail plugins.
#mail_plugin_dir = /usr/lib/dovecot/modules

# Space separated list of plugins to load for all services. Plugins specific to
# IMAP, LDA, etc. are added to this list in their own .conf files.
#mail_plugins = 

##
## Mailbox handling optimizations
##

# Mailbox list indexes can be used to optimize IMAP STATUS commands. They are
# also required for IMAP NOTIFY extension to be enabled.
#mailbox_list_index = no

# The minimum number of mails in a mailbox before updates are done to cache
# file. This allows optimizing Dovecot's behavior to do less disk writes at
# the cost of more disk reads.
#mail_cache_min_mail_count = 0

# When IDLE command is running, mailbox is checked once in a while to see if
# there are any new mails or other changes. This setting defines the minimum
# time to wait between those checks. Dovecot can also use dnotify, inotify and
# kqueue to find out immediately when changes occur.
#mailbox_idle_check_interval = 30 secs

# Save mails with CR+LF instead of plain LF. This makes sending those mails
# take less CPU, especially with sendfile() syscall with Linux and FreeBSD.
# But it also creates a bit more disk I/O which may just make it slower.
# Also note that if other software reads the mboxes/maildirs, they may handle
# the extra CRs wrong and cause problems.
#mail_save_crlf = no

# Max number of mails to keep open and prefetch to memory. This only works with
# some mailbox formats and/or operating systems.
#mail_prefetch_count = 0

# How often to scan for stale temporary files and delete them (0 = never).
# These should exist only after Dovecot dies in the middle of saving mails.
#mail_temp_scan_interval = 1w

##
## Maildir-specific settings
##

# By default LIST command returns all entries in maildir beginning with a dot.
# Enabling this option makes Dovecot return only entries which are directories.
# This is done by stat()ing each entry, so it causes more disk I/O.
# (For systems setting struct dirent->d_type, this check is free and it's
# done always regardless of this setting)
#maildir_stat_dirs = no

# When copying a message, do it with hard links whenever possible. This makes
# the performance much better, and it's unlikely to have any side effects.
#maildir_copy_with_hardlinks = yes

# Assume Dovecot is the only MUA accessing Maildir: Scan cur/ directory only
# when its mtime changes unexpectedly or when we can't find the mail otherwise.
#maildir_very_dirty_syncs = no

# If enabled, Dovecot doesn't use the S=<size> in the Maildir filenames for
# getting the mail's physical size, except when recalculating Maildir++ quota.
# This can be useful in systems where a lot of the Maildir filenames have a
# broken size. The performance hit for enabling this is very small.
#maildir_broken_filename_sizes = no

##
## mbox-specific settings
##

# Which locking methods to use for locking mbox. There are four available:
#  dotlock: Create <mailbox>.lock file. This is the oldest and most NFS-safe
#           solution. If you want to use /var/mail/ like directory, the users
#           will need write access to that directory.
#  dotlock_try: Same as dotlock, but if it fails because of permissions or
#               because there isn't enough disk space, just skip it.
#  fcntl  : Use this if possible. Works with NFS too if lockd is used.
#  flock  : May not exist in all systems. Doesn't work with NFS.
#  lockf  : May not exist in all systems. Doesn't work with NFS.
#
# You can use multiple locking methods; if you do the order they're declared
# in is important to avoid deadlocks if other MTAs/MUAs are using multiple
# locking methods as well. Some operating systems don't allow using some of
# them simultaneously.
#
# The Debian value for mbox_write_locks differs from upstream Dovecot. It is
# changed to be compliant with Debian Policy (section 11.6) for NFS safety.
#       Dovecot: mbox_write_locks = dotlock fcntl
#       Debian:  mbox_write_locks = fcntl dotlock
#
#mbox_read_locks = fcntl
#mbox_write_locks = fcntl dotlock

# Maximum time to wait for lock (all of them) before aborting.
#mbox_lock_timeout = 5 mins

# If dotlock exists but the mailbox isn't modified in any way, override the
# lock file after this much time.
#mbox_dotlock_change_timeout = 2 mins

# When mbox changes unexpectedly we have to fully read it to find out what
# changed. If the mbox is large this can take a long time. Since the change
# is usually just a newly appended mail, it'd be faster to simply read the
# new mails. If this setting is enabled, Dovecot does this but still safely
# fallbacks to re-reading the whole mbox file whenever something in mbox isn't
# how it's expected to be. The only real downside to this setting is that if
# some other MUA changes message flags, Dovecot doesn't notice it immediately.
# Note that a full sync is done with SELECT, EXAMINE, EXPUNGE and CHECK 
# commands.
#mbox_dirty_syncs = yes

# Like mbox_dirty_syncs, but don't do full syncs even with SELECT, EXAMINE,
# EXPUNGE or CHECK commands. If this is set, mbox_dirty_syncs is ignored.
#mbox_very_dirty_syncs = no

# Delay writing mbox headers until doing a full write sync (EXPUNGE and CHECK
# commands and when closing the mailbox). This is especially useful for POP3
# where clients often delete all mails. The downside is that our changes
# aren't immediately visible to other MUAs.
#mbox_lazy_writes = yes

# If mbox size is smaller than this (e.g. 100k), don't write index files.
# If an index file already exists it's still read, just not updated.
#mbox_min_index_size = 0

# Mail header selection algorithm to use for MD5 POP3 UIDLs when
# pop3_uidl_format=%m. For backwards compatibility we use apop3d inspired
# algorithm, but it fails if the first Received: header isn't unique in all
# mails. An alternative algorithm is "all" that selects all headers.
#mbox_md5 = apop3d

##
## mdbox-specific settings
##

# Maximum dbox file size until it's rotated.
#mdbox_rotate_size = 2M

# Maximum dbox file age until it's rotated. Typically in days. Day begins
# from midnight, so 1d = today, 2d = yesterday, etc. 0 = check disabled.
#mdbox_rotate_interval = 0

# When creating new mdbox files, immediately preallocate their size to
# mdbox_rotate_size. This setting currently works only in Linux with some
# filesystems (ext4, xfs).
#mdbox_preallocate_space = no

##
## Mail attachments
##

# sdbox and mdbox support saving mail attachments to external files, which
# also allows single instance storage for them. Other backends don't support
# this for now.

# Directory root where to store mail attachments. Disabled, if empty.
#mail_attachment_dir =

# Attachments smaller than this aren't saved externally. It's also possible to
# write a plugin to disable saving specific attachments externally.
#mail_attachment_min_size = 128k

# Filesystem backend to use for saving attachments:
#  posix : No SiS done by Dovecot (but this might help FS's own deduplication)
#  sis posix : SiS with immediate byte-by-byte comparison during saving
#  sis-queue posix : SiS with delayed comparison and deduplication
#mail_attachment_fs = sis posix

# Hash format to use in attachment filenames. You can add any text and
# variables: %{md4}, %{md5}, %{sha1}, %{sha256}, %{sha512}, %{size}.
# Variables can be truncated, e.g. %{sha256:80} returns only first 80 bits
#mail_attachment_hash = %{sha1}

```

/etc/dovecot/conf.d/20-imap.conf
```

##
## IMAP specific settings
##

# Maximum IMAP command line length. Some clients generate very long command
# lines with huge mailboxes, so you may need to raise this if you get
# "Too long argument" or "IMAP command line too large" errors often.
#imap_max_line_length = 64k

# IMAP logout format string:
#  %i - total number of bytes read from client
#  %o - total number of bytes sent to client
#imap_logout_format = in=%i out=%o

# Override the IMAP CAPABILITY response. If the value begins with '+',
# add the given capabilities on top of the defaults (e.g. +XFOO XBAR).
#imap_capability = 

# How long to wait between "OK Still here" notifications when client is
# IDLEing.
#imap_idle_notify_interval = 2 mins

# ID field names and values to send to clients. Using * as the value makes
# Dovecot use the default value. The following fields have default values
# currently: name, version, os, os-version, support-url, support-email.
#imap_id_send = 

# ID fields sent by client to log. * means everything.
#imap_id_log =

# Workarounds for various client bugs:
#   delay-newmail:
#     Send EXISTS/RECENT new mail notifications only when replying to NOOP
#     and CHECK commands. Some clients ignore them otherwise, for example OSX
#     Mail (<v2.1). Outlook Express breaks more badly though, without this it
#     may show user "Message no longer in server" errors. Note that OE6 still
#     breaks even with this workaround if synchronization is set to
#     "Headers Only".
#   tb-extra-mailbox-sep:
#     Thunderbird gets somehow confused with LAYOUT=fs (mbox and dbox) and
#     adds extra '/' suffixes to mailbox names. This option causes Dovecot to
#     ignore the extra '/' instead of treating it as invalid mailbox name.
#   tb-lsub-flags:
#     Show \Noselect flags for LSUB replies with LAYOUT=fs (e.g. mbox).
#     This makes Thunderbird realize they aren't selectable and show them
#     greyed out, instead of only later giving "not selectable" popup error.
#
# The list is space-separated.
#imap_client_workarounds = 

# Host allowed in URLAUTH URLs sent by client. "*" allows all.
#imap_urlauth_host =

protocol imap {
  # Space separated list of plugins to load (default is global mail_plugins).
  #mail_plugins = $mail_plugins

  # Maximum number of IMAP connections allowed for a user from each IP address.
  # NOTE: The username is compared case-sensitively.
  #mail_max_userip_connections = 10
}

```

/etc/roundcube/main.inc.php
```

<?php

/*
+-----------------------------------------------------------------------+
| Main configuration file                                               |
|                                                                       |
| This file is part of the Roundcube Webmail client                     |
| Copyright (C) 2005-2011, The Roundcube Dev Team                       |
|                                                                       |
| Licensed under the GNU General Public License version 3 or            |
| any later version with exceptions for skins & plugins.                |
| See the README file for a full license statement.                     |
|                                                                       |
+-----------------------------------------------------------------------+

*/

$rcmail_config = array();

// ----------------------------------
// LOGGING/DEBUGGING
// ----------------------------------

// system error reporting, sum of: 1 = log; 4 = show, 8 = trace
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

// Log sent messages to <log_dir>/sendmail or to syslog
$rcmail_config['smtp_log'] = true;

// Log successful logins to <log_dir>/userlogins or to syslog
$rcmail_config['log_logins'] = false;

// Log session authentication errors to <log_dir>/session or to syslog
$rcmail_config['log_session'] = false;

// Log SQL queries to <log_dir>/sql or to syslog
$rcmail_config['sql_debug'] = false;

// Log IMAP conversation to <log_dir>/imap or to syslog
$rcmail_config['imap_debug'] = true;

// Log LDAP conversation to <log_dir>/ldap or to syslog
$rcmail_config['ldap_debug'] = false;

// Log SMTP conversation to <log_dir>/smtp or to syslog
$rcmail_config['smtp_debug'] = false;

// ----------------------------------
// IMAP
// ----------------------------------

// The mail host chosen to perform the log-in.
// Leave blank to show a textbox at login, give a list of hosts
// to display a pulldown menu or set one host as string.
// To use SSL/TLS connection, enter hostname with prefix ssl:// or tls://
// Supported replacement variables:
// %n - hostname ($_SERVER['SERVER_NAME'])
// %t - hostname without the first part
// %d - domain (http hostname $_SERVER['HTTP_HOST'] without the first part)
// %s - domain name after the '@' from e-mail address provided at login screen
// For example %n = mail.domain.tld, %t = domain.tld
// WARNING: After hostname change update of mail_host column in users table is
//          required to match old user data records with the new host.
$rcmail_config['default_host'] = array("localhost");

// TCP port used for IMAP connections
$rcmail_config['default_port'] = 143;

// IMAP AUTH type (DIGEST-MD5, CRAM-MD5, LOGIN, PLAIN or null to use
// best server supported one)
$rcmail_config['imap_auth_type'] = null;

// If you know your imap's folder delimiter, you can specify it here.
// Otherwise it will be determined automatically
$rcmail_config['imap_delimiter'] = null;

// If IMAP server doesn't support NAMESPACE extension, but you're
// using shared folders or personal root folder is non-empty, you'll need to
// set these options. All can be strings or arrays of strings.
// Folders need to be ended with directory separator, e.g. "INBOX."
// (special directory "~" is an exception to this rule)
// These can be used also to overwrite server's namespaces
$rcmail_config['imap_ns_personal'] = null;
$rcmail_config['imap_ns_other']    = null;
$rcmail_config['imap_ns_shared']   = null;

// By default IMAP capabilities are readed after connection to IMAP server
// In some cases, e.g. when using IMAP proxy, there's a need to refresh the list
// after login. Set to True if you've got this case.
$rcmail_config['imap_force_caps'] = false;

// By default list of subscribed folders is determined using LIST-EXTENDED
// extension if available. Some servers (dovecot 1.x) returns wrong results
// for shared namespaces in this case. http://trac.roundcube.net/ticket/1486225
// Enable this option to force LSUB command usage instead.
$rcmail_config['imap_force_lsub'] = false;

// Some server configurations (e.g. Courier) doesn't list folders in all namespaces
// Enable this option to force listing of folders in all namespaces
$rcmail_config['imap_force_ns'] = false;

// IMAP connection timeout, in seconds. Default: 0 (no limit)
$rcmail_config['imap_timeout'] = 0;

// Optional IMAP authentication identifier to be used as authorization proxy
$rcmail_config['imap_auth_cid'] = null;

// Optional IMAP authentication password to be used for imap_auth_cid
$rcmail_config['imap_auth_pw'] = null;

// Type of IMAP indexes cache. Supported values: 'db', 'apc' and 'memcache'.
$rcmail_config['imap_cache'] = null;

// Enables messages cache. Only 'db' cache is supported.
$rcmail_config['messages_cache'] = false;


// ----------------------------------
// SMTP
// ----------------------------------

// SMTP server host (for sending mails).
// To use SSL/TLS connection, enter hostname with prefix ssl:// or tls://
// If left blank, the PHP mail() function is used
// Supported replacement variables:
// %h - user's IMAP hostname
// %n - hostname ($_SERVER['SERVER_NAME'])
// %t - hostname without the first part
// %d - domain (http hostname $_SERVER['HTTP_HOST'] without the first part)
// %z - IMAP domain (IMAP hostname without the first part)
// For example %n = mail.domain.tld, %t = domain.tld
$rcmail_config['smtp_server'] = '';

// SMTP port (default is 25; use 587 for STARTTLS or 465 for the
// deprecated SSL over SMTP (aka SMTPS))
$rcmail_config['smtp_port'] = 25;

// SMTP username (if required) if you use %u as the username Roundcube
// will use the current username for login
$rcmail_config['smtp_user'] = '';

// SMTP password (if required) if you use %p as the password Roundcube
// will use the current user's password for login
$rcmail_config['smtp_pass'] = '';

// SMTP AUTH type (DIGEST-MD5, CRAM-MD5, LOGIN, PLAIN or empty to use
// best server supported one)
$rcmail_config['smtp_auth_type'] = '';

// Optional SMTP authentication identifier to be used as authorization proxy
$rcmail_config['smtp_auth_cid'] = null;

// Optional SMTP authentication password to be used for smtp_auth_cid
$rcmail_config['smtp_auth_pw'] = null;

// SMTP HELO host 
// Hostname to give to the remote server for SMTP 'HELO' or 'EHLO' messages 
// Leave this blank and you will get the server variable 'server_name' or 
// localhost if that isn't defined. 
$rcmail_config['smtp_helo_host'] = '';

// SMTP connection timeout, in seconds. Default: 0 (no limit)
// Note: There's a known issue where using ssl connection with
// timeout > 0 causes connection errors (https://bugs.php.net/bug.php?id=54511)
$rcmail_config['smtp_timeout'] = 0;

// ----------------------------------
// SYSTEM
// ----------------------------------

// THIS OPTION WILL ALLOW THE INSTALLER TO RUN AND CAN EXPOSE SENSITIVE CONFIG DATA.
// ONLY ENABLE IT IF YOU'RE REALLY SURE WHAT YOU'RE DOING!
$rcmail_config['enable_installer'] = false;

// don't allow these settings to be overriden by the user
$rcmail_config['dont_override'] = array();

// provide an URL where a user can get support for this Roundcube installation
// PLEASE DO NOT LINK TO THE ROUNDCUBE.NET WEBSITE HERE!
$rcmail_config['support_url'] = '';

// replace Roundcube logo with this image
// specify an URL relative to the document root of this Roundcube installation
$rcmail_config['skin_logo'] = null;

// automatically create a new Roundcube user when log-in the first time.
// a new user will be created once the IMAP login succeeds.
// set to false if only registered users can use this service
$rcmail_config['auto_create_user'] = true;

// Enables possibility to log in using email address from user identities
$rcmail_config['user_aliases'] = false;

// use this folder to store log files (must be writeable for apache user)
// This is used by the 'file' log driver.
$rcmail_config['log_dir'] = 'logs/';

// use this folder to store temp files (must be writeable for apache user)
$rcmail_config['temp_dir'] = 'temp/';

// lifetime of message cache
// possible units: s, m, h, d, w
$rcmail_config['message_cache_lifetime'] = '10d';

// enforce connections over https
// with this option enabled, all non-secure connections will be redirected.
// set the port for the ssl connection as value of this option if it differs from the default 443
$rcmail_config['force_https'] = false;

// tell PHP that it should work as under secure connection
// even if it doesn't recognize it as secure ($_SERVER['HTTPS'] is not set)
// e.g. when you're running Roundcube behind a https proxy
// this option is mutually exclusive to 'force_https' and only either one of them should be set to true.
$rcmail_config['use_https'] = false;

// Allow browser-autocompletion on login form.
// 0 - disabled, 1 - username and host only, 2 - username, host, password
$rcmail_config['login_autocomplete'] = 0;

// Forces conversion of logins to lower case.
// 0 - disabled, 1 - only domain part, 2 - domain and local part.
// If users authentication is case-insensitive this must be enabled.
// Note: After enabling it all user records need to be updated, e.g. with query:
//       UPDATE users SET username = LOWER(username);
$rcmail_config['login_lc'] = 2;

// Includes should be interpreted as PHP files
$rcmail_config['skin_include_php'] = false;

// display software version on login screen
$rcmail_config['display_version'] = false;

// Session lifetime in minutes
$rcmail_config['session_lifetime'] = 10;

// Session domain: .example.org
$rcmail_config['session_domain'] = '';

// Session name. Default: 'roundcube_sessid'
$rcmail_config['session_name'] = null;

// Session authentication cookie name. Default: 'roundcube_sessauth'
$rcmail_config['session_auth_name'] = null;

// Session path. Defaults to PHP session.cookie_path setting.
$rcmail_config['session_path'] = null;

// Backend to use for session storage. Can either be 'db' (default) or 'memcache'
// If set to memcache, a list of servers need to be specified in 'memcache_hosts'
// Make sure the Memcache extension (http://pecl.php.net/package/memcache) version >= 2.0.0 is installed
$rcmail_config['session_storage'] = 'db';

// Use these hosts for accessing memcached
// Define any number of hosts in the form of hostname:port or unix:///path/to/socket.file
$rcmail_config['memcache_hosts'] = null; // e.g. array( 'localhost:11211', '192.168.1.12:11211', 'unix:///var/tmp/memcached.sock' );

// check client IP in session athorization
$rcmail_config['ip_check'] = false;

// check referer of incoming requests
$rcmail_config['referer_check'] = false;

// X-Frame-Options HTTP header value sent to prevent from Clickjacking.
// Possible values: sameorigin|deny. Set to false in order to disable sending them
$rcmail_config['x_frame_options'] = 'sameorigin';

// this key is used to encrypt the users imap password which is stored
// in the session record (and the client cookie if remember password is enabled).
// please provide a string of exactly 24 chars.
$rcmail_config['des_key'] = '{key_removed}';

// Automatically add this domain to user names for login
// Only for IMAP servers that require full e-mail addresses for login
// Specify an array with 'host' => 'domain' values to support multiple hosts
// Supported replacement variables:
// %h - user's IMAP hostname
// %n - hostname ($_SERVER['SERVER_NAME'])
// %t - hostname without the first part
// %d - domain (http hostname $_SERVER['HTTP_HOST'] without the first part)
// %z - IMAP domain (IMAP hostname without the first part)
// For example %n = mail.domain.tld, %t = domain.tld
$rcmail_config['username_domain'] = '';

// This domain will be used to form e-mail addresses of new users
// Specify an array with 'host' => 'domain' values to support multiple hosts
// Supported replacement variables:
// %h - user's IMAP hostname
// %n - http hostname ($_SERVER['SERVER_NAME'])
// %d - domain (http hostname without the first part)
// %z - IMAP domain (IMAP hostname without the first part)
// For example %n = mail.domain.tld, %t = domain.tld
$rcmail_config['mail_domain'] = '';

// Password charset.
// Use it if your authentication backend doesn't support UTF-8.
// Defaults to ISO-8859-1 for backward compatibility
$rcmail_config['password_charset'] = 'ISO-8859-1';

// How many seconds must pass between emails sent by a user
$rcmail_config['sendmail_delay'] = 0;

// Maximum number of recipients per message. Default: 0 (no limit)
$rcmail_config['max_recipients'] = 0; 

// Maximum allowednumber of members of an address group. Default: 0 (no limit)
// If 'max_recipients' is set this value should be less or equal
$rcmail_config['max_group_members'] = 0; 

// add this user-agent to message headers when sending
$rcmail_config['useragent'] = 'Roundcube Webmail/'.RCMAIL_VERSION;

// use this name to compose page titles
$rcmail_config['product_name'] = 'Roundcube Webmail';

// try to load host-specific configuration
// see http://trac.roundcube.net/wiki/Howto_Config for more details
$rcmail_config['include_host_config'] = false;

// path to a text file which will be added to each sent message
// paths are relative to the Roundcube root folder
$rcmail_config['generic_message_footer'] = '';

// path to a text file which will be added to each sent HTML message
// paths are relative to the Roundcube root folder
$rcmail_config['generic_message_footer_html'] = '';

// add a received header to outgoing mails containing the creators IP and hostname
$rcmail_config['http_received_header'] = false;

// Whether or not to encrypt the IP address and the host name
// these could, in some circles, be considered as sensitive information;
// however, for the administrator, these could be invaluable help
// when tracking down issues.
$rcmail_config['http_received_header_encrypt'] = false;

// This string is used as a delimiter for message headers when sending
// a message via mail() function. Leave empty for auto-detection
$rcmail_config['mail_header_delimiter'] = NULL;

// number of chars allowed for line when wrapping text.
// text wrapping is done when composing/sending messages
$rcmail_config['line_length'] = 72;

// send plaintext messages as format=flowed
$rcmail_config['send_format_flowed'] = true;

// According to RFC2298, return receipt envelope sender address must be empty.
// If this option is true, Roundcube will use user's identity as envelope sender for MDN responses.
$rcmail_config['mdn_use_from'] = false;

// Set identities access level:
// 0 - many identities with possibility to edit all params
// 1 - many identities with possibility to edit all params but not email address
// 2 - one identity with possibility to edit all params
// 3 - one identity with possibility to edit all params but not email address
// 4 - one identity with possibility to edit only signature
$rcmail_config['identities_level'] = 0;

// Mimetypes supported by the browser.
// attachments of these types will open in a preview window
// either a comma-separated list or an array: 'text/plain,text/html,text/xml,image/jpeg,image/gif,image/png,application/pdf'
$rcmail_config['client_mimetypes'] = null;  # null == default

// Path to a local mime magic database file for PHPs finfo extension.
// Set to null if the default path should be used.
$rcmail_config['mime_magic'] = null;

// Absolute path to a local mime.types mapping table file.
// This is used to derive mime-types from the filename extension or vice versa.
// Such a file is usually part of the apache webserver. If you don't find a file named mime.types on your system,
// download it from http://svn.apache.org/repos/asf/httpd/httpd/trunk/docs/conf/mime.types
$rcmail_config['mime_types'] = null;

// path to imagemagick identify binary
$rcmail_config['im_identify_path'] = null;

// path to imagemagick convert binary
$rcmail_config['im_convert_path'] = null;

// Size of thumbnails from image attachments displayed below the message content.
// Note: whether images are displayed at all depends on the 'inline_images' option.
// Set to 0 to display images in full size.
$rcmail_config['image_thumbnail_size'] = 240;

// maximum size of uploaded contact photos in pixel
$rcmail_config['contact_photo_size'] = 160;

// Enable DNS checking for e-mail address validation
$rcmail_config['email_dns_check'] = false;

// Disables saving sent messages in Sent folder (like gmail) (Default: false)
// Note: useful when SMTP server stores sent mail in user mailbox
$rcmail_config['no_save_sent_messages'] = false;

// ----------------------------------
// PLUGINS
// ----------------------------------

// List of active plugins (in plugins/ directory)
$rcmail_config['plugins'] = array();

// ----------------------------------
// USER INTERFACE
// ----------------------------------

// default messages sort column. Use empty value for default server's sorting, 
// or 'arrival', 'date', 'subject', 'from', 'to', 'fromto', 'size', 'cc'
$rcmail_config['message_sort_col'] = '';

// default messages sort order
$rcmail_config['message_sort_order'] = 'DESC';

// These cols are shown in the message list. Available cols are:
// subject, from, to, fromto, cc, replyto, date, size, status, flag, attachment, 'priority'
$rcmail_config['list_cols'] = array('subject', 'status', 'fromto', 'date', 'size', 'flag', 'attachment');

// the default locale setting (leave empty for auto-detection)
// RFC1766 formatted language name like en_US, de_DE, de_CH, fr_FR, pt_BR
$rcmail_config['language'] = 'fi_FI';

// use this format for date display (date or strftime format)
$rcmail_config['date_format'] = 'Y-m-d';

// give this choice of date formats to the user to select from
// Note: do not use ambiguous formats like m/d/Y
$rcmail_config['date_formats'] = array('Y-m-d', 'Y/m/d', 'Y.m.d', 'd-m-Y', 'd/m/Y', 'd.m.Y', 'j.n.Y');

// use this format for time display (date or strftime format)
$rcmail_config['time_format'] = 'H:i';

// give this choice of time formats to the user to select from
$rcmail_config['time_formats'] = array('G:i', 'H:i', 'g:i a', 'h:i A');

// use this format for short date display (derived from date_format and time_format)
$rcmail_config['date_short'] = 'D H:i';

// use this format for detailed date/time formatting (derived from date_format and time_format)
$rcmail_config['date_long'] = 'Y-m-d H:i';

// store draft message is this mailbox
// leave blank if draft messages should not be stored
// NOTE: Use folder names with namespace prefix (INBOX. on Courier-IMAP)
$rcmail_config['drafts_mbox'] = 'Drafts';

// store spam messages in this mailbox
// NOTE: Use folder names with namespace prefix (INBOX. on Courier-IMAP)
$rcmail_config['junk_mbox'] = 'Junk';

// store sent message is this mailbox
// leave blank if sent messages should not be stored
// NOTE: Use folder names with namespace prefix (INBOX. on Courier-IMAP)
$rcmail_config['sent_mbox'] = 'Sent';

// move messages to this folder when deleting them
// leave blank if they should be deleted directly
// NOTE: Use folder names with namespace prefix (INBOX. on Courier-IMAP)
$rcmail_config['trash_mbox'] = 'Trash';

// display these folders separately in the mailbox list.
// these folders will also be displayed with localized names
// NOTE: Use folder names with namespace prefix (INBOX. on Courier-IMAP)
$rcmail_config['default_folders'] = array('INBOX', 'Drafts', 'Sent', 'Junk', 'Trash');

// automatically create the above listed default folders on first login
$rcmail_config['create_default_folders'] = false;

// protect the default folders from renames, deletes, and subscription changes
$rcmail_config['protect_default_folders'] = true;

// if in your system 0 quota means no limit set this option to true 
$rcmail_config['quota_zero_as_unlimited'] = false;

// Make use of the built-in spell checker. It is based on GoogieSpell.
// Since Google only accepts connections over https your PHP installatation
// requires to be compiled with Open SSL support
$rcmail_config['enable_spellcheck'] = true;

// Enables spellchecker exceptions dictionary.
// Setting it to 'shared' will make the dictionary shared by all users.
$rcmail_config['spellcheck_dictionary'] = false;

// Set the spell checking engine. 'googie' is the default. 'pspell' is also available,
// but requires the Pspell extensions. When using Nox Spell Server, also set 'googie' here.
$rcmail_config['spellcheck_engine'] = 'pspell';

// For a locally installed Nox Spell Server, please specify the URI to call it.
// Get Nox Spell Server from http://orangoo.com/labs/?page_id=72
// Leave empty to use the Google spell checking service, what means
// that the message content will be sent to Google in order to check spelling
$rcmail_config['spellcheck_uri'] = '';

// These languages can be selected for spell checking.
// Configure as a PHP style hash array: array('en'=>'English', 'de'=>'Deutsch');
// Leave empty for default set of available language.
$rcmail_config['spellcheck_languages'] = NULL;

// Makes that words with all letters capitalized will be ignored (e.g. GOOGLE)
$rcmail_config['spellcheck_ignore_caps'] = false;

// Makes that words with numbers will be ignored (e.g. g00gle)
$rcmail_config['spellcheck_ignore_nums'] = false;

// Makes that words with symbols will be ignored (e.g. g@@gle)
$rcmail_config['spellcheck_ignore_syms'] = false;

// Use this char/string to separate recipients when composing a new message
$rcmail_config['recipients_separator'] = ',';

// don't let users set pagesize to more than this value if set
$rcmail_config['max_pagesize'] = 200;

// Minimal value of user's 'refresh_interval' setting (in seconds)
$rcmail_config['min_refresh_interval'] = 60;

// Enables files upload indicator. Requires APC installed and enabled apc.rfc1867 option.
// By default refresh time is set to 1 second. You can set this value to true
// or any integer value indicating number of seconds.
$rcmail_config['upload_progress'] = false;

// Specifies for how many seconds the Undo button will be available
// after object delete action. Currently used with supporting address book sources.
// Setting it to 0, disables the feature.
$rcmail_config['undo_timeout'] = 0;

// ----------------------------------
// ADDRESSBOOK SETTINGS
// ----------------------------------

// This indicates which type of address book to use. Possible choises:
// 'sql' (default), 'ldap' and ''.
// If set to 'ldap' then it will look at using the first writable LDAP
// address book as the primary address book and it will not display the
// SQL address book in the 'Address Book' view.
// If set to '' then no address book will be displayed or only the
// addressbook which is created by a plugin (like CardDAV).
$rcmail_config['address_book_type'] = 'sql';

// In order to enable public ldap search, configure an array like the Verisign
// example further below. if you would like to test, simply uncomment the example.
// Array key must contain only safe characters, ie. a-zA-Z0-9_
$rcmail_config['ldap_public'] = array();

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
// Replacement variables supported in host names:
// %h - user's IMAP hostname
// %n - hostname ($_SERVER['SERVER_NAME'])
// %t - hostname without the first part
// %d - domain (http hostname $_SERVER['HTTP_HOST'] without the first part)
// %z - IMAP domain (IMAP hostname without the first part)
// For example %n = mail.domain.tld, %t = domain.tld
'hosts'         => array('directory.verisign.com'),
'port'          => 389,
'use_tls'	      => false,
'ldap_version'  => 3,       // using LDAPv3
'network_timeout' => 10,    // The timeout (in seconds) for connect + bind arrempts. This is only supported in PHP >= 5.3.0 with OpenLDAP 2.x
'user_specific' => false,   // If true the base_dn, bind_dn and bind_pass default to the user's IMAP login.
// %fu - The full username provided, assumes the username is an email
//       address, uses the username_domain value if not an email address.
// %u  - The username prior to the '@'.
// %d  - The domain name after the '@'.
// %dc - The domain name hierarchal string e.g. "dc=test,dc=domain,dc=com"
// %dn - DN found by ldap search when search_filter/search_base_dn are used
'base_dn'       => '',
'bind_dn'       => '',
'bind_pass'     => '',
// It's possible to bind for an individual address book
// The login name is used to search for the DN to bind with
'search_base_dn' => '',
'search_filter'  => '',   // e.g. '(&(objectClass=posixAccount)(uid=%u))'
// DN and password to bind as before searching for bind DN, if anonymous search is not allowed
'search_bind_dn' => '',
'search_bind_pw' => '',
// Default for %dn variable if search doesn't return DN value
'search_dn_default' => '',
// Optional authentication identifier to be used as SASL authorization proxy
// bind_dn need to be empty
'auth_cid'       => '',
// SASL authentication method (for proxy auth), e.g. DIGEST-MD5
'auth_method'    => '',
// Indicates if the addressbook shall be hidden from the list.
// With this option enabled you can still search/view contacts.
'hidden'        => false,
// Indicates if the addressbook shall not list contacts but only allows searching.
'searchonly'    => false,
// Indicates if we can write to the LDAP directory or not.
// If writable is true then these fields need to be populated:
// LDAP_Object_Classes, required_fields, LDAP_rdn
'writable'       => false,
// To create a new contact these are the object classes to specify
// (or any other classes you wish to use).
'LDAP_Object_Classes' => array('top', 'inetOrgPerson'),
// The RDN field that is used for new entries, this field needs
// to be one of the search_fields, the base of base_dn is appended
// to the RDN to insert into the LDAP directory.
'LDAP_rdn'       => 'cn',
// The required fields needed to build a new contact as required by
// the object classes (can include additional fields not required by the object classes).
'required_fields' => array('cn', 'sn', 'mail'),
'search_fields'   => array('mail', 'cn'),  // fields to search in
// mapping of contact fields to directory attributes
//   for every attribute one can specify the number of values (limit) allowed.
//   default is 1, a wildcard * means unlimited
'fieldmap' => array(
// Roundcube  => LDAP:limit
'name'        => 'cn',
'surname'     => 'sn',
'firstname'   => 'givenName',
'jobtitle'    => 'title',
'email'       => 'mail:*',
'phone:home'  => 'homePhone',
'phone:work'  => 'telephoneNumber',
'phone:mobile' => 'mobile',
'phone:pager' => 'pager',
'street'      => 'street',
'zipcode'     => 'postalCode',
'region'      => 'st',
'locality'    => 'l',
// if you country is a complex object, you need to configure 'sub_fields' below
'country'      => 'c',
'organization' => 'o',
'department'   => 'ou',
'jobtitle'     => 'title',
'notes'        => 'description',
// these currently don't work:
// 'phone:workfax' => 'facsimileTelephoneNumber',
// 'photo'         => 'jpegPhoto',
// 'manager'       => 'manager',
// 'assistant'     => 'secretary',
),
// Map of contact sub-objects (attribute name => objectClass(es)), e.g. 'c' => 'country'
'sub_fields' => array(),
// Generate values for the following LDAP attributes automatically when creating a new record
'autovalues' => array(
// 'uid'  => 'md5(microtime())',               // You may specify PHP code snippets which are then eval'ed 
// 'mail' => '{givenname}.{sn}@mydomain.com',  // or composite strings with placeholders for existing attributes
),
'sort'          => 'cn',    // The field to sort the listing by.
'scope'         => 'sub',   // search mode: sub|base|list
'filter'        => '(objectClass=inetOrgPerson)',      // used for basic listing (if not empty) and will be &'d with search queries. example: status=act
'fuzzy_search'  => true,    // server allows wildcard search
'vlv'           => false,   // Enable Virtual List View to more efficiently fetch paginated data (if server supports it)
'numsub_filter' => '(objectClass=organizationalUnit)',   // with VLV, we also use numSubOrdinates to query the total number of records. Set this filter to get all numSubOrdinates attributes for counting
'sizelimit'     => '0',     // Enables you to limit the count of entries fetched. Setting this to 0 means no limit.
'timelimit'     => '0',     // Sets the number of seconds how long is spend on the search. Setting this to 0 means no limit.
'referrals'     => true|false,  // Sets the LDAP_OPT_REFERRALS option. Mostly used in multi-domain Active Directory setups

// definition for contact groups (uncomment if no groups are supported)
// for the groups base_dn, the user replacements %fu, %u, $d and %dc work as for base_dn (see above)
// if the groups base_dn is empty, the contact base_dn is used for the groups as well
// -> in this case, assure that groups and contacts are separated due to the concernig filters! 
'groups'        => array(
'base_dn'     => '',
'scope'       => 'sub',   // search mode: sub|base|list
'filter'      => '(objectClass=groupOfNames)',
'object_classes' => array("top", "groupOfNames"),
'member_attr'  => 'member',   // name of the member attribute, e.g. uniqueMember
'name_attr'    => 'cn',       // attribute to be used as group name
),
);
*/

// An ordered array of the ids of the addressbooks that should be searched
// when populating address autocomplete fields server-side. ex: array('sql','Verisign');
$rcmail_config['autocomplete_addressbooks'] = array('sql');

// The minimum number of characters required to be typed in an autocomplete field
// before address books will be searched. Most useful for LDAP directories that
// may need to do lengthy results building given overly-broad searches
$rcmail_config['autocomplete_min_length'] = 1;

// Number of parallel autocomplete requests.
// If there's more than one address book, n parallel (async) requests will be created,
// where each request will search in one address book. By default (0), all address
// books are searched in one request.
$rcmail_config['autocomplete_threads'] = 0;

// Max. numer of entries in autocomplete popup. Default: 15.
$rcmail_config['autocomplete_max'] = 15;

// show address fields in this order
// available placeholders: {street}, {locality}, {zipcode}, {country}, {region}
$rcmail_config['address_template'] = '{street}<br/>{locality} {zipcode}<br/>{country} {region}';

// Matching mode for addressbook search (including autocompletion)
// 0 - partial (*abc*), default
// 1 - strict (abc)
// 2 - prefix (abc*)
// Note: For LDAP sources fuzzy_search must be enabled to use 'partial' or 'prefix' mode
$rcmail_config['addressbook_search_mode'] = 0;

// ----------------------------------
// USER PREFERENCES
// ----------------------------------

// Use this charset as fallback for message decoding
$rcmail_config['default_charset'] = 'UTF-8';

// skin name: folder from skins/
$rcmail_config['skin'] = 'larry';

// show up to X items in messages list view
$rcmail_config['mail_pagesize'] = 50;

// show up to X items in contacts list view
$rcmail_config['addressbook_pagesize'] = 50;

// sort contacts by this col (preferably either one of name, firstname, surname)
$rcmail_config['addressbook_sort_col'] = 'surname';

// the way how contact names are displayed in the list
// 0: display name
// 1: (prefix) firstname middlename surname (suffix)
// 2: (prefix) surname firstname middlename (suffix)
// 3: (prefix) surname, firstname middlename (suffix)
$rcmail_config['addressbook_name_listing'] = 0;

// use this timezone to display date/time
// valid timezone identifers are listed here: php.net/manual/en/timezones.php
// 'auto' will use the browser's timezone settings
$rcmail_config['timezone'] = 'auto';

// prefer displaying HTML messages
$rcmail_config['prefer_html'] = true;

// display remote inline images
// 0 - Never, always ask
// 1 - Ask if sender is not in address book
// 2 - Always show inline images
$rcmail_config['show_images'] = 0;

// open messages in new window
$rcmail_config['message_extwin'] = false;

// open message compose form in new window
$rcmail_config['compose_extwin'] = false;

// compose html formatted messages by default
// 0 - never, 1 - always, 2 - on reply to HTML message, 3 - on forward or reply to HTML message
$rcmail_config['htmleditor'] = 0;

// show pretty dates as standard
$rcmail_config['prettydate'] = true;

// save compose message every 300 seconds (5min)
$rcmail_config['draft_autosave'] = 300;

// default setting if preview pane is enabled
$rcmail_config['preview_pane'] = false;

// Mark as read when viewed in preview pane (delay in seconds)
// Set to -1 if messages in preview pane should not be marked as read
$rcmail_config['preview_pane_mark_read'] = 0;

// Clear Trash on logout
$rcmail_config['logout_purge'] = false;

// Compact INBOX on logout
$rcmail_config['logout_expunge'] = false;

// Display attached images below the message body 
$rcmail_config['inline_images'] = true;

// Encoding of long/non-ascii attachment names:
// 0 - Full RFC 2231 compatible
// 1 - RFC 2047 for 'name' and RFC 2231 for 'filename' parameter (Thunderbird's default)
// 2 - Full 2047 compatible
$rcmail_config['mime_param_folding'] = 1;

// Set true if deleted messages should not be displayed
// This will make the application run slower
$rcmail_config['skip_deleted'] = false;

// Set true to Mark deleted messages as read as well as deleted
// False means that a message's read status is not affected by marking it as deleted
$rcmail_config['read_when_deleted'] = true;

// Set to true to never delete messages immediately
// Use 'Purge' to remove messages marked as deleted
$rcmail_config['flag_for_deletion'] = false;

// Default interval for auto-refresh requests (in seconds)
// These are requests for system state updates e.g. checking for new messages, etc.
// Setting it to 0 disables the feature.
$rcmail_config['refresh_interval'] = 60;

// If true all folders will be checked for recent messages
$rcmail_config['check_all_folders'] = false;

// If true, after message delete/move, the next message will be displayed
$rcmail_config['display_next'] = true;

// 0 - Do not expand threads 
// 1 - Expand all threads automatically 
// 2 - Expand only threads with unread messages 
$rcmail_config['autoexpand_threads'] = 0;

// When replying:
// -1 - don't cite the original message
// 0  - place cursor below the original message
// 1  - place cursor above original message (top posting)
$rcmail_config['reply_mode'] = 0;

// When replying strip original signature from message
$rcmail_config['strip_existing_sig'] = true;

// Show signature:
// 0 - Never
// 1 - Always
// 2 - New messages only
// 3 - Forwards and Replies only
$rcmail_config['show_sig'] = 1;

// Use MIME encoding (quoted-printable) for 8bit characters in message body
$rcmail_config['force_7bit'] = false;

// Defaults of the search field configuration.
// The array can contain a per-folder list of header fields which should be considered when searching
// The entry with key '*' stands for all folders which do not have a specific list set.
// Please note that folder names should to be in sync with $rcmail_config['default_folders']
$rcmail_config['search_mods'] = null;  // Example: array('*' => array('subject'=>1, 'from'=>1), 'Sent' => array('subject'=>1, 'to'=>1));

// Defaults of the addressbook search field configuration.
$rcmail_config['addressbook_search_mods'] = null;  // Example: array('name'=>1, 'firstname'=>1, 'surname'=>1, 'email'=>1, '*'=>1);

// 'Delete always'
// This setting reflects if mail should be always deleted
// when moving to Trash fails. This is necessary in some setups
// when user is over quota and Trash is included in the quota.
$rcmail_config['delete_always'] = false;

// Directly delete messages in Junk instead of moving to Trash
$rcmail_config['delete_junk'] = false;

// Behavior if a received message requests a message delivery notification (read receipt)
// 0 = ask the user, 1 = send automatically, 2 = ignore (never send or ask)
// 3 = send automatically if sender is in addressbook, otherwise ask the user
// 4 = send automatically if sender is in addressbook, otherwise ignore
$rcmail_config['mdn_requests'] = 0;

// Return receipt checkbox default state
$rcmail_config['mdn_default'] = 0;

// Delivery Status Notification checkbox default state
// Note: This can be used only if smtp_server is non-empty
$rcmail_config['dsn_default'] = 0;

// Place replies in the folder of the message being replied to
$rcmail_config['reply_same_folder'] = false;

// Sets default mode of Forward feature to "forward as attachment"
$rcmail_config['forward_attachment'] = false;

// Defines address book (internal index) to which new contacts will be added
// By default it is the first writeable addressbook.
// Note: Use '0' for built-in address book.
$rcmail_config['default_addressbook'] = null;

// Enables spell checking before sending a message.
$rcmail_config['spellcheck_before_send'] = false;

// Skip alternative email addresses in autocompletion (show one address per contact)
$rcmail_config['autocomplete_single'] = false;

// Default font for composed HTML message.
// Supported values: Andale Mono, Arial, Arial Black, Book Antiqua, Courier New,
// Georgia, Helvetica, Impact, Tahoma, Terminal, Times New Roman, Trebuchet MS, Verdana
$rcmail_config['default_font'] = 'Verdana';

$rcmail_config['enable_caching'] = FALSE; 

// end of config file


```

---

### Post by finni on 2014-08-14
Uppety up

---

### Post by finni on 2014-10-06
Anyone?

---

### Post by DigiAngel on 2014-10-06
Try enabling:

disable_plaintext_auth = no

in /etc/dovecot/conf.d/10-auth.conf

---

### Post by finni on 2014-10-14
> **DigiAngel said:**
> Try enabling:

disable_plaintext_auth = no

in /etc/dovecot/conf.d/10-auth.conf

This didn't help. Same error messages still.

---

### Post by Oluwafemi_Korede on 2015-02-18
> **ljbade2 said:**
> Can you look at /var/log/mail.err and mail.log log for error messages and post any here.

Also post the Dovecot and Roundcube configuration you are using.

Make sure to delete any sensitive info first.

I managed to get a working Dovecot and Roundcube using the default settings and packages in 15mins on 14.04.

So it should be working unless you did something wrong in the configuration somewhere.


Please can you post the tutorial you followed for me here, I have been struggling with this issue for some days now.

*How do I remove the postfix+dovecot only from my ubuntu

---

### Post by Travis_Souza on 2015-06-23
I got mine working!!!!!
After looking at the logs while running the rc installer tests vs login, I found the login was appending the "@domain.com." causing authentication to fail.  I commented out $config['username_domain'] in config.inc.php and it works. Now to verify that TLS is working.

---

### Post by finni on 2015-08-13
I updated  roundcube to version 1.0.5 via ppa and this seems to work now OK.

---

### Post by ackbeat on 2015-08-31
> **DigiAngel said:**
> Try enabling:

disable_plaintext_auth = no

in /etc/dovecot/conf.d/10-auth.conf

Thanks! This helped!

---

