---
title: "Rather than having email server set default SMTP settings"
date: 2011-01-31
forum: Server Platforms
---

### Post by tbobker on 2011-01-31
I am using my VPS Ubuntu 10 server as a webserver. I have added MX records to my DNS so that I can use an external email server and am using the domain hosts nameserver to add and delete DNS entries. 

The idea is that my VPS server is purely to act as a web server. 

The problem is that many applications rely on the php mail function to send mail. 

Is there any way I can set a default SMTP setting so that the mail function uses this rather than having to tell each application to use a SMTP setting?

Any ideas appreciated.

---

### Post by SeijiSensei on 2011-01-31
On *nix platforms, PHP expects to find sendmail or a sendmail equivalent.  The simplest solution for you would be to install sendmail or Postfix and configure the "smart host" for whichever you choose to point to your external mail server.

In sendmail, I'd just edit /etc/mail/sendmail.cf as follows:
```

# "Smart" relay host (may be null)
DSsmtp-relay.example.com

```

using the actual server name, of course.

I'm sure there's an equivalent setting in Postfix, but I don't use that.

---

### Post by tbobker on 2011-01-31
This is what I am after. 

SendMail. I can see a sendmail directory on my server and a file called aliases.  Is this where I put the entries.

---

### Post by SeijiSensei on 2011-01-31
No, you need to edit the sendmail.cf file as I said before.  By adding a smart host, messages sent by PHP will be automatically forwarded along to the external mail server.

The file /etc/aliases maps symbolic addresses to other addresses or lists of addresses.  So the alias entry:

```

John.Smith:     john

```

accepts mail for "John.Smith@example.com" and delivers it to user john's mailbox.  You can also have entries replacing "john" with "john@somewhere.net" so mail for "John.Smith@example.com" would be forwarded to his mailbox at somewhere.net.

I'd check to make sure sendmail is installed properly with "sudo apt-get install sendmail".  Ubuntu should set up sendmail to start automatically at boot.  You can check to see if it's running by typing "ps ax | grep sendmail" at a prompt.  You should see "sendmail: accepting connections" in the process list.  Another good check is to type "telnet localhost 25" at a prompt and see if sendmail replies with its greeting message.

---

### Post by tbobker on 2011-01-31
Ok thanks for the help.

---

