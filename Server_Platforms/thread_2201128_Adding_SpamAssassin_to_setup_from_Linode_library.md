---
title: "Adding SpamAssassin to setup from Linode library"
date: 2014-01-22
forum: Server Platforms
---

### Post by wolfgentleman on 2014-01-22
I have Postfix, Dovecot, and MySQL setup from following [this]("https://library.linode.com/email/postfix/postfix2.9.6-dovecot2.0.19-mysql") (almost) to the letter. I got SpamAssassin installed and setup by following [this]("http://www.townx.org/index.php?q=blog/elliot/simple_spamassassin_setup_with_postfix_and_dovecot_on_ubuntu_breezy") as best I could. The mail server works great, but when I started on that guide for SpamAssassin I noticed the training portion... Does this setup support the training as showed there? If not how?

---

### Post by SeijiSensei on 2014-01-24
That link didn't work for me, but in general, you should train SpamAssassin manually using the sa-learn command line tool.

Usually you'll need a good sample of spam and non-spam messages to start, though it's the non-spam messages that matter the most. For that, you should use known good messages that you have already received.

You can also turn off the SA Bayesian inference engine entirely (set "use_bayes=0" in the configuration for SA) and rely on the content-based scoring at the start.  If you don't have good archives of spam and non-spam content, I'd start without Bayes and see how well SA does.  Make sure you keep copies of all the spam and non-spam it finds during this period.  After you've gotten a reasonably large sample of each type, say 500 or more messages, you can consider training SA.  Scan both sets of messages manually for any mis-classifications, then feed the resulting message sets to sa-learn.  I use the mbox format, which means I start with two files and run "sudo sa-learn --mbox --ham /path/to/ham_file" and similarly for spam.

For details on the Bayesian methods used by SpamAssassin see the [manual page for sa-learn]("http://linux.die.net/man/1/sa-learn").  That page suggests using samples of 2,000 messages or more.  As someone with a statistics background, I think that's overkill.  Unless you're running a busy server, or you have a few years' worth of archived mail, it'll take quite a while to get to 2,000 non-spam messages.  You'll have no trouble getting that many spams though.  Even my little server that handles just a dozen or so domains received over 1,000 spams per day this week, and those are only the ones that scaled my outer defenses (filters at the SMTP level).

---

### Post by wolfgentleman on 2014-01-24
> **SeijiSensei said:**
> That link didn't work for me, but in general, you should train SpamAssassin manually using the sa-learn command line tool.
Which link?
> **SeijiSensei said:**
> 
Usually you'll need a good sample of spam and non-spam messages to start, though it's the non-spam messages that matter the most. For that, you should use known good messages that you have already received.

You can also turn off the SA Bayesian inference engine entirely (set "use_bayes=0" in the configuration for SA) and rely on the content-based scoring at the start.  If you don't have good archives of spam and non-spam content, I'd start without Bayes and see how well SA does.  Make sure you keep copies of all the spam and non-spam it finds during this period.  After you've gotten a reasonably large sample of each type, say 500 or more messages, you can consider training SA.  Scan both sets of messages manually for any mis-classifications, then feed the resulting message sets to sa-learn.  I use the mbox format, which means I start with two files and run "sudo sa-learn --mbox --ham /path/to/ham_file" and similarly for spam.
I can export the 500+ spam emails from Yahoo but I wouldn't know how to import them. I don't know if it uses mbox... I thought it was maildir... IDK, I just used the Linode tut for Dovecot+Postfix+MySQL replacing only what was needed (domains, emails, passwords,ect.) but otherwise following it to the letter. To be honest I just copied, pasted, and did a search and replace on their configs... I'm lazy, what can I say? :-P

> **SeijiSensei said:**
> 
For details on the Bayesian methods used by SpamAssassin see the [manual page for sa-learn]("http://linux.die.net/man/1/sa-learn").  That page suggests using samples of 2,000 messages or more.  As someone with a statistics background, I think that's overkill.  Unless you're running a busy server, or you have a few years' worth of archived mail, it'll take quite a while to get to 2,000 non-spam messages.  You'll have no trouble getting that many spams though.  Even my little server that handles just a dozen or so domains received over 1,000 spams per day this week, and those are only the ones that scaled my outer defenses (filters at the SMTP level).

I have 2 domains. One is just a forward domain, the other is actually hosted on my server. I haven't got much spam (5 in the past 7 days) but it's still  annoying... Most of it is from those stupid Google Play bots that find  apps that have next to nothing rep and have been on the market for a  while (3/5 of them).

---

### Post by SeijiSensei on 2014-01-25
> **wolfgentleman said:**
> Which link?

[This one](http://www.townx.org/index.php?q=blog/elliot/simple_spamassassin_setup_with_postfox_and_dovecot_on_ubuntu_breezy).

> I can export the 500+ spam emails from Yahoo but I wouldn't know how to import them. I don't know if it uses mbox... I thought it was maildir... IDK, I just used the Linode tut for Dovecot+Postfix+MySQL replacing only what was needed (domains, emails, passwords,ect.) but otherwise following it to the letter. To be honest I just copied, pasted, and did a search and replace on their configs... I'm lazy, what can I say? :-P

You're not alone!

If the messages are in Maildir format, you can just point sa-learn to the appropriate directories.

> I have 2 domains. One is just a forward domain, the other is actually hosted on my server. I haven't got much spam (5 in the past 7 days) but it's still  annoying... Most of it is from those stupid Google Play bots that find  apps that have next to nothing rep and have been on the market for a  while (3/5 of them).

Five spam messages in seven days???  For that I wouldn't bother with training SpamAssassin at all.  Just let its array of content-based checks tag your mail.  If SA misses a couple, and you use Thunderbird to read your mail, you can [train its Bayesian engine]("http://kb.mozillazine.org/Junk_Mail_Controls") by tagging messages in your inbox.  

I take it you have never advertised an email address on a website.  Once you do, you can be certain that it will get spammed incessantly forever after.  I still get mail for addresses that have not been active for years but were once published on a web site.  Plus there are just lots of spamming sites that harvest every registered domain and start sending spam to [email]postmaster@example.com[/email], [email]info@example.com[/email], etc.  As I said, I get over 1,000 spams per day for just a few domains.  I've spent many hours over the years improving my anti-spam defenses at both the SMTP and content-screening levels.  If I only had five spams per week, I wouldn't have invested nearly as much effort in fighting spam.

---

### Post by wolfgentleman on 2014-01-25
I think I boogered up the mail server as no messages are being received, so I will be reversing the changes to postfix conf... however that still leaves me with the question, how do I add SpamAssassin to the setup from the Linode tut?
And for the link I mispelled it as I had to manually type it in due to a bug in Samsung Android stock browsers (no paste/copy or special keys suchas arrow keys or ctrl) I am fixing it now.
And for the mail clients I use K9 mail (Android), Thunderbird, and Roundcube.

---

### Post by CharlesA on 2014-01-25
You are probably not going to like this, but I got it working on my mail server like this:

[https://help.ubuntu.com/12.04/serverguide/mail-filtering.html](https://help.ubuntu.com/12.04/serverguide/mail-filtering.html)

I ended up scripting the commands so I wouldn't have to mess with getting spamassassin/DKIM/clamav working on reinstalls.

---

### Post by wolfgentleman on 2014-01-25
> **CharlesA said:**
> You are probably not going to like this, but I got it working on my mail server like this:

[https://help.ubuntu.com/12.04/serverguide/mail-filtering.html](https://help.ubuntu.com/12.04/serverguide/mail-filtering.html)

I ended up scripting the commands so I wouldn't have to mess with getting spamassassin/DKIM/clamav working on reinstalls.
I don't want virus scanning... I will see if I can disable that portion.

---

### Post by CharlesA on 2014-01-25
> **wolfgentleman said:**
> I don't want virus scanning... I will see if I can disable that portion.

You can!

Look for this line:

```
@bypass_virus_checks_maps = (
   \%bypass_virus_checks, \@bypass_virus_checks_acl, \$bypass_virus_checks_re);

```

It should be disabled by default, which is why I added the above line in /etc/amavis/conf.d/50-user

---

### Post by wolfgentleman on 2014-01-25
> **CharlesA said:**
> You can!

Look for this line:

```
@bypass_virus_checks_maps = (
   \%bypass_virus_checks, \@bypass_virus_checks_acl, \$bypass_virus_checks_re);

```

It should be disabled by default, which is why I added the above line in /etc/amavis/conf.d/50-user
I also don't want the DKIM filter, can that be diabled too? Basically I just want spam filter, nothing more and nothing less, that if it thinks it is spam it drops it in the "Spam" folder rather than deleting it or "flagging" it. I got another spam mail a few minutes ago... I don't NEED a server side spam filter, but it would be very much perferred so that it does not eat too much bandwidth... 1000 spam mail at 100kb per message adds up really quick.

---

### Post by CharlesA on 2014-01-25
I don't see anything on that page to enable DKIM signing, were you talking about allowing spamassassin to whitelist any mail coming from domains with proper DKIM keys or something else?

Also: If you are worried about bandwidth, you could always redirect spam to another mail account on the same server, so you wouldn't have to download it,

---

### Post by SeijiSensei on 2014-01-26
You might consider running [spamd]("http://manpages.ubuntu.com/manpages/natty/man8/spamd.8p.html"), the daemonized version of SpamAssassin.  If you also install procmail, you can write a "[recipe]("http://wiki.apache.org/spamassassin/UsedViaProcmail")" that invokes the spamc client to check each message against the daemon before delivery.  This moves the scanning process from the MTA (Postfix) to the MDA (procmail).

I also use the following additional directives in /etc/postfix/main.cf to block obvious spams at the SMTP level:
```

smtpd_client_restrictions = reject_unknown_client_hostname,
			    check_sender_access pcre:/etc/postfix/sender_access,
# delay before banner; similar to sendmail greetpause
			    sleep 3, reject_unauth_pipelining

smtpd_delay_reject = no

smtpd_sender_restrictions = reject_unknown_sender_domain,
			    check_sender_access pcre:/etc/postfix/sender_access

# block sending servers from non-US/CA locations
smtpd_helo_required = yes
smtpd_helo_restrictions =   check_helo_access pcre:/etc/postfix/helo_access

# relaying
smtpd_relay_restrictions =  reject_unauth_destination

```

These rules block automated spammers that begin sending before the SMTP handshake is concluded, and set up databases (using Perl-compatble regular expressions) that reject messages based on things like the server's domain or sender's address.

For instance, in /etc/postfix/sender_access, I have rules like:
```

# no two-letter country-code domains except us/ca
/\.us$/			OK
/\.ca$/			OK
/\.[a-z][a-z]$/		REJECT US senders only

```
This is for a US-based healthcare provider who has no need to correspond with overseas domains.  Since a large chunk of spam comes from compromised spambots in two-letter country-code domains like .my or .ru, these rules block any such senders outside of the US and Canada.  The denial message from the server will read "US senders only."

> 1000 spam mail at 100kb per message adds up really quick.
Spams are rarely as large as 100K.  Most of them are well under 20K and a lot are smaller than 1K like this one:

```
Enhance your bed energy http://somewhere.example.com/
```

That's it.  Even with headers it was only 553 bytes long.

Also, if this server is at Linode, which I believe it is, you really shouldn't worry about bandwidth.  Even the $20/month service includes 2000 GB of data transfer.  I rarely break 5% of that figure.  My busier server is at 105 GB this month; the other one is under 10 GB.  The busy server handles mail for a number of listservers; most of that 105 GB is outbound.

---

### Post by wolfgentleman on 2014-01-27
> **CharlesA said:**
> I don't see anything on that page to enable DKIM signing, were you talking about allowing spamassassin to whitelist any mail coming from domains with proper DKIM keys or something else?

Also: If you are worried about bandwidth, you could always redirect spam to another mail account on the same server, so you wouldn't have to download it,
> To install the rest of the applications enter the following from a terminal prompt:        
```
sudo apt-get install amavisd-new spamassassin **clamav-daemon**
sudo apt-get install **opendkim** *postfix-policyd-spf-python*
```

I bolded the ones I don't want and italicized the ones I don't know what they are. All I want is detected "spam" to be dropped in the "Spam" folder on dovecot and when I drop something from another folder into the "Spam" folder it teaches the filter that it *is *spam or if I take something out of the "Spam" folder it teaches the filter that that *is not *spam. No virus scanning or domain validity checks.
> **SeijiSensei said:**
> You might consider running [spamd]("http://manpages.ubuntu.com/manpages/natty/man8/spamd.8p.html"), the daemonized version of SpamAssassin.
spamc is installed... It installed when I used "apt-get install spamassassin"
> **SeijiSensei said:**
>   If you also install procmail, you can write a "[recipe]("http://wiki.apache.org/spamassassin/UsedViaProcmail")" that invokes the spamc client to check each message against the daemon before delivery.  This moves the scanning process from the MTA (Postfix) to the MDA (procmail).
Well... Is there a way to adapt my current setup to just use procmail as a middle man between Postfix or Dovecot?
> **SeijiSensei said:**
> Spams are rarely as large as 100K.  Most of them are well under 20K and a lot are smaller than 1K like this one:

```
Enhance your bed energy http://somewhere.example.com/
```

That's it.  Even with headers it was only 553 bytes long.
Except the ones that have 50 pounds of pictures, in which the large majority of the spam in my Yahoo mailbox has. But either way that wasn't even the point...
> **SeijiSensei said:**
> Also, if this server is at Linode, which I believe it is, you really shouldn't worry about bandwidth.  Even the $20/month service includes 2000 GB of data transfer.  I rarely break 5% of that figure.  My busier server is at 105 GB this month; the other one is under 10 GB.  The busy server handles mail for a number of listservers; most of that 105 GB is outbound.
Yes, it is Linode. In fact I believe you are the one that suggested it to me :). They even have free outbound traffic, the 2TB of transfer is only for incoming. I also have 3 domains pointing at this server. Either way I wasn't really "worried" about bandwidth, I just find any form of advirts annoying... well almost, the BMW vs. Audi billboard war was pretty funny. Anyway, I don't really want to filter spam on MTA level because I have a mail forward setup for someone that owns a business. So is there any way I can do this as a plugin or something for dovecot?

---

### Post by CharlesA on 2014-01-27
You can remove clamav-daemon and opendkim from that list if you don't want to use those packages.

You can also remove postfix-policyd-spf-python if you aren't going to be using SPF.
[https://support.google.com/a/answer/33786?hl=en](https://support.google.com/a/answer/33786?hl=en)

I use DKIM and SPF on my mail server, but I am also using it to send and receive mail instead of just sending it.

---

### Post by wolfgentleman on 2014-01-27
> **CharlesA said:**
> You can remove clamav-daemon and opendkim from that list if you don't want to use those packages.

You can also remove postfix-policyd-spf-python if you aren't going to be using SPF.
[https://support.google.com/a/answer/33786?hl=en](https://support.google.com/a/answer/33786?hl=en)
Ok...
> **CharlesA said:**
> I use DKIM and SPF on my mail server, but I am also using it to send and receive mail instead of just sending it.
I am using it for sending & receiving... I have one domain that is send+receive, one that is forward only, and another that doesn't use mail.

---

### Post by CharlesA on 2014-01-27
Gotcha. I would probably set up DKIM, so you don't have to worry about mail coming from your domain getting flagged as spam, but I don't think it's 100% required.

---

### Post by CharlesA on 2014-01-28
> **SeijiSensei said:**
> 
I also use the following additional directives in /etc/postfix/main.cf to block obvious spams at the SMTP level:
```

smtpd_client_restrictions = reject_unknown_client_hostname,
			    check_sender_access pcre:/etc/postfix/sender_access,
# delay before banner; similar to sendmail greetpause
			    sleep 3, reject_unauth_pipelining

smtpd_delay_reject = no

smtpd_sender_restrictions = reject_unknown_sender_domain,
			    check_sender_access pcre:/etc/postfix/sender_access

# block sending servers from non-US/CA locations
smtpd_helo_required = yes
smtpd_helo_restrictions =   check_helo_access pcre:/etc/postfix/helo_access

# relaying
smtpd_relay_restrictions =  reject_unauth_destination

```

I've noticed a bunch (failed) attempts to use my mail server as a relay. Would the above config drop those connections before they attempt to send mail?

---

### Post by SeijiSensei on 2014-01-28
> **wolfgentleman said:**
> spamc is installed... It installed when I used "apt-get install spamassassin"

Well... Is there a way to adapt my current setup to just use procmail as a middle man between Postfix or Dovecot?

First, here's a solution that uses spamc/spamd but doesn't require procmail: [https://www.digitalocean.com/community/articles/how-to-install-and-setup-spamassassin-on-ubuntu-12-04](https://www.digitalocean.com/community/articles/how-to-install-and-setup-spamassassin-on-ubuntu-12-04).  However it works with Postfix at the SMTP level.

Procmail is a "mail delivery agent," a program that sits between the "mail transfer agent," Postfix in this case, and the user's mailbox.  

I use CentOS on servers rather than Ubuntu where procmail is built into the mail system by default. I did get it to work on Ubuntu like this:

1)  Install the software: ```
sudo apt-get install spamassassin spamc procmail
```

2)  Create a **.forward** file in my home directory that reads
```
"|exec /usr/bin/procmail"
```

3)  Create a **.procmailrc** in my home directory that reads:
```
VERBOSE=on
LOGFILE=~/procmailog

:0fw: spamassassin.lock
* < 256000
| spamc

```

4)  Edit **/etc/default/spamassassin** and set 
```
ENABLED=1
```

5)  Start the spamd daemon
```
service spamassassin start
```

If you send yourself an email (using, e.g., "echo test | mail -s test Seiji"), you'll see entries in /var/log/mail.log for the initial transaction that look like this:
```

Jan 28 14:21:06 vid spamd[26471]: spamd: connection from localhost [127.0.0.1] at port 41509
Jan 28 14:21:06 vid spamd[26471]: spamd: setuid to Seiji succeeded
Jan 28 14:21:06 vid spamd[26471]: spamd: creating default_prefs: /home/Seiji/.spamassassin/user_prefs
Jan 28 14:21:06 vid spamd[26471]: config: created user preferences file: /home/Seiji/.spamassassin/user_prefs
Jan 28 14:21:06 vid spamd[26471]: spamd: processing message <00000000000000.9F2C21C1336@vid> for Seiji:1000
Jan 28 14:21:06 vid spamd[26471]: spamd: clean message (1.4/5.0) for Seiji:1000 in 0.1 seconds, 391 bytes.
Jan 28 14:21:06 vid spamd[26471]: spamd: result: . 1 - FH_FROMEML_NOTLD,NO_RELAYS,TO_MALFORMED scantime=0.1,size=391,user=Seiji,
uid=1000,required_score=5.0,rhost=localhost,raddr=127.0.0.1,rport=41509,mid=<00000000000000.9F2C21C1336@vid>,autolearn=no
Jan 28 14:21:06 vid postfix/local[26490]: 9F2C21C1336: to=<Seiji@vid>, relay=local, delay=0.22, delays=0.07/0.01/0/0.15, dsn=2.0.0, status=sent (delivered to command: exec /usr/bin/procmail)
Jan 28 14:21:06 vid postfix/qmgr[26434]: 9F2C21C1336: removed
Jan 28 14:21:06 vid spamd[26470]: prefork: child states: II

```

In ~/procmailog I have:
```

procmail: Match on "< 256000"
procmail: Locking "spamassassin.lock"
procmail: Executing "spamc"
procmail: Unlocking "spamassassin.lock"
procmail: Locking "/var/mail/Seiji.lock"
procmail: Assigning "LASTFOLDER=/var/mail/Seiji"
procmail: Opening "/var/mail/Seiji"
procmail: Acquiring kernel-lock
procmail: Unlocking "/var/mail/Seiji.lock"
procmail: Notified comsat: "Seiji@9222170:/var/mail/Seiji"
From root@vid  Tue Jan 28 14:21:06 2014
 Subject: test
  Folder: /var/mail/Seiji                                                587

```

The "587" is the message length.

This was just a test to make sure everything worked together.  If you want to route mail to a spam folder, you need some additional rules in .procmailrc.  SpamAssassin adds headers to the message before delivery that procmail can use to do filtering.  

Here's a sample set of headers for the message logged above:
```

X-Spam-Checker-Version: SpamAssassin 3.3.2 (2011-06-06) on vid
X-Spam-Level: *
X-Spam-Status: No, score=1.4 required=5.0 tests=FH_FROMEML_NOTLD,NO_RELAYS,
        TO_MALFORMED autolearn=no version=3.3.2

```
There are a number of ways we could parse these headers to determine if something is a spam.  The [documentation](http://wiki.apache.org/spamassassin/UsedViaProcmail) at the Apache Foundation counts up the number of stars in the "X-Spam-Level" header.  Another method would just rely on SpamAssassin's own judgement based on its default criterion of five spam points.  In that case you can append a procmail "recipe" like this:
```

:0
* ^X-Spam-Status:.*Yes
/path/to/spam-folder

```
The ":0" designates the beginning of a recipe.  The asterisk tells procmail to scan all the headers; the remainder of the filter uses a regular expression to find the line that begins with "X-Spam-Status".  If that line contains a "Yes," the message is routed to spam-folder.  If not, it is delivered to the default inbox, /var/mail/username on Ubuntu.  Because procmail runs with the user's permissions, /path/to/spam-folder must be writable by the recipient user's account.

> **CharlesA said:**
> I've noticed a bunch (failed) attempts to use my mail server as a relay. Would the above config drop those connections before they attempt to send mail?
The "sleep 3, [reject_unauth_pipelining]("http://www.postfix.org/postconf.5.html#reject_unauth_pipelining")" directives  block servers that do not wait for the SMTP handshake to complete.  They did wonders on a server I had that had been exploited as an open relay.  Most rejections I log come from the various "unknown" rules that reject servers without proper forward and reverse DNS records.  Usually it's a missing reverse lookup that trips "[reject_unknown_client_hostname]("http://www.postfix.org/postconf.5.html#reject_unknown_client_hostname")."  This rule drops the connection as soon as the remote server cannot be identified.  That's a bit quicker than rejections that rely on the HELO announcement and certainly faster than accepting the message, scanning it, and only then dropping it because it tripped an anti-virus or anti-spam rule.  If all your rejections are happening during the SMTP handshake there isn't much you can do there to improve upon performance.

However, you can avoid a connection to the SMTP server if you can use iptables rules to block known offending hosts at the kernel level.  I run a script every night that parses /var/log/mail.log and counts up the number of times a connection was blocked from each three-octet IP prefix in the log.  Ones that were blocked more than ten times are added to a list.  Another script reads the list and creates iptables blocking rules for the banned addresses.  I use a rotation scheme so that an address is dropped from the list if it hasn't made another failed attempt at sending a message in eight days.

---

### Post by CharlesA on 2014-01-28
Thanks! I think I'll go for the sleep method and reject_unknown_client_hostname and see if that cuts down on the attempts.

I've only noticed this happened for the last two days.

---

### Post by wolfgentleman on 2014-01-28
> **SeijiSensei said:**
> First, here's a solution that uses spamc/spamd but doesn't require procmail: [https://www.digitalocean.com/community/articles/how-to-install-and-setup-spamassassin-on-ubuntu-12-04](https://www.digitalocean.com/community/articles/how-to-install-and-setup-spamassassin-on-ubuntu-12-04).  However it works with Postfix at the SMTP level.
Hmmmm... Well, one question about this. Can I exclude one of the virtual domains from any filtering?

> **SeijiSensei said:**
> Procmail is a "mail delivery agent," a program that sits between the "mail transfer agent," Postfix in this case, and the user's mailbox.
Forgive my ignorance and stupid/annoying question here, but isn't Dovecot a mail delivery agent? If so, couldn't I just find a way to do the below via Dovecot? I wouldn't even know where to start on that though... Any ideas on that?
> **SeijiSensei said:**
> I use CentOS on servers rather than Ubuntu where procmail is built into the mail system by default. I did get it to work on Ubuntu like this:

1)  Install the software: ```
sudo apt-get install spamassassin spamc procmail
```

2)  Create a **.forward** file in my home directory that reads
```
"|exec /usr/bin/procmail"
```

3)  Create a **.procmailrc** in my home directory that reads:
```
VERBOSE=on
LOGFILE=~/procmailog

:0fw: spamassassin.lock
* < 256000
| spamc

```

4)  Edit **/etc/default/spamassassin** and set 
```
ENABLED=1
```

5)  Start the spamd daemon
```
service spamassassin start
```

If you send yourself an email (using, e.g., "echo test | mail -s test Seiji"), you'll see entries in /var/log/mail.log for the initial transaction that look like this:
```

Jan 28 14:21:06 vid spamd[26471]: spamd: connection from localhost [127.0.0.1] at port 41509
Jan 28 14:21:06 vid spamd[26471]: spamd: setuid to Seiji succeeded
Jan 28 14:21:06 vid spamd[26471]: spamd: creating default_prefs: /home/Seiji/.spamassassin/user_prefs
Jan 28 14:21:06 vid spamd[26471]: config: created user preferences file: /home/Seiji/.spamassassin/user_prefs
Jan 28 14:21:06 vid spamd[26471]: spamd: processing message <00000000000000.9F2C21C1336@vid> for Seiji:1000
Jan 28 14:21:06 vid spamd[26471]: spamd: clean message (1.4/5.0) for Seiji:1000 in 0.1 seconds, 391 bytes.
Jan 28 14:21:06 vid spamd[26471]: spamd: result: . 1 - FH_FROMEML_NOTLD,NO_RELAYS,TO_MALFORMED scantime=0.1,size=391,user=Seiji,
uid=1000,required_score=5.0,rhost=localhost,raddr=127.0.0.1,rport=41509,mid=<00000000000000.9F2C21C1336@vid>,autolearn=no
Jan 28 14:21:06 vid postfix/local[26490]: 9F2C21C1336: to=<Seiji@vid>, relay=local, delay=0.22, delays=0.07/0.01/0/0.15, dsn=2.0.0, status=sent (delivered to command: exec /usr/bin/procmail)
Jan 28 14:21:06 vid postfix/qmgr[26434]: 9F2C21C1336: removed
Jan 28 14:21:06 vid spamd[26470]: prefork: child states: II

```

In ~/procmailog I have:
```

procmail: Match on "< 256000"
procmail: Locking "spamassassin.lock"
procmail: Executing "spamc"
procmail: Unlocking "spamassassin.lock"
procmail: Locking "/var/mail/Seiji.lock"
procmail: Assigning "LASTFOLDER=/var/mail/Seiji"
procmail: Opening "/var/mail/Seiji"
procmail: Acquiring kernel-lock
procmail: Unlocking "/var/mail/Seiji.lock"
procmail: Notified comsat: "Seiji@9222170:/var/mail/Seiji"
From root@vid  Tue Jan 28 14:21:06 2014
 Subject: test
  Folder: /var/mail/Seiji                                                587

```

The "587" is the message length.

This was just a test to make sure everything worked together.  If you want to route mail to a spam folder, you need some additional rules in .procmailrc.  SpamAssassin adds headers to the message before delivery that procmail can use to do filtering.  

Here's a sample set of headers for the message logged above:
```

X-Spam-Checker-Version: SpamAssassin 3.3.2 (2011-06-06) on vid
X-Spam-Level: *
X-Spam-Status: No, score=1.4 required=5.0 tests=FH_FROMEML_NOTLD,NO_RELAYS,
        TO_MALFORMED autolearn=no version=3.3.2

```
There are a number of ways we could parse these headers to determine if something is a spam.  The [documentation]("http://wiki.apache.org/spamassassin/UsedViaProcmail") at the Apache Foundation counts up the number of stars in the "X-Spam-Level" header.  Another method would just rely on SpamAssassin's own judgement based on its default criterion of five spam points.  In that case you can append a procmail "recipe" like this:
```

:0
* ^X-Spam-Status:.*Yes
/path/to/spam-folder

```
The ":0" designates the beginning of a recipe.  The asterisk tells procmail to scan all the headers; the remainder of the filter uses a regular expression to find the line that begins with "X-Spam-Status".  If that line contains a "Yes," the message is routed to spam-folder.  If not, it is delivered to the default inbox, /var/mail/username on Ubuntu.  Because procmail runs with the user's permissions, /path/to/spam-folder must be writable by the recipient user's account.


Again, sorry for my ignorance and stupid/annoying/repetitive questions.

---

### Post by wolfgentleman on 2014-01-28
Ok, I did some digging and I found a few things:
[Dovecot's Wiki on integrating procmail]("http://wiki2.dovecot.org/procmail")
[Tutorial for setting up Maildrop as an automated spam mover in Debian]("http://www.stevefortuna.com/postfix-maildrop-spam-folder"), curtesy of DJ_Max from [this thread]("http://ubuntuforums.org/showthread.php?t=2055150").
I also looked over [Dovecot's wiki on mail storage]("http://wiki2.dovecot.org/MailLocation") and found that it is Maildir that I have set up. It also showed me how to use hierarchical directories instead of the .Folder.Subfolder style.
Here are a few lines of my configs that I thought might be needed in adding procmail to the mix:

Dovecot:
```

mail_location = maildir:/var/mail/vhosts/%d/%n*:LAYOUT=fs*

```
On the line above I italicized what I changed. I fixed the directory structure to work with that layout. It seems to be working as if it didn't even change.

Postfix:
main.cf
```

smtpd_sasl_type = dovecot
virtual_transport = lmtp:unix:private/dovecot-lmtp

```
master.cf
```

maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}

```
I'm not real sure what is going on with the maildrop thing... I didn't even realize that was in master.cf nor do I know if it is even installed, but I will check in a bit.

```
ls /var/mail/vhosts/twprogrammers.com/admin
``` Outputs:
> Bugs dovecot-keywords Drafts Spam cur dovecot.mailbox.log Forums subscriptions
dovecot.index dovecot-uidlist new tmp dovecot.index.cache
dovecot-uidvalidity Postmaster Trash dovecot.index.log
dovecot-uidvalidity.52c9ee07 Sent Webmaster

So now I need help combining this info to create a solution. Also, with this can I also direct things going to webmaster@twprogrammers.com to the "Webmaster" folder? That would make sorting much easier... being not client-side sorting and all...

---

### Post by SeijiSensei on 2014-01-29
> **wolfgentleman said:**
> Forgive my ignorance and stupid/annoying question here, but isn't Dovecot a mail delivery agent? If so, couldn't I just find a way to do the below via Dovecot? I wouldn't even know where to start on that though... Any ideas on that?

No, dovecot is an IMAP/POP server. It provides the interface between your folders and mail clients.  Procmail (and /usr/bin/maildrop) are MDAs.  They take the mail that has been processed by the SMTP server and *deliver* it to the appropriate destinations.

I don't have any other suggestions to offer considering I provided a step-by-step solution already.  Good luck!

---

### Post by wolfgentleman on 2014-01-29
> **SeijiSensei said:**
> No, dovecot is an IMAP/POP server.
Oooooooh! Hehe. That explains why it wasn't working previous to following the Linode tutorial :P
 > **SeijiSensei said:**
> I don't have any other suggestions to offer considering I provided a step-by-step solution already.  Good luck!
[s]Any idea on migrating from maildrop to procmail? By looking at [this]("http://www.stevefortuna.com/postfix-maildrop-spam-folder") maildrop has a much more complicated config.[/s] Done. [s]You didn't answer the other question in my previous post, about the filtering based on the 'to' address. Can procmail do that as well?[/s] Done. However nothing is being dropped in any other folder than inbox...
Here is the configs:
doveconf -a
```

# 2.0.19: /etc/dovecot/dovecot.conf
# OS: Linux 3.12.6-x86_64-linode36 x86_64 Ubuntu 12.04.4 LTS ext3
auth_anonymous_username = anonymous
auth_cache_negative_ttl = 1 hours
auth_cache_size = 0
auth_cache_ttl = 1 hours
auth_debug = yes
auth_debug_passwords = yes
auth_default_realm = 
auth_failure_delay = 2 secs
auth_first_valid_uid = 500
auth_gssapi_hostname = 
auth_krb5_keytab = 
auth_last_valid_uid = 0
auth_master_user_separator = 
auth_mechanisms = plain login
auth_realms = 
auth_socket_path = auth-userdb
auth_ssl_require_client_cert = no
auth_ssl_username_from_cert = no
auth_use_winbind = no
auth_username_chars = abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ01234567890.-_@
auth_username_format = 
auth_username_translation = 
auth_verbose = yes
auth_verbose_passwords = plain
auth_winbind_helper_path = /usr/bin/ntlm_auth
auth_worker_max_count = 30
base_dir = /var/run/dovecot
config_cache_size = 1 M
debug_log_path = /var/log/dovecot-debug.log
default_client_limit = 1000
default_idle_kill = 60
default_internal_user = dovecot
default_login_user = dovenull
default_process_limit = 100
default_vsz_limit = 256 M
deliver_log_format = msgid=%m: %$
dict_db_config = 
director_doveadm_port = 0
director_mail_servers = 
director_servers = 
director_user_expire = 15 mins
disable_plaintext_auth = yes
dotlock_use_excl = yes
doveadm_allowed_commands = 
doveadm_password = 
doveadm_proxy_port = 0
doveadm_socket_path = doveadm-server
doveadm_worker_count = 0
first_valid_gid = 1
first_valid_uid = 500
hostname = 
imap_capability = 
imap_client_workarounds = 
imap_id_log = 
imap_id_send = 
imap_idle_notify_interval = 2 mins
imap_logout_format = bytes=%i/%o
imap_max_line_length = 64 k
import_environment = TZ
info_log_path = 
instance_name = dovecot
last_valid_gid = 0
last_valid_uid = 0
lda_mailbox_autocreate = no
lda_mailbox_autosubscribe = no
lda_original_recipient_header = 
libexec_dir = /usr/lib/dovecot
listen = *, ::
lmtp_proxy = no
lmtp_save_to_detail_mailbox = no
lock_method = fcntl
log_path = /var/log/dovecot.log
log_timestamp = "%b %d %H:%M:%S "
login_access_sockets = 
login_greeting = Dovecot ready.
login_log_format = %$: %s
login_log_format_elements = user=<%u> method=%m rip=%r lip=%l mpid=%e %c
login_trusted_networks = 
mail_access_groups = 
mail_attachment_dir = 
mail_attachment_fs = sis posix
mail_attachment_hash = %{sha1}
mail_attachment_min_size = 128 k
mail_cache_fields = flags
mail_cache_min_mail_count = 0
mail_chroot = 
mail_debug = yes
mail_fsync = optimized
mail_full_filesystem_access = no
mail_gid = 
mail_home = 
mail_location = maildir:/var/mail/vhosts/%d/%n:LAYOUT=fs
mail_log_prefix = "%s(%u): "
mail_max_keyword_length = 50
mail_max_lock_timeout = 0
mail_max_userip_connections = 10
mail_never_cache_fields = imap.envelope
mail_nfs_index = no
mail_nfs_storage = no
mail_plugin_dir = /usr/lib/dovecot/modules
mail_plugins = 
mail_privileged_group = mail
mail_save_crlf = no
mail_temp_dir = /tmp
mail_uid = 
mailbox_idle_check_interval = 30 secs
mailbox_list_index_disable = no
maildir_copy_with_hardlinks = yes
maildir_stat_dirs = no
maildir_very_dirty_syncs = no
master_user_separator = 
mbox_dirty_syncs = yes
mbox_dotlock_change_timeout = 2 mins
mbox_lazy_writes = yes
mbox_lock_timeout = 5 mins
mbox_min_index_size = 0
mbox_read_locks = fcntl
mbox_very_dirty_syncs = no
mbox_write_locks = dotlock fcntl
mdbox_preallocate_space = no
mdbox_rotate_interval = 0
mdbox_rotate_size = 2 M
mmap_disable = no
passdb {
  args = /etc/dovecot/dovecot-sql.conf.ext
  deny = no
  driver = sql
  master = no
  pass = no
}
pop3_client_workarounds = 
pop3_enable_last = no
pop3_fast_size_lookups = no
pop3_lock_session = no
pop3_logout_format = top=%t/%p, retr=%r/%b, del=%d/%m, size=%s
pop3_no_flag_updates = no
pop3_reuse_xuidl = no
pop3_save_uidl = no
pop3_uidl_format = %08Xu%08Xv
postmaster_address = 
protocols = imap lmtp
quota_full_tempfail = no
recipient_delimiter = +
rejection_reason = Your message to <%t> was automatically rejected:%n%r
rejection_subject = Rejected: %s
sendmail_path = /usr/sbin/sendmail
service anvil {
  chroot = empty
  client_limit = 0
  drop_priv_before_exec = no
  executable = anvil
  extra_groups = 
  group = 
  idle_kill = 4294967295 secs
  privileged_group = 
  process_limit = 1
  process_min_avail = 1
  protocol = 
  service_count = 0
  type = anvil
  unix_listener anvil-auth-penalty {
    group = 
    mode = 0600
    user = 
  }
  unix_listener anvil {
    group = 
    mode = 0600
    user = 
  }
  user = $default_internal_user
  vsz_limit = 18446744073709551615 B
}
service auth-worker {
  chroot = 
  client_limit = 1
  drop_priv_before_exec = no
  executable = auth -w
  extra_groups = 
  group = 
  idle_kill = 0
  privileged_group = 
  process_limit = 0
  process_min_avail = 0
  protocol = 
  service_count = 1
  type = 
  unix_listener auth-worker {
    group = 
    mode = 0600
    user = $default_internal_user
  }
  user = vmail
  vsz_limit = 18446744073709551615 B
}
service auth {
  chroot = 
  client_limit = 4096
  drop_priv_before_exec = no
  executable = auth
  extra_groups = 
  group = 
  idle_kill = 0
  privileged_group = 
  process_limit = 1
  process_min_avail = 0
  protocol = 
  service_count = 0
  type = 
  unix_listener /var/spool/postfix/private/auth {
    group = postfix
    mode = 0666
    user = postfix
  }
  unix_listener auth-client {
    group = 
    mode = 0600
    user = 
  }
  unix_listener auth-login {
    group = 
    mode = 0600
    user = $default_internal_user
  }
  unix_listener auth-master {
    group = 
    mode = 0600
    user = 
  }
  unix_listener auth-userdb {
    group = 
    mode = 0600
    user = vmail
  }
  unix_listener login/login {
    group = 
    mode = 0666
    user = 
  }
  user = dovecot
  vsz_limit = 18446744073709551615 B
}
service config {
  chroot = 
  client_limit = 0
  drop_priv_before_exec = no
  executable = config
  extra_groups = 
  group = 
  idle_kill = 0
  privileged_group = 
  process_limit = 0
  process_min_avail = 0
  protocol = 
  service_count = 0
  type = config
  unix_listener config {
    group = 
    mode = 0600
    user = 
  }
  user = 
  vsz_limit = 18446744073709551615 B
}
service dict {
  chroot = 
  client_limit = 1
  drop_priv_before_exec = no
  executable = dict
  extra_groups = 
  group = 
  idle_kill = 0
  privileged_group = 
  process_limit = 0
  process_min_avail = 0
  protocol = 
  service_count = 0
  type = 
  unix_listener dict {
    group = 
    mode = 0600
    user = 
  }
  user = $default_internal_user
  vsz_limit = 18446744073709551615 B
}
service director {
  chroot = 
  client_limit = 0
  drop_priv_before_exec = no
  executable = director
  extra_groups = 
  fifo_listener login/proxy-notify {
    group = 
    mode = 00
    user = 
  }
  group = 
  idle_kill = 4294967295 secs
  inet_listener {
    address = 
    port = 0
    ssl = no
  }
  privileged_group = 
  process_limit = 1
  process_min_avail = 0
  protocol = 
  service_count = 0
  type = 
  unix_listener director-admin {
    group = 
    mode = 0600
    user = 
  }
  unix_listener director-userdb {
    group = 
    mode = 0600
    user = 
  }
  unix_listener login/director {
    group = 
    mode = 00
    user = 
  }
  user = $default_internal_user
  vsz_limit = 18446744073709551615 B
}
service dns_client {
  chroot = 
  client_limit = 1
  drop_priv_before_exec = no
  executable = dns-client
  extra_groups = 
  group = 
  idle_kill = 0
  privileged_group = 
  process_limit = 0
  process_min_avail = 0
  protocol = 
  service_count = 0
  type = 
  unix_listener dns-client {
    group = 
    mode = 0666
    user = 
  }
  unix_listener login/dns-client {
    group = 
    mode = 0666
    user = 
  }
  user = $default_internal_user
  vsz_limit = 18446744073709551615 B
}
service doveadm {
  chroot = 
  client_limit = 1
  drop_priv_before_exec = no
  executable = doveadm-server
  extra_groups = 
  group = 
  idle_kill = 0
  privileged_group = 
  process_limit = 0
  process_min_avail = 0
  protocol = 
  service_count = 1
  type = 
  unix_listener doveadm-server {
    group = 
    mode = 0600
    user = 
  }
  user = 
  vsz_limit = 18446744073709551615 B
}
service imap-login {
  chroot = login
  client_limit = 0
  drop_priv_before_exec = no
  executable = imap-login
  extra_groups = 
  group = 
  idle_kill = 0
  inet_listener imap {
    address = 
    port = 0
    ssl = no
  }
  inet_listener imaps {
    address = 
    port = 993
    ssl = yes
  }
  privileged_group = 
  process_limit = 0
  process_min_avail = 0
  protocol = imap
  service_count = 1
  type = login
  user = $default_login_user
  vsz_limit = 18446744073709551615 B
}
service imap {
  chroot = 
  client_limit = 1
  drop_priv_before_exec = no
  executable = imap
  extra_groups = 
  group = 
  idle_kill = 0
  privileged_group = 
  process_limit = 1024
  process_min_avail = 0
  protocol = imap
  service_count = 1
  type = 
  unix_listener login/imap {
    group = 
    mode = 0666
    user = 
  }
  user = 
  vsz_limit = 18446744073709551615 B
}
service ipc {
  chroot = empty
  client_limit = 0
  drop_priv_before_exec = no
  executable = ipc
  extra_groups = 
  group = 
  idle_kill = 0
  privileged_group = 
  process_limit = 1
  process_min_avail = 0
  protocol = 
  service_count = 0
  type = 
  unix_listener ipc {
    group = 
    mode = 0600
    user = 
  }
  unix_listener login/ipc-proxy {
    group = 
    mode = 0600
    user = $default_login_user
  }
  user = $default_internal_user
  vsz_limit = 18446744073709551615 B
}
service lmtp {
  chroot = 
  client_limit = 1
  drop_priv_before_exec = no
  executable = lmtp
  extra_groups = 
  group = 
  idle_kill = 0
  privileged_group = 
  process_limit = 0
  process_min_avail = 0
  protocol = lmtp
  service_count = 0
  type = 
  unix_listener /var/spool/postfix/private/dovecot-lmtp {
    group = postfix
    mode = 0600
    user = postfix
  }
  unix_listener lmtp {
    group = 
    mode = 0666
    user = 
  }
  user = 
  vsz_limit = 18446744073709551615 B
}
service log {
  chroot = 
  client_limit = 0
  drop_priv_before_exec = no
  executable = log
  extra_groups = 
  group = 
  idle_kill = 0
  privileged_group = 
  process_limit = 1
  process_min_avail = 0
  protocol = 
  service_count = 0
  type = log
  user = 
  vsz_limit = 18446744073709551615 B
}
service pop3-login {
  chroot = login
  client_limit = 0
  drop_priv_before_exec = no
  executable = pop3-login
  extra_groups = 
  group = 
  idle_kill = 0
  inet_listener pop3 {
    address = 
    port = 110
    ssl = no
  }
  inet_listener pop3s {
    address = 
    port = 995
    ssl = yes
  }
  privileged_group = 
  process_limit = 0
  process_min_avail = 0
  protocol = pop3
  service_count = 1
  type = login
  user = $default_login_user
  vsz_limit = 18446744073709551615 B
}
service pop3 {
  chroot = 
  client_limit = 1
  drop_priv_before_exec = no
  executable = pop3
  extra_groups = 
  group = 
  idle_kill = 0
  privileged_group = 
  process_limit = 1024
  process_min_avail = 0
  protocol = pop3
  service_count = 1
  type = 
  unix_listener login/pop3 {
    group = 
    mode = 0666
    user = 
  }
  user = 
  vsz_limit = 18446744073709551615 B
}
service ssl-params {
  chroot = 
  client_limit = 0
  drop_priv_before_exec = no
  executable = ssl-params
  extra_groups = 
  group = 
  idle_kill = 0
  privileged_group = 
  process_limit = 0
  process_min_avail = 0
  protocol = 
  service_count = 0
  type = startup
  unix_listener login/ssl-params {
    group = 
    mode = 0666
    user = 
  }
  user = 
  vsz_limit = 18446744073709551615 B
}
shutdown_clients = yes
ssl = required
ssl_ca = 
ssl_cert = </etc/ssl/certs/dovecot.pem
ssl_cert_username_field = commonName
ssl_cipher_list = ALL:!LOW:!SSLv2:!EXP:!aNULL
ssl_client_cert = 
ssl_client_key = 
ssl_key = </etc/ssl/private/dovecot.pem
ssl_key_password = 
ssl_parameters_regenerate = 168
ssl_verify_client_cert = no
submission_host = 
syslog_facility = mail
userdb {
  args = uid=vmail gid=vmail home=/var/mail/vhosts/%d/%n
  driver = static
}
valid_chroot_dirs = 
verbose_proctitle = no
verbose_ssl = no
version_ignore = no

```
postconf
```

2bounce_notice_recipient = postmaster
access_map_defer_code = 450
access_map_reject_code = 554
address_verify_cache_cleanup_interval = 12h
address_verify_default_transport = $default_transport
address_verify_local_transport = $local_transport
address_verify_map = btree:$data_directory/verify_cache
address_verify_negative_cache = yes
address_verify_negative_expire_time = 3d
address_verify_negative_refresh_time = 3h
address_verify_poll_count = ${stress?1}${stress:3}
address_verify_poll_delay = 3s
address_verify_positive_expire_time = 31d
address_verify_positive_refresh_time = 7d
address_verify_relay_transport = $relay_transport
address_verify_relayhost = $relayhost
address_verify_sender = $double_bounce_sender
address_verify_sender_dependent_default_transport_maps = $sender_dependent_default_transport_maps
address_verify_sender_dependent_relayhost_maps = $sender_dependent_relayhost_maps
address_verify_sender_ttl = 0s
address_verify_service_name = verify
address_verify_transport_maps = $transport_maps
address_verify_virtual_transport = $virtual_transport
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
allow_mail_to_commands = alias, forward
allow_mail_to_files = alias, forward
allow_min_user = no
allow_percent_hack = yes
allow_untrusted_routing = no
alternate_config_directories =
always_add_missing_headers = no
always_bcc =
anvil_rate_time_unit = 60s
anvil_status_update_time = 600s
append_at_myorigin = yes
append_dot_mydomain = no
application_event_drain_time = 100s
authorized_flush_users = static:anyone
authorized_mailq_users = static:anyone
authorized_submit_users = static:anyone
backwards_bounce_logfile_compatibility = yes
berkeley_db_create_buffer_size = 16777216
berkeley_db_read_buffer_size = 131072
best_mx_transport =
biff = no
body_checks =
body_checks_size_limit = 51200
bounce_notice_recipient = postmaster
bounce_queue_lifetime = 5d
bounce_service_name = bounce
bounce_size_limit = 50000
bounce_template_file =
broken_sasl_auth_clients = no
bsmtp_delivery_slot_cost = $default_delivery_slot_cost
bsmtp_delivery_slot_discount = $default_delivery_slot_discount
bsmtp_delivery_slot_loan = $default_delivery_slot_loan
bsmtp_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
bsmtp_destination_concurrency_limit = $default_destination_concurrency_limit
bsmtp_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
bsmtp_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
bsmtp_destination_rate_delay = $default_destination_rate_delay
bsmtp_destination_recipient_limit = $default_destination_recipient_limit
bsmtp_extra_recipient_limit = $default_extra_recipient_limit
bsmtp_initial_destination_concurrency = $initial_destination_concurrency
bsmtp_minimum_delivery_slots = $default_minimum_delivery_slots
bsmtp_recipient_limit = $default_recipient_limit
bsmtp_recipient_refill_delay = $default_recipient_refill_delay
bsmtp_recipient_refill_limit = $default_recipient_refill_limit
bsmtp_time_limit = $command_time_limit
canonical_classes = envelope_sender, envelope_recipient, header_sender, header_recipient
canonical_maps =
cleanup_service_name = cleanup
command_directory = /usr/sbin
command_execution_directory =
command_expansion_filter = 1234567890!@%-_=+:,./abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ
command_time_limit = 1000s
config_directory = /etc/postfix
connection_cache_protocol_timeout = 5s
connection_cache_service_name = scache
connection_cache_status_update_time = 600s
connection_cache_ttl_limit = 2s
content_filter =
cyrus_sasl_config_path =
daemon_directory = /usr/lib/postfix
daemon_table_open_error_is_fatal = no
daemon_timeout = 18000s
data_directory = /var/lib/postfix
debug_peer_level = 2
debug_peer_list =
debugger_command =
default_database_type = hash
default_delivery_slot_cost = 5
default_delivery_slot_discount = 50
default_delivery_slot_loan = 3
default_destination_concurrency_failed_cohort_limit = 1
default_destination_concurrency_limit = 20
default_destination_concurrency_negative_feedback = 1
default_destination_concurrency_positive_feedback = 1
default_destination_rate_delay = 0s
default_destination_recipient_limit = 50
default_extra_recipient_limit = 1000
default_filter_nexthop =
default_minimum_delivery_slots = 3
default_privs = nobody
default_process_limit = 100
default_rbl_reply = $rbl_code Service unavailable; $rbl_class [$rbl_what] blocked using $rbl_domain${rbl_reason?; $rbl_reason}
default_recipient_limit = 20000
default_recipient_refill_delay = 5s
default_recipient_refill_limit = 100
default_transport = smtp
default_verp_delimiters = +=
defer_code = 450
defer_service_name = defer
defer_transports =
delay_logging_resolution_limit = 2
delay_notice_recipient = postmaster
delay_warning_time = 0h
deliver_lock_attempts = 20
deliver_lock_delay = 1s
destination_concurrency_feedback_debug = no
detect_8bit_encoding_header = yes
disable_dns_lookups = no
disable_mime_input_processing = no
disable_mime_output_conversion = no
disable_verp_bounces = no
disable_vrfy_command = no
dnsblog_reply_delay = 0s
dnsblog_service_name = dnsblog
dont_remove = 0
double_bounce_sender = double-bounce
duplicate_filter_limit = 1000
empty_address_default_transport_maps_lookup_key = <>
empty_address_recipient = MAILER-DAEMON
empty_address_relayhost_maps_lookup_key = <>
enable_long_queue_ids = no
enable_original_recipient = yes
error_delivery_slot_cost = $default_delivery_slot_cost
error_delivery_slot_discount = $default_delivery_slot_discount
error_delivery_slot_loan = $default_delivery_slot_loan
error_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
error_destination_concurrency_limit = $default_destination_concurrency_limit
error_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
error_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
error_destination_rate_delay = $default_destination_rate_delay
error_destination_recipient_limit = $default_destination_recipient_limit
error_extra_recipient_limit = $default_extra_recipient_limit
error_initial_destination_concurrency = $initial_destination_concurrency
error_minimum_delivery_slots = $default_minimum_delivery_slots
error_notice_recipient = postmaster
error_recipient_limit = $default_recipient_limit
error_recipient_refill_delay = $default_recipient_refill_delay
error_recipient_refill_limit = $default_recipient_refill_limit
error_service_name = error
execution_directory_expansion_filter = 1234567890!@%-_=+:,./abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ
expand_owner_alias = no
export_environment = TZ MAIL_CONFIG LANG
fallback_transport =
fallback_transport_maps =
fast_flush_domains = $relay_domains
fast_flush_purge_time = 7d
fast_flush_refresh_time = 12h
fault_injection_code = 0
flush_service_name = flush
fork_attempts = 5
fork_delay = 1s
forward_expansion_filter = 1234567890!@%-_=+:,./abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ
forward_path = $home/.forward${recipient_delimiter}${extension}, $home/.forward
frozen_delivered_to = yes
hash_queue_depth = 1
hash_queue_names = deferred, defer
header_address_token_limit = 10240
header_checks =
header_size_limit = 102400
helpful_warnings = yes
home_mailbox =
hopcount_limit = 50
html_directory = no
ifmail_delivery_slot_cost = $default_delivery_slot_cost
ifmail_delivery_slot_discount = $default_delivery_slot_discount
ifmail_delivery_slot_loan = $default_delivery_slot_loan
ifmail_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
ifmail_destination_concurrency_limit = $default_destination_concurrency_limit
ifmail_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
ifmail_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
ifmail_destination_rate_delay = $default_destination_rate_delay
ifmail_destination_recipient_limit = $default_destination_recipient_limit
ifmail_extra_recipient_limit = $default_extra_recipient_limit
ifmail_initial_destination_concurrency = $initial_destination_concurrency
ifmail_minimum_delivery_slots = $default_minimum_delivery_slots
ifmail_recipient_limit = $default_recipient_limit
ifmail_recipient_refill_delay = $default_recipient_refill_delay
ifmail_recipient_refill_limit = $default_recipient_refill_limit
ifmail_time_limit = $command_time_limit
ignore_mx_lookup_error = no
import_environment = MAIL_CONFIG MAIL_DEBUG MAIL_LOGTAG TZ XAUTHORITY DISPLAY LANG=C
in_flow_delay = 1s
inet_interfaces = all
inet_protocols = all
initial_destination_concurrency = 5
internal_mail_filter_classes =
invalid_hostname_reject_code = 501
ipc_idle = 5s
ipc_timeout = 3600s
ipc_ttl = 1000s
line_length_limit = 2048
lmtp_address_preference = any
lmtp_assume_final = no
lmtp_bind_address =
lmtp_bind_address6 =
lmtp_body_checks =
lmtp_cname_overrides_servername = no
lmtp_connect_timeout = 0s
lmtp_connection_cache_destinations =
lmtp_connection_cache_on_demand = yes
lmtp_connection_cache_time_limit = 2s
lmtp_connection_reuse_time_limit = 300s
lmtp_data_done_timeout = 600s
lmtp_data_init_timeout = 120s
lmtp_data_xfer_timeout = 180s
lmtp_defer_if_no_mx_address_found = no
lmtp_delivery_slot_cost = $default_delivery_slot_cost
lmtp_delivery_slot_discount = $default_delivery_slot_discount
lmtp_delivery_slot_loan = $default_delivery_slot_loan
lmtp_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
lmtp_destination_concurrency_limit = $default_destination_concurrency_limit
lmtp_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
lmtp_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
lmtp_destination_rate_delay = $default_destination_rate_delay
lmtp_destination_recipient_limit = $default_destination_recipient_limit
lmtp_discard_lhlo_keyword_address_maps =
lmtp_discard_lhlo_keywords =
lmtp_dns_resolver_options =
lmtp_enforce_tls = no
lmtp_extra_recipient_limit = $default_extra_recipient_limit
lmtp_generic_maps =
lmtp_header_checks =
lmtp_host_lookup = dns
lmtp_initial_destination_concurrency = $initial_destination_concurrency
lmtp_lhlo_name = $myhostname
lmtp_lhlo_timeout = 300s
lmtp_line_length_limit = 998
lmtp_mail_timeout = 300s
lmtp_mime_header_checks =
lmtp_minimum_delivery_slots = $default_minimum_delivery_slots
lmtp_mx_address_limit = 5
lmtp_mx_session_limit = 2
lmtp_nested_header_checks =
lmtp_per_record_deadline = no
lmtp_pix_workaround_delay_time = 10s
lmtp_pix_workaround_maps =
lmtp_pix_workaround_threshold_time = 500s
lmtp_pix_workarounds = disable_esmtp,delay_dotcrlf
lmtp_quit_timeout = 300s
lmtp_quote_rfc821_envelope = yes
lmtp_randomize_addresses = yes
lmtp_rcpt_timeout = 300s
lmtp_recipient_limit = $default_recipient_limit
lmtp_recipient_refill_delay = $default_recipient_refill_delay
lmtp_recipient_refill_limit = $default_recipient_refill_limit
lmtp_reply_filter =
lmtp_rset_timeout = 20s
lmtp_sasl_auth_cache_name =
lmtp_sasl_auth_cache_time = 90d
lmtp_sasl_auth_enable = no
lmtp_sasl_auth_soft_bounce = yes
lmtp_sasl_mechanism_filter =
lmtp_sasl_password_maps =
lmtp_sasl_path =
lmtp_sasl_security_options = noplaintext, noanonymous
lmtp_sasl_tls_security_options = $lmtp_sasl_security_options
lmtp_sasl_tls_verified_security_options = $lmtp_sasl_tls_security_options
lmtp_sasl_type = cyrus
lmtp_send_dummy_mail_auth = no
lmtp_send_xforward_command = no
lmtp_sender_dependent_authentication = no
lmtp_skip_5xx_greeting = yes
lmtp_skip_quit_response = no
lmtp_starttls_timeout = 300s
lmtp_tcp_port = 24
lmtp_tls_CAfile =
lmtp_tls_CApath =
lmtp_tls_block_early_mail_reply = no
lmtp_tls_cert_file =
lmtp_tls_ciphers = export
lmtp_tls_dcert_file =
lmtp_tls_dkey_file = $lmtp_tls_dcert_file
lmtp_tls_eccert_file =
lmtp_tls_eckey_file = $lmtp_tls_eccert_file
lmtp_tls_enforce_peername = yes
lmtp_tls_exclude_ciphers =
lmtp_tls_fingerprint_cert_match =
lmtp_tls_fingerprint_digest = md5
lmtp_tls_key_file = $lmtp_tls_cert_file
lmtp_tls_loglevel = 0
lmtp_tls_mandatory_ciphers = medium
lmtp_tls_mandatory_exclude_ciphers =
lmtp_tls_mandatory_protocols = !SSLv2
lmtp_tls_note_starttls_offer = no
lmtp_tls_per_site =
lmtp_tls_policy_maps =
lmtp_tls_protocols = !SSLv2
lmtp_tls_scert_verifydepth = 9
lmtp_tls_secure_cert_match = nexthop
lmtp_tls_security_level =
lmtp_tls_session_cache_database =
lmtp_tls_session_cache_timeout = 3600s
lmtp_tls_verify_cert_match = hostname
lmtp_use_tls = no
lmtp_xforward_timeout = 300s
local_command_shell =
local_delivery_slot_cost = $default_delivery_slot_cost
local_delivery_slot_discount = $default_delivery_slot_discount
local_delivery_slot_loan = $default_delivery_slot_loan
local_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
local_destination_concurrency_limit = 2
local_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
local_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
local_destination_rate_delay = $default_destination_rate_delay
local_destination_recipient_limit = 1
local_extra_recipient_limit = $default_extra_recipient_limit
local_header_rewrite_clients = permit_inet_interfaces
local_initial_destination_concurrency = $initial_destination_concurrency
local_minimum_delivery_slots = $default_minimum_delivery_slots
local_recipient_limit = $default_recipient_limit
local_recipient_maps = proxy:unix:passwd.byname $alias_maps
local_recipient_refill_delay = $default_recipient_refill_delay
local_recipient_refill_limit = $default_recipient_refill_limit
local_transport = local:$myhostname
luser_relay =
mail_name = Postfix
mail_owner = postfix
mail_release_date = 20130203
mail_spool_directory = /var/mail
mail_version = 2.9.6
mailbox_command =
mailbox_command_maps =
mailbox_delivery_lock = fcntl, dotlock
mailbox_size_limit = 0
mailbox_transport =
mailbox_transport_maps =
mailman_delivery_slot_cost = $default_delivery_slot_cost
mailman_delivery_slot_discount = $default_delivery_slot_discount
mailman_delivery_slot_loan = $default_delivery_slot_loan
mailman_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
mailman_destination_concurrency_limit = $default_destination_concurrency_limit
mailman_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
mailman_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
mailman_destination_rate_delay = $default_destination_rate_delay
mailman_destination_recipient_limit = $default_destination_recipient_limit
mailman_extra_recipient_limit = $default_extra_recipient_limit
mailman_initial_destination_concurrency = $initial_destination_concurrency
mailman_minimum_delivery_slots = $default_minimum_delivery_slots
mailman_recipient_limit = $default_recipient_limit
mailman_recipient_refill_delay = $default_recipient_refill_delay
mailman_recipient_refill_limit = $default_recipient_refill_limit
mailman_time_limit = $command_time_limit
mailq_path = /usr/bin/mailq
manpage_directory = /usr/share/man
maps_rbl_domains =
maps_rbl_reject_code = 554
masquerade_classes = envelope_sender, header_sender, header_recipient
masquerade_domains =
masquerade_exceptions =
master_service_disable =
max_idle = 100s
max_use = 100
maximal_backoff_time = 4000s
maximal_queue_lifetime = 5d
message_reject_characters =
message_size_limit = 10240000
message_strip_characters =
milter_command_timeout = 30s
milter_connect_macros = j {daemon_name} v
milter_connect_timeout = 30s
milter_content_timeout = 300s
milter_data_macros = i
milter_default_action = tempfail
milter_end_of_data_macros = i
milter_end_of_header_macros = i
milter_header_checks =
milter_helo_macros = {tls_version} {cipher} {cipher_bits} {cert_subject} {cert_issuer}
milter_macro_daemon_name = $myhostname
milter_macro_v = $mail_name $mail_version
milter_mail_macros = i {auth_type} {auth_authen} {auth_author} {mail_addr} {mail_host} {mail_mailer}
milter_protocol = 6
milter_rcpt_macros = i {rcpt_addr} {rcpt_host} {rcpt_mailer}
milter_unknown_command_macros =
mime_boundary_length_limit = 2048
mime_header_checks = $header_checks
mime_nesting_limit = 100
minimal_backoff_time = 300s
multi_instance_directories =
multi_instance_enable = no
multi_instance_group =
multi_instance_name =
multi_instance_wrapper =
multi_recipient_bounce_reject_code = 550
mydestination = localhost
mydomain = twprogrammers.com
myhostname = mail.twprogrammers.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mynetworks_style = subnet
myorigin = /etc/mailname
nested_header_checks = $header_checks
newaliases_path = /usr/bin/newaliases
non_fqdn_reject_code = 504
non_smtpd_milters =
notify_classes = resource, software
owner_request_special = yes
parent_domain_matches_subdomains = debug_peer_list,fast_flush_domains,mynetworks,permit_mx_backup_networks,qmqpd_authorized_clients,smtpd_access_maps
permit_mx_backup_networks =
pickup_service_name = pickup
plaintext_reject_code = 450
postmulti_control_commands = reload flush
postmulti_start_commands = start
postmulti_stop_commands = stop abort drain quick-stop
postscreen_access_list = permit_mynetworks
postscreen_bare_newline_action = ignore
postscreen_bare_newline_enable = no
postscreen_bare_newline_ttl = 30d
postscreen_blacklist_action = ignore
postscreen_cache_cleanup_interval = 12h
postscreen_cache_map = btree:$data_directory/postscreen_cache
postscreen_cache_retention_time = 7d
postscreen_client_connection_count_limit = $smtpd_client_connection_count_limit
postscreen_command_count_limit = 20
postscreen_command_filter =
postscreen_command_time_limit = ${stress?10}${stress:300}s
postscreen_disable_vrfy_command = $disable_vrfy_command
postscreen_discard_ehlo_keyword_address_maps = $smtpd_discard_ehlo_keyword_address_maps
postscreen_discard_ehlo_keywords = $smtpd_discard_ehlo_keywords
postscreen_dnsbl_action = ignore
postscreen_dnsbl_reply_map =
postscreen_dnsbl_sites =
postscreen_dnsbl_threshold = 1
postscreen_dnsbl_ttl = 1h
postscreen_enforce_tls = $smtpd_enforce_tls
postscreen_expansion_filter = $smtpd_expansion_filter
postscreen_forbidden_commands = $smtpd_forbidden_commands
postscreen_greet_action = ignore
postscreen_greet_banner = $smtpd_banner
postscreen_greet_ttl = 1d
postscreen_greet_wait = ${stress?2}${stress:6}s
postscreen_helo_required = $smtpd_helo_required
postscreen_non_smtp_command_action = drop
postscreen_non_smtp_command_enable = no
postscreen_non_smtp_command_ttl = 30d
postscreen_pipelining_action = enforce
postscreen_pipelining_enable = no
postscreen_pipelining_ttl = 30d
postscreen_post_queue_limit = $default_process_limit
postscreen_pre_queue_limit = $default_process_limit
postscreen_reject_footer = $smtpd_reject_footer
postscreen_tls_security_level = $smtpd_tls_security_level
postscreen_use_tls = $smtpd_use_tls
postscreen_watchdog_timeout = 10s
postscreen_whitelist_interfaces = static:all
prepend_delivered_header = command, file, forward
process_id_directory = pid
procmail_delivery_slot_cost = $default_delivery_slot_cost
procmail_delivery_slot_discount = $default_delivery_slot_discount
procmail_delivery_slot_loan = $default_delivery_slot_loan
procmail_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
procmail_destination_concurrency_limit = $default_destination_concurrency_limit
procmail_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
procmail_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
procmail_destination_rate_delay = $default_destination_rate_delay
procmail_destination_recipient_limit = $default_destination_recipient_limit
procmail_extra_recipient_limit = $default_extra_recipient_limit
procmail_initial_destination_concurrency = $initial_destination_concurrency
procmail_minimum_delivery_slots = $default_minimum_delivery_slots
procmail_recipient_limit = $default_recipient_limit
procmail_recipient_refill_delay = $default_recipient_refill_delay
procmail_recipient_refill_limit = $default_recipient_refill_limit
procmail_time_limit = $command_time_limit
propagate_unmatched_extensions = canonical, virtual
proxy_interfaces =
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $sender_bcc_maps $recipient_bcc_maps $smtp_generic_maps $lmtp_generic_maps $alias_maps
proxy_write_maps = $smtp_sasl_auth_cache_name $lmtp_sasl_auth_cache_name $address_verify_map $postscreen_cache_map
proxymap_service_name = proxymap
proxywrite_service_name = proxywrite
qmgr_clog_warn_time = 300s
qmgr_daemon_timeout = 1000s
qmgr_fudge_factor = 100
qmgr_ipc_timeout = 60s
qmgr_message_active_limit = 20000
qmgr_message_recipient_limit = 20000
qmgr_message_recipient_minimum = 10
qmqpd_authorized_clients =
qmqpd_client_port_logging = no
qmqpd_error_delay = 1s
qmqpd_timeout = 300s
queue_directory = /var/spool/postfix
queue_file_attribute_count_limit = 100
queue_minfree = 0
queue_run_delay = 300s
queue_service_name = qmgr
rbl_reply_maps =
readme_directory = no
receive_override_options =
recipient_bcc_maps =
recipient_canonical_classes = envelope_recipient, header_recipient
recipient_canonical_maps =
recipient_delimiter = +
reject_code = 554
reject_tempfail_action = defer_if_permit
relay_clientcerts =
relay_delivery_slot_cost = $default_delivery_slot_cost
relay_delivery_slot_discount = $default_delivery_slot_discount
relay_delivery_slot_loan = $default_delivery_slot_loan
relay_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
relay_destination_concurrency_limit = $default_destination_concurrency_limit
relay_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
relay_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
relay_destination_rate_delay = $default_destination_rate_delay
relay_destination_recipient_limit = $default_destination_recipient_limit
relay_domains = $mydestination
relay_domains_reject_code = 554
relay_extra_recipient_limit = $default_extra_recipient_limit
relay_initial_destination_concurrency = $initial_destination_concurrency
relay_minimum_delivery_slots = $default_minimum_delivery_slots
relay_recipient_limit = $default_recipient_limit
relay_recipient_maps =
relay_recipient_refill_delay = $default_recipient_refill_delay
relay_recipient_refill_limit = $default_recipient_refill_limit
relay_transport = relay
relayhost =
relocated_maps =
remote_header_rewrite_domain =
require_home_directory = no
reset_owner_alias = no
resolve_dequoted_address = yes
resolve_null_domain = no
resolve_numeric_domain = no
retry_delivery_slot_cost = $default_delivery_slot_cost
retry_delivery_slot_discount = $default_delivery_slot_discount
retry_delivery_slot_loan = $default_delivery_slot_loan
retry_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
retry_destination_concurrency_limit = $default_destination_concurrency_limit
retry_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
retry_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
retry_destination_rate_delay = $default_destination_rate_delay
retry_destination_recipient_limit = $default_destination_recipient_limit
retry_extra_recipient_limit = $default_extra_recipient_limit
retry_initial_destination_concurrency = $initial_destination_concurrency
retry_minimum_delivery_slots = $default_minimum_delivery_slots
retry_recipient_limit = $default_recipient_limit
retry_recipient_refill_delay = $default_recipient_refill_delay
retry_recipient_refill_limit = $default_recipient_refill_limit
rewrite_service_name = rewrite
sample_directory = /usr/share/doc/postfix/examples
scalemail-backend_delivery_slot_cost = $default_delivery_slot_cost
scalemail-backend_delivery_slot_discount = $default_delivery_slot_discount
scalemail-backend_delivery_slot_loan = $default_delivery_slot_loan
scalemail-backend_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
scalemail-backend_destination_concurrency_limit = $default_destination_concurrency_limit
scalemail-backend_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
scalemail-backend_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
scalemail-backend_destination_rate_delay = $default_destination_rate_delay
scalemail-backend_destination_recipient_limit = $default_destination_recipient_limit
scalemail-backend_extra_recipient_limit = $default_extra_recipient_limit
scalemail-backend_initial_destination_concurrency = $initial_destination_concurrency
scalemail-backend_minimum_delivery_slots = $default_minimum_delivery_slots
scalemail-backend_recipient_limit = $default_recipient_limit
scalemail-backend_recipient_refill_delay = $default_recipient_refill_delay
scalemail-backend_recipient_refill_limit = $default_recipient_refill_limit
scalemail-backend_time_limit = $command_time_limit
send_cyrus_sasl_authzid = no
sender_bcc_maps =
sender_canonical_classes = envelope_sender, header_sender
sender_canonical_maps =
sender_dependent_default_transport_maps =
sender_dependent_relayhost_maps =
sendmail_fix_line_endings = always
sendmail_path = /usr/sbin/sendmail
service_throttle_time = 60s
setgid_group = postdrop
show_user_unknown_table_name = yes
showq_service_name = showq
smtp_address_preference = any
smtp_always_send_ehlo = yes
smtp_bind_address =
smtp_bind_address6 =
smtp_body_checks =
smtp_cname_overrides_servername = no
smtp_connect_timeout = 30s
smtp_connection_cache_destinations =
smtp_connection_cache_on_demand = yes
smtp_connection_cache_time_limit = 2s
smtp_connection_reuse_time_limit = 300s
smtp_data_done_timeout = 600s
smtp_data_init_timeout = 120s
smtp_data_xfer_timeout = 180s
smtp_defer_if_no_mx_address_found = no
smtp_delivery_slot_cost = $default_delivery_slot_cost
smtp_delivery_slot_discount = $default_delivery_slot_discount
smtp_delivery_slot_loan = $default_delivery_slot_loan
smtp_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
smtp_destination_concurrency_limit = $default_destination_concurrency_limit
smtp_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
smtp_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
smtp_destination_rate_delay = $default_destination_rate_delay
smtp_destination_recipient_limit = $default_destination_recipient_limit
smtp_discard_ehlo_keyword_address_maps =
smtp_discard_ehlo_keywords =
smtp_dns_resolver_options =
smtp_enforce_tls = no
smtp_extra_recipient_limit = $default_extra_recipient_limit
smtp_fallback_relay = $fallback_relay
smtp_generic_maps =
smtp_header_checks =
smtp_helo_name = $myhostname
smtp_helo_timeout = 300s
smtp_host_lookup = dns
smtp_initial_destination_concurrency = $initial_destination_concurrency
smtp_line_length_limit = 998
smtp_mail_timeout = 300s
smtp_mime_header_checks =
smtp_minimum_delivery_slots = $default_minimum_delivery_slots
smtp_mx_address_limit = 5
smtp_mx_session_limit = 2
smtp_nested_header_checks =
smtp_never_send_ehlo = no
smtp_per_record_deadline = no
smtp_pix_workaround_delay_time = 10s
smtp_pix_workaround_maps =
smtp_pix_workaround_threshold_time = 500s
smtp_pix_workarounds = disable_esmtp,delay_dotcrlf
smtp_quit_timeout = 300s
smtp_quote_rfc821_envelope = yes
smtp_randomize_addresses = yes
smtp_rcpt_timeout = 300s
smtp_recipient_limit = $default_recipient_limit
smtp_recipient_refill_delay = $default_recipient_refill_delay
smtp_recipient_refill_limit = $default_recipient_refill_limit
smtp_reply_filter =
smtp_rset_timeout = 20s
smtp_sasl_auth_cache_name =
smtp_sasl_auth_cache_time = 90d
smtp_sasl_auth_enable = no
smtp_sasl_auth_soft_bounce = yes
smtp_sasl_mechanism_filter =
smtp_sasl_password_maps =
smtp_sasl_path =
smtp_sasl_security_options = noplaintext, noanonymous
smtp_sasl_tls_security_options = $smtp_sasl_security_options
smtp_sasl_tls_verified_security_options = $smtp_sasl_tls_security_options
smtp_sasl_type = cyrus
smtp_send_dummy_mail_auth = no
smtp_send_xforward_command = no
smtp_sender_dependent_authentication = no
smtp_skip_5xx_greeting = yes
smtp_skip_quit_response = yes
smtp_starttls_timeout = 300s
smtp_tls_CAfile =
smtp_tls_CApath =
smtp_tls_block_early_mail_reply = no
smtp_tls_cert_file =
smtp_tls_ciphers = export
smtp_tls_dcert_file =
smtp_tls_dkey_file = $smtp_tls_dcert_file
smtp_tls_eccert_file =
smtp_tls_eckey_file = $smtp_tls_eccert_file
smtp_tls_enforce_peername = yes
smtp_tls_exclude_ciphers =
smtp_tls_fingerprint_cert_match =
smtp_tls_fingerprint_digest = md5
smtp_tls_key_file = $smtp_tls_cert_file
smtp_tls_loglevel = 0
smtp_tls_mandatory_ciphers = medium
smtp_tls_mandatory_exclude_ciphers =
smtp_tls_mandatory_protocols = !SSLv2
smtp_tls_note_starttls_offer = no
smtp_tls_per_site =
smtp_tls_policy_maps =
smtp_tls_protocols = !SSLv2
smtp_tls_scert_verifydepth = 9
smtp_tls_secure_cert_match = nexthop, dot-nexthop
smtp_tls_security_level =
smtp_tls_session_cache_database =
smtp_tls_session_cache_timeout = 3600s
smtp_tls_verify_cert_match = hostname
smtp_use_tls = no
smtp_xforward_timeout = 300s
smtpd_authorized_verp_clients = $authorized_verp_clients
smtpd_authorized_xclient_hosts =
smtpd_authorized_xforward_hosts =
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_client_connection_count_limit = 50
smtpd_client_connection_rate_limit = 0
smtpd_client_event_limit_exceptions = ${smtpd_client_connection_limit_exceptions:$mynetworks}
smtpd_client_message_rate_limit = 0
smtpd_client_new_tls_session_rate_limit = 0
smtpd_client_port_logging = no
smtpd_client_recipient_rate_limit = 0
smtpd_client_restrictions =
smtpd_command_filter =
smtpd_data_restrictions =
smtpd_delay_open_until_valid_rcpt = yes
smtpd_delay_reject = yes
smtpd_discard_ehlo_keyword_address_maps =
smtpd_discard_ehlo_keywords =
smtpd_end_of_data_restrictions =
smtpd_enforce_tls = no
smtpd_error_sleep_time = 1s
smtpd_etrn_restrictions =
smtpd_expansion_filter = \t\40!"#$%&'()*+,-./0123456789:;<=>?@ABCDEFGHIJKLMNOPQRSTUVWXYZ[\\]^_`abcdefghijklmnopqrstuvwxyz{|}~
smtpd_forbidden_commands = CONNECT GET POST
smtpd_hard_error_limit = ${stress?1}${stress:20}
smtpd_helo_required = no
smtpd_helo_restrictions =
smtpd_history_flush_threshold = 100
smtpd_junk_command_limit = ${stress?1}${stress:100}
smtpd_milters =
smtpd_noop_commands =
smtpd_null_access_lookup_key = <>
smtpd_peername_lookup = yes
smtpd_per_record_deadline = ${stress?yes}${stress:no}
smtpd_policy_service_max_idle = 300s
smtpd_policy_service_max_ttl = 1000s
smtpd_policy_service_timeout = 100s
smtpd_proxy_ehlo = $myhostname
smtpd_proxy_filter =
smtpd_proxy_options =
smtpd_proxy_timeout = 100s
smtpd_recipient_limit = 1000
smtpd_recipient_overshoot_limit = 1000
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination
smtpd_reject_footer =
smtpd_reject_unlisted_recipient = yes
smtpd_reject_unlisted_sender = no
smtpd_restriction_classes =
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = no
smtpd_sasl_exceptions_networks =
smtpd_sasl_local_domain =
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_tls_security_options = $smtpd_sasl_security_options
smtpd_sasl_type = dovecot
smtpd_sender_login_maps =
smtpd_sender_restrictions =
smtpd_service_name = smtpd
smtpd_soft_error_limit = 10
smtpd_starttls_timeout = ${stress?10}${stress:300}s
smtpd_timeout = ${stress?10}${stress:300}s
smtpd_tls_CAfile =
smtpd_tls_CApath =
smtpd_tls_always_issue_session_ids = yes
smtpd_tls_ask_ccert = no
smtpd_tls_auth_only = yes
smtpd_tls_ccert_verifydepth = 9
smtpd_tls_cert_file = /etc/ssl/certs/dovecot.pem
smtpd_tls_ciphers = export
smtpd_tls_dcert_file =
smtpd_tls_dh1024_param_file =
smtpd_tls_dh512_param_file =
smtpd_tls_dkey_file = $smtpd_tls_dcert_file
smtpd_tls_eccert_file =
smtpd_tls_eckey_file = $smtpd_tls_eccert_file
smtpd_tls_eecdh_grade = strong
smtpd_tls_exclude_ciphers =
smtpd_tls_fingerprint_digest = md5
smtpd_tls_key_file = /etc/ssl/private/dovecot.pem
smtpd_tls_loglevel = 0
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_mandatory_exclude_ciphers =
smtpd_tls_mandatory_protocols = !SSLv2
smtpd_tls_protocols =
smtpd_tls_received_header = no
smtpd_tls_req_ccert = no
smtpd_tls_security_level =
smtpd_tls_session_cache_database =
smtpd_tls_session_cache_timeout = 3600s
smtpd_tls_wrappermode = no
smtpd_use_tls = yes
soft_bounce = no
stale_lock_time = 500s
stress =
strict_7bit_headers = no
strict_8bitmime = no
strict_8bitmime_body = no
strict_mailbox_ownership = yes
strict_mime_encoding_domain = no
strict_rfc821_envelopes = no
sun_mailtool_compatibility = no
swap_bangpath = yes
syslog_facility = mail
syslog_name = ${multi_instance_name:postfix}${multi_instance_name?$multi_instance_name}
tcp_windowsize = 0
tls_append_default_CA = no
tls_daemon_random_bytes = 32
tls_disable_workarounds =
tls_eecdh_strong_curve = prime256v1
tls_eecdh_ultra_curve = secp384r1
tls_export_cipherlist = aNULL:-aNULL:ALL:+RC4:@STRENGTH
tls_high_cipherlist = aNULL:-aNULL:ALL:!EXPORT:!LOW:!MEDIUM:+RC4:@STRENGTH
tls_legacy_public_key_fingerprints = no
tls_low_cipherlist = aNULL:-aNULL:ALL:!EXPORT:+RC4:@STRENGTH
tls_medium_cipherlist = aNULL:-aNULL:ALL:!EXPORT:!LOW:+RC4:@STRENGTH
tls_null_cipherlist = eNULL:!aNULL
tls_preempt_cipherlist = no
tls_random_bytes = 32
tls_random_exchange_name = ${data_directory}/prng_exch
tls_random_prng_update_period = 3600s
tls_random_reseed_period = 3600s
tls_random_source = dev:/dev/urandom
tlsproxy_enforce_tls = $smtpd_enforce_tls
tlsproxy_service_name = tlsproxy
tlsproxy_tls_CAfile = $smtpd_tls_CAfile
tlsproxy_tls_CApath = $smtpd_tls_CApath
tlsproxy_tls_always_issue_session_ids = $smtpd_tls_always_issue_session_ids
tlsproxy_tls_ask_ccert = $smtpd_tls_ask_ccert
tlsproxy_tls_ccert_verifydepth = $smtpd_tls_ccert_verifydepth
tlsproxy_tls_cert_file = $smtpd_tls_cert_file
tlsproxy_tls_ciphers = $smtpd_tls_ciphers
tlsproxy_tls_dcert_file = $smtpd_tls_dcert_file
tlsproxy_tls_dh1024_param_file = $smtpd_tls_dh1024_param_file
tlsproxy_tls_dh512_param_file = $smtpd_tls_dh512_param_file
tlsproxy_tls_dkey_file = $smtpd_tls_dkey_file
tlsproxy_tls_eccert_file = $smtpd_tls_eccert_file
tlsproxy_tls_eckey_file = $smtpd_tls_eckey_file
tlsproxy_tls_eecdh_grade = $smtpd_tls_eecdh_grade
tlsproxy_tls_exclude_ciphers = $smtpd_tls_exclude_ciphers
tlsproxy_tls_fingerprint_digest = $smtpd_tls_fingerprint_digest
tlsproxy_tls_key_file = $smtpd_tls_key_file
tlsproxy_tls_loglevel = $smtpd_tls_loglevel
tlsproxy_tls_mandatory_ciphers = $smtpd_tls_mandatory_ciphers
tlsproxy_tls_mandatory_exclude_ciphers = $smtpd_tls_mandatory_exclude_ciphers
tlsproxy_tls_mandatory_protocols = $smtpd_tls_mandatory_protocols
tlsproxy_tls_protocols = $smtpd_tls_protocols
tlsproxy_tls_req_ccert = $smtpd_tls_req_ccert
tlsproxy_tls_security_level = $smtpd_tls_security_level
tlsproxy_tls_session_cache_timeout = $smtpd_tls_session_cache_timeout
tlsproxy_use_tls = $smtpd_use_tls
tlsproxy_watchdog_timeout = 10s
trace_service_name = trace
transport_maps =
transport_retry_time = 60s
trigger_timeout = 10s
undisclosed_recipients_header =
unknown_address_reject_code = 450
unknown_address_tempfail_action = $reject_tempfail_action
unknown_client_reject_code = 450
unknown_helo_hostname_tempfail_action = $reject_tempfail_action
unknown_hostname_reject_code = 450
unknown_local_recipient_reject_code = 550
unknown_relay_recipient_reject_code = 550
unknown_virtual_alias_reject_code = 550
unknown_virtual_mailbox_reject_code = 550
unverified_recipient_defer_code = 450
unverified_recipient_reject_code = 450
unverified_recipient_reject_reason =
unverified_recipient_tempfail_action = $reject_tempfail_action
unverified_sender_defer_code = 450
unverified_sender_reject_code = 450
unverified_sender_reject_reason =
unverified_sender_tempfail_action = $reject_tempfail_action
uucp_delivery_slot_cost = $default_delivery_slot_cost
uucp_delivery_slot_discount = $default_delivery_slot_discount
uucp_delivery_slot_loan = $default_delivery_slot_loan
uucp_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
uucp_destination_concurrency_limit = $default_destination_concurrency_limit
uucp_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
uucp_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
uucp_destination_rate_delay = $default_destination_rate_delay
uucp_destination_recipient_limit = $default_destination_recipient_limit
uucp_extra_recipient_limit = $default_extra_recipient_limit
uucp_initial_destination_concurrency = $initial_destination_concurrency
uucp_minimum_delivery_slots = $default_minimum_delivery_slots
uucp_recipient_limit = $default_recipient_limit
uucp_recipient_refill_delay = $default_recipient_refill_delay
uucp_recipient_refill_limit = $default_recipient_refill_limit
uucp_time_limit = $command_time_limit
verp_delimiter_filter = -=+
virtual_alias_domains = $virtual_alias_maps
virtual_alias_expansion_limit = 1000
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual-alias-maps.cf
virtual_alias_recursion_limit = 1000
virtual_delivery_slot_cost = $default_delivery_slot_cost
virtual_delivery_slot_discount = $default_delivery_slot_discount
virtual_delivery_slot_loan = $default_delivery_slot_loan
virtual_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
virtual_destination_concurrency_limit = $default_destination_concurrency_limit
virtual_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
virtual_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
virtual_destination_rate_delay = $default_destination_rate_delay
virtual_destination_recipient_limit = $default_destination_recipient_limit
virtual_extra_recipient_limit = $default_extra_recipient_limit
virtual_gid_maps =
virtual_initial_destination_concurrency = $initial_destination_concurrency
virtual_mailbox_base =
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf
virtual_mailbox_limit = 51200000
virtual_mailbox_lock = fcntl, dotlock
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf
virtual_minimum_delivery_slots = $default_minimum_delivery_slots
virtual_minimum_uid = 100
virtual_recipient_limit = $default_recipient_limit
virtual_recipient_refill_delay = $default_recipient_refill_delay
virtual_recipient_refill_limit = $default_recipient_refill_limit
virtual_transport = lmtp:unix:private/dovecot-lmtp
virtual_uid_maps =

```
cat /etc/postfix/master.cf|egrep -i -v '^((\s+)?#)'
```

smtp      inet  n       -       -       -       -       smtpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
relay     unix  -       -       -       -       -       smtp
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
procmail  unix  -       n       n       -       -       pipe
  flags=DRO user=vmail argv=/usr/bin/procmail -t -m USER=${user}
  RECIPIENT=${recipient} /etc/procmailrc
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix    -    n    n    -    2    pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

```
cat /etc/procmailrc
```

:0
* RECIPIENT ?? .*@\/.*$
{ DOMAIN = "$MATCH" }
# file: /etc/procmailrc
# system-wide settings for procmail
:0fw: spamassassin.lock
* < 256000
| spamc
SHELL="/bin/bash"
SENDMAIL="/usr/sbin/sendmail -oi -t"
VERBOSE=on
LOGFILE="/var/log/procmail.log"
DELIVER="/usr/lib/dovecot/deliver"
# fallback:
DEFAULT="/var/mail/vhosts/$DOMAIN/$USER/"
MAILDIR="/var/mail/vhosts/$DOMAIN/$USER/"
:0 w
* ^X-Spam-Status: Yes
| $DELIVER -m Spam
:0 w
* ^TO.*postmaster@twprogrammers.com
| $DELIVER -m Postmaster
:0 w
* ^TO.*webmaster@twprogrammers.com
| $DELIVER -m Webmaster
:0 w
* ^TO.*bug@twprogrammers.com
| $DELIVER -m Bugs
:0 w
* ^TO.*bugs@twprogrammers.com
| $DELIVER -m Bugs
:0 w
* ^TO.*forum@twprogrammers.com
| $DELIVER -m Forums
:0 w
* ^TO.*forums@twprogrammers.com
| $DELIVER -m Forums
:0 w
| $DELIVER

```
cat /etc/default/spamassassin|egrep -i -v '^((\s+)?#)'
```

ENABLED=1
SAHOME="/var/log/spamassassin/"
OPTIONS="--create-prefs --max-children 2 --username spamd -H ${SAHOME} -s ${SAHOME}spamd.log"
PIDFILE="/var/run/spamd.pid"
CRON=0

```

---

### Post by SeijiSensei on 2014-01-29
Procmail can filter on any header it finds.  It has a special macro for To addresses that include things like cc's, etc.  See "[man procmailrc]("http://linux.die.net/man/5/procmailrc")" for all the gritty details and "[man procmailex]("http://linux.die.net/man/5/procmailex")" for a variety of useful example recipes.

The method I gave uses .forward to send mail to procmail so you don't have to change anything in the Postfix config.  When maildrop delivers the message to your user account, it finds the ~/.forward file and hands the message over to procmail for further processing.  I looked at some other solutions, like the Postfix-only one I cited above, but they required more futzing with the Postfix internals than using a simple .forward to invoke procmail.

The .forward method also lets you restrict the application of procmail by username.  Only users with the appropriate .forward file in their home directories will have their mail passed to procmail and scanned by SpamAssassin.  That way you can scan your own mail and not scan mail for other clients if you wish.

---

### Post by wolfgentleman on 2014-01-29
updated post

---

### Post by SeijiSensei on 2014-01-29
> **wolfgentleman said:**
> However nothing is being dropped in any other folder than inbox...

The [dovecot wiki]("http://wiki2.dovecot.org/procmail#Ubuntu_12.04_Update") suggests splitting up the sendmail command like this:
```

SENDMAIL=/usr/sbin/sendmail
SENDMAILFLAGS="-oi"

```
The wiki also doesn't use the -t switch.  I don't know whether that matters or not.

Otherwise the configuration looks like it should work.  What do you see in /var/log/procmail.log? Whose inbox gets all the mail? Is it directed to the correct virtual user but not filtered?

---

### Post by wolfgentleman on 2014-01-29
> **SeijiSensei said:**
> What do you see in /var/log/procmail.log?
For some reason it didn't exist, I created it with touch when I finished the configs and restarted postfix. Just created it again with touch and verified with 'ls /var/log' that it exists.
> **SeijiSensei said:**
> Whose inbox gets all the mail? Is it directed to the correct virtual user but not filtered?
Hmmm... I forgot to test that... Let me test that right quick. To my knowledge it is going to the proper user but I haven't tested sending an email to to the other user, but no it's not being filtered. I will restart Postfix again and send a test mail to the other user.

UPDATE:
Well, crap. It's sending everything to the admin user... and the log is of no use as it is empty.

---

### Post by SeijiSensei on 2014-01-31
```

:0
* RECIPIENT ?? .*@\/.*$
{ DOMAIN = "$MATCH" }
# file: /etc/procmailrc
# system-wide settings for procmail
:0fw: spamassassin.lock
* < 256000
| spamc
SHELL="/bin/bash"
SENDMAIL="/usr/sbin/sendmail -oi -t"
VERBOSE=on
LOGFILE="/var/log/procmail.log"
DELIVER="/usr/lib/dovecot/deliver"
# fallback:
DEFAULT="/var/mail/vhosts/$DOMAIN/$USER/"
MAILDIR="/var/mail/vhosts/$DOMAIN/$USER/"

```

[s]I don't know what that first recipe is supposed to do.  Where is $MATCH set?[/s]
I see, you're trying to extract the domain from the email address.  I take it the RECIPIENT header is something found in messages with delivery to virtual mailboxes?

I also think you need to use the $LOGNAME environment variable rather than $USER.  See "man procmailrc" for the list of available variables.

 I'd also put all the environment variables ahead of any recipes and write the top of procmailrc like this:
```

# file: /etc/procmailrc
# system-wide settings for procmail
SHELL="/bin/bash"
SENDMAIL=/usr/sbin/sendmail
SENDMAILFLAGS="-oi"
VERBOSE=on
LOGFILE="/var/log/procmail.log"
DELIVER="/usr/lib/dovecot/deliver"

:0
* RECIPIENT ?? .*@\/.*$
{ DOMAIN = "$MATCH" }

# fallback:
DEFAULT="/var/mail/vhosts/$DOMAIN/$LOGNAME/"
MAILDIR="/var/mail/vhosts/$DOMAIN/$LOGNAME/"

:0fw: spamassassin.lock
* < 256000
| spamc

[etc.]

```

---

### Post by wolfgentleman on 2014-01-31
> **SeijiSensei said:**
> 
I see, you're trying to extract the domain from the email address.  I take it the RECIPIENT header is something found in messages with delivery to virtual mailboxes?

I also think you need to use the $LOGNAME environment variable rather than $USER.  See "man procmailrc" for the list of available variables.
> **master.cf]
procmail  unix  -       n       n       -       -       pipe
  flags=DRO user=vmail argv=/usr/bin/procmail -t -m **USER=${user}**
  **RECIPIENT=${recipient}** /etc/procmail/rc
[/QUOTE]
$USER and $RECIPIENT is set in that. BTW, I created a directory in /etc called procmail with a subdirectory of bak and then I moved /etc/procmailrc into it renaming it rc, for ease of backups. UPDATE: $LOGNAME delivered it to the void. I used $USER and it worked fine, that is after I changed it and took a 2 hour nap :P.

[QUOTE=SeijiSensei said:**
> 
 I'd also put all the environment variables ahead of any recipes and write the top of procmailrc like this:
```

# file: /etc/procmailrc
# system-wide settings for procmail
SHELL="/bin/bash"
SENDMAIL=/usr/sbin/sendmail
SENDMAILFLAGS="-oi"
VERBOSE=on
LOGFILE="/var/log/procmail.log"
DELIVER="/usr/lib/dovecot/deliver"

:0
* RECIPIENT ?? .*@\/.*$
{ DOMAIN = "$MATCH" }

# fallback:
DEFAULT="/var/mail/vhosts/$DOMAIN/$LOGNAME/"
MAILDIR="/var/mail/vhosts/$DOMAIN/$LOGNAME/"

:0fw: spamassassin.lock
* < 256000
| spamc

[etc.]

```
I can do that... but ATM I have a bigger problem. I rebooted the server and now I cannot [s]send[/s] (Fixed) *or receive* any mail whatsoever. I rummaged through the logs and found nothing. I (backed up and) deleted all configs, 'apt-get remove --purge'-ed all things dovecot and postfix, then I followed the directions from Linode on setting up everything skipping the MySQL db setup. Now The logs say:
[s][QUOTE=mail.err]
Jan 30 23:29:07 Frask postfix/smtpd[1436]: fatal: open lock file pid/inet.smtp: cannot create file exclusively: No such file or directory
[/QUOTE]
[QUOTE=mail.warn]
Jan 30 23:29:08 Frask postfix/master[19824]: warning: process /usr/lib/postfix/smtpd pid 1436 exit status 1
Jan 30 23:29:08 Frask postfix/master[19824]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jan 30 23:29:24 Frask postfix/master[19824]: warning: master_wakeup_timer_event: service qmgr(public/qmgr): No such file or directory
[/QUOTE]
stopped postfix and rsyslog, deleted /var/log/mail.*, started rsyslog. Now they are empty, ok... start postfix... same errors as below.
prior to using "service postfix start" and:
[QUOTE=mail.err]
Feb  1 01:26:39 Frask postfix/master[7383]: fatal: bind 0.0.0.0 port 25: Address already in use
Feb  1 01:26:39 Frask postfix/smtpd[7384]: fatal: open lock file pid/inet.smtp: cannot create file exclusively: No such file or directory
[/QUOTE]
[QUOTE=mail.warn]
Jan 30 23:29:08 Frask postfix/master[19824]: warning: process /usr/lib/postfix/smtpd pid 1436 exit status 1
Jan 30 23:29:08 Frask postfix/master[19824]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jan 30 23:29:24 Frask postfix/master[19824]: warning: master_wakeup_timer_event: service qmgr(public/qmgr): No such file or directory
Jan 30 23:29:51 Frask postfix/master[19824]: warning: master_wakeup_timer_event: service pickup(public/pickup): No such file or directory
[/QUOTE]
after. The second line in mail.err is displayed 1543 times, some of it before and some after the first line. The total line count for mail.err is 1544.[/s]
I have fixed almost everything... But one thing escapes me - receiving. Here is a few things:

[LIST]
[*]mail.err is empty 
[*]mail.warn is empty 
[*]mailq outputs: 
[/LIST]
```
-Queue ID- --Size-- ----Arrival Time---- -Sender/Recipient-------
7880B50F8A     2071 Sat Feb  1 14:12:17  pwthomas95@satx.rr.com
(lost connection with mail.twprogrammers.com[private/dovecot-lmtp] while receiving the initial
server greeting)
                                         admin@twprogrammers.com

2FD9F50F8E     2071 Sat Feb  1 14:12:18  pwthomas95@satx.rr.com
(lost connection with mail.twprogrammers.com[private/dovecot-lmtp] while receiving the initial
server greeting)
                                         admin@twprogrammers.com

D30F850F8D     2071 Sat Feb  1 14:12:17  pwthomas95@satx.rr.com
(lost connection with mail.twprogrammers.com[private/dovecot-lmtp] while receiving the initial
server greeting)
                                         admin@twprogrammers.com

0B87F50F8F     1233 Sat Feb  1 15:02:49  pwthomas95@satx.rr.com
(lost connection with mail.twprogrammers.com[private/dovecot-lmtp] while receiving the initial
server greeting)
                                         admin@twprogrammers.com

-- 10 Kbytes in 4 Requests.
```
[LIST]
[*]mail.log contains: 
[/LIST]
```
Feb  1 14:44:08 Frask postfix/master[4331]: daemon started -- version 2.9.6, configuration /etc/postfix
Feb  1 14:44:28 Frask postfix/smtpd[4351]: connect from li341-187.members.linode.com[96.126.116.187]
Feb  1 14:44:28 Frask postfix/smtpd[4351]: lost connection after UNKNOWN from li341-187.members.linode.com[96.126.116.187]
Feb  1 14:44:28 Frask postfix/smtpd[4351]: disconnect from li341-187.members.linode.com[96.126.116.187]
Feb  1 14:45:06 Frask postfix/smtpd[4351]: connect from localhost[127.0.0.1]
Feb  1 14:45:37 Frask postfix/smtpd[4351]: lost connection after HELO from localhost[127.0.0.1]
Feb  1 14:45:37 Frask postfix/smtpd[4351]: disconnect from localhost[127.0.0.1]
Feb  1 14:48:57 Frask postfix/anvil[4354]: statistics: max connection rate 1/60s for (smtp:96.126.116.187) at Feb  1 14:44:28
Feb  1 14:48:57 Frask postfix/anvil[4354]: statistics: max connection count 1 for (smtp:96.126.116.187) at Feb  1 14:44:28
Feb  1 14:48:57 Frask postfix/anvil[4354]: statistics: max cache size 1 at Feb  1 14:44:28
Feb  1 14:52:09 Frask postfix/smtpd[4484]: connect from li341-187.members.linode.com[96.126.116.187]
Feb  1 14:52:40 Frask postfix/smtpd[4484]: lost connection after HELO from li341-187.members.linode.com[96.126.116.187]
Feb  1 14:52:40 Frask postfix/smtpd[4484]: disconnect from li341-187.members.linode.com[96.126.116.187]
Feb  1 14:52:53 Frask postfix/smtpd[4484]: connect from li341-187.members.linode.com[96.126.116.187]
Feb  1 14:52:53 Frask postfix/smtpd[4484]: lost connection after UNKNOWN from li341-187.members.linode.com[96.126.116.187]
Feb  1 14:52:53 Frask postfix/smtpd[4484]: disconnect from li341-187.members.linode.com[96.126.116.187]
Feb  1 14:53:03 Frask postfix/smtpd[4484]: connect from li341-187.members.linode.com[96.126.116.187]
Feb  1 14:53:03 Frask postfix/smtpd[4484]: lost connection after UNKNOWN from li341-187.members.linode.com[96.126.116.187]
Feb  1 14:53:03 Frask postfix/smtpd[4484]: disconnect from li341-187.members.linode.com[96.126.116.187]
Feb  1 14:53:22 Frask postfix/smtpd[4484]: connect from cpe-70-114-11-49.satx.res.rr.com[70.114.11.49]
Feb  1 14:53:28 Frask postfix/smtpd[4484]: warning: TLS library problem: 4484:error:14094418:SSL routines:SSL3_READ_BYTES:tlsv1 alert unknown ca:s3_pkt.c:1256:SSL alert number 48:
Feb  1 14:53:28 Frask postfix/smtpd[4484]: lost connection after STARTTLS from cpe-70-114-11-49.satx.res.rr.com[70.114.11.49]
Feb  1 14:53:28 Frask postfix/smtpd[4484]: disconnect from cpe-70-114-11-49.satx.res.rr.com[70.114.11.49]
Feb  1 14:56:48 Frask postfix/anvil[4486]: statistics: max connection rate 3/60s for (smtp:96.126.116.187) at Feb  1 14:53:03
Feb  1 14:56:48 Frask postfix/anvil[4486]: statistics: max connection count 1 for (smtp:96.126.116.187) at Feb  1 14:52:09
Feb  1 14:56:48 Frask postfix/anvil[4486]: statistics: max cache size 2 at Feb  1 14:53:22
Feb  1 15:01:14 Frask postfix/smtpd[4515]: connect from cpe-70-114-11-49.satx.res.rr.com[70.114.11.49]
Feb  1 15:01:14 Frask postfix/smtpd[4515]: F00BF50F8F: client=cpe-70-114-11-49.satx.res.rr.com[70.114.11.49], sasl_method=PLAIN, sasl_username=admin@twprogrammers.com
Feb  1 15:01:15 Frask postfix/cleanup[4521]: F00BF50F8F: message-id=<52ED0C4B.6080801@twprogrammers.com>
Feb  1 15:01:15 Frask postfix/qmgr[4333]: F00BF50F8F: from=<admin@twprogrammers.com>, size=601, nrcpt=1 (queue active)
Feb  1 15:01:15 Frask postfix/smtpd[4515]: disconnect from cpe-70-114-11-49.satx.res.rr.com[70.114.11.49]
Feb  1 15:01:17 Frask postfix/smtp[4523]: F00BF50F8F: to=<pwthomas95@satx.rr.com>, relay=cdptpa-smtpin01.mail.rr.com[75.180.132.243]:25, delay=2.7, delays=0.08/0.01/2.3/0.31, dsn=2.0.0, status=sent (250 OK D3/4A-10390-C3C0DE25)
Feb  1 15:01:17 Frask postfix/qmgr[4333]: F00BF50F8F: removed
Feb  1 15:02:49 Frask postfix/smtpd[4515]: connect from cdptpa-omtalb.mail.rr.com[75.180.132.120]
Feb  1 15:02:50 Frask postfix/smtpd[4515]: 0B87F50F8F: client=cdptpa-omtalb.mail.rr.com[75.180.132.120]
Feb  1 15:02:50 Frask postfix/cleanup[4521]: 0B87F50F8F: message-id=<52ED0CAA.6020301@satx.rr.com>
Feb  1 15:02:50 Frask postfix/qmgr[4333]: 0B87F50F8F: from=<pwthomas95@satx.rr.com>, size=1233, nrcpt=1 (queue active)
Feb  1 15:02:50 Frask postfix/lmtp[4526]: 0B87F50F8F: to=<admin@twprogrammers.com>, relay=mail.twprogrammers.com[private/dovecot-lmtp], delay=0.17, delays=0.15/0.01/0.01/0, dsn=4.4.2, status=deferred (lost connection with mail.twprogrammers.com[private/dovecot-lmtp] while receiving the initial server greeting)
Feb  1 15:02:55 Frask postfix/smtpd[4515]: disconnect from cdptpa-omtalb.mail.rr.com[75.180.132.120]
Feb  1 15:06:15 Frask postfix/anvil[4517]: statistics: max connection rate 1/60s for (smtp:70.114.11.49) at Feb  1 15:01:14
Feb  1 15:06:15 Frask postfix/anvil[4517]: statistics: max connection count 1 for (smtp:70.114.11.49) at Feb  1 15:01:14
Feb  1 15:06:15 Frask postfix/anvil[4517]: statistics: max cache size 1 at Feb  1 15:01:14
Feb  1 15:09:08 Frask postfix/qmgr[4333]: 0B87F50F8F: from=<pwthomas95@satx.rr.com>, size=1233, nrcpt=1 (queue active)
Feb  1 15:09:08 Frask postfix/lmtp[4550]: 0B87F50F8F: to=<admin@twprogrammers.com>, relay=mail.twprogrammers.com[private/dovecot-lmtp], delay=379, delays=379/0.02/0.01/0, dsn=4.4.2, status=deferred (lost connection with mail.twprogrammers.com[private/dovecot-lmtp] while receiving the
initial server greeting)
```
So, I am going on another internet info hunt... Fun. After I get that straitened, I can begin modding configs for procmail, again.
UPDATE:
[s]Hmmm... Well, I thought I had it working. It says procmail delivered it... If it did it was to the void.[/s]
HAHA!!! Ok, [s]for some reason it just mysteriously started working[/s] it was what I was using for the username portion, check above... So I an going to run a few other tests and report back with the results. Alright, here is the results:
Everything is being delivered to my catch-everything-else user, however it is being placed in the proper folders so that's a plus.
Here is the contents of virtual_aliases
```

id        domain_id        source                            destination
1        1            helpfulbatchfiles@twprogrammers.com    hbf@twprogrammers.com
2        1            co-owner@twprogrammers.com            hbf@twprogrammers.com
3        1            co-founder@twprogrammers.com            hbf@twprogrammers.com
100        1            @twprogrammers.com                    admin@twprogrammers.com
1000        4            @hawkladybeadery.com                REMOVED@satx.rr.com

```

---

### Post by wolfgentleman on 2014-02-02
[s]bump.[/s] - reopening my [other question]("http://ubuntuforums.org/showthread.php?t=2197996") as this belongs to it.
Also I figured out why $LOGNAME delivered it to the void. With my setup $LOGNAME always =vmail
I have everything else working. When I finish the catch-everything-else, I will post an entire tutorial (and possibly write a script) [here](http://twprogrammers.com/mail-server-on-ubuntu) for those who run across this topic that can't seem to find a complete tutorial.

---

