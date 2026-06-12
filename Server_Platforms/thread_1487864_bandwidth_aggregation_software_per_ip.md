---
title: "bandwidth aggregation software per ip"
date: 2010-05-19
forum: Server Platforms
---

### Post by damarusama on 2010-05-19
Hi there, 

I am running Ubuntu server 9.10 and I am trying to find a way to cumulate and visualized bandwidth for all the ips on my network. 

I created a server connected to a mirror port of my router and I am running snort and nessus and ntop to monitor and scan my network for security. Everything is running fine and I can see all the traffic happening, ntop creates really nice report of what is going on in the network, snort with base alert me of probable security problem and nessus help me secure the network with weekly scans. 

What else do I need ? I really simply need a software that will calculate the total bandwith usage per ip address. Ntop seems to gather all that information somewhere, but there is not simple way to get the information out of it. I was thinking maybe cacti would be the software to use but I am not too familiar with Cacti and it's interface seems a bit daunting still. 

I don't need it to be web interface - but it would be nice. I could probably rig up something on a console base program. What I want the output to be should look like tcptrack but with the running totals for last day, last month, last year, and if there could be a graph for it- even better. 

Any idea ? 

thanks

---

### Post by The Real Dave on 2010-05-19
You could use Squid Proxy and use the Squint bandwidth monitor. Squid is a caching proxy, which stores often loaded files, speeding up your internet and saving you some bandwidth. If you'd rather not cache stuff, you can tell it to cache nothing.

Squid is extremely versatile, and there are some nice guides online to help. 

Squint is a separate small program, which you'll find on the Squid website. It takes the reports from Squid and changes them to a human readable form, into a nice webpage even. The screen shot will show you what I mean.

If you choose to cache Internet, don't worry, you don't need that powerful a rig. My server [1.7Ghz PentiumIV with 384Mb RAM] is compfortably handling running Squid along with many other things. Squid is using around 10% of the RAM, and that's with a 6.5GB cache. A general rule of thumb is to have 32MB of RAM per GB of cache.

Personally I'd advise using Squid3 instead of just Squid, it's newer, and better. There's plenty to explain on their site anyway.

[Squid-Cache.org]("http://www.squid-cache.org/")

[URL="http://kuscsik.blogspot.com/2008/01/transparent-proxy-with-squid-3-on.html"]
Transparent Squid Proxy[/URL]

[Ubuntu Docs on Squid]("https://help.ubuntu.com/community/Squid")

---

### Post by damarusama on 2010-05-19
nice - I installed squid3 and connect to it - everything seems good ~ Any tips and trick for squint ? most of the documentation points our direction that is a bit different than Ubuntu 

Let me know if you have any info on that - I'll play around to see if I can make it work 

thanks again that is exactly what I was looking for !!

---

### Post by damarusama on 2010-05-19
ok - got it to work - all is good - I just had to change some settings in the squint.cron.sh to point to the squid3 log folder ! 

thanks again - I learnt squid long time ago and it seems to have matured really well - it's a great tool to complement a security server !

---

### Post by The Real Dave on 2010-05-19
Ya, it definitely is, Squid3 is awesome like :) I'm glad you got Squint working so quick, it took me quite a while messing with dirs and permissions >.<

Hey, don't forget to display your server's specs, and a couple of pictures on the [Show Us Your Server thread]("http://ubuntuforums.org/showthread.php?t=334293"). :D :D

---

