---
title: "how to setup citadel email server? ubuntu 10.04 server"
date: 2010-07-13
forum: Server Platforms
---

### Post by gabak on 2010-07-13
i have ubuntu 10.04
this is what i have done. according with some website i saw tutorials
[http://www.citadel.org/doku.php/installation:easyinstall:prereq-debian.html](http://www.citadel.org/doku.php/installation:easyinstall:prereq-debian.html)

aptitude update
aptitude install build-essential curl g++ gettext shared-mime-info
aptitude update
aptitude install libssl-dev
aptitude install citadel-suite

then after that i had few option that i leaved everything by default.
now i m at other pc then i wrote in the browser the ip of my server and voila , i m on the webcit but i have not clue what to do in all those menus.

i had a zimbra email server that the mobo just die , so i m using other pc.
my domain is mail [.] gabakmail [.] com [.] ar
i have a public ip and the dns i have them in zoneedit or everydns aiming to my ip.
so now what?
i found this site that helps me a little but there are examples that i dont understand 100% [http://www.aeronetworks.ca/citadel-basics.html](http://www.aeronetworks.ca/citadel-basics.html)
Plz some examples will be great
how do i protect my server against hackers? or ppl who want to use my server to send spam?

thank you all in advance

---

### Post by HermanAB on 2010-07-13
You don't need to add anything to Linux to protect against hackers.  There are just a few things that you should *not* do on a public server:
Do not run VNC server.
Do not run Telnet server.
Do not run FTP server.
Do not run Samba server.
Do not use short passwords.

Citadel is secure, provided that you use long passwords for everybody and don't allow self service account creation (kinda well duh...).  

Install SpamAssassin and ClamAV and hook them in Citadel at the network configuration screen to filter out junk mail.

---

### Post by gabak on 2010-07-13
thxs good advice.
i got it up and running this is great and very easy.
plz could you tell me 
1-how to force users to use SSL for pop and smtp?
2-Also how do i setup smtp requiere authentication?
3- how do i do , so the user wont create their own account?

thank you so much in advance.

---

### Post by pmla on 2010-07-27
**Advice n.1**
Remove Citadel. I runned it for 6 months... I know what I'm talking. Just bad as you eventually see.
It's a pre-history software FULL of bugs and citserver crashes and database problems. Yes the database is not Mysql... lol, the database is BERKELEY.
I think the problem you had was the database going nuts in it's famous spiral of death.... **not an attack**
Their support is rude and obnoxious, and basically useless... have you ever seem their support forum????
Why don't you try the sieve rules, try the vacation rule lolololol... wait better not.
Their webmail is badly constructed and it looks like "c**p". The administrator part is worse... most of the admmin commands are missing (so you need to command line). Their rules, user, groups, distributions list is buggy and only makes sense in their mind.
Try to group members and then created a distribution list... better not :).
Email server BBS style? 1980's.

Advice n.2.. use Postfix
Use something professional, very easy to install. With tons of documentation online and excellent support forums.
For the webmail install round cube on top of postfix.
Your email will be solved forever.

---

### Post by gabak on 2010-08-01
ok
thank you for the   advice.
what do you think about zimbra?
do you know any step by step to make a good mail server?

> **pmla said:**
> **Advice n.1**
Remove Citadel. I runned it for 6 months... I know what I'm talking. Just bad as you eventually see.
It's a pre-history software FULL of bugs and citserver crashes and database problems. Yes the database is not Mysql... lol, the database is BERKELEY.
I think the problem you had was the database going nuts in it's famous spiral of death.... **not an attack**
Their support is rude and obnoxious, and basically useless... have you ever seem their support forum????
Why don't you try the sieve rules, try the vacation rule lolololol... wait better not.
Their webmail is badly constructed and it looks like "c**p". The administrator part is worse... most of the admmin commands are missing (so you need to command line). Their rules, user, groups, distributions list is buggy and only makes sense in their mind.
Try to group members and then created a distribution list... better not :).
Email server BBS style? 1980's.

Advice n.2.. use Postfix
Use something professional, very easy to install. With tons of documentation online and excellent support forums.
For the webmail install round cube on top of postfix.
Your email will be solved forever.

---

### Post by gabak on 2010-08-01
Step 1

      Install Ubuntu 9.04 server with no extra options. The installer does offer to include a mail server---DO NOT SELECT THIS OPTION. Once the basic installation is complete, reboot your computer and log in at the prompt.
Step 2

      Install the required packages and Citadel itself. At the command prompt, enter
      sudo apt-get install spamassassin clamav clamav-milter citadel-suite amavisd-new
Step 3

      Enable SpamAssassin, and start it. As root, edit the /etc/default/spamassassin configuration file, and set
      ENABLED=1
      Then run "/etc/init.d/spamassassin start"
Step 4

      Log into the Citadel administration interface from a web browser, by on your server's IP address. If your server's IP is 192.168.0.1 for example, you would enter this in your browser's URL bar:
      [http://192.168.0.1](http://192.168.0.1)
      The default user is "Administrator" and the default password is the one you choosed when you install citadel
Step 5

      Click "Administration," then "edit site-wide configuration." Enter your web server's fully qualified domain name (such as mail.foobar.com). If you do not have one, you can use dyndns.org or a similar service to generate one dynamically for you. This option must be set for email to work.
Step 6
      Return to the Administration menu; use "add, change, delete user accounts" to create your mail users. Your citadel email and webmail server is complete.

---

### Post by pmla on 2010-08-02
> **gabak said:**
> ok
thank you for the   advice.
what do you think about zimbra?
do you know any step by step to make a good mail server?

Zimbra is also very good... as you know smtp is postfix based.

In November this year they are finally releasing support for Ubuntu 10.04 x64 LTS.... iupiiiii it will happen in Zimbra build 6.0.9 ... the current build is 6.0.7 (support for ubuntu 8.04)

In November, I'm going to change to Zimbra to have easy and central administration over the entire system using the web browser.

---

### Post by kevin11951 on 2010-08-02
> **pmla said:**
> **Advice n.1**
Remove Citadel. I runned it for 6 months... I know what I'm talking. Just bad as you eventually see.
It's a pre-history software FULL of bugs and citserver crashes and database problems. Yes the database is not Mysql... lol, the database is BERKELEY.
I think the problem you had was the database going nuts in it's famous spiral of death.... **not an attack**
Their support is rude and obnoxious, and basically useless... have you ever seem their support forum????
Why don't you try the sieve rules, try the vacation rule lolololol... wait better not.
Their webmail is badly constructed and it looks like "c**p". The administrator part is worse... most of the admmin commands are missing (so you need to command line). Their rules, user, groups, distributions list is buggy and only makes sense in their mind.
Try to group members and then created a distribution list... better not :).
Email server BBS style? 1980's.

Advice n.2.. use Postfix
Use something professional, very easy to install. With tons of documentation online and excellent support forums.
For the webmail install round cube on top of postfix.
Your email will be solved forever.

I disagree COMPLETELY!  I have been using Citadel for a while, and even though I haven't used all the features, what I use has worked reliably.

Are you sure you are using the latest release from their Debian repos?  Mine: Citadel 7.82 with WebCit 7.81, server build 8707

---

### Post by pmla on 2010-08-02
> **kevin11951 said:**
> I disagree COMPLETELY!  I have been using Citadel for a while, and even though I haven't used all the features, what I use has worked reliably.

Are you sure you are using the latest release from their Debian repos?  Mine: Citadel 7.82 with WebCit 7.81, server build 8707

Yes... Tested it just last week. Besides I runned it on a production system with 120 users.... Biggest mistake and worse months of my life. Still remember today the 2 database corruptions I had with it.
Just the old cr*p like 6 months ago.

-Database = still berkeley = BIG MISTAKE, you if don't know the difference between a mysql and berkeley database... not going to explain you... just google :)
-Distributions lists = no improvement
-User Management and grouping = no improvement
-ROOMS = still only makes sense in citadel peoples minds.
-Commands = still only available in command line and not web browser
-Sieve Rules = not working fully.... giving error as seen more than 1 year ago... sieve vacation still does not work in ubuntu based systems ( exactly the same as more than 1 year ago)
-webmin = better display / layout but, same old design, no extra functions added to the administrator.
-client software = no special integration, no client
-Calendars = joke, no free /busy support
-log = still giving errors
LIST IS ENDLESS


Hey kevin, you clearly have low expectations when it comes to an email server or integrated system, not even mentioning anything production related. With don't you try a real email system like Zimbra that can easily be used in Production. NO COMPARISON

Rest my case... please use citadel if that makes you feel warm inside... the rest of us can use postfix / zimbra :)

---

### Post by gabak on 2010-08-02
yes PMLA you are right surely but i short of time right now ,i had up and runnig citadel in 5 minutes and i have few users for the email now but i could make work the antispam do you know how to make it work???
i have done this but nothing yet

sudo apt-get install clamav clamav-milter spamassassin citadel-suite amavisd-new

Install and Start Spamassassin

vim /etc/default/spamassassin

# Change to one to enable spamd
ENABLED=1

sudo /etc/init.d/spamassassin start

according this [http://ubuntuforums.org/showthread.php?p=9672048#post9672048](http://ubuntuforums.org/showthread.php?p=9672048#post9672048)

---

### Post by HermanAB on 2010-08-03
Hmm, I've been running Citadel for many years.  Yes, there have been one or two hiccups that I know of when new releases were buggy, but I always managed to resolve it easily.

I had a database corruption once after a PSU failure and it was resolved easily as well.  The solution is in the FAQ.  If you have many users, then you need to change a few database options to improve efficiency - this is documented as well.  With those tweaks, Citadel can handle tens of thousands of users.

The main advantage of Citadel is the Easy Install script.  There is no other complete mail system that one can get up and running in 20 minutes flat.

BTW, a 'Citadel Room' is just another name for an 'Imap Folder' - not exactly hard to fathom.  Citadel is the easiest mail server since King Tut's Abacus.

---

### Post by pmla on 2010-08-03
> **gabak said:**
> yes PMLA you are right surely but i short of time right now ,i had up and runnig citadel in 5 minutes and i have few users for the email now but i could make work the antispam do you know how to make it work???
i have done this but nothing yet

sudo apt-get install clamav clamav-milter spamassassin citadel-suite amavisd-new

Install and Start Spamassassin

vim /etc/default/spamassassin

# Change to one to enable spamd
ENABLED=1

sudo /etc/init.d/spamassassin start

according this [http://ubuntuforums.org/showthread.php?p=9672048#post9672048](http://ubuntuforums.org/showthread.php?p=9672048#post9672048)


Spam and anti-virus managements are a click away in zimbra, basically out-of-the-box and everything can be done in the administrator zone (web browser).
In citadel... that is your first problem out of many :). It will eventually run if you keep on trying :). Why don't you ask for help in their support forum :)
I also think you should be asking for help from these 2 users that seem to "love and find perfect" citadel!?! Let's see how much they will help you?!

---

### Post by pmla on 2010-08-03
> **HermanAB said:**
> Hmm, I've been running Citadel for many years.  Yes, there have been one or two hiccups that I know of when new releases were buggy, but I always managed to resolve it easily.

I had a database corruption once after a PSU failure and it was resolved easily as well.  The solution is in the FAQ.  If you have many users, then you need to change a few database options to improve efficiency - this is documented as well.  With those tweaks, Citadel can handle tens of thousands of users.

The main advantage of Citadel is the Easy Install script.  There is no other complete mail system that one can get up and running in 20 minutes flat.

BTW, a 'Citadel Room' is just another name for an 'Imap Folder' - not exactly hard to fathom.  Citadel is the easiest mail server since King Tut's Abacus.

I think you are running citadel for so many years that you just got detached from reality and other softwares. Again, when expectations are low, everything is fine.

About the database... that's is your opinion. Everybody knows how hard it is to manipulate the closed berkeley database and how slow it manipulates and handles data. The support forum is full of database spins of death and entire email systems lost. Please update yourself and google berkeley vs mysql. What tweeks are you talking about to improve berkeley :)?!?! when and where was that tested?!?!?!
tens of thousands of users?!?!?! when, where, what?!?! reality check.

The main advantage of citadel is the 20m setup. The time "saved" here is surely lost fixing issues, browsing the web for the little documentation available and asking for help. Do not see the point there?!?!?!
For i.e. in zimbra it might take you from half a day to 3 days to get it up and running perfectly. But it runs as it is supposed to  with beautiful, acclaimed postfix in the background as smtp and MySql as database. Trying to compare this to citadel,  is to live in a warped world.

ROOMS is an IMAP folder... LOL so what is a distribution list?? do you know the concept of that? And how do I group users for those ROOMS?!
By the way...what is a FLOOR?! lol, how do I group rooms in a floor and set rules for them?!?!
lol... Please get real, do not try to invent a square wheel, because the round wheel was already invented... and it just works better.

---

### Post by ahbart on 2010-08-03
@pmla: sounds like you have had some bad experience with citadel :D

---

### Post by gabak on 2010-08-03
PMLA you are right there is very little information out there.
that is why i m asking here, but my expectation are very low.
i need an email server for 10 ppl with webmail and pop and smtp and a good antispam.
that's it.
please would you help me with the antispam thing?
how do i install it?
the thing is that now i dont have much time to spend in the server but surely i ll install roundcube or zimbra but now it is nt the moment cuz matter of time.
Except if u send me a link with a nice tutorial step by step how to install zimbra and that i wont have to be fighting to make it work.
At least citadel i made it work in 5 minutes. ( i dont count the time it took to be installed)


> **pmla said:**
> Spam and anti-virus managements are a click away in zimbra, basically out-of-the-box and everything can be done in the administrator zone (web browser).
In citadel... that is your first problem out of many :). It will eventually run if you keep on trying :). Why don't you ask for help in their support forum :)
I also think you should be asking for help from these 2 users that seem to "love and find perfect" citadel!?! Let's see how much they will help you?!

---

### Post by ahbart on 2010-08-03
Zimbra would be a very good solution than. Because it is all in one and working out of the box. It is including all the software needed. but... Zimbra is not yet available for 10.04.
There are very good tutarials for setting up your own mailserver on U10.04, including imap, secure connections, antispam and antivirus. Have a Google.

Edit: Well, actually I did install Zimbra on Lucid. But I had to do some tweaking to get it running. I didn't like the all in one thing. I got conflict with my own webserver/mysql for example.

---

### Post by pmla on 2010-08-03
> **gabak said:**
> PMLA you are right there is very little information out there.
that is why i m asking here, but my expectation are very low.
i need an email server for 10 ppl with webmail and pop and smtp and a good antispam.
that's it.
please would you help me with the antispam thing?
how do i install it?
the thing is that now i dont have much time to spend in the server but surely i ll install roundcube or zimbra but now it is nt the moment cuz matter of time.
Except if u send me a link with a nice tutorial step by step how to install zimbra and that i wont have to be fighting to make it work.
At least citadel i made it work in 5 minutes. ( i dont count the time it took to be installed)

Again... there's a support "forum"... if you can call it a forum... it's more like a citadel room/BBS type of thing:
[HERE'S THE LINK]("http://uncensored.citadel.org:8080/")

---

### Post by pmla on 2010-08-03
> **ahbart said:**
> Zimbra would be a very good solution than. Because it is all in one and working out of the box. It is including all the software needed. but... Zimbra is not yet available for 10.04.
There are very good tutarials for setting up your own mailserver on U10.04, including imap, secure connections, antispam and antivirus. Have a Google.

Edit: Well, actually I did install Zimbra on Lucid. But I had to do some tweaking to get it running. I didn't like the all in one thing. I got conflict with my own webserver/mysql for example.


Yes... agree, might take half a day to 3 days to have it perfected. Let's wait and see 6.0.9 for UB 10.04

---

### Post by kevin11951 on 2010-08-04
Small - Medium Business:

Citadel:  They just need a simple email server with pop and imap, and they need it now.

Large - Enterprise:

Zimbra:  They need to be able to configure it to do anything at any time.  Also, for those who need/want professional support.  

Plus, you need/should buy a separate server just for email with at least 4GB of ram, for more than a few small businesses, this is out of the question.

See, that wasn't so hard ;)

---

### Post by caseygibbs on 2010-09-05
My $.02 - I have been using citadel for a very small group of users, less than ten, for most of a year now and have loved every minute of it. It's brainless and beautiful, haven't had a hiccup (though I do wish the xmpp worked with more clients - maybe I just haven't figured it out fully yet). Chat, IM, imap, pop, the calendar, the text client, love it all. Super cool package. You get, yes, much of the same functionality with Zimbra, but I'm not crazy about how resource-intensive Zimbra is, and what a hassle. If I wanted only email, I'd use postfix, and if I wanted only email and webmail I'd use postfix and roundcube, but since I want mailing lists, forums, chat, IM, email, webmail, calendar, and a convenient text client for ssh: Citadel. No contest.

---

### Post by houndi on 2010-09-05
I disagree COMPLETELY! I have been using Citadel for a while, and even though I haven't used all the features, what I use has worked reliably.

---

### Post by caseygibbs on 2010-09-07
...I will add though that at least in my personal opinion, Citadel's hurting for lack of documentation. It all tells you to go to the mothership Citadel network, called Uncensored; but I have a hard time using that site to find data I'm looking for. I mean, there's more than enough documentation for garden-variety processes like installation, configuration, backup, etc; and maybe if I spent more time on Uncensored I'd make more sense of it; but I'd love it if there were more user-friendly data sources out there on this amazing suite.

---

### Post by KpSingh on 2013-01-10
):P
hi 
this post is too old but i think now your work experience on citadel  or other email servers might had got increased by 2 years 

so my question is for citadel

sieve programming can i get help on it (rookie in it:o)
i want to edit my every received mail's subject 
any redirection to helpful link or a invaluable suggestion will be helpful

and @pmla - yes it is very buggy as you said but what i can say need it as client demands;)

---

### Post by howefield on 2013-01-10
Old thread closed.

---

