---
title: "GUI monitoring for server"
date: 2010-04-08
forum: Server Platforms
---

### Post by vladoportos on 2010-04-08
Hello all,

could somebody advice me, I have my ubuntu "server" running at home in rack box, and front door is transparent plastic... and inside is also LCD panel plugged to server, now it only shows command line ( log in prompt ), there is no X installed on server.

What I want is to show on this LCD is information about server, whats going on, how much ram, how much CPU, network and so on... in some cool way, because it is in room and always on display...  I would not mind to install X on this sever but not whole gnome or something like that... is there any light version specific for this... also I would not like to have to run it as root or something so somebody can open box, cancel monitoring and mess with system...

Not sure if I made myself clear, but I hope so.... 

I really appreciate all hints and links for something useful...

Many thanks
Vlad

---

### Post by dudumomo on 2010-04-08
Interesting thread.
It seems possible to do so.

May be by doing a script with several different command in it.

By example, the command "top" will give you your RAM, SWAP, CPU, usage and from which process.
Network I don't really know...Do need to know the data transfered ? the speed ? your IP ?

If you want a light gnome version you can install gnome-core (It will install only gnome with a couple of dependencies). If you don't want gnome, I recommand you fluxbox very light.

But actually, what you are looking for, is a "conky" for your server.
Check mine:
My conky: [http://img223.imageshack.us/i/capture1lh3.png/](http://img223.imageshack.us/i/capture1lh3.png/)

But this was on my laptop. (You need X to do that)
Don't know if there is an alternative solution to conky without X.

---

### Post by CharlesA on 2010-04-08
You'd more then likely need to be logged in to view that sort of information. If you have something set to autologon to an X environment, that is not totally secured would be a problem.

You could try installing Webmin and accessing it from another machine, but it won't display anything on the LCD in the rack.

---

### Post by cdenley on 2010-04-08
What version?
```

lsb_release -d

```

---

### Post by Menthu_Rae on 2010-04-08
```
sudo apt-get install htop
```

[IMG]http://img534.imageshack.us/img534/9434/htop1.png[/IMG]

Sweet as :P

---

### Post by dudumomo on 2010-04-08
htop is not bad.
Anything for the network ?

---

### Post by cdenley on 2010-04-08
> **cdenley said:**
> What version?
```

lsb_release -d

```

You never answered me. I will assume 9.10. This will not work on 8.04.

1. Disable getty on tty1
/etc/init/tty1.conf
```

# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

**[COLOR="Red"]#[/COLOR]start on stopped rc RUNLEVEL=[2345]**
stop on runlevel [!2345]

respawn
exec /sbin/getty -8 38400 tty1

```

2. Create an upstart service to start htop at boot
/etc/init/htop.conf
```

start on (filesystem and tty-device-added KERNEL=tty1)
stop on runlevel [016]

respawn
exec /usr/bin/htop>/dev/tty1</dev/full

```

3. reboot

This will not be interactive, and will not be run in a shell, so I don't see any security problems. For networking, you can look at atop, or create a simple script which uses netstat.

---

