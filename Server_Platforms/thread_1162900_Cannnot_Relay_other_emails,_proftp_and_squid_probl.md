---
title: "Cannnot Relay other emails, proftp and squid problem"
date: 2009-05-18
forum: Server Platforms
---

### Post by dalitso on 2009-05-18
I have an ubuntu 8.04 server which among other things I setup postfix, dovecot and fetchmail. I use webmin for configurations.I got a dynamic host name with dyndns and everything seem to be working fine. There are just three problems am facing. 

Firstly, I cannot relay my gmail emails or any other emails that are not under my hostname through my sever. I am using Mozilla Thunderbird as my email client on my client PC. My server is only relaying my dynamic hostname address, [email]me@mydydns.com[/email] and not [email]me@gmail.com[/email] when I set it in thunderbird. I am looking for a solution where I can relay any email (or rather specific email)

Secondly, I cannot access my ftp server outside my network. It only works on my LAN.
Lastly, I am failling to setup squid proxy server to block some websites.

I am still learning Linux, therefore not so advanced. I have been googling and visited forums and searched in the Post but doesn't seem to help me a lot. Its either not working or maybe too complicated for me.

Can anyone please help.

---

### Post by sidcypher on 2009-05-24
are you actually able to send emails out through the dyndns "domain"? I know they actually offer a pay mailhop to send out.  I don't know about the rest of email issue.

Your ftp server, do you have the router set to port forward to that machine? Would be main reason the FTP not accessible from outside.

No idea on squid.

---

### Post by dalitso on 2009-05-25
Thank you for your reply. FTP port 21 is really forwarded to my server. The error message I get when I try to access my FTP outside my network is:"an error occured openning that folder on the FTP server. Make sure you have permissions to access that folder. Details: The connection with the server was reset."

Yet using the same username and password, I can access the FTP on my LAN.

And yes my server can send emails using my dyndns domain.

---

### Post by dalitso on 2009-11-09
After alot of googling, the Relay problem was solved using this tutorial [http://www.howtoforge.com/postfix_re...her_mailserver](http://www.howtoforge.com/postfix_re...her_mailserver)

I also think that there was something wrong with my postfix main.cf
under  mynetworks=

The FTP problem was solved by changing ftp user group from "ftp" to "no group" under virtualmin..server templates..default settings...edit template...Proftp server.

As for squid..well its kinda long how I solved it. If anyone else has the same problem with squid you can contact me on skype. "nitram_m" is my skype name. By the way, I'm using webmin to do most of these configurations.

---

