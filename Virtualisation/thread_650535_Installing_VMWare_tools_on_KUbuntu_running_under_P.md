---
title: "Installing VMWare tools on K/Ubuntu running under Player"
date: 2007-12-26
forum: Virtualisation
---

### Post by AdamDare on 2007-12-26
Hello All,

Just to set expectations I'm a super noob to both Ubuntu and VMWare, so I'm doing mass learning here.  So please type slowly and use small words when responding. :)

I have been able to build installs of both Kubuntu and Ubuntu, 7.10 on both, for VMWare Player 2.0.  I'd like to be able to install VMWare tools on those OSs, but I've been unable to so far.  I realize that people typically don't do that on the Player, but I've been doing other things, such as creating the installs, so I'm assuming its possible.

I've been searching the forums and web for solutions, but I have come up empty.  I haven't found a solution that works for me.  I think the biggest problem is that I don't know where to get a copy the tools.

Or, alternatively, does anyone know where I can get an image with the VMTools already installed?

Thanxx,

Adam

---

### Post by fjgaude on 2007-12-26
I don't use the Player, but do the Server. In Server the Tools are installed from the VM tab menu when you are running the guest OS. Likely the Player is the same.

---

### Post by AdamDare on 2007-12-26
I've seen instructions for doing it that way, but the Player doesn't have that option.  From what I've seen that basically mounts a CD with the VMWare tools on it.  I don't have such a CD, so I can't do that in any event.

I've also seen references to having to rebuild some files.  Ideally what I'd like is a list of steps to do the following:

1. Location where I can download the VMWare tools for both Ubuntu and Kubuntu.  Unless I need to build them then the sources would be great.
2. The commands necessary to mount and install the tools.

Thanxx, 

Adam

---

### Post by milliganp on 2008-01-02
The necessary ISO file is part of the free distributions of VMWare server 1.x and 2 (beta). The VMWare website states that server 2 beta supports 7.10.

If you download the server [**[COLOR="Blue"]32 bit[/COLOR]**]("http://download3.vmware.com/software/vmserver/VMware-server-e.x.p-63231.i386.tar.gz") or [**[COLOR="Blue"]64 bit[/COLOR]**]("http://download3.vmware.com/software/vmserver/VMware-server-e.x.p-63231.x86_64.tar.gz") you can then extract the linux tools iso file which is located at [COLOR="Magenta"]vmware-server-distrib\lib\isoimages\[/COLOR]

That gets you the file. Installation instructions are documented elsewhere.

Hope this helps

---

