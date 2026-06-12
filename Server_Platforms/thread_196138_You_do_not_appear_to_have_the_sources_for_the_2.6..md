---
title: "You do not appear to have the sources for the 2.6.15-23-server kernel installed."
date: 2006-06-13
forum: Server Platforms
---

### Post by Harlyman on 2006-06-13
hi

need some help here, i'm working on a asterisk system and need to get installed  the sources for the 2.6.15-23-server kernel, i have installed the 2.6.15 but it don't help since uname gives the 2.6.15-23-server, and zaptel use the uname command to find the correct kernel version.

any ideas? anyone??

---

### Post by jameshuntsville on 2006-07-07
You need to update to the latest kernel... This will put your sources and you image in sync.

---

### Post by lamego on 2006-07-07
First you should make sure you are using the latest kernel version available with:
```
sudo apt-get update && sudo apt-get upgrade
```
Then you should be able to install the kernel source with:
```
sudo apt-get install linux-source
```

---

### Post by Harlyman on 2006-07-10
> **lamego said:**
> First you should make sure you are using the latest kernel version available with:
```
sudo apt-get update && sudo apt-get upgrade
```
Then you should be able to install the kernel source with:
```
sudo apt-get install linux-source
```

well the problem is not that easy, i have done that but it only install linux-source-2.6.15 not linux-source-2.6.15-server and that makes problem when installing zaptel for use with asterisk.

zaptel looks for the linux-source-2.6.15-server not linux-source-2.6.15.

---

### Post by lamego on 2006-07-10
There is no such thing as -source-server because there is only one source, the -server are just kernel options/patches .
You will need to create symbolic links where required to point to the "normal" kernel name. Or just hack the zaptel kernel name detetion script and force it to use the "proper" source name.

---

### Post by Harlyman on 2006-07-11
> **lamego said:**
> There is no such thing as -source-server because there is only one source, the -server are just kernel options/patches .
You will need to create symbolic links where required to point to the "normal" kernel name. Or just hack the zaptel kernel name detetion script and force it to use the "proper" source name.

why use a server option/patch if the kernel is the same? it only makes more work for us if there is applications that needs to know and use the kernel source to compile right

---

### Post by lamego on 2006-07-11
Some of this options make sense for servers which usually run more demanding resources (e.g. databases, file servers) but which would waste resources for desktop applications.

---

### Post by az on 2006-07-11
> **Harlyman said:**
> hi

need some help here, i'm working on a asterisk system and need to get installed  the sources for the 2.6.15-23-server kernel, i have installed the 2.6.15 but it don't help since uname gives the 2.6.15-23-server, and zaptel use the uname command to find the correct kernel version.

any ideas? anyone??

Can't you just use the linux-headers-server instead of the linux-source?

---

### Post by lejudd on 2006-07-12
Have you followed the instructions on the voip-info.org website?
[http://www.voip-info.org/wiki-Asterisk+Zaptel+Installation](http://www.voip-info.org/wiki-Asterisk+Zaptel+Installation)

I am using ubuntu and followed these instructions (for the linux 2.6 kernel) and all seems to be ok. 

Just be aware that the page mentioned also refers also to the 2.4 kernel but addresses the differences for the 2.6 kernel. 

The -23-server section is added to identify the kernel. You need to modify "EXTRAVERSION" statement in the Makefile in /usr/src/linux-source-2.6.15 to reflect that this is what kernel you are already running.

Check out the webpage, anyway. It explains this.

Hope this helps - L8

---

