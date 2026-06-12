---
title: "Apache default and default-ssl"
date: 2012-11-03
forum: Server Platforms
---

### Post by bigmonmulgrew on 2012-11-03
Hi
I was just looking through the ubuntu docs (again) and the apache part reminded me of a question I've been meaning to ask for ages.

Why is it that default and default-ssl (and any you create yourself) have to be separate files. Is it just a matter of organisation or is there some practical reason.

Would it work exactly the same if it was one long file.

---

### Post by volkswagner on 2012-11-03
It helps organization, yes.

It also make it easy to enable and disable sites via the command line.

```
sudo a2ensite filename
```

```
a2dissite filename
```

If you have a misconfigured vhost it may cause Apache2 to fail a restart.  With separate files it is easy to disable the site most 
recently modified and restart apache again.  This may be difficult if all your vhosts reside in one config file.

---

### Post by bigmonmulgrew on 2012-11-03
ok so assuming I want mysite and mysite-ssl enabled then would there be any downside to putting the contents of both in the same file.

---

### Post by bigmonmulgrew on 2012-11-03
other than the issue of finding a problem vhost, I was thinking of performance more of anything

---

### Post by sandyd on 2012-11-03
There isnt any performance benifit to having it in a seperate file other than the time it takes to find a vhost in a file when you have 30 other vhosts in there

---

### Post by bigmonmulgrew on 2012-11-03
> **sandyd said:**
> There isnt any performance benifit to having it in a seperate file other than the time it takes to find a vhost in a file when you have 30 other vhosts in there

great thats what I wanted to hear. I'm not putting a lot of Vhosts in the file just one for http and one for https

---

### Post by SeijiSensei on 2012-11-03
I'd be very surprised if Apache didn't cache all the virtualhost configurations when it starts up.  I doubt it has to read those files more than once when it is started.  Having to do file I/O on every request could create substantial performance problems on a busy server.

---

