---
title: "every kernel release kills VMware workstation, (tired of it)"
date: 2013-10-31
forum: Virtualisation
---

### Post by pksings2 on 2013-10-31
Hello all;

I have VMware workstation running on my Ubuntu box, along with an updated kernel, 3.8 variety. It supports my USB 3.0 adapters whereas the "stock" 12.04 kernel does not. I only run LTS releases for stability.

Every kernel release kills VMware, it cannot find the correct kernel headers. I'm really tired of doing this over and over and over again. Days and sometimes weeks of trying to find a where some genius finally posts a patch or something that allows me to go back to normal. This is so contrary to why I started using Ubuntu, for years it has just worked, lately, it hasn't, I have had to spend inordinate amounts of time trying to fix it.

That being said, what is the best way of preventing the kernel from updating? I realize that I will be "missing" some potentially important updates, but I cannot keep doing this..

Unless of course, somebody has a better idea on how to solve this?

Thanks in advance.

PK

---

### Post by daitau on 2013-11-01
Is using alternative VM products like Virtualbox an option for you? It is quite painless so far on Ubuntu.

---

### Post by TheFu on 2013-11-01
If you are installing exact headers, then that is the issue. Use the meta-package instead.
[http://blog.jdpfu.com/2012/07/05/virtualbox-guest-extension-dependencies](http://blog.jdpfu.com/2012/07/05/virtualbox-guest-extension-dependencies) explains how to determine which meta-package you should install.  That should over it, provided the VMware guess additions are automatically relinked after a new kernel is installed.

BTW, I've generally been highly impressed with VMware Workstation. If you need desktop-on-desktop virtualization, I think that is be best choice regardless of price, provided the corporate wish-washiness from VMware doesn't bother you. ;)

---

### Post by PJs Ronin on 2013-11-02
^^ can't get the link to respond

---

### Post by warp99 on 2013-11-02
It's simple. First see what kernel you are running:

```
uname -r
```

Then install the header meta-package that corresponds with the kernel:

```
sudo apt-get install linux-headers-generic
```

or

```
sudo apt-get install linux-headers-generic-pae
```

Now the headers will always be current with the kernel.

---

### Post by TheFu on 2013-11-02
> **PJs Ronin said:**
> ^^ can't get the link to respond

China, Russia, or Romania?
Or is your ISP prone to internet abuse?  Places like that are blocked by the server. Sorry.

---

### Post by PJs Ronin on 2013-11-02
> **TheFu said:**
> China, Russia, or Romania?
Or is your ISP prone to internet abuse?  Places like that are blocked by the server. Sorry.

Aussie... with Telstra

Edit: can't get there on my iPhone either.

---

### Post by pksings2 on 2013-11-04
Thanks all for your responses, much appreciated. Unfortuneately however, none of them has worked. VMware is still looking for the appropriate headers to recompile the module.
And, no, Virtualbox (which I have running on a different Ubuntu box) will not supply my needs on this one..

PK

---

