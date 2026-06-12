---
title: "Local Repository question"
date: 2010-06-22
forum: Server Platforms
---

### Post by akureikorineko on 2010-06-22
Hey guys! I am looking to make a local repository for my network since i have a VERY tight network bandwidth cap. However, i am also going to be using different package systems as well. (YUM and DEB packages) I was wondering if it was possible to host both of those packages on the same machine and host them on my network. Thanks in advance for the help! :D

---

### Post by brettg on 2010-06-22
Setting up a repository mirror would be difficult, time consuming and consume more bandwidth than it saves. You would have to rsync the entire repo even though you would probably only ever use a fraction of the total number of available packages.

What you actually want to do is set up an apt proxy, which caches any packages downloaded by your clients. Any subsequent clients that request the same package will be served from the cache.

See [this article]("http://tuxnetworks.blogspot.com/2009/05/apt-cacher-ng.html") on how to do this

---

### Post by akureikorineko on 2010-06-22
I see. Now i guess my next question is obvious. Is it possible to do multiple kinds of packages?

---

### Post by brettg on 2010-06-22
The question may indeed be obvious, but not to me :-)

It will do all deb files from any repository that can be accessed via apt get. 

If you want a general purpose web proxy you will want to look at squid. Squid is not a good option for apt-get though, as it will silently drop files if they are not accessed after a set time. apt-cacher-ng will keep local copies of all files until such a time as an updated version is downloaded.

---

### Post by tribaal on 2010-06-22
You might want to have a look at apt-proxy. It's a very efficient way to save bandwidth if you have multiple Ubuntu machines on the same LAN. The first machine downloads the package from the repos, subsequent calls to this package will get it from the local proxy instead.

If for some reason you wish to really have a proper *mirror* (copy all the packages to a local hard drive), you'll be looking at apt-mirror.
The setup isn't so hard (just a config file), and you can find plenty of documentation online.

A mirror for Ubuntu's repositories takes up about 30 Gb of disk space per architecture, per version (Karmic, Lucid, Maverick).

Hope this helps!

- Trib'

---

### Post by brettg on 2010-06-22
I used to use apt-proxy but I found it to crash a lot.

I also believe that another problem with apt-proxy is that you are required to configure every line of every clients sources.list to suit it. 

apt-cacher-ng is completely transparent apart from adding a single line to /etc/apt/apt.conf on each client.

But of course YMMV

---

### Post by akureikorineko on 2010-06-22
Thanks guys. :D This does help, i just need to find out if it is possible to do the same thing with RPM packages on the same machine. Rather not have two caching servers really.

---

### Post by brettg on 2010-06-22
One of the reasons that I don't like RPM based distros is the fact that there is no RPM proxy available AFAIK.

If anybody knows a working solution then I would love to know it too as I am forced to use Centos machines at work.

---

### Post by akureikorineko on 2010-06-22
I hope there is a solution. I want to do a lot of experimenting with many different distro's, and some of the distro's i am dealing with use RPM packages.

---

### Post by akureikorineko on 2010-06-22
[https://bugs.launchpad.net/ubuntu/+source/apt-cacher-ng/+bug/227240](https://bugs.launchpad.net/ubuntu/+source/apt-cacher-ng/+bug/227240)

Does this mean that it has already been fixed?

---

