---
title: "How can I stop my ISP throttling my LAMP server?"
date: 2008-08-31
forum: Server Platforms
---

### Post by muramura on 2008-08-31
Hello all,

I'm running a basic LAMP server, and recently its speed has slowed down to a crawl due to ISP throttling.  I've done some speed tests, and downloading a normal file over http continually decreases speed, and levels off at about 10kbps.  HTTPS is not much better, also levelling off at about 20-30kbsp.

So what can I do to stop this?  I'm a complete newb at this.  Packet encryption?  But how would the reciever know to expect it's encrypted?  A special router?  Port spoofing? (Lol - if there is such a thing!)  I'm at a loss and desperate!  Please advise!

(P.S. I'm paying for 16mb dl, 1mb up!  Other programs, even torrents, are blazingly fast down and up)

---

### Post by windependence on 2008-08-31
How do you KNOW they are doing this?

If your other stuff is blazingly fast, it's probably NOT your ISP, but something that you have misconfigured. What exactly is slow besides "speed tests" (which are most of the time highly inaccurate BTW)?

-Tim

---

### Post by muramura on 2008-08-31
That's a good question.  The speedtest that I did was very simple.  I put links to large files on my site, and downloaded them from afar.  One file over http, the other https.  As I download them one at a time, firefox told told me the speed.  It starts off fast-ish, but slows to a crawl within seconds, levelling off at almost exactly 10kbps.  Meanwhile, with htop I see my server cpu usage is 0%.

If it's just something I've missconfigured, I'd be very happy.  Ideas?  Though I don't know how one can accidental configure a server to upload slowly.

---

### Post by windependence on 2008-08-31
Ahhh OK, well I hate to break it to you but for web serving you need high upload speed, NOT download speed. MOST ISPs upload speeds are pathetically low because as a regular web client you don't need a high up speed, just a good download speed, so you know all those blazingly fast speeds they advertise on TV? Forget it for serving.

Try this test and see what you get:

[http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/)

-Tim

---

### Post by muramura on 2008-08-31
I think you're wrong about this.  It's throttling.  I get almost 1mbps upload speed on all speedtests - which should be more than enough for a simple website to load quickly.

---

### Post by mellowd on 2008-08-31
What happens if you try and ftp from your server?

---

### Post by muramura on 2008-08-31
I never installed ftp for security reasons, but might do so now for testing.  But they could throttle ftp uploads too...

Basically my internet is very fast for almost every normal use.  With the speed that I have (1mbps upload), no one could reasonably expect <10k download speed from my site.  I'm convinced it's throttling, and need help getting around it. :)

---

### Post by mellowd on 2008-08-31
The easiest thing to do is simply phone them up and ask them. 

I would test with ftp first, you can always remove the daemon afterwards

---

### Post by muramura on 2008-08-31
I did phone, and the lady I spoke with didn't even know what a port was.  She admitted they do "kinda slow some stuff down" she thought, but all that information is kept hush hush for pr reasons.

I'll try an FTP test to be certain.  Are there any better ways to test speed though?  I'm sure my ISP throttles FTP servers just as badly as web servers, so I don't think it will be a very scientific test.

---

### Post by mellowd on 2008-08-31
> **muramura said:**
> I did phone, and the lady I spoke with didn't even know what a port was.  She admitted they do "kinda slow some stuff down" she thought, but all that information is kept hush hush for pr reasons.

I'll try an FTP test to be certain.  Are there any better ways to test speed though?  I'm sure my ISP throttles FTP servers just as badly as web servers, so I don't think it will be a very scientific test.

Ask for your call to be escalated. Tell them that's an unacceptable answer.

You won't be sure until you test. Test first and you can progress from there

---

### Post by muramura on 2008-08-31
Can't easily install ftp... proftpd relies on php4 for some damn reason.  I have 5.

turck-mmcache: Depends: php4-cli but it is not installable
               Depends: phpapi-20050606 but it is not installable

---

### Post by mellowd on 2008-08-31
[http://ubuntuforums.org/showthread.php?t=218630](http://ubuntuforums.org/showthread.php?t=218630)

---

### Post by muramura on 2008-08-31
Exact same problem.  Requires turck-mmcache, which requires php4, which is uninstallable.

---

### Post by mellowd on 2008-08-31
[http://www.linux.org/apps/AppId_7396.html](http://www.linux.org/apps/AppId_7396.html)

---

### Post by windependence on 2008-08-31
> **muramura said:**
> I did phone, and the lady I spoke with didn't even know what a port was.  She admitted they do "kinda slow some stuff down" she thought, but all that information is kept hush hush for pr reasons.

I'll try an FTP test to be certain.  Are there any better ways to test speed though?  I'm sure my ISP throttles FTP servers just as badly as web servers, so I don't think it will be a very scientific test.

I'm tellin' ya, you guys are barking up the wrong tree.

First, are you in the US and who is your ISP? This is just generally not done, in fact, there was just a case with Comcast where they refused to let them throttle peer to peer traffic. Something else is going on, and it could be something as simple as your NIC card or a network configuration. I would bet money it's not your ISP.

[http://www.downloadsquad.com/2008/01/08/comcast-could-receive-hefty-fcc-fine-for-throttling-bit-torrent/](http://www.downloadsquad.com/2008/01/08/comcast-could-receive-hefty-fcc-fine-for-throttling-bit-torrent/)

[http://www.publicknowledge.org/node/1670](http://www.publicknowledge.org/node/1670)

> Almost exactly two years ago today, the FCC issued its order allowing Comcast and Time Warner to divide up the bankrupt Adelphia cable and swap systems between them. MAP, on behalf of Free Press and others, pressed the FCC to adopt a bunch of conditions designed to make sure Comcast and Time Warner did not block or degrade content. The FCC declined, siding with Comcast in the belief that emerging competition would keep Comcast from trying to mess with content or applications.

But the FCC didn&#8217;t stop there. It went on to say:

    If in the future evidence arises that any company is willfully blocking or degrading Internet content, affected parties may file a complaint with the Commission

Note that this was throttling *download* speeds, not uploads. They really don't care about that.

That was the reason I wanted you to do the speed test, to find out what your upload was. Are you SURE you weren't reading the download speed? Here, one of our local cable companies limits their upload to a mere 35kps. MOST ISPs have nowhere near their download speed as upspeed. It is possible however, as I have 1.5 up and down, but I am lucky, most don't.

-Tim

---

### Post by Vegan on 2008-08-31
Tesing my connection from that speakeasy link I got 

31549 kbps download and 884 upload. This is typical for ISPs. Very asymmetrical. Very.

I use HTTP compression to compensate as best I can. It is not widely used but I suggest adopting it.

---

### Post by skunkbad on 2008-08-31
I'd try another ISP. I'm in Southern California, and I use dslextreme.com. I haven't had any problems with my connection, and while not the fastest of connections, you wouldn't know it by going to one of the sites that are hosting on my server.

---

### Post by muramura on 2008-08-31
Yeah, I'm switching ISPs... or at least getting a second one and I'll see how they go.  I have great speed, but they throttle it.

Great if it worked...
[IMG]http://www.speedtest.net/result/316311573.png[/IMG]

I live in Toronto, Canada, and throttling is a bit more common here I think.

To make matters worse, there are basically only 2 ISPs throughout the whole country.  Bell and Rogers.  Most other companies piggy-back off bell's dsl lines for example, so when bell throttles your ISP, even they are unable to do anything.  It's basically a government sanctioned monopoly.

So back to my original question - assuming they are throttling me, is there no way to prevent it?

---

