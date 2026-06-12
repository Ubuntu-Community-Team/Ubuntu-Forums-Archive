---
title: "Mail Server to Collect from POP3 and place in IMAP"
date: 2007-03-28
forum: Server Platforms
---

### Post by Catsworth on 2007-03-28
Hi Guys,

Just a quickie (hopefully).....

Is it possible to:

a) set up a server, or a service running on a server, that will collect emails from a number of different POP3 accounts

b) have that server sort those emails, placing them into folders according to either a pre-defined ruleset or according to which POP3 account they were downloaded from

c) have these folders available across the network, or remotely connecting to the network via SHH or some secure/encrypted connection, to my users.  

d) restrict access to the folders to designated account holders only


It's important that, when the users access them, the emails aren't downloaded to the local machine - this means that users can access their email from whatever box they want to.  Am I right in thinking that these emails need to be stored in IMAP folders, or is that a red herring?

Would appreciate any thoughts on this one.

Thanks.

---

### Post by tonym on 2007-03-28
To collect from the POP3 accounts - fetchmail

To deliver to folders - you need an MTA - I use EXIM but there are others.

To make mails available via IMAP - I use Courier IMAP but Dovecot seems popular.

Regards

Tony.

---

### Post by Catsworth on 2007-03-28
Thanks Tony, I'll take a look into those.

---

### Post by Morkalin on 2007-05-19
A few years ago when I was setting up a mail server I found that fetchmail had some limitations regarding sorting mail or something to that effect, and an alternative which I found to be very good is getmail:

[http://pyropus.ca/software/getmail/](http://pyropus.ca/software/getmail/)

Cheers,
Wayne

---

### Post by BroadArrow on 2007-07-14
> **Catsworth said:**
> Thanks Tony, I'll take a look into those.

Did you have any luck?

I think I'm wanting to do something similar in that I already have a IMAP mail server (Dovecot) operating on my home LAN and want the server to also be able to download mail from some remote POP3 mailboxes to some of the IMAP accounts -- but haven't found a solution yet.

---

### Post by Mr. C. on 2007-07-14
> **tonym said:**
> To deliver to folders - you need an MTA 

Almost, but not quite.  It is an MDA (mail delivery agent) that delivers mail to the storage location.  An MTA relays mail between servers, but often acts as an MDA as well.

Fetchmail can deliver to an MTA or MDA (eg. procmail, sendmail).

Catsworth, don't provide SSH access to what are essentially your user's mail folder.  Use IMAP.

Do you want to prevent user's from deleting mail on the IMAP server (it sounds like you might, since you don't want them downloading the message).  Or are you just trying to provide easy, multi-machine email for them, and they can delete as they see fit?

MrC

---

### Post by BroadArrow on 2007-07-14
Mr C: I know you were replying to the original poster but I'll be cheeky and post a couple of follow-up questions to you as I'm a bit confused about the MTA/MDA distinction.

1. What packages would be needed to transfer mail from the remote POP server and then deliver it to the local IMAP server (assuming something like Dovecot was already installed)?

2. What packages would be needed to relay any messages sent to a local SMTP server (such as Postfix) to a remote SMTP server?

OK, a third question as well which might answer both of the above: is there a HOWTO explaining how to set up the above? I suspect there are more home users with multiple POP and SMTP accounts wanting to set up a local server clearing and sending mail for them but using the same protocols a mail client would.

---

### Post by Mr. C. on 2007-07-14
No problem.  Let's see if I can clarify for you.

An MTA's job is to relay mail; the MDA's job is to deliver it to a local store, as I mentioned earlier.  Because these roles are often combined within a single software "package" (eg. postfix, exim, Sendmail, etc), it is difficult to see the distinction.  However, it becomes more clear when one thinks in terms of network services.  An MTA typically sits listening on a network port such as TCP port 25, waiting to receive a connection for mail delivery from another MTA or MUA.  It also typically manages a queue of mail messages.  And today's primary standard protocol for email on the Internet is SMTP.

Contrast that with an MDA, that may be a local program called upon by the MTA for local delivery (such as postfix's local delivery program, or maildrop).  An MDA's job is to place the mail into the appropriate store, such as a MySQL database, a Maildir file, or an mbox file.  They do not manage a queue, nor send error replies back to the original MTA.

Fetchmail is an amalgam of programs - it can retrieve email via POP, IMAP, ETRN, etc.  It can then either deliver to an MTA, or to an MDA.

Mail can be retrieved from a POP server either by an MUA (for final deposit into a user's local inbox, generally removing it from the server's storage), or by a program such as Fetchmail.

An IMAP server does not listen for incoming mail connections for mail relay - rather, it provides access to already delivered email.  One would not use fetchmail to send mail to IMAP.  Rather, fetchmail can send to a local MTA, or to an MDA such as procmail.  How you configure these, and which solution you choose very much depends on your needs.  If you are running a mail server anyway, you might just use fetchmail to relay to your local MTA.

Select an MTA that meets your needs if you want to relay mail.  Your choices are: Sendmail, Postfix, Exim, or even the trivial ssmtp or mini_sendmail.  It depends on your needs and goals.

Select an MDA that is appropriate for your needs as well.  If you've installed postfix, you can simply use the postfix local MDA.

I do not recommend other peoples' "cookbook" approaches in general, as they fail to teach users *how* and *why* things work.  Unfortunately, internet email is far too complex for such trivial HowTo's.  It is best to a) scope your needs, b) determine the available solutions, and c) begin one step at a time implementing and configuring the software based upon your understanding and requirements, and d) continue to refine your knowledge about how to further improve your system to best meet your needs.  If all this is too much trouble, or too difficult, it is best to use mail services such as gmail, hotmail, AoL, etc.

MrC

---

### Post by doogy2004 on 2007-09-02
does someone know where there is a good how to on how to get this setup and working.

Thanks

---

### Post by Mr. C. on 2007-09-02
Every situation is somewhat unique.  Describe what you mean by "this".

MrC

---

### Post by doogy2004 on 2007-09-02
the entire setup, from start to finish.

download email via pop from:
comcast, verizon, gmail, etc.

access the email via imap client.

---

### Post by HermanAB on 2007-09-02
Hmm, you need fetchmail, procmail, postfix, dovecot, amavisd-new, spamassassin, clamav, dcc and razor.  

As mentioned above, configuring a mail server is a difficult problem.  You need to go to the web sites of all those projects and start reading, then bring each part up one by one.  Probably the best howto guides are on the postfix web site, but you'll find no single howto guide will describe what you need to do.  You need some ideas from one and some from another.  BTW, the simple mail program mutt and the general purpose debugger telnet are good tools to get this kind of thing to work.

Another option, which is usually much easier to set up, is Citadel.

---

### Post by doogy2004 on 2007-09-03
Citadel looks very interesting and was easy to setup using the virtual appliance.

here is my current status:
I use outlook to download my emails via pop from verizon, comcast, gmail, and others.

I want to be able to use my server to (GOAL):
login with outlook (to my server) via imap, to retrieve and send email, from all of my accounts (e.g. verizon, comcast, gmail, etc.)  A web interface would be nice for when i'm not on my laptop.

how can I get citadel to accomplish my goal?

Thanks

---

### Post by wislon on 2007-09-06
Here's a quick "HOWTO", it covers only the basics, but it was enough to get us going. It's by no means the Final Solution, but I hope you can use it as a base to work from. 

I just helped my dad do this, the idea was to collect email from 2 separate POP3 accounts and have them delivered into separate IMAP  accounts on a machine accessible from more than one workstation. We set it up using Feisty, but I don't think it would be that much different for other versions. This machine is NOT facing the internet, and it's behind a firewall.

He had nothing email server related installed, so we did this:

Created two new user accounts on the linux box, we'll call them "acc1" and "acc2" with passwords "pass1" and "pass2" respectively. These were to be local users to "hold" the IMAP mail accounts. I am sure it must be possible to do it with just one user, but we're both still learning this, so we went with what we knew would work.

```

sudo adduser acc1
sudo adduser acc2

```

then we installed dovecot (I believe there's others like courier, but I've seen dovecot get some good reviews and it's easy to work with)

```
sudo aptitude install dovecot
```

(we accepted some dependencies with this, it wanted to install some pop3 stuff as well, we told it to just go ahead and do what it needed to do)

It initially bombed out when we tried to start it, with an error about no protocols selected, so we had to edit the dovecot config file:

```
sudo nano /etc/dovecot/dovecot.conf
```

we basically left everything as a default

but set the protocols line to read:

```
protocols = imap pop3
```

we fiddled with the log timestamping format, but I can't remember if we kept it or not:

```
log_timestamp = "%Y-%m-%d %H:%M:%S "
```

and I'm pretty sure we set

```
disable_plaintext_auth = no
```

and that was about it. we restarted the dovecot service:

```
sudo /etc/init.d/dovecot restart
```

oops! an error about pop3 not being installed:

**'dovecotError: Can't use mail executable /usr/lib/dovecot/pop3: No such file or directory'**

must have missed that one. Installing:

```

sudo aptitude install pop3
sudo /etc/init.d/dovecot restart

```

and it didn't complain any more. 

A quick 

```

telnet localhost 110
user acc1
pass pass1

```

gave us access to the mailbox for account "acc1", so everything appears to be working thus far. Typed "quit<enter>" to get out of it, and back to the command prompt.

All well and good, now we needed to actually collect the email from the POP3 accounts.

we installed fetchmail

```
sudo aptitude install fetchmail
```

and when that was done, spent an inordinate amount of time mucking around on this forum (thanks guys, in general!), inside the man pages and playing with the command line.

Eventually I came up with this:

created a **.fetchmailrc** file in the home folder of the regular user of that PC (we'll call him "bob", that's who's usually logged in)

```
sudo nano /home/bob/.fetchmailrc
```

and added the following lines:

```

set no bouncemail
set logfile fetchmail.log
set idfile fetchmail_uidls.log
poll mail.server.one with proto pop3 service 110 uidl username "mail_username" with password "your_password_here" is "acc1" here keep
poll mail.server.two with proto pop3 service 110 uidl username "username_here" with password "password" is "acc2" here keep

```

The neat thing about this config is that it can be written almost as natural language, as it's parsed intelligently just for the keywords and parameters. Just be careful, you could be going around in circles if you do things like putting the username before the server to poll, stuff like that. The errors are actually pretty helpful, and the lower sections of the man pages dealing with the .fetchmailrc (as opposed to command line options are pretty good with examples too). I made sure I put "**keep**" in at the end of each line, so that I didn't clobber any emails accidentally

Saved it, exited it and tried to confirm the configuration with 

```
fetchmail --configdump
```

And got an error about permissions, something like "it's not going to work, for security reasons the permissions on .fetchmailrc need to be set to 0710"

Ok, fine:

```

cd /home/bob
chmod 0710 .fetchmailrc

```

pretty much did the trick. Tried again

```
fetchmail --configdump
```

and got a whole lot of info back, looks something like an array of lists parameters. I came to learn that as long as you got this info, everything was correctly formatted.

Good stuff, ran fetchmail telling it to just check the mailboxes and be verbose about it, but not download anything 

fetchmail -cv

Cool! Got a running commentary on the contents of the two mailboxes and what it was doing.

Unfortunately fetchmail won't just drop the emails into the separate accounts. Ok, so we haven't set up a mail server (MTA) or delivery method (MDA) yet so it would have no way to get the email to the different accounts yet either. Enter  **postfix**

We decided to go with the most barebones setup of postfix at this point, we're not going to use this machine as a proper mailserver yet, coz I've run up against this thing before and it can get quite messy. It's too complex to go into for the purposes of this demo.

```
sudo aptitude install postfix
```

accepted all dependencies and so on, and let it do its thing.

When it was finished downloading, it ran a little curses based installer asking us what we wanted to do. We selected the "local only" option, and it went off and did more stuff. 

Tried to start postfix and it bombed out with an error or two about various things not being set. Fair enough, let's go fix the config:

```
sudo nano /etc/postfix/main.cf
```

and set the following options:

```

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 2h

myhostname = bobcat
mydomain = bobcat
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost.localdomain, localhost
mynetworks = 127.0.0.0/8, 192.168.0.0/24
mailbox_size_limit = 0
recipient_delimiter = +
home_mailbox = Maildir/

#allow anonymous and plaintext authentication
smtp_sasl_security_options =

inet_protocols = ipv4
smtp_destination_concurrency_limit = 5



```

I am sure there are other options for securing it better, and getting it to help you wash the dishes, but the above settings are all we needed in that file.

Saved and closed nano, tried to restart postfix. 

```
sudo /etc/init.d/postifx restart
```

Got an error about a missing file called /etc/mailname. oops!

```
sudo echo bobcat >> /etc/mailname
```

tried again

```
sudo /etc/init.d/postifx restart
```

it started, with no errors!

** *dance.of.joy***

did a quick test:

```
mail acc1<enter>

some arbitrary subject
<enter>
some arbitrary data here terminated
with a dot on a line by itself, like so:
.
cc:<enter>

```

and a quick 

```
tail /var/log/mail.log
```

showed us a bunch of stuff, culminating in something along the lines of "delivered to maildir"

Fantastic, we're almost done.

just to be sure that fetchmail doesn't bounce emails for whom it cannot find a recipient based on the username you gave it (for instance if you were BCC'd in an email) back to the sender, we need to set up a default postmaster on this machine, and point it to an existing user, so that the mails go there instead. We'll make the postmaster "acc1".

```
sudo nano /etc/aliases
```

and filled in

```
root:   bob
postmaster: acc1

```

saved and closed, and ran the "newaliases" command to rebuild the little database that postfix uses for distributing mail. Restarted postfix

```

sudo newaliases
sudo /etc/init.d/postfix restart

```

Great, so it looks like we're all set:

Now that postfix is working, we can use sendmail as the message delivery agent by means of a command-line. The man pages for fetchmail sugggested using 

```
mda "/usr/sbin/sendmail -i -f %F %T"
```

in the .fetchmailrc, so we'll go back and insert it there. This will allow fetchmail to collect any messages from a particular POP3 server for a particular user and ask sendmail to do the delivery of each message into the local mailbox. 

%F is the "from" email address, and %T is the "to". This means that the correct email addresses end up in the right fields so that when you hit reply/forward from inside your mail client, the correct "from" field appears in the outgoing mail (e.g. "acc1@bobcat" on an outgoing mail probably wouldn't be accepted by your average ISP)

back into the .fetchmailrc

```
sudo nano /etc/bob/.fetchmailrc
```

and added it at the end

```

set no bouncemail
set logfile fetchmail.log
set idfile fetchmail_uidls.log
poll mail.server.one with proto pop3 service 110 uidl username "mail_username" with password "your_password_here" is "acc1" here keep
poll mail.server.two with proto pop3 service 110 uidl username "username_here" with password "password" is "acc2" here keep
and wants mda "/usr/sbin/sendmail -i -f %F %T"

```

Closed and saved. Did the fetchmail --configdump to ensure we didn't break anything.

Ok, after taking a deep breath, and crossing the fingers, we ran it

```
fetchmail
```

...and was promptly greeted by a LOT of information about what it was doing, where it was going, what it was downloading, quite overwhelming! 

OK, so it's obviously working. In the meantime I'd also set up a test IMAP account in an email client, and it was starting to squeak about messages arriving in the inbox of the "acc1" user. Perfect. I let it run a little longer, it finished with the first mail server and moved onto the second. I was watching the mail delivery log in another terminal window

```
tail -f /var/log/mail.log
```

And I could see the MDA delivering the messages into the "acc2" account.

Almost done!

Obviously you don't want to be running the fetchmail manually every few minutes, so luckily it has a "daemon" mode which will background it immediately and get it to check at intervals you specify. However, it doesn't dump its output to the screen, so you won't see it, however you might want to know what it is up to by monitoring the system log.

back into the .fetchmailrc (hopefully for the last time)

```
sudo nano /etc/bob/.fetchmailrc
```

and added some stuff at the top:

```

set daemon 300
set syslog
set no bouncemail
set logfile fetchmail.log
set idfile fetchmail_uidls.log
poll mail.server.one with proto pop3 service 110 timeout 120 uidl username "mail_username" with password "your_password_here" is "acc1" here keep
poll mail.server.two with proto pop3 service 110 timeout 120 uidl username "username_here" with password "password" is "acc2" here keep
and wants mda "/usr/sbin/sendmail -i -f %F %T"

```

Also added some timeout values for the servers, just in case (it defaults to 300 seconds, which is a bit long for my taste). I left the "keep" in as well, for now.

Ran fetchmail again, and it immediately dropped into the background, and the lights on the router went bananas again as it started pulling down the mail. A quick check at /var/log/mail.log confirmed it was busy collecting emails.

And that was that. The only thing left to do was add the "fetchmail" command to the session startup, when bob logs in, and it happily backgrounded itself and continues to run. Of course this could probably be run as a cron job as well, without the daemon mode, but that's just one variation on this theme.

I hope this helps somebody. It's very basic, doesn't do any spam blocking or antivirus checking etc., but I am quite sure this can be built on to include this.

Good luck with your efforts! :)

wislon

---

