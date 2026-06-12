---
title: "Large linux deployments: Munich and Vienna"
date: 2012-04-02
forum: The Cafe
---

### Post by keithpeter on 2012-04-02
Hello All

[Munich: a news site summary]("http://www.computerworlduk.com/news/public-sector/3348475/munich-mayor-says-switch-linux-is-much-cheaper-reduced-complaints/")

[LiMux (Munich's own spin) site]("http://www.muenchen.de/Rathaus/dir/limux/english/index.html"): Debian Sarge! They must have upgraded now surely?

[Vienna (Wein): failure to fully migrate ]("http://www.freesoftwaremagazine.com/articles/vienna_failed_to_migrate_to_linux_why") one view

Anyone any other examples of large deployments of GNU/Linux or other free operating systems? What interests me is the age of the software and the stability needed (i.e. lack of change) in these deployments. Do we need the Mother of all LTSes?

---

### Post by HermanAB on 2012-04-02
These are actually small deployments.  The large ones are Amazon, Google, Yahoo and Akamai.  There are also whole country governments that use Linux, for example the South African Revenue Service changed first and everything else is folowing and also the Brazillian government.

---

### Post by keithpeter on 2012-04-02
Hello HermanAB

Thanks for the South African reference.

[http://tectonic.co.za/?p=4435](http://tectonic.co.za/?p=4435)

2009 is the most recent I can find about the South African Revenue Service. Servers moved over, thin clients being developed. 14000 screens mentioned, which is about 50% bigger than Munich.

Its the *migration process* in 'normal' organisations that interests me. The Googles of this world have developed their own platforms on the GNU/Linux base, and their business is Web based.

---

### Post by HermanAB on 2012-04-02
So, how about 1 million computers in the Brazillian government?
[http://www.linuxtoday.com/infrastructure/2011070800339OSSWDV](http://www.linuxtoday.com/infrastructure/2011070800339OSSWDV)

or this list:
[http://www.focus.com/fyi/50-places-linux-running-you-might-not-expect/](http://www.focus.com/fyi/50-places-linux-running-you-might-not-expect/)

---

### Post by Lars Noodén on 2012-04-02
Also in Brazil is [350,000 multi-seat desktops](http://www.desktoplinux.com/news/NS2824724304.html) with the help of Canadian company Userful.  Multi-seat is otherwise underrated and underutilized.

---

### Post by keithpeter on 2012-04-02
@Herman AB

> "The letter asserts that the ODF standard is already a guarantee of interoperability within the government."--july 2011 

That's great stuff

@Lars Noodén

> "Compared to offering a similar number of individual PCs, Brazil was able to save 60 percent in up-front costs, 80 percent in annual power savings, as well as additional savings in administration and support costs, says Userful"--2009

Huge thinstation roll out there, using a modified KDE on top of Debian. Data from the supplier but I doubt that they would inflate the figures on a public contract. Linux Educacional is up to version 4.0 now, I suppose upgrading is easier on a thin client system. Version 3 had oOo2.4 and an XP like interface

[http://linuxeducacional.com/mod/page/view.php?id=118](http://linuxeducacional.com/mod/page/view.php?id=118)

Just wondering what happens when the 'new' interfaces (Gnome Shell and/or Unity) start appearing as part of the upgrade process in huge numbers.

---

### Post by HermanAB on 2012-04-03
The thing is that MS is mostly an English OS.  MS support for other languages is spotty and varies from bad to worse.  The result is that the Spanish and Portuguese part of the world basically gave up with MS Windows and is a very large user of Linux.  This includes Spain, Portugal and all of America from Mexico on southwards.

There are also many other countries that commonly use Linux in government such as Latvia, Iceland, Belarus, Czechia, India, China, Russia, South Africa and a few others - again driven by language issues, with cost as a secondary thing.  Linux is also popular in German countries, but its use is a bit more spotty than the above.

Certain industries also favour Linux, for example banks and stock exchanges the world over almost exclusively use Linux - this industry is dominated by IBM and Oracle.  The military is also a heavy user of Linux systems and the US DOD is likely the largest user of Linux in North America.

The result is that the total market penetration of Linux on the desktop is probably around 12 to 15%.  Even O'l Steve Balmer of Microsoft estimated it at about 10%, which explains the feverish opposition campaign of MS against Linux.  They obviously see Linux as a very big threat to their livelyhood - much more so than Apple.

---

### Post by keithpeter on 2012-04-03
> **HermanAB said:**
> Certain industries also favour Linux, for example banks and stock exchanges the world over almost exclusively use Linux - this industry is dominated by IBM and Oracle.  The military is also a heavy user of Linux systems and the US DOD is likely the largest user of Linux in North America.

Good stuff

Hence my interest in what happens when the 'new' interfaces (Gnome Shell and Unity) roll out to these conservative organisations. Not to mention graphics capability of thin client stations and requirements of Unity (compiz) and GS (mutter). It will be interesting.

---

### Post by vasa1 on 2012-04-03
> **HermanAB said:**
> ...
There are also many other countries that commonly use Linux in government such as ..., India....

I'm not sure India fits in. Possibly at the (invisible to the public) server level. But at the desktop level, I've never seen Linux.

---

### Post by Lars Noodén on 2012-04-05
There's also Spain:

[http://www.h-online.com/open/news/item/Extremadura-CIO-plans-Linux-rollout-on-40-000-desktops-1419281.html](http://www.h-online.com/open/news/item/Extremadura-CIO-plans-Linux-rollout-on-40-000-desktops-1419281.html)

[http://joinup.ec.europa.eu/news/extremadura-move-all-its-40000-desktops-open-source](http://joinup.ec.europa.eu/news/extremadura-move-all-its-40000-desktops-open-source)

Mostly though when sites make a large scale move up to Linux or other FOSS software, they get dropped out of the news.

---

### Post by Buovjaga on 2012-04-05
Extremadura seems to be a hotspot for all kinds of open source, hardware included: [http://openeland.org/open-e-land-camp-2012/](http://openeland.org/open-e-land-camp-2012/)

---

### Post by keithpeter on 2012-04-05
> **Lars Noodén said:**
> There's also Spain:

[http://www.h-online.com/open/news/item/Extremadura-CIO-plans-Linux-rollout-on-40-000-desktops-1419281.html](http://www.h-online.com/open/news/item/Extremadura-CIO-plans-Linux-rollout-on-40-000-desktops-1419281.html)

[http://joinup.ec.europa.eu/news/extremadura-move-all-its-40000-desktops-open-source](http://joinup.ec.europa.eu/news/extremadura-move-all-its-40000-desktops-open-source)

Mostly though when sites make a large scale move up to Linux or other FOSS software, they get dropped out of the news.

Hello Lars Noodén and all

> "200,000 LinEx CDs have been distributed for free by local newspapers and 70,000 copies of the operating system have been downloaded from the website as of May 2003. About 10% of the inhabitants of Extremadura are estimated to use LinEx." --[wikipedia article about LinEx]("http://en.wikipedia.org/wiki/GnuLinEx")

That's huge! 

If I understand the news stories correctly, the regional government is now moving their desktops over to *another* Debian based distro. These people are solving problems about updates and large scale migration and have been doing for 8 years. Its a shame their experience cannot be shared more widely.

---

### Post by Buovjaga on 2012-04-05
> **keithpeter said:**
> 
If I understand the news stories correctly, the regional government is now moving their desktops over to *another* Debian based distro.

Yes, the Spanish Wikipedia article for gnuLinEx says: El 29 de diciembre de 2011 anunció su clausura. Which means it was discontinued on 29th Dec 2011.

---

