---
title: "Should ubuntu fork the kernel to support Hardware ABIs / drivers?"
date: 2010-11-20
forum: The Cafe
---

### Post by madjr on 2010-11-20
so i was reading an article about some of the graphical problems on linux and came across this paragraph:
[I]
**Slashdot blogger hairyfeet wrote:**
"Personally, I am hoping that Canonical will just go ahead and **fork** the kernel away from Linus and thus finally give us a true 'third way' for home users," he added. "By adding a stable **hardware ABI**, drivers could be written that 'install once, run for years' like Windows and OSX, and with Wayland, it could finally make a desktop that is as easy to use thanks to Unity as Windows 7 and OSX Snow Leopard."[/I] 

more:
[http://www.linuxinsider.com/rsstory/71234.html?wlc=1290271064](http://www.linuxinsider.com/rsstory/71234.html?wlc=1290271064)

Another older comment on the matter, referring to how the solaris kernel handled things (anonymous):
> [I]**Hopefully hardware manufacturers will find that the open source and stable API/ABI of the Solaris kernel (and bsd?) makes building and maintaining drivers a piece of cake.**

The Linux kernel has a pretty impressive pace of development, but the constant, seemingly uneccessary churn in kernel API/ABI is a major pain when it comes time to do something outside whatever your distribution has decided to package.

I almost certainly wouldn't bother with Solaris as an OS (all its 'neat' features such as dtrace and zones are completely irrelevant to me), but I can certainly see some merit in using a kernel that doesn't force anyone who develops with it's code into a perpetual 'upgrade treadmill'

I understand the argument that the developers don't care about binary drivers, but even people writing GPL drivers are forced to constantly bug fix and upgrade them as the other kernel devs arbitarily decide to break stuff.

I find it stunningly hypocritical that the Linux kernel devs see it as paramount to keep their freedom to make changes in the way the kernel works by ensuring nobody can code against a stable ABI, and then beat up people like Hans Reiser because he sees it as paramount to keep his freedom to make changes in the way his filesystem works by implementing his own incompatible plugin system.[/I]

So would this solve the problems with plymouth, kms not being adopted by nvidia or ati, flickering, X, wayland, etc ?

am not sure, but if we're going with such a big change away from X, and are really trying make ubuntu unique from other distros (kinda like android/meego), by adopting wayland and using our own interface: Unity; Then why not also complete the polishing by adding hardware ABIs?

[Nvidia has no plans of supporting wayland, because of kms..]("http://www.phoronix.com/scan.php?page=news_item&px=ODc2Mg")

Am not sure if forking would be the best route, so does anyone know an alternate way other than forking the kernel so we can archive the same support/polish as in proprietary OSs directly from nvidia and ati?

Probably we could just add the support as modules, instead of hacking right in...

I know many will suggest the open drivers, but they will never have the same performance or support for some hardcore special features as the binary ones.

Speaking of open drivers, another idea would be to switch between both the open and binary driver on the fly, kinda like gpu switching? (well, if possible..)

ok, am out of ideas and not sure what you guys think, so discuss ! ;)

---

### Post by czr114 on 2010-11-20
Forking the kernel should be seen as a last resort. If the most popular desktop distro, which also commands a fair share of the server market, enters into divergent development, that can have consequences for the community as a whole.

Parallel development comes with a very real opportunity cost in man-hours spent. It should be avoided except as a last resort.

The preferred solution would be revamping the mainline going forward to reflect the modern challenges of using Linux in a desktop environment.

I realize that's much easier said than done.

That being said, graphics drivers in Linux have been a problem since the advent of the GUI itself, and it's time the problem was fixed for good.

---

### Post by madjr on 2010-11-20
yeah, i also think it should be as last resort

---

### Post by Ric_NYC on 2010-11-20
No fragmentation, please.

---

### Post by NCLI on 2010-11-20
No, no, and no. They should work with Linus to solve this within the mainline kernel.

Now, if he is not willing to even consider the idea, maybe Canonical should create a fork, though they should keep it as compatible as possible, and keep it up-to-date with and contribute to the mainline kernel, in order to avoid wasting developer time on developing features and solving bugs which may already have been solved.

---

### Post by JDShu on 2010-11-20
I don't think Canonical even has that kind of resources.

---

