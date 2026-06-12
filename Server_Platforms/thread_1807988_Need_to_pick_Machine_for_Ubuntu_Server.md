---
title: "Need to pick Machine for Ubuntu Server"
date: 2011-07-19
forum: Server Platforms
---

### Post by asdasDan on 2011-07-19
Hey guys, long story short: I need to setup a server in my home, I plan on it being mainly a web/mail/development server, php/apache/mysql/postfix, and of course some development tools (Xdebug), and I need it to be running 24/7. I was planning on using ubuntu server edition and just secure shelling in after I had it setup, so I need a machine that's cheap, lightweight hardware, and can be fine left running constantly.

I was thinking something along the lines of a shuttle, or something like this:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856176025](http://www.newegg.com/Product/Product.aspx?Item=N82E16856176025)

However, I'm unsure how they are in the cooling department.

I know the basic minimum requirements for ubuntu server are extremely low, but what do some people experienced with it have to say about minimum requirements, how much ram/how powerful of a cpu do you need for the server to be running smoothly?

Thanks for any/all advice!

---

### Post by mcarrara on 2011-07-20
What kind of load will the server see?  Just one client (you)?  Most likely you will not use a GUI so I would think you could get buy with a pretty simple machine.  I would go for a older off lease or used computer.  Add a little RAM and you should be ready to go.  Right know I have a Pentium 4 with 1 gb RAM running as a test server.  It has the LAP stack(I connect it to my main MySQL server) and webmin.  I have not run into any problems.  If you are concerned about losing data, buy a new HD and use the original with rsync to backup the important data.  The worst that can happen is the power supply dies, but your HD can be put in another computer.

---

### Post by rubylaser on 2011-07-20
I've run Ubuntu server on a socket 939 AMD 3000+ for years.  I just recently upgraded to an AMD X2 240e.  The 3000+ is great as long as you don't need to compile code.  So, you don't need a much of a processor at all.  I've ran 2GB of RAM for a long time, and also recently upgraded to 4GB because RAM is so cheap these days.

At work, we have a Blender render farm that has ( 8 ) Q9550 quad cores in Shuttle cases, and they've been running well for almost 2 years now.  I'd probably just build my own Zacate powered machine if you want to go the APU route (you will need to run a recent kernel 2.6.38+).  It will be cheaper, and you could build in some extra cooling.  Something like this.

**[[MOBO+CPU+GPU]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813157228")** [COLOR="Red"]$99.00[/COLOR]
**[[CASE+PSU]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811154091")** [COLOR="red"]$44.99[/COLOR]
**[[FAN]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16835226024")** [COLOR="red"]$12.99[/COLOR]
**[[MEMORY]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820146742")** [COLOR="red"]$39.98[/COLOR]
_**TOTAL:** [COLOR="red"]($197)[/COLOR]_

This should be pretty quiet, and able to cool itself better than the Giada.  You could spend a little more money on the Zacate board, and go [this route]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131732") instead if you don't want the 40mm fan.

---

### Post by That Guy Is Here on 2011-07-20
I dont think I'd use a nettop for a server. They are quiet and small, but I would worry about it over heating from being on 24/7. I would say build your own or buy a used PC/Old server. If you build your own, you can do it extremely cheaply with parts these days. I would be glad to help you with that, but we need to know what kind of load and more about the usage of it.

---

### Post by Entilza on 2011-07-20
That Giada is one cool looking PC..

There are so many of these nowadays, zotac have some too.

There were other versions that had integrated video memory which might be better if you want to actually run some games or something.

If you want a headless machine though you can probably find something cheaper?

---

### Post by asdasDan on 2011-07-20
Hey guys, thanks for all the suggestions, after looking through everything I ended up greatly considering something like this:
[http://www.newegg.com/Product/Product.aspx?Item=59-105-954](http://www.newegg.com/Product/Product.aspx?Item=59-105-954)
Price isn't a huge concern, just don't want to spend more than 400ish.

Along with additional RAM, and maybe even throwing in another hard drive and rsyncing or setting up a RAID. (No clue how to set one up).

The load of the webserver wouldn't be high, but it will be on the internet and act as a development server for me and a few others, and I would put legit content on there except I know the internet connection couldn't handle it.

Most of this ordeal is giving me a cool development server, while learning a ton about configuring/securing/maintaining an apache server.

---

