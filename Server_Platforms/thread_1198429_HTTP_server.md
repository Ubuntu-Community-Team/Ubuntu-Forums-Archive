---
title: "HTTP server"
date: 2009-06-27
forum: Server Platforms
---

### Post by Muscovy on 2009-06-27
I have two questions regarding running an http server off Ubuntu.
-What software should I use?
-Does the server use port 80?

---

### Post by credobyte on 2009-06-27
> -What software should I use?LAMP ( Apache, PHP, MySQL )

> -Does the server use port 80? Yes!

---

### Post by Muscovy on 2009-06-27
Unless I'm mistaken, LAMP isn't the core http server itself. If it is, how do I set that part up?

---

### Post by DGortze380 on 2009-06-27
> **Muscovy said:**
> Unless I'm mistaken, LAMP isn't the core http server itself. If it is, how do I set that part up?

Apache is the the web sever.
You can have it installed along with the Server Ubuntu instsll, or sudo apt-get isntall apache2

---

### Post by philcamlin on 2009-06-27
did you use apache2 :popcorn:

---

### Post by Muscovy on 2009-06-27
I believe it was appache2.
  Also, I am using desktop edition for this. It's basically a 'play around with' server, and because the bottleneck for me is upload speed by a long shot, I went with GUI to make it easier for me.

---

### Post by v3xtra on 2009-06-27
> **credobyte said:**
> LAMP ( Apache, PHP, MySQL )

Yes!

Most of the time, you will want to just install LAMP, because it is easier than actually having to install each component individually....and you will probably want some sort of PHP / MySQL environment for most web sites to make them a lot more functional.  If you really are just going to be creating a page with some links to stuff, in HTML only, then just installing apache2 is the way to go.  Otherwise:

```

sudo tasksel install lamp-server

```

Should install all of the components of LAMP.

---

### Post by credobyte on 2009-06-27
> **v3xtra said:**
> Most of the time, you will want to just install LAMP, because it is easier than actually having to install each component individually....and you will probably want some sort of PHP / MySQL environment for most web sites to make them a lot more functional.  If you really are just going to be creating a page with some links to stuff, in HTML only, then just installing apache2 is the way to go.  Otherwise:

```

sudo tasksel install lamp-server

```Should install all of the components of LAMP.

Yes, maybe it's easier to install lamp package, but - if I want to be sure about what I have, I install all the parts separately. More over, it does not take any additional work ..
```
sudo apt-get install apache2 php5 libapache2-mod-php5 php5-gd php5-curl php5-xdebug php5-mysql mysql-server mysql-admin phpmyadmin
```

---

### Post by philcamlin on 2009-06-27
> **credobyte said:**
> Yes, maybe it's easier to install lamp package, but - if I want to be sure about what I have, I install all the parts separately. More over, it does not take any additional work ..
```
sudo apt-get install apache2 php5 libapache2-mod-php5 php5-gd php5-curl php5-xdebug php5-mysql mysql-server mysql-admin phpmyadmin
```


the code there is what youd want :popcorn:

---

### Post by credobyte on 2009-06-27
> **philcamlin said:**
> the code there is what youd want :popcorn:
[COLOR=Gray]sudo tasksel install lamp-server[/COLOR] ? Yes, it'll give me the same result, but, what if I want to remove php5-gd ? Will it remove GD module without removing the whole LAMP package ( remove != disable ) ?

---

### Post by R.Bucky on 2009-06-28
you need to keep the php5-gd as it processes graphics from php. if you are strictly using html pages, I believe you can do without it.

---

