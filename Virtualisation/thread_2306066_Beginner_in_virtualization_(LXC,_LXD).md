---
title: "Beginner in virtualization (LXC, LXD)"
date: 2015-12-11
forum: Virtualisation
---

### Post by Reiny Junior on 2015-12-11
Hello friends, i will be direct !

What is the correlation between lxd and lxc in simple words?
Why containers created with lxc-create command not appear in "lxc list" command ?

Thanks

---

### Post by TheFu on 2015-12-12
websearch "*lxd vs lxc*" says:

> LXD (sic) Relationship with LXC

LXD isn't a rewrite of LXC, in fact it's building on top of LXC to provide a new,
better user experience. Under the hood, LXD uses LXC through liblxc and its Go binding
to create and manage the containers.

It's basically an alternative to LXC's tools and distribution template system
with the added features that come from being controllable over the network.

LXD is licensed under the Apache 2 license.
LXD is headed by Canonical, the makers of Ubuntu.

Neat trick, huh?  Use "vs" to see comparisons of anything. Also, like a product and add "vs" to see alternatives.  "linux vs" ... 

Anyway, hope that helps.

---

### Post by Reiny Junior on 2015-12-12
I read documentation of two technologies (very limited), but how i said, i dont have experience in virtualization, i need a simple explanation, i'm  a beginner, i make a bunch of web search, e read a bunch of articles !

[http://linuxcontainers.org](http://linuxcontainers.org)
[http://flockport.com](http://flockport.com)

and much moore ! Thanks !

---

### Post by TheFu on 2015-12-12
How much experience do you have with chroot?  cgroups?  server administration?  With those vocabularies, we can start talking.  We were all new at some point, so keep asking. Some light reading:
[https://en.wikipedia.org/wiki/Chroot](https://en.wikipedia.org/wiki/Chroot)
[https://en.wikipedia.org/wiki/Cgroups](https://en.wikipedia.org/wiki/Cgroups)
[https://www.kernel.org/doc/Documentation/cgroups/](https://www.kernel.org/doc/Documentation/cgroups/)
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

I've only played with LXC myself, so hopefully someone with a better take on these technologies will step up and provide the details you seek plus correct everything I got wrong. Hopefully. ;)

---

### Post by Reiny Junior on 2015-12-14
Ok thanks =) !

---

### Post by bobk48 on 2015-12-23
It also depends greatly upon what you want to use virtualization for. That is, if you only want to experiment with hypervisors ( like VirtualBox) to run say a single guest machine under a host, that is one very easy, well-documented approach for a beginner and single user on one host machine. But if you want to learn about operating system level virtualization (lxc, lxd, Docker) that is way more difficult due to lack of good documentation( as you mention and I second your vote here), and you would have a completely different reason for doing it. One of the reasons being, for example, running multiple containers on a single server, where you have web-facing apps like nginx in those containers for security and other reasons. So you first have to figure out what you want to learn about, then go after that method. IMHO lxc, lxd, Docker are locked up because they are highly commercially viable systems of information right now- unless you want to break into that business where venture capitalists are pouring $50million at a time into those things, stick with hypervisors they're more fun and easier and more rewarding to deploy for the average user.

---

### Post by bmullan2 on 2015-12-23
I'll try to answer.

The LXD implements the means to communicate with both remote & local LXC daemon's running on remote or local servers or even in hw VM's like KVM/virtualbox etc using a new LXD/LXC REST API.   If you don't know what REST API means then you'll have to google.

LXC can be used in 2 ways...  Priviliged LXC containers and Un-Privileged LXC containers.    

What's the difference?   

You would create a "privileged" container using SUDO  

                           $ sudo lxc-create -t download -n my_cn_name

Access to a "privileged" LXC container requires someone to have SUDO privileges.

But what about normal non-sudo users?   How can they use LXC.   That's where un-privileged LXC containers come in.    Any user can create an un-privileged LXC container 

            $ lxc-create -t download -n my_cn_name

*Did you note in the above there's no SUDO* before the lxc-create command ?

LXD/LXC by default now uses "unprivileged" LXC containers.    

In LXD/LXC, the LXC command line & options add new capabilities to LXC such as the ability to specific a certain Host/server target for the LXC activity to be directed to.

This is different from LXC in the past where the LXC commands were **_always_** executed on the local host.

To implement the new LXD capabilities new LXC command options had to be introduced so although the traditional lxc commands still work... the NEW LXD/LXC commands are not only simpler but easier to remember... as well as MUCH more powerful.

So with LXD/LXC if you execute an LXC command: 
If the command is intended for a remote Host/server then LXD will send via REST messages to the LXC daemon running on that Host/server for those commands to be executed.
if the command is intended for the localhost... they just get executed locally as LXC in the past.

Stephane Graber (one of the Lead LXC developers) gave a great presentation to explain LXC !

The Video recording of the presentation is on Youtube -  [https://www.youtube.com/watch?v=yEr_EIZG0ZM](https://www.youtube.com/watch?v=yEr_EIZG0ZM)

I'd highly recommend watching it.

In my opinion you should only focus on the LXD/LXC and that command line syntax as that is the future.

LXD/LXC is so easy to use.   You really can't hurt our system [by installing LXD/LXC and just trying it]("https://linuxcontainers.org/lxd/getting-started-cli/").   

Everything you do with it is in an LXC container and doesn't touch your Host OS config/installation.

I'd follow the instructions to install LXD/LXC and then may just watch  start/stop Stephane's video and execute the same commands he does .. follow along in a sense.

You'll very quickly learn how its working and I think be fascinated with what you can now do.

---

