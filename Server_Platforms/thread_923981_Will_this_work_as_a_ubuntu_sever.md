---
title: "Will this work as a ubuntu sever?"
date: 2008-09-19
forum: Server Platforms
---

### Post by housedog on 2008-09-19
hey guys I'm new to ubuntu and i need some help i have ubuntu 8.04lts and 7.10 sever addition heres what i need to know 1st

1st i have an old dell that i want to turn into a sever to host games and host websites...will it work as ubuntu sever its old and its hard wear specs are 256mb ram 2.6 ghz Intel CPU and 20 gig hard drive?

2nd will it be able to host windows games and websites?

3rd what disk should i use and what installation guide should i use so that it will be able to host games and websites 

thanks
housedog

---

### Post by baudday on 2008-09-19
What do you mean by what disk? That sounds like a system with some limited capabilities. It all depends on what kind of websites you plan on running, and the system requirements for the game servers. I'm sure a basic webserver would work.

---

### Post by housedog on 2008-09-19
hey thanks for the fast reply

"what disk should i use"
 i mean should i use the 8.04 lts sever edition or

the 7.10 sever edition

-----
i want sever to host basic personal websites and host some games low system requirement games "the games are not very demanding"

would lamp be the right set up opiton?..do you no a good website that guides you through set up process?

thanks 
housedog

---

### Post by baudday on 2008-09-19
I'm not sure on the basic system requirements for Ubuntu server, but if you're able to run 8.04, I would just go with the newer one. It's command line, so I would assume it shouldn't be much of a problem.

---

### Post by housedog on 2008-09-19
do you think i am beater off to install ubuntu desktop edition and use that as a sever as i am new to ubuntu?...you can do that right?

thanks
housedog

---

### Post by baudday on 2008-09-19
> **housedog said:**
> do you think i am beater off to install ubuntu desktop edition and use that as a sever as i am new to ubuntu?...you can do that right?

thanks
housedog

I would suggest getting the server edition and if you're not comfortable with command line (like me) you can install a GUI. Server edition allows you to install various servers like LAMP mail print samba. To install a GUI over it you just issue a very simple command depending on what GUI you want

---

### Post by TurboRush on 2008-09-19
You should be fine hosting a website with those specs. 

I have 7.10 server edition installed on an old HP unit with nearly identical specs and it hosts my website, mediaserver (it works, haven't really tried it with anything heavy duty yet), and also acts as my backup server.

Either 7.10 or 8.04 will be fine, I would advise that you go forego the Desktop version so you have a "minimal" amount of services running and unnecessarily consuming resources. You'll be able to find tutorials to do just about anything you want via command line.

Assuming this isn't your primary PC, best way to see how it performs it to install what you want and push it until it falls over... :guitar:

---

### Post by housedog on 2008-09-19
hey thanks for the replies yea not very comfortable with command line would like to in stall a GUI over top but i failed to do SO heres what i did:

i set up the 8.04 sever last night by flowing this guide [http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html](http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html)

every thing worked fine it finished installing and ran the command line i was not very confident with the command line so i deiced to install a GUI over top so i type In the  console

[PHP]sudo aptitude update

sudo aptitude install ubuntu-desktop[/PHP]

it finishes downloading then i type 

[PHP]sudo /etc/init.d/gdm start[/PHP]

it says 
*starting gnome display manger...                           [ok]

then nothing happens it goes to a new line in the console and doesn't load the GUI!! thats all i have done i haven't changed any settings or anything any help guys?

thanks
housedog

---

### Post by housedog on 2008-09-19
i am re-downloading sudo aptitude install ubuntu-desktop  

do you think that will fix it?

thanks
housedog

---

### Post by Iowan on 2008-09-19
The RAM may be the limiting factor for installing a desktop.

---

### Post by baudday on 2008-09-19
have you tried just rebooting after it's installed?

---

### Post by housedog on 2008-09-20
hey rebooted ...did not work i had to download about 66 files and it now works :P running GUI very happy and i am very happy :KS i have to flowed this guide [http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/](http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/) and it has got my ubuntu sever working on lan yay!:) as i can view a small website a made now i would like to know how to get my sever working on the Internet so every one can see my website any one know of a noob friendly guide that will show me how to do so?

also running 8.04 on 256 mb of ram is pushing it a little sluggish at some times"when i have about 2+ apps running lol" it should be fine to sever web sites any way 

thanks 
housedog:popcorn:

---

### Post by windependence on 2008-09-20
> **baudday said:**
> I would suggest getting the server edition and if you're not comfortable with command line (like me) you can install a GUI. Server edition allows you to install various servers like LAMP mail print samba. To install a GUI over it you just issue a very simple command depending on what GUI you want


Just FYI, you can install all that stuff easily on the desktop edition also. If you really have to have a GUI and you're just doing a small home server, there is really no reason to load server and put a GUI on it. You're kinda defeating the purpose of the product.

-Tim

---

### Post by Vivaldi Gloria on 2008-09-20
> **housedog said:**
> and it now works :P running GUI very happy

Nice to hear that you got it fixed. 

Ubuntu desktop will be a little slow on 256mb ram. You can also try openbox which is much ligher. Either install it yourself using [[COLOR="Sienna"]urukrama'a guide[/COLOR]]("http://urukrama.wordpress.com/openbox-guide/") or use [[COLOR="Sienna"]crunchbag[/COLOR]]("http://crunchbang.org/projects/linux/") which already uses openbox.

The best is of course getting used to command line and using no gui at all. See the links in CLI in my sig to improve your command line.

---

### Post by housedog on 2008-09-20
thanks for the replys guys 

dose any one know a noob friendly guide for hosting websites on the sever i just made 

thanks
housedog:popcorn:

---

