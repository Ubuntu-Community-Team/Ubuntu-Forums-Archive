---
title: "A way to test remote server connection speed"
date: 2008-03-05
forum: Server Platforms
---

### Post by wxman on 2008-03-05
I don't know if this is the right spot to ask, but I've built a server using Ubuntu that will be used to host web sites. The sites are now on a dedicated Linux server in a remote location from me, which I have full access to. 

I am trying to figure out a way to test what upload/download speed the current, remote server is getting. I know how to test the speed of my connection here, but I can't figure out how to test the remote one. I hope this makes sense, I think I'm getting tired.

---

### Post by rapiscan on 2008-03-05
While this isn't very scientific, it is probably more accurate then some of the other methods:  you can upload a few largish files then download them from your server to your home pc.  Your browser will let you know the average download speed, and you'll get a good feel after a few tests.

If you want to test latency (how long it takes for a packet to get from your computer to the server) use the ping comand.
[code]ping mydomain.com[/command]
Anything under 100 ms is fine.

---

### Post by azadpanchi on 2008-03-07
Additionally if you have apache already running just create a large file in one of your apache folders on the server:
[http://esofthub.blogspot.com/2007/02/creating-large-files.html](http://esofthub.blogspot.com/2007/02/creating-large-files.html)

Then use wget to download the large file and if you get other friends or workers to run the test other places you will have a good idea.

---

### Post by odinfromvalhalla on 2008-03-07
install bing on the server then read it's manual

sudo apt-get install bing
man bing 

:)

---

### Post by wxman on 2008-03-07
> **odinfromvalhalla said:**
> install bing on the server then read it's manual

sudo apt-get install bing
man bing 

:)

It sounds like I might try this. I think what I'm trying to do is see just how much faster, if it even is, my current server is compared to the one we're building. I even contacted the server tech support to ask what speed the connection is, and they couldn't tell me. That worries me.

What I might do is install Bing on both the current dedicated server, and the one I'm building, then compare results.

---

### Post by vpsville on 2008-03-08
Since its going to be a webserver, why not use apachebench 'ab' to test its performance?  That will be much more relevant for your users and will also help you tune apache/mysql for the fastest customer experience.

---

