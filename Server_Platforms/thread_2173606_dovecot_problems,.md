---
title: "dovecot problems,"
date: 2013-09-10
forum: Server Platforms
---

### Post by turbo5546 on 2013-09-10
So i've been up all night trying to get postfix and dovecot to work together using the guides [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix) and [https://help.ubuntu.com/community/Dovecot](https://help.ubuntu.com/community/Dovecot). it took me a long while of tinkering before I was able to get postfix to run and accept and send e-mails. but dovecot just simple won't go, the logs are empty, it doesn't give me an error at startup, and when I test it with telnet it says connection closed by foreign host. I'm not sure what I'm missing or whats misconfigured. I was noticing that with it "running" there were a few proccess missing with the following command. [COLOR=#000000][FONT=courier]ps auxw|grep "dovecot\|imap\|pop3"[/FONT][/COLOR]
```
  ps auxw|grep "dovecot\|imap\|pop3"root      2075  0.0  0.0  17436   772 ?        Ss   06:50   0:00 /usr/sbin/dovecot
dovecot   2076  0.0  0.0   8956   908 ?        S    06:50   0:00 dovecot/anvil
root      2077  0.0  0.0   9080  1044 ?        S    06:50   0:00 dovecot/log
turbo    10505  0.0  0.0   9388   912 pts/2    R+   08:57   0:00 grep --color=auto dovecot\|imap\|pop3

```
this is the result of my attempt to telnet
```
 turbo@mailserver:/etc/dovecot$ telnet localhost imap2
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.

```
my dovecot.conf
```



auth_debug_passwords=yes
mail_debug=yes
auth_verbose=yes
verbose_ssl=yes
protocols = pop3 imap
pop3_uidl_format = %08Xu%08Xv
ssl = yes
## Dovecot configuration file


# If you're in a hurry, see http://wiki2.dovecot.org/QuickConfiguration


# "doveconf -n" command gives a clean output of the changed settings. Use it
# instead of copy&pasting files when posting to the Dovecot mailing list.


# '#' character and everything after it is treated as comments. Extra spaces
# and tabs are ignored. If you want to use either of these explicitly, put the
# value inside quotes, eg.: key = "# char and trailing whitespace  "


# Default values are shown for each setting, it's not required to uncomment
# those. These are exceptions to this though: No sections (e.g. namespace {})
# or plugin settings are added by default, they're listed only as examples.
# Paths are also just examples with the real defaults being based on configure
# options. The paths listed here are for configure --prefix=/usr
# --sysconfdir=/etc --localstatedir=/var
#protocols = imap


# Enable installed protocols
!include_try /usr/share/dovecot/protocols.d/*.protocol
# A comma separated list of IPs or hosts where to listen in for connections.
# "*" listens in all IPv4 interfaces, "::" listens in all IPv6 interfaces.
# If you want to specify non-default ports or anything more complex,
# edit conf.d/master.conf.
#listen = *, ::


# Base directory where to store runtime data.
#base_dir = /var/run/dovecot/


# Name of this instance. Used to prefix all Dovecot processes in ps output.
#instance_name = dovecot


# Greeting message for clients.
login_greeting = Dovecot ready.


# Space separated list of trusted network ranges. Connections from these
# IPs are allowed to override their IP addresses and ports (for logging and
# for authentication checks). disable_plaintext_auth is also ignored for
# these networks. Typically you'd specify your IMAP proxy servers here.
#login_trusted_networks =
# Sepace separated list of login access check sockets (e.g. tcpwrap)
#login_access_sockets =


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
mail_location = maildir:/home/%u/Maildir

``` 
I've tested sending and receiving mail with postfix, and they are getting through both ways. its just dovecot that seems to refuse to start and I've stumped as to why its having issues.

---

### Post by CharlesA on 2013-09-11
I used this to set up my mail server, maybe it will help you.
[https://library.linode.com/email/postfix/postfix2.9.6-dovecot2.0.19-mysql](https://library.linode.com/email/postfix/postfix2.9.6-dovecot2.0.19-mysql)

Thunderbird doesn't like detecting the settings automatically, but you can set them yourself and it will work fine.

---

