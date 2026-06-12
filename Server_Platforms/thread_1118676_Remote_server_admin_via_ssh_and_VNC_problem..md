---
title: "Remote server admin via ssh and VNC problem."
date: 2009-04-07
forum: Server Platforms
---

### Post by mramsey on 2009-04-07
OK I have an issue.  I prefer to use a gui interface to admin my server. I am running ubuntu server 8.10 and installed xcfe for the gui and onlt start the x when remotly logging in. 

I connect locally via ssh then launch tight VNC for the remote the desktop. Everything launches fine and I get the desktop but I have no functionality as far as right click menus. the cursor moves correctly I just cannot get any other functions to work. 

Any Ideas??  :-k

---

### Post by madverb on 2009-04-07
Try with a different VNC Client?

---

### Post by HermanAB on 2009-04-07
This comes up every week or two on these forums.  If you have SSH working then you ***don't need VNC***.  Leave the server in runlevel 3 (no X server needed) and connect to it like this from another machine:
```
$ ssh -X -C -c blowfish user@server gnome-panel
```

and go click happy.

The other machine can be Linux or Windows.  The only requirement is that it must have X and SSH.  For Windows use Xming and PuTTY to connect to the server.

---

### Post by redonwhite on 2009-04-07
> **HermanAB said:**
> This comes up every week or two on these forums.  If you have SSH working then you ***don't need VNC***.  Leave the server in runlevel 3 (no X server needed) and connect to it like this from another machine:
```
$ ssh -X -C -c blowfish user@server gnome-panel
```

and go click happy.

The other machine can be Linux or Windows.  The only requirement is that it must have X and SSH.  For Windows use Xming and PuTTY to connect to the server.

what is runlevel 3?

---

### Post by BkkBonanza on 2009-04-07
[http://en.wikipedia.org/wiki/Runlevel](http://en.wikipedia.org/wiki/Runlevel)

Now I'm curious what a minimal install of X server for above takes in RAM usage? Herman or anyone know?

---

### Post by kbtarl on 2009-04-09
> **redonwhite said:**
> what is runlevel 3?

Yes can you tell us more about this? I've been wanting to make a new server using the server edition instead of the desktop but have been intimidated by the Command line as I have not learned linux that well. I would like to have the clean dedicated functionality of a server but with a GUI. I was thinking about webmin. If I can log in through SSH and on command get a gnome interface that is great!

Care to point me toward more information or tutorials about this?

---

### Post by BkkBonanza on 2009-04-09
When a linux machine boots it chooses what runlevel to use. This determines what boot sequence is run and what apps will be up and going. Runlevel 3 is typical for multi-user but non-gui (no X) support and is usually used on servers.

Webmin is not a gui as it is a simple web based interface. No gui components are installed on the server since it's interface is provided entirely by http and the web server. What Herman above is saying is that after you setup your server install of Ubuntu you can apt-get to install X. Then you can use the -X feature of ssh to do X forwarding and run the gui remotely.

As for tutorials - G O O G L E: X forwarding tutorial

For server admin the only real advantage I see here is being able to use a nice editor rather than the cumbersome console based ones. Most of the server management is done through config files anyway. The easy but shallow approach is to use Webmin.

---

### Post by HermanAB on 2009-04-10
Ubuntu runlevels are controlled by upstart in /etc/event.d/rc-default.

Runlevel 3 is the normal level for a server - no X and no GUI.  You can use ssh to connect to a server and let any program that needs X, forward its graphical rendering requests to the local machine X server.

```
So you can do things like:
ssh -X -C -c blowfish user@server gnome-panel

or
ssh -X -C -c blowfish user@server "gedit /etc/fstab"
```

and the program will appear to run seamlessly on the local desktop while actually executing remotely.  That even works from a Windows machine if you have Xming and PuTTY installed.

---

