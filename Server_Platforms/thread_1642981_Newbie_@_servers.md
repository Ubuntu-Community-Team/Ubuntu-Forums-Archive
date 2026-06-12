---
title: "Newbie @ servers"
date: 2010-12-11
forum: Server Platforms
---

### Post by jesuisbenjamin on 2010-12-11
Hello there,

I'd like to figure out how servers are working and learn how to use PHP SQL etc properly.
Using free hosting online is a pain, there is little info and much limitations.

I'm a newbie when it comes down to servers, i'd like to learn how to set up a server (on an old computer) with Ubuntu, and use it as a platform to host a dummy site, use SQL, run cron jobs etc.

Is there any good tutorial for this? Thanks.
Benjamin

---

### Post by Wader_WS on 2010-12-11
well if your looking for a nice quick way to learn when your out and about then i highly recommend XAMPP or WAMP/LAMP.

Those are both webservers that include Apache, PHP and SQL. XAMPP also supports Pearl. They can both be used on windows and linux as a localhost server. 


If your looking to setup a dedicated box with ubuntu server, then when your installing you should select LAMP and OpenSSH to be installed, that will allow you to use commands over your network rather than going to your server to install things. 

Once install you have a selection of options. I personally would go with webmin and phpMyAdmin and that should see you on the way to learning some PHP ect. However there are many other options which could be used but imo those are the best. 

When i was learning PHP + SQL i found that W3schools is the best site. However there are many out there. I know [www.Lynda.com](www.Lynda.com) have good tutorials, although you have to buy a subscription with them. 

hope it helps :)

~Wader

---

### Post by jesuisbenjamin on 2010-12-11
Hi there!

Thanks, i have learnt with W3School, i really liked it, but never practiced.

So i am not sure i understand everything:
XAMP, WAMP or LAMP are installed _on_ Ubuntu Server?
With OpenSSH, i then can play around with my server from my desktop through the network?
PhPmyadmin is for working on SQl right?

And another question: if i have a server on a separate box at home, can it be accessed from anywhere on the net? I imagine the server address is an IP only then?


(I told you i _really_ am new at that :) )

---

### Post by jesuisbenjamin on 2010-12-12
Hi there!

Well i installed on my laptop: Apache2, Php5, Mysql, phpmyadmin etc. all following a tutorial online. (This is just for me to test and play around with the idea of a server).
First i must say i am not very sure as to what's going on on my computer, because none of this is visual and i am used to visualising the software and data i am using. What is Apache really doing and where is it? 
Second i tried to connect to my server from another computer connected through the net on the same modem/router. Connection went fine. Does this mean anyone can connect to my server through the internet? Is it that simple?

Can you tell me more? The tutorials assume i should know all this.

Thanks.
B.

---

