---
title: "Postfix + Postgrey on 7.10?"
date: 2007-10-25
forum: Server Platforms
---

### Post by whit on 2007-10-25
I've got postfix running on 7.10, and am trying to run postgrey (greylisting) as described (for generic Debian) at: [http://www.roedie.nl/wiki/index.php/Spam_Filtering_With_Postfix](http://www.roedie.nl/wiki/index.php/Spam_Filtering_With_Postfix). Postgrey is running, but the mail.log doesn't show the expected greylisting responses. I notice that postfix in 7.10 is running chrooted, and wonder if that means there's something extra needed to get it speaking with postgrey and whitelister.

---

### Post by mousepad on 2007-11-03
same question, bump

---

### Post by ubnuturero on 2007-11-04
after you installed  postgrey  :
sudo apt-get install postgrey

the postgrey settings are in  /etc/default/postgrey
and your lists  are in /etc/postgrey

there's a known bug in the package   libdb4.4  in ubuntu and you can install the debian unstable 

[http://packages.debian.org/sid/libdb4.4](http://packages.debian.org/sid/libdb4.4)

for postfix configuration just add :

  check_policy_service inet:127.0.0.1:60000

to your smtpd_recipient_restrictions in  main.cf

restart postfix and postgrey and you are done.

---

### Post by HermanAB on 2007-11-04
Also note that you have to delete the postgrey database at least weekly, preferably nightly.  If you don't, two things will happen: The postgrey database will eventually get corrupted and postgrey will stop working, and most spammers will end up in the postgrey database and postgrey will become ineffective.  So put a delete script in cron.daily.

Cheers,

Herman

---

### Post by MJN on 2007-11-05
> **HermanAB said:**
> Also note that you have to delete the postgrey database at least weekly, preferably nightly.  If you don't, two things will happen: The postgrey database will eventually get corrupted and postgrey will stop working, and most spammers will end up in the postgrey database and postgrey will become ineffective.  So put a delete script in cron.daily.

Cheers,

Herman

Do you have a reference (URL) to support this?

Purging the database of all records goes against the whole auto-whitelisting function of a greylisting service. Emptying the database every day will mean that connection triplets that passed yesterday will get deferred again today, yet the whole idea is that they should be trusted given they've recently 'passed' the connection test. Delaying them again serves no purpose.

What did you mean when you said most spammers will be in the database and postgrey will become ineffective? Do you know how greylisting works? If a spammer is responding to the 450 correctly and comes back for a repeat delivery then greylisting is not going to stop them - the whole purpose of greylisting is to stop spammers that don't attempt redelivery. Nothing more, nothing less.

Incidentally, Postgrey purges records by default after 35 days (since last seen) to enable monthly mailing shots to avoid repeated greylisting.

If you could post a reference it would be appreciated.

Mathew

---

### Post by HermanAB on 2007-11-05
I ran postgrey for a few years.  This is just my experience with it.  Some spammers retry on 450 messages.  Clearing out the greylist every day results in significantly less spam than letting it grow.  At minimum, I had to reset it once a week, else it will eventually screw up.  

If you reset it every night using cron.daily, then you will have zero spam in the morning and some spam in the afternoon.  Weird - but that is how it worked in practise.

Cheers,

Herman

---

### Post by HermanAB on 2007-11-05
BTW, I don't use postfix and postgrey anymore.  I switched to Citadel a few months ago.  Instead of doing complicated greylisting, I simply delay the server banner by 10 seconds on every connection attempt and then delay 1 second every step of the way in the SMTP receive engine, thus simulating an incredibly slow and overloaded mail server.

This is done with two simple sleep() additions to the Citadel SMTP engine.  It works better than postgrey and is super simple.  Most spammers cannot afford to waste 20 seconds to deliver a message, so they give up and go away.  The downside is more active (sleeping) threads on my mail server, but it works amazingly well since a sleeping thread doesn't expend any processing time.

Cheers,

Herman

---

### Post by MJN on 2007-11-05
> **HermanAB said:**
> Some spammers retry on 450 messages.

Then greylisting is not going to have **any** effect on them. Simple as that. Greylisting is only effective against spammers who don't retry - that's the fundamental concept of operation.

> Clearing out the greylist every day results in significantly less spam than letting it grow.Clearing out the greylist serves only to cause delay to legitimate senders. It does not result in more spam being stopped (if the spammer got through yesterday then they'll get through today - greylisting will not stop them).

> At minimum, I had to reset it once a week, else it will eventually screw up.There must have been something wrong with your setup. Postgrey is extremely robust, indeed one of its design principles is that is 'simply works' hence why it has fewer advanced features compared with other greylisters because robust reliable operation is the #1 goal.

Mathew

---

### Post by HermanAB on 2007-11-05
"Then greylisting is not going to have any effect on them. Simple as that. Greylisting is only effective against spammers who don't retry"

Yup, that is exactly why I don't bother with greylisting anymore.  A simple delay in the mail processing without the bother of keeping a database, works better.

In addition I also use black lists, spam assassin and clamav of course.  My mail server gets about 10,000 connection attempts per hour.

---

### Post by MJN on 2007-11-05
There is no anti-spam silver bullet, that's why a multitude of defences is required. I've found greylisting to be extremely effective, as have many others, but then it does require your setup to be working properly...! ;-)

For your SMTP banner delay, you really ought to be detecting for dialogue during the interval as many spammers will start the SMTP without waiting for the banner - if they chatter drop 'em (or reject to aid fault diagnosis of broken 'genuine' MTAs).

Mathew

---

### Post by drhiii on 2008-02-15
I installed Postgrey a few days ago and man, did it choke down the SPAM or what!  Such a simple but elegant concept.  

Qoestion is... where are those pesky Postgrey databases?  Searched but couldn;t find reference to where they are located.

And... are there any example of what a cron delete script might look like?  Am looking fror best practices or elegant ways of deleting the Postgrey database... like, does one need to temporarily disable Postfix, the Postgrey daemon, etc... before deleting them?  And of course, where are they, etc??

Hopefully someone can shed some light.  It really did throttle down what was an avalanche of email and after tweaking up Spamassassin and a host of additional apps, things were reasonably tightened but Postgrey was the icing....



> **HermanAB said:**
> Also note that you have to delete the postgrey database at least weekly, preferably nightly.  If you don't, two things will happen: The postgrey database will eventually get corrupted and postgrey will stop working, and most spammers will end up in the postgrey database and postgrey will become ineffective.  So put a delete script in cron.daily.

Cheers,

Herman

---

### Post by MJN on 2008-02-15
Herman's comment was wrong. Or, giving the benefit of the doubt, was referring to a very old version (or, dare I say, his setup!). ;)

There is no need to delete the databases - indeed you really don't want to otherwise you will lose all your auto-whitelisting entries and force all servers to be delayed even though you accepted them only yesterday (for example). With greylisting there is no point in delaying servers that will retry successfully, and that's what the database is partly for - keeping track of those that get through successfully.

In answer to your question though - the databases are in /var/lib/postgrey/ ... but don't touch 'em!

Mathew

P.S. A little known, yet useful, tool within Postgrey is 'postgreyreport' - run it as **sudo postgreyreport < /var/log/mail.log** and it'll scan the logfile in conjunction with its database and work out those connections that 'never came back' (i.e. likely spammers). It gives a good insight into how well the concept is working. You may find some legitimate entries in there - these are either 'genuine' mail servers that don't retry (there are unfortunately some of them around) or the result of pools of servers being used - the original server may well have been rejected but then the message was delivered using another server later on. All in all you should have very few problems, particularly as the package whitelist contains a whole load of known-non-compliant servers out there (usually old(er) ones).

---

### Post by drhiii on 2008-02-15
Dang... excellent information here.  I will NOT touch the DBs'.  Was uneasy by this advice for the reasons that you state, so some validation with your comment is what was needed.  I sh'ant fiddle with them.

And I have not seen any reference to the postgreyreport app.  Yes, very useful as you say.

Thank you for creating this reponse.  Packed with info  and for an app that really seems to be doing a dandy job, it is nice to learn there are deeper things in play here to.

Much gracias....



> **MJN said:**
> Herman's comment was wrong. Or, giving the benefit of the doubt, was referring to a very old version (or, dare I say, his setup!). ;)

There is no need to delete the databases - indeed you really don't want to otherwise you will lose all your auto-whitelisting entries and force all servers to be delayed even though you accepted them only yesterday (for example). With greylisting there is no point in delaying servers that will retry successfully, and that's what the database is partly for - keeping track of those that get through successfully.

In answer to your question though - the databases are in /var/lib/postgrey/ ... but don't touch 'em!

Mathew

P.S. A little known, yet useful, tool within Postgrey is 'postgreyreport' - run it as **sudo postgreyreport < /var/log/mail.log** and it'll scan the logfile in conjunction with its database and work out those connections that 'never came back' (i.e. likely spammers). It gives a good insight into how well the concept is working. You may find some legitimate entries in there - these are either 'genuine' mail servers that don't retry (there are unfortunately some of them around) or the result of pools of servers being used - the original server may well have been rejected but then the message was delivered using another server later on. All in all you should have very few problems, particularly as the package whitelist contains a whole load of known-non-compliant servers out there (usually old(er) ones).

---

### Post by drhiii on 2008-02-15
As you appear to be way up to speed on this stuff.... another question if I may...

What log file analysis app do you recommend for parsing and reporting on /var/log/mail.log, and apache log files for that matter?   I've blown together Awstats and am giving that a go.  Other ways to come at this log analysis in your opinion.

tx a mil in advance... 


> **MJN said:**
> Herman's comment was wrong. Or, giving the benefit of the doubt, was referring to a very old version (or, dare I say, his setup!). ;)

There is no need to delete the databases - indeed you really don't want to otherwise you will lose all your auto-whitelisting entries and force all servers to be delayed even though you accepted them only yesterday (for example). With greylisting there is no point in delaying servers that will retry successfully, and that's what the database is partly for - keeping track of those that get through successfully.

In answer to your question though - the databases are in /var/lib/postgrey/ ... but don't touch 'em!

Mathew

P.S. A little known, yet useful, tool within Postgrey is 'postgreyreport' - run it as **sudo postgreyreport < /var/log/mail.log** and it'll scan the logfile in conjunction with its database and work out those connections that 'never came back' (i.e. likely spammers). It gives a good insight into how well the concept is working. You may find some legitimate entries in there - these are either 'genuine' mail servers that don't retry (there are unfortunately some of them around) or the result of pools of servers being used - the original server may well have been rejected but then the message was delivered using another server later on. All in all you should have very few problems, particularly as the package whitelist contains a whole load of known-non-compliant servers out there (usually old(er) ones).

---

### Post by MJN on 2008-02-15
Awstats is great for Apache (my report is [here]("http://www.newtonnet.co.uk/cgi-bin/awstats.pl")), but I found it lacking when it comes to Postfix/mail.

I use [Logwatch]("http://www2.logwatch.org:81/") to send me daily summaries of my key logs, and Postfix/mail is one such log that it covers. One of the posters here, 'MrC', maintains the Postfix 'plugin' for Logwatch and you can download his latest from [here]("http://www.mikecappella.com/logwatch/").

Okay, so Logwatch is not graphical but it suits me down to the ground - I only really need to know general stats and any problems that might occur.

Note that many log analysers don't sit well with greylisting - all those temporary rejects don't paint a good picture, and indeed only the greylister knows who came back so the analyser is unable to measure its effectiveness like it can do with more 'traditional' (and open/upfront) anti-spam techniques.

So, waffling aside, I use Awstats for web and Logwatch for Postfix (and other system logs, including Apache for that matter - it gives a neat little summary of traffic, hack attempts etc).

Mathew

---

### Post by drhiii on 2008-02-15
Excellent.  I was not 100% on the first outputs from Awstats for mail.log and you may have solved this as well, recommending logwatch.  I too don't need pretty pictures to tell me what I need to now.

So again, thankx for this pointer.

And...... another one just came to mind, so I will go to the well one more time and ask...

The server and clientbase are small.  Most are fixed IPs but a few roam, changing their location due to travel, etc.  I used to run a kludgy app when running sendmail that would scan teh logs for a PAM authentication from a user and if successful, would add this user to an ACL list for sendmail and 'allow' POP3 to occur. Am just now starting to look for a similar application that provides this portable or roaming authentication.  The reason am looking for something like this is the few users are unsophisticated and other types of authentication would be pulling teeth to get them to tweak up on their systems.  I know this is a kludge... but know of any such app?

I'll stop my incessant questions.  This has been most excellent tho.  A lot learned in a really short period of time.  Am grateful for your responses, and I will also give it a rest after this one.  

tx



> **MJN said:**
> Awstats is great for Apache, but I found it lacking when it comes to Postfix.

I use [Logwatch](http://www2.logwatch.org:81/) to send me daily summaries of my key logs, and Postfix/mail is one such log that it covers. One of the posters here, 'MrC', maintains the Postfix 'plugin' for Logwatch and you can download his latest from [here](http://www.mikecappella.com/logwatch/).

Okay, so Logwatch is not graphical but it suits me down to the ground - I only really need to know general stats and any problems that might occur.

Note that many log analysers don't sit well with greylisting - all those temporary rejects don't paint a good picture, and indeed only the greylister knows who came back so the analyser is unable to measure its effectiveness like it can do with more 'traditional' (and open/upfront) anti-spam techniques.

So, waffling aside, I use Awstats for web and Logwatch for Postfix (and other system logs, including Apache for that matter - it gives a neat little summary of traffic, hack attempts etc).

Mathew

---

### Post by MJN on 2008-02-15
I'm afraid I can't help with that one as I use full authentication for SMTP and IMAP/POP.

Can you not do the same? If you're getting your users to authenticate their SMTP connections then they should be able to configure their POP access too.

Indeed, it's sounds odd to be doing 'SMTP-before-POP' - I would expect it to be the other way around given all POP sessions require authentication, it is the SMTP side of things that are usually optional.

Are you sure you haven't written this the wrong way round?

Edit: It could be just the way I read what you wrote. In which case, I still can't help directly!

Mathew

---

### Post by drhiii on 2008-02-16
Howdie,

No probs on this latest question.  I have gone to the well enough times as it is, and you help propelled my tasks well forward as it is...

And yes, it is the way I wrote it that made it bass-akwards.  I constructed a solution to this local need so all is well in the authentication dept there too....

Mucho gracias for all of your help and responses.  Really makes this community worthy.  

regards



> **MJN said:**
> I'm afraid I can't help with that one as I use full authentication for SMTP and IMAP/POP.

Can you not do the same? If you're getting your users to authenticate their SMTP connections then they should be able to configure their POP access too.

Indeed, it's sounds odd to be doing 'SMTP-before-POP' - I would expect it to be the other way around given all POP sessions require authentication, it is the SMTP side of things that are usually optional.

Are you sure you haven't written this the wrong way round?

Edit: It could be just the way I read what you wrote. In which case, I still can't help directly!

Mathew

---

### Post by Mr. C. on 2008-02-21
> **MJN said:**
> 
Note that many log analysers don't sit well with greylisting - all those temporary rejects don't paint a good picture, and indeed only the greylister knows who came back so the analyser is unable to measure its effectiveness like it can do with more 'traditional' (and open/upfront) anti-spam techniques.

Mathew

Starring with 2007-11-14 (version: 1.36.13pre5) of postfix-logwatch, you can configure the types of reject categories desired in the report.  This allows you to group your 5xx rejects, and distinguish 4xx rejects (such as distinguishing 421 transmission channel closes from 45x errors).

As you're probably aware, postfix-logwatch can run either within logwatch or standalone.

There's also full top N and threshold limiting, and lots of other goodies.

MrC

---

### Post by drhiii on 2008-02-21
Yessir, I dug into the configuration characteristics and now have a reasonable report generating out to me.  It has already targeted a couple of things that needed tuning.  I'd used logwatch awhile ago but when returning to a rebuilt server, wanted to generate logs but not knowing the landscape, asked.  Nice to see some things that started life with smart ideas improve with age....

Am running standalone, and creating other reports as well...  kewl stuff.




> **Mr. C. said:**
> Starring with 2007-11-14 (version: 1.36.13pre5) of postfix-logwatch, you can configure the types of reject categories desired in the report.  This allows you to group your 5xx rejects, and distinguish 4xx rejects (such as distinguishing 421 transmission channel closes from 45x errors).

As you're probably aware, postfix-logwatch can run either within logwatch or standalone.

There's also full top N and threshold limiting, and lots of other goodies.

MrC

---

