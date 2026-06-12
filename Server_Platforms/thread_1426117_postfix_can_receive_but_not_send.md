---
title: "postfix can receive but not send"
date: 2010-03-09
forum: Server Platforms
---

### Post by nycterfin on 2010-03-09
Hi, everyone.
I've been trying to set up postfix so that I may send and receive email from my domain.  However, I have comcast as an ISP and apparently I need to relay outbound messages through their smtp server on port 587.  I have been able to configure postfix in a way that allows it to receive email but not send email by using these two guides: [https://help.ubuntu.com/community/Postfix]("https://help.ubuntu.com/community/Postfix") and [http://justatheory.com/computers/mail/postfix-and-comcast.html]("http://justatheory.com/computers/mail/postfix-and-comcast.html").  I've looked around on the forums and google for a solution but nothing seems to be quite my problem.  When I try to send an email, I immediately get an email titled "Undelivered Mail Returned to Sender" with the contents: > This is the mail system at host mail.domain.com.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                   The mail system

<emailIWasSendingTo>: host smtp.comcast.net[76.96.62.117] said: 550
    5.1.0 Authentication required (in reply to MAIL FROM command)



Reporting-MTA: dns; mail.domain.com
X-Postfix-Queue-ID: 7E87A6E205
X-Postfix-Sender: rfc822; emailIWasSendingFrom
Arrival-Date: Tue,  9 Mar 2010 21:36:37 -0500 (EST)

Final-Recipient: rfc822; emailIWasSendingTo
Original-Recipient: rfc822;emailIWasSendingTo
Action: failed
Status: 5.1.0
Remote-MTA: dns; smtp.comcast.net
Diagnostic-Code: smtp; 550 5.1.0 Authentication required



Subject:
postfix send test 3
From:
Test <email I sent from>
Date:
Tue, 09 Mar 2010 21:36:08 -0500
To:
First Last <email I was trying to send to>

message contents 

As stated earlier I can receive emails just fine.  I do have my comcast email details in /etc/postfix/sasl/passwd and I my relayhost is [smtp.comcast.net]:587 as stated in the latter guide.  I need some help here.  If you need any more information regarding the issue or specific log files (please provide a path of the log, as I am still very new to linux.  They should be the defaults for the postfix package e.g. /var/log/mail.log, etc.) just let me know and I will post them ASAP.  Also, I'm using dovecot if that helps at all.

---

