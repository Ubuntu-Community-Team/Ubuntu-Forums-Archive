---
title: "Postfix submits the mail but it is not being delivered to given mail id"
date: 2014-03-04
forum: Server Platforms
---

### Post by amitshree on 2014-03-04
Hello Everyone
I have configured postfix.
I'm using simple php program to send email.
Message gets submitted but I'm not able to see it in my mail.
Any help will be much appreciated.
Here is my PHP code
[HTML]<code><html>
<head>
<title>Sending email using PHP</title>
</head>
<body>
<?php
   $to = "amit@retailon.com";
   $subject = "This is subject";
   $message = "This is simple text message.";
   $header = "From:abc@somedomain.com \r\n";
   $retval = mail ($to,$subject,$message,$header);
   if( $retval == true )  
   {
      echo "Message sent successfully...";
   }
   else
   {
      echo "Message could not be sent...";
   }
?>
</body>
</html></code>[/HTML]

---

### Post by thnewguy on 2014-03-04
Does the server sending the e-mail have a fully qualified domain name? If not, your message is probably being blocked. Can Postfix relay messages to other domains/servers, it looks like the PHP script is sending to a host other than the one it is running on. It might help if you can post your postfix configuration file and confirm Postfix is able to send e-mails when you access it using another method like an e-mail client or telnet.

---

### Post by SeijiSensei on 2014-03-04
Look in /var/log/mail.log to see what problems Postfix is having.

---

### Post by amitshree on 2014-03-04
thnewguy, on running command telnet localhost 25
I am getting Message
[B]Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.
[/B]

---

### Post by lisati on 2014-03-04
Are you able to post the last few lines from /var/log/mail.log ? This might give us some clues as to what information we should ask about.

---

### Post by amitshree on 2014-03-04
thnewguy, These are my configurations.
General type of mail configuration: **Internet Site**
System mail name:  [B]server1.example.com
[/B]Root and postmaster mail recipient:** mail.example.com,localhost.localdomain,localhost**
Other destinations to accept mail for (blank for none): **mydomain.com mydomain localhost.localdomain localhost__**
Force synchronous updates on mail queue? **No**
Local Networks: **127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.0.0/24___**
Use procmail for local delivery?: **Yes**
Mailbox size limit (bytes): **0**
Local address extension character:** +**
Internet protocols to use: **all**

---

### Post by amitshree on 2014-03-05
lisati Here are last few lines:
```
Mar  5 10:05:43 amitshree-Inspiron-N5010 postfix/smtp[3022]: 625376D093: host mx00.1and1.es[212.227.17.175] refused to talk to me: 554-kundenserver.de (mxeue106) Nemesis ESMTP Service not available 554-No SMTP service 554 invalid DNS PTR resource record
Mar  5 10:05:43 amitshree-Inspiron-N5010 postfix/smtp[3022]: 625376D093: to=<amit@retailon.com>, relay=mx01.1and1.es[212.227.15.150]:25, delay=66467, delays=66465/0.2/2/0, dsn=4.0.0, status=deferred (host mx01.1and1.es[212.227.15.150] refused to talk to me: 554-kundenserver.de (mxeue106) Nemesis ESMTP Service not available 554-No SMTP service 554 invalid DNS PTR resource record)
```

---

### Post by lisati on 2014-03-05
Thanks for the lines from your mail log.

Unfortunately, that does not tell me much about why connections through telnet might be disconnected. It does, however, highlight something that might affect deliverability to some email providers. [blackilstalert.org]("http://blacklistalert.org") describes the problem this way:
> WARNING: Forward-DNS does NOT match Reverse-DNS.
DNS is INCONSISTENT.
Please request your Admin or Provider to fix this.

---

