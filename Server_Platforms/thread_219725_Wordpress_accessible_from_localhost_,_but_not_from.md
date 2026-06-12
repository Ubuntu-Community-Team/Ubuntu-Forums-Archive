---
title: "Wordpress accessible from localhost , but not from internet"
date: 2006-07-20
forum: Server Platforms
---

### Post by harisund on 2006-07-20
I am not sure if this is a Wordpress configuration issue or a apache2 configuration issue. 

I installed wordpress by the standard method, first installing mysql etc, creating database all that stuff. 

The funny thing is, I am able to access the wordpress installation just fine from the same machine. [http://localhost/~wordpress](http://localhost/~wordpress) (I have created a user called wordpress for that, and enabled userdir)  everything works fine and the php is parsed, mysql databases accessed and so on. 

However, I go to a different machine on the internet and access it, firefox wants to download a file, the httpd file. 

I am thinking there is some apache configuration that prevents viewers outside of the local subnet or something like that. 

Any ideas?

---

### Post by cptnapalm on 2006-07-20
I'm not too sure what you mean by the httpd file... the httpd.conf file?  If so, that is truly bizarre.

How are you accessing the machine?  By IP address or URL?

(BTW, I am assuming that you installed Word Press through Synaptic or apt-get.  Also, I am not near my Linux computer as I am at work so I might be a bit off on directories and whatnot.)

Assuming you set up WordPress from the /usr/share/wordpress/examples setup script, what did you call the site during setup.  I have found that wordpress will ONLY respond to that name.  For example, I have Apache2 with WordPress running on my laptop and, when I'm at home, a URL points to it.  I set it up to point to autobituary.com.  WordPress will NOT respond to [www.autobituary.com](www.autobituary.com).  While it may be possible to get it to do so, I don't know how.

---

### Post by nix4me on 2006-09-16
I am also having similar problems.

I can use it fine from localhost but not from the net.  I messed around with the location urls and i could see the blog from another machine via my domain name however the page was all messed up with the text inline.

Weird.  Ive wasted 2 days on this already.

nix4me

---

### Post by pufuwozu on 2006-09-16
Sounds like a hardware firewall problem. Nothing to do with Apache.

You'll probably have to port-forward or allow port 80 connections on whatever you use - a router, possibly?

---

### Post by chrisfay on 2006-09-16
> However, I go to a different machine on the internet and access it, firefox wants to download a file, the httpd file. 

Can you access 'anything' on your webserver outisde your network?

> WordPress will NOT respond to [www.autobituary.com](www.autobituary.com). While it may be possible to get it to do so, I don't know how.

Did you add the [www.autobituary.com](www.autobituary.com) alias to your virtual host that points to the wordpress folder?

> You'll probably have to port-forward or allow port 80 connections on whatever you use - a router, possibly?

I would think if he was blocked on port 80, he wouldn't even get an option to download a file from Apache.

---

