---
title: "Ubuntu + MailWatch"
date: 2007-08-23
forum: Server Platforms
---

### Post by insanity2k7 on 2007-08-23
Long story made short...  I'm a Linux novice but I'm smart enough to realize how incredibe Ubuntu is.  Out of nowhere I start getting pummelled with spam so I decide to build a spam/virus filtering box.  SpamAssassin/MailScanner is the only free solution for this problem I'm aware of, requires Linux -- BAM -- Ubuntu server.  And it runs GREAT!  Anyways, after I make my decision, I locate this site:

[http://www.howtoforge.com/postfix_antispam_mailscanner_clamav_ubuntu](http://www.howtoforge.com/postfix_antispam_mailscanner_clamav_ubuntu)

I get my server running and everything is beautiful, so now it's time to move onto details.  I happen to have a Linux messiah for a friend, but I don't want to abuse him with too many questions...  asked him what to use to releasing e-mails from the quarantine area.  He immediately recommended MailWatch and provided a link for downloading the software and the installation procedures.  After looking around on their site I agreed it was a great solution.  Here's the install instructions I followed:

[http://mailwatch.sourceforge.net/doku.php?id=mailwatch:documentation:install](http://mailwatch.sourceforge.net/doku.php?id=mailwatch:documentation:install)

HOWEVER...

Having followed these instructions word for word and making educated guesses when exact information was not provided, MailWatch didn't work.  My understanding is that MailWatch is just an interface to make managing a spam filtering box easier which is great...  That having been said I do not believe I have destroyed my incoming e-mail server.  When I try to open [http://server/mailscanner](http://server/mailscanner) I get this error:

Fatal error: Call to undefined function mysql_escape_string() in /var/www/mailscanner/functions.php on line 539

For S&G's I commented out line 539...  then I got a similar error for line 508.

So I'm left with a two-part question...  First, is there an alternative/CLI way to release messages from the quarantine?
-OR-
Any ideas for what I've done wrong, or a link to a better how-to?

I looked around and couldn't find anything to help me, so I hope this isn't a dupe.  Regardless thanks in advance for your help!

---

### Post by insanity2k7 on 2007-08-24
Is there additional information that I could provide that would help, or is this a legitimate stumper?

---

### Post by Blairboy on 2007-08-24
Well, I used/adapted flurdy's guide years ago.  I used dovecot for imap and altered some settings, but I found it to be a pretty intensive howto.  It includes having spamassassin looped through amavis, so it's pretty powerful.

---

### Post by insanity2k7 on 2007-08-27
I got a sorta kinda answer to my problem and I wanted to post it up here for anyone else in my shoes...  I never did figure out yet what the problem with MailWatch is, but I finally figured out how to manually release a message from quarantine on the commandline:

sendmail -t -i < /var/spool/MailScanner/quarantine/<DATE>/spam/<MESSAGEID>

Replace <DATE> with something like: 20070827
Replace <MESSAGEID> with something like: 56CBF8FEED.CD7F8

Then you're in business.  To get the Message ID you want, you have to make sure the actions are to STORE and NOTIFY in your MailScanner.conf file.  For example:

Spam Actions = store notify

It'll send your end users the Message ID and a very nice e-mail letting them know what's up and what to tell you when they call you.  Hopefully this helps someone else as this has seriously been driving me insane for days.  With getting MailWatch working though...  still open to any suggestions.

---

