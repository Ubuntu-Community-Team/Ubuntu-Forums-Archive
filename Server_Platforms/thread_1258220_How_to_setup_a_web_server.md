---
title: "How to setup a web server?"
date: 2009-09-04
forum: Server Platforms
---

### Post by kronos262 on 2009-09-04
So I was following this guide [http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/4](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/4)
 
but I get issues at Samba. 
 
I can only assume i is because I am using, 9.04 and this guide is a little older.
 
I was just hoping to host some of my own webpages and maybe even a WoW private server, not too sure about the second one, but definitely web pages.
 
Anyone know a solid way to do it?
 
I use DreamWeaver to create websites.

---

### Post by gordintoronto on 2009-09-04
> **kronos262 said:**
> So I was following this guide [http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/4](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/4)
 
but I get issues at Samba. 
 
I can only assume i is because I am using, 9.04 and this guide is a little older.
 
I was just hoping to host some of my own webpages...


That guide is for setting up a file server.  You want a LAMP server.  (Linux, Apache, MySQL and PHP.)  If you are a little uncomfortable doing everything at the command line, you can install all the LAMP components in a regular Ubuntu system.  Apache is really all you need to host a few simple web pages.

---

### Post by kronos262 on 2009-09-04
> **gordintoronto said:**
> That guide is for setting up a file server.  You want a LAMP server.  (Linux, Apache, MySQL and PHP.)  If you are a little uncomfortable doing everything at the command line, you can install all the LAMP components in a regular Ubuntu system.  Apache is really all you need to host a few simple web pages.


I am totally comfortable with that. 

Not afraid of command line at all, since I do it often.. I will google a tutorial, and see what happens.

---

### Post by kronos262 on 2009-09-04
ok so I do

```
sudo tasksel
```

I select LAMP SERVER 

hit enter, and I get this message 

```
tasksel: aptitude failed (100)
```


Any Clues

---

### Post by Vegan on 2009-09-04
try the following:

```
sudo apt-get update
```

and see if that helps

---

### Post by kronos262 on 2009-09-04
I just noticed, updates were installing in the background, that is why it didn't work.

Got it installed now, so now I just need to learn out to use it.

---

### Post by Vegan on 2009-09-04
good luck, a book or 5 would be a real help

---

### Post by kronos262 on 2009-09-04
> **Vegan said:**
> good luck, a book or 5 would be a real help
Yeah I hear ya ha ha.

I am just using an old PC with 80 gigs at the moment to get used to it, before I spend on the bigger HDDs.

I got a UNIX course coming soon so hopefully that will help, and I also got that Ubuntu Pocket guide on my netbook. 

Learning is fun lol.

---

### Post by bear24rw on 2009-09-04
its easy to get started with web server all the files for the webserver are located be default to

/var/www

you might have to give yourself permission to that folder before you can edit the files

---

### Post by kronos262 on 2009-09-04
> **bear24rw said:**
> its easy to get started with web server all the files for the webserver are located be default to

/var/www

you might have to give yourself permission to that folder before you can edit the files



So I make a page in dreamweaver, save it then put it in the /var/www directory?

how do I set the address?

I static the ip already, and was able to access it on another computer (got a KVM switch going). 

Thanks for your responses.

---

### Post by bear24rw on 2009-09-04
i would just edit you pages straight in /var/www/ makes it easier (assuming your own the same computer)

what do you mean set the address?

to view the page just type you static ip in firefox

---

### Post by kronos262 on 2009-09-04
> **bear24rw said:**
> i would just edit you pages straight in /var/www/ makes it easier (assuming your own the same computer)

what do you mean set the address?

to view the page just type you static ip in firefox



If I want to access the site off the network.

Say I want to host my own review page or something. 

I want it to be accessed off the network as well. 

Dreamweaver, is on another computer, so I will have to put the files on a flash drive and copy it over to the directory.

---

### Post by bear24rw on 2009-09-04
> **kronos262 said:**
> If I want to access the site off the network.

Say I want to host my own review page or something.
I want it to be accessed off the network as well. 


Foward port 80 on your router and then give people your external ip found at

[www.whatismyip.com](www.whatismyip.com)

> **kronos262 said:**
> 
Dreamweaver, is on another computer, so I will have to put the files on a flash drive and copy it over to the directory.

Flash drive??? <cringe>

on the webserver do

$ sudo aptitude install openssh-server

then on your dream weaver computer install filezilla client 
and connect to your webserver using its local static ip and port 22

click and drag your files over :)

dreamweaver might even have ssh syncing capabilities idk

EDIT:

Filezilla client for windows

[http://filezilla-project.org/download.php?type=client](http://filezilla-project.org/download.php?type=client)

---

### Post by kronos262 on 2009-09-04
> **bear24rw said:**
> Foward port 80 on your router and then give people your external ip found at

[www.whatismyip.com]("http://www.whatismyip.com")



Flash drive??? <cringe>

on the webserver do

$ sudo aptitude install openssh-server

then on your dream weaver computer install filezilla client 
and connect to your webserver using its local static ip and port 22

click and drag your files over :)

dreamweaver might even have ssh syncing capabilities idk

EDIT:

Filezilla client for windows

[http://filezilla-project.org/download.php?type=client](http://filezilla-project.org/download.php?type=client)


Der forgot about the FTP. Yeah Dreamweaver has that built in. 

thanks for the info

---

