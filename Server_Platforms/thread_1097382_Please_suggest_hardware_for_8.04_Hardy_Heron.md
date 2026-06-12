---
title: "Please suggest hardware for 8.04 Hardy Heron"
date: 2009-03-15
forum: Server Platforms
---

### Post by neoman on 2009-03-15
Hello everybody,

I am seriously considering  to ether purchase or put together my own server for the purpose of hosting my site which is PHP based and is pretty busy with over 110k visitors a day. Having said that i need a server that will be able to handle 2 million visitors. I am planing on installing 8.04 LAMP server Hardy Heron. 

My questions:

1) What server name would you suggest? DELL, HP etc OR

2) What hardware would you suggest if were to put it together? I really dont want to go over $1,000 but i am not sure if its possible. 

3) Are there any good tutorials on how to set up my own web server?


Thank you so much!

---

### Post by neoman on 2009-03-16
does anybody has any opinion? any experience? any suggestion?

---

### Post by real_magiz on 2009-03-17
buy HP DC 7800. ok?

---

### Post by JeppeM on 2009-03-17
Hey... We have a collection of php sites which pull in 200k unique visitors and around 3 mil pageviews per month... The server handling this is a Xeon 5160 3.0 GHz with 4 gig ram - So i guess you should try to look for something in the range of a at least a Dual cored 2.8 Ghz and min. 3 gig ram... The rest is pretty much up to you. 

As for a guide, have a look at this one: [http://howtoforge.com/perfect-server-ubuntu8.04-lts](http://howtoforge.com/perfect-server-ubuntu8.04-lts) (you only need apache, mysql and php most likely) - Or browse howtoforge for other howtos about the subject :)

---

### Post by neoman on 2009-03-17
JepperM, thank you so much, i am thinking about buying quad core 2.8 with 1333 FSB, also thinking about 4 GB @ 800Mhz ram with two raid HD @ 250 GB ea. I guess my biggest concern is installing and making Ubuntu run smoothly... i dont want to spend $1200 just to find out that my hardware is not compatible...

By the way the mobo i am looking into is this one [HERE]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128369")

Also, can anyone tell if building just a regular strong pc is good for a server? or should i use the server parts on new egg (which are more expensive for some reason)? 

Thank you so much!

---

### Post by windependence on 2009-03-18
If you're doing that much traffic, you really need a server class mobo, and more spindles in RAID 5 or 6 for performance. I am biased because I run most all my webservers on FreeBSD, but if you want to run on Linux, then I would seriously consider Tyan or SuperMicro for the board. Consider using virtualization (the real, bare metal kind like ESXi) 

My main web server is on a SuperMicro board, with dual AMD quad core Opterons, and 12 GB of RAM, however, I plan to host somewhere around 20 virtual boxes on that machine. The box has 4 SATA II hard drives in RAID 5 (hardware), and 4 GB NICs. I did cost me $2,000 to build though, and I did not buy parts retail as I am a parts reseller.

I think you may be making a mistake by using a desktop mobo. This is the heart of your machine.

-Tim

---

### Post by neoman on 2009-03-18
thanks Tim, i appreciate your advice, i will look into it...

---

