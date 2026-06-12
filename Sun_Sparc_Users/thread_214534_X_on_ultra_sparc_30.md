---
title: "X on ultra sparc 30"
date: 2006-07-12
forum: Sun Sparc Users
---

### Post by grapnell on 2006-07-12
I have a Sun Ultra 30 creator with a strange graphics card. I have been head over heals trying to figure out what it is. I have taken it out, and found nothing on it that tells me what chipset it is.  I have successfully installed ubuntu-server on this machine, but No matter what I do, when I try to start X it gives me the no screens found error.  I tried this on generic vesa, vga, and fbdev drivers.  I really don't know where else to go with this.  I also tried installing a (known working) pci graphics card in this machine, but for some reason, the computer will not recognize it at all.  I have no idea how to go into the cmos, (if there is such a thing) on this sparc station. This is the first sparc ive ever dealt with.  I know linux/ubuntu quite well on x86 and ppc machines.  Any help would be appreciated. 

Thanks in advance,
Jeff

---

### Post by grapnell on 2006-07-13
Why does no one ever answer my posts whenever I post a question on a forum?  I see everyone else gets tons of replies, but me, well, I don't think I've ever had a reply to any thing I've ever posted.  If you need more info to be able to answer this question, let me know what it is, I will get it for you.

Thanks again,
Jeff

---

### Post by gevans on 2006-07-14
Hi Jeff,

I hate to say this, because I would *really* like to love linux as much as my friends do (I am typically a NetBSD guy myself), but I have noticed that the linux community in general hasn't been very helpful for me in comparison to the community for what I normally use.

As for your sparc question, the cmos you are asking about is the open boot prom [obp]. You get into it obviously (since you have ubuntu installed I am assuming) with stop-a and that should get you to an ok> prompt (if it says boot: just hit stop-a again and you will get the ok> prompt.

Here are some links to information about obp that might help you:

[URL="http://www.gentoo.org/doc/en/gentoo-sparc-obpreference.xml"]
http://www.gentoo.org/doc/en/gentoo-sparc-obpreference.xml[/URL]
[http://www.google.com/search?as_q=OpenBoot&num=30&hl=en&btnG=Google+Search&as_epq=Command+Reference&as_oq=&as_eq=&lr=lang_en&as_ft=i&as_filetype=&as_qdr=all&as_occt=any&as_dt=i&as_sitesearch=sun.com&safe=images]("http://www.google.com/search?as_q=OpenBoot&num=30&hl=en&btnG=Google+Search&as_epq=Command+Reference&as_oq=&as_eq=&lr=lang_en&as_ft=i&as_filetype=&as_qdr=all&as_occt=any&as_dt=i&as_sitesearch=sun.com&safe=images")

Sorry I can't help you more. I don't have a ton of experience with Sun hardware myself. Got my Ultra10 and Ultra1 just last year and threw Solaris 10 on the Ultra10 and NetBSD on the Ultra1 (it is running ubuntu sans gui now)

-Greg

---

### Post by netztier on 2006-07-14
> **grapnell said:**
> I have a Sun Ultra 30 creator with a strange graphics card. I have been head over heals trying to figure out what it is. I have taken it out, and found nothing on it that tells me what chipset it is. 

The "Creator" part of the Machine name is a hint that it might be a Creator or Creator3d card.

Checking with [sunsolve.sun.com's Ultra 30 page]("http://sunsolve.sun.com/handbook_pub/Systems/U30/U30.html") and reading the "Full Components List" right there shows what range graphics cards Sun did support with that Box. If you take the part number from each of these cards, you can search Sun's site for them and see drawings, sketches and pictures of the cards, so you'll be able to determine which one it is.

If it is a Creator card, use the **sunffb** driver with X.org and don't forget to load the **cfb** and **cfb32** modules in x.org.

See also [this thread]("http://www.ubuntuforums.org/showthread.php?p=955542#post955542"). 

Does no one ever use the search functions in these forums (or at least point out what search terms he or she used in Google or forum search)? :-k 

kind regards

Marc

---

