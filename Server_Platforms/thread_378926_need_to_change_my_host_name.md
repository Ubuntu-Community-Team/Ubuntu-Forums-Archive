---
title: "need to change my host name"
date: 2007-03-07
forum: Server Platforms
---

### Post by nephish on 2007-03-07
hello there 

i just set up an email server on my edgy box at work. Most mail gets delivered ok, but some is rejected because i do not have a fully qualified host name.

i think that means i need to change the host name of my computer from 
mydomain to mydomain.com

so, my three questions are:
how do i do this ?
will i have to reboot ? ( production machine )
will this create any consequences in my apache or mail servers ( will i need to change anything anywhere else ? )

oh, and please let me know if there are any more gotchas out there i may need to be aware of before doing this ..

thanks for any tips.

---

### Post by Mr. C. on 2007-03-07
Most large email servers will reject email from unqualified hosts.

To use a domain, you must purchase one via a registar.  Once you have it, you set up certain DNS entries to allow email to be directed to your system, and to indicate to other servers you are legitimate.

You will need a static IP.

The actual hostname of your machine is less important than your mail configuration.  No, you will not need to reboot.

Apache doesn't send email by itself.  No consequences.  I don't understand your question about mail servers - which mail servers?

Be prepared to invest a large amount of time getting over a learning curve, that you are now just starting.  There are far too many things to know, to simply categorize as "gotchas".

MrC

---

### Post by nephish on 2007-03-07
sorry, left out some info. 
we do have a dns and static ip and host name.
i am using postfix and courier, all is working fine. 
i can send and receive mail from my work computer as 
[email]user@mydomain.com[/email] and it seems to work ok. 
apache serves the company web page. I don't remember if there would be any consequence to changing the host name of the computer. 
the host name of the computer is mydomain, but the mail server is mail.mydomain.com . The reject message i got showed the host name as mydomain so i thought that it would fix stuff if i changed the host name to mydomain.com

thanks for your help on this. I have done a lot already, but still have a lot to learn

---

### Post by Mr. C. on 2007-03-07
Ah, ok, got it.

You simply need to configure postfix to announce its email name when it sends outbound email.

myhostname = mail.mydomain.com

in main.cf

Its not clear how/if you have your internal DNS setup, or if you are relying entirely on /etc/hosts.

Your MX record needs to point to mail.mydomain.com
There must be an A record for mail.mydomain.com
There must be a PTR record that matches the IP to the mail.mydomain.com hostname.

PM me your domain name, and I'll check out your DNS records.  Also check DNS Stuff's DNS report at the bottom of the page: [http://www.dnsstuff.com/](http://www.dnsstuff.com/)

MrC

---

