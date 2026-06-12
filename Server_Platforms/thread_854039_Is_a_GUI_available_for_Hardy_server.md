---
title: "Is a GUI available for Hardy server ?"
date: 2008-07-09
forum: Server Platforms
---

### Post by Julian David Pitt on 2008-07-09
Just experimenting with Hardy server and being fairly new to Linux I would much rather have the ability to tweak the server setup with a GUI as I have very little knowledge of the command line. Is it possible to install server with a GUI please?

---

### Post by Martje_001 on 2008-07-09
Yes,
```
sudo apt-get install ubuntu-desktop
```
Good luck ;)

---

### Post by windependence on 2008-07-09
> [SIZE="5"]**No X server by design**[/SIZE]


By design, Ubuntu Server Edition does not include an X server. This is a deliberate choice as we believe that most servers should be serviced remotely, are safer without the addition of code that needs direct communication from user space to hardware, and should not be used as a desktop by their administrator. 

[I]"So I applaud the Ubuntu team’s common sense (and courage) in keeping the X Window System out of the default installation of Ubuntu Server."
--Mick Bauer in April 2008 Linux Journal - "Security Features in Ubuntu Server" [/I]

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security)

You would do well to learn some command line. It's noting to be scared of and very very powerful and quick. Almost all Linux configuration is done in plain text files, so a GUI is not necessary, uses unnecessary resources, and opens up security holes in your server.

From a practical sense, it's a crutch. I know. I have been there, and got the T-shirt. :) I had to actually force myself to learn REAL server admin after having been spoiled by a GUI for years. Whe crap hits the fan and your server is down and the pretty GUI isn't there, you'll thank me over and over again.

-Tim

---

### Post by Julian David Pitt on 2008-07-09
Many thanks for that, I understand the reasons for it now and I did not realise it was so easy to install the gui. Do you know if it is on the install cd as I currently do not have a network connection, thanks again.

---

### Post by comandrei on 2008-07-09
There's no GUI on the server CD. You should download a Desktop or alternate CD and add it to the /etc/apt/sources.list

---

### Post by netztier on 2008-07-09
> **Julian David Pitt said:**
> Just experimenting with Hardy server and being fairly new to Linux I would much rather have the ability to tweak the server setup with a GUI as I have very little knowledge of the command line. Is it possible to install server with a GUI please?

You *technically* can install the ubuntu-desktop, xubuntu-desktop or another desktop environment package on a server installation:

```
sudo aptitude install ubuntu-desktop
```

This will install a considerable amount of packages, the X.org windowing system, you may run into issues with having a VGA adapter not properly supported, the whole shebang as you know it from setting up a desktop version of Ubuntu. Plus this will drag things along that you definitely won't need on a server, like network-manager.

**My advice: don't.** Rather start here: [https://help.ubuntu.com/8.04/serverguide/C/](https://help.ubuntu.com/8.04/serverguide/C/)

By their design nature, servers of the unixoid flavour are made to be run headless, without a graphics card (at least not in graphical mode, but text-only), without the X.org environment running. 

They are configured by editing their configuration files (which you still can do from your GUI workstation with the text editor of your choice), see: [http://ubuntuforums.org/showthread.php?t=853847](http://ubuntuforums.org/showthread.php?t=853847)

You might consider **webmin**, which offers a web based GUI to most of the common server software you might find on a Linux server.

To put it very bluntly:

*"Wanna run Ubuntu server? Gotta learn command line!"*

Tough as it may seem - that's very much the way it still is today. And hey - if ever you touched, loved or hated MS-DOS, you'll be amazed what *this* command line is capable of!

And if you remember the good old Norton Commander from the MS-DOS age, you'll find a mighty tool named **Midnight Commander**, ```
sudo aptitude install mc
``` which is a close-to-perfect clone of th venerable Norton Commander. It gives you a two-pane navigation view of your file system, to shove files and directories around and view/edit them right there - and since it's console-based you can do it also from remote via an SSH session - all while avoiding  the kludgy (and potentially sluggish) remote-desktop issues with VNC, NX and the likes. I for one can't actually live without mc on my servers.

regards

Marc

---

### Post by jrb99 on 2008-08-23
I am in a similar situation of being really new with Linux. Reading all the comments about using server without a GUI I understand the reasoning but for me I need to get a file server up and running quickly. Fortunately for me work gave me two "old" servers, old for Windows but really speedy for Ubuntu server. One has a normal server install as a command line server and the second one I added a stripped down GUI just to help get it up and running quickly.  Eventually both will be command line. If you really need a GUI take a look at this URL vs loading the entire GUI which is fat with a lot of applications you probably don't need. This one will run faster then loading the entire desktop.

[http://www.swedcore.net/?p=31](http://www.swedcore.net/?p=31)

Jim

---

### Post by SunnyRabbiera on 2008-08-23
its more the possible to get something like gnome working in a server, sure it will slow things down but it will give you a GUI.
You can get gnome via apt if needed.

---

### Post by hyper_ch on 2008-08-23
and how does a gui help you setting up a file server?

also have a read at [http://www.howtoforge.com](http://www.howtoforge.com)

---

### Post by mbeach on 2008-08-23
one of these 'is there a gui for server' should be a sticky.

---

### Post by windependence on 2008-08-23
I think that other big thread where we have the debate would be a good one ;)

-Tim

---

### Post by mellowd on 2008-08-24
I agree with most here.

It'll be a bit difficult in the beginning, but you'll learn a heck of a lot more this way.

---

### Post by mansonthomas on 2008-08-24
Hi, 

I'm quite interested for a GUI on a server, but not for the same reason. I manage several server from command line only since several years. In fact I quite don't known desktop linux.

My server,  I want it multi purpose.
My current server is dying (and the other is already dead)

My next server would hold a windows 2003 server in a VMWare (I know I don't need X for this)

And also, the motherboard offer a HDMI interface, so I'd like to make it a HTPC (Home Theater PC).


So GUI on server would be nice.

Why would it be more difficult to configure X from a server install that a desktop install ? 

does "apt-get install ubuntu-desktop" suck ?

How do you choose which flavor of desktop you install ? 


Regards,
Thomas

---

### Post by CarlosNYB on 2008-08-24
I'm not familiar with the difference between aptitude and apt, but I heard mention here before of using aptitude to get desktop packages, something about aptitude being good for later removing those packages if you don't want them later on...

As for different desktops  you can just change the ubuntu part of the command line to xubuntu or kbuntu, for example, if you want a different desktop package... or there's other threads on installing x and then a wm like fluxbox or openbox, etc., from the command line and configuring them.

---

### Post by Benismyhorse on 2008-08-25
Just saying that I am 15 Years old and have been using ubuntu for around 4 months and I am all ready running _All_ my servers without a gui.

My 5 cents :lolflag:

---

### Post by kreawit on 2008-11-05
> **netztier said:**
> You *technically* can install the ubuntu-desktop, xubuntu-desktop or another desktop environment package on a server installation:

```
sudo aptitude install ubuntu-desktop
```

...

To put it very bluntly:

*"Wanna run Ubuntu server? Gotta learn command line!"*


Well, CLI only are not a good answer. My self, an experienced Unix administrator since late 1970, don't have any problems using bash. But my customers SME (Small to medium sized enterprises) with none or a very small IT-department are not confortable with a CLI for daily tasks. They need a simple remote administration possibility with a minimum of learning curve. 

Eg apt-get ubuntu-desktop[-minimal]  + NX, VNC or ssh -X

Since Hardy 8.04 there are problems with Policykit / Consolekit (?)  that makes it impossible to use the standard Gnome administration applications remote. Does anyone know howto configure Hardy for GUI remote administration?

Yes we need a ubuntu-desktop-minimal package for a minimal GUI-installation. [https://blueprints.edge.launchpad.net/ubuntu/+spec/ubuntu-desktop-minimal](https://blueprints.edge.launchpad.net/ubuntu/+spec/ubuntu-desktop-minimal) and [http://brainstorm.ubuntu.com/idea/1653/](http://brainstorm.ubuntu.com/idea/1653/)

---

### Post by hyper_ch on 2008-11-05
better to run webmin and have administration through a webinterface than running a gui all the time... it's just a waste of resources.

---

### Post by netztier on 2008-11-05
> **kreawit said:**
> They need a simple remote administration possibility with a minimum of learning curve. 


Well in that case, I'd stick with my suggestion to use Webmin, eBox et al. Also see the ServerGuide: [https://help.ubuntu.com/8.04/serverguide/C/remote-administration.html](https://help.ubuntu.com/8.04/serverguide/C/remote-administration.html)

Their main advantage is that they're remotely accessible via Browser, without NX, VNC, X-forwarding-over-SSH or other difficult "remote desktop" setups that can be as cumbersome as running a GUI. I know - the Web-GUIs have their own issues, mainly with tool/plugin integration...


regards

Marc

---

### Post by lykwydchykyn on 2008-11-05
Making blanket statements about GUI's on servers is silly.  There are situations where it can be an asset, and some situations where it's required (LTSP doesn't do much for you without a desktop for clients to remote into).

As far as wasting resources... if and idle instance of xorg and some minimal wm/de are going to put a significant dent in your server's resources, it may not be the right piece of gear to use as a server.

Do I use GUI's on all my servers? No.  But if someone wants to know how to put a GUI on their server -- if they'd rather edit config files in gedit than vim; if they'd rather use xterm than a tty; if they want to manage files with nautilus than cp/mv/ls/rm -- why the heck not?

---

### Post by hyper_ch on 2008-11-05
> **lykwydchykyn said:**
> As far as wasting resources... if and idle instance of xorg and some minimal wm/de are going to put a significant dent in your server's resources, it may not be the right piece of gear to use as a server.
yet on high traffic servers it can make the difference... also more things added to a server leads to a more complex system and more complex system are more prone to failure because of something... that's not what you aim for in a server.

---

### Post by bangeko on 2008-11-10
Try apt-get install webmin.
[http://hostname:10000](http://hostname:10000)

---

### Post by jonny.milano on 2008-11-10
> **bangeko said:**
> Try apt-get install webmin.
[http://hostname:10000](http://hostname:10000)

YES! it is a much better (and much more secure!) 

btw, does anyone know if one could install a very very very small xfce onto an ubuntu installation? i'm talking very basic without all the apps that come with xubuntu-desktop. THANKS!

---

### Post by scottuss on 2008-11-13
Webmin really is great, it can do all of the things you would want to do from configuring your firewall to SSH and everything else. It has a front end for APT too so you can install and remove packages (I still prefer to ssh in and use apt-get) but anyway I would definitely recommend Webmin. :guitar:

---

### Post by qwavel on 2008-11-20
> **mbeach said:**
> one of these 'is there a gui for server' should be a sticky.

Agreed.  

And I hope the sticky includes instructions on how to install a minimal desktop.

Normally Ubuntu Server should not be used with a GUI, but there are some circumstances in which users will want a GUI.

---

