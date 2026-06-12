---
title: "Unable to send out email using Postfix mail server"
date: 2012-05-16
forum: Server Platforms
---

### Post by ryan1925 on 2012-05-16
Hi guys,

I just want to ask for a help!

We are using Ubuntu 6.06.1 LTS server in our office with installed Postfix mail server. Our problem is we cannot send out an email due to thousand of spam we received everyday.

A few weeks ago we could not encountered this kind of issue.

When i'm trying to perform a mailq command in terminal minimum of 16-20 spams we received every seconds.

Anybody can give any suggestions or recommendation?

please..............

Thank you and God bless us all!

ryan1925

---

### Post by lisati on 2012-05-16
You might consider upgrading to a newer version of Ubuntu server, 6.06 has not been supported for some time. 

The version of postfix that comes with latest version of Ubuntu Server edition has some bells and whistles useful for spam prevention that 6.06 doesn't have, such as "postscreen"

You might also want to look at some kind of greylisting such as postgrey, and using a tool such as fail2ban which can be configured to automatically block servers that are misbehaving.

---

### Post by SeijiSensei on 2012-05-16
Can you tell from /var/log/mail.log where the spam is originating?  If so, just block the IP address(es) of the sending server(s) with iptables:

```
sudo iptables -I INPUT -s ip.of.spam.server -j REJECT
```

Repeat as necessary.

However I would be worried that your server is misconfigured and is being used as an open relay if you're getting hammered this intensely.  Check all your settings to make sure only mail intended for your domain is accepted, and everything else is rejected.  You'll be able to diagnose the problem more effectively if you first block the senders with those iptables rules.  You'll probably need to clear all the junk out of the outbound queue as well.

If you see entries in mail.log that show destination addresses outside your domain, you're being exploited.  You should take the server offline until you fix the problem, or your IP address will eventually end up on some anti-spam blacklists.

---

### Post by ryan1925 on 2012-05-18
Hi guys,

I Just want to ask some help..this is few days but i can't fix it even I am viewing any forum or blog.
Until now our office can't send out an email due to lot of spam in mail queue log.

here is my /etc/postfix/main.cf


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

myhostname = mail.xxxxxxxxx.com

smtpd_banner = $myhostname ESMTP $mail_name (Pal Mail Server)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

header_checks = regexp:/etc/postfix/header_checks

#permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, reject_unknown_sender_domain
#m See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = herworldtv.com, worldwideproperties.com.sg, hotel-technologies.com, tourismnewsnetwork.com, palvision.com, movielink.com.sg, localhost.localdomain, localhost
relayhost =
local_recipient_maps = unix:passwd.byname $alias_maps
#mynetworks = 127.0.0.0/8,xxx.xx.xxx.xx/xx,xx.xxx.xxx.xx/xx, xxx.xxx.x.0/xx
mynetworks = 127.0.0.0/8,xxx.xx.xxx.xx/28,xxx.xxx.x.0/xx
mailbox_size_limit = 0
mailbox_command = /usr/bin/maildrop
recipient_delimiter = +

inet_interfaces = all
#message_size_limit = 52428800
message_size_limit = 51200000
mailbox_size_limit = 0
home_mailbox = Maildir/
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
maps_rbl_domains = multi.uribl.com, dsn.rfc-ignorant.org, dul.dnsbl.sorbs.net, list.dsbl.org, sbl-xbl.spamhaus.org, bl.spamcop.net, nsbl.sorbs.net,cbl.abuseat.org, ix.dnsbl.manitu.net, combined.rbl.msrbl.net, rabl.nuclearelephant.com, yahoo.com.tw, hinet.net, cyrustech.com.sg, test.com, imf.org
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_invalid_hostname, reject_non_fqdn_hostname, reject_non_fqdn_sender, reject_unknown_recipient_domain, reject_maps_rbl, reject_unauth_destination, reject_unknown_sender_domain, reject_rbl_client yahoo.com.tw
smtpd_helo_restrictions = permit_mynetworks, reject_unknown_helo_hostname
smtpd_helo_restrictions = permit_mynetworks, reject_invalid_helo_hostname
smtpd_sasl_path = smtpd



and thi is my Spamassassin local.cf

This is the right place to customize your installation of SpamAssassin.
#
# See 'perldoc Mail::SpamAssassin::Conf' for details of what can be
# tweaked.
#
# Only a small subset of options are listed below
#
###########################################################################

#   Add *****SPAM***** to the Subject header of spam e-mails
#
rewrite_header Subject *****SPAM*****


#   Save spam messages as a message/rfc822 MIME attachment instead of
#   modifying the original message (0: off, 2: use text/plain instead)
#
# report_safe 1


#   Set which networks or hosts are considered 'trusted' by your mail
#   server (i.e. not spammers)
#
# trusted_networks 212.17.35.


#   Set file-locking method (flock is not safe over NFS, but is faster)
#
# lock_method flock


#   Set the threshold at which a message is considered spam (default: 5.0)

required_score 7.0


#   Use Bayesian classifier (default: 1)
#
use_bayes 1


#   Bayesian classifier auto-learning (default: 1)
#
bayes_auto_learn 1


#   Set headers which may provide inappropriate cues to the Bayesian
#   classifier
#
# bayes_ignore_header X-Bogosity
# bayes_ignore_header X-Spam-Flag
# bayes_ignore_header X-Spam-Status

# Enable or disable network checks
skip_rbl_checks         0
use_razor2              1
use_dcc                 1
use_pyzor               1

whitelist_from *@riverview.com.sg

## Sean added this in 22/12/2008 because of spam complaints from Qala
blacklist_to   *@yahoo.com.tw
blacklist_to   *@*.hinet.net
#blacklist_to   *@yahoo.com
#blacklist_from *@yahoo.com

blacklist_from *@yahoo.com.tw
blacklist_from *@test.com
blacklist_from *@imf.org
blacklist_from *@cyrustech.com.sg
blacklist_from [email]secure.message@abbey.com[/email]
blacklist_from [email]misjudgedyub7@roughcountry.com[/email]
blacklist_from [email]services@dhl.com[/email]



Is there something wrong with the configuration to both of it?


and this is also the sample of mail que log

BCC9E4E40B2     3915 Fri May 18 17:34:48  [email]info@un.org[/email]
(delivery temporarily suspended: host mx-apac.mail.gm0.yahoodns.net[106.10.166.54] refused to talk to me: 421 4.7.1 [TS03] All messages from 119.73.222.35 will be permanently deferred; Retrying will NOT succeed. See [http://postmaster.yahoo.com/421-ts03.html](http://postmaster.yahoo.com/421-ts03.html))
                                         [email]rediffmailcomkapilkumarchauhan@yahoo.co.in[/email]
(host mta6.am0.yahoodns.net[67.195.103.233] refused to talk to me: 421 4.7.1 [TS03] All messages from 119.73.222.35 will be permanently deferred; Retrying will NOT succeed. See [http://postmaster.yahoo.com/421-ts03.html](http://postmaster.yahoo.com/421-ts03.html))
                                         [email]redscornerinc@yahoo.ca[/email]
                                         [email]ref_wife@yahoo.ca[/email]
                                         [email]reginahawco@yahoo.ca[/email]
(delivery temporarily suspended: host mta5.am0.yahoodns.net[72.30.235.6] refused to talk to me: 421 4.7.1 [TS03] All messages from 119.73.222.35 will be permanently deferred; Retrying will NOT succeed. See [http://postmaster.yahoo.com/421-ts03.html](http://postmaster.yahoo.com/421-ts03.html))
                                         [email]Reddust913@yahoo.com[/email]
                                         [email]Reeni1781@yahoo.com[/email]
                                         [email]Refuler98@yahoo.com[/email]
                                         [email]rebeccasia1991@yahoo.com[/email]
                                         [email]rebmay957@yahoo.com[/email]
             (connect to mx1.nospam.com[10.42.23.11]:25: Connection timed out)
                                         [email]refertomywebsite@nospam.com[/email]

Thanks a lot!

---

### Post by SeijiSensei on 2012-05-18
Did you read my posting in the other thread you opened about this?  (Why are you creating a new thread, by the way?)

You didn't solve the problem of being an open relay in time, and now your IP address has been added to anti-spam blacklists.

Go here: [http://www.mxtoolbox.com/SuperTool.aspx](http://www.mxtoolbox.com/SuperTool.aspx) and enter 119.73.222.35 in the search box.  Then click the "blacklist" link.  I see your IP on at least half-a-dozen blacklists now.

I ran the "smtp diag" test, and you no longer appear to be an open relay.  You'll need to spend some time now petitioning to remove your IP address from the various blacklists.  I'd start with Yahoo since that seems to be where your major problem lies. Follow the link to postmaster.yahoo.com in the error messages you quote above.  The MXToolbox page also has some helpful instructions.

---

### Post by nothingspecial on 2012-05-18
Merged.

One thread per issue please.

---

### Post by ryan1925 on 2012-05-20
> **SeijiSensei said:**
> Can you tell from /var/log/mail.log where the spam is originating?  If so, just block the IP address(es) of the sending server(s) with iptables:

```
sudo iptables -I INPUT -s ip.of.spam.server -j REJECT
```Repeat as necessary.

However I would be worried that your server is misconfigured and is being used as an open relay if you're getting hammered this intensely.  Check all your settings to make sure only mail intended for your domain is accepted, and everything else is rejected.  You'll be able to diagnose the problem more effectively if you first block the senders with those iptables rules.  You'll probably need to clear all the junk out of the outbound queue as well.

If you see entries in mail.log that show destination addresses outside your domain, you're being exploited.  You should take the server offline until you fix the problem, or your IP address will eventually end up on some anti-spam blacklists.


Thank you SeijiSense,

Sorry but I am new in Ubuntu server,.Is it good idea to reinstall new server or upgrade to new version of server?How about my IP address? Because it is already catch by the spammer. 

Hoping for your response and great advise to solve this problem..
I try to follow the link in Mxtoolbox.com but I gonna pay to resolve my problem..
Is there something free to help me..

soory for my wrong grammar.

Thank you again.

---

### Post by SeijiSensei on 2012-05-21
> **ryan1925 said:**
> Sorry but I am new in Ubuntu server,.Is it good idea to reinstall new server or upgrade to new version of server?How about my IP address? Because it is already catch by the spammer.

Are you still running the same configuration you listed above or have you made some changes to it?  I noticed that the MXToolbox smtp test doesn't find you to be an open relay.  I also tried pushing a message through 119.73.222.35 and got a "Server configuration problem" response which is a good thing.

I wouldn't change your IP address.  It's already assigned as an MX for a variety of domains.  I would block the spam sending address with iptables as I said before.

I notice this line in your configuration:
> ## Sean added this in 22/12/2008 because of spam complaints from Qala 

It looks like you've had this problem before and tried solving it by blacklisting From domains.  I suggest focusing on the problematic messages like those in the logs.  Can you find the message that had [email]info@un.org[/email] as the From address in your logs?  Why was it accepted?  What about the one allegedly from [email]rediffmailcomkapilkumarchauhan@yahoo.co.in[/email]?  That one appears to have addresses in yahoo.ca in the recipient list.  Why was this one not rejected?

Your configuration includes this line:
```
mynetworks = 127.0.0.0/8,xxx.xx.xxx.xx/28,xxx.xxx.x.0/xx
```

Are you sure you need to permit all the hosts in those obfuscated address blocks?  Were the spams sent from an address in one of these blocks?  From looking at the permissions lists, that looks to be one possible problem.  I don't use Postfix, so I can't be a whole lot of help here.  [Read this](http://www.postfix.org/BASIC_CONFIGURATION_README.html#relay_from).  Just as a guess, you probably don't need any of those address blocks listed besides an entry for 127.0.0.1.

Have you cleared out all this junk from your outbound queue yet?

Yahoo should start accepting mail from you again after it no longer detects you as sending spam. You're also falling off the other lists.  A check at mxtoolbox now shows only four blacklist entries.  

If you haven't done anything to fix the problem since your original posting here, then you do need to figure out how those messages got accepted by your server.  Looking carefully at the logs for why those bogus messages were accepted is the first step.  I'd make fixing this problem your first priority for the week.

---

### Post by ryan1925 on 2012-05-21
> **SeijiSensei said:**
> Are you still running the same configuration you listed above or have you made some changes to it?  I noticed that the MXToolbox smtp test doesn't find you to be an open relay.  I also tried pushing a message through 119.73.222.35 and got a "Server configuration problem" response which is a good thing.

I wouldn't change your IP address.  It's already assigned as an MX for a variety of domains.  I would block the spam sending address with iptables as I said before.

I notice this line in your configuration:
 

It looks like you've had this problem before and tried solving it by blacklisting From domains.  I suggest focusing on the problematic messages like those in the logs.  Can you find the message that had [EMAIL="info@un.org"]info@un.org[/EMAIL] as the From address in your logs?  Why was it accepted?  What about the one allegedly from [EMAIL="rediffmailcomkapilkumarchauhan@yahoo.co.in"]rediffmailcomkapilkumarchauhan@yahoo.co.in[/EMAIL]?  That one appears to have addresses in yahoo.ca in the recipient list.  Why was this one not rejected?

Your configuration includes this line:
```
mynetworks = 127.0.0.0/8,xxx.xx.xxx.xx/28,xxx.xxx.x.0/xx
```Are you sure you need to permit all the hosts in those obfuscated address blocks?  Were the spams sent from an address in one of these blocks?  From looking at the permissions lists, that looks to be one possible problem.  I don't use Postfix, so I can't be a whole lot of help here.  [Read this]("http://www.postfix.org/BASIC_CONFIGURATION_README.html#relay_from").  Just as a guess, you probably don't need any of those address blocks listed besides an entry for 127.0.0.1.

Have you cleared out all this junk from your outbound queue yet?

Yahoo should start accepting mail from you again after it no longer detects you as sending spam. You're also falling off the other lists.  A check at mxtoolbox now shows only four blacklist entries.  

If you haven't done anything to fix the problem since your original posting here, then you do need to figure out how those messages got accepted by your server.  Looking carefully at the logs for why those bogus messages were accepted is the first step.  I'd make fixing this problem your first priority for the week.

Sorry to say that I couldn't familiarize the configuration just because the previous admin was also resign and no one in office is familiar in ubuntu and postfix. I am new employee in our office just 6 days past, that is why I am new also in postfix mail server. Anyways, I only add in smtp_recipient _restriction as of now. Sorry to say that i could not find also any of that spam address in my mail logs. Until now I am so much confuse what is wrong with the configuration why is it accepting spam message again. And mostly where to find the hole thus the intruder catch our domain.,Thank you so much SeijiSense..Hoping for your response again.,

Thank you again.

---

### Post by SeijiSensei on 2012-05-23
Did you remove those other subnet declarations from mynetworks?

---

### Post by lisati on 2012-05-29
Did you get the problems fixed? If so, please tell us about it and mark your thread solved.

I tried connecting to your server and was able to do so, but I notice that there are still listings for the IP address mentioned earlier in the thread on [b.barracudacentral.org]("http://www.barracudanetworks.com/reputation/?pr=1&ip=119.73.222.35") and [dnsbl-1.uceprotect.net]("http://www.uceprotect.net/rblcheck.php?ipr=119.73.222.35")

---

