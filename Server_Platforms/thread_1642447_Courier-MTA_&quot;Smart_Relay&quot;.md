---
title: "Courier-MTA &quot;Smart Relay&quot;"
date: 2010-12-10
forum: Server Platforms
---

### Post by alden_pease on 2010-12-10
I have gotten the Courier-MTA set up, and can receive mail now.  The problem is with sending.  I can send to some domains, but not all (For example, gmail.com).  The problem is that gmail requires that the IP Address resolve to the Domain name (I get this error: "The IP you're using to send mail is not authorized to send email directly to our servers. Please use the SMTP relay at your service provider instead.").

In sendmail, I fixed this problem by relaying my mail to my ISP's SMTP server, using this: "(`SMART_HOST', `smtp-server.maine.rr.com')" (without the quotes).  That worked fine for me, but I switched to Courier-MTA, (for various reasons) and now don't know how to set up a "Smart Host" in it.

I created the file "esmtproutes" to /etc/courier, as I read in the documentation, and added ":smtp-server.maine.rr.com" to it. That got rid of the error from Google, but I'm still not receiving it in my gmail account.  The system log prints this:

```
Dec 10 12:20:52 aldenpease courierd: newmsg,id=0038C081.4D026173.000051A4: dns; localhost (localhost [127.0.0.1])
Dec 10 12:20:52 aldenpease courierd: started,id=0038C081.4D026173.000051A4,from=<root@[**PROTECTED**]>,module=esmtp,host=gmail.com,addr=<[**PROTECTED**]@gmail.com>
Dec 10 12:20:52 aldenpease courierd: started,id=0038C081.4D026173.000051A4,from=<root@[**PROTECTED**]>,module=local,host=alden!!1000!1000!/home/alden!!,addr=<alden>
Dec 10 12:20:52 aldenpease courierd: Waiting.  shutdown time=none, wakeup time=Fri Dec 10 12:25:01 2010, queuedelivering=4, inprogress=2
Dec 10 12:20:52 aldenpease courierlocal: id=0038C081.4D026173.000051A4,from=<root@[**PROTECTED**]>,addr=<alden@[**PROTECTED**]>,size=329,success: Message delivered.
Dec 10 12:20:52 aldenpease courierd: Waiting.  shutdown time=none, wakeup time=Fri Dec 10 12:25:01 2010, queuedelivering=4, inprogress=1
Dec 10 12:20:52 aldenpease courieresmtp: id=0038C081.4D026173.000051A4,from=<root@aldenpease.me>,addr=<[**PROTECTED**]@gmail.com>: 250 OK DD/68-24070-A71620D4
Dec 10 12:20:52 aldenpease courieresmtp: id=0038C081.4D026173.000051A4,from=<root@[**PROTECTED**]>,addr=<[**PROTECTED**]@gmail.com>,size=329,success: delivered: smtp-server.maine.rr.com [71.74.56.22]
Dec 10 12:20:52 aldenpease courieresmtp: id=0038C081.4D026173.000051A4,from=<root@[**PROTECTED**]>,addr=<[**PROTECTED**]@gmail.com>,size=329,status: success
Dec 10 12:20:52 aldenpease courierd: completed,id=0038C081.4D026173.000051A4
Dec 10 12:20:52 aldenpease courierd: Waiting.  shutdown time=Fri Dec 10 13:19:51 2010, wakeup time=Fri Dec 10 12:25:01 2010, queuedelivering=3, inprogress=0

```

I'm getting no response back from the Time Warner servers or the Google server.  I did "telnet smtp-server.maine.rr.com 25" and connected successfully.  Followed by:

```
HELO [**PROTECTED**]
MAIL FROM:<alden@[**PROTECTED**]>
RCPT TO:<[**PROTECTED**]@gmail.com>
DATA
TO:<[**PROTECTED**]@gmail.com>
FROM:<alden@[**PROTECTED**]>
SUBJECT:Test
Test
.
QUIT
```

That sent the message successfully to my gmail account.  There is something wrong with my configuration for the relay.  Thank you for your help.

---

### Post by elico on 2010-12-10
is there a specific reason you dont use postfix for it? (just wondering)

---

### Post by alden_pease on 2010-12-10
Just don't have the time to get it set up, unless you or someone knows of a quick walkthrough for configuring it.

---

### Post by alden_pease on 2010-12-12
I took your advice with Postfix, it was a lot easier than everyone anticipated it would be.  Thank you!

---

