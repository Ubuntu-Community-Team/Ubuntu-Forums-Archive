---
title: "GUI on a server."
date: 2005-10-28
forum: Server Platforms
---

### Post by Terrik on 2005-10-28
Hey all,

I have heard a lot of people say GUIs and server installs don't go together. As much as I enjoy using the command line, I would never be able to use it 24/7 on my ubuntu server install, so I mix it with Gnome for functionality. I just wanted to know if having a GUI on a server is really as bad as many make it out to be, do Gnome and/or the x-window system have many potential security holes than can be exploited? Or is it something else totally different? Thanks.

---

### Post by Corvillus on 2005-10-28
I don't think it really matters that much (unless you are really paranoid about security), it's more an issue of performance...GNOME is resource hungry, and typically people running servers want to maximize their resources for the server applications.

---

### Post by ArukiRei on 2005-10-29
I would think, though I haven't done this myself, that most people who run server and would want to maximize resources would use a seperate computer with a GUI installed to remote connect to it. At least that's what I might do. ;)

---

### Post by dbee on 2005-10-29
The only reason I'd put a gui on a server is to run webmin + modules on it.

When you are starting, webmin is a great tool for you to poke around your server on.

When you know all the paths and functions by heart though, it kinda outlives it usefulness ... as does the GUI IMO.

Although unless you're rolling your own packages, it's tough to track down exactly where the .deb maker puts things for various packages ...

---

### Post by LordHunter317 on 2005-10-29
[QUOTE=Terrik]Hey all,

I have heard a lot of people say GUIs and server installs don't go together.[/quote]Anyone who's said this doesn't do any of the following:[list][*]Administer Windows[*]Administer Oracle[/list] 

> I just wanted to know if having a GUI on a server is really as bad as many make it out to be, do Gnome and/or the x-window system have many potential security holes than can be exploited?If you're giving out shell accounts, potentially.  I'm sure a malcious user could exploit X to cause no end of trouble, because X.org just isn't very secure. 
The lesson here is to trust local users, and not let malicious ones on in the first place.

[quote=Corvillus]it's more an issue of performance...GNOME is resource hungry, and typically people running servers want to maximize their resources for the server applications.[/quote]Unless you're actually using it, it effectively consumes no resources.

[quote=dbee]
Although unless you're rolling your own packages, it's tough to track down exactly where the .deb maker puts things for various packages ..[/quote]What are you talking about?  dpkg -L can list the files contained in any package.

---

### Post by dbee on 2005-10-29
Well LH on my computer 

dpkg -L

gives me ...

/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/apache2
/usr/share/doc/apache2/copyright
/usr/share/doc/apache2/changelog.Debian.gz

which points me in the direction of 

/usr/share/doc/apache2

which contains only some of the relevant information and then points me in the direction of

apache2.conf

which points me in the direction of 

httpd.conf 

and on and on and on ... anyway I've gone on about this before.

My point is that I'm sure this makes perfect sense to someone who is used to it, and if you are only ever going to use apache from an ubuntu .deb, it's probably excellent for reasons that I don't know about. But if you are new to the .deb ubuntu way of doing things then it gets complicated.

---

### Post by LordHunter317 on 2005-10-29
And?  I don't see a point in all of that.  IT told you every file in the package, just like it's supposed to.  What else would you have it do?

---

### Post by sas on 2005-10-29
We always have GUI stuff on too, we tend to export our display to our windows boxes (which run X) and just start individual programs up - e.g. volume manager, netbackup, maybe gnorpm.

---

### Post by Terrik on 2005-10-29
Ok, so it doesn't seem so bad. I'd love to one day be able to know the terminal screen like it nothing, but being a newbie it would take me forever to do stuff currently. I'll just learn to ween myself off Gnome over time. Plus I think Synaptic is the greatest program ever, I currently can't live without it.  

I understand a GUI might eat extra resources too, but for a simple web server for just messing around, I am sure Gnome won't be too much of a performance hog. Thanks all.

---

### Post by sailor420 on 2005-10-29
Yeah, dont worry about it. If you need the GUI, go for it. Like you said, you won't need perfectly tuned performance anyways. I ran a little webserver for a while on an old P2 400, and the load average almost never went above 0.00. Youll be fine :)

---

### Post by d1337 on 2005-10-29
It is possible to use a lighter weight GUI than full blown Ubuntu Desktop.  I followed directions from [the wiki]("https://wiki.ubuntu.com/Installation/LowMemorySystems?highlight=%28CategoryDocumentation%29") to install a minimal desktop on a Breezy Server install.  Slim on resource use.
d1337

---

### Post by JLTB on 2005-10-30
Hey,

The reason that some sysadmin's don't like GUI's (in my experience at least) is as follows:
  * Most big servers often need to be accessed remotely, and are generally not in the same office as you anyway.  A GUI is only useful in these cases when used over VNC (or some other RDP).  VNC is typically a big gaping security hole (yea yea, i know you can tunnel it etc..  but most people don't bother).  Also, VNC is bandwith expensive when compared to SSH or Telnet.
  * GUI's are to easy (seriously, it's a stupid reason ... but I really do know people who still talk like this).. :roll:
  * Servers need to be as lean and mean as possibe (... cause it makes admin's feel cool and smart?)
  * Probably others that I can't think up right now.

But seriously, all my servers that are in office I use a GUI on.  All my remote ones I don't bother to (mostly because of point 1).

---

### Post by sas on 2005-10-31
[QUOTE=JLTB]Hey,

  * Most big servers often need to be accessed remotely, and are generally not in the same office as you anyway.  A GUI is only useful in these cases when used over VNC (or some other RDP).  VNC is typically a big gaping security hole (yea yea, i know you can tunnel it etc..  but most people don't bother).  Also, VNC is bandwith expensive when compared to SSH or Telnet.
But seriously, all my servers that are in office I use a GUI on.  All my remote ones I don't bother to (mostly because of point 1).[/QUOTE]

We use remote X while we're in work to access our servers in the datacenters and if we're connecting from home we use terminal services to log into a windows box and run remote X from there. 

That way there's only one box which requires locking down.

---

### Post by jonzep on 2005-11-01
if you have physical access to the box and you're using it to experiment why not start with a gui and work your way towards a leaner install as you become more familiar with the cli...

---

### Post by hostile on 2005-11-01
> if you have physical access to the box and you're using it to experiment why not start with a gui and work your way towards a leaner install as you become more familiar with the cli...

I agree.

I have just come over from the RH world, and the CLI w/ rpm was confusing at first, as was the way RH dealth with inits. Now it's nothing for me - I'm still getting used to apt-get, dpkg...

My personal server at home is getting a bit long in the tooth (Mdk 9.2), and I want to re-arrange drives, so I just built a spanky new Ubuntu box. 

I chose the "server" install, then apt-got (?? past tense of apt-get ?? :D ) myself the GUI interface, then waded in and starting ripping out all the crap like evolution/games/CD player so I have a completely stripped down GUI other than Firefox, gftp, and the system admin stuff.

Since Ubuntu doesn't have all sorts of GUI tools to config daemons (like Mandrake), I think it will become rather useless in short order for me. Hell, I'm too lazy to wheel my chair across the room to my work desk where the new box is, so I'm ssh'd into it using apt-get from the CLI... *shrug* On today's hardware, running a GUI is all but meaningless in terms of resources. If I do a "top" on my new box here... it looks like it's using just under 100MB of RAM and no swap with 0.0% CPU... out of 1 GB of RAM... whatever... who cares?  :)

---

### Post by dbee on 2005-11-01
how did you go about ripping out all the games hostile ???

---

### Post by hostile on 2005-11-01
[quote=dbee]how did you go about ripping out all the games hostile ???[/quote]

Well... apart from just using apt-get at the cli, an easy GUI way to do it is to log into your GUI, then on the "Applications" menu, click on "Add Application", and uncheck anything you dont want in there. It will uninstall them for you.

---

