---
title: "possible to share resources?"
date: 2011-02-06
forum: Server Platforms
---

### Post by MG2R on 2011-02-06
I don't know if this is possible, but if it is, that would be awesome!

I have an overpowered file server (1.66GHz dual-core intel atom with hyperthreading, only for file sharing and bittorrent) running Ubuntu 10.04 LTS, I also have a 4 year old laptop which is underpowered (1.8 GHz single-core AMD Athlon). Actually, the laptop works fine for regular use (e.g. checking e-mail, going on facebook, chatting, etc.) but fire up a youtube vid and 70-80% of the CPU is in use... GIMP same thing... VM is a mess.

I was thinking this: I have a monster of a CPU upstairs doing nothing, wouldn't it be great if I could use that cpu-time on my laptop (over my lan)? If it is possible to share resources, I would be very interested!

---

### Post by garfonzo on 2011-02-06
> **MG2R said:**
> I don't know if this is possible, but if it is, that would be awesome!

I have an overpowered file server (1.66GHz dual-core intel atom with hyperthreading, only for file sharing and bittorrent) running Ubuntu 10.04 LTS, I also have a 4 year old laptop which is underpowered (1.8 GHz single-core AMD Athlon). Actually, the laptop works fine for regular use (e.g. checking e-mail, going on facebook, chatting, etc.) but fire up a youtube vid and 70-80% of the CPU is in use... GIMP same thing... VM is a mess.

I was thinking this: I have a monster of a CPU upstairs doing nothing, wouldn't it be great if I could use that cpu-time on my laptop (over my lan)? If it is possible to share resources, I would be very interested!

It is possible to set up a cluster of computers to share resources. I've never done it before, but here's a link to get the mind thinking...

[Cluster HOWTO]("http://tldp.org/HOWTO/Cluster-HOWTO.html")

Cheers

---

### Post by rudelgurke on 2011-02-06
For what you want to do like Gimp, Youtube vids etc. - nope - it's useless trying to setup a Cluster.
Seems Flash doesn't fork into threads, Gimp can but most plugins not so there would be no real benefit running a cluster.
Not to forget that even if you get some more performance, you'll need a primary node for managing your cluster and other nodes being ready to handle tasks the primary node gives them. This needs performance too so you may have a 5% increase of a 4% overall loss.

---

### Post by MG2R on 2011-02-06
> **rudelgurke said:**
> For what you want to do like Gimp, Youtube vids etc. - nope - it's useless trying to setup a Cluster.
Seems Flash doesn't fork into threads, Gimp can but most plugins not so there would be no real benefit running a cluster.
Not to forget that even if you get some more performance, you'll need a primary node for managing your cluster and other nodes being ready to handle tasks the primary node gives them. This needs performance too so you may have a 5% increase of a 4% overall loss.

Well, the programs I mentioned are just to give examples... I just need some extra processing power when I'm running multiple programs/threads + I like experimenting and seeking the edge of what is possible :)
I'm going to look into that cluster thing, for better, or for worse :D

thanks!

---

### Post by elico on 2011-02-07
well it is possible but in this specific case it's on the edge...
atom vs athlon is pretty close.
what os are you using on the AMD?
atom cpu is not that a monster as you can think of it.
atom can do filesharing but also the AMD with no problem.
it depends on you Hardware and OS.
for my needs ATOM small-server is fine but as for a workstation that uses 20 tabs of firefox not a chance the atom will survive.
clustering... is about gaining more cpu power but you need to do some homework (most of the software you now is not built for this kind of usage)

---

### Post by SeijiSensei on 2011-02-07
You can run programs on the server and display the results on your laptop.

Use "ssh -X" from the laptop to the server to set up an X-Windows tunnel with SSH.  Then on the server, run a graphical program from the prompt with a trailing ampersand to put it in the background like "firefox &".  Firefox will start on the server; its display will pop up on the laptop.

---

### Post by MG2R on 2011-02-08
> **elico said:**
> well it is possible but in this specific case it's on the edge...
atom vs athlon is pretty close.
what os are you using on the AMD?
atom cpu is not that a monster as you can think of it.
atom can do filesharing but also the AMD with no problem.
it depends on you Hardware and OS.
for my needs ATOM small-server is fine but as for a workstation that uses 20 tabs of firefox not a chance the atom will survive.
clustering... is about gaining more cpu power but you need to do some homework (most of the software you now is not built for this kind of usage)

I'm running Ubuntu 10.04 LTS on both machines (64-bit desktop edition on notebook, 64-bit server edition on server). Hardware: notebook==>HP Pavilion DV 5075 / server ==> Asus AT3IONT-I deluxe motherboard (onboard ION graphics and Intel Atom 1.6GHz dual-core CPU) + 2GD DDR3 1066 RAM (and 4 hard disks totalling 5.25 TB)

[QUOTE=SeijiSensei]You can run programs on the server and display the results on your laptop.

Use "ssh -X" from the laptop to the server to set up an X-Windows tunnel  with SSH.  Then on the server, run a graphical program from the prompt  with a trailing ampersand to put it in the background like "firefox  &".  Firefox will start on the server; its display will pop up on  the laptop.[/QUOTE]

This would be exactly what I need and it looks way easier than clustering... I'll try it and keep you guys updated! 

Thanks to you all!

---

### Post by aeiah on 2011-02-08
i guess the moral of the story for next time is:

when splurging a load of cash on a high powered fileserver, consider buying a cheap one and using the spare cash to buy a new laptop too :p



ps - you could consider vnc or freeNX instead of ssh -X

---

### Post by MG2R on 2011-02-08
> **aeiah said:**
> i guess the moral of the story for next time is:

when splurging a load of cash on a high powered fileserver, consider buying a cheap one and using the spare cash to buy a new laptop too :p



ps - you could consider vnc or freeNX instead of ssh -X

Oh, the parts for the server weren't that expensive and I wouldn't have wanted anything else... The laptop is coming one of these months ;)

VNC needs a GUI to work with for as far as I know and wouldn't work on ubuntu server (or am I mistaking?)

---

