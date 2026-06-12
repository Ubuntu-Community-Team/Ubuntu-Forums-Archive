---
title: "Squid proxy content filter with good reporting"
date: 2014-07-22
forum: Server Platforms
---

### Post by John_Haswell on 2014-07-22
Hi Guys, 

We are looking to use squid proxy for our enterprise and I am currently testing qlproxy with squid 3.3.8. I have got it to work despite the failed instruction that do not mention icap..... Anyway. now it's all setup and working I have found that the reporting functionality is very lacking. 

You can see in realtime who is browsing what but unless we hire someone to record this information as it happens it's not fit for purpose. We need to be able to produce customer reports on demand showing what people have been viewing at a defined time. We need to be able to separate the reports per AD group or AD user.


Can someone help me to find the best solution using squid for this? I have tried running a 3rd party app SARG with squid and qlproxy but I cannot reach the url to view it due to qlproxy listening on the same port. :guitar:No reason for the guitar man but I like him :-)

---

### Post by SeijiSensei on 2014-07-22
If you're using Apache, set up another virtual host that listens on a different port than the proxy and point its DocumentRoot to the SARG results.

I ended up writing a fairly complex application in PHP for a client that parses each night's Squid access log, puts the contents into a database, and provides a web-based interface to let the administrator run common queries like listing all the destinations accessed by a specific internal IP address over a specific time period.  It's a lot more flexible than SARG, but it was a reasonably substantial investment by my client.

---

### Post by John_Haswell on 2014-07-22
I don't suppose you have the ability to sell/licence this software? 

It's taken me quite sometime getting this squid proxy up and running and I think my ability to create an apache server to point to sarg would be very limited. 



Is there any config I can do on the current box to allow me to view that page?

---

### Post by SeijiSensei on 2014-07-22
> **John_Haswell said:**
> I don't suppose you have the ability to sell/licence this software?

I don't own it, so no, unless my client wants to make a few bucks.  It also doesn't have any hooks to work with Active Directory which seems like a requirement.  I can ask if you're curious.  They have no experience with anything like software licensing, though.  They are a healthcare provider.

> It's taken me quite sometime getting this squid proxy up and running and I think my ability to create an apache server to point to sarg would be very limited. 

Setting up Apache is much easier than Squid, especially if you're using things like c-icap.  We use that with SquidClamAV to check downloaded objects for viruses.

> Is there any config I can do on the current box to allow me to view that page?

Well if you can view the directory with a browser you should be able to see the reports.  Either use a browser on the server itself and open the URL "file:///path/to/the/SARG/directory", or export the directory to the network with NFS or Samba and open it from a client browser with a "file://" URL.

---

### Post by elico on 2014-07-28
I must admit that you are asking for something that might not be possible...
In general what you need to do is use special log format and then extract the data from there if needed assuming it is not too big.

---

### Post by jaimerosario on 2014-07-28
Maybe you should try SquidAnalyzer.

I worked with it in my last job.

It reports what user/computer/ip has been accessing.

[http://squidanalyzer.darold.net/](http://squidanalyzer.darold.net/)

---

