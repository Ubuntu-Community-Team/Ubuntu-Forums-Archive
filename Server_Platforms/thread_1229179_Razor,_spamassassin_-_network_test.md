---
title: "Razor, spamassassin - network test"
date: 2009-08-01
forum: Server Platforms
---

### Post by polo23 on 2009-08-01
Hi I need help with antispam. I use spamassassin with razor. And when I test spamassassin --lint -D razor2 then I get result that razor2 : test local only, skipping razor. I need test razor in connection to the internet. I dont know how it do. Can you advise me? 
I find out from spamassassin web the following: 

How to turn on network tests 

Edit your spamd start-up script, or start-up options file (depending on which OS you're running, these may be different). There should be a -L or --local switch in that file. Remove it to enable network tests. 

But i cant find the file with the switch -L. I use CentOS... 
When I type the folowing: spamassassin -t -D razor2 < /tmp/spam 
 I want to get something like this: 
debug: Razor is available 
 debug: Razor Agents 1.20, protocol version 2. 
 debug: Read server list from /home/jgb/.razor.lst 
 debug: 72636 seconds before closest server discovery 
 debug: Closest server is 209.204.62.150 
 debug: Connecting to 209.204.62.150... 
 debug: Connection established 
 debug: Signature: 48e74b8496877ba45072b201b41eebed7038186b 
 debug: Server version: 1.11, protocol version 2 
 debug: Server response: Negative 
 48e74b8496877ba45072b201b41eebed7038186b 
 debug: Message 1 NOT found in the catalogue

---

