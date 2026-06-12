---
title: "Postfix woes"
date: 2007-07-04
forum: Server Platforms
---

### Post by Uranium235 on 2007-07-04
I have made several unsuccessful attempt at configuring postfix using the guide at [https://help.ubuntu.com/7.04/server/C/postfix.html](https://help.ubuntu.com/7.04/server/C/postfix.html) . So far everytime I have gotten to the libsasl2 installation part of the configuration it has crashed all email function.  I have stopped at this point and I can receive email into my server just fine, but I cannot send any.  When I try to send mail using a client program e.g. thunderbird, it asks for the password repeatedly.  And when i try to send mail from telnet I get this output:

dpit@dpit:~$ telnet mail.dpit.biz 25
Trying 24.248.215.166...
Connected to dpit.biz.
Escape character is '^]'.
mail from: radar@220 mail.dpit.biz ESMTP Postfix (Ubuntu)
 
250 2.1.0 Ok
rcpt to: [email]wardbl001@yahoo.com[/email]
554 5.7.1 <wardbl001@yahoo.com>: Relay access denied

help! :)

---

### Post by Uranium235 on 2007-07-04
on trying a different client program (Evolution) I get this error:

Unable to authenticate SMPT server.
Bad authentication response from server.

---

### Post by Uranium235 on 2007-07-05
bump

---

### Post by Uranium235 on 2007-07-05
Ok I have completed installation at the guide I linked above.  I can still receive emails just fine, but I cannot send them.  It will ask for the password over and over, just like it was before.  How can I view my mail logs?

---

### Post by Uranium235 on 2007-07-05
is it possible that I am simply needing to add each users password for it to work?

---

### Post by Uranium235 on 2007-07-05
Ok I have gotten past the "relay access denied" when I try to send a message from telnet, but I still can't send from a client type program

---

### Post by Uranium235 on 2007-07-05
I can definitely send mail to the outside now by using the terminal, but for some reason on the client end I can't send anything.  I'm still stuck at the authentication where it asks for the password over and over.  Can someone please tell me what I'm doing wrong?

---

### Post by Uranium235 on 2007-07-05
I am now sending and receiving but only one the initial test account.  Mail going to other users gets this error message:

Diagnostic-Code: X-Postfix; maildir delivery failed: create maildir file
    /home/rmahmens/Maildir/tmp/1183664300.P7958.dpit: Permission denied

obviously the outside world cannot make the file needed, so what do I need to do to fix it?

---

### Post by mbradlcu on 2007-07-05
the ~/Maildir/* could be setup in the /etc/skel so new users would have the dir, but for existing accounts I think you'll have to run 

mb2md -m -s .mail #this creates ~/Maildir/{cur,new,tmp}
mb2md -s mail/ -R #this creates ~/Maildir/. folders and messages created by the users

---

