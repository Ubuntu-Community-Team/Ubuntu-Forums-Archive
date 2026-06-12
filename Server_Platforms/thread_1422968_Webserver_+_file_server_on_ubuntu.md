---
title: "Webserver + file server on ubuntu"
date: 2010-03-06
forum: Server Platforms
---

### Post by group256 on 2010-03-06
Hello everyone,

There are few questions I would like to ask and thanks a lot in advance for helping.

I have installed ubuntu server on one of my old laptops with openssh installed on it. I can easily access my files inside my network with no problem. Now I'm installing Apache, MySQL and PHP to make it a webserver as well.

1- First question is that, I don't need to have sophisticated website, just something that I can access my files. Something exactly like this:

[http://distro.ibiblio.org/pub/linux/distributions/puppylinux/]("http://distro.ibiblio.org/pub/linux/distributions/puppylinux/")

I want to know how I can have files like that, it seems like I'm using my browser to browse my files.

2- Second question, if I setup my webserver, but I just want a portion of my files to be accessed through the webserver, the rest it would be perfect just to be reachable through SSH. Is that really possible??

What I mean is, let's say, I have 2 folders, one is "my photos" that I want it to be accessible through the web browser and a folder with name of "private" that I just want them to be safe unless I access them using SSH.


Thank you very very much for any provided information.

---

### Post by HermanAB on 2010-03-06
Apache will index any directory that you point it to, so you need not do anything much for that.

However, if you want some control, then you may want to add a username and password to it with Apache basic authentication and if you want something fancy, then you may want OpenDocMan.

---

### Post by group256 on 2010-03-06
Many thanks for your help, but I'm not a professional, so could you please provide more details?

Thanks again.

---

### Post by stlsaint on 2010-03-06
Apache reads whatever is in the /var/www/ dir. So if you have a /var/www/photos... than that is what apache is going to output to your browser. All you need is apache (actually apache2 is what will be installed)

Therefore whatever you want to view than put it in the /var/www/ dir. But dont just put various files in there. Make a folder (ie: photos) than put the files in it and in your browser you will enter:

192.168.1.11/photos. (or whatever your server ip is)
Also if you plan on accessing this server outside your lan you will need to setup [port forwarding ]("http://en.wikipedia.org/wiki/Port_forwarding")in your router.

---

### Post by group256 on 2010-03-06
Thank you very much. I kept working on it and now I have full server connectivity. Web server + file server + ssh and ftp.

And I tried the Apache method, worked very good. Thanks a lot for the help.

---

