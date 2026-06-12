---
title: "Dovecot Configuration Issues"
date: 2013-07-11
forum: Server Platforms
---

### Post by tortilaman on 2013-07-11
I have been agonizing over this for a couple days. I only found where the errors were being sent to just an hour ago because they're not being sent where /etc/dovecot/conf.d/10-logging.conf says it should be. My problem is basically that the dovecot process always fatally crashes.

After finding this error file, I went on an error chase, commenting out any line that caused errors, restarting dovecot, opening the log, and finding a new error etc. It has basically been giving me errors in almost every configuration file for unknown settings, including ssl, ssl_cert, plugin, and now protocols. It doesn't make sense to me that protocols would be an unknown setting, it's kind of important.

I'll attach my default.conf file just in case it's helpful, but beyond that, I'm sure there must be some underlying problem for there to be errors in more than 3 configuration files.

```
# Enable installed protocols!include_try /usr/share/dovecot/protocols.d/*.protocol


# A comma separated list of IPs or hosts where to listen in for connections.
# "*" listens in all IPv4 interfaces, "::" listens in all IPv6 interfaces.
# If you want to specify non-default ports or anything more complex,
# edit conf.d/master.conf.
listen = *, [::]


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


# Space separated list of trusted network ranges. Connections from these
# IPs are allowed to override their IP addresses and ports (for logging and
# for authentication checks). disable_plaintext_auth is also ignored for
# these networks. Typically you'd specify your IMAP proxy servers here.
#login_trusted_networks =


# Sepace separated list of login access check sockets (e.g. tcpwrap)
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


protocols = pop3 imap
mail_location = maildir:~/Maildir
ssl_cert_file = /etc/apache2/ssl/apache.crt
ssl_key_file = /etc/apache2/ssl/apache.key
ssl_disable = no

```

Any help you can give is much appreciated, I'm at my wit's end.

---

### Post by tortilaman on 2013-07-11
Ok, I fixed my issue, it was a bigger problem, I had commented out a bracket in one of the config files. I'm dumb.

---

