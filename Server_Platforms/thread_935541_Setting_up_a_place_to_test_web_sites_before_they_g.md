---
title: "Setting up a place to test web sites before they go live"
date: 2008-10-01
forum: Server Platforms
---

### Post by kerryhall on 2008-10-01
I want to set up a place where I can test web sites before they go live. For HTML I would just open it in Firefox to see how it looks, but I have started to use php. What does everyone else do in terms of web site testing?

Cheers

---

### Post by cariboo on 2008-10-02
If you've got a spare computer sitting around you could use the server version of Hardy and select a lamp server during setup. There won't be a gui if you choose this option, so be aware of that.

Another option if you have to have a gui and just use the computer to test web sites, once you have the Hardy desktop installed go to System-->Administartion-->Synaptic Package Manager-->Edit-->Mark Packages By Task and select the lamp server installation option

The lamp server inclides the following componenets:
Linux
Apache2
Mysql
Php5

Jim

---

### Post by windependence on 2008-10-02
If you want to use just one box, you can use vmware ESXi or VMware Server and set up a virtual server.

-Tim

---

### Post by kerryhall on 2008-10-02
Thanks to both of you, but is there really no way to do it without having to set up another machine, real or virtual? I don't have an extra machine, and the vmware solution seems like overkill. What if I need multiple test servers? Would it be possible to configure apache so I can go to a url like
test1.localhost or test2.localhost? Or maybe localhost:8080 or something like that? And of course, these should not be accessible by the outside world.

Thanks!!

---

### Post by cpetercarter on 2008-10-02
You don't need a second machine, real or vitual. You simply need to install Apache, php (and MySQL and phpmyadmin if you need a database) on your own computer. When you have got these set up, [http://localhost](http://localhost) will display your "website", which you can then tweak to your heart's content before loading it onto a normal server and going live. First read through guidance in this forum on how to set up and start Apache etc - eg [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by jamesr on 2008-10-02
Hi All,

I would 2nd the last reply. I actually follow the Howto "the perfect server" from the [www.howtoforge.com](www.howtoforge.com) site. It is only necessary to install apache2 with php additions

---

### Post by kerryhall on 2008-10-02
I have a web server set up already on my machine, and it is currently live. I use the same machine for web dev, and I don't have another computer. That is the whole point, I need a testbed.

---

### Post by jms1989 on 2008-10-02
Setup another apache config file in /etc/apache2/sites-enabled/. Just copy the existing one and change the directory for the website and domain to use. Create a directory for the new server to use. Make sure that you have write permissions to it so you can add files.

I run about 8 seperate websites on this machine and 2 on another machine. I keep my files in ~/domains/*domain*/public_html/ and store my config files in /etc/apache2/sites-avalible/ and make a symlink to the avalible sites in /etc/apache2/sites-enabled/. Those files must be own by root and have read and write permission for root. Once you configure your new virtual server, restart it by running sudo /etc/init.d/apache2 restart in the terminal.

---

### Post by kerryhall on 2008-10-06
> **jms1989 said:**
> Setup another apache config file in /etc/apache2/sites-enabled/. Just copy the existing one and change the directory for the website and domain to use. Create a directory for the new server to use. Make sure that you have write permissions to it so you can add files.

I run about 8 seperate websites on this machine and 2 on another machine. I keep my files in ~/domains/*domain*/public_html/ and store my config files in /etc/apache2/sites-avalible/ and make a symlink to the avalible sites in /etc/apache2/sites-enabled/. Those files must be own by root and have read and write permission for root. Once you configure your new virtual server, restart it by running sudo /etc/init.d/apache2 restart in the terminal.

This is pretty much exactly what I am looking for. Thank you! I'll see if I can get this set up.

---

### Post by kerryhall on 2008-10-08
Ok, I got a question. How do I visit this virtual web site now?

---

### Post by ddarsow on 2008-10-08
I assume, if you are developing web sites, that you have access to a server. What I ususally do is upload the files to a "test" dir and hve this dir listed in the robots.txt file to be excluded from indexing by search engines.

That works for me anyway.

---

### Post by kerryhall on 2008-10-08
That's a good idea. I think it would be useful to know how to set up multiple web sites on one server though. Do you know how to set up what jms1989 is talking about? How do I visit the virtual web site once I set it up?

---

### Post by jms1989 on 2008-10-10
Opps, It seems I forgot that part. What I do is edit my /etc/hosts file to include the new domain or subdomain.

Something like this should work;
```

192.168.X.X     sub.domain.com

```

Of course that is just an example, you'll need to add your computer's ip address to the first column, add a few spaces or a tab, and insert you chosen domain. If you have multiple computers in your house, you can add that line to their hosts file along with your computers ip address and they should be able to access it as well.

---

### Post by kerryhall on 2008-10-13
Hmmm, but how do you get apache to attach an ip address to a virtual web site? For example, my web server is 192.168.1.101

If I set up a new virtual server, what identifier does apache give it? Does it get a completely new ip address? Or does it get a sub domain? Or does it get a new port?

Thanks!

---

### Post by lykwydchykyn on 2008-10-14
> **kerryhall said:**
> 
If I set up a new virtual server, what identifier does apache give it? Does it get a completely new ip address? Or does it get a sub domain? Or does it get a new port?

Thanks!

The answer is .. yes.  Whichever you choose.  When you set up a virtual host, you tell apache how to listen for it.  You can do this by the name used by the client, the ip address, or the port.

---

