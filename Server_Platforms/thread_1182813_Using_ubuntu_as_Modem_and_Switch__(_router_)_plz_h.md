---
title: "Using ubuntu as Modem and Switch  ( router ) plz help mee"
date: 2009-06-09
forum: Server Platforms
---

### Post by creation39 on 2009-06-09
hi,

I just wanted to know if its possible and how if it is possible to do that usIng ubuntu
Here is my situation, am currently using a bad Isp name Nomad, that seriously leading me to depression, due to the lack of the Phone Cable i cannot get Adsl or any other connection coming from the telephone line, so i am using Wimax that do sucks :( 
But i got an Idea last night but i got no Router for doing and got no cash for buying one too... 
what i got is an amd athlon x32 pc with 512 MB ram /1,7ghz n gforce 5500 with 4 Gig Hdd < enough to run ubuntu : ) > 
i wanted to know if my neighbour [COLOR=Red]Usb [/COLOR]Adsl modem could plugin to the [COLOR=Orange]ubuntu[/COLOR] pc and then 
dial on the [COLOR=Blue]ISP[/COLOR] network so that the[COLOR=Orange] ubuntu[/COLOR] pc do get[COLOR=SeaGreen] internet connectivity[/COLOR] and then split that connection using[COLOR=Green] two Lan pci cards[/COLOR], One to his Pc and One to mine  ?
ANd if that is possible < further on adding a firewall on ubuntu to filter bad packets n for a good port fOwarding  > 
More infO
my Friend is running on Xp Pro
and Me on Ubuntu 9.04 and Windows 7 

Any replies will be highly appreciated Thanks in AdVance : )

P.s. am not stealing his connection, i already talk to him n we are going to pay the bill 50 / 50 = D

---

### Post by zharmad on 2009-06-09
Ok, so what I understand from your post is that you want to use the Ubuntu box to share the DSL modem (connected via USB) with your friends system and your windows 7 system via ethernet. As a quick question, do you have a switch availible? It would eliminate the need for crossover cables. Setting up NAT using IPTables is entirely possible, and I urge you to take a look at [http://www.section6.net/wiki/index.php/Setting_up_a_Firewall_NAT_using_IPTables](http://www.section6.net/wiki/index.php/Setting_up_a_Firewall_NAT_using_IPTables).

---

### Post by creation39 on 2009-06-10
Yes you got it right X) zharmad, i do have a switch but the problem is that is a 24 ports switch which i usually use to make lan party btw friends x) n its damn big, i wanted to prevent from using that big stuff but if its get complicated then mayBe i will use it : )

But i wanted to know too if the Adsl usb modem is perfectly recognised by ubuntu
its a sagem one ...
Thanks for the quick reply too ;)

---

### Post by zharmad on 2009-06-10
It appears that the eagle-usb driver supports a number of sagem modems, without knowing exactly what model you have I couldn't say for certain. You can check out some more information here [http://faq.eagle-usb.org/wakka.php?wiki=ModemSupport](http://faq.eagle-usb.org/wakka.php?wiki=ModemSupport).

---

### Post by creation39 on 2009-06-11
Omg Thanks zharmad, it seems to be the first ONe
SAGEM FAST 800
I must try that with Ubuntu =D on Saturday lol ^.^ 
I will get my Lan Cable on Friday :p 
i just need to get my electric cable Running x) 
But how do we do Internet Sharing on Ubuntu as i guest its nt as easy as Windows Xp nan ?
Well i just surf n surf n see that maybe i will be Using ebox for acting as a router / firewall :D

---

