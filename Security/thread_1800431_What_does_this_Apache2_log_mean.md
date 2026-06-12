---
title: "What does this Apache2 log mean?"
date: 2011-07-08
forum: Security
---

### Post by lethalfang on 2011-07-08
For the past 2 weeks, I have seen the following 4 bizarre entires in /var/log/apache2/access.log, on my computer at work.


> 202.38.89.133 - - [27/Jun/2011:02:28:46 -0700] "GET [http://www.sciencedirect.com/](http://www.sciencedirect.com/) HTTP/1.1" 200 8300 "-" "Mozilla/4.0 (compatible; MSIE 4.01; Windows 98 )"
222.204.49.108 - - [02/Jul/2011:04:59:23 -0700] "GET [http://www.sciencedirect.com/](http://www.sciencedirect.com/) HTTP/1.1" 200 8300 "-" "Mozilla/4.0 (compatible; MSIE 4.01; Windows 98 )"
60.7.81.238 - - [06/Jul/2011:19:41:59 -0700] "GET [http://www.sciencedirect.com/](http://www.sciencedirect.com/) HTTP/1.1" 200 8300 "-" "Mozilla/4.0 (compatible; MSIE 4.01; Windows 98 )"
202.38.89.133 - - [07/Jul/2011:23:31:20 -0700] "GET [http://www.sciencedirect.com/](http://www.sciencedirect.com/) HTTP/1.1" 200 8300 "-" "Mozilla/4.0 (compatible; MSIE 4.01; Windows 98 )"


[www.sciencedirect.com]("http://www.sciencedirect.com") is an Elsevier site, where full access requires subscription. My network at work does have subscription, but where do those requests come from? Why are those requests successful? How do I get rid of them?

Thanks.

---

### Post by Doug S on 2011-07-10
I have been watching for a reply on this thread, but since I didn't see one yet I will give it a try. (I am not certain about my reply, is why I delayed waiting for someone else.)
 
I think you will find that your apache server actually returned your root web page for the "GET" request. Consider the following entries from my sever logs:
```
 
access.log.22:118.39.135.9 - - [06/Feb/2011:19:56:09 -0800] "GET http://www.ya.ru:80/ HTTP/1.0" 200 9518 "-" "Mozilla/4.0 (compatible; Synapse)"
access.log.22:67.52.36.178 - - [08/Feb/2011:01:32:03 -0800] "GET http://www.ya.ru:80/ HTTP/1.0" 200 9518 "-" "Mozilla/4.0 (compatible; Synapse)"
access.log.14:122.225.218.234 - - [08/Apr/2011:06:45:47 -0700] "GET http://www.google.com/ HTTP/1.0" 200 9518 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"

```
In my case: I know that 9518 bytes is (was) the size of my root web page; In my tcpdump logs, I can seee the traffic is my root web page.
If a subpage is asked for, then the 404 error is always returned. Example:
```
access.log.21:92.240.68.153 - - [17/Feb/2011:01:03:20 -0800] "GET http://www.dragtimes.com/images/7621-2006-Dragster-Motorcycle.jpg HTTP/1.1" 404 505 "http://random.yahoo.com/fast/ryl" "webcollage/1.135a"

```
So, I would ask you, is your root web page 8300 bytes?
For your other questions: Where from? The source IP addresses are shown, so I guess I don't understand the question. I think I explained why they seem to be successful. You cann't really get rid of such requests (well, you can block persistent stuff from given IP addresses), you just want to be sure your site is secure, and myself I don't think you have a problem.

---

### Post by lethalfang on 2011-07-10
> **Doug S said:**
> I have been watching for a reply on this thread, but since I didn't see one yet I will give it a try. (I am not certain about my reply, is why I delayed waiting for someone else.)
 
I think you will find that your apache server actually returned your root web page for the "GET" request. Consider the following entries from my sever logs:
```
 
access.log.22:118.39.135.9 - - [06/Feb/2011:19:56:09 -0800] "GET http://www.ya.ru:80/ HTTP/1.0" 200 9518 "-" "Mozilla/4.0 (compatible; Synapse)"
access.log.22:67.52.36.178 - - [08/Feb/2011:01:32:03 -0800] "GET http://www.ya.ru:80/ HTTP/1.0" 200 9518 "-" "Mozilla/4.0 (compatible; Synapse)"
access.log.14:122.225.218.234 - - [08/Apr/2011:06:45:47 -0700] "GET http://www.google.com/ HTTP/1.0" 200 9518 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"

```
In my case: I know that 9518 bytes is (was) the size of my root web page; In my tcpdump logs, I can seee the traffic is my root web page.
If a subpage is asked for, then the 404 error is always returned. Example:
```
access.log.21:92.240.68.153 - - [17/Feb/2011:01:03:20 -0800] "GET http://www.dragtimes.com/images/7621-2006-Dragster-Motorcycle.jpg HTTP/1.1" 404 505 "http://random.yahoo.com/fast/ryl" "webcollage/1.135a"

```
So, I would ask you, is your root web page 8300 bytes?
For your other questions: Where from? The source IP addresses are shown, so I guess I don't understand the question. I think I explained why they seem to be successful. You cann't really get rid of such requests (well, you can block persistent stuff from given IP addresses), you just want to be sure your site is secure, and myself I don't think you have a problem.

My "index.html" is 8039 byte.
The 3 IP addresses all came from China. And all those requests seemed to come from Windows 98 machines with IE 4.0. Due to the vulnerable reputation of Win98 and IE4, I was afraid those are compromised "zombie" computers doing things to my server, made more nervous by "200 successful" logs. 
What puzzled me is why a 3rd party website is recorded for GET. Even more curious is that I'm actually very familiar with "sciencedirect.com", a for-subscription (and many say unreasonably expensive) academic publication website by Elsevier. A few of my publications are included by sciencedirect.com. 
I'm like, this can't be just a coincidence.

---

### Post by Doug S on 2011-07-10
Sorry, but I was not clear when I asked "what is your root page size?" The transfer size shown in the apache logs will be larger than the actual file size. In my case by 280 bytes. What I actually do, verses what I said before, is look in the logs for an actual root page page "GET" and compare the transfer size. Example (notice the exact same transfer size):
```
 
61.247.204.35 - - [06/Feb/2011:13:16:01 -0800] "GET / HTTP/1.1" 200 9518 "-" "Yeti/1.0 (NHN Corp.; http://help.naver.com/robots/)"
 

```
Yes, A high percentage of undesireable activity seems to source from China these days.
I agree it seems as if it cann't be a coincidence. Do you use tcpdump and/or wireshark? If yes, you could capture such an event and look in detail at the actual network traffic.

---

### Post by SeijiSensei on 2011-07-11
I can create the identical result if it telnet to my server's port 80 and enter the following:

```

[me@host ~]$ telnet localhost 80
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
GET http://www.sciencedirect.com/

```

The server returns my default home page and creates a log entry for sciencedirect.  My guess is that you're being probed to see if the remote machine in China can exploit some security hole in your system to access Science Direct.  If it's an institutional membership, yours is probably not the only machine being probed like this.  They could be running similar probes against all the Internet-facing machines at your place of work.

---

### Post by lethalfang on 2011-07-11
> **SeijiSensei said:**
> I can create the identical result if it telnet to my server's port 80 and enter the following:

```

[me@host ~]$ telnet localhost 80
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
GET http://www.sciencedirect.com/

```

The server returns my default home page and creates a log entry for sciencedirect.  My guess is that you're being probed to see if the remote machine in China can exploit some security hole in your system to access Science Direct.  If it's an institutional membership, yours is probably not the only machine being probed like this.  They could be running similar probes against all the Internet-facing machines at your place of work.

Yes, I can reproduce the same result. Looks like nothing I should be worrying about.....

---

