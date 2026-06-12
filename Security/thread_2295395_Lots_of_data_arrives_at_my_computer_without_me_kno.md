---
title: "Lots of data arrives at my computer without me knowing where it comes from"
date: 2015-09-18
forum: Security
---

### Post by desconocido on 2015-09-18
Sorry if this is a bit vague; I can't find any way to formulate my problem that gets useful search results.

Yesterday (twice) and today (once so far), I notice that for far longer than I would normally expect, for example, for a web page, lots of data (as viewed by System Monitor -> Resources -> Network History) suddenly starts arriving at the maximum rate my internet connection allows (2.5Mbit/sec).

I get nervous, so I turn the Wifi off. When I turn it on again, I get a spike of data at 2Gbit/sec (how is that possible?!) and then there is no more data download (till the next time).

I use Firefox with lots of tabs open, so I suppose it might be Ajax doing something; it's not in response to anything I have done. Also, it's not a pattern I have ever seen before. The only other programs that I have set running are Thunderbird, Nautilus and System Monitor.

I suspect automatic software updating, but as far as I know all software is configured to ask me first. Firefox nags me about ten times a day to update from 39.0.

When it happens again is there any way to find out which program is pulling the data?

Any ideas what might be happening?

Thanks,

---

### Post by ian-weisser on 2015-09-18
I use Etherape (available in the Ubuntu repositories) to tell me the source when such things occur.
For me, it's usually a web page being too clever.
Sometimes it's a job I forgot I had running in the background.

Apt *will* update your package database once each day...if enabled. It does so at a predictable time each day, and it's not big. See /etc/cron.daily .

---

### Post by Habitual on 2015-09-18
Torrents?

---

### Post by untrustytahr on 2015-09-18
Nethogs will give you bandwidth by process.

---

### Post by waltsullivan on 2015-09-18
`sudo lsof -i` will show you all open network connections

---

### Post by desconocido on 2015-09-19
Not torrents, I think.

Of course, it hasn't happened again (yet) now I am ready to have a look.

Thanks.

---

### Post by cogset on 2015-09-20
Also, ```
 watch -n2 ss -aptn state established
```
will display all established connections every 2 seconds (you can choose the value you want with -n1, n2 and so on)
 and
```
sudo netstat -altupn -c
``` will continuously display all TCP connections regardless of their state.

May I  also suggest you have a look at Wireshark, it is definitely not an easy piece of software (I only have a very  basic understanding of it) but even so it can hint at which connections are causing such issues.

---

### Post by desconocido on 2015-09-21
The problem recurred. Not so fast this time: often downloading at 1/2 Mbit/sec. I notice it also uploads at about 10% of the rate of the download.

I used lsof.

Here is output while the mysterious data was arriving:
```
abc@Otilia:~$ sudo lsof -i
[sudo] password for abc: 
COMMAND    PID     USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
avahi-dae  880    avahi   13u  IPv4   9684      0t0  UDP *:mdns 
avahi-dae  880    avahi   14u  IPv6   9685      0t0  UDP *:mdns 
avahi-dae  880    avahi   15u  IPv4   9686      0t0  UDP *:51981 
avahi-dae  880    avahi   16u  IPv6   9687      0t0  UDP *:33605 
cupsd      881     root    9u  IPv6  11171      0t0  TCP ip6-localhost:ipp (LISTEN)
cupsd      881     root   10u  IPv4  11172      0t0  TCP localhost:ipp (LISTEN)
mysqld    1054    mysql   10u  IPv4  10705      0t0  TCP localhost:mysql (LISTEN)
apache2   1139     root    4u  IPv6  10642      0t0  TCP *:http (LISTEN)
apache2   1316 www-data    4u  IPv6  10642      0t0  TCP *:http (LISTEN)
apache2   1317 www-data    4u  IPv6  10642      0t0  TCP *:http (LISTEN)
apache2   1318 www-data    4u  IPv6  10642      0t0  TCP *:http (LISTEN)
apache2   1319 www-data    4u  IPv6  10642      0t0  TCP *:http (LISTEN)
apache2   1320 www-data    4u  IPv6  10642      0t0  TCP *:http (LISTEN)
gweather- 2030      abc   13u  IPv4  49785      0t0  TCP Otilia.local:51250->a88-221-52-75.deploy.akamaitechnologies.com:http (CLOSE_WAIT)
ubuntu-ge 2086      abc   11u  IPv4  18602      0t0  TCP Otilia.local:34775->mistletoe.canonical.com:http (CLOSE_WAIT)
dhclient  3343     root    6u  IPv4  18560      0t0  UDP *:bootpc 
dnsmasq   3351   nobody    4u  IPv4  18411      0t0  UDP localhost:domain 
dnsmasq   3351   nobody    5u  IPv4  18412      0t0  TCP localhost:domain (LISTEN)
firefox   3491      abc   32u  IPv4  51492      0t0  TCP Otilia.local:32925->185.31.19.207:https (ESTABLISHED)
firefox   3491      abc   40u  IPv4  50101      0t0  TCP Otilia.local:43902->185.31.18.67:http (ESTABLISHED)
firefox   3491      abc   56u  IPv4  51494      0t0  TCP Otilia.local:37367->185.31.18.67:https (ESTABLISHED)
firefox   3491      abc   57u  IPv4  51495      0t0  TCP Otilia.local:37368->185.31.18.67:https (ESTABLISHED)
firefox   3491      abc   58u  IPv4  52308      0t0  TCP Otilia.local:39971->185.31.18.207:http (ESTABLISHED)
firefox   3491      abc   59u  IPv4  52413      0t0  TCP Otilia.local:37369->185.31.18.67:https (ESTABLISHED)
firefox   3491      abc   60u  IPv4  51496      0t0  TCP Otilia.local:37370->185.31.18.67:https (ESTABLISHED)
firefox   3491      abc   63u  IPv4  51760      0t0  TCP Otilia.local:43767->185.31.18.207:https (ESTABLISHED)
firefox   3491      abc   70u  IPv4  51866      0t0  TCP Otilia.local:37448->185.31.18.67:https (ESTABLISHED)
firefox   3491      abc   71u  IPv4  51757      0t0  TCP Otilia.local:32987->185.31.19.207:https (ESTABLISHED)
firefox   3491      abc   72u  IPv4  51894      0t0  TCP Otilia.local:34603->185.31.19.67:http (ESTABLISHED)
firefox   3491      abc   74u  IPv4  52677      0t0  TCP Otilia.local:43768->185.31.18.207:https (ESTABLISHED)
firefox   3491      abc   75u  IPv4  51796      0t0  TCP Otilia.local:43473->185.31.17.70:http (ESTABLISHED)
firefox   3491      abc   76u  IPv4  52595      0t0  TCP Otilia.local:37384->185.31.18.67:https (ESTABLISHED)
firefox   3491      abc   77u  IPv4  51656      0t0  TCP Otilia.local:37383->185.31.18.67:https (ESTABLISHED)
firefox   3491      abc   78u  IPv4  52678      0t0  TCP Otilia.local:43769->185.31.18.207:https (ESTABLISHED)
firefox   3491      abc   84u  IPv4  51746      0t0  TCP Otilia.local:43287->ec2-54-247-94-147.eu-west-1.compute.amazonaws.com:http (ESTABLISHED)
firefox   3491      abc   85u  IPv4  52756      0t0  TCP Otilia.local:44008->185.31.18.67:http (ESTABLISHED)
firefox   3491      abc   88u  IPv4  52602      0t0  TCP Otilia.local:37391->185.31.18.67:https (ESTABLISHED)
firefox   3491      abc   89u  IPv4  52603      0t0  TCP Otilia.local:37392->185.31.18.67:https (ESTABLISHED)
firefox   3491      abc   90u  IPv4  52668      0t0  TCP Otilia.local:38771->185.31.19.207:http (ESTABLISHED)
firefox   3491      abc   92u  IPv4  51683      0t0  TCP Otilia.local:43267->ec2-54-247-94-147.eu-west-1.compute.amazonaws.com:http (ESTABLISHED)
firefox   3491      abc   94u  IPv4  52682      0t0  TCP Otilia.local:37433->185.31.18.67:https (ESTABLISHED)
firefox   3491      abc   95u  IPv4  52688      0t0  TCP Otilia.local:37434->185.31.18.67:https (ESTABLISHED)
firefox   3491      abc  104u  IPv4  51771      0t0  TCP Otilia.local:37435->185.31.18.67:https (ESTABLISHED)
firefox   3491      abc  105u  IPv4  51772      0t0  TCP Otilia.local:37436->185.31.18.67:https (ESTABLISHED)
firefox   3491      abc  106u  IPv4  51773      0t0  TCP Otilia.local:37437->185.31.18.67:https (ESTABLISHED)
firefox   3491      abc  107u  IPv4  41476      0t0  TCP Otilia.local:35152->ec2-54-247-160-217.eu-west-1.compute.amazonaws.com:http (ESTABLISHED)
firefox   3491      abc  108u  IPv4  51774      0t0  TCP Otilia.local:37438->185.31.18.67:https (ESTABLISHED)
firefox   3491      abc  109u  IPv4  51797      0t0  TCP Otilia.local:43474->185.31.17.70:http (ESTABLISHED)
firefox   3491      abc  110u  IPv4  41479      0t0  TCP Otilia.local:35155->ec2-54-247-160-217.eu-west-1.compute.amazonaws.com:http (ESTABLISHED)

```

I then turned the Wifi off and then on again and get no data flows and:
```
abc@Otilia:~$ sudo lsof -i
COMMAND    PID     USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
avahi-dae  880    avahi   13u  IPv4   9684      0t0  UDP *:mdns 
avahi-dae  880    avahi   14u  IPv6   9685      0t0  UDP *:mdns 
avahi-dae  880    avahi   15u  IPv4   9686      0t0  UDP *:51981 
avahi-dae  880    avahi   16u  IPv6   9687      0t0  UDP *:33605 
cupsd      881     root    9u  IPv6  11171      0t0  TCP ip6-localhost:ipp (LISTEN)
cupsd      881     root   10u  IPv4  11172      0t0  TCP localhost:ipp (LISTEN)
mysqld    1054    mysql   10u  IPv4  10705      0t0  TCP localhost:mysql (LISTEN)
apache2   1139     root    4u  IPv6  10642      0t0  TCP *:http (LISTEN)
apache2   1316 www-data    4u  IPv6  10642      0t0  TCP *:http (LISTEN)
apache2   1317 www-data    4u  IPv6  10642      0t0  TCP *:http (LISTEN)
apache2   1318 www-data    4u  IPv6  10642      0t0  TCP *:http (LISTEN)
apache2   1319 www-data    4u  IPv6  10642      0t0  TCP *:http (LISTEN)
apache2   1320 www-data    4u  IPv6  10642      0t0  TCP *:http (LISTEN)
gweather- 2030      abc   13u  IPv4  57018      0t0  TCP Otilia.local:51377->a88-221-52-75.deploy.akamaitechnologies.com:http (ESTABLISHED)
ubuntu-ge 2086      abc   11u  IPv4  57016      0t0  TCP Otilia.local:35256->mistletoe.canonical.com:http (CLOSE_WAIT)
firefox   3491      abc   32u  IPv4  51492      0t0  TCP Otilia.local:32925->185.31.19.207:https (ESTABLISHED)
firefox   3491      abc   40u  IPv4  57113      0t0  TCP Otilia.local:43803->185.31.18.207:https (ESTABLISHED)
dhclient  3687     root    6u  IPv4  56920      0t0  UDP *:bootpc 
dnsmasq   3691   nobody    4u  IPv4  55980      0t0  UDP localhost:domain 
dnsmasq   3691   nobody    5u  IPv4  55981      0t0  TCP localhost:domain (LISTEN)

```

Anything suspicious?

---

### Post by desconocido on 2015-09-21
By the way, when I turn the Wifi back on again, I get a spike of data thus:

[IMG]http://misc.artprop.org/photos/Screenshot%20from%202015-09-19%2015%3A37%3A34.png[/IMG]

I imagine there is some sort of rounding error as I only have a 2.5Mbit/sec link.

---

### Post by ian-weisser on 2015-09-21
> **desconocido said:**
> Here is output while the mysterious data was arriving:
```

firefox   3491      abc   32u  IPv4  51492      0t0  TCP Otilia.local:32925->185.31.19.207:https (ESTABLISHED)
...[many more firefox results]...
firefox   3491      abc  110u  IPv4  41479      0t0  TCP Otilia.local:35155->ec2-54-247-160-217.eu-west-1.compute.amazonaws.com:http (ESTABLISHED)

```

The 'mysterious data' seems like one or more web pages downloading to your browser.

> **desconocido said:**
> Anything suspicious?
No. Seems ordinary to me. Looks like gweather and ubuntu-geoclue updated upon connection (both expected).

---

### Post by desconocido on 2015-09-21
> The 'mysterious data' seems like one or more web pages downloading to your browser.
Yes, but as far as I could see, there was nothing going on in Firefox. I hadn't opened a new page in about five minutes; none of the tabs seemed to be revolving the reload symbol... Maybe it was ajax code doing something odd?

I have ad block, flash block and privacy badger.

---

### Post by Habitual on 2015-09-21
```
185.31.17.70
185.31.18.207
185.31.18.67
185.31.19.207
185.31.19.67
``` all belong to Fastly, Inc. a content delivery provider.

have you tried firefox in safemode (no addons) to see if it may be an addon?

---

### Post by ian-weisser on 2015-09-21
> **desconocido said:**
> Maybe it was ajax code doing something odd?

Odd? No. 
It is ajax or js or other client-side code doing exactly what it is supposed to do - downloading new content and ads for you.
You are apparently using websites that cleverly avoid or workaround your ad-blockers.
Your interaction with those pages, in this case, seems irrelevant. We have all seen plenty of web pages that will, say, rotate ads regardless of your actions (or inaction).
Nothing unusual nor suspicious about it...beyond the usual sleaziness of code-heavy and ad-heavy websites.

---

### Post by desconocido on 2015-09-21
> You are apparently using websites that cleverly avoid or workaround your ad-blockers.
Your interaction with those pages, in this case, seems irrelevant. We have all seen plenty of web pages that will, say, rotate ads regardless of your actions (or inaction).
Nothing unusual nor suspicious about it...beyond the usual sleaziness of code-heavy and ad-heavy websites. 

Well, thanks everyone. I think it was definitely Firefox, and probably some ad server sending me gigabytes of data and then finding at the last minute that it was blocked from displaying them on the screen. That spooked me a bit because I had never seen such volumes of data before unless I was explicitly downloading something. (So do people who don't used adblockers find their computer is always slowing down to a crawl?)

I had a clear out and closed half my Firefox tabs. Since then nothing unusual has happened. Here's hoping.

---

### Post by cogset on 2015-09-29
I you want to get rid of such issues, assuming that is that some obnoxious adserver currently not blocked by your adblock rules, you should identify which is and add a rule for it.

The first place to start could maybe be adding another (more aggressive) adblock subscription list, depending on which list(s) are you currently using and how much you are willing to deal with website breakages, because aggressive/too generic adblock rules can break some websites.

Or, you can investigate the issue by opening the blockable items list from you adblock menu (shortcut CTRL+SHIFT+V) at the time such issues surfaces, and try to spot which could be the source of the incoming data.
There also is the Element hiding helper addon that complements Adblock and makes writing custom rules much easier, it also is nicely integrated with the built-in web inspector in Firefox, so that you can identify some element in the page using the inspector and add a specific rule for it on the fly with Adblock.

Once you have identified the source(s) of this unwanted data, you should eventually consider adding them to your hostfile: assuming you don't want to receive any data from let's say  adserver.com, after adding  a rule like that ```
||adserver.com^$match-case
``` to your adblock filters, also add adserver.com to your hostfile and you won't be getting any more data from them.

---

### Post by ian-weisser on 2015-09-29
> **desconocido said:**
> So do people who don't used adblockers find their computer is always slowing down to a crawl?.

It depends entirely upon your browsing habits and choices.
If you choose to browse code-heavy and ad-heavy sites, then yes your browsing experience will grow sluggish.
I don't use an ad-blocker, have a moderately slow connection, and have modest hardware. My experience is quite zippy...but I don't frequent ad-heavy neighborhoods online.

---

### Post by mystics on 2015-09-29
> **desconocido said:**
> (So do people who don't used adblockers find their computer is always slowing down to a crawl?)

Like ian-weisser said, it mostly has to do with sites that you frequent. Sites like Facebook and Google (including related sites like YouTube) don't generally cause a significant performance decrease with their ads (in fact, I don't think I've ever had an issue with Google or Facebook). Short of ads before YouTube videos (which normally aren't even that bad), they avoid letting the ads hinder your user experience. On the flip side, some sites offer very low content, require multiple pages to click through for an article, and have potentially dozens of ads (sometimes videos) running at a single time. These are going to slow down the experience significantly, bringing the web browser (and sometimes computer) to a screeching halt. 

So no, ads aren't themselves a problem. Plenty of companies know how to use them properly to both make money and avoid hindering the user experience. So best to put the blame for slowdown on the sites that abuse them than on ads themselves.

---

### Post by desconocido on 2015-10-03
Thanks everyone. I have had no recurrence.

---

