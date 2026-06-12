---
title: "[SOLVED] What are the benefits of Ubuntu Server"
date: 2008-05-05
forum: Server Platforms
---

### Post by sp0nge on 2008-05-05
Please forgive my ignorance. I have been tossing around the idea of turning one of my old desktop machines into a server for the webpages that I have hosted- I think it will be a much more cost effective solution as well as giving me a great education. 

My reason for this post is that I have been asking around the few people I know who have their own servers, most are businesses. I have tried to get some insight into what all will be involved only to find out not one of them actually set up the server themselves, they just know how to run it, and none are *nix. 

I have Feisty installed on the machine I'm thinking of converting, and I wonder if it is really necessary to install a server edition or would the desktop edition work just as well? Will the desktop edition not run Apache and other server applications just as well? 

I'm interested in creating an extranet using this machine. I want to serve the web pages as well as having a central location to store music, movies, and other files to be accessed by the other machines on my network. I appreciate any education the good people in the forums can offer me.

---

### Post by smileypaul on 2008-05-05
If you're just messing around with a home server, sure, install the Apache webserver, and have some fun.

Generally, in a _production_ environment, it is undesirable to run Xserver due to security issues, and resource issues. 

Beyond that, most companies use Microsoft Servers due to corporate support. That and the software is generally bundled with whatever server they have bought/leased, or it was recommended based on their IT staff's recommendation.

---

### Post by hyper_ch on 2008-05-05
you don't need a gui on the server as configuration is done by editing config files... there's no need for a gui there...

Setting up apache to serve webpages... acting as fileserver... that's all simple and straight forward.

---

### Post by sp0nge on 2008-05-05
Thanks for the input! 

I am only playing with this for the education at the moment, but I would like to have the ability to run the web pages for my businesses through my home server. I was reading up on Apache and had considered this to be the best option, but am I understanding X Server to be more secure? I deal with a lot of personal information in my business and have been assured by my current web host that it is secure. I want to be certain that I have as much security in place as possible. 

And is that the only REAL major difference- the server edition doesn't have a gui?

---

### Post by tubezninja on 2008-05-05
> **sp0nge said:**
> 
And is that the only REAL major difference- the server edition doesn't have a gui?

The primary difference between the server and desktop editions is that ubuntu server comes configured with ONLY the services you need to run a server.

It's more than just the GUI.  The Desktop edition comes with all the desktop software packages installed (FireFox, OpenOffice, GIMP, etc.), as well as printer sharing resources, bluetooth drivers, and tons of other stuff.  

A server on the other hand, typically doesn't need all these things.  presumably, you aren't going to be using a server as a desktop at the same time.  A production server's focus is just being a server, and oftentimes is sitting on a rack in a server room, where there isn't going to be a lot of direct mouse/keyboard interaction.  For this reason, it doesn't make sense to install the desktop packages, and that way the server can focus its memory, hard drive space and CPU resources on *just* the required server applications.

Is it possible to install the desktop items on a computer running server edition?  Absolutely.  But it's not considered very efficient to do so.

If you're absolutely new and want to try out running the server in a GUI environment, I would recommend installing the xubuntu-desktop package on top of the server edition software, as it's the "leanest" of the desktop GUIs.  You can do that by typing in:

```
sudo apt-get install xubuntu-desktop
```

But even with xubuntu, I'd consider this like training wheels, and the GUI is really just a comfortable crutch. At its base, you're still using text editors to configure everything, they just have a nice looking window around them and can be visually arranged. Eventually you'll want to ditch the GUI, especially if you plan on administering production servers.

This isn't to mean you're TOTALLY never using a windowing environment again, however. :)  A lot of people who run servers do it the way I do: we ssh in and make changes and such in a terminal window, on a remote desktop that IS using a GUI.  I'm regularly logged into my server using ubuntu desktop, Mac OS X, and (very) occasionally, a Windows machine with PuTTY installed.

---

### Post by cdenley on 2008-05-05
> **sp0nge said:**
> Thanks for the input! 

I am only playing with this for the education at the moment, but I would like to have the ability to run the web pages for my businesses through my home server. I was reading up on Apache and had considered this to be the best option, but am I understanding X Server to be more secure? I deal with a lot of personal information in my business and have been assured by my current web host that it is secure. I want to be certain that I have as much security in place as possible. 

And is that the only REAL major difference- the server edition doesn't have a gui?

X server and apache are 2 completely different things.

X server = graphics environment
apache = web server

X server is generally secure, but a web server with apache is a little more secure if you aren't running an X server. X server probably isn't what you would consider a server. It should only be used by the local user.

If you are going to host a server which receives sensitive information from users, you should use SSL encryption to ensure the data is not intercepted. If you are programming your site yourself, I would be more worried about your own code.

The server edition is the base ubuntu without a desktop environment, the server kernel installed by default instead of the generic kernel, and "sudo tasksel" is run during the install so you can use typical server configurations such as LAMP (linux+apache+mysql+php). You can easily add a desktop environment, choose a server configuration, or switch your kernel with either installation.

---

### Post by exaviorn on 2008-05-05
Basically ubuntu server without an interface is very good for memory (GUI's) take memory:)
Boot time is quick
there are many other advantages (that I have forgotten)

---

### Post by sp0nge on 2008-05-05
I'm new to server administration, but more than comfortable with ubuntu.  At this point, I'm just a few clicks away from downloading the server edition. If I understand correctly, I can then detatch the monitor and mouse and just use the Terminal Server client to configure the server. Can you direct me to any guides that might be helpful?

---

### Post by FakeOutdoorsman on 2008-05-05
If you're going to run a site for business, then use a server install.  Play around with it for a few months to get comfortable with it and then make the move.  While you are learning you might decide you don't want the responsibility or you might find that you really like having complete control over your site.

As said already, the server version uses the same repos as the desktop version, but with some different packages installed (minus any desktop stuff).  The kernel is also different and is tuned for server use.

> **sp0nge said:**
> ... If I understand correctly, I can then detatch the monitor and mouse and just use the Terminal Server client to configure the server. Can you direct me to any guides that might be helpful?

Exactly.  Once I get the OS installed it can become headless and I connect to it via ssh with public keys: [HOWTO: SSH & Public Keys]("http://http://ubuntuforums.org/showthread.php?t=30709").

If this machine is going to be accessible from the internet, then make sure it is firewalled and ssh is secured.  This is one of the best resources around: [Securing Debian Manual]("http://www.debian.org/doc/manuals/securing-debian-howto/").

I also recommend using a different terminal profile for each machine so you don't confuse your local machine with your server (which I have done).  You can add this to your .bashrc:
```
alias sshserver='gnome-terminal --window-with-profile=PROFILENAME -e "ssh user@domain.tld"'
```

Replace PROFILENAME with whatever your Gnome Terminal profile is and [email]user@domain.tld[/email] to your machine (can be an ip like user@192.168.1.153).  Restart bash with "source ~/.bashrc" and then type sshserver to launch your new ssh session with it's own Gnome Terminal profile.

---

### Post by FakeOutdoorsman on 2008-05-05
Since I'm a vile thread recycler; pros/cons of Ubuntu Server over some other distros: [Why Ubuntu Server?]("http://http://ubuntuforums.org/showpost.php?p=4403083&postcount=6")

And the compulsory link to the Ubuntu Wiki page on [Apache, php, mySQL]("https://wiki.ubuntu.com/ApacheMySQLPHP").

---

### Post by sp0nge on 2008-05-06
Great info here, thanks a lot for the help. I've just downloaded the server edition and will be burning it in just a moment. 

I would like to use this for my business ventures eventually, but I think I'll take the advice of toying with it for some time first- the same way I made the leap from windows when I first discovered Ubuntu.

---

### Post by ronag on 2008-05-06
> **scaredpoet said:**
> The primary difference between the server and desktop editions is that ubuntu server comes configured with ONLY the services you need to run a server.

It's more than just the GUI.  The Desktop edition comes with all the desktop software packages installed (FireFox, OpenOffice, GIMP, etc.), as well as printer sharing resources, bluetooth drivers, and tons of other stuff.  

A server on the other hand, typically doesn't need all these things.  presumably, you aren't going to be using a server as a desktop at the same time.  A production server's focus is just being a server, and oftentimes is sitting on a rack in a server room, where there isn't going to be a lot of direct mouse/keyboard interaction.  For this reason, it doesn't make sense to install the desktop packages, and that way the server can focus its memory, hard drive space and CPU resources on *just* the required server applications.

Is it possible to install the desktop items on a computer running server edition?  Absolutely.  But it's not considered very efficient to do so.

If you're absolutely new and want to try out running the server in a GUI environment, I would recommend installing the xubuntu-desktop package on top of the server edition software, as it's the "leanest" of the desktop GUIs.  You can do that by typing in:

```
sudo apt-get install xubuntu-desktop
```

But even with xubuntu, I'd consider this like training wheels, and the GUI is really just a comfortable crutch. At its base, you're still using text editors to configure everything, they just have a nice looking window around them and can be visually arranged. Eventually you'll want to ditch the GUI, especially if you plan on administering production servers.

This isn't to mean you're TOTALLY never using a windowing environment again, however. :)  A lot of people who run servers do it the way I do: we ssh in and make changes and such in a terminal window, on a remote desktop that IS using a GUI.  I'm regularly logged into my server using ubuntu desktop, Mac OS X, and (very) occasionally, a Windows machine with PuTTY installed.

Please excuse the dumb question...but how do I install xubuntu-desktop "on top of" Ubuntu Server edition?

I've installed the server edition, but really want the comfort of a GUI ...at least until I get comfortable.   I tried the command line as listed above, but just got an error message...couldn't find the file on E:\ (my CD rom drive).  

I had the Ubuntu Server disc in the drive at the time.  I've also downloaded and created the Xubuntu desktop CD, and tried the command line with that CD in the drive and still no luck...

Any help is greatly appreciated.

FYI, my purpose is similar to the original poster, I want to make a web/file server to host our web site.

Thanks in advance.

---

