---
title: "Google Earth network link crashes server machine"
date: 2007-07-12
forum: Server Platforms
---

### Post by TomFumb on 2007-07-12
Hi, I really hope that someone can help me with this as I'm quite desparate!

I'm running apache, oracle XE, and perl (with DBI) on my Ubuntu Feisty laptop, while broadcasting an adhoc network.
This laptop generates KML, which is then sent to clients on the wireless network. 

Unfortunately, whenever the clients request a network link (KML feature), the server stops responding. I understand that not everyone will be familiar with KML or network links, but the important bit (I think) is that they send HTTP 200 requests (whatever they are) to the server. Could this be what is crashing my server? If it is, how would I configure apache to allow them?

I'm pretty sure that it isn't the load that's crashing the machine, and when I don't use network links the system runs ok.

If anyone can suggest a potential solution to this bizarre problem I will be very happy, and my dissertation will be much easier!


thanks,
tom

---

### Post by Footballkid4 on 2007-07-12
```
s that they send HTTP 200 requests (whatever they are) to the server
```
I presume that is a typo?  Clients shouldn't be sending any status codes to the server, that's the server's job.  You can't send a 200 request, the server responds 200 OK to a document request from the client, assuming that everything is in check.

You can see this by opening up a terminal and trying

```
telnet msn.com 80
GET /index.html HTTP/1.1
Connection: close


```
(Make sure you press return twice after typing Connection: close)
You'll see a 404 Not Found status code.  Then try:

```
telnet google.com 80
GET /index.html HTTP/1.1
Connection: close


```
You'll see a 200 OK response code.

**Edit:** Other than that, I can't quite understand what you need, especially without knowing how the requests are made

---

### Post by TomFumb on 2007-07-28
Hi, thanks for replying so soon Footballkid4, sorry I didn't respond quicker. I've given up on this, partly because I don't understand what's going on, but mainly because I ran out of time on this and pursued an alternative route. 

Apologies for not explaining too well. The KML I was using contained a NetworkLink, which periodically requests a CGI script when loaded in Google Earth. The CGI script will generally operate on the parameters appended to the request, including Google Earth's bounding box in lat/lon, and output KML, which is loaded directly into Google Earth (it's quite a neat idea). 
In order to function properly, the NetworkLink must receive a HTTP 200 code from the server when refreshing the NetworkLink. 

I still don't konw why this was causing my whole server machine to freeze, but I assume it must just have been getting overloaded (Oracle XE already puts huge strain on this little machine just to run, so I guess it just couldn't cope). 

Anyway, thanks for trying to help

tom

---

