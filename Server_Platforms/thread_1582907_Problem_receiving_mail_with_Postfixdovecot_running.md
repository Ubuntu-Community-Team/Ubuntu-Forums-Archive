---
title: "Problem receiving mail with Postfix/dovecot running ISPconfig3"
date: 2010-09-27
forum: Server Platforms
---

### Post by klemorali on 2010-09-27
Running Ubuntu 10.04.1 32Bit server with install per perfect ISPconfig3 from How forge.
 
I can access the server via my Email client (I've tried Outlook and Evolution which both appear to be making the connections). However there is never any mail in the inbox. I am accessing the accounts as POP
 
when accessing postfix thru Webmin 1.520 I see mail in the que. However, the mail has the following status 
 
'temporary failure. Command output: pipe: fatal: pipe_command: execvp /usr/bin/maildrop: Permission denied'
 
I have attempted to send mail to other addresses and they are rejected by the receiving server. In my first attempt charter.net denied me returning this message 
 
'[SIZE=1]host ib1.charter.net[216.33.127.20] refused to talk to me: 421 imp06 charter.net ?? charter.net connection refused from [75.176.32.193] E1210'[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]I've been tinkering with this server for about 2 weeks now and having a number of issues which I have mostly worked thru. This one has me stumped at the moment.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]NOTE: Dell PE 2600 with a sudo functional CD/Floppy combo drive. Having to use Super Grub2 disk to loopboot an iso from USB drive. Not much fun!![/SIZE]

---

