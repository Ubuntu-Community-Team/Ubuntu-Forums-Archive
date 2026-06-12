---
title: "Problem getting weather data"
date: 2009-11-28
forum: The Cafe
---

### Post by 5BallJuggler on 2009-11-28
Is any one else having a problem connecting to [http://xoap.weather.com](http://xoap.weather.com), 

my conky script has not been working correctly for a couple of days now and I think the site might be down, can anyone else access it?

Cheers
Phil

---

### Post by earthpigg on 2009-11-28
site looks up to me.

but the website probably changed some of it's innards so that your script points to stuff that is now in a different location.

---

### Post by 5BallJuggler on 2009-11-28
> **earthpigg said:**
> site looks up to me.

but the website probably changed some of it's innards so that your script points to stuff that is now in a different location.

That is odd, I can't "Ping" the site from a terminal either

Any ideas???

Phil

---

### Post by earthpigg on 2009-11-28
odd. i cannot ping it either.

but i can wget it...

```
[chris: ~]$ wget [http://xoap.weather.com](http://xoap.weather.com)
--2009-11-28 17:17:37--  [http://xoap.weather.com/](http://xoap.weather.com/)
Resolving xoap.weather.com... 65.212.118.29
Connecting to xoap.weather.com|65.212.118.29|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 114696 (112K) [text/html]
Saving to: “index.html”

100%[======================================>] 114,696      195K/s   in 0.6s    

2009-11-28 17:17:37 (195 KB/s) - “index.html” saved [114696/114696]

[chris: ~]$ cat index.html

--html code here--
```

---

### Post by earthpigg on 2009-11-28
however, something i have seen that may be of note that i just recalled...

i use curl to find my ip sometimes.

from .bashrc:

```
alias myip='echo My IP is && curl [http://www.whatismyip.com/automation/n09230945.asp](http://www.whatismyip.com/automation/n09230945.asp) && echo'
```

so:

```
[chris: ~]$ myip
My IP is
xxx.xxx.xxx.xxx
[chris: ~]$
```


if i do it a bunch of times in a row, however, it stops working and i cannot ping the site either.

iirc, i had to email the website and tell them i was testing/tweaking my .bashrc, that my usage would not normally be like that, and ask them to unban me. which they where nice enough to do.

i could still visit the website in my web browser when i was banned.

---

### Post by 5BallJuggler on 2009-11-28
> **earthpigg said:**
> odd. i cannot ping it either.

but i can wget it...

```
[chris: ~]$ wget [http://xoap.weather.com](http://xoap.weather.com)
--2009-11-28 17:17:37--  [http://xoap.weather.com/](http://xoap.weather.com/)
Resolving xoap.weather.com... 65.212.118.29
Connecting to xoap.weather.com|65.212.118.29|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 114696 (112K) [text/html]
Saving to: &#8220;index.html&#8221;

100%[======================================>] 114,696      195K/s   in 0.6s    

2009-11-28 17:17:37 (195 KB/s) - &#8220;index.html&#8221; saved [114696/114696]

[chris: ~]$ cat index.html

--html code here--
```

This is all I get-
```

phil@phil-netbook:~$ wget http://xoap.weather.com
--2009-11-29 01:24:56--  http://xoap.weather.com/
Resolving xoap.weather.com... 63.111.24.129
Connecting to xoap.weather.com|63.111.24.129|:80...failed: Connection timed out.
Retrying.

--2009-11-29 01:28:06--  (try: 2)  http://xoap.weather.com/
Connecting to xoap.weather.com|63.111.24.129|:80... 

``` 

and it just sits there

---

### Post by 5BallJuggler on 2009-11-28
> **earthpigg said:**
> however, something i have seen that may be of note that i just recalled...

i use curl to find my ip sometimes.

from .bashrc:

```
alias myip='echo My IP is && curl [http://www.whatismyip.com/automation/n09230945.asp](http://www.whatismyip.com/automation/n09230945.asp) && echo'
```

so:

```
[chris: ~]$ myip
My IP is
xxx.xxx.xxx.xxx
[chris: ~]$
```

if i do it a bunch of times in a row, however, it stops working and i cannot ping the site either.

iirc, i had to email the website and tell them i was testing/tweaking my .bashrc, that my usage would not normally be like that, and ask them to unban me. which they where nice enough to do.

i could still visit the website in my web browser when i was banned.

I'm using the script in a Conky function, but I only call it once every hour, I suppose it could be an issue where I have been banned for over using, but surely other conky users would have the same problem if they use the conkyforecast script?

Phil

---

### Post by blueshiftoverwatch on 2009-11-28
> **5BallJuggler said:**
> Is any one else having a problem connecting to [http://xoap.weather.com](http://xoap.weather.com),
If that's the site that the weather applet on my taskbar connects to, yes. At first I thought it was just the city I lived near being down. So I tried other cities and none of them worked either.

---

### Post by cariboo on 2009-11-28
I use it for the weather applet in gnome-do docky, it is working fine here. I have to enter a code number to get it to work, in my case it is CAXX0542.

---

### Post by 5BallJuggler on 2009-11-29
> **cariboo907 said:**
> I use it for the weather applet in gnome-do docky, it is working fine here. I have to enter a code number to get it to work, in my case it is CAXX0542.

I have set the code to UKXX0017, which is the closest location to where I live, and I have registered on the site when I first started using conky weather (about 10 months ago) it just stopped working, I have tried accessing it from other PC's on my home network, all to no avail

Is there anyone in the UK who can see if they can access the site 

[http://xoap.weather.com](http://xoap.weather.com)

---

### Post by pborman on 2009-11-30
Cannot access weather.com from any machine on my broadband network here either, but works fine from my mobile on 3g. I think the problem is a router on the orange broadband network (my broadband is from orange/wanadoo), perhaps someone with more technical knowledge can shed some light on this. Traceroute [www.weather.com](www.weather.com) gets stuck with no reply from ashburn.opentransit.net 

Traceroute gives this (ignore hop 1, tenda is my home network router)

traceroute to [www.weather.com](www.weather.com) (65.212.121.21), 30 hops max, 60 byte packets
1  tenda (192.168.1.250)  0.833 ms  1.138 ms  1.455 ms
2  217.47.105.58 (217.47.105.58)  49.193 ms  58.696 ms  62.614 ms
3  217.47.105.145 (217.47.105.145)  62.874 ms  63.189 ms  63.403 ms
4  213.1.67.78 (213.1.67.78)  73.806 ms  86.042 ms  92.429 ms
5  213.1.67.249 (213.1.67.249)  93.923 ms  94.254 ms  94.580 ms
6  87.237.20.240 (87.237.20.240)  94.879 ms  94.542 ms  94.610 ms
7  bundle-ether1.lontr1.London.opentransit.net (193.251.255.101)  94.606 ms  59.877 ms  57.861 ms
8  ge-3-3-0-0.loncr4.London.opentransit.net (193.251.242.22)  61.541 ms  61.906 ms  62.161 ms
9  so-0-0-3-0.ashtr1.Ashburn.opentransit.net (193.251.240.182)  139.739 ms so-0-1-3-0.ashtr1.Ashburn.opentransit.net (193.251.131.186)  155.943 ms so-1-1-3-0.ashtr1.Ashburn.opentransit.net (193.251.240.82)  150.466 ms
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *

---

### Post by 5BallJuggler on 2009-12-01
Guess what!

```
phil@phil-netbook:~$ traceroute www.weather.com 
traceroute to www.weather.com (65.212.121.21), 30 hops max, 60 byte packets
 1  Livebox-9930 (192.168.1.1)  4.038 ms  4.721 ms  9.531 ms
 2  217.47.108.186 (217.47.108.186)  39.910 ms  41.267 ms  44.677 ms
 3  217.47.108.161 (217.47.108.161)  46.505 ms  47.147 ms  53.279 ms
 4  213.1.67.22 (213.1.67.22)  57.000 ms  58.131 ms  58.585 ms
 5  213.1.67.249 (213.1.67.249)  59.584 ms  60.753 ms  63.126 ms
 6  87.237.20.240 (87.237.20.240)  65.928 ms  45.862 ms  47.584 ms
 7  bundle-ether1.lontr1.London.opentransit.net (193.251.255.101)  53.950 ms  40.759 ms  43.387 ms
 8  ge-5-0-0-0.loncr4.London.opentransit.net (193.251.243.34)  48.654 ms  49.385 ms  49.807 ms
 9  so-0-1-3-0.ashtr1.Ashburn.opentransit.net (193.251.131.186)  129.621 ms so-0-0-3-0.ashtr1.Ashburn.opentransit.net (193.251.240.182)  120.200 ms  121.998 ms
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *

```

Exactly the same issue for me, and I'm also on a orange, I'll give them a call, 

But I know exactly what the answer will be.....
...."sorry we do not support linux based systems"

---

### Post by pborman on 2009-12-01
Doesn't matter what system you are on, my windows boxes can't ping weather.com either, just times out.

---

### Post by 5BallJuggler on 2009-12-03
> **5BallJuggler said:**
> Guess what!

```
phil@phil-netbook:~$ traceroute www.weather.com 
traceroute to www.weather.com (65.212.121.21), 30 hops max, 60 byte packets
 1  Livebox-9930 (192.168.1.1)  4.038 ms  4.721 ms  9.531 ms
 2  217.47.108.186 (217.47.108.186)  39.910 ms  41.267 ms  44.677 ms
 3  217.47.108.161 (217.47.108.161)  46.505 ms  47.147 ms  53.279 ms
 4  213.1.67.22 (213.1.67.22)  57.000 ms  58.131 ms  58.585 ms
 5  213.1.67.249 (213.1.67.249)  59.584 ms  60.753 ms  63.126 ms
 6  87.237.20.240 (87.237.20.240)  65.928 ms  45.862 ms  47.584 ms
 7  bundle-ether1.lontr1.London.opentransit.net (193.251.255.101)  53.950 ms  40.759 ms  43.387 ms
 8  ge-5-0-0-0.loncr4.London.opentransit.net (193.251.243.34)  48.654 ms  49.385 ms  49.807 ms
 9  so-0-1-3-0.ashtr1.Ashburn.opentransit.net (193.251.131.186)  129.621 ms so-0-0-3-0.ashtr1.Ashburn.opentransit.net (193.251.240.182)  120.200 ms  121.998 ms
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *

```

Exactly the same issue for me, and I'm also on a orange, I'll give them a call, 

But I know exactly what the answer will be.....
...."sorry we do not support linux based systems"

I've got no further, 
it seems I can ping the ashburn.opentransit.net location, so I think this is OK.

is there a way of finding out which location comes next??

---

### Post by 5BallJuggler on 2009-12-03
However, I did find this website,

It gives a visual representation of the traceroute path...
....cool!

[http://www.yougetsignal.com/tools/visual-tracert/](http://www.yougetsignal.com/tools/visual-tracert/)

---

### Post by pborman on 2009-12-06
Definitely a router problem at ashburn.opentransit.net, others are reporting problems accessing various sites from uk to usa through ashburn. Google for ashburn.opentransit.net 

Don't know we can do about it or how to report it.

If you use a proxy server to get off the orange network the problem goes away but I don't know of a free one.

---

### Post by blueshiftoverwatch on 2009-12-06
My weather data taskbar applet is functioning properly now.

---

### Post by pborman on 2009-12-17
Screenlets weather applet is working properly since last night, the problem at ashburnopentransit.net seems to be fixed as traceroute shows the route goes through the same path but doesn't get stuck now

---

### Post by bitsmart on 2010-03-09
When I was setting up Conky and trying to get the weather part configured, I dug around on weather.com and found that they want you to register to get access to the on-demand stuff as if you were going to embed it in a website. They also place restrictions on how often you are allowed to refresh it. Best to explore alternatives IMHO.

Weather On Your Website Registration
[https://registration.weather.com/ursa/wow/step1?from=WOWsSalesPage](https://registration.weather.com/ursa/wow/step1?from=WOWsSalesPage)

---

