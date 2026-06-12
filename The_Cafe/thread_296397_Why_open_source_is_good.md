---
title: "Why open source is good"
date: 2006-11-09
forum: The Cafe
---

### Post by ade234uk on 2006-11-09
I am slowly finding out pound for pound why Open source is good for business. 

We bought an auction website off the shelf, its written in .php, its currently getting over 14,000 hits a day. It's hosted on a freebsd server and the peformance has been adsolutely fantastic, touch wood.

If we had gone down the aspx route with a windows server this whole project would have cost us ten times more.

Secondly my boss who has partnered with this company asked me to migrate their site over to .php as it was written in .asp

I dont have to do anything special. There is no database needed, just basically a static site. 

The old .asp site had a database on the back end, which allowed users to to create and modify content on the site. 
Looking on the windows server I have never ever seen so many pages needed to create a database driven website in .asp It was absolutely ridicolous. It was overkill. 
The same thing in .php would have used half the pages.

The subject of webhosting was bought up, and apparently this company has been paying over £900 a year for webhosting. I could not beleive it. The same quality hosting account on Linux costs about £200 quid a year.

---

### Post by jpeddicord on 2006-11-09
And that is why proprietary software costs you a lot more in the long run. ;)

---

### Post by DC@DR on 2006-11-09
Yeah, and not only you save/reduce TCO a lot, other benefits are FREEDOM, free of choices, and free to change whatever/whenever you need, and will not ever get locked in by big-but-bad companies like M$ :p .Cheers, and best wishes for FOSS/GNU/Linux/Ubuntu all ;)

---

### Post by .t. on 2006-11-09
Yeah; freedom is good for the soul. 

(Hint at [my new proverb]("http://ubuntuforums.org/showthread.php?t=296406")!)

---

### Post by mips on 2006-11-09
If you look at webserver up time FreeBSD is at the top of the list. Reliable & pretty bulletproof.

---

### Post by .t. on 2006-11-09
I don't care, so long as it's free.

---

### Post by jpeddicord on 2006-11-09
I really like BSD, but I don't like the fact that no one likes anything binary to be used in it. I like portage, but there should be a version that doesn't require you to compile everything.

Another thing I don't really care for is how a bunch of BSD communnities hate Linux. Why can't we all just get along?

---

### Post by mips on 2006-11-09
> **.t. said:**
> I don't care, so long as it's free.

Free is not the only consideration to take into account. If you work in a production environment you cannot have unreliable/unsecure operating systems or applications.

---

### Post by .t. on 2006-11-09
Portage is the Gentoo system. It supports installing packages through any method. Write the ebuild, and it does what you tell it.

Ports (the BSD way) just uses Makefiles. Again, write them to install a binary, and that's what they will do.

---

### Post by Tipo on 2006-11-09
I always like open source projects because of the community that surrounds them. Everyone's involved, and there is always a way for anybody to help out, whether it's contributing patches, or answering questions on the forums

---

### Post by TheRingmaster on 2006-11-09
I like open-source because of the lack of cops at my door for using a "illegal" MS windiz os.
lol

EDIT: this sentence doesn't sound right. :(

---

### Post by shining on 2006-11-09
> **jacobmp92 said:**
> I really like BSD, but I don't like the fact that no one likes anything binary to be used in it. I like portage, but there should be a version that doesn't require you to compile everything.


Portage is gentoo specific, but it's based on BSD port system. Which one did you mean?
I agree the priority is really given to the ports system, that's what the majority of fbsd users seemed to use when I tried it. Binary packages are also built from the ports, and you can mix both, but it seems like they are always outdated.
It would be nice to have apt-get on fbsd :)

> 
Another thing I don't really care for is how a bunch of BSD communnities hate Linux. Why can't we all just get along?

About that, I don't really know, but I don't think it's that bad, is it?
It seemed to me many bsd users are also using linux. They generally prefer bsd for server and linux for desktop. But well, bsd is ok as desktop too, and linux is ok as server too :)

---

### Post by mips on 2006-11-09
> **shining said:**
> 
It would be nice to have apt-get on fbsd :)
)

Now you are talking :)

---

### Post by .t. on 2006-11-09
Well the source is there; you just need a repo now.

---

### Post by jpeddicord on 2006-11-09
Yeah, I always get BSD Ports and Gentoo Portage mixed up. APT on BSD would be awesome. :)

.t., congrats on the 1000th post! :KS

---

### Post by .t. on 2006-11-10
As I said, the source is there for the building. Just set up a build system, or get Ubuntu to provide a BSD target (like Gentoo does), and you're set to go. It's just package management, remember!

Re congrats: Thanks! May beans come swiftly to you all.

---

