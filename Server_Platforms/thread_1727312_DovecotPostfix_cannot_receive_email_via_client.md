---
title: "Dovecot/Postfix cannot receive email via client"
date: 2011-04-12
forum: Server Platforms
---

### Post by LittleLebowski on 2011-04-12
I have a very basic install of dovecot and postfix on the latest version of Ubuntu server.  This is an internal only email server with internal only DNS.

  I can send email via clients and check said emails via the command line when logged in as the appropriate user.  I cannot for the life of me check said emails via SquirrelMail on the server nor using IMAP clients.  I have no idea where to look and I can't find a basic tutorial for the life of me.  Where should I start?

---

### Post by HermanAB on 2011-04-12
Where to start?  You should start at the Postfix home page:
[http://www.postfix.org/documentation.html](http://www.postfix.org/documentation.html)

The problem is that Postfix is very complex and you really need to read the documentation and howto guides.

If however you would like to use something that is easier, then you should install Citadel instead:
[http://www.citadel.org](http://www.citadel.org)

---

### Post by LittleLebowski on 2011-04-12
Postfix is sending successfully and I can view said messages logging into the server as the user.

---

### Post by LittleLebowski on 2011-04-12
All I am trying to do is get up a webmail server (squirrelmail?) and an IMAP or POP server with SMTP.  All local/internal LAN only.
 
 Suggestions?  I tried out citadel and did not like it.

---

### Post by SeijiSensei on 2011-04-12
What do you see if you run "telnet localhost 143" from the command prompt?  Does dovecot respond with its banner? 

Did you run ./conf.pl in the Squirrelmail config directory and point it at localhost:25 for smtp and localhost:143 for IMAP?

---

### Post by LittleLebowski on 2011-04-12
I just purged and started over on dovecot.  It is running but not listening.  I reconfigured Squirrelmail as you suggested as well.  The telnet test is not working because IMAP is not listening.  I have a bone stock Dovecot.conf file except that I uncommented the maildir location.  This shouldn't be this hard.

---

### Post by LittleLebowski on 2011-04-12
OK, a reboot got me to the below.  Squirrelmail is configured for use with Dovecot on 143.  

  Mail is being sent but not showing up in Squirrelmail still.  I can view the mail via command line though.

```
root@mail:~# telnet localhost 143
Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 LITERAL+ SASL-IR LOGIN-REFERRALS ID ENABLE STARTTLS AUTH=PLAIN] Dovecot ready.

```

---

### Post by SeijiSensei on 2011-04-13
I'm guessing you're not pointing to the correct location where the mail is stored.  I can't help with this since I use mbox files rather than Maildir.  Perhaps someone with more experience with Maildir can help.

Post the contents of config.php in [noparse][code][/noparse] tags.  We don't need any of the theme definitions at the bottom of file.

---

### Post by LittleLebowski on 2011-04-13
Solved.  Something is wrong with the test account I was using.  It's the one I created during the Ubuntu install.  Creating new accounts via the command line worked perfectly and I don't know why.  

  Much thanks SeijiSensei!

---

### Post by SeijiSensei on 2011-04-13
You're welcome.  Mark the thread [solved] by editing the original post and choosing [solved] from the drop-down box.

---

