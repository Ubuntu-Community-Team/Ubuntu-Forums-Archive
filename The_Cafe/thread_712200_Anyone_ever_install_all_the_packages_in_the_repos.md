---
title: "Anyone ever install all the packages in the repos?"
date: 2008-03-01
forum: The Cafe
---

### Post by blithen on 2008-03-01
I know there would be some conflicts with packages and such but still, anyone ever do it? How did it go?

---

### Post by fedex1993 on 2008-03-01
i dont even know if there is a command to install all the packages in the repo plus it would probley take forever to download all of them and then some will be missing dependices at first

---

### Post by bwhite82 on 2008-03-01
I think this would be a pretty interesting experiment. Anyone up to the task? I would try it in VirtualBox if I had the HD space or bandwidth.

---

### Post by bobbocanfly on 2008-03-01
How large do you think it would be? Ive got an external HD where i run my Unstable/Dev partition with about 100 gb spare. Could stick a copy of Hardy on there and give it a go, just to see what happens.

---

### Post by blithen on 2008-03-01
I'm really tempted to do it....but I don't really want to mess up my computer. xD I haven't re-installed in like..2 months. That's a record!

---

### Post by blithen on 2008-03-01
> **bobbocanfly said:**
> How large do you think it would be? Ive got an external HD where i run my Unstable/Dev partition with about 100 gb spare. Could stick a copy of Hardy on there and give it a go, just to see what happens. I think that would be enough. Then again there is a lot of packages. Nothing ventured, nothing gained I suppose though.

---

### Post by darsu on 2008-03-01
*This Ubuntu 7.10 Repository is a 5 DVD set with 17.2GB of software for the PC platform. The DVDs contain all packages from the officially-supported (main repository) and community-maintained (universe repository) mirrors, as of Friday December 21st 2007.*
[(quoted from here)](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html?ad=distrowatch)

That should give some bearing on the size of it.

---

### Post by Joeb454 on 2008-03-01
I think I read somewhere that the repo's have around 36GB of data in them :)

---

### Post by bobbocanfly on 2008-03-01
I'd be up for doing this if i had a faster net connection. My guess is that it would take 20 hours for me to download the packages if my connection stayed at full speed (and Virgin have a habit of closing my connection off a lot if ive been downloading). Sorry guys!

---

### Post by fedex1993 on 2008-03-01
yeah but could you just do i like in apt instead of using the cds or get the full cd set :)

---

### Post by SomeGuyDude on 2008-03-01
If anyone has a "spare machine" on hand, why not just highlight everything, hit "install" and just let 'er roll? I sadly don't, but I'd LOVE to see how this turned out.

I have to admit, this was the first thread title I've ever seen that made me laugh just reading it.

---

### Post by Vadi on 2008-03-01
Yes, someone did:

[http://www.fsckin.com/2007/09/29/giving-away-software-for-free-costs-more-than-you-would-think/](http://www.fsckin.com/2007/09/29/giving-away-software-for-free-costs-more-than-you-would-think/)

---

### Post by scragar on 2008-03-01
I'd do it on my spare machine, but it's only got a 20 GB HD...

---

### Post by spupy on 2008-03-01
Wow, guys, you have it easy! :D Imagine someone doing this in Gentoo... having to **compile** all the stuff!:shock:

---

### Post by SZF2001 on 2008-03-01
> **spupy said:**
> Wow, guys, you have it easy! :D Imagine someone doing this in Gentoo... having to **compile** all the stuff!:shock:

AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA

---

### Post by estaticd on 2008-03-02
> **Vadi said:**
> Yes, someone did:

[http://www.fsckin.com/2007/09/29/giving-away-software-for-free-costs-more-than-you-would-think/](http://www.fsckin.com/2007/09/29/giving-away-software-for-free-costs-more-than-you-would-think/)

Yes, I did it... lol.  I _do not recommend_ anybody actually do attempt to download all the packages just for fun or to brag about doing it, because unless you're doing something with each package you're downloading, you're wasting the resources of those who help Ubuntu by providing the repositories to begin with.

The process is NOT fun at all and takes a helluva lot of time.  I have a several locally hosted Ubuntu mirrors which can't max out my ~25Mb/sec internet connection - frustrating?  Yes.  :)

To correct Vadi on a minor point, I did not install all packages, but I did download all dependencies and all source code to build every packages listed in [this archive]("http://packages.ubuntu.com/gutsy/allpackages.en.txt.gz").  That list is NOT up to date however:

```
wayne@gutsy:~$ apt-get install [tab] [tab]
Display all 29817 possibilities? (y or n)
```

As far as 36GB for a mirror, that would *only* include binary packages for one CPU architecture.

I downloaded ~93GB just getting the source code... which includes everything to build a program from scratch, so things like images, help files, etc in a program came along with the source code.

In the repositories, there are x86, amd-64, and sparc versions of all those ~30,000 packages - it ends up being quite a bit of space,

I would guess it takes around 180GB to mirror source code and binary repositories of main, multiverse and universe for 3 different architectures PER release - if you count dapper, edgy, feisty, gutsy, hardy - that ends up being something like 1TB (or more) total disk space required for a full mirror.

Anybody care to elaborate and provide real numbers for disk space used on a full Ubuntu repository mirror?

-Wayne

---

### Post by gnome.youbuntoo on 2008-03-02
> **blithen said:**
> I know there would be some conflicts with packages and such but still, anyone ever do it? How did it go?
the entire repositories will occupy[COLOR="Blue"] 25GB+[/COLOR] of ur hard disk space and take several hours to download. Plus, ur *Applications Menu* will be cluttered. Do u wanna try out, even now???

---

