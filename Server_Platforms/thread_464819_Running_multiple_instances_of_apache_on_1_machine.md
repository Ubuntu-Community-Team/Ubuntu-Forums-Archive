---
title: "Running multiple instances of apache on 1 machine"
date: 2007-06-05
forum: Server Platforms
---

### Post by gisaalter on 2007-06-05
hi,

I need to configure several web-applications using apache on the same machine
My situation:

1 apache running on port 8080
1 apache running on port 8888
1 apache tomcat running on port 9880

Right now, I've managed to install 1 apache on port 8080. 
I'm not sure how to configure the other ones, I'm unsure how to install
them. Can anyone help me out ?

Thanks !!

---

### Post by beatbros on 2007-06-05
Hi,

you can achieve this with different methods (Virtual Host, Reverse Proxy)
have a look here to find the best way to do it:

[http://webhosting.devshed.com/c/a/Web-Hosting-HowTos/Configuring-Apache-Intermediate/](http://webhosting.devshed.com/c/a/Web-Hosting-HowTos/Configuring-Apache-Intermediate/)
[http://ez.no/community/articles/multiple_apache_installations_howto](http://ez.no/community/articles/multiple_apache_installations_howto)

Bye

---

### Post by jtc on 2007-06-05
Well, I haven't done this myself, but at least I can give you a nod in the right direction.

Obviously all the Apaches need their own unique configurations files. To explicitly tell apache what configuration to read you use the -f flag. Except giving them their own port you might also want to give them unique pid-files. If you copy Ubuntus default apache2.conf then note that it uses includes with absolute paths, which you probably want to do something about.

To make your everyday use smoother you probably want to give them their unique apache2ctl and/or init-script. That is, copy and modify the existing ones. This is by the way when it comes in handy to have specified unique pid-files.

A lot of this is of course assuming you want to use the same apache2-binary for all three servers. Another option is to build/compile separate apaches, with their own default settings.

---

### Post by gisaalter on 2007-06-05
> **jtc said:**
>  Another option is to build/compile separate apaches, with their own default settings.

jtc, I thought that was impossible...so I CAN compile Apache 2 or more times on the same server ?
can you confirm that ? 
I'll give it a try...

---

### Post by jtc on 2007-06-05
> **gisaalter said:**
> jtc, I thought that was impossible...so I CAN compile Apache 2 or more times on the same server ?

Yes, that is very possible. Just make sure you give feed configure with different paths, or else the second install will overwrite the previous ones.

```
./configure --help
```

---

### Post by gisaalter on 2007-06-05
> **jtc said:**
> Yes, that is very possible. Just make sure you give feed configure with different paths, or else the second install will overwrite the previous ones.

```
./configure --help
```

jtc, thanks, but can you be a bit more specific ?
I'm quite new to ubuntu and wouldn't want to loose my original apache config...
Thanks for being so helpfull !

---

### Post by granilus on 2008-03-22
I was trying to setup something similar on my server. I mostly wanted to run two different Apache servers so that I could restart one without having to take down the other. (One server was a reverse proxy, the other was a Wiki.)

I had a hard time finding a good tutorial on how to do this, but I think I mostly got it working and wrote up the steps on my blog. I thought it might be helpful for this thread in case anybody was trying to do something similar: [http://blog.granilus.com/2008/03/multiple-apache-instances-in-ubuntu.html]("http://blog.granilus.com/2008/03/multiple-apache-instances-in-ubuntu.html")

Thanks to everybody on these forums for providing related hints that eventually helped me figure this out!

---

