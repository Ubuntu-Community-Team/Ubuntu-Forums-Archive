---
title: "Issue with MailScanner in Ubuntu 13.10"
date: 2014-03-18
forum: Server Platforms
---

### Post by Robin_Wilson on 2014-03-18
[FONT=Calibri,sans-serif][SIZE=2]Hello[/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2] [/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2]I’m hoping someone can tell me what I have done wrong.[/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2] [/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2]Firstly I set up postfix and dovecot and got these working correctly and also integrated the system with postgreSQL so user accounts are stored in the database.[/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2] [/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2]I then downloaded MailScanner:[/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][FONT=Courier New][COLOR=red]**mkdir /downloads/**[/COLOR][/FONT][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][FONT=Courier New][COLOR=red]**cd /downloads/**[/COLOR][/FONT][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][FONT=Courier New][COLOR=red]**wget **[/COLOR][/FONT][[FONT=Courier New]**[COLOR=red]http://mailscanner.info/files/4/tar/MailScanner-install-4.84.6-1.tar.gz[/COLOR]**[/FONT]]("http://mailscanner.info/files/4/tar/MailScanner-install-4.84.6-1.tar.gz")[/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][FONT=Courier New][COLOR=red]**tar xzvf MailScanner-install-4.84.6-1.tar.gz**[/COLOR][/FONT][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][FONT=Courier New][COLOR=red]**cd MailScanner-install-4.84.6-1**[/COLOR][/FONT][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][FONT=Courier New][COLOR=red]**sudo bash install.sh**[/COLOR][/FONT][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2] [/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2]The script then ran through and installed but I realised I should have installed SpamAssasin first so I installed this afterwards and then re-ran install.sh[/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2] [/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2]Both times I ran install.sh it seemed to run through ok and I did not see any errors.[/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2] [/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2]After install I noticed that it was throwing up a lot of errors about folders being missing so I created them:[/SIZE][/FONT]
[FONT=Times New Roman,serif][SIZE=3][FONT=Courier New][SIZE=2][COLOR=red]**mkdir /var/spool/MailScanner/incoming/Locks**[/COLOR][/SIZE][/FONT][/SIZE][/FONT]
[FONT=Times New Roman,serif][SIZE=3][FONT=Courier New][SIZE=2][COLOR=red]**mkdir /var/spool/mqueue**[/COLOR][/SIZE][/FONT][/SIZE][/FONT]
[FONT=Times New Roman,serif][SIZE=3][FONT=Courier New][SIZE=2][COLOR=red]**sudo nano /var/spool/mqueue.in**[/COLOR][/SIZE][/FONT][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2] [/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2]After installing SpamAssasin I wasn’t sure if I needed to enable it by editing the config:[/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][FONT=Courier New][COLOR=red]**sudo nano /etc/default/spamassassin**[/COLOR][/FONT][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][COLOR=black] [/COLOR][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][COLOR=black]I tried turning it on but I’m not sure if this is handled separately in MailScanner so not sure if turning it on here is correct.[/COLOR][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][COLOR=black] [/COLOR][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][COLOR=black]Then I edited the MailScanner conf file as it seemed to be set for Emsim by default.[/COLOR][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][COLOR=black] [/COLOR][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][COLOR=black]Mail still didn’t seem to be getting scanned but then I read I needed to alter the postfix config to move mail to the hold location for MailScanner to check it:[/COLOR][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][FONT=Courier New][COLOR=red]**header_checks = regexp:/etc/postfix/header_checks**[/COLOR][/FONT][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][FONT=Calibri,sans-serif][COLOR=black]Then[/COLOR][/FONT][FONT=Courier New][COLOR=black] [/COLOR][/FONT][FONT=Courier New][COLOR=red]**sudo nano /etc/postfix/header_checks**[/COLOR][/FONT][FONT=Courier New][COLOR=red] [/COLOR][/FONT][FONT=Calibri,sans-serif][COLOR=black]and added[/COLOR][/FONT][FONT=Courier New][COLOR=black] [/COLOR][/FONT][FONT=Courier New][COLOR=red]**/^Received:/ HOLD**[/COLOR][/FONT][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][FONT=Courier New][SIZE=2][COLOR=black] [/COLOR][/SIZE][/FONT][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][FONT=Calibri,sans-serif][COLOR=black]But since redirecting it the mail is just held in the queue and nothing happens.[/COLOR][/FONT][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][FONT=Calibri,sans-serif][COLOR=black] [/COLOR][/FONT][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][FONT=Calibri,sans-serif][COLOR=black]I feel I have tried everything I can think of now and am a bit lost.[/COLOR][/FONT][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][FONT=Calibri,sans-serif][COLOR=black] [/COLOR][/FONT][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][FONT=Calibri,sans-serif][COLOR=black]Also the script in [/COLOR][/FONT][FONT=Courier New][COLOR=red]**/etc/init.d**[/COLOR][/FONT][FONT=Calibri,sans-serif][COLOR=red] [/COLOR][/FONT][FONT=Calibri,sans-serif][COLOR=black]seems to be called [/COLOR][/FONT][FONT=Courier New][COLOR=red]**mailscanner.dpkg-new **[/COLOR][/FONT][FONT=Calibri,sans-serif][COLOR=black]rather than just [/COLOR][/FONT][FONT=Courier New][COLOR=red]**mailscanner**[/COLOR][/FONT][FONT=Calibri,sans-serif][COLOR=black]. I tried to wget the Debian init.d script and save it as mailscanner but I’m really not sure if this is correct.[/COLOR][/FONT][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][FONT=Calibri,sans-serif][COLOR=black] [/COLOR][/FONT][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][FONT=Courier New][COLOR=red]**ps aux | grep MailScanner**[/COLOR][/FONT][FONT=Calibri,sans-serif][COLOR=red] [/COLOR][/FONT][FONT=Calibri,sans-serif][COLOR=black]shows all the processes as defunct as well[/COLOR][/FONT][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][FONT=Calibri,sans-serif][COLOR=black] [/COLOR][/FONT][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][FONT=Calibri,sans-serif][COLOR=black]I would appreciate any help to get this working.[/COLOR][/FONT][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][FONT=Calibri,sans-serif][COLOR=black] [/COLOR][/FONT][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][FONT=Calibri,sans-serif][COLOR=black]Thanks[/COLOR][/FONT][/SIZE][/FONT]
[FONT=Calibri,sans-serif][SIZE=2][FONT=Calibri,sans-serif][COLOR=black]Robin[/COLOR][/FONT][/SIZE][/FONT]

---

### Post by SeijiSensei on 2014-03-18
As a long-time MailScanner user, I have found it much easier to install on RedHat-flavored distros than on Debian-flavored ones like Ubuntu.  If you're building a server from scratch,, I suggest giving [CentOS]("http://www.centos.org/") a try and installing MailScanner on that.  A good starting point might be to install [VirtualBox]("http://www.virtualbox.org/") and then install CentOS 6.5 into that for development and testing before deployment into production.  Use the bundle Julian provides [here](http://www.mailscanner.info/files/4/rpm/MailScanner-4.84.6-1.rpm.tar.gz).

Are you also running ClamAV for virus scanning?  On busy servers, I recommend using clamd rather than invoking clamscan or using clamavmodule.  Using the clamd daemon improved throughput considerably for us.

---

### Post by Robin_Wilson on 2014-05-01
> **SeijiSensei said:**
> As a long-time MailScanner user, I have found it much easier to install on RedHat-flavored distros than on Debian-flavored ones like Ubuntu.  If you're building a server from scratch,, I suggest giving [CentOS]("http://www.centos.org/") a try and installing MailScanner on that.  A good starting point might be to install [VirtualBox]("http://www.virtualbox.org/") and then install CentOS 6.5 into that for development and testing before deployment into production.  Use the bundle Julian provides [here]("http://www.mailscanner.info/files/4/rpm/MailScanner-4.84.6-1.rpm.tar.gz").

Are you also running ClamAV for virus scanning?  On busy servers, I recommend using clamd rather than invoking clamscan or using clamavmodule.  Using the clamd daemon improved throughput considerably for us.

Hello SeijiSensei

Thanks a lot for the information. Sorry for not replying sooner but I have only just seen your response.

I couldn't get this to work on Ubuntu after starting from scratch 5 times. I keep hitting dependency issues now which I can't seem to resolve so I will give CentOs a go as you have suggested.
I am planning to set up the server to scan email for an Exchange server and also use the server to host some websites. The email scanner could get quite busy although there are only about 50 users at most.

I managed to get the postfix/dovecot email server set up ok and the hosting.
I'm no expert with Linux as I mostly administer Windows servers so appreciate the advice.

Thanks
Robin

---

### Post by SeijiSensei on 2014-05-01
I manage a MailScanner installation on a CentOS gateway in front of an Exchange server.  We use ClamAV and SpamAssassin, plus some restrictions at the SMTP level.  The client never exchanges mail with people in foreign countries, so we block most connections from country-code domains except .us and .ca.  This cuts down a lot of spam from the usual suspects like .cn, .vn, .th, .br, etc.

This client is a healthcare provider with about 250 employees.  Yesterday we scanned about 3,000 inbound messages and 1,000 outbound ones.  We use the "MCP" facility in MailScanner to intercept outbound messages that may violate the US "HIPAA" rules about the privacy of patient information. The same box also runs an outbound Squid proxy that uses SquidClamAV to scan every object downloaded over the web.  This machine rarely breaks a sweat, but it's a dual-Xeon with 8 GB of memory.

---

### Post by Robin_Wilson on 2014-05-04
Hello SeijiSensei

Thanks for the reply

What you have set up sounds impressive. I've actually got to look at alternatives for Microsoft TMG for web filtering too but that is a future project!

I have tried CentOS as you suggested and it does seem like the way I need to go but after spending hours on it I'm struggling to get everything working.
I have been following a combination of different tutorials as I can't find one that goes through the whole process on this OS and due to differences in setups between the guides I think this is why I am getting problems.

What I need is a mail server that handles different virtual domains and holds mailbox details in a MySQL database and scans all the email for viruses/spam.
Emails to some domains need to be delivered internally on the same server whilst others need to be forwarded on to the Exchange server.

Are you able to recommend a good guide for setting this up?

Thanks
Robin

---

### Post by SeijiSensei on 2014-05-04
Well I'm probably not the best person for that if you want to use Postfix and a database.  I still use **sendmail**, and I just store peoples' messages in mbox format in /var/spool/mail.  I've never seen much value in database backends for email unless you have hundreds and hundreds of users and don't want to give them Unix accounts.  At the same client where the MailScanner gateway is running, I used to maintain a mail server with a couple hundred accounts.  (They now use Exchange.)  We just created Linux users with "/bin/false" as their default shell, so they could only log in to receive mail, and ran IMAP with dovecot for delivery.

Sendmail handles virtual domains just fine.  There's a file usually called virtusertable which maps domains to destinations.  Here's an example:
```

@example.com            bobby
user1@domain.com        harriet
user2@domain.com        bill@gmail.com
@domain.com             priscilla

```
All mail for "example.com" is delivered to bobby.  For domain.com, mail for user1 goes to harriet,user2's mail is forwarded to bill's gmail account, and all other mail for domain.com is sent to priscilla. The targets can be aliases in /etc/aliases as well, so mail can be directed to lists of users.

Forwarding a whole domain or subdomain is the responsibility of the "mailertable" database in sendmail.  You set up routings like this:
```

exchange.example.com      relay:[ip.of.exch.server]

```
Now mail for that subdomain is sent to the Exchange server, while all other mail for example.com is delivered locally.  Mailertable can also be used to deliver an entire domain or subdomain to a specific local address like this:
```

hr.example.com      local:hr

```
This delivers the HR department's mail to the local hr mailbox on the server. The targets in the mailertable database consist of a mailer ("relay," "local," etc.) and a destination.

If you're curious, here's a longer description of using [sendmail for virtual hosting]("http://www.sendmail.com/sm/open_source/tips/virtual_hosting/").  Skip the stuff about how to compile and configure sendmail to support these features.  All major distributions like CentOS include those by default.

---

### Post by Robin_Wilson on 2014-05-05
Hello SeijiSensei

Thanks again for all the useful information.

I don't mind what I use really as long as I can get it working.
I thought the database might be good as it would allow me to possibly write a PHP frontend allowing users to update their password and possibly add new accounts.

I did manage to get postfix working on CentOs but then had trouble getting further so went back to Ubuntu.

I have now managed to get a mail server set up on Ubuntu which uses spamassassin and clamav. Do you think I would notice much difference between this and mailscanner? I also added the reject_rbl_client settings for spamhous and spamcop as well.

I have now set up email relaying to the Exchange server for one domain using transport_maps in postfix which seems a bit hit and miss so I'm not really sure yet where it is getting dropped or why.
I wasn't really sure if I needed to modify the frontend transport as the standard one allows anonymous connections on port 25 but it seems I need to add another and set transport layer security and externally secured and tick the box against exchange servers.
Is that needed? Also I'm thinking if Exchange checks the sending server it is going to detect that it is different and cause it to rank higher as spam?

Also the spam and clamav headers are removed from the email when it comes into Exchange so either the Exchange server has removed them or the relayed email is not passing through the filters. Do you know of a way to check this?
I will try sendmail next if this won't work. Would you recommend this over postfix?

Thanks
Robin

---

### Post by SeijiSensei on 2014-05-06
> **Robin_Wilson said:**
> I have now managed to get a mail server set up on Ubuntu which uses spamassassin and clamav. Do you think I would notice much difference between this and mailscanner? I also added the reject_rbl_client settings for spamhous and spamcop as well.
MailScanner has some additional features like rejecting mail with particular types of attachments and other niceties, but dirty attachments should probably trip clamav in the setup you have.

I don't use reject rules for RBLs because of the possibility of false positives.  I prefer to let SpamAssassin handle all those things.  You can see how SA scores various blacklists by looking in /usr/share/spamassassin/50_scores.cf.  Usually a message that hits a blacklist will have plenty of other spammy features so it gets tagged anyway, but rejecting messages at the doorstop is tricky unless you have some experience with spam.  Here's a sample that tripped on Spamcop:
```

BAYES_99 3.50, BAYES_999 5.00, CK_HELO_DYNAMIC_SPLIT_IP 1.50, HELO_DYNAMIC_IPADDR2 3.61, 
HTML_MESSAGE 0.00, MIME_HTML_ONLY 0.72, **RCVD_IN_BL_SPAMCOP_NET 1.35**, 
RCVD_IN_BRBL_LASTEXT 1.45, RCVD_IN_PSBL 2.70, RCVD_IN_RP_RNBL 1.31, 
RCVD_IN_XBL 0.38, RDNS_DYNAMIC 0.98, URIBL_BLACK 1.70, URIBL_DBL_SPAM 2.50, 
URIBL_JP_SURBL 1.25, URIBL_SBL 1.62, URIBL_SC_SURBL 0.57, URIBL_WS_SURBL 1.61, 
URI_RU 10.00

```
URI_RU is a custom rule I wrote that matches embedded URLs that point to Russian domains.  The rest of the scores come from SpamAssassin.  Even without the extra ten SpamAssassin points for URI_RU, the message would score over 31 SA points.  I start tagging at four and quarantine anything that scores over eight.

> I have now set up email relaying to the Exchange server for one domain using transport_maps in postfix which seems a bit hit and miss so I'm not really sure yet where it is getting dropped or why.
Yes, transport_maps are the mechanism to handle relaying just as mailertable does in sendmail.  I would think you'd need a map to tell Postfix which mail to forward to Exchange.  If all the other mail is delivered locally, then I'm not sure why you'd need any others.

> Also I'm thinking if Exchange checks the sending server it is going to detect that it is different and cause it to rank higher as spam?
If all the spam scanning is done on the Linux box, I don't see how Exchange would know whether something is spam or not.  I don't know Exchange, but if it does have some methods for checking inbound mail, I would think you should be able to tell it simply to trust the Linux box.

> Also the spam and clamav headers are removed from the email when it comes into Exchange so either the Exchange server has removed them or the relayed email is not passing through the filters. Do you know of a way to check this?
I'd start with looking at /var/log/mail.log.

I use sendmail because I've used it for fifteen or more years and know how to make it do what I need.  Most systems these days ship with Postfix, so I'd say that's a better long-term investment of your time.  I'm running Postfix on a backup MX server, but it doesn't have much to do other than accept plausibly legitimate messages and forward them on to the MailScanner box.  Most mail to backup MX servers is spam, so I have a few simple entries in helo_access and sender_access to block obvious forgeries and most two-letter country-code domains for reasons I explained above. Both files look pretty similar; here is sender_access:
```

# no mail from outsiders claiming to be us
/\.example\.com$/       REJECT

# no two-letter country-code domains except us/ca
/\.us$/                 OK
/\.ca$/                 OK
/\.[a-z][a-z]$/         REJECT US senders only

```
These use regular expressions and reject messages whose From matches [email]someone@example.com[/email] or [email]someone@somewhere.??[/email].

---

### Post by Robin_Wilson on 2014-05-07
Hello SeijiSensei and again thanks for all the information. It is really useful.

I think I will follow your advice and remove the RBL lines as it sounds like it might block stuff I don't want blocking.

Exchange does have its own spam filtering as well but it is not very good and just seems to let everything through. I was using the Forefront Filtering product but that has been discontinued now. I will probably disable this once I get this new server working properly.

After doing some more reading I have worked out that mail that is relayed via transport maps skips the content filtering as this happens after any relaying is processed so whilst the messages are successfully sent onto the Exchange server they are not being scanned at all. The fix seems to be to add the content filtering in the main.cf file instead but whatever change I make it seems to end up stuck bouncing backwards and forwards between the two content filters and then fails with a NDR of too many hops.
I have posted a question on this here: [http://ubuntuforums.org/showthread.php?t=2222594&p=13016351#post13016351](http://ubuntuforums.org/showthread.php?t=2222594&p=13016351#post13016351)

Once this is resolved I think the server will be doing what I need it to as long as there is a way around the issue.
If it supports regular expressions that should allow for some pretty complex rules so it will be good even though I probably won't need that functionality, at least to start with.

Thanks
Robin

---

### Post by SeijiSensei on 2014-05-09
That's the nice thing about MailScanner -- it runs two instances of sendmail or Postfix.  The first accepts inbound messages before scanning.  The second delivers the messages after scanning. That makes it easy to put MailScanner between the Internet and a network mail server like Exchange.

You could run a second instance of Postfix on a custom port.  Have mail destined for the Exchange server relayed to this second Postfix instance for scanning, with the Exchange server as its relay host.  Just an idea.

SpamAssassin uses Perl regular expressions pretty much throughout.  A rule looks like this:
```

header SAMPLE_RULE    Subject =~ /this is a.*sample rule\.$/
score SAMPLE_RULE     5

```
You can also search the body or URIs embedded in the body.  There are probably other keys, but those are the ones I use.

---

### Post by Robin_Wilson on 2014-05-11
Thanks for the info.

After spending a while trying a combination of different settings I have now managed to get this working.

I needed to specify a content filter in main.cf which forces all mail through the filter (in this case it is ClamAV) and then on the listener which injects the mail back into Postfix I put the SpamAssasin filter on there and this seems to force all mail through the content filters which is working well.

I did find that I also had to add the domains and users into the virtual_users and virtual_domains tables in the database otherwise it rejects the domain as relay access denied and rejects the users saying the user was not found. I suppose this is required as I wouldn't want to allow the server to relay for anything.

So I think everything is sorted now.
It may not be the best way but at least it seems to work.

Thanks
Robin

---

