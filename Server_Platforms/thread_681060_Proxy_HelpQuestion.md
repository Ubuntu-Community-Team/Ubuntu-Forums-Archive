---
title: "Proxy Help/Question"
date: 2008-01-28
forum: Server Platforms
---

### Post by coolbeansdude51 on 2008-01-28
Hello forum,

I have a set up where a router (a WRT54GL) is being used at a local coffee shop.  The owner would like to know if there is a way to keep track of where all the users are going on the internet.  I said I think a proxy server could do this. Also he wants to block porn and other sites that are potentially bad.  The server could not be at the location so it would have to be hosted in a different location.

Is it possible to do this and if so with what software/how?

Thanks for sharing your wisdom!
coolbeansdude51

---

### Post by coolbeansdude51 on 2008-01-28
Would something like this work?
[http://ubuntuforums.org/showthread.php?t=320733](http://ubuntuforums.org/showthread.php?t=320733)

---

### Post by Maxtorm on 2008-01-28
Yes, it would. You may also want to take a look at Clark Connect ( [http://www.clarkconnect.com/](http://www.clarkconnect.com/) ). It includes the services referenced on the page you linked as well VPN, mail services, etc. It has a nice web-baed GUI and is relatively easy to administer. However, why the restriction on the location of the server? If there is enough space for a WRT router, presumably you would have enough space for a small form factor computer -- perhaps a Shuttle PC?

---

### Post by coolbeansdude51 on 2008-01-28
Humm interesting.  

Would that make a difference in speed ... etc?

We would use this for a commercial app.

Any suggestions?

---

### Post by Maxtorm on 2008-01-29
I have a Clark box running on an old Pentium III 500 with 256 MB of RAM. The configuration pages are a little slow sometimes, but the proxy throughput speed is very quick. However, I only have a couple of users on it right now. There is a page on the Clark site that goes into the recommended specs based on how many users you intend to serve and how many services you intend to run.

Not sure I understand the question about the "commercial app." What do you mean?

---

### Post by coolbeansdude51 on 2008-01-29
Sorry about that.

Thanks for your help/wisdom so far.

When I mentioned commercial app.  I was referencing something that I had not explained ... :oops:

My question is would have a WRT54GL router connected to a squid proxy server that uses the filtering software mentioned in the post be something that you think would work commercially?  Is it stable enough?  Is it fast enough?  Does it have the features we require? 

Thanks so much!
-Coolbeansdude51

---

### Post by Maxtorm on 2008-01-29
Yes, I would think so. Certainly will be stable enough if you're going to run it on an Ubuntu Server box. Speed will not be an issue. It has the features you require, though it does not include anti-virus. Dansguardian does have a ClamAV plug-in, but I don't think the post refers to installing it (it *is* referred to on the third page of the post). Hope that helps.

---

