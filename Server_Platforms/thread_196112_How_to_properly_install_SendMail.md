---
title: "How to properly install SendMail"
date: 2006-06-13
forum: Server Platforms
---

### Post by skafiskafnjak on 2006-06-13
I used:

```
sudo apt-get install sendmail
```

It installed sendmail and by this command I could test it:

```
sudo ps aux | grep sendmail
```

Result:

> sudo ps aux | grep sendmail 
root 10366 0.0 0.7 8216 2020 ? Ss 09:50 0:00 sendmail: MTA: accepting connections 
1000 10376 0.0 0.3 2880 796 pts/0 S+ 09:56 0:00 grep sendmail

I also edited global php.ini:

> sendmail_path = /usr/sbin/sendmail

[COLOR="DarkRed"]_**Problem:**_[/COLOR]

Still my forum script does not send emails via PHP mail script that is integrated.
Yes, i restarted server!


Can anybody help?

---

### Post by skafiskafnjak on 2006-06-13
I also open ports 25 and 110 for server IP.

---

### Post by davedekker on 2006-10-09
well, If you get it figured out, you let me know..lol.. I even went as far as to beg a guru to help... very frustrated with it here... may have to switch back to my apple server if no one can set me strait

lemme know

D

---

### Post by XeviouS on 2006-11-22
I too have this exact same problem.

I have been searching the forums for a solution but to no avail.

It seems there are quite a few users with this exact same problem.

---

### Post by tturrisi on 2006-11-22
What error doe php spit out on failure?
Let's see the script.

Does your isp allow mail servers?  Most don't and most block the use of port 25, thus you would need to config sendmail as a smarthost, using the isp smtp server.  Here's an older good guide re debian & sendmail (bottom of page) but still is pretty much the same:
[http://www.aboutdebian.com/internet.htm](http://www.aboutdebian.com/internet.htm)

Myself, I prefer exim4 cause it sets up easily and quickly and is a whole lot easier to config than other MTAs.
[http://newbiedoc.sourceforge.net/networking/exim.html](http://newbiedoc.sourceforge.net/networking/exim.html)

---

### Post by bobsta63 on 2006-11-23
> **tturrisi said:**
> What error doe php spit out on failure?
Let's see the script.

Does your isp allow mail servers?  Most don't and most block the use of port 25, thus you would need to config sendmail as a smarthost, using the isp smtp server.  Here's an older good guide re debian & sendmail (bottom of page) but still is pretty much the same:
[http://www.aboutdebian.com/internet.htm](http://www.aboutdebian.com/internet.htm)

Myself, I prefer exim4 cause it sets up easily and quickly and is a whole lot easier to config than other MTAs.
[http://newbiedoc.sourceforge.net/networking/exim.html](http://newbiedoc.sourceforge.net/networking/exim.html)


This sounds good, I too need a mail server to send out emails from my website forums (phpBB) and therefore I need to use Sendmail or PHP Mail function, Exim sounds good!

Do you know If this should work out of the box and will I need to change my php.ini file?

Is there a command for APT to install Exim from Sources? for example: apt-get exim ?

Thanks in advance,

Bobby

---

### Post by tturrisi on 2006-11-23
apt-get install exim4
is the command for debian.

---

### Post by bobsta63 on 2006-11-23
Brilliant thanks buddy :)

---

### Post by XeviouS on 2006-11-24
OK I installed EXIM and my problems are solved!!!!

Thank you so much for that.

---

### Post by tturrisi on 2006-11-24
> **XeviouS said:**
> OK I installed EXIM and my problems are solved!!!!

Thank you so much for that.
You're welcome.
For years I've read so much negative stuff about exim, mostly because other MTAs are more robust, but I always liked exim, learned the basics and never had any problems w/ it.  There's are reasons exim is the default MTA in Debian!

---

### Post by MJN on 2006-11-25
> **tturrisi said:**
> There's are reasons exim is the default MTA in Debian!

Indeed, and they're not necessarily related to its ease of use! ;)

A lot of the issues are related to culture (Exim has always been the Debian default) and licensing issues (given Postfix's IBM background).

Anyway, as we should be talking Ubuntu-specific there is no default MTA anymore... however in Hoary wasn't it Postfix? Even now, the ubiqitous mail/mailx tool has a dependency on 'Postfix or A.N.Other MTA' so make of that what you will! ;)

I like Postfix but then I've never deployed Exim so can't rely say anything bad against it (not that I'd want to anyway - by all accounts it's superb).

Mathew

---

### Post by tturrisi on 2006-11-25
> Indeed, and they're not necessarily related to its ease of use!
That's for sure.  There's large books written by the developer of exim.  It's a very powerful application and often complex, but for a home server running php & using a smarthost, the setup is all of 30 seconds once apt is done.  Even if you type *dpkg-reconfigure exim4* the error message will say "use the command blah blah to configure exim4...you can't miss unless you are blind!

---

### Post by mic520 on 2007-08-06
> **skafiskafnjak said:**
> I used:

```
sudo apt-get install sendmail
```

It installed sendmail and by this command I could test it:

```
sudo ps aux | grep sendmail
```

Result:



I also edited global php.ini:



[COLOR="DarkRed"]_**Problem:**_[/COLOR]

Still my forum script does not send emails via PHP mail script that is integrated.
Yes, i restarted server!


Can anybody help?

Did you add something to sources.list before sendmail installation? I run 6.o6.1 server and got "no installation candidate error"

---

### Post by UbuNewbie123 on 2007-09-15
After installing exim, what should I change in php.ini?

---

### Post by UbuNewbie123 on 2007-09-15
Ah..

I got it to work without changing my existing php.ini.

My php.ini settings were posted here:

[http://ubuntuforums.org/showthread.php?p=3364228#post3364228](http://ubuntuforums.org/showthread.php?p=3364228#post3364228)

I installed exim4 by entering:

sudo apt-get install exim4 exim4-base exim4-config

Then I configured exim4 by entering:

sudo dpkg-reconfigure exim4-config

I think I selected one of the options to use exim4 as SMTP. I restarted my lamp server and my php mail function works.

---

### Post by UbuNewbie123 on 2007-09-15
Seems like exim works on 1 of my email addresses only.

I did more research and spent a lot of time tweaking and testing.

I edit the exim file passwd.client with my ISP's SMTP settings like:

mail.whatever.com:me@whatever.com:mypassword

I configured exim to send mail via "mail sent by smarthost; no local mail".

```
2007-09-15 23:43:57 1IWZoI-0004gB-Da ** someone@whatever.com R=smarthost T=remote_smtp_smarthost: SMTP error from remote mail server after RCPT TO:<someone@whatever.com>: host whatever.com [74.200.79.210]: 550-Verification failed for <nobody@whatever.com>\n550 Sender verify failed
2007-09-15 23:43:57 1IWZoL-0004gE-Hg <= <> R=1IWZoI-0004gB-Da U=Debian-exim P=local S=1433
2007-09-15 23:43:57 1IWZoI-0004gB-Da Completed
2007-09-15 23:44:00 1IWZoL-0004gE-Hg ** nobody@whatever.com R=smarthost T=remote_smtp_smarthost: SMTP error from remote mail server after RCPT TO:<nobody@whatever.com>: host whatever.com [74.200.79.210]: 550
2007-09-15 23:44:00 1IWZoL-0004gE-Hg Frozen (delivery error message)
```

I am trying to use my "me@whatever.com" mail account to send emails. I do not know where "**nobody@whatever.com**" came from it seems to be causing the problem "**550-Verification failed for <nobody@whatever.com>\n550 Sender verify failed**".

Any ideas to fix this problemo?

---

### Post by UbuNewbie123 on 2007-09-15
I made some changes to my exim config:

I entered “mail.whatever.com:25” into the “IP address or host name of the outgoing smarthost” field.

Same problem...

---

### Post by UbuNewbie123 on 2007-09-22
Could anyone help?

---

### Post by UbuNewbie123 on 2007-09-24
I finally solved this riddle.

You need to edit the file /etc/email-address and add the line of code:

nobody: [email]youremail@domain.com[/email]

Then I updated the exim4 settings by entering:

sudo update-exim4.conf

I restarted exim4 with the command:

sudo /etc/init.d/exim4 restart

Voila! I no longer get the [email]nobody@domain.com[/email] error messages because exim is using a real "from" address to send out emails that matches the one I specified in /etc/exim4/passwd-client.

---

### Post by Znupi on 2008-01-27
Ok here's what I had to do:

sudo apt-get install sendmail
sudo sendmailconfig (just say "Y" to all the questions)

Voila!

At first I didn't run sendmailconfig and it wouldn't work. Now I can send mails even though I have only port 80 forwarded to the server.

Maybe you didn't run sendmailconfig? :)

---

### Post by GoldWing on 2008-05-14
exim seems way better then sendmail (easier at least :) ).
This post made me realize this.
Thanks.

---

### Post by MJN on 2008-05-14
*Everything's* easier than Sendmail... ;-)

Mathew

---

### Post by CaptainMorgan on 2008-06-08
Oh my god... my php form's mail function hasn't been working for almost 8 months, largely due to the time I don't have for research on it. However, I tried everything during 7.04 and 7.10: Sendmail, Dovecot, Postfix and Mailman to name a few with *everything* failing.. I can't believe this problem is now solved for me by using Exim - THANK YOU! I'm in shock. For the love of god I have a functioning contact form!

---

