---
title: "A problem with my local postfix server"
date: 2010-10-09
forum: Server Platforms
---

### Post by najeh10 on 2010-10-09
Salut everybody
i am trying to set up a mailserver for my company using postfix .
i followed a very good tutorial and when i came to the test stage ( if i can send and receive locally before i move on ) i encountered a problem with the telnet .
when i type the following command
Telnet localhost 25 
here what i get
"trying :: 1 ....
trying 127.0.0.1
Connected to localhot.
Escape character is '^]' ."
when i enter the commands as shown in the tutorial 
Ehlo postmaster@localhost 
MAil from : .... ETC
i got no reponse from the telnet server and the Shell stopped responding so i was forced to kill the telnet process to make it Stop .
i did some research and i installed the telnet server Telnetd but that didnt resolve the problem ?
i am depending on you guys cuz time is running out for my deadline 
Thanks in advance
P.S : am using ubuntu server 10.4

---

### Post by SeijiSensei on 2010-10-09
Just to make sure, did you run the following sequence of commands?

```

telnet locahost 25
...
**220 your-server-name ESMTP Postfix (Ubuntu)**
MAIL FROM: yourusername@localhost
**250 2.1.0 Ok**
RCPT TO: youraccount@somewhereelse.net
**250 2.1.5 Ok**
DATA
type in some stuff
maybe some more stuff
.
**250 2.0.0 Ok: queued as [randomstring]**
quit
Ctrl-]
telnet>quit

```

Replies from Postfix are in bold.  The telnet session doesn't close until you use the "escape" sequence of holding down the Ctrl key and typing the closing square bracket "]".  The line with just a single period is crucial, too.  That tells Postfix that the message text has ended.

---

### Post by najeh10 on 2010-10-09
Thank you my friend SeijiSensei
First of all i dont get the response taht i alwys see in your comments :
for instance when i type 
MAIL FROM : [EMAIL="postmaster@localhost"]postmaster@localhost[/EMAIL]
i dont get as u ve shwon 
250 2.1.0 OK ( is that a problem ? )
i ve typed all the commands u ve mentioned and i quited the telnet with ctrl + the bracket ( so greatefull ) and as am executing a tail command on another windows i got the following errors and warnings :
warning : /usr/lib/postfix/smtpd : bad command startup -- throtting
fatal : dict-open unsupported dictionary type : mysq ; is the postfix-mysq is installed ?
warning : process /usr/lib/postfix/trivial-rewrite pid XXX exit status 1
fatal : /etc/postfix/mysql_mailbox.cf : bad string length 0 < 1 : where_field = 
 
Am waiting for ur help and thnx Again

---

### Post by najeh10 on 2010-10-09
I forgot to tell that when i type 
tail -f var/log/mysql.log 
i got nothing !! why is that ?

---

### Post by SeijiSensei on 2010-10-09
If you don't see a greeting beginning with "200" as in my example above, then your Postfix server isn't running.  The various other errors you report suggest that there's something wrong with your installation.  In particular is there some reason you're using MySQL as a password backend?  If so, the errors suggest it isn't configured correctly.

I'd suggest you remove everything related to Postfix on your server and try again.  Just install postfix itself to begin with, not postfix-*.

---

### Post by najeh10 on 2010-10-09
My postfix is very well running , when i run "Postfix status" it tells me that it's running 
i installed mysql to save the users and the domains among othere things needed by postfix not for the password ?
dont u have another solution rather than removing all that because if i do i wont know what was my mistakes ( and tha t not good for me neither for other members )
thanks anyway and GUYS please post ur opinions

---

