---
title: "Ok what are the must have packages"
date: 2005-04-23
forum: The Cafe
---

### Post by greenwom on 2005-04-23
So I installed warty and it was cool before I could tweak it I installed Hoary....

There a alot of problems I've run into trying to get this all working.

BTW this box isn't on the net yet... (getting online will probably solve everything)

1.) I need a complier, I download the "Build-essential" package and tried to get that going.  I'm a newbee and couldn't get it going.  I understand the APT-GET command goes out to the net and does it's thing but [COLOR=DarkRed]what if I'm offline and have a CD with the package? [/COLOR]

Without Build essential I can't get crap on this machine! right?

I'd like to know how to install these packages off-line.  At work I can't plug my laptop into network (illegal).  So.... Please shed some light on a Ubuntu SLUG

-----Long Live Jombe -------

---

### Post by nad on 2005-04-23
You don't need a compiler to installer deb packages.

Edit your /etc/apt/sources.list to include the packages on your cd (just uncomment the first line for your ubuntu cd) and issue ' apt-get update '. This will update the list of available packages. You can also do this in the synaptic gui. If you have other cds with deb packages (Linux Format mag, etc) add these locations to your sources.list and update.

Dan M

---

### Post by greenwom on 2005-04-23
Another Stupid new bee question.

Alot of the different packages I've looked at/ want to install have wanted me to edit
/etc/apt/sources.list   

The file sources.list.orgin is a root-owned file and I can't edit it from gnome with my lack of knowlegde :)

Now the stupid question(s)  
   :roll: I have [COLOR=DarkRed]etc/apt/sources.list.orig   [/COLOR] does that matter?  I ask because I've open some scripts and they point to sources.list 

  :-# Why can't I make and changes is Gnome to the etc/apt/ folder?  Actually anything not in the Home folder.  Is this a root issue?  I tries using the command line but I'm not yet familiar with the Linux commands.  

BTW can you point me to a good Linux command tutorial or online definitions list?

                                           ](*,)  ](*,)  ](*,)  ](*,)  ](*,)

---

### Post by greenwom on 2005-04-23
[QUOTE=nad]You don't need a compiler to installer deb packages.

Edit your /etc/apt/sources.list to include the packages on your cd (just uncomment the first line for your ubuntu cd) and issue ' apt-get update '. This will update the list of available packages. You can also do this in the synaptic gui. If you have other cds with deb packages (Linux Format mag, etc) add these locations to your sources.list and update.

Dan M[/QUOTE]
 I guess I should clarify.

I've downloaded packages and I've burned them to a blank CD.

When I edit the sources.list file what should I do besides uncommenting the first section?

I tried APT-GET UPDATE and that gave me an error (2 no such fille or directory)

At a loss :)  but willing

EDIT ---- BTW I figured out how to edit.. used gedit from root terminal.

---

### Post by TravisNewman on 2005-04-23
you can use sudo instead of the root terminal, but this produces the same effect.

You don't have any internet connection at all on this box, right? Well, the only thing you'll be able to use is the cd repository, so just be sure the first part about the cd is uncommented (no hash marks: #) and go to it. Be sure you have the Ubuntu CD in when you "apt-get update"

unfortunately, unless you have the structure of an apt repository, the packages won't get updated-- so the cd that you've used to download packages won't be "apt-get install"-able.  You'll have to do those manually with "dpkg -i packagename.deb" and/or compiling yourself. Unfortunately, if you've missed any dependencies you'll have to download them as well.

---

### Post by stilus on 2005-04-23
[QUOTE=greenwom]

Why can't I make and changes is Gnome to the etc/apt/ folder?  Actually anything not in the Home folder.  Is this a root issue?  I tries using the command line but I'm not yet familiar with the Linux commands.  
[/quote]
You cannot change (most) stuff outside your homefolder, because those files are not owned by you. It protects you (and other wanted and unwanted guests on your system) from making mistakes/ doing something bad, that would hurt the Operating System. If you are sure you really need to make changes at that level, you should use the root terminal.

[QUOTE=greenwom]

BTW can you point me to a good Linux command tutorial or online definitions list?

[/QUOTE]

 You might want to have a look at:

[http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)
(from [http://www.google.com/search?hl=en&q=linux+command+line+newbie+howto&btnG=Google+Search](http://www.google.com/search?hl=en&q=linux+command+line+newbie+howto&btnG=Google+Search))


the CLI (Command Line Interface) might look daunting, but its a very great tool to work with. Just pour yourself a drink, maybe get a pen and some sticky-notes so you can write down some commands until you've memorized them, and start trying. 
Take your time and enjoy! 

You might want to use file-browser and maybe gedit beforehand to create a directory and create/ copy-paste some test-files in it, so you know you can break stuff and get away with it. One important warning: the **rm** (remove) command is (as good as) permanent, so careful where you point that thing :)

Have fun!

---

### Post by greenwom on 2005-04-23
Ok, I'm loving Ubuntu but I have one gripe!@#$

Why isn't it distributed with these complier packages installed, they're essential to making everything work right? right?

Why not ship Ubuntu with this stuff on there and then have it disabled.

Make it a simple command to enable these packages with the install CD

Just a Newbee's thoughts 
(I'm sure when I get the box online (when I'm not at work) I'll stop being upset.

---

### Post by TravisNewman on 2005-04-23
Most people won't need to build software. That's the idea anyway. Nearly everything that you need is in universe. I'd still like to see it default myself, but it's no major issue.

---

### Post by UbuWu on 2005-04-23
Build essentials is on the installation cd. So no need to download it, it is on the cd, just not installed by default. I was wondering, as you say you are a newbie, why would you need a compiler? You should be able to install almost every program that exists for linux without ever compiling everything, as almost every program out there is in the ubuntu repositories.

---

### Post by UbuWu on 2005-04-23
A little more info:
If your cd is in the repositories list, you can just type 'sudo apt-get build-essentials' in a terminal window to install it (you don't need an internet connection for that).

---

### Post by greenwom on 2005-04-24
I'm trying to get a Wacom tablet (and a older one at that) working.

I'm following some instrustions I ripped off the web.  I've been pointed to the 
Wacom project and I've read some other tutorials.  So I'm trying to pull everything I need together....

I'll re burn the CD and ler you know.  My larget problem _I think_ is that 
I don't understand what each command is doing.  

APT-get for example, I've kind of come to understand that the command goes out and grabs aps/packages from the web and installs them and the command is goverened by other files that point it.  but I haven't read anything that lays it out for me yet,  But it is only my first monuth in Linux :)

I am happy that everything else works out of the box

I'm happy I have at least one thing that doesn't work so I can learn more. :grin:

---

### Post by defkewl on 2005-04-24
Ubuntu didn't include mysql. Huhu, :( And also libdvdcss2 :D

---

### Post by greenwom on 2005-04-24
OK!!!!!!!!!!!!!!!  WTH

I've popped the Ubuntu CD in, edited [COLOR=DarkRed]sources.list.orig[/COLOR], uncommented all of the deb lines so it reads like

[COLOR=Navy]## Uncoment the following......
deb [http://us.archive](http://us.archive).....
deb-src [http://us.archive](http://us.archive).....
deb /cdrom[/COLOR]


I run apt-get update and get 
E: Opening /etc/apt/sources.list - ifstream::ifstream (2 no such file or directory)

Do I need to rename sources.list.orig to sources.list?? (is this a real stupid question)

So now I'm lost.

---

### Post by UbuWu on 2005-04-24
There should be a sources.list. If not rename the sources.list.orig to it and try again.

---

### Post by poofyhairguy on 2005-04-25
[QUOTE=greenwom]
Do I need to rename sources.list.orig to sources.list?? (is this a real stupid question)

[/QUOTE]

Yes.

---

### Post by defkewl on 2005-04-25
[QUOTE=defkewl]Ubuntu didn't include mysql. Huhu, :( And also libdvdcss2 :D[/QUOTE]
 And apache2, php4, vsftpd, libdvdread3

---

### Post by UbuWu on 2005-04-25
[QUOTE=greenwom]
APT-get for example, I've kind of come to understand that the command goes out and grabs aps/packages from the web and installs them and the command is goverened by other files that point it.  but I haven't read anything that lays it out for me yet,  But it is only my first monuth in Linux :)
[/QUOTE]

You could read [this](http://www.newsforge.com/article.pl?sid=04/12/02/1710208) or you could just stick with synaptic which is fine most of the time.

---

