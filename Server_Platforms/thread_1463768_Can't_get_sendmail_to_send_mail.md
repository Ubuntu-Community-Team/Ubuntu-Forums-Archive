---
title: "Can't get sendmail to send mail"
date: 2010-04-27
forum: Server Platforms
---

### Post by kennyrbr on 2010-04-27
I am running Ubuntu Server 9.10 as a virtual machine using VirtualBox. 

I am wanting to set up sendmail so I can use this with some Joomla development I test using this virtual machine web server setup. All I need is to send emails.  

I understand that sendmail should be pretty straight-forward to set up, but I can't seem to get it to work. 

I followed instructions here [http://ubuntuforums.org/showthread.php?t=1343651]("http://ubuntuforums.org/showthread.php?t=1343651"). 

I installed sendmail and restarted apache
> 
kennyb@ubuntu:~$ sudo apt-get install sendmail
kennyb@ubuntu:~$ sudo /etc/init.d/apache2 restart


Performing: 
> 
sudo ps aux | grep sendmail


gives the result.
> 
root      6589  0.0  0.2  94120  2716 ?        Ss   01:21   0:00 sendmail: MTA: accepting connections


I also performed (choosing Y for all options)
> 
sudo sendmailconfig


When configuring for /etc/mail/sendmail.mc, I get the following message. Other that that, it goes through fine. 
> 
Creating /etc/mail/sasl/sasl.m4...

Ah, you're setup with SASL2 !

Unfortunately, there is no automagic way to migrate to /etc/sasldb2 :(

You'll want to make sure /etc/default/saslauthd is setup to start,
and has at least MECHANISMS="pam" !

If you find out what more is needed, please let me know!


I did: 
> 
ps aux | grep sas


with the result: 
> 
root      1253  0.0  0.0  53420   968 ?        Ss   Apr27   0:00 /usr/sbin/saslauthd -a pam -m /var/spool/postfix/var/run/saslauthd -r
root      1254  0.0  0.0  53420   556 ?        S    Apr27   0:00 /usr/sbin/saslauthd -a pam -m /var/spool/postfix/var/run/saslauthd -r
root      1255  0.0  0.0  53420   552 ?        S    Apr27   0:00 /usr/sbin/saslauthd -a pam -m /var/spool/postfix/var/run/saslauthd -r
root      1256  0.0  0.0  53420   552 ?        S    Apr27   0:00 /usr/sbin/saslauthd -a pam -m /var/spool/postfix/var/run/saslauthd -r
root      1257  0.0  0.0  53420   552 ?        S    Apr27   0:00 /usr/sbin/saslauthd -a pam -m /var/spool/postfix/var/run/saslauthd -r



I don't receive an email when I test with (or with other addresses):
> 
kennyb@ubuntu:~$ mail [email]kenn@mydomain.com.au[/email] < test.file
 

When I do:
> 
kennyb@ubuntu:/var/log$ tail mail.log


I can see the following (showing the last line):

> 
Apr 28 01:41:37 ubuntu sm-mta[6691]: o3Q1uxhS002622: to=<kenn@mydomain.com.au>, ctladdr=<www-data@ubuntu.Belkin> (33/33), delay=1+13:44:38, xdelay=00:00:00, mailer=esmtp, pri=7860702, relay=mydomain.com.au., dsn=4.0.0, stat=Deferred: mydomain.com.au.: No route to host


My /etc/hosts contains
> 
27.0.0.1 localhost
127.0.1.1 ubuntu.Belkin ubuntu


Can anyone see something/s I'm doing wrong?

---

### Post by kennyrbr on 2010-04-27
I also did the following. Am thinking that the 'No UCE/UBE' isn't good, but am not really understanding posts I find with a web search on this. 

> 
kennyb@ubuntu:/etc/default$ telnet 127.0.0.1 25
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
220 ubuntu.Belkin ESMTP Sendmail 8.14.3/8.14.3/Debian-9ubuntu1; Wed, 28 Apr 2010 02:15:51 +1000; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]


Obviously I'm new to linux / ubuntu. 

Loving the local web development environment through VirtualBox and Ubuntu, but am a bit stuck on this mail thing...

---

### Post by Bachstelze on 2010-04-27
> Apr 28 01:41:37 ubuntu sm-mta[6691]: o3Q1uxhS002622: to=<kenn@mydomain.com.au>, ctladdr=<www-data@ubuntu.Belkin> (33/33), delay=1+13:44:38, xdelay=00:00:00, mailer=esmtp, pri=7860702, relay=mydomain.com.au., dsn=4.0.0, stat=Deferred: **mydomain.com.au.: No route to host**

Either the source or destination domain (or both) doesn't resolve. Obviously, ubuntu.Belkin doesn't. You have to give your machine a real hostname in a real domain if you want to send mail that way.

---

