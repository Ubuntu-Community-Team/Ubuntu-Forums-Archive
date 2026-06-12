---
title: "Which Version to grab for LAMP + KDE, etc"
date: 2008-05-15
forum: Server Platforms
---

### Post by Donb01 on 2008-05-15
I am new to ubuntu but not to Linux.  I'm running a server now on Mandrake 10.0, and formerly ran 9, 8, etc.

Time to do some upgrading and increase reliability.  This server is not going to be mission critical but that does not mean I want to lose data and rebuild stuff.  I run 4 websites off of it, and do a variety of other stuff - AWStats, some stuff with MySQL databases, etc, and I also need to run Weather Display on it, which requires an X environment, Glib, and other graphical stuff to be present.  I would need at least some of the development stuff on there, compiler, etc because some of my applications need to be made and compiled before use and they ask for this that and the other thing usually.

I just bought a refurb Dell Poweredge 2650 cheap.  In general it has dual Xeon 3.2 processors (which I assume are 32 bit), 5 SCSI HDs I am hoping to have in 2 RAID 1 Arrays and either save the other drive for a spare or use it for misc junk storage, swap, etc, and 4GB RAM, among less important things.

I need Apache, PHP, Perl, MySQL, Postfix, Bind, remote access via Putty/SSH, and probably other stuff I can't remember, in addition that I would want to be able to login on the console as a user (locked) because the Weather Display (which also "serves" data) needs to run as a user right now and it requires a fully tricked out X environment with most of the goodies.  Can I still run Apache 1.3?  I think I have one application that won't run on 2.0 but it has been so long since I set this last one up I don't remember.  Back then it was as simple as telling Apache to switch run states and run as 1.3 - I don't know if it still is that way.

So, do I download the LAMP Server version and then will have to add all the other crap, or do I download the Desktop version and it still has all the LAMP stuff with it, just in addition to all the desktop stuff?

When I installed Mandrake all I had to do was check all the things I needed off a manu of features at install time and it loaded all the packages I wanted.  I haven't done an ubuntu install yet, even though I downloaded the runnable CD of gutsy and played with it a while on my XP desktop machine without installing it.  The server version sounds like it comes "stripped" of all the extras, but does the desktop version come stripped of all the server/LAMP stuff?

I'm sure once I get that far and start playing with the RAID stuff that will be a whole other learning experience, but that's for a different day!

Thanks in advance.

---

### Post by tribaal on 2008-05-15
First of all - while I welcome you to using Ubuntu, why the switch? Why not stick to the distro you know best? 
I'm just curious :) 

Anyway, the server install will let you install a "LAMP" option at the end of the installation, which will install Apache2, MySQL and Php5. Basically, desktop and server share the same package repositories (just like Ubuntu and Kubuntu do), so this is just an easy front-end to installing the required packages.

You can just as easily install the AMP (since you obviously already have the L :) ) combo on your desktop install:

```
sudo aptitude install apache2 libapache2-mod-php5 mysql-server
```

and you should be all set. Most if not all the tools you use on Mandriva should work the same way too.

Hope this helps.

- Trib'

---

### Post by tribaal on 2008-05-15
[Here's an article]("http://howtoforge.com/perfect-server-ubuntu8.04-lts") I like on setting up an ubuntu server - you probably won't need the whole article often, but every part is quite concise and well explained, in my humble opinion.

Hope this helps

- Trib'

---

### Post by Donb01 on 2008-05-15
Well, actually I'm running Mandrake, which stopped existing (along with security updates) not long after I set it all up.  It became Mandriva, and I don't know what of those packages will run on my existing system and what won't.  I already broke KDE trying to update the graphics libraries, and lost the menu driven administration stuff I really like.  Looking at Mandriva world now it seems to be more about money and less about community, and that's kind of a turn-off.

I heard about ubuntu back in the 6 days and started looking at it and working towards the motivation to build a "real" server with some redundancy.  It seems to be much better supported, and there is a lot of excitement in the community - that's a good thing - especially since I will build this and unless it blows up it'll still be here 5+ years from now.  The new version of my survey tool requires MySQL5.  In order to use DKIM with Postfix it requires a much newer version than I have, and the list goes on.  I've only been waiting for the new LTS version to come out so I don't have to do this again for a few years!

I do want to do it right the first time, and then add on other stuff I like later.  I will take several months to build it, make sure it is what I want, port all my data and config to it, and then when it looks like it all works just change its IP address to my live one and let it loose on the world.  That way I can always flip the old one back on if anything goes wrong.

I'm not too proud to ask for help to ge me going in the right direction, and there are always opportunities to learn new tricks!

---

### Post by Donb01 on 2008-05-15
Thanks for the article!  I read thru the vast majority of it.  He seems to be doing an awful lot of stuff manually.  I understand the vast majority of what is going on, but I don't understand why one wouldn't just choose Bind, Apache, etc just off the menu and let it run on autopilot.  I'm going to need to have to edit all those config files anyway to put all my stuff in there.

The only other thing I'm going to need to figure out is how to do this install with DHCP.  I run everything static.  When I run ubuntu off the CD the network setup just fails, and then I go in and set a static IP and off I go.  It does not appear there will be an opportunity for that during Install.  Maybe I'll just slap some DHCP on one of my routers to let it get on the internet and then shut it off when I'm done...  I've been meaning to do that anyway for my wireless "guest" users - maybe I'll just have to motivate myself to get it done.

---

### Post by tribaal on 2008-05-16
Hum yeah, that article is doing pretty much everything by hand, which is usually not required, but at least it is quite a good reference when you want to do something GUI and autopilot doesn't handle...

There definately room for some wrapper scripts on the server side... Like a simple way to configure bind9 for common uses (most of the advanced stuff is too installation-specific anyways), and/or LDAP, Samba, phpmyadmin... Most of the times, the user wants phpmyadmin to be somewhere in the webroot at install... Not linking /usr/share/phpmyadmin to /var/www/phpmyadmin by hand :)

I would love to help on this (with code, even) - What I need is a well defined set of tasks we want to be scripting...

If you have ideas, let me know by PM, we can put something together pretty quick I'd guess (eventually centralising stuff on a wiki page).

Cheers

- Trib'

---

### Post by Donb01 on 2008-05-16
For those who need it, I answered one of my own questions above regarding IP while goofing around with the CD last night.  You can press <F6> for boot options, and then you can tell it to force the static configuration option rather than the DHCP option.  I don't remember the exact command, but you can press <F1> for help and it will list it under boot options for network.


Trib',

Thanks for the replies.  I do have some ideas if you have the coding ability.  I'll make a list and PM you.  One of them is that if you give your system a name such as "server1.example.com" and you are planning to run BIND, then there should/could be a way to automatically edit the named.conf file to make your server the master for domain 'example.com' and have an entry for where the domain zone file is.  Then go in to /var/named (or wherever it is nowadays) and create the 'example.com' domain file with a basic setup that has an NS, www, ftp, and mail entry all pointed at the server and an MX entry for 'mail' - the usual basic stuff, and create the reverse zone entry for 192.168.1, etc....

That would be one idea - a simplistic "out of the box" bind setup for the default domain the user provides.  Same thing could go for a generic Vhost for that domain in Apache, and some other stuff.  I'm not going to use ISPAdmin for that stuff (I've never seen it) - I prefer to do it by hand, but for a novice, a generic starting point would be very helpful.

---

