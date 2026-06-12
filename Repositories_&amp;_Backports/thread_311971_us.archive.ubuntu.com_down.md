---
title: "us.archive.ubuntu.com down??"
date: 2006-12-03
forum: Repositories &amp; Backports
---

### Post by golfing22 on 2006-12-03
:confused: Is us.archive.ubuntu.com down or is it just me???:confused:

---

### Post by atoponce on 2006-12-03
Remove 'us' from the url.  Or, search/replace all the urls with official mirrors from download.ubuntu.com in your /etc/apt/sources.list.

---

### Post by 64mgb on 2006-12-03
I'm pretty much a newbie, but I don't think this is the right answer.  My sources.list file has always had us.archive.ubuntu.com and it has always worked.  But just in the last couple of hours it has quit working.  If I take the "us" off it works but I don't think I'm getting the right stuff.  I tried doing "sudo apt-get install kernel-source" and I got source for the 2.4.27 kernel...it should be 2.6.17.

I'm sure someone will correct me if I have this wrong.

Rich

---

### Post by Mau on 2006-12-03
Down for me too (California).

Traceroute: ```
$ traceroute 146.137.96.15
traceroute to 146.137.96.15 (146.137.96.15), 64 hops max, 40 byte packets
 1  homeportal (172.16.0.1)  3.588 ms  4.667 ms  3.656 ms
 2  209-204-181-1.dsl.static.sonic.net (209.204.181.1)  17.901 ms  13.214 ms  14.658 ms
 3  110.at-4-0-0.gw4.200p-sf.sonic.net (208.106.28.173)  17.952 ms  21.581 ms  20.505 ms
 4  ge-6-2-0.408.ar4.sfo1.gblx.net (64.210.30.133)  26.076 ms  26.555 ms  28.483 ms
 5  so6-0-0-2488m.ar2.pao2.gblx.net (67.17.93.90)  33.220 ms  34.446 ms  32.565 ms
 6  esnet-1.ar2.pao2.gblx.net (208.50.13.54)  32.046 ms  40.410 ms  34.579 ms
 7  snv-paix-pa.es.net (134.55.208.206)  36.710 ms  31.872 ms  30.577 ms
 8  snv1mr1-snvcr1.es.net (134.55.218.22)  30.554 ms  30.959 ms  32.446 ms
 9  snv2mr1-snv1mr1.es.net (134.55.217.6)  32.175 ms  46.831 ms  32.147 ms
10  snv2sdn1-snv2mr1.es.net (134.55.207.37)  32.262 ms  30.557 ms  31.329 ms
11  chicr1-oc192-snv2sdn1.es.net (134.55.209.54)  77.049 ms  79.405 ms  79.870 ms
12  anlrt2-oc12-chicr1.es.net (134.55.209.202)  83.231 ms  81.213 ms  77.645 ms
13  anlmr1-anlrt2.es.net (134.55.222.18)  75.534 ms  79.672 ms  81.778 ms
14  guava-esnet.anchor.anl.gov (192.5.170.77)  81.173 ms  72.206 ms  72.010 ms
15  fwzv662.net.anl.gov (130.202.222.65)  71.722 ms  83.508 ms  83.774 ms
16  * *^C
```

---

### Post by TrendyDark on 2006-12-03
Having the same problem here ''-_-

---

### Post by GliderMike on 2006-12-03
Yes it is down.  And I'm right in the middle of trying to install my mail server ;-)

---

### Post by TrendyDark on 2006-12-03
Found a fix, sort of. . .

```
sudo gedit /etc/apt/sources.list
```

Find every repository url that includes the "us." subdomain,

switch these to either "uk.ubuntu" or "ca.ubuntu"

I'm going with the UK repos because they are definately in english, but does anyone know if the Canadian repos are in english or french?

---

### Post by GliderMike on 2006-12-03
I simply removed the us. and it seems to be working properly.
As noted previously.

---

### Post by 64mgb on 2006-12-03
> **64mgb said:**
> I'm pretty much a newbie, but I don't think this is the right answer.  My sources.list file has always had us.archive.ubuntu.com and it has always worked.  But just in the last couple of hours it has quit working.  If I take the "us" off it works but I don't think I'm getting the right stuff.  I tried doing "sudo apt-get install kernel-source" and I got source for the 2.4.27 kernel...it should be 2.6.17.

I'm sure someone will correct me if I have this wrong.

Rich
I think I got this all wrong.  It DOES work if you remove the "us".  and the command I want ed to try was "sudo apt-get install linux-source", not "sudo apt-get install kernel-source".  I told you I was a newbie  lol.

Rich

---

### Post by TrendyDark on 2006-12-03
crud, i messed up my source list. . . anyone have the default list so i can copy it?

---

### Post by Jerb on 2006-12-03
server's been running 6.06 LAMP install

Just got torrentflux and mysql setup so I restarted my machine using the shutdown command

now the apt-get function no longer works, it attempts to connect to:
us.archive.ubuntu.com    but sits there at 99% until it times out

I've tried apt-get clean
apt-get update
but nothing works, as for my sources file, all I've done was uncomment the default respoitories 

any way to fix this would be wonderful

---

### Post by arkitect on 2006-12-03
I can't connect either. I keep getting timed out.

---

### Post by mbobak on 2006-12-03
I can't run apt-get or Synaptic, both hang when trying to retrieve data.

Is this a known problem?

-Mark

---

### Post by glennric on 2006-12-03
My guess is the server is down.  If you remove the "us" from the front you can access the general archives.  Those still seem to be working.

---

### Post by aysiu on 2006-12-03
As you can see, you're not the only ones noticing it down.

The regular repositories are working, though (minus the *us* part).

---

### Post by Jerb on 2006-12-03
any one know whats going on?



either way I'm glad to see I'm not the only one with this problem, I've been freaking out

---

### Post by Bakerconspiracy on 2006-12-03
Just update the meat of your /etc/apt/sources.list to this:


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by rcarricato on 2006-12-03
Thank god I thought it was me:p

---

### Post by Dual Cortex on 2006-12-03
> **rcarricato said:**
> Thank god I thought it was me:p

:) Same here but it seems that just until about 1 min ago they are back up.

---

### Post by Antonlacon on 2006-12-04
> does anyone know if the Canadian repos are in english or french?

English.

---

### Post by gprasanthkumar on 2011-12-19
I too have the same problem.

I tried the following:
>>updated the us.archive.ubuntu.com which didn't worked
>>updated MTU to 1480 from 1500 which also didn't worked
>>Re-installed the OS from the same CD in which earlier version worked well. And the re-installation taking around 3 to 4Hrs where as it took around 45mins earlier.

Any suggestions on resolving the problem will be very much appreciated.

---

### Post by lisati on 2011-12-24
Hey guys, this thread is five years old, during most of which time it has been asleep!

---

