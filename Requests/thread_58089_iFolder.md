---
title: "iFolder"
date: 2005-08-18
forum: Requests
---

### Post by nixon on 2005-08-18
Any chance we could have packages make up for this?

It looks like it's going to be really handy, I unfortunately have to work with multiple desktops and would love easily share folders and info in a few clicks.. there's been a bit of talk about iFolder around the forums and it seems that ppl are after an easier way to share files and folders.. perhaps this is it?

[www.ifolder.com](www.ifolder.com)

TIA

:)

---

### Post by psoleko on 2005-08-19
I have been wanting to try iFolder for a while now, I second the request.

---

### Post by Mez on 2005-08-21
iFolder cannot be distributed by Ubuntu due to problems with the licencing of novell's libflaim, which iFolder depends on.

---

### Post by jamo on 2005-08-21
Looks nice but seems useless if you dont't have access to an ifolder server.
Please correct me if I don't got it right.

---

### Post by Burgundavia on 2005-08-24
Packages need to be in Breezy to be backported. iFolder is not and therefor cannot be backported.

Corey

---

### Post by Manny C on 2005-08-26
A very good alternative is rsync.

It is activated from a bash. It only synchronises the files that have changed and is great for maintaining exact copies directories in several remote locations.

For info....check out man rsync.

I vouch for its ease and greatness! 

:)

---

### Post by kiddo on 2005-09-13
Yeah but rsync doesn't go both ways. You can mess up if you do it as a temporary measure. iFolder is much much better for keeping up to date with a laptop, in my opinion.

---

### Post by svasie on 2005-09-29
You can try Unison. It works very well and it's in Ubuntu repos.

Hope that version 2.13 will be included in Breezy.

---

### Post by KillerKiwi on 2006-01-15
I have a developmental version of a klik ifolder.cmg 

```
press Alt-F2 and paste
wget klik.atekon.de/client/install -O -|sh
```

apt-get  gtk-sharp, gtk-sharp2

Download the file
[http://www.yourfilelink.com/get.php?fid=5199]("http://www.yourfilelink.com/get.php?fid=5199")

double click the file you downloaded

---

### Post by themindlessmatt on 2006-02-09
Flaim has been open-sourced...

[http://forge.novell.com/modules/xfmod/project/?flaim](http://forge.novell.com/modules/xfmod/project/?flaim)

Any chance of inclusion?

Matt

---

### Post by Mez on 2006-02-09
I'm working on it... it's a big project :D 

Other than that - not a backports issue.

Feel free to email me directly regarding this one - I'm in constant contact with the guys at Novell and we're working together to get this into ubuntu and debian

[email]mez@ubuntu.com[/email]

---

### Post by theidealist on 2006-02-22
I noticed that Martin Meredith and Jorge Castro got this working for dapper

[http://www.sourceguru.net/archives/15]("http://www.sourceguru.net/archives/15")

Any chance we'll get any luck with this in Breezy?

-Patrick

---

### Post by Mez on 2006-02-24
havent tried with breezy yet

---

### Post by adobrin on 2006-12-24
check here for packages:

[www.emplifyhr.com/ifolder](www.emplifyhr.com/ifolder)


these work well for me on Breezy and Dapper.. no go on Edgy yet, i'm working on it.  you will need to install mono and the mono-apache packages to get the necessary libraries, and then install *all* of the packages on that page.

---

### Post by flickerfly on 2007-02-22
Any new news on Edgy support for iFolder?

---

### Post by flickerfly on 2007-02-22
I put a bug in Launchpad to address the lack of iFolder in Edgy and Fiesty:

[https://bugs.launchpad.net/ubuntu/+bug/87122](https://bugs.launchpad.net/ubuntu/+bug/87122)

---

