---
title: "SSH tunneling for SlimServer"
date: 2006-05-17
forum: Server Platforms
---

### Post by SlugO on 2006-05-17
First of all, shame on me :-# I study computer science and have completed a course on information security but still don't know how to do SSH tunneling. Obviously I've been sleeping :D

So I got [SlimServer]("http://www.slimdevices.com/") 6.5b running from the repositories. I got one friend to succesfully hear the /stream.mp3 on his computer and for the other one it didn't work. [SoftSqueeze]("http://softsqueeze.sourceforge.net/") hasn't worked for them yet. I read that it is highly recommended to use SSH tunneling when listening to music across internet connections so I should probably get that running.

Softsqueeze says that these thing are needed:
>     *  An SSH server running on the same machine as your Slimserver
    * A Router/Firewall listening to a specific port for SSH (Typically port 22)
    * A Router/Firewall forwarding that port to the machine running SSH and Slimserver
Most Linux and BSD distros have SSHD running by default. It is recommended that you make a few changes to the default configuration. A good guide to basic SSHD setup can be found at: [http://geodsoft.com/howto/ssh/servers.htm](http://geodsoft.com/howto/ssh/servers.htm).
Doesn't seem too complicated. But I just need to know how to get the SSH server running and configured properly on Ubuntu. That guide provided on Softsqueeze's site is quite far from easily understandable... So help would be appreciated :)

---

### Post by it.henrik on 2006-05-17
have a look at hamachi instead .. its zero conf

---

### Post by SlugO on 2006-05-17
Well I'm not really trying to setup a whole virtual LAN here. Just a way to access my music from other computers.

---

### Post by cvmiller on 2006-05-17
[QUOTE=SlugO]Well I'm not really trying to setup a whole virtual LAN here. Just a way to access my music from other computers.[/QUOTE]

Setting up sshd couldn't be easier ( just use synapsis to install it). Or at least it was that simple for me. It even started sshd for me.

Doing the tunneling is a bit more fun, but not all that hard. I use it at home all the time. After you get ssh installed, read the man page, look at the -L parameter.

BTW, Hamachi looks interesting, but it involves a third party, and it isn't open source (which rules it out for me, as I run Ubuntu on PPC).

I hope this helps,

Craig...

---

