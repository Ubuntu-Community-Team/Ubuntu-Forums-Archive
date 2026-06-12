---
title: "Configuring Denyhosts to use SendMail/Postfix"
date: 2009-10-11
forum: Security
---

### Post by jeffs99 on 2009-10-11
My sendmail/postfix is presently configured to use gmail and it seems to work fine.
 
I enter 'sendmail [email]xxx@xxx.com[/email]' , type the email and send and the email goes through fine with the email coming from a gamil acct.
 
Now I have denyhosts working fine except for the sending mail part.
 
How do I configure denyhosts to use the sendmail/postfix?
I skipped the SMTP settings parts figuring I'm not actually using an SMTP server rather the Ubuntu built in email.
 
What am I doing wrong?
 
Help appreciated.
 
Thanks
Jeff

---

### Post by Lars Noodén on 2009-10-12
It's hard to guess without knowing what daemon you want to booby trap with hosts.deny

If this works in the shell:
[INDENT][FONT="Courier New"]date -u | /usr/bin/mail -s Yo.  A Test [email]xxx@xxx.com[/email][/FONT][/INDENT]

Then this should would inside hosts.deny:

[INDENT][FONT="Courier New"]
sshd: ALL: (/usr/sbin/traceroute -n %h | \
               /usr/bin/mail -s SSHd %d-%h [email]xxx@xxx.com[/email]) &
[/FONT][/INDENT]

---

### Post by jeffs99 on 2009-10-15
Thanks for the info, but what I meant was how do I configure DenyHosts via the /etc/DenyHosts.conf file. There are sections within this file that are used for configuring the email to send out any time a new host is added to the hosts.deny file.
Bu these sections mostly referencing SMTP mailer which I don't think is what I am using since I'm using postfix/send mail.
 
Any new info appreciated.
 
Thanks 
 
> **Lars Noodén said:**
> It's hard to guess without knowing what daemon you want to booby trap with hosts.deny
 
If this works in the shell:
[INDENT][FONT=Courier New]date -u |*/usr/bin/mail -s Yo. A Test [EMAIL="xxx@xxx.com"]xxx@xxx.com[/EMAIL][/FONT]
[/INDENT]Then this should would inside hosts.deny:
[INDENT][FONT=Courier New]sshd: ALL: (/usr/sbin/traceroute -n %h | \[/FONT]
[FONT=Courier New]/usr/bin/mail -s SSHd %d-%h [EMAIL="xxx@xxx.com"]xxx@xxx.com[/EMAIL]) &[/FONT]
[/INDENT]

---

### Post by Lars Noodén on 2009-10-18
> **jeffs99 said:**
> Thanks for the info, but what I meant was how do I configure DenyHosts via the /etc/DenyHosts.conf file. 

Some comments to myself: 

DenyHosts (as opposed to tcpd aka tcpwrappers, which uses the file /etc/hosts.deny) scans ssh logs and based on the configurations in /etc/denyhosts.conf will add offenders to tcpd's /etc/hosts.deny

The documentation for denyhosts configuration is more or less missing.  There is a FAQ that the program's manual points to, but nothing explicitly for the configuration file.  

> **jeffs99 said:**
> There are sections within this file that are used for configuring the email to send out any time a new host is added to the hosts.deny file.

@jeffs : SMTP is what postfix, and all other mail servers, uses to receive and send mail.  DenyHosts seems to use the built-in python mail client in the python module smtplib.  If postfix is set to allow mail from that machine, then it should work to receive mail from DenyHosts.

The documentation for the configuration of DenyHosts seems lacking, but the configuration file is heavily commented and almost a substitute.  

FWIW, there are some examples in /usr/share/doc/denyhosts/examples/

It looks like the part of the DenyHosts script that handles the mail notification is this one:
/usr/share/denyhosts/DenyHosts/util.py

which looks like it in turn uses the python module 'smtplib'
[http://docs.python.org/library/smtplib.html](http://docs.python.org/library/smtplib.html)

---

