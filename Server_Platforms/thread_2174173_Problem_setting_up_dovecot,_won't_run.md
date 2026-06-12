---
title: "Problem setting up dovecot, won't run"
date: 2013-09-13
forum: Server Platforms
---

### Post by Sebastian_Schack on 2013-09-13
Hi there.

I've used ubuntu before to set up Webservers using Apache(2) and never ran into any kind of problems, I couldn't solve by myself.
Now I've tried setting up my own mailserver on ubuntu 12.04LTS following this tutorial: [https://www.exratione.com/2012/05/a-mailserver-on-ubuntu-1204-postfix-dovecot-mysql/](https://www.exratione.com/2012/05/a-mailserver-on-ubuntu-1204-postfix-dovecot-mysql/)
Everything seemed to work as expected. I'm seeing no messages in /var/log/mail.err and /var/log/mail.warn and in /var/log/mail.log everything seems to be ok.

However, dovecot is clearly not working. Roundcube doesn't get any connection to the IMAP server and even a telnet localhost 143 fails (Unable to connect to remote host: Connection refused).

Dovecot also doesn't show up in ps's output.

I'm not sure what I might've done wrong, since nothing throws any errors.
I even wiped the whole machine clear and started over, just to make sure I did everything in order and didn't miss or skip any steps.

Since I'm totally lost here, there's no sense in me posting an config files out of the blue. If you have any idea what might go wrong and want to see any config files our command's output, I'll be more than happy to provide those.

Thanks for taking the time to read this post.

Sebastian

---

### Post by Sebastian_Schack on 2013-09-13
By now I'm almost certain that this is a dovecot problem. So here's my dovecot.conf:

```

protocols = imap
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


# Enable installed protocols
!include_try /usr/share/dovecot/protocols.d/*.protocol


# A comma separated list of IPs or hosts where to listen in for connections.
# "*" listens in all IPv4 interfaces, "::" listens in all IPv6 interfaces.
# If you want to specify non-default ports or anything more complex,
# edit conf.d/master.conf.
listen = *, ::


# Base directory where to store runtime data.
#base_dir = /var/run/dovecot/


# Name of this instance. Used to prefix all Dovecot processes in ps output.
instance_name = dovecot


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
doveadm_socket_path = doveadm-server


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




```

---

### Post by TheFu on 2013-09-13
"ubuntu email server" search found lots of links from Ubuntu-named websites. I tend to trust these "how-to" more.
Ubuntu has a great how-to for setting up email. Is there something wrong with it?
[https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto) There are others too.

It is unclear to me whether you've properly setup
* MTA (postfix is good)
* DNS MX records (I like using external DNS providers, more secure)
* OpenSSL / TLS enable postfix
* only then should you look at pop3s and imaps servers .... 

Adding AV and AS can come later .... 

Before trying to get IMAP working. Doesn't an imap server need an MTA to talk with and /var/spool/mail files to access?

If you did follow the instructions and "locked down" the allowed IP addresses for inbound connections, perhaps the output from **iptables -L** would help us?

The 1st few paragraphs make setting up an email server to be hard.  I don't remember it being that hard, once I understood the mandatory needs and setup things to supply those needs.

How many end-users does this need to support? Often we build something complex for 2000+ users, when we only have 50 and the simple solution would work fine.

---

### Post by Sebastian_Schack on 2013-09-13
Postfix should be up and running well.
After finding and fixing a typo in the dovecot-config files, dovecot is now running and can be connected to via "telnet localhost 143". Which is good, right? :)

It doesn't accept logins, though. The virtual users do exist in the MySQL database, though. As seems as if there are two separate problems right now:
1) The IMAP server not accepting logins.
2) Dovecot not talking properly to/with postfix.

I guess, I'll give the howto you linked to a shot. Well, and as a last resort, there's always Plesk. :)

---

### Post by TheFu on 2013-09-13
To have a "secure server", don't use unencrypted ports like 143 for services.  But for troubleshooting ... it is a smart step.

IMAP = Dovecot, right?  I didn't think that dovecot talked directly to the MTA.  Though it only read from the spool/mail files.Did you tell dovecot to talk to MySQL to access user credentials? Isn't that how this works?

Plesk ... oh - you mean that admin gui tool that gets hacked every few years? Sure, use that. ;)
cPanel, webmin, mysqladmin ... I think of them all as the same thing ... easy access for an attacker to admin rights, unless the server admin locks down which IPs can access those services. Most don't seem to do that. <sigh>

I should admit that I haven't run dovecot in about 5 yrs.  Elected to switch to Zimbra Communications Server and haven't looked back. We needed enterprise calendaring and the only competition what could be internally hosted was MS-Exchange.  Perhaps that has changed now?  Zimbra is a beast when compared to the other pure-email/IMAP solutions.  A minimal Zimbra server wants over 1.5G of RAM, when a minimal postfix/dovecot box is very happy on 384M of RAM.

How many users for your setup?

---

### Post by Sebastian_Schack on 2013-09-13
IMAP = Dovecot, yes. And yes, I have configured Dovecot so that it talks to MySQL to get the user credentials. It doesn't seem to work, though.

As for Plesk: Yeah, you get lots of comfort in exchange for security. I would, however, restrict access to a single IP. :)

I looked at Zimbra and it looks quite good but would be plain overkill, since I'm planning to use the mailserver for, uhm, me and a hand full of family members. It's the "take back the web" approach. I want to host everything myself. And while I've been running Apaches for ages, this is my first real shot at mailservers.

---

### Post by TheFu on 2013-09-13
I am completely with you on taking back ownership of our data!  
*"cloud computing is careless computing"* - RMS

However, of you have less than 50 users, mysql is an added complexity that just isn't needed, IMHO.
You could just install Postfix + dovecot and be done.  I [wrote this]("http://blog.jdpfu.com/2011/08/16/readers-ask-about-hosting-email") a few years ago when some of my blog readers asked. It is NOT a how-to - I try to answer the "why" questions, not the mechanics of commands to type.

Did you setup a primary and failover DNS MX record?  Missing mail due to a down server sucks.

BTW, lots of AWS IPs end up on email block lists - I block entire subnets there due to spammers, plus I use a free email anti-spammer service that was setup with Scrollout email gateway.

---

### Post by Sebastian_Schack on 2013-09-13
Yes, having MySQL in all this is an added complexity. However, not having additional system users gives me the feeling of added security. I know that this doesn't necessarily really add security &#8211; but I'm feeling better with it. Also: I wanted to play with it. :)

I am aware of potential problems with using AWS for mail. That is one of the reasons I'm renting a vServer at the German hosting company Strato.

---

