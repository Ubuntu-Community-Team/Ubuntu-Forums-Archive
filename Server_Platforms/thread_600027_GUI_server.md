---
title: "GUI server"
date: 2007-11-01
forum: Server Platforms
---

### Post by altonbr on 2007-11-01
After reading this thread about a fellow user having his boss force him to install a GUI for a server: [http://ubuntuforums.org/showthread.php?t=408620](http://ubuntuforums.org/showthread.php?t=408620), I was wondering how the state of such a system is in Ubuntu.

Say I went an installed Fluxbuntu or Xubuntu for my boss. What packages are there to administer PHP, MySQL, Apache, Postfix, etc.?

I noticed that there are a plethora for MySQL such as mysql-admin and mysql-query-browser or the dtc-* suite for other aspects of the server.

I know that Red Hat's business primarily has to do with competing with Windows Server and its GUI but my boss is looking for a free alternative.

What "sudo aptitude install ..." line would you recommend for a GUI server?

---

### Post by PetePete on 2007-11-02
theres a nice web interface one which means the server can be administrated from any computer (thats given access)

called, webmin

does lots of nice things, far better than running an actual gui on the server in terms of recources.

---

### Post by altonbr on 2007-11-02
I don't see it in the repositories and I'm quite sure he actually wants a GUI so he can use some of these MySQL admin piece of software. And no, I'm not talking about phpMyAdmin.

---

### Post by JasonRivers on 2007-11-02
Webmin isn't in the repo's have a look at [www.webmin.com](www.webmin.com) it's very very nice, though the default theme is a little.... dated.....

download webmin from there, as a .tar.gz, extract and just run "sudo ./setup.sh" it's very easy to use, easy to configure and just seems to work with most things.

for a nice theme for it, check out [http://www.stress-free.co.nz/webmin-theme](http://www.stress-free.co.nz/webmin-theme) it's a very nice clean theme and is what I use on my servers these days.

much better than installing X and lots of GUI tools :)

/J

---

### Post by gg234 on 2007-11-02
try [this]("http://www.ubuntugeek.com/ubuntu-710-gutsy-gibbon-lamp-server-setup.html") really helpful

---

### Post by altonbr on 2007-11-03
> **JasonRivers said:**
> Webmin isn't in the repo's have a look at [www.webmin.com](www.webmin.com) it's very very nice, though the default theme is a little.... dated.....

download webmin from there, as a .tar.gz, extract and just run "sudo ./setup.sh" it's very easy to use, easy to configure and just seems to work with most things.

for a nice theme for it, check out [http://www.stress-free.co.nz/webmin-theme](http://www.stress-free.co.nz/webmin-theme) it's a very nice clean theme and is what I use on my servers these days.

much better than installing X and lots of GUI tools :)

/J

Yeah, thanks. I've tried installing it on a VM server for now and it looks great, even with it's current theme. It's the theme BEFORE their current one that looks like it's from 1992. I do enjoy the one you showed me and I shall try it, thank you.

But just so you know, they have a Debian version that works with Ubuntu here:

```
$ wget http://prdownloads.sourceforge.net/webadmin/webmin_1.370_all.deb
```

and install via:

```
$ sudo dpkg -i webmin_1.370_all.deb
```

I'm sure you know this, but it's just for other readers.

> **gg234 said:**
> try [this]("http://www.ubuntugeek.com/ubuntu-710-gutsy-gibbon-lamp-server-setup.html") really helpful

Thanks, I found that information out myself and I already have the server installed (and have done many in the past).

I'm quite good at CLI Server Administration (as it's my job), I have just specific requirements to use anything in the repositories and to make it have a GUI interface using XFCE or Flux and I've never done this before.

What else is suggested?

---

