---
title: "centos 7 vs Ubuntu 14.04 vs Ubuntu Core as web/db/app server?"
date: 2015-01-02
forum: Ubuntu, Linux and OS Chat
---

### Post by F.G. on 2015-01-02
Hello everyone,

I'm just starting on a small personal web project and was wondering what the general consensus was regarding the pros and cons of RH/Centos vs Ubuntu or Ubuntu Core as a server? I gather Ubuntu Core is basically a Docker server? I don't know  anyone who has used it, and don't currently think using containers will  be helpfull.

I'm probably going to just be runninng one machine, so it'll be running Apache and a db (postgres or mySql?) and some kind of webframework (maybe ruby on rail or something python based?). In principal it's all pretty flexible. At work I use RH, which i am familiar with in this context and I guess makes sense for an enterpise setup as they have support, but I don't need that. At home i tend to use Ubuntu or Arch.

So, i suppose for me it boils down to, 1) Out of the box security 2) Available packages  / repos? (then again there are loads for both). Principally I don't want to re-invent the wheel or get stuck spending hours on setup because no-one else has tried running Flask on Haiku. Also I don't feel I know enough about basic security to confidently go through it myself, i plan to enable selinux, and add a iptables rule to allow apache to be accessed externally.

I'm also considering using Amazon ec2, It looks like they offer Centos and Ubuntu, or debian but am open to suggestions regarding hosting. The location will ideally be somewhere in south-east Asia. 

Thoughts?

Thanks for all / any replies,
FG

---

### Post by Daletec on 2015-01-02
I am sure you'll find an Ubuntu-based appliance image ready to use at:  [http://www.turnkeylinux.org/](http://www.turnkeylinux.org/)

I find their images for forums, development, NAS, etc. very useful.  Page through the various images, I'm sure you find one useful, plus they are Ubuntu, which is familiar.

---

### Post by grahammechanical on 2015-01-02
I am a Ubuntu user on a Ubuntu forum, why would I recommend anything but Ubuntu? 

[http://www.ubuntu.com/server](http://www.ubuntu.com/server)

[http://www.ubuntu.com/cloud/](http://www.ubuntu.com/cloud/)

[http://www.ubuntu.com/cloud/tools/snappy](http://www.ubuntu.com/cloud/tools/snappy)

Regards.

---

### Post by Dragonbite on 2015-01-02
It's all up to whether you want to use the familiar CentOS/Red Hat version or the Ubuntu version in which you may have to read a little.

I use Ubuntu on my side because I am more familiar with that and its ease of setting up and running.  I've been tempted to try CentOS (or openSUSE) but I know that I would need more time to tweak and learn about it before I can use it.  

So are you going to be running and developing on the same machine? If so, have you made sure what applications you want to use for development are present (and up-to-date enough)?

---

### Post by F.G. on 2015-01-02
Hi all,

Thanks for your replies, I'll probably use Ubuntu server as it's not something I've used that much before. To answer your question Dragonbite, I haven't decided what applications i'm going to use, but I'll probably develop locally and then deploy frequently (maybe on commit, if I can be bothered to setup a jenkins instance or some other scm polling cron job type thing). I don't normally use that many development tools anyhow, so vim + the relevant interpreter / app server will probably do. I'm a little surprised not to see impassioned-dyed-in-the-wool supporters of each battling away about the finer points of package management, but I suppose that's a good thing.

I am curious about Ubuntu Core, I don't really understand how it works though. It sounds a bit like a docker container, like the image can be diffed and then updated or rolled back by being patched as a whole, ie so you basically have a version controlled image of your machine? But I may have got the wrong end of the stick.

cheers,
FG

---

### Post by Dragonbite on 2015-01-02
If you figure out how Ubuntu Core and docker container works.. let me know too?! ;)

---

### Post by bapoumba on 2015-01-03
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by ian-weisser on 2015-01-03
> **Dragonbite said:**
> If you figure out how Ubuntu Core and docker container works.. let me know too?! ;)

An example of Docker on Ubuntu Core is at [http://www.ubuntu.com/cloud/tools/snappy](http://www.ubuntu.com/cloud/tools/snappy)


> **F.G. said:**
> I am curious about Ubuntu Core, I don't really understand how it works though. It sounds a bit like a docker container, like the image can be diffed and then updated or rolled back by being patched as a whole, ie so you basically have a version controlled image of your machine? But I may have got the wrong end of the stick.

I think you're vision is about right.
Snappy provides the version (image) control and package manager.
Ubuntu Core provides the system on each image. It's intended for container/cloud use, and lacks firmware for many bare metal installs (though people can try; it's the same kernel as server/desktop). Ubuntu Core also lacks apt.
Docker is one framework that extends Ubuntu Core to make containers available for other uses. It also happens to include version (image) control for those other uses, which can cause confusion.

---

