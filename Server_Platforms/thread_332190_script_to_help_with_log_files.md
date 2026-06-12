---
title: "script to help with log files"
date: 2007-01-05
forum: Server Platforms
---

### Post by sailingboarder on 2007-01-05
I have just set up a lamp server on my old comp, and added ftp support so that i would not need to touch the machine on most days

i was wondering if someone could point me in the right dirrection of(or write) a simple script that would daily email me a copy of the major log files(for apache, vsftpd, the system in general, etc.). This way, I could easily see the log files from my other comp, and not have to remember to check them.

i would really appreciate any help or ideas

---

### Post by kidders on 2007-01-05
Hi there,

I suppose the kind of thing you're after is **grep "`date +"%a %b %d"`" /var/log/apache2/error.log | sendmail whoever** ... (assuming, of course that your log files' date format is along the lines of "Fri Jan 05", and the command runs at two or three seconds before midnight).

It would certainly make for mind-numbing reading though ... do you suppose there's a way you could filter for "interesting" messages?

---

### Post by sailingboarder on 2007-01-05
this is my first venture into servers, and so i was just thinking that i should probably observe the server just to make sure nothing was happening that shouldn't be, and maybe see if anyone was actually visiting it

if i should be filtering it, i would love some advice on how/what i should filter

---

### Post by MJN on 2007-01-05
Install **logwatch** - this will pick out the most important aspects from the logs every day, format them neatly and send you a nice e-mail. Any entries it doesn't recognise (and hence which could have the potential to be serious) also get notified to you (as 'unrecognised' hence make your own mind up whether they're important or not). It also goes further than just parsing logs, but also compiles other statistical data such as web server traffic counts, mail counters etc.

Mathew

---

### Post by kidders on 2007-01-05
Hey again,

Sorry, I didn't mean to sound critical ... it's just that, if it were me, I'd prefer to receive log summaries by email only if there was something worth reading. What to consider worthwhile is a matter of personal taste, really.

For instance, you might decide that you only want...

[LIST]
[*]Lines from /var/log/auth.log containing the words "invalid" or "failed".
[*]Lines from /var/log/apache2/error.log that contain "/usr/lib/cgi-bin".
[*]Lines from /var/log/mail.log with "NOQUEUE" in them.
[/LIST]

On the other hand, there's the blunderbuss approach. You could mail the entire contents of /var/log to yourself with a "for" loop, record all the file sizes with something like **du -aSD --exclude="*.gz" /var/log > /tmp/whatever.tmp**, and next time around, only mail yourself the new bits in a sort of a "tail -c (newSize-oldSize) /var/log/filename.log" way.

In any case, whatever you'd like to do, I'd be happy to help.

**Edit:** Like MJN says though, something like logwatch is far cleaner ... especially if whatever you end up doing goes beyond a certain level of complexity. No need to re-invent the wheel!

---

### Post by eric_stewart on 2007-01-05
> **kidders said:**
> Hey again,

Sorry, I didn't mean to sound critical ... it's just that, if it were me, I'd prefer to receive log summaries by email only if there was something worth reading. What to consider worthwhile is a matter of personal taste, really.

For instance, you might decide that you only want...

[LIST]
[*]Lines from /var/log/auth.log containing the words "invalid" or "failed".
[*]Lines from /var/log/apache2/error.log that contain "/usr/lib/cgi-bin".
[*]Lines from /var/log/mail.log with "NOQUEUE" in them.
[/LIST]

On the other hand, there's the blunderbuss approach. You could mail the entire contents of /var/log to yourself with a "for" loop, record all the file sizes with something like **du -aSD --exclude="*.gz" /var/log > /tmp/whatever.tmp**, and next time around, only mail yourself the new bits in a sort of a "tail -c (newSize-oldSize) /var/log/filename.log" way.

In any case, whatever you'd like to do, I'd be happy to help.

**Edit:** Like MJN says though, something like logwatch is far cleaner ... especially if whatever you end up doing goes beyond a certain level of complexity. No need to re-invent the wheel!


Actually, logcheck is *very* configurable.  In the /etc/logcheck directory, there are several directories, inside which are files that contain RE-based scripts which define what to check for, what to ignore, what to report, etc.....  

root@mail:/etc/logcheck# ls -al
total 52
drwxr-xr-x   9 root logcheck 4096 2007-01-05 20:52 .
drwxr-xr-x 161 root root     8192 2007-01-05 19:35 ..
drwxr-s---   2 root logcheck 4096 2007-01-02 09:48 cracking.d
drwxr-s---   2 root logcheck 4096 2006-07-11 12:48 cracking.ignore.d
-rw-r--r--   1 root logcheck  180 2004-04-19 14:22 header.txt
drwxr-s---   2 root logcheck 4096 2007-01-02 09:48 ignore.d.paranoid
drwxr-s---   2 root logcheck 4096 2007-01-05 20:54 ignore.d.server
drwxr-s---   2 root logcheck 4096 2007-01-02 09:48 ignore.d.workstation
-rw-r-----   1 root logcheck 1940 2006-07-11 12:48 logcheck.conf
-rw-r-----   1 root logcheck  131 2006-07-11 12:48 logcheck.logfiles
drwxr-s---   2 root logcheck 4096 2007-01-02 09:48 violations.d
drwxr-s---   2 root logcheck 4096 2007-01-02 09:48 violations.ignore.d

There are also a number of command line options.

Here's a short excerpt from the man page:
DESCRIPTION
       The  logcheck  program  helps  spot problems and security violations in
       your logfiles automatically and will send the results to  you  periodiâ[m
       cally  in an e-mail. By default logcheck runs as an hourly cronjob just
       off the hour and after every reboot.

       logcheck supports three level of filtering:  "paranoid"  is  for  high-
       security  machines running as few services as possible. Donât use it if
       you canât handle its verbose messages.  "server"  is  the  default  and
       contains  rules for many different daemons.  "workstation" is for shelâ[m
       tered machines and filters most of the messages.  The ignore rules work
       in  additive  manner.  "paranoid"  rules  are  also  included  at level
       "server" and "workstation".

       The messages reported are sorted  into  three  layers,  system  events,
       security  events  and  attack alerts. The verbosity of system events is
       controlled by which level you choose, paranoid, server or  workstation.
       However, security events and attack alerts are not affected by this.

Anyway...thought I'd share.  I'm using logcheck, in conjunction with syslog-ng, wflogs and the SNORT IDS to notify me of network attacks as well as system level events that need my attention.  Search for the relevant terms on [www.breezy.ca](www.breezy.ca).  There are some interesting links there.  I think if you look at the posts you can see how this might be integrated.

/Eric
webmaster (hobby) [www.breezy.ca](www.breezy.ca)  <-- Linux, Network Security & Cisco Information
Ottawa, Canada

---

### Post by sailingboarder on 2007-01-06
thankyou all for the help

i think logwatch is exactly wut i was looking for...so i'll give it a try

---

### Post by eric_stewart on 2007-01-07
> **sailingboarder said:**
> thankyou all for the help

i think logwatch is exactly wut i was looking for...so i'll give it a try

Probably it's a good fit for what you are doing.  It really is plug 'n play in that a straight install of the Ubuntu package via either apt-get at the command line or using the Synaptic Package Manager will set logcheck up to immediately start parsing your logs hourly and sending messages with different alert categories to the root user.

Please let us know what you think of it after you've installed it.  Also please consider posting at [www.breezy.ca](www.breezy.ca)  We'd love to hear from you there, too!

/Eric

---

### Post by MJN on 2007-01-08
Just to clarify though; **logwatch** and **logcheck** are two completely seperate applications/tools with slightly different purposes and goals.

Mathew

---

### Post by eric_stewart on 2007-01-08
> **MJN said:**
> Just to clarify though; **logwatch** and **logcheck** are two completely seperate applications/tools with slightly different purposes and goals.

Mathew
Ooops.  Good catch.  log*watch* doesn't equal log*check*!!  

....I still like logcheck...

---

### Post by sailingboarder on 2007-01-08
> **eric_stewart said:**
>  parsing your logs hourly and sending messages with different alert categories to the root user.
Does it send the messages to the root user, or email, or both? I really would like email, not just messages on the system.

> **MJN said:**
> Just to clarify though; **logwatch** and **logcheck** are two completely seperate applications/tools with slightly different purposes and goals.

Mathew
What is the difference between logwatch and logcheck?

---

### Post by MJN on 2007-01-08
Read the manpages! ;)

Logwatch: [http://www.die.net/doc/linux/man/man8/logwatch.8.html](http://www.die.net/doc/linux/man/man8/logwatch.8.html)
Logcheck: [http://www.penguin-soft.com/penguin/man/8/logcheck.html](http://www.penguin-soft.com/penguin/man/8/logcheck.html)

However, admittedly these manpages don't help all that much!

On the face of it they're aiming at satisfying different requirements - Log*check* is very much geared towards spotting security violations whereas Log*watch* is more tailored for summarising system events/issues but also includes anything amiss security-wise.

I'd say Logwatch was far more mature but that's not to diss Logcheck - I've never used it.

Your best, if indeed only, bet would be install them both and see what you think of each. Only you can know what you really want. They should work straight out of the box - install them and wait a couple of days... in the meantime you should hopefully have received a couple of summarised e-mails (Logwatch will send you one every day, at the time your Cron.daily tasks fire off).

Mathew

---

### Post by eric_stewart on 2007-01-08
> **sailingboarder said:**
> Does it send the messages to the root user, or email, or both? I really would like email, not just messages on the system.

What is the difference between logwatch and logcheck?

Answer 1:  It sends an email to the root user

Answer 2:  Nicely answered in a separate post by MJN!  

/Eric

---

### Post by sailingboarder on 2007-01-09
> **eric_stewart said:**
> Answer 1:  It sends an email to the root user

If I want it to send an email to a separate email address, [email]me@wutever.com[/email], can it do that?
this question goes to both logWATCH and logCHECK

---

### Post by MJN on 2007-01-09
You really need to install them - it will take a couple of minutes tops. Then you'll be able to answer all these questions, and more, yourself! :)

Mathew

---

### Post by sailingboarder on 2007-01-10
i think logwatch was more wut i was looking for, but since i couldn't find in using apt-get, i settled for logcheck
edited the conf file to email to my address, so now i just have to wait and see how i like it
thanks for the help

---

### Post by MJN on 2007-01-10
Logwatch is in the multiverse repository (see [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) for details of how to add repositories).

I would recommend that you try it, as you might find you actually want *both* installed (given they serve different purposes as discussed).

Mathew

---

