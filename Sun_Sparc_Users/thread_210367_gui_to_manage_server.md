---
title: "gui to manage server???"
date: 2006-07-06
forum: Sun Sparc Users
---

### Post by jpgeerets on 2006-07-06
someone know if it is possible to put a gui on the server?
a friend of mine would also like to start using this, but he doesnt know how to handle the server by clui. 
he normaly used a gui (windowsxp/2003).

im looking for a gui to manage the server. (de-)install software, add users, ad functionality. on desktop systems you can use synaptic for package install, something like on the server?

thanks in advance!!!

Jean-Paul

---

### Post by chris_andrew on 2006-07-06
Jean-Paul,

Can you do:

*apt-get install kde* (for example?)

Cheers,

Chris.

---

### Post by jpgeerets on 2006-07-07
kde will also work on the server?
hmm,
great, i will try that!
if it does, i can make him happy and... we have a new linux user.... :cool:

---

### Post by netztier on 2006-07-07
> **jpgeerets said:**
> kde will also work on the server?
hmm,
great, i will try that!
if it does, i can make him happy and... we have a new linux user.... :cool:

I've even been running **Xubuntu** on my old Sun Ultra 2 with some success (*server install* from CD, then **aptitude install xubuntu-desktop**) . The machine was so low-spec (128MB RAM, 2x 167MHz) that it didn't make any real sense, though. That was back in the 6.06-beta days, and there were some issues with running Firefox, for example. 

I haven't touched that machine since (well, there's more interesting "things" to touch in life than Sun Ultra machines ;) ) so at present I can't tell if 6.06 with Xubuntu-desktop runs well on SPARC machines.

Xubuntu is "more lightweight" than KDE or GNOME, and therefore might be the wiser choice.

Another thing to consider: Ubuntu 6.06 for SPARC comes with a "server-optimized" kernel image; using it as a desktop might have some issues - choosing another kernel image (if available, I can't verify at this time) might be advisable.

kind regards

Marc.

---

### Post by the slayer on 2006-07-07
Use webmin!
Dont use a DE on a server!

---

### Post by jpgeerets on 2006-07-07
it's not intent to use the U10 as a desktop.
but, also on a server you have to do some things, like install packages, make users, config ftp, apache, etc etc.
most server admins do this on the commandline.

in this case, the user is not (at this time) a commandline admin, he is a gui admin.... :-)

that's why im looking for a gui.

i will try to teach him the clui, but for the time he can use the gui.

i will try to install the xubuntu-desktop. perhaps this is enough for him!
tnx marc

Jean-Paul

---

### Post by jpgeerets on 2006-07-07
> **the slayer said:**
> Use webmin!
Dont use a DE on a server!

yeah, webmin was also been in my mind...
webmin works great. also config ie ftp, samba, etc etc.
but,
with webmin you dont have a good package installer like ie synaptic, as far as i know.
in synaptic you can search on "ftp", then you get a lot of results. there you can pick your package and it will be installed. this make live easyer for a linux starter. i think.....

Jean-Paul

---

### Post by allnameswereout on 2006-07-07
(Free)NX + GNOME/KDE.

---

### Post by recupero on 2006-07-08
In this post you need a gui on top of Ubuntu-Server, and you're right.
But what is the real advantage of server machines like the Netra and the Fire over the Ultra's, power consuption? 
What is this factor?
Nowadays this could be an important issue.
Rely-on ability?
Less fans on average, perhaps?
Is installing Ubuntu on a Netra easy?

---

### Post by netztier on 2006-07-10
> **recupero said:**
> 
But what is the real advantage of server machines like the Netra and the Fire over the Ultra's, power consuption? 

Rackmountability, redundancy of fans and power supplies, more slots for disks.

As far as i know, even the motherboards were even the same (i.e. Ultra 80 - Entreprise 420R, Blade 1000 - Fire 280R).

Just to name a few that spring to mind.

kind regards

Marc

---

### Post by jpgeerets on 2006-07-13
> **netztier said:**
> I've even been running **Xubuntu** on my old Sun Ultra 2 with some success (*server install* from CD, then **aptitude install xubuntu-desktop**) . The machine was so low-spec (128MB RAM, 2x 167MHz) that it didn't make any real sense, though. That was back in the 6.06-beta days, and there were some issues with running Firefox, for example. 

I haven't touched that machine since (well, there's more interesting "things" to touch in life than Sun Ultra machines ;) ) so at present I can't tell if 6.06 with Xubuntu-desktop runs well on SPARC machines.

Xubuntu is "more lightweight" than KDE or GNOME, and therefore might be the wiser choice.

Another thing to consider: Ubuntu 6.06 for SPARC comes with a "server-optimized" kernel image; using it as a desktop might have some issues - choosing another kernel image (if available, I can't verify at this time) might be advisable.

kind regards

Marc.



yeah,

i have tryed this, but, after installing xubuntu-desktop, my machine doesn't boot anymore.

when machine boot, it stops at moment graphic is activate.
also no ssh anymore to the machine.
i guess i will install ubuntu server again... :-)
or perhaps put another vga-card in it.

---

### Post by jpgeerets on 2006-07-26
i installed the server again and try again to install xubuntu on it.
still same problem.
it is an original, onboard ATA card.
when system is booting, i see ubuntu (instead off xubuntu).
then several stuff is going to load into memory.
finaly it swtich to graphic mode and then im losing my display...
is becomes black....
also isnt the machine by ssh reacheble.

the only thing i can do is install ubuntu server again.....

hope anyone can help me....

thanks in advace!

Jean-Paul

---

### Post by soapyfish on 2006-07-26
I have been using X-Cygwin with the ssh -X  username@host_ip  command from a windows XP machine to display ubuntu gui apps (like synaptic and gedit etc )  accross my work lan so that I do not have to use the insecure xdmcp it might be an easier route than trying to get the graphics working on the sun machine locally  ?  

[http://www.cygwin.com/](http://www.cygwin.com/)

After all you should really admin a server from the command line....Its the way I am learning the command line..

---

### Post by jpgeerets on 2006-07-26
but, need i to install X on the server?
only reason is to use synaptic for package management.
this server is a "play" server. collegue of me is going to use this.
he know nothing about clui. i will try to teach him, but it will be hard... he's a windows user....

tnx!

Jean-Paul

---

### Post by mips on 2006-07-26
Have a look at WEBMIN.

---

### Post by jpgeerets on 2006-07-26
webmin is also ok.
can i install it with apt-get? when i use apt-get install webmin, the system said it doenst know webmin.

i think the most important thing for a gui is to use a good package manager like synaptic. i think webmin is not as good in this as synaptic. 
to config things like user admin, apache2, etc etc, webmin is ok....

---

### Post by jpgeerets on 2006-07-26
> **soapyfish said:**
> I have been using X-Cygwin with the ssh -X  username@host_ip  command from a windows XP machine to display ubuntu gui apps (like synaptic and gedit etc )  accross my work lan so that I do not have to use the insecure xdmcp it might be an easier route than trying to get the graphics working on the sun machine locally  ?  

[http://www.cygwin.com/](http://www.cygwin.com/)

After all you should really admin a server from the command line....Its the way I am learning the command line..


ok, i have installed this.
i startup by dubble click on the icon.
after that, i type: startx
i get a grapic X.
type: ssh -X ipadres
login with username and pw.
type: sudo synaptic
then this message appears:

(synaptic:32171): Gtk-WARNING **: cannot open display:  

any idea?
what components do i need to install local on my XP machine to get synaptic running? need something to install (except synaptic) on the server?

i hope you can help.

Jean-Paul

---

### Post by allnameswereout on 2006-07-29
Did you start your X server? I doubt it, but you say so. Netstat correct?

After you SSHed in, do this on SSHed box:
export DISPLAY ip_of_host_you_ssh_from_running_X:0

If that not work, on the box you run X from (Windows or not, no matter) start a terminal, do env | grep DISPLAY and implement that in your DISPLAY env on the SSHed box.

Consider to use ssh -C for compression (depending on your network though).

Like I said if you want to run X including DE (or WM) remotely, use NX. GNOME/KDE/whatever remote and fast, with suspend/resume, windowed or fullscreen, printer/soundserver/fontserver support and what not. Plus all the administrative stuff from your DE. Near RDP quality IMO. It doesn't get much easier than this...

---

### Post by allnameswereout on 2006-07-29
Btw, just as note: you can also use PuTTy instead of the command line SSH. It can also do -C / -X and many other options, including key-mapping and such.

---

### Post by jpgeerets on 2006-07-30
on the server i want to manage, there is no X started. i prefer not to put stuff like X on it. but, when it is needed, i have to install that.
im only looking for some stuff so i can run a package manager (ie synaptic) remote in grapfic.
it is for a friend of mine, who doesnt know anything about clui.

---

### Post by allnameswereout on 2006-07-31
Meant X server on your desktop, your server won't run an X server if you use ssh -X; though would if you run NX.

Your package manager will run on the server. Synaptic requires X libs + a lot more libs. Same for ssh -X to a box, the X app will require loads X libraries. That is part of the game.

I do not understand why one would be anal on not wanting NX to run an application and/or DE but doesn't mind having whole X minus server plus DE (GNOME etc) installed to use e.g. Synaptic. Especially since NX, once installed, is very user-friendly.

---

### Post by jpgeerets on 2006-08-01
sure,
i want also use nx. no problem.
if it is not to much load for the server.
how do i setup this?

cheers

Jean-Paul

---

### Post by jpgeerets on 2006-08-01
i have tryed to download..... but there is 1 problem....
if i use linux, i can only choose debian format for i386.... and i use a sun ultra 10. this is sparc hardware....

can i also download solaris? this is for sparc support.... but does that match with my ubuntu server install......?

---

### Post by David Corrales on 2006-08-03
Why don't you use a combination of Webmin for managing servers and stuff and Aptitude from the command line to manage packages?
Aptitude is n-curses based so it's "graphical" and gives you the chance to search packages, install them in batches etc... it's like Synaptic.

---

### Post by allnameswereout on 2006-08-06
Hey JP,

You need to compile NX yourself. I've done this too. I made packages (.debs), for myself. I can give them to you, but they're 3rd party and I could have done sth evil with them (IOW: at your own risk).

$ dpkg -l | grep nx

[i]ii  freenx                                     0.4.4+0.4.5-4ubuntu2                    The FreeNX application/thin-client server ba
ii  nxagent                                    1.4.92+1.5.0-11                         NoMachine NX - nesting X server with roundtr
ii  nxagent-dev                                1.4.92+1.5.0-11                         NoMachine NX - nesting X server with roundtr
ii  nxdesktop                                  1.4.92+1.5.0-11                         NoMachine NX - nesting X server with roundtr
ii  nxlibs                                     1.4.92+1.5.0-11                         NoMachine NX - common agent libraries
ii  nxlibs-dev                                 1.4.92+1.5.0-11                         NoMachine NX - common agent libraries[/i]

..and..

$ dpkg -l | grep xcomp

[i]ii  libxcomp-dev                               1.4.92+1.5.0-11                         NoMachine NX - NX compression library
ii  libxcomp1                                  1.4.92+1.5.0-11                         NoMachine NX - NX compression library
ii  libxcompext-dev                            1.4.92+1.5.0-11                         NoMachine NX - NX compression library
ii  libxcompext1                               1.4.92+1.5.0-11                         NoMachine NX - NX compression library[/i]

I've used .deb control files from others and modified them a bit. Don't use NX 2.0 with FreeNX 1.5 or FreeNX 2.0 with NX 1.5. They're not compatible. There are only .deb control files for FreeNX 1.5 and NX 1.5. Use Serveas his repository:

[http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/)

So you'll have to compile anyway, either make a package, or don't. I prefer the clean way.

Since there are no packages for FreeNX 2.0, NX 2.0 nor .deb control files (not for x86, not for source, not for SPARC) to make .deb from source you only can install those the dirty way or make the .deb control files yourself (and share em? :) ). I tried the latter and gave up. The 2.0 protocol has some advantages over the older ones.

---

