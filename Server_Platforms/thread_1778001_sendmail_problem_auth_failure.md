---
title: "sendmail problem: auth failure"
date: 2011-06-08
forum: Server Platforms
---

### Post by chazz_tsc on 2011-06-08
If I am posting this in the wrong forum, please excuse me; as you can see from my post count, I've not been here long.

While I have been using Ubuntu now for several years, I consider myself a relative newb because my admin has all been done through things like webmin; very seldom to I dare open a terminal window, as I don't know the names of the tools I need to work with the tools I am using.

My issue is this: I am running sendmail for a number of users who connect via dynamic IP address. To allow them to send mail, I have allowed relaying from authenticated users. I am now seeing two cases where non-authenticated users are sending messages to external addresses using my mail server.

In the one case, I see a message come in addressed to [email]bogusaddress@my.domain[/email] and five to fifteen other spam victims. My sendmail accepts this, and queues all the messages, apparently sending the spams on.

In the other case, spammer simply attaches to my mailer and drops a message destined to four to twenty outside IPs, which then all get sent out.

In neither case am I seeing authentication happening in the auth logs.

Sendmail is the stock version that comes with ubuntu 10.04.2LTS, which was very recently upgraded from 8.04LTS. SASL is included and apparently running. I have tried to read the sendmail docs and have been thoroughly confused my them; and the "handy step by step" guides that I have tried to follow, which were somewhere between five and seven years old, seemed to indicate that I was doing things correctly.

If anyone can explain why this is happening and let me know how to fix it, I would be overjoyed. Any information you need, just let me know. But be patient, please; apart from my newb nature, I also have had to disable my mailer to keep it from spewing, and so don't get thread change notifications...

---

### Post by chazz_tsc on 2011-06-09
In the hopes that by adding detail, I can hasten a solution, here is what I have.

In the .mc file, I have the following:
```

dnl #
dnl # Features
dnl #
dnl # use /etc/mail/local-host-names
FEATURE(`use_cw_file')dnl
dnl #
dnl # The access db is the basis for most of sendmail's checking
FEATURE(`access_db', , `skip')dnl
dnl #
dnl # This is used to redirect bounce messages to mailnull, which can be
dnl # defined as /dev/null to eliminate them
define(`LUSER_RELAY', "local:mailnull")dnl
dnl #
dnl # The greet_pause feature stops some automail bots - but check the
dnl # provided access db for details on excluding localhosts...
FEATURE(`greet_pause', `1000')dnl 1 seconds
dnl # Daemon option
dnl #
dnl # Delay_checks allows sender<->recipient checking
FEATURE(`delay_checks', `friend', `n')dnl
dnl #
dnl # If we get too many bad recipients, slow things down...
define(`confBAD_RCPT_THROTTLE',`3')dnl
dnl #
dnl # Stop connections that overflow our concurrent and time connection rates
FEATURE(`conncontrol', `nodelay', `terminate')dnl
FEATURE(`ratecontrol', `nodelay', `terminate')dnl
dnl #
dnl # Authentication for sending
define(`confAUTH_OPTIONS',`A')dnl
dnl #
dnl # Spamcop RBL
define(`confBIND_OPTS', `WorkAroundBrokenAAAA')dnl
FEATURE(`enhdnsbl', `bl.spamcop.net', `"Spam blocked, see http://spamcop.net/bl.shtml?"$&{client_addr}', `t')dnl
dnl #
dnl # Forms of authentication allowed: include plaintext for now
TRUST_AUTH_MECH(`EXTERNAL DIGEST-MD5 CRAM-MD5 LOGIN')
define(`confAUTH_MECHANISMS',`EXTERNAL GSSAPI DIGEST-MD5 CRAM-MD5 LOGIN')


```The access table, which is compressed to access.db, as usual:
```

# /etc/mail/access
# Copyright (c) 1998,2004 Richard Nelson <cowboy@debian.org>.
# Time-stamp: <1998/10/27 10:00:00 cowboy>
# GPL'd config file, please feed any gripes, suggestions, etc. to me
#
# Function:
#     Access Control for this smtp server - determines:
#         * Who we accept mail from
#         * Who we accept relaying from
#         * Who we will not send to
#
# Usage:
#     FEATURE(access_db[, type [-o] /etc/mail/access])dnl
#     makemap hash access < access
#
# Format:
#     lhs:
#         email addr         <user@[host.domain]>
#         domain name     unless  FEATURE(relay_hosts_only) is used,
#             then this is a fqdn - and relay-domains ($=R)
#             must also be fqdns.
#         network number  must end on an octet boundary, or
#             you're stuck going the longwinded way ;-{
#     rhs:
#         OK                 accept mail even if other rules in the
#                         running ruleset would reject it.
#         RELAY             Allow domain to relay through your SMTP
#                         server.  RELAY also serves an implicit
#                         OK for the other checks.
#         REJECT             reject the sender/recipient with a general
#                         purpose message that can be customized.
#                         confREJECT_MSG [550 Access denied] will be issued
#         DISCARD         discard the message completely using
#                         the $#discard mailer.
#         ### any text     where ### is an RFC 821 compliant error code
#                 and "any text" is a message to return for
#             the command
# Examples:
#    spammer@aol.com            REJECT
#    FREE.STEALTH.MAILER@    550 Spam not accepted
#
# Notes:
#    With FEATURE(blacklist_recipients) this is also possible:
#    badlocaluser                 550 Mailbox disabled for this username
#    host.mydomain.com             550 That host does not accept mail
#    user@otherhost.mydomain.com  550 Mailbox disabled for this recipient
#
# Related:
#     define(`confREJECT_MSG', `550 Access denied')dnl
#     define(`confCR_FILE', `-o /etc/mail/relay-domains')dnl <<- $=R
#     FEATURE(relay_hosts_only)dnl
#     FEATURE(relay_entire_domain)dnl <<- relays any host in the $=m class
#     FEATURE(relay_based_on_MX)dnl <<- relaying for boxes MX'd to you
#     FEATURE(blacklist_recipients)dnl
#     FEATURE(rbl[,alternate server])dnl
#     FEATURE(orbs[,alternate server])dnl   <<- Debian addition
#     FEATURE(orca[,alternate server])dnl   <<- Debian addition
#     FEATURE(accept_unqualified_senders)dnl
#     FEATURE(accept_unresolvable_domains)dnl
#
# Local addresses 10.x.x.x, 127.x.x.x, 172.16-31.x.x 192.168.x.x can relay
# Note Well! You *must* make sure these address can't be spoofed externally
# Note, outbound relaying is controlled by connection and/or auth
#    If you're not firewalled, and you don't have a lan, comment these out
#    If you're not firewalled, and you have a lan, get firewalled *NOW*
# GreetPause - delay to check for spammers
# Client Connection rate (and #) control
Connect:localhost        RELAY
GreetPause:localhost    0
ClientRate:localhost    0
ClientConn:localhost    0
Connect:127                RELAY
GreetPause:127            0
ClientRate:127            0
ClientConn:127            0
Connect:[IPv6:::1]        RELAY
GreetPause:[IPv6:::1]    0
ClientRate:[IPv6:::1]    0
ClientConn:[IPv6:::1]    0
#Connect:172.16            RELAY
#Connect:172.17            RELAY
#Connect:172.18            RELAY
#Connect:172.19            RELAY
#Connect:172.20            RELAY
#Connect:172.21            RELAY
#Connect:172.22            RELAY
#Connect:172.23            RELAY
#Connect:172.24            RELAY
#Connect:172.25            RELAY
#Connect:172.26            RELAY
#Connect:172.27            RELAY
#Connect:172.28            RELAY
#Connect:172.29            RELAY
#Connect:172.30            RELAY
#Connect:172.31            RELAY
#Connect:192.168            RELAY
#GreetPause:192.168        0
#ClientRate:192.168        0
#ClientConn:192.168        0
# Defaults
GreetPause:                5000
ClientRate:                10
ClientConn:                10
#
# Don't offer AUTH on local network
#SRV_Features:192.168.1    A
#
# Hosts with to allow relaying
#
#
# Hosts that validly forward to me
#GreetPause:<ip>        0
#ClientRate:<ip>        30
#ClientConn:<ip>        0
#
# Whitelisted users
#
Spam:postmaster@    FRIEND
Spam:abuse@        FRIEND
Spam:spam@        FRIEND
#
# Blacklisted users
#
#Connect:rampellsoft.com 554 Email directly, not through didtheyreadit.com
reject@            REJECT
#cyberpromo.com    REJECT
#From:MAILER-DAEMON@store2.netvisao.pt REJECT
#
# Block invalid IPs
#
Connect:0        REJECT
Connect:169.254 REJECT
Connect:192.0.2 REJECT
Connect:224        REJECT
Connect:255        REJECT

```Just to be on the safe side, I have elected not to trust either of my two local networks; they also must authenticate and accept the greet pause before they can send through my server.

And here we have the resulting log of a single instance from the mail facility:
```

Jun  8 19:46:11 mail2 sendmail[12753]: NOQUEUE: connect from 118-166-210-150.z [118.166.210.150]
Jun  8 19:46:11 mail2 sendmail[12753]: AUTH: available mech=LOGIN DIGEST-MD5 CRAM-MD5, allowed mech=EXTERNAL GSSAPI DIGEST-MD5 CRAM-MD5 LOGIN
Jun  8 19:46:11 mail2 sendmail[12753]: p592kBc0012753: Milter: no active filter
Jun  8 19:46:25 mail2 sendmail[12753]: p592kBc0012753: from=<btngmcytzdjdpj@z>, size=4741, class=0, nrcpts=10, msgid=<DGRTEOIIQKISVARIAMNACAS@z>, bodytype=8BITMIME, proto=SMTP, daemon=MTA, relay=118-166-210-150.z [118.166.210.150]
Jun  8 19:46:25 mail2 sendmail[12753]: p592kBc0012753: to=<es821@x>, delay=00:00:11, mailer=esmtp, pri=304741, dsn=4.4.3, stat=queued
Jun  8 19:46:25 mail2 sendmail[12753]: p592kBc0012753: to=<henryshieh2006@x>, delay=00:00:11, mailer=esmtp, pri=304741, dsn=4.4.3, stat=queued
Jun  8 19:46:25 mail2 sendmail[12753]: p592kBc0012753: to=<evapan8@x>, delay=00:00:11, mailer=esmtp, pri=304741, dsn=4.4.3, stat=queued
Jun  8 19:46:25 mail2 sendmail[12753]: p592kBc0012753: to=<fbiyamaha@x>, delay=00:00:11, mailer=esmtp, pri=304741, dsn=4.4.3, stat=queued
Jun  8 19:46:25 mail2 sendmail[12753]: p592kBc0012753: to=<h810179@x>, delay=00:00:11, mailer=esmtp, pri=304741, dsn=4.4.3, stat=queued
Jun  8 19:46:25 mail2 sendmail[12753]: p592kBc0012753: to=<godofphallus@x>, delay=00:00:11, mailer=esmtp, pri=304741, dsn=4.4.3, stat=queued
Jun  8 19:46:25 mail2 sendmail[12753]: p592kBc0012753: to=<fuching0220@x>, delay=00:00:11, mailer=esmtp, pri=304741, dsn=4.4.3, stat=queued
Jun  8 19:46:25 mail2 sendmail[12753]: p592kBc0012753: to=<fine.design520@x>, delay=00:00:11, mailer=esmtp, pri=304741, dsn=4.4.3, stat=queued
Jun  8 19:46:25 mail2 sendmail[12753]: p592kBc0012753: to=<jay44449@x>, delay=00:00:11, mailer=esmtp, pri=304741, dsn=4.4.3, stat=queued
Jun  8 19:46:25 mail2 sendmail[12753]: p592kBc0012753: to=<hgu025@x>, delay=00:00:11, mailer=esmtp, pri=304741, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: from=<vgzvxv@z>, size=4732, class=0, nrcpts=26, msgid=<RHQTFZGWZIGFFDWJANISP@z>, bodytype=8BITMIME, proto=SMTP, daemon=MTA, relay=118-166-210-150.z [118.166.210.150]
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<gene19841211@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<herman_chen2003@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<elmda@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<hotfqleo@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<jane600806@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<evan627111@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<eymkmy@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<g220758891@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<flyway5207@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<gladiatorcheng@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<hanyanshui@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<gm2000@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<hhjoe0908@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<graphicsbytritia@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<jeff0362@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<g801106200425@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<dog75119@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<j250601@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<flash_sav@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<g121248206@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<irani@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<forms2@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<kevin88899999@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<fbc@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<fang610704@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued
Jun  8 19:46:47 mail2 sendmail[12753]: p592kBc2012753: to=<jacktsai206cc@x>, delay=00:00:20, mailer=esmtp, pri=784732, dsn=4.4.3, stat=queued

```I have removed the domain name in each of the destination addresses; they are all the same, and they are not a domain to which I have authorized relaying any more than I have authorized relaying from the source network which I have also removed. A thing I find significant is the total lack of mention of an AUTH in that log; there are also no mentions of any user authenticating in the auth log.

I don't like being a spammer. Where do I start looking, please?

---

### Post by chazz_tsc on 2011-06-09
So maybe I fixed this, I don't yet know...

I changed the delivery mode from "d" (deferred) to "b" (background). The documentation I found for sendmail 8.7 (!) says that d eliminates all pre-receipt checks, while q (queued) and b (background) do not; "i" (interactive) is the fastest of the lot but won't work for SMTP. It would appear that selecting d as the delivery mode eliminates all relay checking; possibly due to a disconnect between the mailer and the queue handler.

Could it be so simple?

I'm certainly seeing a lot of "ruleset: relaying denied" in the log now, where I wasn't before, and I can still get my mail transferred correctly...

---

