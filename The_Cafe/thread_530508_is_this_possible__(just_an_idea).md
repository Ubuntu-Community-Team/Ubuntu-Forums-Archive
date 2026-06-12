---
title: "is this possible ? (just an idea)"
date: 2007-08-20
forum: The Cafe
---

### Post by @vijay@ on 2007-08-20
recently i saw this post
[http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/](http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/)
about running windows applications on linux 

now my question is
Is  it possible to run the windows applications without having to logoff and the application has to be displayed  only in the linux desktop but not in the windows pc ; so that i can ask one of my friend TO HELP ME RUN GTALK and other usefull apps

---

### Post by loserboy on 2007-08-20
not sure if I understand you correctly, but what they are doing in that howto is running VMware, just a virtual windows sesson in ubuntu.  it runs Windows in a window inside Gnome, although this screenshot makes it look like they have it running more seamlessly and i'm not sure how they did that.

edit: oh i see the way it looks so seamless is a trick the the remote connections

---

### Post by nickburns on 2007-08-20
It is possible with vmware.   I use it everyday.  It will allow you to run windows as an application inside gnome.

It also allows you to cut and paste from linux to windows.  :)

---

### Post by PetePete on 2007-08-20
haven't read the link, but I run Office 2003 straight into KDE as an application using Crossover linux (which is a program that runs in the background unseen)

unlike VMware which you have to run the vmware program and then boot up the windows virtual computer.. makes it much faster, suppose its just a better version of wine.

---

### Post by Mach1US on 2007-08-20
Again it is possible to use wine or crossover linux with most software but i do prefer VmWare which allows me to put it on USB thumb drive and take it with me and use it on multiple machines with all my files,setting and everything else.

---

### Post by @vijay@ on 2007-08-23
what i mean is that when i started an application it runs/displayed  in the client but uses the server(windows) resources ;

---

### Post by popch on 2007-08-23
It is perfectly possible.

You can run Windows with all applications which need Windows on a server and display either the Windows desktop or each individual Windows application in a window on your Linux desktop.

The concept is called Terminal Server. Ubuntu comes out of the box with a Terminal Server Client.

I think that Windows has the terminal server already built in, but I'm not sure.

In our company we use rather powerful servers for running a set of Windows applications in a terminal server environment. The clients on which these applications are used are also Windows machines. We do this partly for security and performance reasons, partly on account of the centralized and thus greatly simplified application maintenance.

---

### Post by Dragonbite on 2007-08-23
This looks like a good option for programs that are not widely used and doesn't work in Wine.  I'd love to get it working but my machine isn't powerful enough.

---

### Post by insane_alien on 2007-08-23
wow, that works pretty well. windows jump around like a washing machine full of bricks with the ballast removed when you drag the windows but the programs work.

---

### Post by popch on 2007-08-23
> **insane_alien said:**
> wow, that works pretty well. windows jump around like a washing machine full of bricks with the ballast removed when you drag the windows but the programs work.

Am I missing something? What did you do? Did it work as expected (or to the contrary, as advertised)?

---

