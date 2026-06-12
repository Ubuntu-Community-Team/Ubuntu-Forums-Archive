---
title: "Sendmail cannot connect.."
date: 2013-01-22
forum: Server Platforms
---

### Post by Incop on 2013-01-22
Hi all,

I have recently set up an old box with Ubuntu 12.10 and LAMP running on it. I am using php as my cron jobs and would like to send an email as part of the scripts. I have set up sSMTP / Sendmail instead of a full mail server because there is already an Outlook 2010 server running on the network and do not want to cause any issues with that in regards to receiving mail.

I have input the correct details into ssmtp.conf but I keep getting the error: 'Cannot open ip:25'

In the conf file I believe it is the mailhub setting, within this setting I have tried using the local and external IP address for the exchange server, I have also tried using the domain mail.*.co.uk

I have searched and searched but cannot find any help in regards to this problem, everyone seems to forward there smtp to google but the data I will email will be private and would much rather do it locally for security reasons.

Thank you so much for reading,

---

### Post by howefield on 2013-01-22
Thread moved to the "*Server Platforms*" forum.

---

### Post by jonobr on 2013-01-22
It looks as if port 25 is blocked or the server is not using 25 ?


I would recommend to try using the command line to interact with the SMTP server to ensure its listening.



open a terminal and try this

```
telnet <SMTP server ip> 25
```
You should get a prompt back- If it hangs there is no port 25 used on the target

```
HELO <mailserver IP>
```


You should get a hello back

```
MAIL FROM:you@yourdomain.com
```


you should get a sender ok message
then enter

```
RCPT TO:person@theirdomain.com
```


You should get a Recipient ok message

then enter 
DATA

You should get a message to enter the message

You can enter

subject:  This is a test the populates the subject field.


When done enter the escape or send sequence (usually given to you around the enter data statement.)


The good thing about doing it on the command line is you will receive an error at some point if something is going wrong

---

