---
title: "postfix - connection refused"
date: 2008-02-01
forum: Server Platforms
---

### Post by beaker15 on 2008-02-01
Hello, 
I currently have an Ubuntu server with Samba working as a domain controller. I also have postfix running on it which I'm having trouble connecting to through thunderbird from a client machine. the client can see the server but it comes up with the error message 'connection refused'. I think it may be an authentication thing so i disabled TLS and SASL (which i haven't set up) and did the same on thunderbird but get the same problem. Any ideas on this? Does postfix need TLS or SASL to work? Eventually I want Postfix to use the Ubuntu system user/passwords so that once a user logs on to the domain, they don't have to log in to their email as well. 

thanks

---

### Post by ssuehr on 2008-02-01
Hello,

I might be confused about what you're attempting to do, but Postfix provides SMTP services, which by default would be on TCP port 25.  When you say that you're attempting to connect to the server with Thunderbird, are you trying to check mail using Thunderbird?  That would indicate to me that you'd need some type of POP3 or IMAP software running, which Postfix is not.  Postfix will provide just the SMTP portion (I'm trying to remember what Thunderbird calls that.)

A connection refused message would indicate to me that the server isn't listening on the port that Thunderbird is trying to connect to rather than an authentication issue.

If you can provide a bit more detail about what you're trying to do with Postfix and Thunderbird, I might be able to help further.

Steve

---

### Post by beaker15 on 2008-02-02
yeah, my incoming email goes to a web based email service and fetchmail grabs mail for me from these mailboxes to folders in /var/mail/(user) on the ubuntu server. I then want the clients on my domain to logon to their settings and then get thunderbird up which will show the messages from that users folder. At least, thats what i would eventually like. Admittedly i didn't realise postfix was smtp only, this is my first attempt at a mail server so a little guidance would come in handy. So i need a pop3 package eh?  can you recommend one?

---

### Post by ssuehr on 2008-02-02
I've tried and used several POP3 packages in ISP environments and I hate all of them just about equally.  :)  A few of the more popular ones (at least from what I can tell) are courier, teapop, and dovecot.  Another one is popa3d ([http://www.openwall.com/popa3d/](http://www.openwall.com/popa3d/)) but I don't know if its still under active development.  I think teapop might have ldap integration which could aid the whole domain logon bit of your requirements.

Steve

---

