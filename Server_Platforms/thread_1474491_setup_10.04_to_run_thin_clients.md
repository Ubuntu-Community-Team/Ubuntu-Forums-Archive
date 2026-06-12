---
title: "setup 10.04 to run thin clients"
date: 2010-05-06
forum: Server Platforms
---

### Post by =SWF=Elias on 2010-05-06
Hey here at the ubuntu forum
 
I administrat a school in Denmark, with around 40 clients runnig xp pro and a windows 2003 server, but i read about the possibility of running a linux server, with thin clintes that can run from the server, if it has network pxe boot.
 
I was wondering if anybody now any links to a good how to page, on what is needed on the setup side of the server, and clients. To make it work. And i have to use my dhcp from the win 2003 server. Is that possible.
 
Hope somebody can help.
 
Best Mads

---

### Post by Aearenda on 2010-05-06
The Linux Terminal Server Project (LTSP) does exactly this. It can be added to standard Ubuntu, but [Edubuntu]("http://www.edubuntu.com/news/10.04-release") is the best way. [This page]("http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/") is a good place to start, and [this page]("https://help.ubuntu.com/community/UbuntuLTSP") has lots of good links. Using Windows DHCP [is documented here]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPWindowsDHCP"). Have fun!

EDIT: I just noticed that the LTSP handbook still refers to the old add-on CD. In 10.04 there is a separate Edubuntu installation disk, so you don't need an add-on, or you can press F4 at start time for the standard Ubuntu 10.04 Alternate CD and choose to install an LTSP server; this would not install the Edubuntu extras, but you can add these later.
More info on the 10.04 changes [is here]("http://jonathancarter.co.za/2010/04/21/whats-been-happening-with-edubuntu/").

There's also a useful mailing list with other school people that [you can browse or join]("https://lists.ubuntu.com/mailman/listinfo/edubuntu-users").

---

### Post by =SWF=Elias on 2010-05-06
Hey again 

Thats was fast respond. And thank you for all the info. I am looking at it right now, will post back how it goes, setting up a test environment.

---

### Post by =SWF=Elias on 2010-05-07
Hey and thanks again for all the info. got my server op and running and had the first thin client to boot from it. In a test enviroment. so it looks pretty good so far, but alot of work for a new linux user:)

---

### Post by Aearenda on 2010-05-07
There is certainly a lot to learn - and it helps if you use Linux on the desktop first before doing an LTSP setup - but you have done it faster than I did with my first LTSP setup, so congratulations!

Once it is running, there are bound to be more questions that come up. LTSP is used in other versions of Linux as well as Ubuntu, and the [k12osn mailing list]("https://www.redhat.com/mailman/listinfo/k12osn") can be very helpful in all sorts of ways.

---

### Post by =SWF=Elias on 2010-05-10
Hey Aearenda
 
Yeah you are right there will come more questions on the setup side, but i have had good luck using google to find alot of good infomation, and ofcouse the links you sent me. 
I have run the desktop version on my own laptop for alittle month or so, and it didn't come easy i used alot of houres to get to this point. and that just running one client in test enviroment getting it to boot, but your right now there are alot of setup questions.
 
Thanks for your reply.

---

