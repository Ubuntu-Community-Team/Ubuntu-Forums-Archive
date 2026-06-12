---
title: "Linux Powered Sites"
date: 2008-01-20
forum: The Cafe
---

### Post by PartisanEntity on 2008-01-20
I would like to create a list of well known sites, like Google, Ebay, etc.. that are powered by Linux operating systems. The emphasis should be on both 'well known' and 'linux'.

Based on my readings I know of the following only (of the big/giant/well known sites and services I mean):

Google
Ebay

:)

What are the others?

---

### Post by rosegarden78 on 2008-01-20
Walgreens invented and was the first to use satelitte-based prescriptions and is the leading innovator in it's field.

---

### Post by Kimm on 2008-01-20
you can download nmap (from repos) and run:

sudo nmap -P0 -O [www.someaddress.com](www.someaddress.com)

Doesn't always give a clear reading, but you can mostly make out the OS.

```

kim@Haze:~$ sudo nmap -P0 -O www.google.com

Starting Nmap 4.20 ( http://insecure.org ) at 2008-01-20 14:41 CET
Warning: Hostname www.google.com resolves to 3 IPs. Using 64.233.183.104.
Interesting ports on nf-in-f104.google.com (64.233.183.104):
Not shown: 1693 filtered ports
PORT    STATE  SERVICE
[hidden ;)]
Device type: general purpose
Running (JUST GUESSING) : Linux 1.X (86%)
Aggressive OS guesses: Linux 1.3.20 (x86) (86%)
No exact OS matches for host (test conditions non-ideal).

OS detection performed. Please report any incorrect results at http://insecure.org/nmap/submit/ .
Nmap finished: 1 IP address (1 host up) scanned in 35.718 seconds

```

---

### Post by Ebuntor on 2008-01-20
You could also use this [site]("http://netcraft.com/"). Easier to figure out what a site  is running.

---

### Post by PartisanEntity on 2008-01-20
Nice, thanks!

---

### Post by rudihawk on 2008-01-20
I know for a while M$ Hotmail servers ran on a Unix based server...

---

### Post by ellis rowell on 2008-01-20
My websites are maintained with Ubuntu 7.10 and are on a unix server (it's cheaper than a windows server).

I've just checked, my websites are running Apache on Linux server.

---

### Post by PartisanEntity on 2008-01-20
> **ellis rowell said:**
> My websites are maintained with Ubuntu 7.10 and are on a unix server (it's cheaper than a windows server).

I've just checked, my websites are running Apache on Linux server.

Thousands if not millions of sites are running on Linux, but my interest is focused on the 'big names' :)

---

### Post by GGLucas on 2008-01-20
Wikipedia runs on linux as far as I know, [Netcraft]("http://uptime.netcraft.com/up/graph/?host=www.wikipedia.org") says so too

---

### Post by sailor2001 on 2008-01-20
> **rosegarden78 said:**
> Interesting question.  It was my understanding that free Apache and Unix and/or LAMP servers have dominated the market until a software company from the Northwest decided free wasn't good enough.  So though deceptive television advertising and psi manipulation, tricked the public into believing their product superior.  However their product used proprietary file formatting and other standards they refused to share and hence are amidst their second class action lawsuit.

You may be right though.  For example, Flash sells a commercial server to deliver streaming content.  My hunch is that Linux servers will ultimately prevail over high cost low quality software from the Northwest.

But there may be other reasons for corporations to ditch Linux that I have overlook.  I can tell you this - Walgreens used Perl for the internal network and operations until 2006 and possibly now.  So, then, I would assume they use Unix-based servers.  And they are the biggest private user of satellites, besides the military, in the US.

Walgreens invented and was the first to use satelitte-based prescriptions and is the leading innovator in it's field.  Walgreens was the first to use laser-guided forklifts to speed operations.  And Walgreens is one of only a handful of companies that has not lost stock value for 30 years in a row.  And the stock has split so many times employees retire wealthy who exercised early stock options.

So is #1 is pharmacy sales and satellite use big enough for you?

at one time, and maybe still is, the largest franchise in the world

---

### Post by fatality_uk on 2008-01-20
Interestingly, [http://www.sony.com](http://www.sony.com) appears to be running Linux / Apache :D

---

### Post by Erik Trybom on 2008-01-20
Unsurprisingly, Slashdot runs on Linux servers.

---

### Post by cardinals_fan on 2008-01-20
All right, it's not Linux.  But the aforementioned [[COLOR="Blue"]_Netcraft_[/COLOR]]("http://www.netcraft.com") runs FreeBSD.

---

