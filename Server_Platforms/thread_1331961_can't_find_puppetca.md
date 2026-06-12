---
title: "can't find puppetca"
date: 2009-11-19
forum: Server Platforms
---

### Post by DouglasAWh on 2009-11-19
I'm actually on a CentOS box, but this is my favorite hangout, so I thought I'd ask here first. :)

I've got puppet installed, but reading the instructions at [http://www.debian-administration.org/articles/526](http://www.debian-administration.org/articles/526) I don't have puppetca.  Yes, those are Debian instructions, but they are better than the CentOS instructions I found.  I admin Fedora and Ubuntu boxes, so I'm familiar both.

Interestingly, just to make sure I had the client and server side stuff right, I typed in puppetca into Fedora and it asked me if I wanted to install puppet-server...which was no, but it makes me think I should be getting puppetca on the server.  I looked to see if it was a separate package, and it's not.

Ideas? Thanks!

---

### Post by konsole on 2009-11-19
puppetca comes from the puppetmaster package.

[http://packages.ubuntu.com/search?searchon=contents&keywords=puppetca&mode=exactfilename&suite=jaunty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=puppetca&mode=exactfilename&suite=jaunty&arch=any)

---

### Post by DouglasAWh on 2009-11-20
> **konsole said:**
> puppetca comes from the puppetmaster package.

[http://packages.ubuntu.com/search?searchon=contents&keywords=puppetca&mode=exactfilename&suite=jaunty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=puppetca&mode=exactfilename&suite=jaunty&arch=any)

Yeah, I know. Sorry I wasn't clear about having puppetmaster installed.  Seems like it doesn't get installed in the path or something on CentOS though.  All of that stuff comes from the EPEL repos.  I'll take a look again tomorrow when I get work and perhaps with fresh eyes I'll figure it out.

Thanks!

---

### Post by DouglasAWh on 2009-11-20
turns out /usr/sbin was not in the path.

---

