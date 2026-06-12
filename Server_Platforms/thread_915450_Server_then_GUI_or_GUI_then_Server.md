---
title: "Server then GUI or GUI then Server?"
date: 2008-09-09
forum: Server Platforms
---

### Post by nathan42100 on 2008-09-09
For an independent study project at school, I'll be setting up a few servers with Ubuntu (or some variation) for "email", dns, web, and so on. To make things easier for me and the "lesser" kids who will be using the server, I would like a gui on it.

I've heard of people installing xUbuntu, then the LAMP server stuff, but also installing ubuntu-server and some packages.

Which is better? What commands will I need to run?

Since the servers won't have any internet connection (damn school), I'll also need to know what packages to download, from where, and install in what order (or just how). I'll have a few disks available to me, including Xubuntu, Ubuntu, Edubuntu 8.04.1  and soon to be an ubuntu-server 8.04.1.

Please help me! I need to start work by Monday.

---

### Post by tuxxy on 2008-09-09
If you are worried about which packages to install then a GUI to server maybe a good option, what files you would install depends on which desktop environment you would like etc

Heres a link to the server guide for more info

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by nathan42100 on 2008-09-09
well, I've decided on xfce4 since that seems to be the least CPU hog-ish, though for my purposes, it doesn't really matter...

Also, the link you provided, though helpful contains nothing (that I can see) about setting up a gui and whether or not to do it before or after the server part of the installation

---

### Post by tuxxy on 2008-09-09
[http://packages.ubuntu.com/hardy/xfce4](http://packages.ubuntu.com/hardy/xfce4)

---

### Post by inphektion on 2008-09-09
Depends on if you want a server with a GUI or a desktop GUI with server roles.  the former would be much more streamlined for pure server role with your choice of desktop, with the latter being a full blown desktop including server roles.
HTH...

---

### Post by nathan42100 on 2008-09-09
Well, I don't really see what I would need a full blown desktop version for in terms of applications. I really just want gedit to be able to edit all the settings and have an icon to click on if I need to restart everything or whatever.

---

### Post by cariboo on 2008-09-09
if you only need a few gui apps, there is no need to install a full desktop, just install the applications you need then access tem using x forwarding through ssh. Have a look at this howto:

[http://handyfloss.wordpress.com/2007/09/17/x-forwarding-through-ssh/](http://handyfloss.wordpress.com/2007/09/17/x-forwarding-through-ssh/)

Jim

---

### Post by nathan42100 on 2008-09-09
> **cariboo907 said:**
> if you only need a few gui apps, there is no need to install a full desktop, just install the applications you need then access tem using x forwarding through ssh. Have a look at this howto:

[http://handyfloss.wordpress.com/2007/09/17/x-forwarding-through-ssh/](http://handyfloss.wordpress.com/2007/09/17/x-forwarding-through-ssh/)

Jim
this isn't going to be on the internet so having X11 viewed on another computer would be pointless. It must be local (sadly). Stupid school rules.

---

### Post by hyper_ch on 2008-09-10
how would a gui on a server help anyone running the server?

---

### Post by lazyart on 2008-09-10
just use nano to edit files.
to restart, use shutdown now -r.

That's a bit extreme to set up a gui for.

---

### Post by volkswagner on 2008-09-10
> **nathan42100 said:**
> this isn't going to be on the internet so having X11 viewed on another computer would be pointless. It must be local (sadly). Stupid school rules.

I think most people would assume these servers would be attached to a network.  You can use ssh within the local network.  Many people running a server don't even have a monitor attached (headless).

If you are building several servers (all on one network), than they all can  be headless, and administered via one machine (ssh).

I am not sure what a server can do, if not connected to some sort of an intranet or at least one other machine.

---

### Post by silverglade00 on 2008-09-10
To answer your question, it's a little easier to set up the server bits by using Ubuntu Server then doing

```
sudo apt-get install ubuntu-desktop
```

The only reason it's easier is because it asks you which server roles you want during the install.

---

### Post by cdenley on 2008-09-10
Install whatever you want, then run
```

sudo tasksel

```
Select whatever server configurations you want, as well as "Xubuntu desktop". It doesn't really matter which comes first, the end result is the same. It doesn't really matter which desktop you install, either, as long as you disable it until you need it.
```

sudo update-rc.d -f gdm remove

```

---

### Post by nathan42100 on 2008-09-10
> **volkswagner said:**
> I think most people would assume these servers would be attached to a network.  You can use ssh within the local network.  Many people running a server don't even have a monitor attached (headless).

If you are building several servers (all on one network), than they all can  be headless, and administered via one machine (ssh).

I am not sure what a server can do, if not connected to some sort of an intranet or at least one other machine.Its going to be used to simulate servers on the internet as well as provide labs and activites for a cisco networking class since the software we need isn't allowed on a school network.

---

### Post by nathan42100 on 2008-09-11
So in order to install xfce from CD, what do I type?

I know i have to do sudo apt-cd enable but thats it.

Remember , no internet. So if I have to download a package, please tell me now!

---

### Post by nokuntrol on 2008-09-12
It does matter and there is a difference with installing server first or install desktop with server roles.

If you install server, you get a kernel compiled with different options. ie. the following:
    * The Server Edition uses the Deadline I/O scheduler instead of the CFQ scheduler used by the Desktop Edition.
    * Pre-emption is turned off in the Server Edition.
    * The timer interrupt is 100 Hz in the Server Edition and 250 Hz in the Desktop Edition.
    * The Server Edition is optimised for i686 processors while the Desktop Edition is optimised for both the i586 and i686.
    * Virtualization is better supported in the Server Edition through the enabling of IPC namespaces.
    * Multiple routing tables for the IPv6 protocol are also supported in the Server Edition.
    * For 32-bit systems the Server Edition is configured to use PAE which allows addressing up to 64GB of memory while the Desktop Edition is configured for 4GB.
    * When running a 64-bit version of Ubuntu on 64-bit processors you are not limited by memory addressing space.

---

### Post by lenswipe on 2008-09-12
> **hyper_ch said:**
> how would a gui on a server help anyone running the server?

because it would make it easer for "lesser users" to open nautilus and thing. For a server i personaly prefer text only but the lesser users would find this easier.

---

### Post by hyper_ch on 2008-09-12
and what do you need nautilus for?

---

### Post by nathan42100 on 2008-09-12
> **hyper_ch said:**
> and what do you need nautilus for?

looking through files, opening them easily etc.

---

### Post by hyper_ch on 2008-09-12
and you need to do that on a server on a regular base for ...?

---

### Post by nathan42100 on 2008-09-12
This is an educational thing for school. It doesn't matter because:
a) I already said it would have a desktop
b) kids that will be changing things don't know how to use the terminal
c) i feel more comfortable in a gui
d) its not going to be on the internet anyway, just a local network.

Just tell me how and stop arguing and telling me it isn't worth it.

---

### Post by rsambuca on 2008-09-12
> **hyper_ch said:**
> and you need to do that on a server on a regular base for ...?

What exactly is your problem here?  The op is asking very specific questions, so perhaps help or move elsewhere.

---

### Post by hyper_ch on 2008-09-12
> **nathan42100 said:**
> This is an educational thing for school. It doesn't matter because:
a) I already said it would have a desktop
b) kids that will be changing things don't know how to use the terminal
c) i feel more comfortable in a gui
d) its not going to be on the internet anyway, just a local network.

Just tell me how and stop arguing and telling me it isn't worth it.

You are welcomed to go back and check what you wrote and what I wrote. You said you wanted to run a server and put a gui on it to make it "easier" to use.
I asked then how a gui would make a server easier to use. However you did not write you want to use it as desktop.

> **rsambuca said:**
> What exactly is your problem here?  The op is asking very specific questions, so perhaps help or move elsewhere.
dito.

---

### Post by nathan42100 on 2008-09-12
> **hyper_ch said:**
> You are welcomed to go back and check what you wrote and what I wrote. You said you wanted to run a server and put a gui on it to make it "easier" to use.
I asked then how a gui would make a server easier to use. However you did not write you want to use it as desktop.


dito.

Now if you go back and read what I wrote, you'd see that I did answer your question.

---

### Post by hyper_ch on 2008-09-12
I did ;) but you asked to run for a server... not a desktop with server capabilities and I still question you how it would make it easier to run a server with a gui.

---

### Post by rsambuca on 2008-09-12
Just ignore him Nathan.  It is clear he is trying to belittle you rather than help you.  Sometimes when people are so familiar with the linux commands they forget that they once didn't have them all memorized, or that some people find GUI's easier to use.

---

### Post by hyper_ch on 2008-09-12
yet he asked how to run a server ;)

---

### Post by rsambuca on 2008-09-12
> **hyper_ch said:**
> yet he asked how to run a server ;)

OK, we get it.  Clearly you are much more competent than the rest of us.  You are superior in every way conceivable.  We bow to your greatness, Oh Mighty One.  Now please go harass someone else.  There is no rule that states that a server can not have a Graphical User Interface.  It is completely legitimate to run a server with a GUI.  While you may not require one, please understand that some of us prefer to use one.

---

