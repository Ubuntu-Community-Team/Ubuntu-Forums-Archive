---
title: "Just a small GUI?"
date: 2010-04-08
forum: Server Platforms
---

### Post by MOGuy78 on 2010-04-08
I'm building a personal file server and after checking out quite a
few, I decided on Ubuntu.  Although I'm doing pretty well with the
CLI, just in case I need it (and please don't yell at me) I'd like
to have just a simple GUI file manager.  I don't want to have to
install an entire version of Gnome or Kde, though.  I've used
Microsoft all the way back to the DOS days, and the best program
that I've ever found was Norton Commander.  Is there anything
similar to that for linux, and if not, what would any of you
suggest?

---

### Post by cascade9 on 2010-04-08
If your looking for somethign simple and light, fluxbox, lxde of xfce would be the best things to use IMO. Way more GUI than NC ever was, (they arent just file managers, its a whole desktop) but they are light, simple and easy to use.

---

### Post by KnottyMars on 2010-04-08
> **MOGuy78 said:**
> I'm building a personal file server and after checking out quite a
few, I decided on Ubuntu.  Although I'm doing pretty well with the
CLI, just in case I need it (and please don't yell at me) I'd like
to have just a simple GUI file manager.  I don't want to have to
install an entire version of Gnome or Kde, though.  I've used
Microsoft all the way back to the DOS days, and the best program
that I've ever found was Norton Commander.  Is there anything
similar to that for linux, and if not, what would any of you
suggest?

lol, i dont think anyone will yell at you. I too wanted a "server" to build in my home for large files and images and stuff. 

I guess it depends on what you are using it for, Samba works great for file and folder sharing and can be installed on the desktop version of Ubuntu. 

If you want a true server, then the server OS is going to be CLI all the way, the only way around it was to install the desktop package which changes the entire thing to a full on GUI. (Someone correct me if Im wrong), but initially I tried to do just that and thought to myself, I could really just use the desktop version and install Samba and a few other apps I needed to get what I wanted. 

The actual server im using at work works as a real server (hosting domains, running ssh, MySQL server, etc...) but it really depends if you are just file sharing or if you intend to use alot of the server, services. 

Currently my server sits in a room and I just access it remotely to make changes and add stuff. Good luck in whatever you choose, either one is a great choice. 

I would recommend playing with the CLI and see if you can get it working, it really is great when you take it bit by bit. Im still a new person to Linux but Im loving it. Still cant get over all this great software is free.

---

### Post by rudy.b on 2010-04-08
> **MOGuy78 said:**
> ... the best program
that I've ever found was Norton Commander.  Is there anything
similar to that for linux, and if not, what would any of you
suggest?

You could try [Midnight Commander]("http://www.midnight-commander.org/") (it's in the repositories).  I've never used it myself, but it's apparently similar to Norton Commander.

---

### Post by dudumomo on 2010-04-09
Otherwise, you can simply install gnome-core, (gnome minimal, without any additional package)

---

### Post by dipeshmehta on 2010-04-09
> **rudy.b said:**
> You could try [Midnight Commander]("http://www.midnight-commander.org/") (it's in the repositories).  I've never used it myself, but it's apparently similar to Norton Commander.

I agree.

I was one of the fan-lover of NC in the DOS era, and I found MC almost similar featured interface.

Dipesh

---

### Post by cascade9 on 2010-04-09
> **KnottyMars said:**
> If you want a true server, then the server OS is going to be CLI all the way, the only way around it was to install the desktop package which changes the entire thing to a full on GUI. (Someone correct me if Im wrong), but initially I tried to do just that and thought to myself, I could really just use the desktop version and install Samba and a few other apps I needed to get what I wanted. 

A 'true server' is command line only? Well...not really. IMO anyway. 

Just installing a desktop enviroment doesnt mean you have to use the deskotp, its easy enough to just log into the command line and never use the dekstop unless you want to. 

As for the difference between 'desktop' and 'server' linux versions, well, I have to admit that I'm slightly ignorant- but I would guess that like in hardware the line has blurred a lot over the last few years. 

I'm old enough to remember when for hardware, 'server' meant buffered/ECC RAM, SCSI RAID systems with hotswap drives, redundant power supplies, etc. Even though this sort of hardware is still the norm in enterprise level servers (well, apart from SAS replacing a lot of SCSI) these days people get a 'xxxx' desktop, put a few files on it and call it a server. Is it a server? sort of, in that it 'serves' files, but its hardly the same as what you get when you go looking as business servers. ;)

---

### Post by Bachstelze on 2010-04-09
> **cascade9 said:**
> If your looking for somethign simple and light, fluxbox, lxde of xfce would be the best things to use IMO. Way more GUI than NC ever was, (they arent just file managers, its a whole desktop) but they are light, simple and easy to use.

+1 Fluxbox, that's what I use on mine.

---

### Post by MOGuy78 on 2010-04-11
Thanks Rudy.b, Midnight Commander is perfect for what I'm needing, plus since I've used the DOS version for so long, I already know how to use this one!  After a while I decided against installing a whole desktop GUI just for a simple file manager, so I decided I'd just go without the app.  Since all I planned on doing was to use the computer as a simple home file server to share my music, videos, and other misc. data between the computers in my house, finding out about Midnight is great.  Thanks a lot for the info.

One other program that I just happened to find out about while
searching on this forum was an app called Webmin.  Though I
haven't had much time working with it, it looks like the perfect
program to run things remotely with.  After installing it, it
even seems like you can set up and run Samba with it, along with
quite a few other utilities I may have need for.  Plus, since
Midnight Commander is a console app itself, I can use it when
I remotely access the CLI on the server, and without all of the
graphics, it still won't slow it down.  Thanks everybody for
all of the help, and with so many great people who are willing
to help with a problem, I'll plan on coming here for anything
I may have a question about!  Thanks again.

---

