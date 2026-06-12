---
title: "ia32-lib problem, catch 22?"
date: 2012-12-30
forum: Server Platforms
---

### Post by Nysaan on 2012-12-30
Hi.
I'm running my first Ubuntu server and i've gotten everything to work except for hosting my CS:GO server.

When I try to install it, it complains that ia32-libs doesn't exsist.
So I did try **[COLOR="SandyBrown"]"apt-get install ia32-libs"[/COLOR]** but it couldn't be installed because of:
```
"ia32-libs: depending on: ia32-libs-multiarch"
```

Then the next thing came:


```
ia32-libs-multiarch:i386:
Beroende av: libgphoto2-2:i386 men det kommer inte att installeras
Beroende av: libsane:i386 men det kommer inte att installeras
```

And the list goes on and on and on.. How do i solve it ? :/

Sorry, but it's swedish -.-

---

### Post by gordintoronto on 2012-12-30
Because of the mix of languages, I don't know what the problem is. Perhaps you could translate?

Did you try:
sudo apt-get install ia32-libs-multiarch

What version of Ubuntu?

There is no reason you can't use Ubuntu desktop as a server, other than a very minor performance hit. That way, all the normal tools (synaptic!) are available to you.

---

### Post by sandyd on 2012-12-30
> **Nysaan said:**
> Hi.
I'm running my first Ubuntu server and i've gotten everything to work except for hosting my CS:GO server.

When I try to install it, it complains that ia32-libs doesn't exsist.
So I did try **[COLOR="SandyBrown"]"apt-get install ia32-libs"[/COLOR]** but it couldn't be installed because of:
```
"ia32-libs: depending on: ia32-libs-multiarch"
```

Then the next thing came:


```
ia32-libs-multiarch:i386:
Beroende av: libgphoto2-2:i386 men det kommer inte att installeras
Beroende av: libsane:i386 men det kommer inte att installeras
```

And the list goes on and on and on.. How do i solve it ? :/

Sorry, but it's swedish -.-

Are you using an openvz VPS?
If you are, post the output of the command below
```

ls /etc/apt/preferences.d/
cat /etc/apt/preferences.d/*
```

Some providers (such as mine...) have a bad pin that screws up 32bit libs.

```

libc6-dev libc-dev-bin
``` needs to be added to the ```
Package:
``` line

---

