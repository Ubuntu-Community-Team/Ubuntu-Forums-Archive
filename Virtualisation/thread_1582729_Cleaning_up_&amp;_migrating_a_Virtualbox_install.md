---
title: "Cleaning up &amp; migrating a Virtualbox install"
date: 2010-09-26
forum: Virtualisation
---

### Post by Objekt on 2010-09-26
I've been using Virtualbox for some time to run virtual Windows XP & 7 machines under Ubuntu 9.10.  As part of moving to Ubuntu 10.04, I'd like to take my existing Virtualbox setup, and have it available when running Ubuntu 10.04.

Is there an easy way to do that?  Is it as simple as installing Virtualbox under Ubuntu 10.04, then moving some files around?  I have a vague notion that my two Virtualbox virtual machines (one Windows XP and one Windows 7) are characterized by one or more files on my Ubuntu 9.10 install, probably in the ~/.Virtualbox folder.  But I'm not too sure exactly which files to move.  Any tips?

FWIW, I found the following walkthrough.  Haven't tried it yet, so I don't know for sure that it works, but it seems worth a try:

[http://www.kernelhardware.org/how-to-move-virtualbox-guest-vm/]("http://www.kernelhardware.org/how-to-move-virtualbox-guest-vm/")

[s]Also, I seem to have several duplicates of my virtual machines, in my ~/.Virtualbox folder.  Together there are about 5 different 8 to 9 GB files, which severely clutter my /home partition, taking up about 45 GB (!).  How can I figure out which ones it is safe to get rid of?[/s]

Nevermind, got it sorted.  I had several snapshots I didn't really need.  Turns out those suckers can be big - several GB.

---

### Post by standingfire on 2010-10-19
You can also use the export function in VirtualBox as well.

---

### Post by aeronutt on 2010-10-19
Agreed, exporting under an old vbox version, then importing under a clean, new vbox install worked well for me.

---

### Post by Objekt on 2010-10-20
What I ended up doing was this: I recreated both virtual machines in my new Virtualbox install under Ubuntu 10.04, using the two *.vdi files as a base.  

That worked quite well, although I did have to re-do all the settings such as shared folder locations, RAM size, etc.

Did 3.2.8 have the "Export" function, or is that new to Virtualbox 3.2.10?  I wouldn't be surprised if I simply missed it before.

---

