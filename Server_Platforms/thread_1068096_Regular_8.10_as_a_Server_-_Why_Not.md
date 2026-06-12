---
title: "Regular 8.10 as a Server - Why Not?"
date: 2009-02-12
forum: Server Platforms
---

### Post by mistypotato on 2009-02-12
Would using regular Ubuntu as a server be a problem?

If so ....WHY?

I thought ubuntu Linux was "secure" ?

I need a non-windows server but I also NEED a GUI.

I can't handle the command line stuff (especially right now).


What do you think ?

thx

---

### Post by Go_Big_Blue on 2009-02-12
You might try Fedora.  I started out setting up Ubuntu 8.04, and learned the command line pretty quick.  Then I was convinced to switch to Fedora, but then I switched back because I liked the command line so much.  I just find it's faster to set things up.

However, if you don't feel comfortable or want to learn the command line, I would recommend Fedora.

There are some good tutorials out there that will walk you through setting up a quick server, depending on the type you want to setup.  Here are links to a few of them:
[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)
[http://www.howtoforge.com/running-a-file-and-print-server-with-ebox-on-ubuntu8.04-server](http://www.howtoforge.com/running-a-file-and-print-server-with-ebox-on-ubuntu8.04-server)
[http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server](http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server)
[http://www.howtoforge.com/perfect-server-fedora-10](http://www.howtoforge.com/perfect-server-fedora-10)

Good luck - hope you have fun and success with it. :D

---

### Post by mistypotato on 2009-02-12
Is there a list somewhere of all the command line commands and what they do?

---

### Post by Go_Big_Blue on 2009-02-12
> **mistypotato said:**
> Is there a list somewhere of all the command line commands and what they do?

There are a couple of other tutorials that give a better description, such as 

[http://lani78.wordpress.com/2008/08/09/setting-up-a-dns-for-the-local-network/](http://lani78.wordpress.com/2008/08/09/setting-up-a-dns-for-the-local-network/)
[http://www.zaphu.com/2007/09/10/ubuntu-dns-server-guide-bind-caching-name-server-setup/](http://www.zaphu.com/2007/09/10/ubuntu-dns-server-guide-bind-caching-name-server-setup/)
[http://www.zaphu.com/2007/09/14/ubuntu-dns-server-guide-bind-master-server-setup/](http://www.zaphu.com/2007/09/14/ubuntu-dns-server-guide-bind-master-server-setup/)

And, believe it or not, I have learned quite a bit from the Ubuntu online documentation (for the server)
[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

The command line is not as scary as you think, it just takes a little bit of time to learn the ins and outs of it.:guitar:

---

### Post by Thirtysixway on 2009-02-12
You can use the desktop version as a server if you want to.  Just install the packages used in server like samba, apache, php, mysql, etc

---

### Post by mistypotato on 2009-02-12
Thats esentially what I did with WindowsXP Pro for the last 4 or 5 years.
But it's time to move away from Windows.

---

### Post by windependence on 2009-02-12
When in a terminal, if you need info on a command, type 

```
man <command>
```

(without the <>)

And you will get the man page for the command.

Also, sounds simple but google is your friend here.

You can most certainly use the desktop version for a home server, and IMHO, many people here on the server forum should really do just that as they really aren't running what the server product was intended for. There is nothing wrong with that. You don't need a full blown server package to run a torrent box.

-Tim

---

### Post by faustcoder on 2009-02-12
I find you need to force yourself to use the command line. It can be intimidating at first but once you give it a chance you'll enjoy the simplicity. There are tons of Ubuntu server books/guides/sites. I recommend "Pro Ubuntu Server Administration" by Sander van Vugt. It is a good introduction. Also just play around in a virtual machine and don't worry about messing up. Mistakes are part of learning. I'm going on 5 years of using Linux and still have to google for simple items. Good luck!

---

### Post by mistypotato on 2009-02-12
Thanks everyone.

Right now I dont have the terminal available.

I ONLY have a command line because I'm running 8.10 SERVER  :confused:

---

### Post by Iowan on 2009-02-12
> **mistypotato said:**
> Thanks everyone.

Right now I dont have the [COLOR="Red"]terminal[/COLOR] available.

I ONLY have a [COLOR="Red"]command line[/COLOR] because I'm running 8.10 SERVER  :confused: Kinda the same thing in my book - although a purist might argue otherwise.

---

### Post by Go_Big_Blue on 2009-02-12
> **mistypotato said:**
> Thanks everyone.

Right now I dont have the terminal available.

I ONLY have a command line because I'm running 8.10 SERVER  :confused:

Well, since you are at the command line, and I presume logged in as the administrator or root, then you can execute the following:
```

sudo apt-get install ubuntu-desktop gdm

```

That will load the desktop so you can use the GUI and still have the server run your server functions.
BTW - may want to google how to load the desktop.  I believe that is the correct command line, but you may want to check.

---

### Post by beatgr on 2009-02-15
IF you are running Ubuntu Server 8.10 and desire a GUI instead of the command line, this command line will install Ubuntu's default desktop environment (Gnome).
> 
sudo apt-get install ubuntu-desktop  

IF you desire KDE, I think this is the proper command line (I don't use KDE)
> 
sudo apt-get install kde


The standard Gnome desktop installation (on Server 8.10) took about 20 minutes for my older Dell PowerEdge server.

Good luck!

---

### Post by beatgr on 2009-02-15
> Is there a list somewhere of all the command line commands and what they do?
Mistypotato -

Based on you command line experience, I would highly recommend the "How To" guides (Ubuntu and others) for basic setups of server functions. 
Here is Sam Davis' Ubuntu list:
[http://www.zaphu.com/category/ubuntu/](http://www.zaphu.com/category/ubuntu/)

[http://lani78.wordpress.com/2008/08/09/setting-up-a-dns-for-the-local-network/](http://lani78.wordpress.com/2008/08/09/setting-up-a-dns-for-the-local-network/)

There are also various tools (GUI/HTTP based or SSH command line) for administration of the server and its apps remotely (elsewhere on your home LAN on a Mac or PC). *You should get use to remote server adminsitration -- not at "server console" -- it will serve you well in future.)*

g. beat

---

