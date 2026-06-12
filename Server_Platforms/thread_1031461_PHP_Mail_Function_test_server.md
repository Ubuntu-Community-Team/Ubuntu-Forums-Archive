---
title: "PHP Mail Function test server"
date: 2009-01-05
forum: Server Platforms
---

### Post by ade234uk on 2009-01-05
I have set up a LAMP server. It looks like I can send mail using the php mail function, as both scripts I have tried report that their are no issues when sending.

However I am not getting the email at the other end. I have set up both scripts to send to my googlemail address and nothing has appeared in my inbox.

What steps do I need to take to get the mail function working properly with php so I can send emails from my LAMP SERVER.

Thank you

---

### Post by volkswagner on 2009-01-05
You need an MTA.

Check out [this]("http://ubuntuforums.org/showthread.php?t=1031171") thread for suggestions.

---

### Post by cdenley on 2009-01-05
> **ade234uk said:**
> I have set up a LAMP server. It looks like I can send mail using the php mail function, as both scripts I have tried report that their are no issues when sending.

However I am not getting the email at the other end. I have set up both scripts to send to my googlemail address and nothing has appeared in my inbox.

What steps do I need to take to get the mail function working properly with php so I can send emails from my LAMP SERVER.

Thank you

It could be blocked as spam because of a bad or suspicious DNS configuration. Check your logs. I can't tell you which log, because it depends which MTA you're using.
```

dpkg -S /usr/sbin/sendmail

```

---

### Post by karthick87 on 2010-09-24
I have the same problem pls help me..

```
karthick@Ubuntu-desktop:~$ dpkg -S /usr/sbin/sendmail
postfix: /usr/sbin/sendmail

```

---

### Post by karthick87 on 2010-09-24
Bump..!

---

### Post by SeijiSensei on 2010-09-24
Run the mailer script and generate a message to yourself, then take a look at /var/log/mail.log.  Do you see the transaction?  Any errors?

Postfix needs to be running as "daemon" process in order for mail handling to work properly.  Run "ps ax | grep postfix" and see if /usr/lib/postfix/master is running.  If not, you need to restart it by running 'sudo /etc/init.d/postfix restart'.

---

### Post by karthick87 on 2010-09-25
I get the following result..

```
karthick@Ubuntu-desktop:~$ ps ax | grep postfix
 2272 pts/0    S+     0:00 grep --color=auto [COLOR=Red]postfix[/COLOR]
```

---

### Post by SeijiSensei on 2010-09-25
Then it's not running; the entry that you see is from the process you just ran to check.  That means there's no "mail transfer agent" running on the server to accept and deliver mail.  Try running 

sudo /etc/init.d/postfix start

then try your script again.

---

### Post by karthick87 on 2010-09-25
```
karthick@Ubuntu-desktop:~$ ps ax | grep postfix
 2641 ?        Ss     0:00 /usr/lib/[COLOR=Red]postfix[/COLOR]/master
 2701 pts/0    S+     0:00 grep --color=auto[COLOR=Red] postfix[/COLOR]
karthick@Ubuntu-desktop:~$ sudo /etc/init.d/postfix status
 * postfix is running

```What next..?

---

### Post by SeijiSensei on 2010-09-25
Like I said, run the PHP script that generated the problem in the first place.  I presume you bumped this thread because you had some PHP code which didn't successfully mail the message your expected.  Try it again now that postfix is installed, and see if it works.

---

### Post by karthick87 on 2010-09-25
Still its not going.I am sending it from localhost,is it wrong?If so pls correct me.

---

### Post by SeijiSensei on 2010-09-25
1)  Do you see an entry in /var/log/mail.log that corresponds to your test?

2)  Here's another way to test; you'll probably need to add the mailx package, though, with 'sudo apt-get install bsd-mailx'.  Once it's installed, from the Terminal first run a command like

echo 'this is a test' | mail -s 'testing' you@localhost

replacing 'you' with your local username.  Now try sending to a remote mailbox by replacing 'you@localhost' with an off-site address. 

Do these messages appear in your mailboxes?  What do you see in /var/log/mail.log?

3)  Is your server connected to the Internet via a "business-class" connection, or are you using a consumer provider like a cable service?  If the latter, your computer may be blocked from sending SMTP traffic to remote servers over port 25.  (This is a common ISP practice nowadays because of the millions of infected Windows computers that have been turned into spambots.)  You'll need to ask the ISP for a dispensation to allow you to send SMTP traffic.

You should be able to tell from mail.log whether the second test to a remote server went through or not.  The log will have an entry with "status=sent" if it went through, or an error if it did not.

---

### Post by karthick87 on 2010-09-25
[COLOR=Red]Mail.log
[/COLOR]
Sep 25 09:21:16 Ubuntu-desktop postfix/local[2287]: 5C06F180FE4: to=<karthick@Ubuntu-desktop>, relay=local, delay=0.16, delays=0.07/0/0/0.09, dsn=2.0.0, status=sent (delivered to mailbox)

---

### Post by SeijiSensei on 2010-09-25
OK, but what about the one sent to a remote server?  

If you run your script with karthick@Ubuntu-desktop as the To address, does it work?

I'll just say that I wouldn't forward mail from a script like the one you posted because it has an enormous security hole, in particular, letting the user designate a From address.  Many ISPs have quite specific rules about what domains they'll forward mail from for good reason.  I have hundreds of entries in my incoming mail logs from spambots using random From addresses being pushed through uncontrolled SMTP servers.  Telling the user "WARNING: Use it at your own risk. Do not use this for Spamming!" assumes you don't have malicious users.  That's definitely a bad assumption to be making when it comes to the Internet.  That's why so many ISPs have had to block traffic on SMTP port 25.

---

### Post by karthick87 on 2010-09-25
Then what do you use..?Whats the solution..?Is it possible to use this script..?

---

### Post by SeijiSensei on 2010-09-25
You still haven't answered my question; what happened when you try to send offsite?

As for your second question, what is the point of this script anyway?  I don't see much purpose for something entitled "Fake Email Prank Script By Srikanth" with the exhortation "Please do not misuse this script. Use it only for having FUN." You can't just put a form out on the Internet that random people might use for spamming.  What exactly are you trying to accomplish with this?

Try this script:

```

<?php
$to="you@example.com";
$from="From: you@example.com";
$msg="Hi there, karthick";
$subj="Test message";

mail($to,$subject,$msg,$from);

exit;
?>
```

Replace "you@example.com" with your email address in both cases.  Try running the script from the command line if you have php5-cli installed:

php -q /path/to/the/script

What happens?

---

### Post by karthick87 on 2010-09-26
I have saved your script as mail.php in my desktop and this is the output..

```
karthick@Ubuntu-desktop:~/Desktop$ php -q mail.php
PHP Notice:  Undefined variable: subject in /home/karthick/Desktop/mail.php on line 7
```

and this is the log when i send it to offsite..

```
Sep 25 23:08:29 Ubuntu-desktop postfix/smtp[2616]: 31569180FB5: to=<XXXX@gmail.com>, relay=gmail-smtp-in.l.google.com[74.125.155.27]:25, delay=5.5, delays=0.12/0/1.2/4.2, dsn=5.7.1, status=bounced (host gmail-smtp-in.l.google.com[74.125.155.27] said: 550-5.7.1 [117.206.89.135] The IP you're using to send mail is not authorized to 550-5.7.1 send email directly to our servers. Please use the SMTP relay at your 550-5.7.1 service provider instead. Learn more at                          550 5.7.1 http://mail.google.com/support/bin/answer.py?answer=10336 w26si10048544wah.104 (in reply to end of DATA command))
```

---

### Post by BkkBonanza on 2010-09-26
When you get tired of trying to bend the **mail** function to work... I'd suggest using a PHP smtp class to send mail. It talks directly to your mail account and avoids local installing any mta software on your system, and the hassles of blocks etc. It just sends mail the way your regular mail program (Thunderbird) would. There's heaps of classes around the web. The one I've used for over 6 years works fine but I don't remember where I originally got it. If you want mine I can post it. It's only about 30k. I have a pop3 class too, for checking mail.

Typical use of smtp class:

```
$smtp = new phpmailer();

$smtp->host("hotmail.com", 25, userid, passwd); 
// can also do host("ssl://gmail.com", 465, user, pwd) to use ssl

$smtp->mail($to, $subject, $body, $from, $realname);
```

---

### Post by karthick87 on 2010-09-26
> **BkkBonanza said:**
> When you get tired of trying to bend the **mail** function to work... I'd suggest using a PHP smtp class to send mail. It talks directly to your mail account and avoids local installing any mta software on your system, and the hassles of blocks etc. It just sends mail the way your regular mail program (Thunderbird) would. There's heaps of classes around the web. The one I've used for over 6 years works fine but I don't remember where I originally got it. If you want mine I can post it. It's only about 30k. I have a pop3 class too, for checking mail.

Typical use of smtp class:

```
$smtp = new phpmailer();

$smtp->host("hotmail.com", 25, userid, passwd); 
// can also do host("ssl://gmail.com", 465, user, pwd) to use ssl

$smtp->mail($to, $subject, $body, $from, $realname);
```

Can you pls post yours..

---

### Post by BkkBonanza on 2010-09-26
Here's a tar archive with my 3 files. I found these years ago when programming my site and have used them reliably since for many thousands of emails. 

You'll see I added some code to support html multipart/alternative. I needed that at the time and it didn't do it. 

Of course, they're not "mine" - each has headers with info from original authors.

Any questions just ask... or pm me.

Don't forget to change the owner/group to match your web server user.

---

### Post by VcDeveloper on 2010-09-26
Hi everyone, I have a question.  How do I test to see if port 25 is being blocked without asking AT&T (this is my ISP)?.  I have Postfix and dovecot installed and when I sent a test email using Evolution Mail I get these messages:

```
Sep 26 07:14:18 anointed postfix/qmgr[13227]: 02EC361DB5: from=<support@mydomain.com>, size=765, nrcpt=1 (queue active)
Sep 26 07:14:48 anointed postfix/smtp[13849]: connect to k.mx.mail.yahoo.com[98.139.54.60]:25: Connection timed out
Sep 26 07:15:18 anointed postfix/smtp[13849]: connect to e.mx.mail.yahoo.com[67.195.168.230]:25: Connection timed out
Sep 26 07:15:49 anointed postfix/smtp[13849]: connect to g.mx.mail.yahoo.com[98.137.54.238]:25: Connection timed out
Sep 26 07:16:19 anointed postfix/smtp[13849]: connect to i.mx.mail.yahoo.com[74.6.140.64]:25: Connection timed out
Sep 26 07:16:49 anointed postfix/smtp[13849]: connect to h.mx.mail.yahoo.com[66.94.236.34]:25: Connection timed out
Sep 26 07:16:49 anointed postfix/smtp[13849]: 02EC361DB5: to=<name@yahoo.com>, relay=none, delay=130661, delays=130510/0.03/151/0, dsn=4.4.1, status=deferred (connect to h.mx.mail.yahoo.com[66.94.236.34]:25: Connection timed out)

```

or what other test can I do to find out why the connection is timing out?

---

### Post by karthick87 on 2010-09-27
Goto terminal and type the following,

[COLOR=Red]telnet mail.yourdomainname.com 25[/COLOR]

what do you get..?

---

### Post by VcDeveloper on 2010-09-27
Before I go live on the internet I'm setting up a dev network using Virtural Machine Manager on a VT kvm server. My dev network structure looks like this:

```
Ubuntu 10.04 LTS (Main Server, anointed.server1.com) VT, Kvm:
--------| Virtual Machine Manager w/4 VM's, Static IP's
-------------------| VM1 Ubuntu 9.04 Karmic (Drupal 6.19 CMS, anointed.webserver.p1) Live
-------------------| VM2 Ubuntu 9.04 Karmic (MySQL Database, anointed.mysqlserver.p1) Live
-------------------| VM3 Ubuntu 9.04 Karmic (Postfix, Dovecot, anointed.mailserver.p1) Live
-------------------| VM4 Ubuntu 9.04 Karmic (DMZ, anointed.dmzserver.p1) Dev

```My DMZ Server is my dev server and I have (Drupal, MySQL and Postfix, Dovecot) all installed and this is where I'm tring to get everything working first before configuring the live servers.  All servers can connect to the internet.  I'm using AT&T as my ISP with a 2wire router w/NAT.  All standard outgoing ports are open and incoming ports are closed.  When I go live I will be opening only port 80.  I only want to be able to send mail locally and to the internet when I go live.

I can connect to my DMZ from anointed.server1.com and anointed.webserver.p1 with telnet successfuly.  From with in DMZ I can connect successfully using "anointed.dmzserver.p1 25" but not with "mail.dmzserver.p1 25".  But I only get:

sysadmin@anointed:~$ telnet anointed.dmzserver.p1 25
Trying 127.0.0.1...
Connected to anointed.dmzserver.p1.
Escape character is '^]'.
220 anointed.dmzserver.p1 ESMTP Postfix (Ubuntu)

...BUT no "telnet>" prompt

---

### Post by VcDeveloper on 2010-09-27
I also tried this reply too [**configuring postfix send and receive across ethernet**]("http://ubuntuforums.org/showthread.php?t=1583111&highlight=port+25")

sysadmin@anointed:~$ telnet gmail-smtp-in.l.google.com 25
Trying 72.14.213.27...
telnet: Unable to connect to remote host: Connection timed out

from the DMZ server.... So, I'm assuming AT&T is blocking my outbound port 25?

---

### Post by BkkBonanza on 2010-09-27
Isn't gmail completely SSL now? I don't think they support regular pop3 any more. You would have to use SSL and connect to port 465.

Scratch that - I just did a port check on that address and port 25 is open, so you shouldn't get a timeout there unless you have a firewall or something blocking you.

It appears for SSL on port 465 the smtp.gmail.com address is used.

---

### Post by SeijiSensei on 2010-09-27
> **BkkBonanza said:**
> Isn't gmail completely SSL now? I don't think they support regular pop3 any more. You would have to use SSL and connect to port 465.

I wrote that suggestion in the other thread.  The server in question is one of Google's inbound SMTP servers.  I extracted it from my mail server logs and tested it just to make sure.

I think he's blocked.

---

### Post by VcDeveloper on 2010-09-27
Uhmmmm... this interesting, becuase I set my AT&T 2Wire Router firewall for the DMZ server as the the DMZmode Zone which open all ports.  And when I di, d a port scan through GRC with a Stealth level rating.  , BUT when I scan from the main server the ports 25, 80, 110, 139, 143, 445, 993, 995, 2000 and 3306 is open.

Not using any fire on this server. Do I need to use one to open these ports to the internet?

---

### Post by BkkBonanza on 2010-09-28
Scanning your computer/router (from outside, like GRC) has nothing to do with outgoing ports. 

You would have to scan from your computer to an outside computer using nmap to see what ports your ISP blocks, and you would need to be sure the one you scan has the ports open to be sure it's the ISP blocking you. Also you would have tobe certain you aren't blocking yourself with an internal firewall like UFW.

Makes sure **sudo iptables -L** returns all flushed and ACCEPT for each chain, on your computer to be certain you aren't blocking yourself. Do an nmap scan on your own router to be sure it isn't blocking you going out. After that, I'd be fairly certain your ISP is blocking you.

If so, then check port 465 because if it's open you could use SSL instead (which is actually far preferred anyway). You don't really want your ISP or anyone filtering your mail... so SSL will limit that ability.

---

### Post by VcDeveloper on 2010-09-28
Thanks for your reply!  I found the problem!  After selecting DMZmode it didn't apply because my server needed to be dynamic.  So I just open the ports I wanted and now I'm getting the open hits from GRC.

---

