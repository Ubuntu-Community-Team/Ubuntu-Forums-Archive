---
title: "How to read emails using outlook?"
date: 2008-07-21
forum: Server Platforms
---

### Post by rubysoft on 2008-07-21
I manage to setup a web/email server (on Linux Ubuntu Hardy Heron)from this site guideline [http://www.mysql-apache-php.com/](http://www.mysql-apache-php.com/)

I'm able to send and receive emails.
The problem is I am unable to retrieve or send mail using Thunderbird or Outlook Express (pop/imap/smtp). 
What settings do I need to change so it can be read using 3rd party program?

---

### Post by windependence on 2008-07-21
It's not using a third party program, it's a mail server just like any other mail server out there (if set up properly). You need to set the POP3 server, and smtp server to your server, and if you you own a domain, point your mx record at your server's externa' IP address. I suspect you have done this if you can receive e-mail already.

-Tim

---

### Post by rubysoft on 2008-07-21
erm ok i have done that.
but still the problem is still there.
i tried accessing email account using outlook express on windows xp to retrieve the email and it failed.


but when i use squirrelmail web-interface i can read and send mail.

---

### Post by windependence on 2008-07-21
Try using the IP address of the mail server.

-Tim

---

### Post by Titan8990 on 2008-07-21
I find it helpful to run a packet sniffer such as wireshark on the server to diagnose problems such as this.

---

### Post by rubysoft on 2008-07-22
:lolflag: its working now (half-way)

I can receive emails from client side but now theres a new problem Im unable to sent out email thats composed at the client side :confused:

---

### Post by rubysoft on 2008-07-22
ok now i get the message that

An error occurred sending mail. The mail server responded: 5.7.1 <name@domain.com>:Relay access denied. Please check the message recipients and try again.

---

### Post by Titan8990 on 2008-07-22
Now you need to check your ACLs and find out how your mail server decides whether or not it will relay a certain message.

---

### Post by windependence on 2008-07-22
I think this is coming either from the recipient's mail server or her own ISP if she is using their server to relay outgoing mail.

-Tim

---

