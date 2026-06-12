---
title: "Postfix not working with client"
date: 2008-05-13
forum: Server Platforms
---

### Post by tonkyman on 2008-05-13
I'm in the process of building a mail server to replace my old exim box with.

I loaded ubuntu with the DNS, LAMP and postfix options then followed the instructions from the ubuntu server guide.

I can send email to my ubuntu server from other mail servers on other domains and I'm able to use POP3 to recieve from my POP3 server but I can not send mail from my mail client on my windows desktop.

I have foxmail setup to use as a test platform but when I try to send mail through my new ubuntu/postfix server I recieve the following error on foxmail;

SMTP Server Reply
502 5.5.2
Error: Command Not Recognized

I'm sure I'm missing something small (like a security setting) but I've beat my head against the wal trying to figure it out. Can you guys shed some light on this for me?

tahnks,
Tony

---

### Post by whitey on 2008-05-13
can you telnet to the smtp port from the command line:

$ telnet <IP address> smtp

Post the reply

---

### Post by tonkyman on 2008-05-14
Yes I can. I telnet into port 25 and issue ehlo localhost and I get the proper response.

In the postfix main.cf file the is a commented section the says there is a text document that explains how to set the client up for SSL but that document is not in the location it should be.

I never expected this to be the hard part... how strange.

---

### Post by whitey on 2008-05-14
Looking at your above comments in your first post, I would check to see if you have your /etc/postfix/virtual and /etc/postfix/mydomains files setup correctly.  If you aren't using those files you will have to edit your /etc/postfix/main.cf to make sure you are explicitly listing your hostname, and or domain name:

```

myhostname = mightymouse.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = mightymouse.com, localhost.localdomain, localhost

```

---

### Post by andyxian on 2008-10-13
Hi all,

I have the same problem. in my case, i can telnet localhost 25 on the server and execute the command AUTH PLAIN. but if I telnet from outside network, no matter what command I type at the first time, the server reply "502 5.5.2 Error: command not recognized".  then I type the command again, it works fine. but this cause the problem for email client like outlook and foxmail, because they will not try one more time the "AUTH PLAIN" command. 

anyone knows this problem?

Thanks,
Andy

---

