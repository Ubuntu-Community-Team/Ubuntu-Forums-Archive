---
title: "My Ubuntu Experience"
date: 2009-01-16
forum: Testimonials &amp; Experiences
---

### Post by haarvik on 2009-01-16
Ok, since my posts get dropped because of my title, I'll try and write a book from top to bottom of what I have been through.

After looking at several distro's for what I wanted to accomplish, I settled on Ubuntu.  Mind you, what I wanted was not a complicated thing...or so I thought.  A minimal desktop with Firefox, Thunderbird, Mplayer, IM.  Not so tough, or so I thought...silly me.  I wanted a lightweight window manager so I chose matchbox.  I downloaded Ubuntu and began installing it at about 9 am on 1/15.  By 9:30 it was done.  I did notice that I was not given an option as to what packages I wanted installed.  It just installed everything.  So, I thought, I'll just use apt to remove what I don't want.  

First order of business...dump bloated gnome.  Next, get rid of useless apps I didn't want.  I spent an hour removing stuff.  Then it was time to add what I did want.

Now comes the fun part.  Remove gnome and x is broken.  Sure it'll run, but nothing works like it is supposed to.  Matchbox themes?  Nope.  Autostart X and login?  Nope.  Searched for hours trying to find an answer.  Nothing.  I even IM'd the developers of matchbox and they were stumped.  None of the files that were supposed to be there were.  I had to write my own scripts that should have been installed with it.  Yet it still did not work correctly.  I also decided to check my disk space to see how much I gained removing the unwanted stuff.  2.1GB used.  WHAT!?!?!?  What could possibly be there?  I removed almost everything.  I would have thought I would have gained more space than that.  The full install was 2.3GB.

So my conclusion is that while Ubuntu may be ok for someone new to Linux, it's not for custom installs.  It doesn't take change very well.  I guess I am back to Debian where I can control it.  I just have to do it in a harder manner.

---

### Post by hyper_ch on 2009-01-16
for custom install use the alternate cd - at boot you can then chose to setup a minimal system... there's also an ubuntu minimal cd...

---

### Post by haarvik on 2009-01-16
I just installed Debian 4.  What is it with every distro installing gnome by default!? Give me a freakin choice will ya?  Does this mini-CD allow me to do that?  Can I actually choose my WM WITHOUT having gnome forced down my throat?

---

### Post by hyper_ch on 2009-01-16
the mini cd normally does not install any gui :)

---

### Post by cardinals_fan on 2009-01-16
> **hyper_ch said:**
> the mini cd normally does not install any gui :)
Actually, by default it will.  However, you just have to enter "cli" at the boot prompt to install a command line system.

---

### Post by solwic on 2009-01-16
> **haarvik said:**
> I just installed Debian 4.  What is it with every distro installing gnome by default!? Give me a freakin choice will ya?  Does this mini-CD allow me to do that?  Can I actually choose my WM WITHOUT having gnome forced down my throat?

From Ubuntu:  

```
sudo apt-get install kubuntu-desktop
```

or

```
sudo apt-get install xubuntu-desktop
```

At least, I'm pretty sure those are the commands from the CLI.  

Then you can choose at the login screen which you want.  You can even change the default, if you like.  :)

EDIT:  I just read through your whole first post, and it looks like you might try installing Xubuntu. [www.xubuntu.com](www.xubuntu.com)  :)

---

### Post by haarvik on 2009-01-16
I looked at that, but it also looks like a gnome desktop.

---

### Post by haarvik on 2009-01-16
Actauly it looks as though Ubuntu Mobile is what I am after.  I just hope it all works, and can be customized as the site says.

---

### Post by cardinals_fan on 2009-01-16
> **haarvik said:**
> I looked at that, but it also looks like a gnome desktop.
They mutated Xfce to resemble GNOME.

What window manager do you prefer to use?

---

### Post by piousp on 2009-01-16
It sure does, but its running XFCE with some gnome apps as far as i can tell.
Since you are running debian, you best shot would be the minimun-cd. From there, you'll have to add everything to get your WM working.
Just curious, will there be any difference between running that custumize ubuntu and debian?
I mean, they'll probably be really similar, dont they?

Also, [this]("http://www.psychocats.net/ubuntu/nox") may come in handy

---

### Post by haarvik on 2009-01-16
Well, I prefer a light manager...like matchbox.  Don't care for the fluff.

---

### Post by haarvik on 2009-01-16
Well, I guess MID is out...looks like it uses gnome as well.  It's a freaking conspiracy.  Gnome must pay the distros to use it.

---

### Post by piousp on 2009-01-16
*Flame warning*
Gnome is overrated

(Oh boy :P )

---

### Post by haarvik on 2009-01-16
Well, I decided to try mobile anyway.  What a load.  2.8GB of useless crap.  I saw about 8 games loaded, so I went into synaptic to remove them and they don;t even register as having been installed!

---

### Post by solwic on 2009-01-16
> **haarvik said:**
> Well, I decided to try mobile anyway.  What a load.  2.8GB of useless crap.  I saw about 8 games loaded, so I went into synaptic to remove them and they don;t even register as having been installed!

There's always DOS.  Or Damn Small Linux.  Puppy is supposed to be pretty small, too, I think.  

Maybe take the Vista Solution:  buy new hardware that runs the "fluff", as you call it, more quickly.  :)

Good luck, whatever you decide.  :)

---

### Post by stchman on 2009-01-16
> **haarvik said:**
> Ok, since my posts get dropped because of my title, I'll try and write a book from top to bottom of what I have been through.

After looking at several distro's for what I wanted to accomplish, I settled on Ubuntu.  Mind you, what I wanted was not a complicated thing...or so I thought.  A minimal desktop with Firefox, Thunderbird, Mplayer, IM.  Not so tough, or so I thought...silly me.  I wanted a lightweight window manager so I chose matchbox.  I downloaded Ubuntu and began installing it at about 9 am on 1/15.  By 9:30 it was done.  I did notice that I was not given an option as to what packages I wanted installed.  It just installed everything.  So, I thought, I'll just use apt to remove what I don't want.  

First order of business...dump bloated gnome.  Next, get rid of useless apps I didn't want.  I spent an hour removing stuff.  Then it was time to add what I did want.

Now comes the fun part.  Remove gnome and x is broken.  Sure it'll run, but nothing works like it is supposed to.  Matchbox themes?  Nope.  Autostart X and login?  Nope.  Searched for hours trying to find an answer.  Nothing.  I even IM'd the developers of matchbox and they were stumped.  None of the files that were supposed to be there were.  I had to write my own scripts that should have been installed with it.  Yet it still did not work correctly.  I also decided to check my disk space to see how much I gained removing the unwanted stuff.  2.1GB used.  WHAT!?!?!?  What could possibly be there?  I removed almost everything.  I would have thought I would have gained more space than that.  The full install was 2.3GB.

So my conclusion is that while Ubuntu may be ok for someone new to Linux, it's not for custom installs.  It doesn't take change very well.  I guess I am back to Debian where I can control it.  I just have to do it in a harder manner.

A full Ubuntu install is about 3GB.  This is far less that most other OSes.  If you do not like Gnome then use Kubuntu or Xubuntu.  What GUI do you prefer?

---

### Post by haarvik on 2009-01-16
matchbox

---

### Post by 3rdalbum on 2009-01-17
Why don't you start with a server install? Or check if Fluxbuntu is still around, and just replace Fluxbox with Matchbox?

---

