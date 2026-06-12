---
title: "Beginner Server questions"
date: 2006-11-28
forum: Server Platforms
---

### Post by campbuds on 2006-11-28
My boss asked me to do some research on using a Linux as our internet server instead of paying for web space. So all our web based stuff (ie. web page, streaming videos, audio downloads, email  etc...) would all be based off of a in house server.

Problem is I don't have a clue. I was wondering if someone would be willing to give me some direction here.

For starters... Is this even possible with ubuntu or any other linux version?

If so what all would be needed?

Thanks so much in advance! This is a difficult one for me.

---

### Post by Goldenmunky on 2006-11-28
Hey Camp,

Welcome to the world of Linux :)

Anyways to answer your question, yes Ubuntu can be used as a server but I would also recommend "Debian".

I have set a server at my own house (Mail server, DNS BIND, Web server) and it's working beautifully.

This linked helped me a lot actually: [http://www.howtoforge.com/](http://www.howtoforge.com/)

Here is a direct link on how to setup a Perfect Debian Sarge server for all your needs: [http://www.howtoforge.com/perfect_setup_debian_sarge](http://www.howtoforge.com/perfect_setup_debian_sarge)

And the same thing but for Ubuntu Edgy 6.10: [http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

Any questions just ask away :)

- GM

---

### Post by campbuds on 2006-11-29
No other questions for right now. First I would like to do some reading on the links you gave me. Then I will come back with questions.

Thanks for the quick response though! If anyone else would like to add to this I would appreciate it.

Also if someone lives in central PA and wouldn't mind giving some lessons in linux/servers I would be interested in that also.

---

### Post by az on 2006-11-29
[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

and

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by campbuds on 2006-12-05
I am really struggling with this. It is not very easy. I am using Debian, and using the Forge website for a how to and having a difficult time. Right now I am stuck at setting a static IP.

---

### Post by pmasiar on 2006-12-06
> **campbuds said:**
> My boss asked me to do some research on using a Linux as our internet server instead of paying for web space. So all our web based stuff (ie. web page, streaming videos, audio downloads, email  etc...) would all be based off of a in house server.

You are in for a lot of learning. If you have time for it (and you are paid for the time), it is great. If your boss wants to save money quickly, you may just want to change your web hosting provider. Because with self-hosting, all services you now pay for (and provider knows how to do) you are paid instead for your time doing it. 

And someone needs to pay for your time while you are learning it. 

Make sure your boss is ready for you crashing system couple times while learning. If something will go wrong (and it will, trust me), you are the one geting the blame. So be carefull, CYA. You may want to learn on non-production server first.

[https://www.nearlyfreespeech.net/](https://www.nearlyfreespeech.net/) was recommended to me as good one. Difference is, you pay only what you use, no montly fixed fees. When you learn the ropes, you can move hosting inhouse.

O'Reilly has interesting online course for Sysadmin: [http://www.oreillylearning.com/courses/sysadmin.php3](http://www.oreillylearning.com/courses/sysadmin.php3) I tried java course, but it was not good match (I am too advanced for stuff they teach), but I liked the way they run courses. Admin and web design are better match for the technology they have. Free 7 day trial, you have nothing to lose.

And of course you found some Linux user group or local gurus in your area, right? Some high school students are real good, will help you get started.

Good luck!

---

### Post by elst on 2006-12-06
> **pmasiar said:**
> You are in for a lot of learning. If you have time for it (and you are paid for the time), it is great. If your boss wants to save money quickly, you may just want to change your web hosting provider. Because with self-hosting, all services you now pay for (and provider knows how to do) you are paid instead for your time doing it. 

And someone needs to pay for your time while you are learning it. 

Make sure your boss is ready for you crashing system couple times while learning. If something will go wrong (and it will, trust me), you are the one geting the blame. So be carefull, CYA. You may want to learn on non-production server first.


I second this - it may well be a false economy to buy and run your own server without in-house knowledge or readily available support. In particular, email is more complex than most folks realise, and sufficiently important that any issues will go straight to you to be resolved.

The RUTE book is an excellent free overview of Linux administration, and matches the LPI curriculum - you can download  it from the Web site, or install the rutebook package and look in  /usr/share/doc/rutebook/html/index.html.

---

### Post by gregor171 on 2006-12-07
hi
why do u need a static ip, anny way it's better to put web server behind firewall. if you are a small company, here is one idea or how i've done it:
- static ip is provided from your web provider
- then set a router Lynksis WRT54G and get a firmware for it on [www.thibor.co.uk](www.thibor.co.uk)
- there you can set internal "static ip" to your box dependet on mac address (actually is dynamic, but you get the same addres)
- set port forwarding on router (ports you need for http, https, ftp, mail etc)
- now you you can set a server i suggest ubuntu server (install also kde if u are not fammiliar with text mode). partitioning is important, since u dont want to owerride some data every time u reinstall:one prat for swap, one for system, one for home (where u put copys of your config files)
- apache2 should cause no problems
- mail server i'm still working on ;-(
- after test period is important that your web provider sets yout domain data in their DNS. 
some also usefull webs:
[http://www.petri.co.il/configure_mx_records_for_incoming_smtp_email_traffic.htm]("http://www.petri.co.il/configure_mx_records_for_incoming_smtp_email_traffic.htm")
[http://www.spamhaus.org]("http://www.spamhaus.org")
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch21_:_Configuring_Linux_Mail_Servers](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch21_:_Configuring_Linux_Mail_Servers)
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch21_:_Configuring_Linux_Mail_Servers]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch21_:_Configuring_Linux_Mail_Servers")
[http://www.wireshark.org/]("http://www.wireshark.org/")
[www.dnsstuff.com]("www.dnsstuff.com")

PS: use some backup system!!

---

### Post by gregor171 on 2006-12-07
ftm I aggree with elst, it is in most casses to expensive for having it in house, or unsafe. your boss will have to pay someone and eventualy it's better he pays u

---

### Post by campbuds on 2006-12-22
I am not getting paid for this. It is for the church I am staffed at so many things happen there that are volunteer. Which is fine for me. Our pastor is a generous guy and I imagine he wants me to do it so he can offer me more hours and possible benefits.

In the mean time I need to figure this out. I appreciate all your input.

I have not found anyone close to me who really knows this stuff. Is there anyone in Central PA or more specifically York, PA who knows this stuff that I could connect with?

---

### Post by MrHorus on 2006-12-22
> **gregor171 said:**
> hi
why do u need a static ip, anny way it's better to put web server behind firewall. 

Because if you have a dynamic IP, every time it changes your DNS data will become invalid and your site will be inaccessabel, that's why.

What you plan on doing is very easy to set up although the trick comes in learning how to lock it down and secure it, how to troubleshoot etc.

At a bare minimum you will want to install Apache for your web server, MySQL/PHP for database-driven dynamic content (if needed) and then your mail solution of choice.

Personally I run a combination of procmail/exim4 on a Debian server and it should install the same way on Ubuntu since it's derived from Debian.

You will want to set up your DNS first and once it's operational, your web server and then your mail since you *WILL* experience difficulties recieveing email if you don't have proper DNS with reverse delegation.

---

### Post by campbuds on 2006-12-22
Ok, what operating system should I use?

I have ubuntu debian that only loads a basic system and leaves you with no gui when it boots. I also have ubuntu, but there is no option for installing a server when you start with the disk. In fact the only option from that disk is to run it from the disk and then install once you have a gui.

Am  I using the wrong versions for this? I would prefer to use the gui to do this but I really could use some direction on a more personal level. Maybe through instant messenger or something. Or maybe point me to a how to ont eh forge page that would be of more help.

thanks!

---

### Post by campbuds on 2006-12-22
AAAHHHH!!! This is getting frustrating. All I keep doing is messing up the system and having to reinstall and all I am doing is following directions to get these results!

---

### Post by PilotJLR on 2006-12-22
Take the problems one at a time, and you'll get this going!

Read this for starters... it's a howto for a server setup. This lists extra thing, like email serving, that you can skip:
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

I would recommend reinstalling from scratch, then take problems one at a time. When you reinstall the system, choose the "Install a LAMP Server" option.

Setting the static IP is easy... just let us know if your server is directly connected to a cable modem or DSL modem (this is not ideal), or if you are using a cable between the server and a router (like a little Linksys, DLink, etc).
Page 3 on the link I sent shows you how to assign a static address.


> **campbuds said:**
> AAAHHHH!!! This is getting frustrating. All I keep doing is messing up the system and having to reinstall and all I am doing is following directions to get these results!

---

### Post by campbuds on 2006-12-22
I am stuck on page 3 of these directions.

[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

---

### Post by PilotJLR on 2006-12-22
What you'll basically need to know if what address you'd like to change the server to... I'm going to make up a number for example purposes and say 192.168.1.100.
I'm also going to assume you are connected to a cable/DSL router, like a little blue Linksys box (or DLink or Netgear).

To make it a little easier, let's use nano (a text editor).
Type this:

```
sudo nano /etc/network/interfaces
```

Take the line that says:
```

auto eth0
iface eth0 inet dhcp

```

And replace it with:
```

auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

```

In order to make sure the addressing makes sense, I'd like for you to post the IP address of your router's local interface. This is basically an address you type in a browser to get to the router's config. An example would be 192.168.1.1. DLInk routers would use 192.168.0.1
These numbers are "private" IP addresses, so there is no real security concern.
If you are NOT using a router, please let us know...

Anyway - make these changes, then press Control + X to exit. Press Y when asked if you want to save the changes.

Reboot and you should be on the correct address. (there is a command that would allow you to not reboot, but rebooting is fine for now)

---

### Post by campbuds on 2006-12-22
I am hooked up to a router. It is a netgear and I don't remember what ip I enter to access it.

Right now I am stuck at the page where the directions on page 3 take you to. I don't know how to exit that.

I did get it to look like what the directions said to make it look like with a lot of fiddling with the keys since it only types what I want it to half the time. It is like the keys change what they are sometimes.

---

### Post by PilotJLR on 2006-12-22
> **campbuds said:**
> 
Right now I am stuck at the page where the directions on page 3 take you to. I don't know how to exit that.


Try pressing ESC, then type a Colon (Shift + Semicolon) then type "wq" and press Enter

---

### Post by campbuds on 2006-12-22
I don't know that I am getting any of this right.

---

### Post by campbuds on 2006-12-22
I don't know that I am getting any of this right.

Is there anyway I can do this in a gui format? This code and stuff is driving me nuts! I am a young guy that never really had to use DOS or anything.

---

### Post by campbuds on 2006-12-22
I am taking a break. I really need some more personal help with this.

---

### Post by Brazen on 2006-12-22
> **campbuds said:**
> I am taking a break. I really need some more personal help with this.

I sent you a PM, you goober.

---

### Post by envis on 2006-12-23
i found it extremely simple and quick (like 15 minutes when i took me a week and a half to set up the same thing on a windows xp)to set my own webserver running on my Unbuntu following this guide: [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) (check section 21.8)

the guide lets you see that the root of your webserver is at /var/www/ in your computer

to edit/create files in this folder i personaly launch a terminal on my Ubuntu Desktop, type in "sudo nautilus", put in my root password and manage everything inside of this file browser that is nautilus and i also use the default text editor of the OS (gedit) to edit the contents of the files

gedit is actually really great! i wish it was available for windows
its a simple text editor but has tabs and also knows a bunch of languages like PHP for example and will usually detect automatically what language you are writing in and apply colors to the code accordingly to help you detect potential syntax errors...

---

### Post by Littleweseth on 2006-12-24
campbud : to edit system files  in a nice friendly GUI editor, try running 'sudo gedit /file/you/want/to/open' from a terminal. The 'sudo' is necessary because you, as a mere mortal user, are not allowed to edit system files as yourself. The 'sudo' authenticates you as the superuser for one command, letting you do (nearly) anything.

To find your router's IP, find the IP of the computer you're sitting at (connected to the router) and replace the last number with a 1. If your computer is, for example, 192.168.2.55, try [http://192.168.2.1](http://192.168.2.1) in a web browser. In most cases this will turn out to be the right IP.

You can find your own ip by typing 'ifconfig' at a terminal and looking for the 'net addr' listed under interface eth0 or eth1 - note that it is not '127.0.0.1', listed under interface 'lo'. 127.0.0.1 is a special one called the local loopback.

> I did get it to look like what the directions said to make it look like with a lot of fiddling with the keys since it only types what I want it to half the time. It is like the keys change what they are sometimes.

Welcome to the wonderful world of vi, the modal text editor. The keys *do* change what they are depending on what mode you're in (feel like screaming yet?). Save your sanity and use nano for editing text files instead. Really. Vi is notable for two things - how efficient experienced users are with it, and how new users are unable to use it at all - it's not unknown for people to reboot computers because they can't figure out how to quit vi.

In passing, it's notable that if you spend any significant amount of time around a linux server, you're going to have to learn to drive a terminal. It's not hard, especially if just following instructions, which incidentally is one of the better ways to be introduced to termnal commands.

---

