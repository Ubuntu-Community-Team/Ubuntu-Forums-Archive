---
title: "postfix send mail on port other than 25"
date: 2006-01-19
forum: Server Platforms
---

### Post by papayiya on 2006-01-19
Hi,

I have a home built server running out of my house with a dynamic ip.  I'm using a dynamic dns service, so thats all good.  The webserver, etc. is running fine.

I want to create my own mail server, and so I installed Postfix (no spamassasin, etc. etc.) and wanted to just get that working intially.  I just learned that my ISP has port 25 blocked, so when I run from the command line:

sendmail [email]xxxx@gmail.com[/email]
....
...

mail.log shows:

```

Jan 19 18:41:41 localhost postfix/smtp[10943]: connect to gsmtp83.google.com[66.249.83.27]: Connection timed out (port 25)
Jan 19 18:42:11 localhost postfix/smtp[10943]: connect to gsmtp163.google.com[64.233.163.27]: Connection timed out (port 25)

```

Can someone please tell me how do I configure postfix to **send** email on another port, like 465?

Thank you

---

### Post by darth_vector on 2006-01-19
if you change the SMTP port i think your mail will be lost in the void unless you have a whole bunch of mailservers communicating on that port. even then, you will only be able to send/recieve mail from these mailservers. dunno; i could be wrong.

try asking your ISP to unblock the port - or go to another ISP.

---

### Post by LordHunter317 on 2006-01-20
I don't know how to do what you want and it won't help anyway.  Most ISPs and other people will ignore your mail for being on a residental ISP block.  You need to use relayhost and relay through your ISP's mailservers.

---

### Post by MJN on 2006-01-20
Agreed. Whilst my ISP doesn't block port 25 I was finding many receiving MTAs were rejecting by messages due to my IP being listed in known dynamic netblocks.

As LordHunter says, simply use the [relayhost]("http://www.postfix.org/postconf.5.html#relayhost") option to direct outgoing mail via your ISP's mail server. It'll not have any negative consequence for you - you'll still have full control over your mail server, incoming and outgoing.

Incidentally, one assumes your ISP doesn't block *incoming* port 25...? (I've not heard of this)

Mathew

---

### Post by Zelut on 2006-01-31
I was having this issue as well.  I used the advice above & setup relayhost (in /etc/postfix/main.cf).  Its now relayed thru my ISP account & everything is getting thru just fine.  Give that a try..

---

