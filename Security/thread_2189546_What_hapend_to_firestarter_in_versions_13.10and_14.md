---
title: "What hapend to firestarter in versions 13.10and 14.04"
date: 2013-11-22
forum: Security
---

### Post by leeper69 on 2013-11-22
Hi everyone I was reading a post started by alixying200005 in todays new posts and it struk a nerve I had the same expireance about three years back. my system was being hacked by someone in china I was able to find out who his server was and block him from my system using firestarter a firewall with real time monitoring. so after typing in my reply to his post I went into xubuntu 12.4 and downloded and enabled firestarter and it functiond perfecty. then I booted 13.10 and tryed to do the same
It was missing from the repository, found the same thing in ubuntu 14.04 can anyone help with restoring this program in the next lts version? It as a easy way to deal with iptabels and more in a nice graphical interface I for one am sad to see it is gone from the newer versions and havent found anything including my lack of skills in the terminal that come close to what it can do with a few mouse clicks.

---

### Post by kansasnoob on 2013-11-23
Decommissioned:

[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

> Firestarter is abandonned software and has been removed from Ubuntu as of 2013-06-18. See bug #1183651. 

---

### Post by leeper69 on 2013-11-23
Hi kansasnoob
thanks for your input I read the bug report and from what I got from it firestarter is fully functional and it is still in the 12.4 repo I just downlode it today, also read about altranet firewall tools none of them had an  active port watcher like firestarter so unless you want to use the terminal I cant find a replacement for this gui tool. if you know of a replacement gui port watcher pleas let me know. i dont need to connect to any local networks and have sucsefuly used this gui to find intrusions so as I mentioned before I for one will miss it. am I the only one?

---

### Post by kansasnoob on 2013-11-23
I use 'gufw' now:

[ATTACH=CONFIG]248017[/ATTACH]

---

### Post by OrangeCrate on 2013-11-23
+1 for UFW. Firestarter is a dead duck.

From the command line:

```
sudo ufw enable
```

Check your install:

```
sudo ufw status
```

or

```
sudo ufw status verbose
```

which includes the latest NHL hockey scores
(just kidding)

Documentation:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by leeper69 on 2013-11-24
is ufw a real time port watcher?
will it run in gui mode? 
is ufw not finished?
am I asking for to much, if a program is droped shouldent there be one that can replace it in the newer versions?
I can use ufw but what am I going to use for a live port scanner that is all I used firestarter fo in the first place.
and I havent ben able to find anything that will replace it. I know firestarter is gone and there is nothing I can do
about that except keep looking for a replacement and if need be and I think my system has ben comprimized 
use a live cd to connect to the net and let the hacker try to get into that, kind of like tripwire in the old days
only without the honey pot.
I found a cupple of good sites on ubuntu sacurity one for psad (port scan attack detector) and the other is top 10 port scanners for ubuntu the following links will get you to them.
[http://www.unixmen.com/how-to-block-port-scan-attacks-with-psad-on-ubuntu-debian/](http://www.unixmen.com/how-to-block-port-scan-attacks-with-psad-on-ubuntu-debian/)
[http://www.binarytides.com/top-port-scanners-on-ubuntu-linux/](http://www.binarytides.com/top-port-scanners-on-ubuntu-linux/)

ps: thank you OrangeCrate for the tips there is also gufw firewall the gui version of gfw. I will be checking them out.
I checked out ufw and must be missing somting in its configuration because all I got after enabling it and typing sudo ufw status verbose in terminal was status active no NHL hockey scores. ha ha!

---

### Post by zika on 2013-11-25
(G)UFW is just a front-end to iptables. As FS also was, as far asI recall. So, nothing is really missing.

---

### Post by leeper69 on 2013-11-25
Hi zika
           thanks for answering this post!
           arnt all firewalls implamenting iptabels?
            is there any programs for ubuntu that will use netstat -tuvc and alert you of new ports being open?
            is that what the pearl skript psad is doing?

---

### Post by QDR06VV9 on 2013-11-25
There is also psad.
```
PSAD is a collection of four lightweight system daemons (in Perl and
C) designed to work with iptables to detect port scans. It features:
 * a set of highly configurable danger thresholds (with sensible
   defaults provided);
 * verbose alert messages that include the source, destination,
   scanned port range, beginning and end times, TCP flags, and
   corresponding Nmap options;
 * reverse DNS information;
 * alerts via email;
 * automatic blocking of offending IP addresses via dynamic firewall
   configuration.
```
More Here [http://www.cyberciti.biz/faq/linux-detect-port-scan-attacks/](http://www.cyberciti.biz/faq/linux-detect-port-scan-attacks/)
You Beat Me You already saw psad!:D

---

### Post by kansasnoob on 2013-11-25
Back in post #4 I posted a screenshot of GUFW.

Have you even tried clicking on the Listening Report or Log tags????

---

### Post by leeper69 on 2013-11-25
Hi kansasnoob yes I have and am running it now but as you know it is not a live port watcher for your local ip. agin thanks for answring this post.
Hi runrikus thanks for the url I will be checking it out I have implamented psad and am running it now and will be looking up fwsnort.
ps found this url for help with psad and fwsnort.
[http://www.cipherdyne.com/psad/](http://www.cipherdyne.com/psad/)
will fwsnort work with the genaric kernals in 13.10 and up?
thanks runrickus for the info it seems psad is a good port watcher but things are done through a demon.
so far this is the cosest tool to replace firestarter I can find I have it emplamented in xubuntu studio 13.10 and kde  14.04 
if an entruder has a port open on your system in terminal will sudo netstat -punt tell you what pid and ip addres thay are using?
and can you just kill the pid in system monitor to disconect the unwanted intrusion?

---

### Post by QDR06VV9 on 2013-12-01
Sorry I had not noticed you added to your request.
But this i s a very long topic best covered here [http://ubuntuforums.org/showthread.php?t=1477696](http://ubuntuforums.org/showthread.php?t=1477696)
Lots to read but worth learning.:D

---

### Post by leeper69 on 2013-12-01
Hi runrickus thanks for the url it is a varry good help page for psad, fwsnort, snort, nmap, and base. I am curently runing psad and am thinking about installing fwsnort and after reading your posted url written by bodhi.zazen I am also intrested in post as well.

---

### Post by cariboo on 2013-12-01
Moved to the Security sub-forum, as this thread has morphed into something else other than a discussion about firestrarter.

---

### Post by leeper69 on 2013-12-01
Hi cariboo907 thanks for the moove I am just trying to find a replacement for the port watcher in firestarter. what are your thoughts on using netstat -punt to get the ip of your attacker then using iptables to block his ip or just killing the pid or both?

---

### Post by cariboo on 2013-12-01
Truthfully I don't monitor ports any more, after I made sure that my firewall wasn't letting anything through that I didn't want, I stopped. I've relied on the firewall built into my router, for the past 10+ years, and so far I haven't had any problems.

---

### Post by leeper69 on 2013-12-01
Hi cariboo907 I havent had any problems eather but was alerted when answring another post about a virus in ubuntu which reminded me of a simuler thing that had happend to me a few years ago.I found a good url about how even routers can spred this worm at [http://www.pcworld.com/article/2067700/worm-targets-linux-pcs-and-embeded-devices.html](http://www.pcworld.com/article/2067700/worm-targets-linux-pcs-and-embeded-devices.html)

---

