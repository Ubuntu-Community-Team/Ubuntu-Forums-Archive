---
title: "Shortcut That Loads Snapshot possible?"
date: 2008-05-07
forum: Virtualisation
---

### Post by studiosonic on 2008-05-07
Hi - first time poster, so go easy on me :)

I've decided to make the switch to Ubuntu and I'm currently configuring my system. I have flirted with Linux in the past, but this is the first time I've used a distro that is advanced and user-friendly. Before, although I've wanted to make the switch, I just couldn't quite do it due to h/w incompatibilities etc. Using Vista for a while made me think about trying Linux again! :)

So, I've got most things working how I want them, but I need to address some programs that I can't find good equivalents with in Ubuntu, for example Photoshop Elements. I know there is Gimp and other gfx editors, but my workflow is so much better in Elements when processing RAW photos. I've installed VirtualBox and I'm installing XP. 

So, to my question! I was going to install Elements in the XP guest machine, run it and then save it as a snapshot so I can load the guest right into a usable state. Is it possible to create a shortcut in Ubuntu that automatically launches Virtualbox and goes straight into that snapshot, so from just clicking on a link, I'm straight into Elements? 

....now all I need is someone to get ipod Touch syncing via itunes in VirtualBox working and I'm all set! :)

Cheers!

---

### Post by FScheltens on 2009-01-17
with virtualbox you can give a command like:
VBoxManage startvm <name of vm>
This also works with paused virtual machines.

---

### Post by binbash on 2009-01-17
you can also add that command to GDM session so you can start the vm without launching gnome/kde etc.

---

