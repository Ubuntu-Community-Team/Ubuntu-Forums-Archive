---
title: "I broke my server :("
date: 2012-09-01
forum: Server Platforms
---

### Post by daz1uk on 2012-09-01
Hi,

I installed ubuntu-desktop on top of my 12.04 server install in order to easily activate the ATI drivers.

I then used tasksel to remove ubuntu-desktop and restarted my machine, it is now broke.

I have tried fixing dependencies to no avail, on boot it seems to stall on starting the apache web server although i'm not completely sure as the message isn't printing on the screen properly.

Any ideas of how to fix this without a re-install?

---

### Post by Lars Noodén on 2012-09-01
Can you get to a console by pressing ctrl-alt-f1 etc?

---

### Post by daz1uk on 2012-09-01
Yeah I can, :)

Looks like I'm going to have to re-install ubuntu-desktop now anyway. 

I'm trying to run a server setup for me, that runs xbmc as a front end for the Mrs, hence installing the desktop in the first place for the drivers. 

Now I have an issue with no sound so it's seeming that it may be simpler to leave the desktop on there?

---

### Post by TheFu on 2012-09-01
As Lars suggests, you need to get to a shell interface on the machine.  Either getting to a different console alt-F1, alt-F2, ..... might work.

Another option is that you can ssh into the box from another to get to a shell interface and reinstall that GUI stuff.

A few other related thoughts.
* Loading a GUI onto a server has historically make the server less stable.  X/Windows has bugs, Video drivers have bugs. They can crash servers.
* If you do want/need a GUI, load the smallest one that works and avoid GPU acceleration - which seems to be the buggiest code.  I've used LXDE.  (sudo apt-get install lxde) ; don't load the entire lxde-desktop, just the interface.

Having a Linux server means using the shell. Live it, know it, love it. ;)

--- update ----
Running XBMC on top of a "server" makes this into a media center that happens to share files.  I'm a long time XBMC user too, but that is a different question for a different thread.  I don't think you need a "desktop" to load XBMC as xbmc-standalone will handle that.

---

### Post by daz1uk on 2012-09-01
Yeah, best of both worlds didn't work out so well.

Thanks for the advice guys, I know how i'm going to proceed from here. It involves a format ; )

---

### Post by sandyd on 2012-09-01
just do this after you install the server again.

```

sudo apt-get install xorg-server
sudo add-apt-repository ppa:team-xbmc/ppa
sudo apt-get update
sudo apt-get install xbmc-ppa-keyring
sudo apt-get install xbmc

```

Now, get it to automatically login to an already existing user.
```

sudo apt-get install mingetty
sudo nano /etc/init/tty1.conf

```

Replace the line that starts with
```

exec /sbin/getty

```
with
```

exec /sbin/mingetty --autologin USERNAME tty1

```
where username is the name of the user.

I myself used a different setup at this point, as XBMC was a bit cranky without pulseaudio.

However, you can just add xbmc to ~/.profile , and it will run on login.

In case you run into the same audio problems that I did, run xbmc on top of openbox

```

sudo apt-get install openbox

```

```

nano ~/.xinitrc

```

At the bottom of the file, add
```

exec openbox-session
```

Now, start openbox once.
```

startx
```

Exit by right clicking, and choosing "quit"

Now, add xbmc and pulseaudio to the openbox startup
```

nano ~/.config/openbox/autostart
```

place this inside.
```

#!/bin/bash
pulseaudio -D
sleep 10
xbmc
shutdown -h now

```

Allow shutdown without password
```

sudo chmod u+s /sbin/shutdown

```

Note that much of this is from memory - might require some tweaking.

---

### Post by daz1uk on 2012-09-02
Thanks sandyd, it's now working great.

---

