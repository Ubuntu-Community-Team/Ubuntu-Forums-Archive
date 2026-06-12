---
title: "Request: gnokii 0.6.3 -&gt; gnokii 0.6.5 or better"
date: 2005-06-13
forum: Ubuntu Backports
---

### Post by amilist on 2005-06-13
if possible, a current version of gnokii would be really great, as it offers 
"....DKU2 cable support with the kernel driver, better phonebook and calendar output, possibility to disable the retransmission policy, enhancements to the gnapplet driver. ..."

i hope, i am not the only one who is getting sick about the bad nokia-linux compatibility.....

---

### Post by Seth on 2005-06-14
[QUOTE=amilist]if possible, a current version of gnokii would be really great, as it offers 
"....DKU2 cable support with the kernel driver, better phonebook and calendar output, possibility to disable the retransmission policy, enhancements to the gnapplet driver. ..."

i hope, i am not the only one who is getting sick about the bad nokia-linux compatibility.....[/QUOTE]
 Packages and libs and supporting drivers oh my! Six files here; looks like the sms daemon is separate (I haven't used gnokii; Sony Ericsson forever :-D)

Pick what you need:
Gnokii: [http://sethkinast.com/ubuntu/hoary/backports/gnokii_0.6.5-1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/gnokii_0.6.5-1~5.04ubp1_i386.deb)
libGnokii: [http://sethkinast.com/ubuntu/hoary/backports/libgnokii2_0.6.5-1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/libgnokii2_0.6.5-1~5.04ubp1_i386.deb)
libGnokii_dev: [http://sethkinast.com/ubuntu/hoary/backports/libgnokii2-dev_0.6.5-1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/libgnokii2-dev_0.6.5-1~5.04ubp1_i386.deb)

smsd: [http://sethkinast.com/ubuntu/hoary/backports/gnokii-smsd_0.6.5-1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/gnokii-smsd_0.6.5-1~5.04ubp1_i386.deb)
smsd (mysql): [http://sethkinast.com/ubuntu/hoary/backports/gnokii-smsd-mysql_0.6.5-1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/gnokii-smsd-mysql_0.6.5-1~5.04ubp1_i386.deb)
smsd (pgsql): [http://sethkinast.com/ubuntu/hoary/backports/gnokii-smsd-pgsql_0.6.5-1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/gnokii-smsd-pgsql_0.6.5-1~5.04ubp1_i386.deb)

---

### Post by amilist on 2005-06-14
Thank your very much for your excellent work!! Finally i can edit my mobiles phonebook!!!

YESS YESS YESS!!!

 :grin:   :grin:   :grin:

---

### Post by nemik on 2005-06-16
[QUOTE=amilist]Thank your very much for your excellent work!! Finally i can edit my mobiles phonebook!!!

YESS YESS YESS!!!

 :grin:   :grin:   :grin:[/QUOTE]
 hmmm been having some questions about this since you guys know what's up. i currently use SMStools and its smsd along with a shell script i wrote to pass the number an SMS came from, and the text inside, to a PHP script. it works well with a DLR-3P cable and nokia 6310i, but this is expensive.

I want to use cheaper phones. i got a 6190 and a DAU-9 cable, but heard SMStools doesn't support it (haven't tried yet though). i only need this to process incoming SMS's and pass the number it came from and the message to a PHP script. what do you guys recommend? sony ericssons such a t300 and t226 are cheap but not sure if they would work. also for those do i need the DRS-11 OEM serial cable or can I use an aftermarket serial cable? or even better, can I use USB cable so I could have many phones connected to a USB hub so one computer could handle many incoming.

thanks in advance for any help and sorry if its way off-topic.

---

### Post by Nightwind on 2005-12-25
> **Seth]Packages and libs and supporting drivers oh my! Six files here said:**
> http://sethkinast.com/ubuntu/hoary/backports/gnokii_0.6.5-1~5.04ubp1_i386.deb[/url]
libGnokii: [http://sethkinast.com/ubuntu/hoary/backports/libgnokii2_0.6.5-1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/libgnokii2_0.6.5-1~5.04ubp1_i386.deb)
libGnokii_dev: [http://sethkinast.com/ubuntu/hoary/backports/libgnokii2-dev_0.6.5-1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/libgnokii2-dev_0.6.5-1~5.04ubp1_i386.deb)

smsd: [http://sethkinast.com/ubuntu/hoary/backports/gnokii-smsd_0.6.5-1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/gnokii-smsd_0.6.5-1~5.04ubp1_i386.deb)
smsd (mysql): [http://sethkinast.com/ubuntu/hoary/backports/gnokii-smsd-mysql_0.6.5-1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/gnokii-smsd-mysql_0.6.5-1~5.04ubp1_i386.deb)
smsd (pgsql): [http://sethkinast.com/ubuntu/hoary/backports/gnokii-smsd-pgsql_0.6.5-1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/gnokii-smsd-pgsql_0.6.5-1~5.04ubp1_i386.deb)
Hi! 
Are there any existing instructions or links to detailed step by step instructions to install Gnokii on a 5.10 for a newbie that knows nothing about installing anything in Ubuntu 5.10? I am trying to help my brother get his phone working so he can kill the last Windows box in his house. We have NO clue how to compile (if that's needed) to get this app running. Any help would be greatly appreciated.

---

