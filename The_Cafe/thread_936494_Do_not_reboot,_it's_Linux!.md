---
title: "Do not reboot, it's Linux!"
date: 2008-10-02
forum: The Cafe
---

### Post by medic2000 on 2008-10-02
In this topic i want the help of community. We will find what services are needed to be restarted after specific tasks. My friend who reboots so much his ArchLinux gave me the idea that many users doesnt know which services should be restarted to avoid rebooting the whole system.

First comes from me;
If you changed "DNS" or something about network you need to do:

```


sudo /etc/init.d/networking restart


```

from knattlhuber:


Stop and restart the Display Manager:
```

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

```

to mount a drive that you just added to /etc/fstab:

```


sudo mount -a


```

From InfinityCircuit:

If you install firmware for a wireless device, you shouldn't have to reboot. Just:

```


sudo modprobe -r ipw2200
sudo depmod -a
sudo modprobe ipw2200


```

From Lux Perpetua:

X server catch-all : 

```
<Ctrl> + <Alt> + <Backspace> (which simply kills the X server and restarts it)
```

If you add a new printer or modify something in printers.conf, you can run

```

sudo /etc/init.d/cupsys restart

```

and your applications will show the updated list of printers.

---

### Post by knattlhuber on 2008-10-02
Stop and restart the Display Manager:
```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

Not really a "restart" but kinda:
```
sudo mount -a
```
to mount a drive that you just added to /etc/fstab

---

### Post by david_lynch on 2008-10-02
> **medic2000 said:**
> In this topic i want the help of community. We will find what services are needed to be restarted after specific tasks. My friend who reboots so much his ArchLinux gave me the idea that many users doesnt know which services should be restarted to avoid rebooting the whole system.

First comes from me;
If you changed "DNS" or something about network you need to do:
"**sudo /etc/init.d/networking restart**"
+1 

good advice - I've currently got a dozen or so linux servers in production with uptimes of over 770 days. No need to go rebooting linux all the time.

---

### Post by Joeb454 on 2008-10-02
Usually the only thing I need to reboot for is a hard lockup - which is very very rare, and usually my fault - or a kernel upgrade

---

### Post by chungy on 2008-10-02
Well, there's (re)starting a service or two which isn't a particularly difficult task even though many people might reboot; then there's the unloading/loading of dozens of kernel modules.... unless you have some other service that must be up as long as possible, you might as well just reboot.

---

### Post by HyperHacker on 2008-10-02
Yeah, I'm sure when something weird happens (like Thunar refuses to launch and after logging in again you have no desktop), you could fix it without rebooting, but realistically, hours of Googling/reading manpages for solutions and trying random things, or minutes rebooting? For a desktop where 24/7 uptime isn't important, it's a simple choice.

That said, it is good to know how to fix things without rebooting. Often just logging out and in again fixes things; it's like rebooting, but faster.

---

### Post by Bungo Pony on 2008-10-02
> Often just logging out and in again fixes things

That's usually what I end up doing. I almost never reboot unless I feel the need to reboot into Windows for something.

---

### Post by schauerlich on 2008-10-02
I dual boot with OS X, so I reboot fairly often.

---

### Post by niccholaspage on 2008-10-02
I haven't rebooted for a VERY long time. Is there any way to remove that Restart Icon that bugs you after an update?

---

### Post by Saint Angeles on 2008-10-02
what i find really annoying is when there is a problem with the internet in our house. The router is in my housemates' room and when i ask them about whats going on with the router and if the internet is working for them, i usually get a response like "well did you try restarting your computer?"

i try to explain how linux almost never needs a restart but people that have been using windows all their lives really never understand.

---

### Post by Frak on 2008-10-02
Debian Sarge server, been up for 2 years without reboot.

---

### Post by knattlhuber on 2008-10-02
> **EDavidBurg said:**
> I dual boot with OS X, so I reboot fairly often.

There's an easy way to circumvent the need for a reboot into Mac OSX. It involves the *fdisk* command :D

---

### Post by DarkDancer on 2008-10-02
> I dual boot with OS X, so I reboot fairly often.

Hehe, Hibernate, you get to keep your up time and don't have to end any programs (though you may want to pause any video or music playing (you don't even have to do that, but when coming back it can be a bit weird at first)) ;).

---

### Post by schauerlich on 2008-10-02
> **knattlhuber said:**
> There's an easy way to circumvent the need for a reboot into Mac OSX. It involves the *fdisk* command :D

I'm happy with OS X, thank you very much :)

---

### Post by schauerlich on 2008-10-02
> **DarkDancer said:**
> Hehe, Hibernate, you get to keep your up time and don't have to end any programs (though you may want to pause any video or music playing (you don't even have to do that, but when coming back it can be a bit weird at first)) ;).

My uptime is 15 days at the moment, and OS X is running beautifully.

---

### Post by knattlhuber on 2008-10-02
> **EDavidBurg said:**
> I'm happy with OS X, thank you very much :)

No offense meant, David. Been on OSX for 7 years. :)

---

### Post by -grubby on 2008-10-02
> **knattlhuber said:**
> No offense meant, David. Been on OSX for 7 years. :)

His name is actually eric

---

### Post by InfinityCircuit on 2008-10-02
If you install firmware for a wireless device, you shouldn't have to reboot.  Just:

```
sudo modprobe -r ipw2200
sudo depmod -a
sudo modprobe ipw2200
```

Personally, my servers are Xen domUs, so I never have to reboot a physical system...

---

### Post by vishzilla on 2008-10-02
A simple one (for new users) after installing new apps and the app launcher doesn't show up in the menu
```
killall gnome-panel
```

---

### Post by WWSmith36 on 2008-10-02
What is commmand to determine when the last system boot was ?

---

### Post by knattlhuber on 2008-10-02
> **WWSmith36 said:**
> What is commmand to determine when the last system boot was ?

```
cat /proc/uptime
```

gives you the time in seconds.

---

### Post by PointyWombat on 2008-10-02
> 
What is commmand to determine when the last system boot was ?


```
# who -r
```

or

```
# uptime
```

---

### Post by RiceMonster on 2008-10-02
When I had no Windows partition (I require windows for school, so I'm dual booting right now) I would almost never reboot; just when I had a kernel update. Instead of shutting down, I would suspend or hibernate. Now I shut down so I can access my Linux partition from Windows. I keep a bunch of my music there, so and I like to listen to music sometimes while doing work.

---

### Post by Dale61 on 2008-10-03
> **joeb454 said:**
> usually the only thing i need to reboot for is a hard lockup - which is very very rare, and usually my fault - or a kernel upgrade

+1

---

### Post by binbash on 2008-10-03
I like seeing my usplash i reboot often for fun : )

---

### Post by mrgnash on 2008-10-03
I rarely reboot, but I might take my system down to runlevel 1 on occasion ;)

---

### Post by FuturePilot on 2008-10-03
> **Frak said:**
> Debian Sarge server, been up for 2 years without reboot.

That's :shock:

---

### Post by Bachstelze on 2008-10-03
> **medic2000 said:**
> 
First comes from me;
If you changed "DNS" or something about network you need to do:
"**sudo /etc/init.d/networking restart**"

Changes of DNS servers apply automatically and don't need any further manipulation, not even that.

---

### Post by Bachstelze on 2008-10-03
> **Frak said:**
> Debian Sarge server, been up for 2 years without reboot.

OpenBSD 3.4 server, was up for four yers but I rebooted it recently to upgrade to 4.3.

---

### Post by epidemiks on 2008-10-03
well I like paying less for electricity, so mine goes off every night unless im leeching/seeding something :)

---

### Post by Ioky on 2008-10-03
I usually shut down my computer. Therefore it is kind of a reboot all the time. haha. I don't want to leave it on when I don't need it because more or less dust will go in. and I hate dust

---

### Post by medic2000 on 2008-10-03
Hey community! We should suggest the services for not rebooting remember? :)

---

### Post by SunnyRabbiera on 2008-10-03
I reboot once in a blue moon, sometimes during system hiccups (that I get every so often, 3 out of 10 times. Windows is much higher at 8 out of 10 times)
and when I have to reset my net connection

---

### Post by Lux Perpetua on 2008-10-03
X server catch-all : <Ctrl> + <Alt> + <Backspace> (which simply kills the X server and restarts it)

If you add a new printer or modify something in printers.conf, you can run
```
sudo /etc/init.d/cupsys restart
```and your applications will show the updated list of printers.

---

### Post by forrestcupp on 2008-10-03
> **epidemiks said:**
> well I like paying less for electricity, so mine goes off every night unless im leeching/seeding something :)

+1

Some people shut their computers down to save on electric bills and greenhouse gases.  It's not all about uptime unless you're talking about a company network.  And I've had just as long of uptimes in Vista that I have had in Ubuntu.

---

### Post by klange on 2008-10-03
Why shut down when you can hibernate? (which actually is shutting down, but keeping your entire session available immediately upon restart)

Personally, I suspend my laptop all the time.

---

### Post by Dr Small on 2008-10-03
I never shutdown or reboot unless absolutely necessary. Why, Dad was hooking up a new cable in the electrical panel the other day, and was going to disconnect the power first. He said that we should turn off our systems, but I left mine on and running on battery backup :)

---

### Post by Frak on 2008-10-03
> **FuturePilot said:**
> That's :shock:

> **HymnToLife said:**
> OpenBSD 3.4 server, was up for four yers but I rebooted it recently to upgrade to 4.3.

I just recently found my Sarge server in the backhouse, so I'm guessing about 2 years. The UPS was still going, so I guess it's time to use it for something.

---

### Post by medic2000 on 2008-10-07
What shall we restart after changing groups?

---

