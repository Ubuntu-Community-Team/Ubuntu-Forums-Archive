---
title: "mail.log logfile problem"
date: 2019-05-12
forum: Server Platforms
---

### Post by tomdf on 2019-05-12
Hello guys,

i am running ubuntu 18.04 and webserver setup with ispconfig and postfix etc. 

i see the following logfile entry:

```


May 12 21:29:45 server1 dovecot: pop3-login: Aborted login (auth failed, 1 attempts in 2 secs): user=<test@teneriffa-akupunktur.com>, method=PLAIN, rip=89.248.174.205, lip=173.249.25.125, session=<izNi0rWIIkJZ+K7N>



```

i assume the user [EMAIL="test@teneriffa-akupunktur.com"]test@teneriffa-akupunktur.com[/EMAIL] tries to connect via php3 login 
rip = the source ip from where?
lip = the ip address of the server where the domain is running?

i never setup an email account [EMAIL="test@teneriffa-akupunktur.com"]test@teneriffa-akupunktur.com[/EMAIL] 
Can it be that there is a hack on the server?

it would be great if you can give me some help how to analyze the logfiles

thanks a lot

---

### Post by SeijiSensei on 2019-05-13
Someone is trying to exploit your IMAP server (dovecot), perhaps to grab email addresses to add to a spam list. These sorts of attacks happen all the time.

If you're not providing any mail services on this machine, there's no need for dovecot. Why is it running?

---

### Post by tomdf on 2019-05-14
thanks for you kind answer.
I am running dovecot because it is a webserver who has domains and email accounts.

is there a way to prevent these kind of attacks or can i only do it not running dovecot?

thanks a lot

---

### Post by SeijiSensei on 2019-05-14
Unless the attacker has the username and password for an account on your machine, these efforts will fall flat.  

There is a secure version of POP3 that runs on port 995 rather than 110.  If you could migrate your users to that, you'd see fewer attempts on the POP3 port. Plus I suspect it's easier to probe the insecure ports like 110 and 143.

My server gets these attacks from time to time. They seem relatively harmless since they fail login.

---

### Post by tomdf on 2019-05-18
thanks so much for your kind.
every time you help me so much.. have a nice day and thanks..

---

