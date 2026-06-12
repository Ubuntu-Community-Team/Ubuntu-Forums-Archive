---
title: "How is a simple server made?"
date: 2009-07-13
forum: Server Platforms
---

### Post by UbuKunubi on 2009-07-13
Hello!

While I have experience of using Jaunty, I have an older machine (Dell iMedia 850MHz with 256 MB ram), that I would like to host my own web site.

I've looked at a lot of links from google, but they all seem to jump in with advice which is past my current level of knowledge.

Given the hardware available I guess I'll be using 8.04 LTS, but Im not sure if I should use the server edition or the desktop (I expect a low level of traffic), and from that decision, how do I actually go about setting it up as a basic server?

I guess i'm asking for a little 'hand-holding' while I learn these ropes, but even a little advice will/is highly appreciated.

Many thanks,
Ubu

---

### Post by irv on 2009-07-13
You can install a desktop Ubuntu on a computer and then install LAMP.
(Linux,Apache,MySQL,PHP)
Here is a link on how to install and configure a Web server.
[http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100]("http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100") 
This will get you started.

---

### Post by UbuKunubi on 2009-07-13
> **irv said:**
> You can install a desktop Ubuntu on a computer and then install LAMP.
(Linux,Apache,MySQL,PHP)
Here is a link on how to install and configure a Web server.
[http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100]("http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100") 
This will get you started.

Thank you!

That is just what I needed.

All the best,
Ubu

---

### Post by HermanAB on 2009-07-13
Simple server?  Just use regular Ubuntu and install whatever server functions you want.  You can relatively easily configure stuff with the wizards provided by Webmin.

---

### Post by UbuKunubi on 2009-07-13
> **HermanAB said:**
> Simple server?  Just use regular Ubuntu and install whatever server functions you want.  You can relatively easily configure stuff with the wizards provided by Webmin.

Thanks for your time Herman.

The link to your site is VERY informative and useful.
All the best,
Ubu

---

### Post by jeffathehutt on 2009-07-13
The official documentation at [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) might also provide some tips if you get stuck along the way.

---

### Post by jimv on 2009-07-13
Just an FYI, don't think of a server as a special machine.  A server is simply a computer that runs any program that "serves" data.  So essentially, if you want a web server, you just need to install a program like Apache.

---

### Post by ddrichardson on 2009-07-13
> **jeffathehutt said:**
> The official documentation at [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) might also provide some tips if you get stuck along the way.
Thats actually the community documentation, the official server guide is available here: [http://doc.ubuntu.com/ubuntu/serverguide/C/index.html](http://doc.ubuntu.com/ubuntu/serverguide/C/index.html) there's a lot of stuff in it and Adam is always updating it.

---

### Post by jeffathehutt on 2009-07-13
> **ddrichardson said:**
> Thats actually the community documentation, the official server guide is available here: [http://doc.ubuntu.com/ubuntu/serverguide/C/index.html](http://doc.ubuntu.com/ubuntu/serverguide/C/index.html) there's a lot of stuff in it and Adam is always updating it.

Oops, I guess I should have read that big banner at the top of the page I linked. :)  My mistake...

---

### Post by ddrichardson on 2009-07-13
> **jeffathehutt said:**
> Oops, I guess I should have read that big banner at the top of the page I linked. :)  My mistake...
I shouldn't worry, we can never seem to explain the different sites. No matter how much we try, people try to add howtos to the team wiki site (wiki.ubuntu.com) and not the community site (help.ubuntu.com/community).

I only mention it because the server guide team work very hard at it and get a lot of "I'm cross fix it now grrrr" type bugs and never complain.  It also builds as a PDF quite well, better than most of the official chapters.

---

### Post by UbuKunubi on 2009-07-13
Thanks for all the input!

Its appreciated. If anyone has actually done this then I'd be very interested to hear from someone who has already done this from a 'newbie' perspective. 
I have a good grasp of programming, and this is an entirely new avenue to me, so any words of wisdom are welcome.

Cheers,
Ubu

---

### Post by irv on 2009-07-13
> **UbuKunubi said:**
> Thanks for all the input!

Its appreciated. If anyone has actually done this then I'd be very interested to hear from someone who has already done this from a 'newbie' perspective. 
I have a good grasp of programming, and this is an entirely new avenue to me, so any words of wisdom are welcome.

Cheers,
Ubu

Even from a newbie's standpoint, all you need to do is install Ubuntu desktop on a pc and follow the instruction in this link I gave you
[http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100]("http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100")
My hard drive crashed last week and I had to install a fresh install and followed the steps in this link, re-installed my back up and I was up and running. Yesterday I did a complete backup of my server and if this happens again I will just restore the complete system as it is today. Then the only thing I will need to do is update my data if it changes.
I think we have given you enough information to setup a server.

---

### Post by UbuKunubi on 2009-07-13
> **irv said:**
> Even from a newbie's standpoint, all you need to do is install Ubuntu desktop on a pc and follow the instruction in this link I gave you
[http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100]("http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100")
My hard drive crashed last week and I had to install a fresh install and followed the steps in this link, re-installed my back up and I was up and running. Yesterday I did a complete backup of my server and if this happens again I will just restore the complete system as it is today. Then the only thing I will need to do is update my data if it changes.
I think we have given you enough information to setup a server.

Yes - you've given me ample information, and Im very grateful.
Its reassuring to know that backups work as intended,because as we all know the unplanned will occur!

Thanks again,
Ubu

---

### Post by dragos2 on 2009-07-14
> **UbuKunubi said:**
> Hello!

While I have experience of using Jaunty, I have an older machine (Dell iMedia 850MHz with 256 MB ram), that I would like to host my own web site.

I've looked at a lot of links from google, but they all seem to jump in with advice which is past my current level of knowledge.

Given the hardware available I guess I'll be using 8.04 LTS, but Im not sure if I should use the server edition or the desktop (I expect a low level of traffic), and from that decision, how do I actually go about setting it up as a basic server?

I guess i'm asking for a little 'hand-holding' while I learn these ropes, but even a little advice will/is highly appreciated.

Many thanks,
Ubu

Server edition is for servers, and desktop edition is for desktops.

Are you afraid of the fact that the server editions lacks graphical configuration ?
Don't! As more apps running on your server as many potential problems!

---

### Post by windependence on 2009-07-14
I doubt seriously if you will need PHP and MySQL. many n00bs (and some experienced folks) on this site really have no idea what either one of them does so they keep saying LAMP, LAMP, LAMP without knowing anything about LAMP because they heard it from someone they think is experienced and it's "cool" Same with RAID. 

If you just want to put up a few static pages, all you need is Apache. Pure and simple. You can do this with the desktop edition, but if you are serious about learning, like Dragos said, take some time to learn the command line and you'll be glad you did, especially if you are thinking about doing anything professional in the future.

-Tim

---

### Post by dragos2 on 2009-07-14
> **windependence said:**
> I doubt seriously if you will need PHP and MySQL. many n00bs (and some experienced folks) on this site really have no idea what either one of them does so they keep saying LAMP, LAMP, LAMP without knowing anything about LAMP because they heard it from someone they think is experienced and it's "cool" Same with RAID. 

If you just want to put up a few static pages, all you need is Apache. Pure and simple. You can do this with the desktop edition, but if you are serious about learning, like Dragos said, take some time to learn the command line and you'll be glad you did, especially if you are thinking about doing anything professional in the future.

-Tim

Well said :)

Also lighttpd, nginx and others does a pretty light job for busy sites.

---

### Post by irv on 2009-07-14
> **windependence said:**
> I doubt seriously if you will need PHP and MySQL. many n00bs (and some experienced folks) on this site really have no idea what either one of them does so they keep saying LAMP, LAMP, LAMP without knowing anything about LAMP because they heard it from someone they think is experienced and it's "cool" Same with RAID. 

If you just want to put up a few static pages, all you need is Apache. Pure and simple. You can do this with the desktop edition, but if you are serious about learning, like Dragos said, take some time to learn the command line and you'll be glad you did, especially if you are thinking about doing anything professional in the future.

-Tim
Well said Tim, but people do things for different reasons. In my case I am 70 and don't look to getting back to IT work in my future, but While I was in the workforce I managed servers, but they were Novell and Windows. I did some work on a RS6000 and did everything at the command line. Novell had it's menus etc, but not a gooie interface. I agree the best way to go is a server install, but at my age it is much easier to do it graphically so I don't have to remember all the commands. I keep a file of them when I do need them, because there are time that the only way out of trouble is at a command line. I guess the saying is right; different strokes for different folks!
One more point, It is nice to have a desktop on my server, because when my grandkids come over, I let them play on my server, but they are locked out of su user so they can't hurt it. It serves a dual purpose.

---

### Post by UbuKunubi on 2009-07-14
I now have the hardware set up, and have installed the server edition of 8.04 LTS (32 bit), taking guidance from [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

I am now at the stage where I need to configure the network, and change the DHCP setting to a static IP address.

On the server I ran the command 'dhclient eth0', and have presented with a list of data, such as hex addresses where LPF is listening and sending, and also 'normal' decimal format addresses of DHCPDISCOVER/OFFER and REQUEST.

which one of these should be entered into etc/network/interfaces?

---

### Post by spynappels on 2009-07-15
Do you just want to set it up with a static Local IP? Then you do not need to worry about any of that. In the terminal, enter:

```
sudo nano /etc/network/interfaces
```

you can use any editor, I just tend to work in nano

Add the following lines

```
auto ethX  
iface ethX inet static
address: 192.168.x.x
netmask: 255.255.255.0
gateway: 192.168.1.1
```

replacing the X in ethX with the correct adapter number, normally 0, and the ip address with the required local static IP, and save. You will also need to add your dns server ips to the resolv.conf file. To do this, enter:

```
sudo nano /etc/resolv.conf
```

Add the following lines

```
nameserver 192.168.1.1
nameserver 4.2.2.1
```

or whatever DNS servers you have been given by your ISP.

This will give you a static local IP address for your server, just make sure it is not in the DHCP scope given by your router to avoid conflicts.

---

### Post by UbuKunubi on 2009-07-15
spynappels,
Thank you for your post.

When (on the server) I type sudo dhclient eth0 I get the following information:

DHCPDISCOVER on eth0 to 255.255.255.255
DHCPOFFER of 192.168.1.12
DHCPREQUEST of 192.168.1.12
DHCPACK of 192.168.1.12 from 192.168.1.1
bound to 192.168.1.12

Which of these should be entered against address,netmask, and gateway?
Also, how do I discover the DNS servers I have been given by my ISP?

Thanks in advance,
Ubu

---

### Post by benh13 on 2009-07-15
install LAMP. i found this website really useful for installing apache, php and mysql: [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)
thanks

---

### Post by UbuKunubi on 2009-07-15
> **benh13 said:**
> install LAMP. i found this website really useful for installing apache, php and mysql: [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)
thanks

Thanks for your input, but until I can get the server setup correctly to host my website I see little point in installing apache yet!

It seems I have to hurdle the 'change from dynamic to static IP' issue first, and then yes I'll follow the advice on the page you pointed me to.

Cheers,
Ubu

---

### Post by windependence on 2009-07-16
To set your static IP:

```
sudo nano /etc/network/interfaces
```For the primary interface, which is usually eth0, you will see these lines:
 ```
auto eth0
iface eth0 inet dhcp
```Change the file like this. Obviously you’d customize this to your network.

```
auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```There's one more thing you need to do then, set up your DNS:

```
sudo nano /etc/resolv.conf
```Then make it look like this:

```
nameserver  208.67.222.222 
nameserver  208.67.220.220
nameserver  4.2.2.2
```Here, you can use your ISP's nameservers or these from OpenDNS, and the 4.2.2.2 is a DNS server on the main backbone of the internet. It's generally very fast.

You need to also remove the dhcp client for this to stick:
```
sudo apt-get remove dhcp-client

```If you get an error, you may have to remove version 3 of the DHCP client:
```
sudo apt-get remove dhcp-client3
```After you're all finished, you'll need to restart the network:
```
sudo /etc/init.d/networking restart
```After that, try to ping something like google.com to make sure everything is working and if successful you are finished. 

When you get your IP set, I'll explain how to install Apache. You probably DON'T need LAMP.

-Tim

---

### Post by irv on 2009-07-16
If you are interested I put a post on the forum today about how to host your webpages on your own server. A kind a how I did it.
Here is the link: [http://ubuntuforums.org/showthread.php?p=7624912#post7624912]("http://ubuntuforums.org/showthread.php?p=7624912#post7624912")

---

### Post by UbuKunubi on 2009-07-16
Many thanks for the efforts - its really is highly appreciated.

I DID discover, in the small hours, that my problem was as simple as forgetting to enable port-forwarding on one of the routers here.... live and learn.

All the best,
Ubu

---

