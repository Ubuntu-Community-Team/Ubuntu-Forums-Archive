---
title: "www.microsoft.com runs Linux? Up to a point ..."
date: 2006-02-02
forum: The Cafe
---

### Post by linuxden on 2006-02-02
[http://news.netcraft.com/archives/2003/08/17/wwwmicrosoftcom_runs_linux_up_to_a_point_.html](http://news.netcraft.com/archives/2003/08/17/wwwmicrosoftcom_runs_linux_up_to_a_point_.html)

That just cracks me up!!!

---

### Post by Derek Djons on 2006-02-02
It's funny to read. 
I remember several years ago Bill Gates said he was interested in Linux and wanted more talking with developers. Of course the whole Linux community first laughed, than said firmly... NO.

---

### Post by fuscia on 2006-02-02
and isn't there some pic of him with his powerbook in the background? the man's no dummy.

---

### Post by Viro on 2006-02-02
Perhaps I'm being obtuse, but what's funny about the article?

---

### Post by Brunellus on 2006-02-02
[QUOTE=Derek Djons]It's funny to read. 
I remember several years ago Bill Gates said he was interested in Linux and wanted more talking with developers. Of course the whole Linux community first laughed, than said firmly... NO.[/QUOTE]
what's to prevent him from talking to Linux developers?  

Seriously.  The community's hatred of Microsoft and Bill Gates is one thing, but since the software is f/Free, he can pick it up, hire his own devs, and study it to his heart's content.  What's so wrong with that?

---

### Post by Vlammetje on 2006-02-02
[QUOTE=Viro]Perhaps I'm being obtuse, but what's funny about the article?[/QUOTE]

Don't worry about it :p It's an article from **August 2003** there is nothing in there we didn't know

---

### Post by prizrak on 2006-02-02
This has been beaten to death some years ago. The website itself is actually hosted on MS servers, ALL of their systems are MS. What happened was MS was tired of getting DDoS'ed all the time so they hired a company that deals with load balancing and their load balancers are all Linux based. Since the company's servers act as a gateway for MS's it looks like MS is running Linux.

---

### Post by TechSonic on 2006-02-02
I've said it before and I'll say it again.  Bill Gates is for Linux and open source.  The CEO of Microsoft, is not.

---

### Post by Bandit on 2006-02-02
Steve Balmer is the real jerk behind the wheel at microslappy..
Bill is just a geek thats just not very creative.
Cheers,
Bandit

---

### Post by Lord Illidan on 2006-02-02
[quote=Bandit]Steve Balmer is the real jerk behind the wheel at microslappy..
Bill is just a geek thats just not very creative.
Cheers,
Bandit[/quote]

Not creative.......but......rolling in money.

---

### Post by Malphas on 2006-02-02
Bill Gates is not for Linux and open-source.  He's indirectly referred to the proponents of FOSS as communists for Christ's sake.

---

### Post by prizrak on 2006-02-02
[QUOTE=Malphas]Bill Gates is not for Linux and open-source.  He's indirectly referred to the proponents of FOSS as communists for Christ's sake.[/QUOTE]
Agreed, in fact back in the 70's Gates himself distrubuted a letter to the computer hobbyists saying that it is not only illegal but also unethical for them to share programs amongst each other. If Gates was for FOSS he would've started another company, or a foundation to fund FOSS projects, so far I am not aware of any such plans on his part.

---

### Post by linuxden on 2006-02-03
Hey,

wow!! I know the article says its not really running there site on linux just protecting themselves from ddos attacks... but its funny that Microsoft the big corp is using Linux to defend itself from such attacks.... 

If 10 years ago they had done the same with MAC servers... LMAO we would have had the same discuss...

Its cool that so many people think of Bill as an innocent geek... But i think he is not so innocent...!!! You dont get to where he is without being a shark!!! (am not saying shark in a negative way here, Mr Coca-Cola was prob one too!!!) 

Tehcsonic, just curious where can i read more about Mr Gates being for open source...?? I had always assumed that since he was the creator of such a monopolistic company that make there money from proprietary software and DRM filled programs... That he would not be for Open Source...

---

### Post by Viro on 2006-02-03
I don't think you understand, but the fact is they were using Akamai to defend them. And Akamai just happened to use Linux. What's so hilarious about that?

---

### Post by linuxden on 2006-02-03
[QUOTE=ubuntulifestyle]wow!! I know the article says its not really running there site on linux just protecting themselves from ddos attacks... but its funny that Microsoft the big corp is using Linux to defend itself from such attacks.... [/QUOTE]

Ok i will rephrase so "you" understand what i find funny...(not that it really matters but hey...)

wow!! I know the article says its not really running there site on linux just protecting themselves from ddos attacks... but its funny that Microsoft the big corp is using Linux to defend itself from such attacks "via the use of Akamai".... 

happy?

My point is that Microsoft should have there own systems to protect themselves or at least subcontract any thing they need done to people running Microsoft... and that is what i find funny... nothing more nothing less...

---

### Post by Malphas on 2006-02-03
Viro, it's humorous because Microsoft are constantly trying to spread FUD about Linux yet are using Linux (albeit indirectly) to protect their own servers rather than use a solution of their own, which according to them should be superior to what Linux has to offer.  I would have thought this was obvious.

---

### Post by Sirin on 2006-02-03
[IMG]http://www.businessweek.com/magazine/content/03_48/art03_48/0348_72inftec.jpg[/IMG]

---

### Post by Mikorist on 2008-11-03
What are most internet sites that host DNS using for their DNS? Are they using Microsoft DNS? 

What an Akamaized page looks like?
> 
Suppose you enter [www.cnn.com](www.cnn.com) in your browser. This fetches the index.html file from the cnn server. In that file there will be images which will be pointing to the Akamai servers. Those URLs look like

[http://a388.g.akamaitech.net/7/388/21/fc35...000/ad.info.gif]("http://a388.g.akamaitech.net/7/388/21/fc35ed7f236388/cnn.com/images/hub2000/ad.info.gif")
[http://a1380.g.akamaitech.net/7/1380/175/0...age/catalog.gif]("http://a1380.g.akamaitech.net/7/1380/175/03202000/www1.jcpenney.com/images/homepagev4/homepage/catalog.gif")
[http://a620.g.akamai.net/7/620/16/259fdbf4...rn_more_off.gif]("http://a620.g.akamai.net/7/620/16/259fdbf4ed29de/www.computer.com/images/learn_more_off.gif")
 

    * The number after "a", I think, identifies the customer. So 388 is cnn, 1380 is jcpenny and 620 is computer.com. Note that it is crucial to have different machine name for each customer as will become clear later.
    * I am not sure what 7 stands for but it was present in almost of the Akamaized URLs I saw.
    * Next is again the customer identifier.
    * What the following  two identifiers (21 and  fade2068e7503e for cnn) represent is not fully clear. A plausible explanation (courtesy Neal Cardwell) is  that the 14 digit hex strings are checksums of the content that path refers to. That way the name always changes if the content changes so the akamai caches at the edge don't have to worry about consistency or freshness.

    * * update (courtesy John Jacob): The hex string is created using "md5sum [file_name] |  cut -c3-16". It can also be replaced by a cache time-to -live value like "1d" for one day,  and "15m" for 15 mins. Next is the customer url itself. The path after that is identical to the path on the customer machine. So the above jcpenny URL and "www1.jcpenney.com/images/homepagev4/homepage/catalog.gif" lead to the same gif.

From: [http://research.microsoft.com/~ratul/akamai.html]("http://research.microsoft.com/~ratul/akamai.html")

```

:~$ telnet www.microsoft.com http
Trying 207.46.193.254...
Connected to lb1.www.ms.akadns.net.
Escape character is '^]'.

or

$ host -tAAAA www.microsoft.com
www.microsoft.com is an alias for toggle.www.ms.akadns.net.
toggle.www.ms.akadns.net is an alias for g.www.ms.akadns.net.
g.www.ms.akadns.net is an alias for lb1.www.ms.akadns.net.
$ host -tAAAA lb1.www.ms.akadns.net
lb1.www.ms.akadns.net has no AAAA record

```       

[img]http://i75.photobucket.com/albums/i306/mikorist/19655521250wwwmsakadnsnet1AS23NET13.png[/img]

Look : [http://www.robtex.com/dns/lb1.www.ms.akadns.net.html]("http://www.robtex.com/dns/lb1.www.ms.akadns.net.html")

Robotex & Netcraft are reporting [www.microsoft.com](www.microsoft.com) running the “impossible” combination of the Linux operating system and Microsoft-IIS/7.0 web server. 

Look :[http://uptime.netcraft.com/up/graph?site=www.microsoft.com]("http://uptime.netcraft.com/up/graph?site=www.microsoft.com")


[http://whois.domaintools.com/lb1.www.ms.akadns.net]("http://whois.domaintools.com/lb1.www.ms.akadns.net")

[b]
[color="quot"]Registrant Search: "Akamai Technologies, Inc." owns about 982 other domains
Email Search: 	is associated with about 963 domains
is associated with about 699 domains[/color]
[/b]


Akamai provides an internet-wide caching system, which can act as a symmetric defence to distributed denial of service attacks. Just as a denial of service attack funnels traffic from many different points to a single destination, Akamai's DNS servers multiplex requests for a specific hostname to the nearest point to each attacking machine in its global caching system, diminishing the effect of the attack by dividing the inbound requests amongst its many servers, and limiting the amount of DDoS traffic by localising the distance between attacker and target. Akamai presents a more challenging target for a DDoS than any single network, and would seem to be the best practical step where a distributed denial of service is directed at a hostname that the target organisation cannot reasonably take offline. 

Akamai servers are running 15,000 Linux-based servers spread around the globe.


I just wanted to share a couple more things to add to the list of why I love using linux.

Everyone else had generic responses like “Apache”, “Apache (Unix)”, “Microsoft-IIS/7.0, or “Sun-ONE-Web-Server” or secret replies with a simple “Webserver” which is a front for Akamai. 

We are seeing some positive signs around that ???

Here’s what I found: 

LOOK THIS LINK:


[http://lb1.www.ms.akadns.net/en/us/default.aspx]("http://lb1.www.ms.akadns.net/en/us/default.aspx")


Website’s Response Headers to see what web server they’re using:
```

**1.**
~$ lynx -dump -head http://microsoft.com/en/us/default.aspx
HTTP/1.1 301 Moved Permanently
Connection: close
Date: Mon, 03 Nov 2008 23:57:23 GMT
Server: Microsoft-IIS/6.0
P3P: CP='ALL IND DSP COR ADM CONo CUR CUSo IVAo IVDo PSA PSD TAI TELo OUR SAMo C
NT COM INT NAV ONL PHY PRE PUR UNI'
X-Powered-By: ASP.NET
X-UA-Compatible: IE=EmulateIE7
X-AspNet-Version: 2.0.50727
Location: http://www.microsoft.com/en/us/default.aspx
Cache-Control: private
Content-Length: 0
**2.**
:~$ lynx -dump -head http://lb1.www.ms.akadns.net/en/us/default.aspx
HTTP/1.1 200 OK
Cache-Control: public
Content-Length: 16452
Content-Type: text/html; charset=utf-8
Content-Encoding: gzip
Expires: Tue, 04 Nov 2008 00:08:05 GMT
Last-Modified: Mon, 03 Nov 2008 08:01:56 GMT
ETag: 633612673160000000
Vary: Accept-Encoding
Server: Microsoft-IIS/7.0
X-AspNet-Version: 2.0.50727
P3P: CP="ALL IND DSP COR ADM CONo CUR CUSo IVAo IVDo PSA PSD TAI TELo OUR SAMo C
NT COM INT NAV ONL PHY PRE PUR UNI"
X-Powered-By: ASP.NET
Date: Mon, 03 Nov 2008 23:58:04 GMT
Connection: keep-alive

```


1.Server: Microsoft-IIS/6.0
2.Server: Microsoft-IIS/7.0


Actually, I can't find anyone running IIS/6.0 and IIS/7.0 in same time on same site????


:guitar:

---

### Post by RATM_Owns on 2008-11-03
tl;dr

I still think that Microsoft should be able to take care of their own servers.

---

### Post by Mikorist on 2008-11-03
> **RATM_Owns said:**
> tl;dr

I still think that Microsoft should be able to take care of their own servers.

Here’s the short version :

LOOK THIS LINK:
[http://lb1.www.ms.akadns.net/en/us/default.aspx]("http://lb1.www.ms.akadns.net/en/us/default.aspx")

(this is the [http://www.microsoft.com/](http://www.microsoft.com/)  akamaized )

Website’s Response Headers to see what web server they’re using:
```

**1. orginal link **
~$ lynx -dump -head http://microsoft.com/en/us/default.aspx
HTTP/1.1 301 Moved Permanently
Connection: close
Date: Mon, 03 Nov 2008 23:57:23 GMT
Server: Microsoft-IIS/6.0
P3P: CP='ALL IND DSP COR ADM CONo CUR CUSo IVAo IVDo PSA PSD TAI TELo OUR SAMo C
NT COM INT NAV ONL PHY PRE PUR UNI'
X-Powered-By: ASP.NET
X-UA-Compatible: IE=EmulateIE7
X-AspNet-Version: 2.0.50727
Location: http://www.microsoft.com/en/us/default.aspx
Cache-Control: private
Content-Length: 0
**2. akamaized microsoft.com **
:~$ lynx -dump -head http://lb1.www.ms.akadns.net/en/us/default.aspx
HTTP/1.1 200 OK
Cache-Control: public
Content-Length: 16452
Content-Type: text/html; charset=utf-8
Content-Encoding: gzip
Expires: Tue, 04 Nov 2008 00:08:05 GMT
Last-Modified: Mon, 03 Nov 2008 08:01:56 GMT
ETag: 633612673160000000
Vary: Accept-Encoding
Server: Microsoft-IIS/7.0
X-AspNet-Version: 2.0.50727
P3P: CP="ALL IND DSP COR ADM CONo CUR CUSo IVAo IVDo PSA PSD TAI TELo OUR SAMo C
NT COM INT NAV ONL PHY PRE PUR UNI"
X-Powered-By: ASP.NET
Date: Mon, 03 Nov 2008 23:58:04 GMT
Connection: keep-alive

```

1.Server: Microsoft-IIS/6.0
2.Server: Microsoft-IIS/7.0

Actually, I can't find anyone running IIS/6.0 and IIS/7.0 in same time on same site????

:lolflag:

---

### Post by jpeddicord on 2008-11-03
February 3rd, 2006 vs November 3, 2008.

Hmmmmm... no.

---

