---
title: "how to parse a postfix log and insert into a database"
date: 2014-12-24
forum: Server Platforms
---

### Post by avinash7 on 2014-12-24
Hi 

I user postfix server for the email campaign purpose. I'm unable to send judge the emails which are hard bounce and soft bounce for the emails I have sent.

Is there any procedure to get the status for the email id's which I used to send a campaign through the postfix server.

I ll be appreciated if any one can solve the problem.

---

### Post by Sef on 2014-12-26
1) Moved to server platform.
2) What version of Ubuntu are you running?

---

### Post by TheFu on 2014-12-26
> **avinash7 said:**
> Hi 

I user postfix server for the email campaign purpose. I'm unable to send judge the emails which are hard bounce and soft bounce for the emails I have sent.

Is there any procedure to get the status for the email id's which I used to send a campaign through the postfix server.

I ll be appreciated if any one can solve the problem.

Bounced emails are usually due to the sender not being configured as a non-spam server.  That means having a static IP, using forward and reverse DNS and not getting caught by anti-spammer services as a spammer.  My email servers use a few anti-spam servers and bounce about 90% of all email sent - because the actual sender is NOT from the domain claiming to be sending the emails.  Then we use a few different services which watch for spammers in real-time and refuse email from those.  Sometimes gmail and yahoo mail are included in those sources, so we bounce email from them as well.

Postfix will try to resend soft-bounced messages later, automatically.  More and more people have found that spammers only try to send once and never again. This is an easy way to drastically prevent spam.  I've also found that spammers will not use the primary MX server, preferring the secondary and tertiary servers instead even when the primary is available.

So ... I don't really understand how the title relates to the question. Could you explain more?

---

### Post by avinash7 on 2015-01-02
Thanks for replying 

I Need to parse the postfix log file which is located at "/var/log/mail.log" collect all the bounce email addresses and insert into mysql database . I'm using 14.04 ubuntu VPS

---

### Post by avinash7 on 2015-01-02
[COLOR=#000000]Thanks for replying [/COLOR]

[COLOR=#000000]I Need to parse the postfix log file which is located at "/var/log/mail.log" collect all the bounce email addresses and insert into mysql database . I'm using 14.04 ubuntu VPS[/COLOR]

---

### Post by lisati on 2015-01-02
What mailing list software are you using? Some software, e.g. mailman, can be set to process bounces automatically without the need to scan the logs.

It is also possible to have postfix send copies of bounce information to a dedicated mailbox which can then be accessed like a regular mailbox. This can be done by setting the [notify_classes](http://www.postfix.org/postconf.5.html#notify_classes) parameter to include "bounce". The default is to send the bounce information to postmaster, but it can be set to any mailbox you choose with the [bounce_notice_recipient](http://www.postfix.org/postconf.5.html#bounce_notice_recipient)parameter.

---

### Post by avinash7 on 2015-01-02
I'm Using Postfix is there another way to process bounce without [bounce_notice_recipient]("http://www.postfix.org/postconf.5.html#bounce_notice_recipient") [COLOR=#000000]parameter. just I need the email ID's that's it[/COLOR]

---

### Post by lisati on 2015-01-02
Your mailing list software, if it's any good, *should* be processing the bounces. You could always write your own software to read and analyse the log file.

---

### Post by avinash7 on 2015-01-02
I'm a mass mailer I send daily 100000 mails from my postfix server some of them were hard bounce and other are soft bounce I need a tool for the postfix which tracks a emails which I sent are bounce and which are valid . Is there any tool.

---

### Post by lisati on 2015-01-02
> **avinash7 said:**
> I'm a mass mailer I send daily 100000 mails from my postfix server some of them were hard bounce and other are soft bounce I need a tool for the postfix which tracks a emails which I sent are bounce and which are valid . Is there any tool.

Doesn't your mass mailing software do that for you? What mass mailing software do you use?

---

### Post by avinash7 on 2015-01-02
I Just install Postfix and I send Emails from interspire tool

---

### Post by avinash7 on 2015-01-02
> **lisati said:**
> Doesn't your mass mailing software do that for you? What mass mailing software do you use?


I just install a Postfix software and I USE interspire tool to send mails or through a php script.

---

### Post by lisati on 2015-01-02
According to the Interspire website, their mass email software automates bounce handling.

Blindly sending out emails through a PHP script is NOT a good idea, particularly if you do not have consent from the potential recipients for receiving email from you. You could easily get labelled as a spammer.

---

### Post by avinash7 on 2015-01-02
> **lisati said:**
> According to the Interspire website, their mass email software automates bounce handling.

Blindly sending out emails through a PHP script is NOT a good idea, particularly if you do not have consent from the potential recipients for receiving email from you. You could easily get labelled as a spammer.

Please tell me which mail software is best to handle bounce for mass mailling in postfix.

---

### Post by lisati on 2015-01-02
You might want to consider replacing whatever it is you're using with [mailman]("https://help.ubuntu.com/lts/serverguide/mailman.html") or listserv, both of which can handle bounce processing.

---

### Post by niconux2 on 2015-01-28
If you're looking for a way to get Postfix logs in a database, then using a tool to query it and investigate any email crossing your Postfix servers, you might be interested by a project hosted on Sourceforge, here is a link on the wiki pages: [https://sourceforge.net/p/x-itools/wiki/Home/](https://sourceforge.net/p/x-itools/wiki/Home/)

There is also a Virtual Machine available...

---

### Post by SeijiSensei on 2015-01-28
Can you write scripts in a language like Python or PHP?  I use the latter to parse logs and post the results to PostgreSQL databases.

Otherwise you can try using a combination of grep and awk at the command line.  Use grep to pick the lines that contain the text that identifies the bounces, then pipe the result to awk and let it split the line into tokens and "print" the appropriate field to a file.  

For instance, here's a line from my sendmail logs (I don't use Postfix):
```

Jan 28 09:09:06 mail sendmail[18086]: t0SE95bQ018084: to=<user@example.com>, delay=00:00:01, xdelay=00:00:01, mailer=relay, pri=133388, relay=[10.1.1.1] [10.1.1.1], dsn=2.0.0, stat=Sent (t0SE96fl014273 Message accepted for delivery)

```
If I wanted to extract the email address for sent messages, I'd use this:
```

grep 'stat=Sent' /var/log/mail.log | awk '{print $7}' | sed 's/to=<//g' | sed 's/>,//g'

```
which will return "user@example.com".

---

### Post by TheFu on 2015-01-28
Or in perl:

```
#!/usr/bin/env perl

NEXT:
while (<>){
   chomp;
   next NEXT if ( ! m/to=/o );
   my @line = split(/[<>]/ );
   my $to = $line[1];
   print "$to\n";

}

```
will return the TO: email addresses too. Should be faster than the shell/awk solution, especially for large log files. But this stuff runs so fast it doesn't matter.

---

