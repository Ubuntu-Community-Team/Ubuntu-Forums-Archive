---
title: "Modify FireFox for faster speeds"
date: 2010-04-22
forum: The Cafe
---

### Post by linden940 on 2010-04-22
First thing first...this is my first tutorial and hope this is helpful and easy for you to understand.

This will work on Ubuntu or windows *I have done this on XP and vista)

At the end of this tutorial there will be a video that you can watch that will help you out if you don't understand this.

The things we are going to be modifying in Firefox as said will help speed it up and is very simple to do.

Open up firefox and type into the address bar 

about:config

your going to get a warring telling you to be careful just click that off and once you got it open type this into the "filter" bar.

network.http.

then look for the following and double click on them to make the change

network.http.pipelining = True
network.http.proxy.pipelining = True
network.http.pipelining.maxrequests = 30

network.http.max-connections = 96
network.http.max-connections-per-server = 32

after you did that then just close Firefox down and reopen it and your done =)

The youtube video 
[http://www.youtube.com/watch?v=KdMOB3MUBdw](http://www.youtube.com/watch?v=KdMOB3MUBdw)


[http://kb.mozillazine.org/Firefox_:_FAQs_:_About:config_Entries](http://kb.mozillazine.org/Firefox_:_FAQs_:_About:config_Entries)  << A good place to go to learn/understand more about the Firefox about:config

---

