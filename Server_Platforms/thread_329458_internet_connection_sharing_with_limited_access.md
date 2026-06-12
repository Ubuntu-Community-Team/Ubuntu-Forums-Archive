---
title: "internet connection sharing with limited access"
date: 2007-01-01
forum: Server Platforms
---

### Post by shashi123 on 2007-01-01
i have been using ubuntu and xubuntu on two of my pc 

now my setup is like ubuntu is the server and xubuntu is client

i am using ubuntu pc as router to share internet connection so xubuntu can also surf the net

but i want to give only limited access to xubuntu 

say   i want xubuntu to only surf [www.123.com](www.123.com) [www.234.com](www.234.com) and [www.345.com](www.345.com) and i dont want xubuntu to surf any other site besides above three

i am using proxy.sh 
i have taken the help of the below mentioned url to do that and the xubuntu pc is getting its ip address via a dhcp3-server installed on ubuntu server

[http://www.aboutdebian.com/proxy.htm](http://www.aboutdebian.com/proxy.htm)

i have been trying to this for last three months and finally the above link did the trick but it 
dosent mention anything abt restricted webaccess to client pc 

can any one plz help me with this 

sorry if i am writing a really long story but it was necessory

---

### Post by adaptr on 2007-01-01
That seems like a really roundabout way to do things.
I'd set up Squid and forget about it.
You can get squid from the repositories, and configuring it to allow access to only certain web sites is about an hour work (that includes learning how it works)

I would strongly recommend you to drop the debian-learning stuff (as that page clearly identifies itself), and Google for a Ubuntu-centric iptables solution with Squid to do mandatory HTTP proxying.

---

### Post by shashi123 on 2007-01-02
thanx for ur reply i will try with squid again lets hope it works out 

can u suggest me any howto page for help regarding squid

bcoz debian link was really easy to do

---

### Post by SuperMike on 2007-01-14
I got Squid working at my office but it was a bit confusing. Besides, it's like mega-overkill for what you're trying to do. Instead, consider [[COLOR="SandyBrown"]_**Tinyproxy**_[/COLOR]]("http://www.ubuntuforums.org/showpost.php?p=683303&postcount=1").

---

