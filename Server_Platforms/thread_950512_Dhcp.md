---
title: "Dhcp"
date: 2008-10-17
forum: Server Platforms
---

### Post by DarkAlec on 2008-10-17
Hallo,

This must have been asked so many times but can't really find it so i thought just to ask...

I'm so new to Linux and after installing Ubuntu server on my server I had no idiee what i'm doing, but hey, thats what it's all about. I have also no exepriance in windows servers so this is where the fun starts.

1; how to know when the server is on the network after fresh install and boot up?

2; if not, how to set it up?

3; then how to setup DHCP?

Please note...I have no idiee how so if possible don't skip lines:lolflag:

Oh yes, if possible, how to load a GUI so just for now I can learn how it all works.

---

### Post by drakkus on 2008-10-17
if you've never done it before i hope your setting it up on a home pc rather then in a live office :)

On another point, if i was you i would install a client version of ubuntu first, and play around with that.. so you actually know what linux looks like, how to use the terminal and all the other key points to linux, then afterwards play around with setting servers up on a client version, theres no reason u cant...

trying to go full whack into being a whiz kid with any linux server os isn't really gonna work to well unless you know the roots of what you are doing and handling first of all lol.

---

### Post by lykwydchykyn on 2008-10-17
> **DarkAlec said:**
> Hallo,

1; how to know when the server is on the network after fresh install and boot up?

The command to see networking information is:
```

sudo ifconfig 

```
If you see an entry for eth0 and it has an IP, then you should be on the network.  You can try pinging a few things like google or yahoo to make sure everything is working ok.
> 
2; if not, how to set it up?

Typically you want your server to be on a static IP.  You just need to edit the file /etc/network/interfaces, and have it say something like this:
```

auto eth0
iface eth0 inet static
  address 192.168.1.100
  netmask 255.255.255.0
  gateway 192.168.1.1

```
Obviously,those numbers will be dependent on your network setup.  Once you've done that, just restart networking:
```

sudo invoke-rc.d networking restart

```
> 
3; then how to setup DHCP?

You mean how to set up a DHCP server, or to make your server get a DHCP address?

> 
Please note...I have no idiee how so if possible don't skip lines:lolflag:

Oh yes, if possible, how to load a GUI so just for now I can learn how it all works.

Assuming your network is connected, you can install a gui like so:
```

sudo aptitude install xorg gdm gnome
sudo invoke-rc.d gdm start

```

That will get you a GUI, but that may not be much help.  Most configuration is done by editing files and using commands.  Though, admittedly, that's nicer to do in gedit and gnome-terminal than nano and a virtual term.

---

### Post by DarkAlec on 2008-10-17
lykwydchykyn; from all i have read on the GUI topic, that was 500% thanks!!!!!!!!! i would say that is all for knowledge and will break it so i can fix again....:lolflag:

will try the rest later....and yes, I want to set up so server run as my DHCP!!!

do u maybe know how to set up a Dedicated COD4 server on LINUX. hosting our clan server but want learn to host on LINUX!!!

G_WIZZ...GUI still unpaking and loading...understand what u meen now:lolflag:

---

### Post by DarkAlec on 2008-10-17
sudo invoke-rc.d gdm start did not work so i did "startx" worked but loaded with error in GUI mode "the pannel encounter a problem while loading" ; "OAFIID:GNOME_FastuserSwitchApplet"

"don't delete" or "delete"

i'm going to not del

---

### Post by lykwydchykyn on 2008-10-17
Did the first command complete without errors?

---

### Post by DarkAlec on 2008-10-18
well i think so......not sure!!!!!!!!!!

---

### Post by lykwydchykyn on 2008-10-18
Run it again and paste the output here.

---

### Post by DarkAlec on 2008-10-20
will do!!!!

---

### Post by DarkAlec on 2008-10-20
To be honest lets forget the GUI, its just (I think) a waste of time, it seems to me you can do more and faster when you have no GUI&#8230;.realy wanted to try and run COD4 dedicated server and lost badly:(:lolflag:don't even know how to create or edit shortcut...
I think the best way to go is I say what I want to do and you tell me the best way to do it and then stick with that&#8230;I&#8217;m the guy that just want to do to much at once&#8230;

I think the best way to start is with the simple File sharing FTP server&#8230;what you think?

---

### Post by egeneral27 on 2008-10-20
hey you can have a gnome desktop by typing the following command:

```

sudo apt-get install ubuntu-desktop

```

considering that you have a fast internet connection, this setup would only take 10-15 mins... after that you will find yourself in an environment similar to that of the desktop edition....

i haven't configured dhcp on my server though...

cheers!

---

### Post by koenn on 2008-10-20
dhcp server in 12 seconds :
[http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm#dhcp](http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm#dhcp)

or you could run tasksel - maybe there's an option to set up dhcp

---

