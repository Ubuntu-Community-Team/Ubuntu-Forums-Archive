---
title: "Do you use a graphical user interface on your server?"
date: 2011-04-15
forum: Server Platforms
---

### Post by Learning Linux 2011 on 2011-04-15
I suppose a purist might say no, but are there downsides to using a GUI on a server?

I guess it would take up some resources, but would it open security holes?

---

### Post by espressobeanie on 2011-04-15
Do you prefer to be blind or to see?

I use a GUI because it teaches me a lot more about the file structure of my server and it's hard to setup a php site without being able to locally render pages on firefox and test before deployment. I'll eventually go back to CLI completely. GDM3 is being stubborn and won't let me use 'startx' from CLI instead of login boot.

---

### Post by dtfinch on 2011-04-15
When semi-covertly turning our backup servers into a render farm, when command line renders aren't sufficient (scripted renders, not regular animations), I run Blender at low priority within a temporary xvfb session (X11 server that renders to memory rather than the screen) and connect to it with x11vnc. I'm not sure if that counts though.

Otherwise, not much. I sometimes use swat (web interface) for samba config, but the rest is command line over ssh.

---

### Post by usatonycuba on 2011-04-15
It all depends on how you want to deploy the structure of the software on your server and what are the plans you have for this server .. if the purpose of learning ... you have the option of a GUI, but for purposes of a real production server, I do not think anyone would recommend a Graphical Interface .. especially  problem will be the whole resources consumed by the system because a GUI... and also but not less >> security ... Remember that each application of sortware you install on your server .. must be ONE MORE application software  >  to:  update, secure, debug .. etc. .. etc.

IMO

---

### Post by kamaji792 on 2011-04-15
Command line.

In the very early days of using Linux I'm sure I like having a GUI.  But after my first install of Ubuntu 6.04 server (I think), for which the Ubuntu howto was for CLI I have been in love with it.  I don't even use SWAT these days for SAMBA.  I am left with the feeling that a GUI is just getting the in way of me really understanding what is going on.

But each to his own.  If using a GUI gets you going, go for it.  I'd still bet you end up using the CLI if you keep at it for long enough.  The biggest thing is all the instructions for server work use the CLI.

Atb K

---

### Post by reddevil2064 on 2011-04-15
Command line. Why use a GUI on a server? I suppose if it is not in production using a GUI would be fine though. It is much easier to learn by using the command line first, then a gui, that way you understand the underlying concepts.

---

### Post by usatonycuba on 2011-04-15
> **reddevil2064 said:**
> command line. Why use a gui on a server? I suppose if it is not in production using a gui would be fine though. It is much easier to learn by using the command line first, then a gui, that way you understand the underlying concepts.
+1

---

### Post by kevinthecomputerguy on 2011-04-15
IMHO GUI has no place on a server.
A web-based control panel is totally fine, but a graphical desktop, no way. Too tempting to use the server for things it was not meant for.

---

### Post by stmiller on 2011-04-16
Just command line / no gui for me.

I'm security paranoid and I like to have only the minimally required software installed on a server that is on the web. And likewise tight on user accounts allowed on the box, and running services and what user they run as, etc. But I'm paranoid. :P

Red Hat / Centos does have some nice server GUI sort of tools for things like BIND and apache, but the command line ones are great as well.

---

### Post by Holdolin on 2011-04-28
> **stmiller said:**
> Just command line / no gui for me.

I'm security paranoid and I like to have only the minimally required software installed on a server that is on the web. And likewise tight on user accounts allowed on the box, and running services and what user they run as, etc. But I'm paranoid. :P

Red Hat / Centos does have some nice server GUI sort of tools for things like BIND and apache, but the command line ones are great as well.

Aye, I'm paranoid as well.  For each peice of software you have running, that's one more chance for something to go wrong or someone to get in.  I'm setting up my first server, and she's gonna be a LAMP server, so I'd really like her to be as secure as possible.  I also feel that using the CLI only is making me learn a lot about just what goes on and how stuff works on my server.

---

### Post by AllGamer on 2011-04-28
GUI for my private servers

it makes managing things are lot easier, it's faster, and you can do copy and paste of repetitive tasks that needs manual intervention, and don't work nicely as a batch job

otherwise Command for production servers

---

### Post by CharlesA on 2011-04-28
I run CLI for my home server. I do use phpvirtualbox, since I got tired of having to ssh into the box and configuring a VM with a long list of commands.

My web development box is just a VM running the lamp stack (with a GUI).

---

