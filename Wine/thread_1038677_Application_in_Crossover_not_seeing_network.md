---
title: "Application in Crossover not seeing network"
date: 2009-01-13
forum: Wine
---

### Post by bereta on 2009-01-13
Hello 

I have installed the demo version of corssover Linux and I have installed Yahoo Messenger. It installed fine by the looks of it, even tho its not on the list of supported applications. The problem is that it times out when I try to log in with my ID and password. I can log in just fine to yahoo using gyache or pidgin. This leads me to believe that the application in the bottle do not have access to the network.

Are there any setting that I need to change? Has any one else had problems similar to this?

Thanks

---

### Post by pytheas22 on 2009-01-13
If you install another Internet application in CrossOver--for example the [Windows version]("http://www.mozilla.com/en-US/firefox/all.html") of Firefox--does that work?  Knowing this will help to determine where the source of the problem lies.

Also, is there a particular reason that you want to install Yahoo messenger in the first place instead of just using Pidgin or another native Linux client that supports the Yahoo protocol?  In general you're much better off using native applications.

---

### Post by bereta on 2009-01-13
I have just installed the windows version of opera and it gets online fine. So there must be a different problem than what I suspected.

And yes you are right its much simpler to use a linux program for yahoo IM but I realy want the voice and video conference function. I'm useing Gyache witch can do both video and voice but im haveing some problems with voice and video that im working on. I just want to see what the real yahoo is like on linux and then I will make a decision.

Thanks

---

### Post by pytheas22 on 2009-01-14
I looked up Yahoo Messenger in the wine database and it doesn't look like other users have had much luck getting it to work functionally.  See [this page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=7401"), and especially the tips at the bottom; there are some involving how to get around a login problem that sounds like it may be the same one you're having.

Unfortunately, your best bet is probably going to be Gyache, or using a virtual machine.

---

### Post by bereta on 2009-01-14
Thanks for the tips. 
When I do ctrl+m and then go to connection preferences I don't have the option Firewall - no proxies... must be becuse I installed yahoo 9, Il try to get a copy of 8.
Any ways on the yahoo messenger oficial site is says that yahoo relies on internet explorer to connect to the internet, so I installed IE 6 (IE 7 did not work) in the same bottle as yahoo, but still no go.

I like Gyache but if I could just get the voice to work and the webcam to show more than just a black screen it would be awsome.

Thanks

---

### Post by pytheas22 on 2009-01-16
Unfortunately I don't really have any other suggestions besides Gyache or a virtual machine.  The one thing I can think of is Skype, which now has video-chat support for Linux, although obviously that doesn't help if you need to use Yahoo.

---

