---
title: "First hurdle with mod_rewrite..."
date: 2009-06-08
forum: Server Platforms
---

### Post by Qure on 2009-06-08
Hello there,

I'm relatively new to Ubuntu and Apache - I recently needed to set these up to work on a website. I'm trying to mirror the server's set up so I can work on it locally. 

Most things have been going fine, but one thing I still haven't been able to work out is how to enable mod_rewrite.

I've been following the instructions on Apache's site for configuring, making and installing Apache 2.0 from source, and according to the documentation, I should just have to specify "--enable-rewrite" when I run the ./configure command. I get a lot of debug out in the terminal as this happens, and it clearly states that mod_rewrite = yes. 

However, when I try to start the server, I get:
```
/usr/local/apache2/bin/httpd: error while loading shared libraries: mod_rewrite.so: cannot open shared object file: No such file or directory
```I don't understand why it isn't there?

I've followed many different websites I've found on how to enable this module manually, but all without success... can anyone point out what I did wrong with the above? 

Thanks very much

---

### Post by LepeKaname on 2009-06-08
Sorry, but why are you trying to compile apache?

You just need to install apache2 and set a symlink:

```
cd /etc/apache2/mods-enabled
sudo ln -s ../mods-available/rewrite.load .
sudo apachectl restart

```

That's all you need to do to use mod-rewrite

---

### Post by Qure on 2009-06-13
A few reasons - I'm mirroring our web server's set-up as closely as possible, which involves installing the exact same version of Apache. I believe installing apache2 through the package manager gets Apache 2.2, I need Apache 2.0.

Also, I will be integrating with Resin which recommends you compile/install yourself so that the files aren't all over the place. I don't think Resin works with Apache 2.2 either, could be wrong on that.

Any advice on getting mod_rewrite to work when installing Apache this way?

---

### Post by LepeKaname on 2009-06-13
Follow this post:
[http://ubuntuforums.org/showthread.php?t=1183268](http://ubuntuforums.org/showthread.php?t=1183268)

You can search for apache 2.0 in older repositories...

---

