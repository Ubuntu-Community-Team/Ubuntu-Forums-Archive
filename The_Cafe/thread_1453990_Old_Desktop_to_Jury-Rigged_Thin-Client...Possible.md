---
title: "Old Desktop to Jury-Rigged Thin-Client...Possible?"
date: 2010-04-14
forum: The Cafe
---

### Post by chessnerd on 2010-04-14
I have a 14 year old computer that I've been trying to think of something to do with. The specs are pretty sad: 200 MHz Pentium I, 32 MB RAM, 4 GB HDD, so even DSL or another really small GUI distro didn't seem too promising. After all, even a normal web page would suck up all the RAM. So far, my best idea had been a CLI-only workstation, but that seemed, well, boring.

Then, I thought about, maybe, using the computer as a jury rigged thin-client-esque machine.

I would install a minimal, CLI distro and give it the smallest window manager I could find. I would then give it only one GUI program: a VNC client. Then, I would SSH into another desktop running Linux and use the VNC client to run all of the programs off of that machine. Then, two people could use the same computer at the same time, doubling the abilities of said computer. 

My question is, would this type of a setup even be possible? 

If so, would it be possible on that hardware? (The other computer would have a 2.8GHz Pentium 4, 1 GB RAM, and a 120 GB HDD)

Also, can you think of any better/easier/more efficient way to do this?

---

### Post by samalex on 2010-04-14
You could run something like [DSL]("http://www.damnsmalllinux.org/") or [Xubuntu]("http://www.xubuntu.org/") which both work really well on smaller systems.  

A command line only system would be great, and with that you could even install Ubuntu Server and install any extra bells and whistles using apt-get. 

[Here's a thread]("http://ubuntuforums.org/showthread.php?t=1453527") I started yesterday with some thoughts on running a productive system from shell only (no GUI), and I'm thinking of expanding this abit on a website once I have time to put it together.

But using one of these smaller distros you can run RDP or VNC to connect to other systems if you'd like, But even at 200Mhz you can still have a productive system though Flash and video playback might not work all that well.

Take care --

Sam

---

### Post by The Real Dave on 2010-04-14
I'd take a look at [KMandla's blog]("http://kmandla.wordpress.com/") if I were you, before making it just a VNC machine. 32Mb of RAM can be worked with :) You just need to change how you work ;) DSL and TinyCore will both work perfectly on there, as will Slax, Crux and [KolibriOS]("http://www.kolibrios.org/")

---

### Post by fromthehill on 2010-04-14
you could install something like ubuntu-server or arch with a window manager like twm

---

