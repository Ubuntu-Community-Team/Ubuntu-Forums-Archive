---
title: "Advantages of Ubuntu Server over Debian?"
date: 2009-02-13
forum: Server Platforms
---

### Post by Yashiro on 2009-02-13
Are there any?

---

### Post by Dr Small on 2009-02-13
A disadvantage, which I learned from, is that you must keep the system up to date (and seriously, I mean up to date). Eventually, they drop the old repositories and then you are stuck without any software. So, I just moved to Debian and using the Stable repository.

---

### Post by tubezninja on 2009-02-13
On the other hand, some users (myself included) view the frequent package updates as a plus.

It really all depends on what you're doing with the server.  If updating and keeping software packages moving forward is a priority, as is security patching, then Ubuntu is what you want to use.  If you plan on putting a server in place and keeping the software stable over a long period of time, then go with either an LTS release of Ubuntu, or with Debian Stable.

---

### Post by glotz on 2009-02-13
So what you're saying is Ubuntu is better for security than Debian?

---

### Post by tubezninja on 2009-02-13
My experience has been that the Ubuntu dev folks seem to roll out security patches more quickly.  In that context, I guess you could say they are better.

Either way, both are pretty secure.

---

### Post by koenn on 2009-02-13
> **scaredpoet said:**
> On the other hand, some users (myself included) view the frequent package updates as a plus.

It really all depends on what you're doing with the server.  If updating and keeping software packages moving forward is a priority, as is security patching, then Ubuntu is what you want to use.  
This is misleading, as it can be interpreted as if Debian doesn't release security patches for its Stable release. 
Hence the next post
> **glotz said:**
> So what you're saying is Ubuntu is better for security than Debian?

---

> **scaredpoet said:**
> My experience has been that the Ubuntu dev folks seem to roll out security patches more quickly.  In that context, I guess you could say they are better.
It would be interesting if you could show some examples, because the facts seem to contradict your proclaimed experience. If you have a look in the security repo, you'll see that "universe" security updates have been taken straight out of debian, while the "main" security updates are a mixture of debian packages and ubuntu packages. The latter may well just be ubuntufied debian packages.
So, how would Ubuntu be able to release these updates sooner than Debian ?

---

### Post by koenn on 2009-02-13
> **Dr Small said:**
> A disadvantage, which I learned from, is that you must keep the system up to date (and seriously, I mean up to date). Eventually, they drop the old repositories and then you are stuck without any software. So, I just moved to Debian and using the Stable repository.
I wouldn't even think about a server with a 6 month release cycle and a 'get every release upgrade or get stuck without a migration path' policy. 
It's OK following and testing new developments, but not for a production server. 
LTS might be a acceptible, Debian is safe.

On the other hand, Debian is more of a (well tested, well maintained, well organized, ...) software repository run by volunteers, where Ubuntu is more of a product (with its possibly more integrated than is the case with Debian) and has the option to get professional corporate support. That may be a reason to lean towards Ubuntu in some cases. Or Red Hat or Novel, of course.

---

### Post by unixeducation on 2009-02-13
Or you can buy professional Debian support services :).

---

### Post by koenn on 2009-02-13
> **unixeducation said:**
> Or you can buy professional Debian support services :).

never heard that before.
where can I get them ?

---

### Post by skunkbad on 2009-02-13
Are there any packages that monitor for updates, and then send an email to the admin, recommending action? Or perhaps a package that auto updates and restarts services to keep current?

---

### Post by jimv on 2009-02-14
OR you can put your server out behind your firewall and let it be a server and not fret about updates.

Unless this is going to be open to the internet...then you'll want to make sure than any apps you have that are serving data over the net stay up-to-date.

---

### Post by hyper_ch on 2009-02-14
I just prefer debian because it has proven to be rock-stable. If you setup a new server with Debian go with Lenny. It will be declared stable soon.

---

### Post by bigbearomaha on 2009-02-14
There is something to be said for both, buntu LTS is a strong option as it provides updates for 5 years and at that point, many admins are looking at newer hardware and re-evaluating software, etc.. So it gives them a 'window' to make changes they can plan for.

On the other hand, Debian uses a rolling release cycle which means, if you have no need to worry about the hardware, you can keep a system going , stable, for a tremendously long time.

The only possible negative is with a rolling repo, once they make a change, say from etch to lenny as the stable , then you are looking at a dist upgrade to continue getting support.  if your hardware won't support the kernel in Lenny, well, too bad for you.  keep what you have running without security updates, or improve the hardware to support the kernel.  That doesn't always have to be a deal breaker either.  if you buy the right mainboard that allows for updating to a new proc that is supported by the next kernel, with debian you have potential to run that machine for a very long time with minimal maintenance.

As usual in the Linux world, a lot is relevant to the situation and expectations  you have.  The fact that Linux provides so many worthwhile options to fit all those possibilities is incredible as   it is.


and remember, buntu or debian, it's all Linux.

have fun, learn lots, 

Big Bear

---

### Post by tubezninja on 2009-02-14
> **koenn said:**
> This is misleading, as it can be interpreted as if Debian doesn't release security patches for its Stable release. 

It's only misleading if you put words in my mouth, which you very clearly did.  Please don't do that.  It leads to unpleasant misunderstandings.

---

