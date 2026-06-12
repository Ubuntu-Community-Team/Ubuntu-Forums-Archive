---
title: "should I change to &quot;linux-server&quot; kernel"
date: 2008-04-11
forum: Server Platforms
---

### Post by jackocleebrown on 2008-04-11
Hello,

I have a couple of computers that I use as basic servers. Nothing more complex than file server + slimserver (audio server). I installed these using Ubuntu desktop edition (mostly version 7.10) just because I had the disk around, it is also quite handy to have GNOME too on occasions where my terminal skills fail me. Now they are setup and running they are headless and I rarely change settings and mostly use ssh (occasionally NX) if I do need to.

I had to downgrade the hardware on one of the machines (due to a catastrophic mobo failure). The replacement machine is noticeably more sluggish to respond. I was wondering if it would be a help to install the "linux-server" package and use this kernel instead of the "linux-generic" that they are using now. Is the "linux-server" kernel significantly different from the generic one?

Thanks, Jack

---

### Post by Deathrend on 2008-04-11
I really can't say baised on what I know about Linux/Ubuntu Kernels, however I can speak from a server standpoint

A general kernel stads to have more errors/holes/general open spots, because it's compiled to work with pretty much anything and everything, where as a normal server kernel, they're ment to run for months at a time, only going down for updates, and also not having programs installed/removed constantly.  Generally servers have fewer memory leaks as well because of how they're made.  

With that bing said, it could be the same Kernel, however I'm guessing that it's just a cleaner kernel that's ment to run forever with little down time, which is harder to come by iwth a normal desktop system (Most of which reboot on a nightly/weekly basis).

---

### Post by songshu on 2008-04-11
you could.

if its a home server then you could save yourself the trouble because i think you would not notice much difference..

on the other hand its just a few minutes work to install the server kernel.

don't know what you are running but i think the server kernel lacks support for the restricted graphical drivers that you are not using anyway

---

### Post by jackocleebrown on 2008-04-14
Thanks for the advice,

I've installed the linux-server kernel package and rebooted the machine in question... Unless I am deluding myself it does seem usefully more responsive than it was - particularly on serving the http page to control the audio server, Excellent.

Jack.

---

### Post by hyper_ch on 2008-04-14
the server kernel is more geared towards serving as server... :)

---

### Post by ikonia on 2008-04-14
which in turn means less support for desktop kit (no restricted drivers etc)

---

### Post by hyper_ch on 2008-04-14
not sure about restricted drivers...

but then, who runs a gui on a server anyway?

---

### Post by ikonia on 2008-04-14
a lot of people want it, and they want things like wirless drivers, this is because a.) people run a server on a bit of home kit, so use their home technologies like wirless b.) want a gui because they don't know how to run the server c.) think only the server version can serve "things"

If you had to post on this forum asking what to do with gui's how to install etc etc, you should be using the desktop version to run your services.

If you running on home PC hardware, use the desktop version.

---

### Post by Deathrend on 2008-04-14
> **ikonia said:**
> If you running on home PC hardware, use the desktop version.

That statement isn't right at all, more so with older desktop equpment.  I currently have two PIII 1ghz PC's, one with FreeNAS, the other with Ubuntu 7.10 server.  There's no way it would load a desktop, atleast weel.  With a server OS it runs faster than it's ever.  

On the other end of that, I have an HP Dl580 G@, an older verson of one of the biggest (Non-Superdome) servers HP makes, sporting Quad 2.4Ghz Xeons, with 16 Gb of RAM.  This would easily support a GUIed OS, however it's running Ubuntu Server 8.04.

Just because it's a server platform, doesn't mean it /has/ to be a non-desktop platform, as well as jut because it's a desktop, doesn't meen it will only run the desktop version.  

Now, if you want to see a grown Linux-Expert cry, I work on HP servers on a daily basis, the flagships of our network being Four(4) HP Superdomes, fully loaded 64 Dule Core Itanum Processors, with Two(2) Terabytes of hot swap ram, all controled by Windows 2003 Datacenter 64.  I say this, because it's an OS that shouldn't be on a server like this normally, however people use what works for them, be it a CLI server OS, or a GUI Desktop/Server OS.

---

### Post by ikonia on 2008-04-14
I didn't say it "HAD" to be a server hardware, I'm saying the majority of people will run it on a home PC and will be better off with the desktop version for things like graphics/network card drivers.

I have old kit running desktop versions, it's all down to personal taste.

I am generalising about the mass majority, not saying everyone using a PC must run desktop edition.

---

