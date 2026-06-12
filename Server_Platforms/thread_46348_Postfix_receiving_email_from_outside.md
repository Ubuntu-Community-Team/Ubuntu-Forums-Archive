---
title: "Postfix receiving email from outside"
date: 2005-07-04
forum: Server Platforms
---

### Post by Spleenie on 2005-07-04
I know this is one that often gets asked, but I am not finding a solution that works for me :(

I am able to send outbound messages from my server, and internally sending and receiving email is working, it is receiving mail from the net that is not working.

Here is my main.cf file:

```
 

readme_directory = /usr/share/doc/postfix/README.debian
sendmail_path = /usr/sbin/sendmail
setgid_group = postdrop
command_directory = /usr/sbin
manpage_directory = /usr/share/man
daemon_directory = /usr/lib/postfix
newaliases_path = /usr/bin/newaliases
mailq_path = /usr/bin/mailq
queue_directory = /var/spool/postfix
mail_owner = postfix
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# User configurable parameters

myhostname = www.mydomain.com
mydomain = mydomain.com
myorigin = $mydomain
inet_interfaces = all
mydestination = $myhostname, $mydomain, localhost.$mydomain, localhost
mynetworks_style = host
delay_warning_time = 4h
smtpd_banner = $myhostname ESMTP $mail_name ($mail_version) (Ubuntu Linux)
unknown_local_recipient_reject_code = 450
smtp-filter_destination_concurrency_limit = 2
lmtp-filter_destination_concurrency_limit = 2
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
recipient_delimiter = +
owner_request_special = no
alias_maps = hash:/etc/postfix/aliases
virtual_alias_domains = mydomain.com www.mydomain.com
virtual_alias_maps = hash:/etc/postfix/virtual


``` 

wherever you see mydomain listed, I have actually used my fully qualified domain name.

I am able to connect to port 25 using telnet from the outside.

This is the readout from netstat -ntl

```
netstat -ntl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN
tcp6       0      0 :::80                   :::*                    LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN
tcp6       0      0 :::25                   :::*                    LISTEN

``` 

Outside mailers eventually receive an email from their provider stating that they were unable to connect and the email delivery has been delayed.

This is what my /var/log/syslog is reporting for a typical email sending from outside experience (note I have my emails going to [email]user@mydomain.com[/email] forwarding off server to a webmail service (mynetmailaccount@gmail.com))

```
Jul  5 09:50:11 mydomain postfix/smtpd[9334]: connect from zproxy.gmail.com[64.233.162.195]
Jul  5 09:50:11 mydomain postfix/smtpd[9334]: DD8E333B8D: client=zproxy.gmail.com[64.233.162.195]
Jul  5 09:50:12 mydomain postfix/cleanup[9337]: DD8E333B8D: message-id=<af8bc8bb050704164934b9fc5c@mail.gmail.com>
Jul  5 09:50:12 mydomain postfix/qmgr[9331]: DD8E333B8D: from=<mynetmailaccount@gmail.com>, size=1366, nrcpt=1 (queue active)
Jul  5 09:50:12 mydomain postfix/smtpd[9334]: disconnect from zproxy.gmail.com[64.233.162.195]
Jul  5 09:50:18 mydomain postfix/smtp[9338]: DD8E333B8D: to=<mynetmailaccount@gmail.com>, orig_to=<user@mydomain.com>, relay=gmail-smtp-in.l.google.com[64.233.171.27], delay=7, status=sent (250 2.0.0 OK 1120520957 63si2174755rna)
Jul  5 09:50:18 mydomain postfix/qmgr[9331]: DD8E333B8D: removed
``` 

ie everything looks kosher

Perhaps I have set up the main.cf incorrectly. I just have no idea what I have done wrong. Any help would be awesome. I am using Hoary Ubuntu if that helps anyone wishing to compare their working *envy* version to mine :)

Cheers, Spleenie

---

### Post by alastair on 2005-07-05
I use and like Postfix, but am not an expert. But the parameter :

mynetworks_style = host

seemed new/odd to me. From :

[http://www.postfix.org/postconf.5.html#mynetworks_style](http://www.postfix.org/postconf.5.html#mynetworks_style)

"The method to generate the default value for the mynetworks parameter. This is the list of trusted networks for relay access control etc."

You seem to have no "mynetworks" - so the above parameter will default it to "host" - "when Postfix should "trust" only the local machine".

Perhaps try without.

Be careful with this - we don't want open relays.

---

### Post by LordHunter317 on 2005-07-05
I don't see anything wrong with what's provided.  I don't fully understand the problem either.  It looks like mail to the account you see gets sent OK.

If you're getting an error email, why didn't you post it?  It's hard to tell what's wrong without the error...

---

### Post by sundancer on 2005-07-05
I think it's a small one - you forget
```

local_recipient_maps=

```
because postfix will reject every mail from outside, that is not listed in these maps. With this setting, you disable this behavior.

---

### Post by Spleenie on 2005-07-05
[QUOTE=LordHunter317]I don't see anything wrong with what's provided.  I don't fully understand the problem either.  It looks like mail to the account you see gets sent OK.

If you're getting an error email, why didn't you post it?  It's hard to tell what's wrong without the error...[/QUOTE]

The email error was the standard error, cannot connect to host sending has been delayed, which was wierd because, like I said in the original post, I could connect to port 25 using telnet.

I removed the repetition in mydomain and virtual_alias_domains and tried that.

Eventually came to the solution, which was the only possible one given my seeming success in the syslog log file: It bloody was working dammit.

gmail seems to have an issue with receiving email that is a copy of the one it just sent. ie I was sending an email from mywebmail@gmail to com to my mailserver account, which was being forwarded intentionally back to my gmail account. I think gmail was silently preventing my email from getting back to me. I used another webmail account (hotmail) and that email was received by my mailserver and dutifully forward to gmail, where it was shown as a new message.

SO i think it is a problem/feature (  :)  ) of gmail, not a problem with postfix or my server, thankfully.

Thankyou everyone for your replies!

Ps i have also checked my mailserver for relaying and it not a relayer, which is a good thing too ;)

---

### Post by reformist on 2006-08-19
I don't know how you discovered that issue with Gmail Spleenie, but I had the same conditions as you, and you're right - it was working, but was invisible because Gmail was dropping the test emails. Great work.

I've posted a [simple guide]("http://philisoft.com/blog/howto-setup-mail-forwarding-on-ubuntu-its-easy/") with explicit steps to get forwarding going on Ubuntu. It really is quick and straight forward, it's just no one that I've seen explicitly documents how to do mail forwarding and only mail forwarding.

---

### Post by Spleenie on 2006-08-19
Glad my hours of headache and its resolution was of some use :)

Enjoyed the page by the way, although I am unfamiliar with mailx. It seems to make postfix function in a similar way to sendmail, which did utilise .forward files in the users home dir.

The way I set it up, which required only postfix, was to edit a file called virtual in /etc/postfix and at the bottom add the following sort of thing:

[email]user@mydomain.com[/email]          [email]mywebmail@gmail.com[/email]

The first being your user at your domain and the second being the one you wish to forward the email to.

You then issue the following commands to update your postfix:

postfix reload
postmap /etc/postfix/virtual

This is a more global method of controlling email forwarding, which I actually found more useful than having .forwards floating around in various home dirs. I can at a glance see what is going where and modify easily.

As a sidenote, I am now able to send from my gmail account back to my domain and bounce back to myself without it disappearing. I did email them about it a while back when I discovered it. Perhaps they fixed or removed that feature.

---

