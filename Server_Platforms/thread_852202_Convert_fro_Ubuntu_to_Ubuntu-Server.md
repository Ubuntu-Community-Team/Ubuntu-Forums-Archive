---
title: "Convert fro Ubuntu to Ubuntu-Server"
date: 2008-07-07
forum: Server Platforms
---

### Post by jcr1 on 2008-07-07
Hi all,

I currently have a server set up with just a regular install of Ubuntu (8.04). This is an old pc and struggles running all the gnome stuff, but the more I learn, the less I need to access the GUI stuff as I am doing most of my work via ssh on a command line. 

So now that I have the server set up more or less how I want it, I was thinking if I could convert it into ubuntu-server somehow and irradicate the gnome stuff to free it all up a bit?

Is it as simple as removing the gnome-desktop?

I also have xubuntu-desktop on there somewhere as it was originally a xubuntu setup, so i think there is a lot to remove...hopefully improving performance.

Or perhaps, is there an option to log into a session that does not load up any gui x session stuff, just a console is it?

Also... is any of this possible to do all thru ssh remote control?

Thanks in advance.

---

### Post by Titan8990 on 2008-07-07
You can remove the desktop with this command:

#apt-get purge ubuntu-desktop


This will not give you the server kernel. If this is a home server that probably will not be an issue.

Edit: yes, you can do this through ssh.

---

### Post by cdenley on 2008-07-07
> **Titan8990 said:**
> You can remove the desktop with this command:

#apt-get purge ubuntu-desktop


This will not give you the server kernel. If this is a home server that probably will not be an issue.

Edit: yes, you can do this through ssh.

I think that will just remove the meta-package. Maybe this will work better.
```

sudo tasksel

```

---

### Post by brambles on 2008-07-07
But be wary in Tasksel.If you just uncheck ubuntu desktop and click ok it WILL remove a huge tract of stuff. Make sure you add your server stuff or you may remove more than you bargained for - I speak from bitter experience :(

Cheers

M

---

### Post by jcr1 on 2008-07-08
what about "aptitude remove ubuntu-desktop" will that achieve the same thing? Once I have done that (remotely over ssh) I guess the thing will want to reboot...but just looking at a terminal, how will I know it wants to reboot? How will I log back in remotely?

I assume everything can be done from command line? Example, due to inexperience, I initially installed xubuntu, then could not find the system > preferences > remote desktop to enable remote desktoping, so installed ubuntu-desktop just to be able to do that! Sounds very daft I know, but I didn't know how else to do it. I assume this could have been done on a command line?

But like I said, most importantly, how will this go over ssh?

---

### Post by Titan8990 on 2008-07-08
I always use apt-get purge because from my experience apt-get remove leaves some config files which I usually like to get rid of.

---

### Post by dje on 2008-07-08
Have a look [here]("http://www.psychocats.net/ubuntu/purekde") for commands to fully remove both gnome and xfce

---

### Post by jcr1 on 2008-07-08
ahh lovely thanks for that link.

But lets say I will leave one...XFCE. But most of the time I will not need the GUI, only if I had to go and locally turn on a monitor to do something... Most of the time I just ssh in with a terminal, so it is pointless the server loading up and running any GUI.

Can I 'remotely' log out and back into a text / command line only session? 

Then if needs be reboot into an gui xfce...

Thanks for your help.

---

### Post by Titan8990 on 2008-07-08
That is a good question. I have done this on Fedora Core 8 with ease. After looking through my Ubuntu book it looks like it might be a bit tougher. I am interested in hearing if anyone knows how to do this without booting directly into single user recovery mode.

---

### Post by cdenley on 2008-07-08
To stop your X server
```

sudo /etc/init.d/gdm stop

```

To start your X server
```

sudo /etc/init.d/gdm start

```

To prevent your X server from starting automatically
```

sudo update-rc.d -f gdm remove

```

---

### Post by Titan8990 on 2008-07-08
Why is this so much different then just changing a runlevel in a distro like Fedora?

I can't undertand why ttyl 2-5 are all graphical...

---

### Post by cdenley on 2008-07-08
> **Titan8990 said:**
> Why is this so much different then just changing a runlevel in a distro like Fedora?

I can't undertand why ttyl 2-5 are all graphical...

Just the way debian distros are.
[http://www.debian.org/doc/FAQ/ch-customizing.en.html#s-booting](http://www.debian.org/doc/FAQ/ch-customizing.en.html#s-booting)

---

### Post by jcr1 on 2008-07-09
> **cdenley said:**
> To stop your X server
```

sudo /etc/init.d/gdm stop

```

To start your X server
```

sudo /etc/init.d/gdm start

```

To prevent your X server from starting automatically
```

sudo update-rc.d -f gdm remove

```


Will the stop command release the memory and resources that gnome was using? Is this the same command if I was running xfce?

How do I reverse the last command? i.e. if I wanted the system to return to automatically booting with X server?

Thanks for your replies!

---

### Post by windependence on 2008-07-09
> **Titan8990 said:**
> Why is this so much different then just changing a runlevel in a distro like Fedora?

I can't undertand why ttyl 2-5 are all graphical...

I thought it was weird as well since it isn't what we would call "standard" behavior. You CAN configure the runlevels to whatever you want to start though, so if you wanted to make it "standard" you certainly could. Just comment out the GUI start in the runlevel 3 script and you're good to go without a GUI. :)

-Tim

---

### Post by cdenley on 2008-07-09
> **jcr1 said:**
> Will the stop command release the memory and resources that gnome was using? Is this the same command if I was running xfce?

How do I reverse the last command? i.e. if I wanted the system to return to automatically booting with X server?

Thanks for your replies!

Looking at package dependencies, I think xubuntu-destkop also uses the gdm graphical login by default. Stopping gdm will kill the xserver and any graphical applications.

To make gdm start automatically
```

sudo update-rc.d gdm defaults 30 01

```

---

