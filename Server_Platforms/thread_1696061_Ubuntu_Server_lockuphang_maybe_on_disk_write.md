---
title: "Ubuntu Server lockup/hang maybe on disk write"
date: 2011-02-26
forum: Server Platforms
---

### Post by Mizutsuki on 2011-02-26
Hello,

I have a little tiny computer that I am trying to set up as a seedbox, and I'm having some trouble.

I believe that it is the same thing or close to this one:
[http://www.igologic.com/products/Product.aspx?ProductID=24]("http://www.igologic.com/products/Product.aspx?ProductID=24")

It should also be noted that I am using a converter with compact flash instead of a laptop hard drive.

The problem is that the system is locking up very badly.  It's a little difficult for me to say exactly when the system locks up, but it happens when I am doing something, not when the system is idle.

So I've tested some things.  I've installed 10.10 server edition 32 bit maybe 6 times, and every time it's been smooth sailing.  I've installed with and without LVM, in EXT4 and EXT2, and all behave the same.  I am doing the bare-necessities install, so no packages other than what's installed automatically.

Each time when I boot up I log in to the plain terminal and I get to the prompt fine.  I left the ping on for maybe half and hour and it didn't lock up there, also, idling for an hour or so doesn't lock it up in any way.  Opening virtual consoles with ctrl-alt-f2 etc. does not lock up, nor does logging in several times.

Most of the time, doing sudo apt-get update locks the system, but twice it has gotten through that, but then locks up very shortly into sudo apt-get upgrade.

I ran a memory test for one and a half cycles, maybe an hour, and I'll leave it on tonight testing to get more complete results, but I don't think this is a memory problem (otherwise the problem would show even worse when using live distributions.)

One time I tried making a new directory, and it was successful, but then using vim to create a test file within that directory locked it up without entering vim at all.

I have no idea what's causing these lockups.  Is there anything I can do to get more information.  I don't even know how to search for help for such a problem.  I don't know when or why the system is locking.

Oh, and another piece of information I just realized, the console cursor continues to blink even while the system is locked, but the apt-get doesn't go forward, nor can I open a new virtual terminal.

Thank you for your insight.

---

### Post by Mizutsuki on 2011-02-27
Bump.

---

### Post by Mizutsuki on 2011-02-28
Bump.

---

### Post by rbishop on 2011-02-28
I know you don't think it's your RAM, but have you tried swapping it out, or dropping down to just 1 stick, etc.  

I had some similar problems with my desktop Ubuntu install.  I didn't think that it was a problem with the RAM until I took one out and tested it in both slots, with no problems, but as soon as I put the other stick in it started having problems no matter which port it was in.  I ran multiple Mem tests with no problem.

Just my thought.  Hope you get it resolved.

---

