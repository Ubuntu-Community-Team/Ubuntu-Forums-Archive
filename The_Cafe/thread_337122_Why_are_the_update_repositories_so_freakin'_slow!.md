---
title: "Why are the update repositories so freakin' slow?!?"
date: 2007-01-12
forum: The Cafe
---

### Post by BarfBag on 2007-01-12
I strayed (again) to Arch and came running back to the open arms of Ubuntu (again).  Typing this on a fresh install.

My PC has been updating for close to twenty-four hours now.  What's going on here?!?  It was downloading around three hundred KB a second before it hit the OpenOffice updates, now it's down in the bites!  I know it isn't my connection or my router.  Everything else is fast and my settings look fine.  Is this happening for everyone?  X_X

---

### Post by riven0 on 2007-01-12
Yeah, that's why I went over to the main servers. I have no idea what is going on. Perhaps a huge influx of new users?

---

### Post by Mateo on 2007-01-12
happens to me too but not that often.

---

### Post by zerhacke on 2007-01-12
If you look in /etc/apt/sources.list and remove the "us." part of the repos then apt-get update you will return to close to full speed if not totally full speed.

There's something up with the US repositories.

---

### Post by SZF2001 on 2007-01-12
I'm not very sure...

We (me, someone, a team, anybody) needs to make a Wiki (or a better pafe of, since I didn't know) on upgrading through the CDs. It's simple, really...

Just set the repositories to the next upgrade CD you have in your computer, disable all the internet repo's and in the terminal type **sudo aptitude upgrade** (or maybe it's install upgrade I'm not sure since I'm at school).

But ya, the CD's aren't ever really up to date. But that would somewhat help, I suppose... After doing that I only had a few updates to install.

---

### Post by firezip on 2007-01-24
Gah, the main server repos are slow as hell now. Any suggestions? (I'm stuck at 50 kb/s when I usually avg. 300 kb/s)

---

### Post by Choad on 2007-01-24
ive always been amazed at how fast the (official) repos are

never fails to max out my connection

---

### Post by mips on 2007-01-24
Depending on where you live I would get a list of repos/mirrors and test each ones response time with some sort of tool. Add the best one to your sources list and off you go.

---

### Post by firezip on 2007-01-24
I'm trying multiple mirrors but nothing is helping my speed. (Btw this is a fresh install of ubuntu dvd edition)

---

### Post by Choad on 2007-01-24
> **firezip said:**
> I'm trying multiple mirrors but nothing is helping my speed. (Btw this is a fresh install of ubuntu dvd edition)
theres a dvd edition?!?

---

### Post by geek_Man on 2007-01-24
> **Choad said:**
> theres a dvd edition?!?

Yeah, it's a live CD basically, but with a text install option and it can install the server (and LAMP).

---

### Post by The Noble on 2007-01-25
For me the servers have been god slow for 4 or 5 days now, usually hovering around 30 kB/s. Not enough to bitch about and fix, but enough to get annoying...I'm using the official servers, not the us servers, for anyone's information. I don't even want to think about what will happen if this isn't fixed before feisty is realeased[mass panic and lots of overnight upgrades].

---

### Post by onx on 2007-02-09
Is there a way to make synaptic download more than one file at a time?

---

### Post by picpak on 2007-02-09
I thought it did that by default when you download a large file.

---

### Post by zubrug on 2007-02-09
ya, dumped the canadian repo's for that reason, first thing I do on a fresh install. Makes a huge difference.

---

