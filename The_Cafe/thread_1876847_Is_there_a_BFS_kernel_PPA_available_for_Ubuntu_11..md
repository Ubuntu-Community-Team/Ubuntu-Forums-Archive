---
title: "Is there a BFS kernel PPA available for Ubuntu 11.10?"
date: 2011-11-06
forum: The Cafe
---

### Post by hotweiss on 2011-11-06
Is there a BFS kernel PPA available for Ubuntu 11.10?  Just want to give it a try...

---

### Post by cbowman57 on 2011-11-06
[http://www.liquorix.net/](http://www.liquorix.net/)

There ya go.

---

### Post by Copper Bezel on 2011-11-06
The most recent I can find is [_for 11.04_]("https://launchpad.net/~chogydan/+archive/ppa"). It doesn't seem that there's a lot of buzz around BFS anymore, and apparently the usability difference from CFS isn't very noticeable at all.

Edit: Never mind. = D

---

### Post by cbowman57 on 2011-11-06
I feel like a dummy, you were looking for a ppa.

As far as I know there isn't a ppa for it, but once you add the repository & key it acts like one.

---

### Post by Copper Bezel on 2011-11-07
Yeah, same thing - I just didn't think to look for anything else. I forget that packages are sometimes released for systems other than Ubuntu. = )

---

### Post by kvvv on 2011-11-07
The package was built specifically for Debian though, and not for Ubuntu. I faced more problems than improvements, and removed it after a week.

This was however with Natty. I suspect it should work better with Oneiric.

---

### Post by cbowman57 on 2011-11-07
> **Copper Bezel said:**
> Yeah, same thing - I just didn't think to look for anything else. I forget that packages are sometimes released for systems other than Ubuntu. = )

I just looked at that link, I run the -ck kernel on my Arch setup, real good kernel.

Guess I didn't realize that he also had a ppa, thought it was just an Arch thing. :)

* side note to that though, I did try the BFQ scheduling and it doesn't like my hardware and/or gnome shell.  I just let it default to CFQ, have  also forced it to use noop without any problems.
Haven't tried BFS that I remember.

---

### Post by kvvv on 2011-11-07
> **cbowman57 said:**
> 
* side note to that though, I did try the BFQ scheduling and it doesn't like my hardware and/or gnome shell.  I just let it default to CFQ, have  also forced it to use noop without any problems.
Haven't tried BFS that I remember.

Just curious, how did you do this? I thought there was only one scheduler in the kernel depending on which package you used.

---

### Post by cbowman57 on 2011-11-07
I can't remember the specifics, it's on his Arch wiki I think.

But the -ck kernel has noop, cfq, bfq & probably bfs.  There are a couple ways to do it but the best way is from the kernel command line in grub.  If you want to run bfq as an example you would just add elevator=bfq, it defaults to cfq but the same method applies to all 4 of the schedulers.

Reasonably sure the same would apply to all kernels, dependent on what they were built with of course.

---

### Post by hotweiss on 2011-11-08
> **cbowman57 said:**
> [http://www.liquorix.net/](http://www.liquorix.net/)

There ya go.

Thanks.  Will give it a try.

---

### Post by kvvv on 2011-11-08
> **hotweiss said:**
> Thanks.  Will give it a try.

Nooo. dont use that. That is for debian and might break in ubuntu.

Use the laumcjpad ppa posted some posts before.

---

### Post by nocnokneo on 2011-11-19
Here's the PPA with 11.10 oneiric support:

[https://launchpad.net/~chogydan/+archive/ppa?field.series_filter=oneiric](https://launchpad.net/~chogydan/+archive/ppa?field.series_filter=oneiric)

---

### Post by cbowman57 on 2011-11-19
> **nocnokneo said:**
> Here's the PPA with 11.10 oneiric support:

[https://launchpad.net/~chogydan/+archive/ppa?field.series_filter=oneiric]("https://launchpad.net/%7Echogydan/+archive/ppa?field.series_filter=oneiric")

I use the linux kernel with the -ck patch on Arch, it works quite well.

---

### Post by cbowman57 on 2011-11-19
> **kvvv said:**
> Nooo. dont use that. That is for debian and might break in ubuntu.

Use the laumcjpad ppa posted some posts before.

You really have no idea what you're talking about do you?

---

### Post by hotweiss on 2011-11-25
> **cbowman57 said:**
> [http://www.liquorix.net/](http://www.liquorix.net/)

There ya go.

I finally tried this kernel.  All I have to say is wow!  Everything is so much more snappier with it.  Thanks.

---

### Post by cbowman57 on 2011-11-25
> **hotweiss said:**
> I finally tried this kernel.  All I have to say is wow!  Everything is so much more snappier with it.  Thanks.

Yeah, it's a noticeable improvement on my machine as well.

---

### Post by Cerebrux on 2012-05-14
There is also Optimus Kernel which is built to be compatible with Ubuntu. There is no PPA though, and you just install the packages

more at [http://optimus-linux.blogspot.com]("http://optimus-linux.blogspot.com")

---

