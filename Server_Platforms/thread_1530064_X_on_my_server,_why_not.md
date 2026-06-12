---
title: "X on my server, why not?"
date: 2010-07-13
forum: Server Platforms
---

### Post by Xi0N on 2010-07-13
Well,.... i have beeen managing a server for some months now, and i sometimes think about installing a gnome desktop on it so i can manage some things of my server in a more comfortable way.
The server is not a critical server, and is not a potential target for attacks....
Is it so uncommon and so not-recommended to do so?
Some advice on this would be really nice...
Some pros, some cons.........thanks! :popcorn:

---

### Post by DrMelon on 2010-07-13
I've seen people run graphical servers before. It's not TOO uncommon.

---

### Post by pmlxuser on 2010-07-13
alot of server configuration is done through editing text configuration files, very few graphical tools exist to do most of the command used to run a server. it can be done but you will likely get back to the terminal for most of the things

---

### Post by Xi0N on 2010-07-13
I know i will have to use the terminal for a lot of things but, one of the reason, for example, is that i want to run virtual machines on the server with virtualbox.
I can do this via console, BUT its infinitely easyer to manage those via the graphical tools.

---

### Post by =ChAoS= on 2010-07-13
Sorry to butt in but I too am interested in this topic. I have just rented a dedicated server running ubuntu server 10.04 and would like a very basic interface to nx into. I am not interested in a flashy pretty desktop just the basics that will expand as i install things via putty or terminal when i can connect via NX. Maybe it's already there and i just need to install vnc4server to connect? 
 
thanks =ChAoS=
 
*****UPDATE*****
 
I found a thread about this and did this install ...
 
```
apt-get install x-window-system-core xserver-xorg gnome-desktop-environment
```
 
Now to see what i've installed lol At worse i can re install my o/s

---

### Post by arrrghhh on 2010-07-13
Yea, I think there's also a gnome-core package instead of the entire DE package... not sure tho.

The main reason I don't run X on my server is utilization - I want my server dedicated to running its services... NOT displaying a pretty GUI!  Besides, I don't do anything that needs a GUI.

I did play with VBoxHeadless, which probably would've been easier with an interface... but I know the virtual machine ran that much better because there's very little overhead.

---

### Post by Xi0N on 2010-07-13
I redirected the X via ssh , created the vms in another computer, exported them, and then imported them on the headless server.... then, the only command i need is the one for starting the virtual machines (i used "screen" for running multiple ones.....

I think i will stick to headless but now, i wont be "afraid" if some day i decide i really need to install and run an x server... :)

---

### Post by Xi0N on 2010-07-26
This is the solution for managing my virtualbox headless server: [http://code.google.com/p/phpvirtualbox](http://code.google.com/p/phpvirtualbox)

:D

---

### Post by Iowan on 2010-07-26
[Here]("https://help.ubuntu.com/community/ServerGUI") is some more reading material on Server GUI's - if you need it. :-k

---

### Post by v1ad on 2010-07-26
reason i don't is because it's a waste of computer resources. it will draw more cpu power resulting in more power usage and also might slow your system down a bit under a heavy load.

---

### Post by arrrghhh on 2010-07-26
> **Iowan said:**
> [Here]("https://help.ubuntu.com/community/ServerGUI") is some more reading material on Server GUI's - if you need it. :-k

I bow to your knowledge sir, that link is most excellent.  I'm sure I'll be using it quite frequently as this topic always seems to in one way or another...

---

