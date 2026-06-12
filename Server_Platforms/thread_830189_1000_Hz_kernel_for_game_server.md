---
title: "1000 Hz kernel for game server"
date: 2008-06-15
forum: Server Platforms
---

### Post by CarVac on 2008-06-15
I'm trying to recompile my kernel so that it has a 1000 Hz tickrate. This is for getting the Source Dedicated Server running at 1000 frames per second. Is there any way to tell if it is 1000 Hz? The server runs at 250 fps, indicating (I think) that the kernel is also 250 Hz. I tried to use 'make menuconfig' and editing the config files in ubuntu-hardy/debian/config/amd64. Is this the proper way? I'm using Xubuntu Hardy (and will later use a server edition).

---

### Post by kevmitch on 2008-06-15
[QUOTE] The server runs at 250 fps,[\QUOTE] 
What do you mean by this? Where does it say that?

[QUOTE]I tried to use 'make menuconfig' and editing the config files in ubuntu-hardy/debian/config/amd64. Is this the proper way?[\QUOTE]

Yes, that will work for you, however you want first to be sure that you're looking at the configuration of the running kernel. To ensure this run 

```

cp /boot/config-`uname -r` /usr/src/linux/.config
cd /usr/src/linux && makemenuconfig

```

Under **Processor type and features** you'll find a "Timer Frequency" setting. You might also want to disable "Tickless System (Dynamic Ticks)" (though I could be grossly wrong on that one). Also of interest might be "Preemption model" and "Big Kernel Lock". Of course you will have to recompile the kernel ([http://newbiedoc.sourceforge.net/system/kernel-pkg.html](http://newbiedoc.sourceforge.net/system/kernel-pkg.html)) if you actually want to change something.

If you just want to see what your system is running without changing it,

```

grep HZ /boot/config-`uname -r`

```

---

### Post by windependence on 2008-06-16
IMHO you should just run the desktop version. Just because it says "server" on it doesn't mean it will make a good game server. I don't think there are any benefits to you using the server version for a game server. Most of the server "features" are geared toward things like web servers, DB servers, VMs, and files servers. JMHO. Of course YMMV.

-Tim

---

