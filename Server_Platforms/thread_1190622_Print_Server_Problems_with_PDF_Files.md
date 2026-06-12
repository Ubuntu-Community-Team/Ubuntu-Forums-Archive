---
title: "Print Server Problems with PDF Files"
date: 2009-06-18
forum: Server Platforms
---

### Post by xyvian on 2009-06-18
So I have had my print server up and running for about a year now (thanks to all of your help :D ) however I now have a new and irritating problem. I recently bought a new laptop which is running Vista. This laptop is set up to print to my print server wirelessly, and does so flawlessly. Until I tried to print out a PDF file a week or so ago and could not. In fact it would appear that my server never actually receives the job from the laptop (as the cups web administrator has not received a single job). 

Microsoft Office prints normally, as do the other programs one could print from. I have tried Adobe Reader as well as Foxit, but it does not appear to be a problem with that. In fact the machine will say that it has successfully finished printing after it gets done "sending" the job. I tried updating the driver and it did not work either.

From my windows XP machines there have never been a single problem. 

My printer is an HP PSC 1315, an all-in-one. Computer is running Vista Home Premium x86. 

My cupsd.conf is attached, please look through it if you think it will help.

Please give any advice, as I am unsure as to whether I should continue searching for problems with the Vista machine or with the server.

Responses are appreciated,
Brian

---

### Post by HermanAB on 2009-06-18
You can just send the PDF file straight to the print server and it will print it for you.

Here are the basics on LPR:
[http://aeronetworks.ca/print-howto.html](http://aeronetworks.ca/print-howto.html)

Although that is for Linux, it may help you understand the problem.

---

