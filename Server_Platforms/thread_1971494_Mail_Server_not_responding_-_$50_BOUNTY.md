---
title: "Mail Server not responding - $50 BOUNTY"
date: 2012-05-02
forum: Server Platforms
---

### Post by KMatsumari on 2012-05-02
****
BOUNTY OF $50 TO WHOEVER COMPLETELY SATISFIES THESE ISSUES WITH A PERMANENT FIX TO MY EMAIL SERVER PROBLEMS.
Bounty will be paid upon the successful sending and receiving of an email message from both my server and your email address. I require that my android phone either POP3 or IMAP connect to my email server, and I will send AND receive the two emails using my phone. Upon completion, payment details will be given.
This Bounty may be increased if I deem it necessary. A full documentation of what was done MUST be submitted so the problem can be fixed by myself in the future (after all, this is a learning experience for me as well).
****

I have finally worked out the major kinks in my system and I now have it online, but my mailer serving portion of my server is not sending or receiving any mail. Guide for Perfect Ubuntu Server 11.10 Oneiric Ocelot w/ISPConfig 3.0.4.4 was followed explicitly, ISPConfig was allowed access to MySQL database, and I followed the manual for ISPConfig 3. It would seem that EVERYTHING else is fine, but users cannot send or receive any emails from outside of the local host, and only if access is established directly from the server's network and not from the internet (I have to test a couple of things before this is absolutely certain; as of now, assume that messages CANNOT be sent in any way). I have the ISPConfig 3 android app that will check my ports and logs and such, and my mail ports are open and my mail service is up (pinged and checked from another internet source separate from the server). I think my mail error log has something to offer as to why this is happening:

```

Apr 29 21:03:47 web postfix/trivial-rewrite[18588]: fatal: proxy:mysql:/etc/postfix/mysql-virtual_domains.cf(0,lock|fold_fix): table lookup problem
Apr 29 21:03:47 web postfix/trivial-rewrite[18589]: fatal: proxy:mysql:/etc/postfix/mysql-virtual_domains.cf(0,lock|fold_fix): table lookup problem
Apr 29 21:04:39 web postfix/smtp[18596]: fatal: mysql:/etc/postfix/mysql-virtual_relaydomains.cf(0,lock|fold_fix): table lookup problem
Apr 29 21:04:39 web postfix/smtp[18597]: fatal: mysql:/etc/postfix/mysql-virtual_relaydomains.cf(0,lock|fold_fix): table lookup problem
Apr 29 21:04:40 web postfix/error[18601]: fatal: mysql:/etc/postfix/mysql-virtual_relaydomains.cf(0,lock|fold_fix): table lookup problem
Apr 29 21:04:40 web postfix/error[18606]: fatal: mysql:/etc/postfix/mysql-virtual_relaydomains.cf(0,lock|fold_fix): table lookup problem
Apr 29 21:04:40 web postfix/error[18602]: fatal: mysql:/etc/postfix/mysql-virtual_relaydomains.cf(0,lock|fold_fix): table lookup problem
Apr 29 21:04:40 web postfix/error[18603]: fatal: mysql:/etc/postfix/mysql-virtual_relaydomains.cf(0,lock|fold_fix): table lookup problem
Apr 29 21:04:40 web postfix/error[18604]: fatal: mysql:/etc/postfix/mysql-virtual_relaydomains.cf(0,lock|fold_fix): table lookup problem
Apr 29 21:04:41 web postfix/qmgr[18595]: fatal: mysql:/etc/postfix/mysql-virtual_relaydomains.cf(0,lock|fold_fix): table lookup problem
Apr 29 21:04:48 web postfix/trivial-rewrite[18609]: fatal: proxy:mysql:/etc/postfix/mysql-virtual_domains.cf(0,lock|fold_fix): table lookup problem
Apr 29 21:04:48 web postfix/trivial-rewrite[18610]: fatal: proxy:mysql:/etc/postfix/mysql-virtual_domains.cf(0,lock|fold_fix): table lookup problem
Apr 29 21:05:49 web postfix/trivial-rewrite[18658]: fatal: proxy:mysql:/etc/postfix/mysql-virtual_domains.cf(0,lock|fold_fix): table lookup problem
Apr 29 21:05:49 web postfix/trivial-rewrite[18659]: fatal: proxy:mysql:/etc/postfix/mysql-virtual_domains.cf(0,lock|fold_fix): table lookup problem
Apr 29 21:06:50 web postfix/trivial-rewrite[18665]: fatal: proxy:mysql:/etc/postfix/mysql-virtual_domains.cf(0,lock|fold_fix): table lookup problem
Apr 29 21:06:50 web postfix/trivial-rewrite[18666]: fatal: proxy:mysql:/etc/postfix/mysql-virtual_domains.cf(0,lock|fold_fix): table lookup problem
Apr 29 21:07:51 web postfix/trivial-rewrite[18675]: fatal: proxy:mysql:/etc/postfix/mysql-virtual_domains.cf(0,lock|fold_fix): table lookup problem
Apr 29 21:07:51 web postfix/trivial-rewrite[18676]: fatal: proxy:mysql:/etc/postfix/mysql-virtual_domains.cf(0,lock|fold_fix): table lookup problem
Apr 29 21:08:52 web postfix/trivial-rewrite[18682]: fatal: proxy:mysql:/etc/postfix/mysql-virtual_domains.cf(0,lock|fold_fix): table lookup problem
Apr 29 21:08:52 web postfix/trivial-rewrite[18683]: fatal: proxy:mysql:/etc/postfix/mysql-virtual_domains.cf(0,lock|fold_fix): table lookup problem

```

I know there is going to be a lot of asking for outputs from many different commands, so please don't reply once for each command you want me to paste output from; give it all to me at once and I can pump it out in one reply.

Again, I can access my server entirely from any internet source, and I can get in and out of ispconfig, squirrelmail, phpmyadmin, and ssh/vnc to it as well. I don't believe that my ISP is blocking any of my mail ports, but I will give them a call and make certain that they aren't, but there shouldn't be any port problems if I can login to my squirrelmail email accounts (although I could be mistaken).

---

### Post by elico on 2012-05-02
leave the bounty for now.
just state your server purposes.(web, mail others..)
i dont like ISPconfig in any portion.
if you dont know how the server works you wont be able to debug... as you understand.
if you can upload\send the whole /etc/* in a tar file it will be wonderful.
else then that start with cat /etc/postfix/"every cf fie" output.
i like more dovecot then courier.

50,000 users working 24X7 none one problem mail server is good?

---

### Post by tangerine0469 on 2012-05-02
judging by the errors it looks like i could be a database error. it says table lookup problem. try the following

1. look into the database and see if the table has crashed (if it was working previously) and note the database connection info(database name, ip(or localhost), table name, username, password and permissions for the db in question.

2. check that postfix has the correct datbase info base off of step one. like the connection or even correct mysql sting for the lookup.

that would be my first place to start.

---

### Post by LHammonds on 2012-05-03
Looks like a database problem to me too.

Is your Database running?  Did it run out of space?   Did you upgrade MySQL recently?

PS - Not interested in the $$

---

### Post by Jonathan L on 2012-05-03
Hi KMatsumari

```

fatal: proxy:mysql:/etc/postfix/mysql-virtual_domains.cf(0,lock|fold_fix): table lookup problem
fatal: mysql:/etc/postfix/mysql-virtual_relaydomains.cf(0,lock|fold_fix): table lookup problem

```Seems pretty evident to me that you've got a problem with postfix accessing your MySQL databases, and you need to solve those before you try any networking issues.

You do this by looking things up with postmap -q name filename in the various maps (virtual_domains, virtual_relaydomains and so on).

I'd recommend getting everything working correctly with file-based maps, and do MySQL later.

The following is from [http://www.postfix.org/DATABASE_README.html](http://www.postfix.org/DATABASE_README.html)[INDENT]_**Preparing Postfix for LDAP or SQL lookups**_

 LDAP and SQL are complex systems. Trying to set up both Postfix and LDAP or SQL at the same time is definitely not a good idea. You can save yourself a lot of time by implementing Postfix first with local files such as Berkeley DB.  Local files have few surprises, and are easy to debug with the postmap(1) command:[INDENT] % **postmap -q [EMAIL="info@example.com"]info@example.com[/EMAIL] hash:/etc/postfix/virtual **  [/INDENT]Once you have local files working properly you can follow the instructions in ldap_table(5), mysql_table(5), pgsql_table(5) or sqlite_table(5) and replace local file lookups with LDAP or SQL lookups.  When you do this, you should use the postmap(1) command again, to verify that database lookups still produce the exact same results as local file lookup:[INDENT] % **postmap -q [EMAIL="info@example.com"]info@example.com[/EMAIL] ldap:/etc/postfix/virtual.cf **  [/INDENT]Be sure to exercise all the partial address or parent domain queries that are documented under "table search order" in the relevant manual page:  access(5), canonical(5), virtual(5), transport(5), or under the relevant configuration parameter: mynetworks, relay_domains, parent_domain_matches_subdomains. 
[/INDENT]Hope that's of some help.

Send your money to a charity you like, we'll help you anyway: this is ubuntu: [http://en.wikipedia.org/wiki/Ubuntu_%28philosophy%29](http://en.wikipedia.org/wiki/Ubuntu_%28philosophy%29)

Kind regards,
Jonathan.

---

### Post by KMatsumari on 2012-05-03
> 
leave the bounty for now.
just state your server purposes.(web, mail others..)
i dont like ISPconfig in any portion.
if you dont know how the server works you wont be able to debug... as you understand.
if you can upload\send the whole /etc/* in a tar file it will be wonderful.
else then that start with cat /etc/postfix/"every cf fie" output.
i like more dovecot then courier.

50,000 users working 24X7 none one problem mail server is good?


My server purposes are stated in the guide I have referenced from [http://www.howtoforge.com/perfect-server-ubuntu-11.10-ispconfig-3-p3](http://www.howtoforge.com/perfect-server-ubuntu-11.10-ispconfig-3-p3). This is going to guide the user step by step on setting up a composite multi-caste server (web, ftp, mail, dns, and db) with phpmyadmin and ispconfig 3.

I'm sorry to hear that you do not like ISPConfig at all, but I do, and I am going to use it. I do understand how a server works, unfortunately I am just getting to the point of asking for help recently as I have been spending about 12 hours each day working on my server, getting past many other obstacles while having school and a life to take care of, and I am stretched beyond my limit now, and I need a break to do something else that won't cause me to take a sledge to my machine if it gives me another error.

I'm sure if I did compress my entire etc directory and send it to you, it will likely be fixed very quickly, but I must respectfully decline to go that route as this machine contains sensitive client data, and the etc directory is known to contain enough information to give any knowledgable user unlimited access to the computer in question. I am sorry, but I do not have the time or desire to censor all applicable files of my sensitive information nor change my sensitive information after the fact.

cat'ing every configuration file for postfix is just as effective as looking at the file itself in editor, so I will attach the files as my post will be rather long as it is.

I understand that dovecot can handle some of the other tasks by itself and be a heavy lifter so to speak, but call me old-fashioned; I prefer to delegate certain tasks so the errors can be narrowed down to a process and thus specific to the cause. Plus, I unfortunately have heard about more complaints and problems for dovecot than courier, especially when it came to virtual user mailpaths and dovecot not looking in the correct directory after it gets updated (I'm not wanting more problems, although I have plenty already)

I don't think I understood your last comment, but I'm guessing you are saying that you are hosting a server with 50,000 users, it's up and running 24 hours a day all week long, and you haven't had a single problem, and that your mail server is good. That's great, but that isn't my mail server with my services and files on it with other services and components running in unison with it, nor is it my hardware that you are using either. One setup can never be compared to another unless it is a duplicated setup on the same hardware with the *exact* same configuration and data. Even on different networks, different problems can occur (my routers give me hell all of the time).

> 
judging by the errors it looks like i could be a database error. it says table lookup problem. try the following

1. look into the database and see if the table has crashed (if it was working previously) and note the database connection info(database name, ip(or localhost), table name, username, password and permissions for the db in question.

2. check that postfix has the correct datbase info base off of step one. like the connection or even correct mysql sting for the lookup.

that would be my first place to start.


1. It seems that all of my database tables are green, except for these errors:

mysql.general_log	: The storage engine for the table doesn't support a... | No index defined
mysql.slow_log		: The storage engine for the table doesn't support a... | No index defined

I assume these are not a problem, so moving on. After a few days away from this, and a few cups of coffee later, I decided to take a closer look at this with a level head. The database issue I have is being green-lighted. Anyone who has used ISPConfig 3 knows (or should know) that the server it runs on may or may not be the server for anything else, as the software is just as it implies: an **I**nternet **S**ervice **P**rovider, so it can and will direct the database to wherever you say your services are being hosted for a specific client. after looking into the 'mysql-virtual_domains.cf' file in /etc/postfix/, I matched its intended value with what ISPConfig has issued to the database, which is my unqualified domain name (should be the FQDN of my machine where my mail server is found). So I am going to browse my ISPConfig for my mail server domain and try to set a fix on this.

2. correct place to look, db just has an incorrect value. As said in (1), I am going to attempt to fix that using the ISPConfig interface first. If that fails, I guess I could just edit that domain field and any other records that contain the incorrect location to my mail server (I can always change them back). Good thing I am familiar with database concepts, and glad this isn't a microsoft access db or i'd be having some "fun".

Working now...

made a couple changes, but it seems I have something new that doesn't sound good:

```

May 3 10:30:15 web postfix/master[19863]: warning: process /usr/lib/postfix/trivial-rewrite pid 19251 exit status 1
May 3 10:31:15 web postfix/proxymap[14211]: warning: connect to mysql server 127.0.0.1: Access denied for user 'ispconfig'@'web.kelina-enterprises.com' (using password: YES)
May 3 10:31:15 web postfix/proxymap[14211]: warning: connect to mysql server 127.0.0.1: Access denied for user 'ispconfig'@'web.kelina-enterprises.com' (using password: YES)
May 3 10:31:15 web postfix/trivial-rewrite[19257]: fatal: proxy:mysql:/etc/postfix/mysql-virtual_domains.cf(0,lock|fold_fix): table lookup problem
May 3 10:31:15 web postfix/trivial-rewrite[19258]: fatal: proxy:mysql:/etc/postfix/mysql-virtual_domains.cf(0,lock|fold_fix): table lookup problem
May 3 10:31:16 web postfix/smtpd[14408]: warning: problem talking to service rewrite: Connection reset by peer
May 3 10:31:16 web postfix/smtpd[14210]: warning: problem talking to service rewrite: Success
May 3 10:31:16 web postfix/master[19863]: warning: process /usr/lib/postfix/trivial-rewrite pid 19257 exit status 1
May 3 10:31:16 web postfix/master[19863]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling
May 3 10:31:16 web postfix/master[19863]: warning: process /usr/lib/postfix/trivial-rewrite pid 19258 exit status 1
May 3 10:31:16 web postfix/smtpd[19006]: warning: problem talking to service rewrite: Success
May 3 10:31:22 web postfix/qmgr[19259]: A3FCE6C3097: from=, size=652, nrcpt=1 (queue active)
May 3 10:31:22 web postfix/qmgr[19259]: 6F7686C1209: from=, size=630, nrcpt=1 (queue active)
May 3 10:31:22 web postfix/qmgr[19259]: 0E7DD6C3096: from=, size=654, nrcpt=1 (queue active)
May 3 10:31:22 web postfix/qmgr[19259]: D35B76C308C: from=, size=652, nrcpt=1 (queue active)
May 3 10:31:22 web postfix/qmgr[19259]: 3F51B6C308E: from=, size=650, nrcpt=1 (queue active)
May 3 10:31:22 web postfix/qmgr[19259]: E4F886C1519: from=, size=657, nrcpt=1 (queue active)
May 3 10:31:22 web postfix/qmgr[19259]: 6049E6C3091: from=, size=652, nrcpt=1 (queue active)
May 3 10:31:22 web postfix/qmgr[19259]: A630E6C30AE: from=, size=653, nrcpt=1 (queue active)
May 3 10:31:22 web postfix/qmgr[19259]: 2ED8D6C30DD: from=, size=648, nrcpt=1 (queue active)
May 3 10:31:22 web postfix/qmgr[19259]: C31FE6C307D: from=, size=656, nrcpt=1 (queue active)
May 3 10:31:22 web postfix/qmgr[19259]: 3E3926C309C: from=, size=655, nrcpt=1 (queue active)
May 3 10:31:22 web amavis[13614]: (!)DENIED ACCESS from IP 192.168.0.6, policy bank ''
May 3 10:31:22 web amavis[13614]: (!)DENIED ACCESS from IP 192.168.0.6, policy bank ''
May 3 10:31:22 web postfix/smtp[19260]: A3FCE6C3097: to=, relay=127.0.0.1[127.0.0.1]:10024, delay=472221, delays=472221/0.01/0/0, dsn=4.4.2, status=deferred (lost connection with 127.0.0.1[127.0.0.1] while receiving the initial server greeting)
May 3 10:31:22 web postfix/smtp[19260]: warning: connect to mysql server 127.0.0.1: Access denied for user 'ispconfig'@'web.kelina-enterprises.com' (using password: YES)
May 3 10:31:22 web postfix/smtp[19260]: fatal: mysql:/etc/postfix/mysql-virtual_relaydomains.cf(0,lock|fold_fix): table lookup problem
May 3 10:31:22 web postfix/smtp[19261]: 6F7686C1209: to=, orig_to=, relay=127.0.0.1[127.0.0.1]:10024, delay=10881, delays=10881/0.03/0/0, dsn=4.4.2, status=deferred (lost connection with 127.0.0.1[127.0.0.1] while receiving the initial server greeting)

```

> 
Looks like a database problem to me too.

Is your Database running? Did it run out of space? Did you upgrade MySQL recently?

PS - Not interested in the $$


MySQL was installed with apt only last week, and I haven't looked for any updates yet (doing that right now to be safe), and I just restarted to make certain it is running. It said stop/wait, so it implies it was running.

```

mysql  Ver 14.14 Distrib 5.1.62, for debian-linux-gnu (i686) using readline 6.2

```

It seems to me I am using the older development release that is currently supported, and I do not want to change over just yet. Once I am able to, I will setup a new system with ubuntu 12.04 LTS and fresh install everything again, thus making the version being installed 5.5.23.

> 
Seems pretty evident to me that you've got a problem with postfix accessing your MySQL databases, and you need to solve those before you try any networking issues.

You do this by looking things up with postmap -q name filename in the various maps (virtual_domains, virtual_relaydomains and so on).

I'd recommend getting everything working correctly with file-based maps, and do MySQL later.

The following is from [http://www.postfix.org/DATABASE_README.html](http://www.postfix.org/DATABASE_README.html)
Preparing Postfix for LDAP or SQL lookups

LDAP and SQL are complex systems. Trying to set up both Postfix and LDAP or SQL at the same time is definitely not a good idea. You can save yourself a lot of time by implementing Postfix first with local files such as Berkeley DB. Local files have few surprises, and are easy to debug with the postmap(1) command:
% postmap -q [email]info@example.com[/email] hash:/etc/postfix/virtual
Once you have local files working properly you can follow the instructions in ldap_table(5), mysql_table(5), pgsql_table(5) or sqlite_table(5) and replace local file lookups with LDAP or SQL lookups. When you do this, you should use the postmap(1) command again, to verify that database lookups still produce the exact same results as local file lookup:
% postmap -q [email]info@example.com[/email] ldap:/etc/postfix/virtual.cf
Be sure to exercise all the partial address or parent domain queries that are documented under "table search order" in the relevant manual page: access(5), canonical(5), virtual(5), transport(5), or under the relevant configuration parameter: mynetworks, relay_domains, parent_domain_matches_subdomains. 
Hope that's of some help.

Send your money to a charity you like, we'll help you anyway: this is ubuntu: [http://en.wikipedia.org/wiki/Ubuntu_%28philosophy%29](http://en.wikipedia.org/wiki/Ubuntu_%28philosophy%29)

Kind regards,
Jonathan.


ISPConfig states that it configures and sets up courier, postfix, maildrop, getmail, and all other services for the related servers for each installation. I'm assuming that I did something wrong along the way, so I may just start fresh again after I make some backups of my client information.

I appreciate that you guys are wanting to help me without worry to the bounty, but it seems that once I had advertized a bounty that I finally got some responses (this thread actually was created last week with this problem, but no answers.

I will try some things and post my findings.

---

### Post by tangerine0469 on 2012-05-03
> May 3 10:31:15 web postfix/proxymap[14211]: warning: connect to mysql server 127.0.0.1: Access denied for user 'ispconfig'@'web.kelina-enterprises.com' (using password: YES)
May 3 10:31:15 web postfix/proxymap[14211]: warning: connect to mysql server 127.0.0.1: Access denied for user 'ispconfig'@'web.kelina-enterprises.com' (using password: YES)

Try going in to phpmyadmin and checking the access rights for the username ispconfig. 

also i noticed in the config file for mysql-virtual_domains.cf
that the two commands are touching and possibly reading as a single command and may be the root of the issue

> user = ispconfig
password = ********************
dbname = dbispconfigtable = mail_domain
select_field = domain
where_field = domain
additional_conditions = and active = 'y' and server_id = 1
hosts = 127.0.0.1


Unless that was my notepad bringing it up incorrectlybut i did not see a line break there.

try this:

> user = ispconfig
password = ********************
dbname = dbispconfig
table = mail_domain
select_field = domain
where_field = domain
additional_conditions = and active = 'y' and server_id = 1
hosts = 127.0.0.1

i am still checking between calls at work (network solutions) and i will let you know if i find anything else in the config files.

---

### Post by elico on 2012-05-03
i wasnt following the ubuntu releases and the latest one that i have used was 11.10.
one thing i forgot to ask? are you using a 32 bit or 64 version of ubuntu?
has i have seen in the mysql header it seems like a 32 bit?
it wiil take me sometime but for the first time i will try ISPconfig just to see how it works.

until now from the cf files it seems like ISPconfig is using the old cf sql query format which is bad in my opinion.
the new version is much more sql syntax compatible.

fix the password\access for the ispconfig db user.
and also something really recommended is to remove for testing the:
proxy_read_maps ......

it's kind of chrooting mysql postfix proxy and can cause a lot of pain in the ***!!

Thats for now.

---

### Post by elico on 2012-05-03
well it's just seems like ISPconfig was not meant to work yet smoothly with 12.04TLS.
it has too much things that needed to be done instead of just start and run.
it took me an hour to make stuff work and then it complains on sasl stuff.
after solving that i have seen couple of other missing things.
so either use it on 11.10 what meant for or wait for the next version.
and dont rush to run any new software without getting any flashbacks\flashbangs to your face.

try this:
[http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3)

that was ment for 1204LTS

---

### Post by tangerine0469 on 2012-05-03
Ok, so i am still going through these as i work and i do notice that several of them seem to be missing line breaks for the db names and table names, etc. as a rule of thumb i am going to check all of these and note them all for you. i could be wrong and it could just be my text editor being a pain in the you know what but i have done this before following a mail server setup on workaround.org and found that when i do the setup and copy and paste i sometimes have to put the line breaks in manually.

mysql-virtual_relaydomains.cf:
> user = ispconfig
password = ********************
dbname = dbispconfig
table = mail_transport
select_field = domain
where_field = domain
additional_conditions = and active = 'y' and server_id = 1
hosts = 127.0.0.1


mysql-virtual_transports.cf:
> user = ispconfig
password = ********************

dbname = dbispconfig

table = mail_transport

select_field = transport

where_field = domain

additional_conditions = and active = 'y' and server_id = 1
hosts = 127.0.0.1


with this:
> May 3 10:31:22 web amavis[13614]: (!)DENIED ACCESS from IP 192.168.0.6, policy bank ''
May 3 10:31:22 web amavis[13614]: (!)DENIED ACCESS from IP 192.168.0.6, policy bank ''

check the amavis configuration for the ip listed if that is indead your local ip for the server and see if it is in the blocked section.

---

### Post by elico on 2012-05-03
well i worked by the 12.04 TLS ISPconfig3 guide and it seems to work fine.
i had only two problems:
1. with mailman 
2. with dovecot settings to not apply correctly 

as for now i can send and recive mail.

---

### Post by KMatsumari on 2012-05-04
1. yes, I am using the 32-bit kernel system with 32-bit software.
2. I am running Oneiric Ocelot, so it all should work.
3. The missing line breaks were either caused by my duplication of the files when I copied, edited, then added them to the archive, or when your editor opened them. The originals in my postfix cf directory were never altered.
4. I bypassed the common sasl authentication errors that most people get simply by not requiring it if the connection can be performed on the loopback interface; failing the primary route forces sasl, then TLS (never happens anyway). This helps to keep the service from sapping more resources than it needs, and the connection will have the maximum throughput.
5. I have checked all of my phpmyadmin databases and tables, and nothing seems to be out of the ordinary (with exception to those that I have mentioned earlier). My user permissions do allow my server by hostname, LAN IP, and localhost to access root by the root password with all privileges (as described in the manual and guide). The user ispconfig I have upgraded to a "grant" status, and then went further and granted all privileges, but I think that is unnecessary anyways. Still no difference.
6. I just started buying more computer components, so likely I will postpone these issues until my parts arrive and I have my new system built. I am going to base install 12.04LTS 64-bit, but there doesn't seem to be a guide out for that yet. If the recommended pop and imap server is dovecot at this point, then I see no reason to use courier anymore if I can get by with no more errors. I will be using ISP Config no matter what as I have immersed myself in it completely and am already very familiar with it. I will be providing services once I can get my services running properly (all but the mail service is cooperating ATM), so I will not abandon ISPConfig for any reason (there are many success cases thus far, and the benefits outweigh the hassle, even at this point).

With that said, everyone can take a break from this for at least a week or so, and I will have a new thread if problems persist on the next system installation. I will title such a thread with "Mail service won't work in composite server". Since I have finally gotten some replies to this issue, I can drop the bounty, but it is still collectible to the user who first contributes the solution to the problem. Move on for now, I am sure I will see this problem again when I start over. Thanks for the help, and I will continue to look into what went wrong.

---

### Post by elico on 2012-05-04
you dont need to update anything.
just add a 127.0.1.1 yourdomain.com 
in the hosts file and it will fix it.
for security reasons youd better not allow any mysql external access.

good luck

---

