---
title: "Reducing multiple wordpress websites TTFB"
date: 2015-07-13
forum: Server Platforms
---

### Post by rob134 on 2015-07-13
I have about 5 websites running all with different TTFB but all made with Wordpress. I setup a new 1gb ram ubuntu 14.04LTS thinking a new clean install would fix it - but did not, unfortunately. 
Once the homepage is loaded, the subpages load quick enough. My guess the server has a hard time loading all the Wordpress PHP, Ajax scripts and what not which causes the slow loads. Loading purely a [http://www.domain.com/img.jpg](http://www.domain.com/img.jpg) from the server for example loads instantly so it's definately not a DNS problem.
TTFB averages 5 to 15 seconds, 30seconds or even refuses to load. Turning off plugins or changing themes helps a little bit but doesn't take care of the problem.
I use the W3 total cache plugin. I tried to switch on/off some of those options without too much difference in result.


Are there tests I can run that can find the cause of this? Or is there some memory or Apache setting that I can fine tune that will speed things up? I feel like I've researched all I could on this subject without any luck  :roll: 


My Setup:
PHP 5.5.9-1ubuntu4.9 (cli)
Apache/2.4.7
mysql  Ver 14.14 Distrib 5.5.43,
I run ubuntu 14.04LTS of 1gb ram.
2800 MHz Intel(R) Celeron(R) M processor 1.50GHz 


$ egrep --color 'Mem|Cache|Swap' /proc/meminfo
MemTotal:        1011464 kB
MemFree:           25740 kB
MemAvailable:     502984 kB
Cached:           433468 kB
SwapCached:         4868 kB
SwapTotal:        262140 kB
SwapFree:         210624 kB


```
Apache setup:
    <IfModule mpm_prefork_module>
        StartServers          2
        MinSpareServers       6
        MaxSpareServers      12
        MaxClients          15
        MaxRequestsPerChild   3000
    </IfModule>
    KeepAlive Off
    MaxKeepAliveRequests 100

```

---

### Post by Bucky Ball on 2015-07-13
*Thread moved to **Server Platforms**.*

Please attach all those screenshots rather than inserting them in the body of your post by editing your first post, clicking 'Go Advanced' and attaching them with the paperclip icon. I've done the first one to get you started. Please think of those with slow connections or vision issues. Thanks.

Your lack of RAM may be an issue.

---

### Post by rob134 on 2015-07-13
> [COLOR=#000000]Your lack of RAM may be an issue.[/COLOR]

There's enough RAM with half available - it just looks like it because of the cache it uses.

---

### Post by SeijiSensei on 2015-07-14
I'm going to guess it's the CPU.  I run a small WP site on a virtual machine I rent at [Linode]("http://www.linode.com/"); it loads the home page in about a second or less.  "cat /proc/cpuinfo" reports that Linux on this machine thinks it is running on a Xeon at 2.80 GHz.   I'm also connected to a really big pipe, but that's unlikely to be the difference if you are on any sort of broadband service.

I've steered away from Celerons in general except for low-stress activities like processing mail.  I'd take a real Pentium 4 over a Celeron any day.  Modern i5/i7 processors average 10-20X faster performance than a Celeron M: [http://www.cpubenchmark.net/cpu.php?cpu=Intel+Celeron+M+1.60GHz](http://www.cpubenchmark.net/cpu.php?cpu=Intel+Celeron+M+1.60GHz).  The "M" series is designed for mobile use as I recall, a use-case where speed is sacrificed for improved battery life.

If you're curious, you can invest $10 or less and buy the cheapest machine available from Linode for a month.  Upload your sites to it and see how they test out.  If you decide to bail before the month is up, you'll get refunded the difference.

New acronym of the week for me: TTFB ("time-to-first-byte").

---

### Post by rob134 on 2015-07-14
> **SeijiSensei said:**
> If you're curious, you can invest $10 or less and buy the cheapest machine available from Linode for a month. 
This VPS is hosted at Linode. The $10 one.

---

### Post by SeijiSensei on 2015-07-15
That's not what I would have concluded from reading this:

> **rob134 said:**
> My Setup:
PHP 5.5.9-1ubuntu4.9 (cli)
Apache/2.4.7
mysql  Ver 14.14 Distrib 5.5.43,
I run ubuntu 14.04LTS of 1gb ram.
**2800 MHz Intel(R) Celeron(R) M processor 1.50GHz **


---

### Post by rob134 on 2015-08-01
> **SeijiSensei said:**
> That's not what I would have concluded from reading this:

I've upgraded my linode vps to 2gb intead of 1gb. 1cpu to 2cpu's. Still experiencing slow initial load.

Thinking of other ways to speed up the database.

---

