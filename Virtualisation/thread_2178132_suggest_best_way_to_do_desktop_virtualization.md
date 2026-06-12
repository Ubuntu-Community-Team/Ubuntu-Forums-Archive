---
title: "suggest best way to do desktop virtualization"
date: 2013-10-02
forum: Virtualisation
---

### Post by ikki_72 on 2013-10-02
i have vmware sphere 5.0 environment at my office

desktop virtualization on windows done with vmware view 4.6, so i'm looking to asimilar way to do desktop virtualization with open source softwares

is it possible for me todo that?

---

### Post by TheFu on 2013-10-02
I've never used VMware View - **LTSP** is what I'd guess is the most similar.
Or you can run a remote desktop using any VM server (**KVM** + libvirt+**virt-manager**) and **rdp**, **vnc**, **NX**, **spice**.
Or you can use **XDMP** which is how UNIX has handled this for .... 30 yrs ... I guess.

So you have 2 separate issues.
* virtualization
* VDI or remote desktop

Remote desktops on a LAN are easy.  If you don't need audio or video, they are almost trivial. 
If you need audio/video, then spice is really the only game. You'll need to read up on that. It should be trivial, but I've never gotten it to work well.
Remote desktops over the Internet means you have to be concerned about security. **FreeNX** server and any NX client will have that built-in. For the other solutions, you'll need a VPN or manual ssh tunnel (that is 3 items now).

Desktop virtualization for 1-5 people is trivial. Desktop virtualization for 50-50,000 not so much.

There are a thousand different solutions for this in Linux. If you need to mix Windows in, the solution set drops and commonly used methods fail.

I use FreeNX for the server running inside an Lubuntu Desktop running inside a KVM VM host as my daily "desktop".  
So, google all the things that I've **bold**ed above to learn more.
If you are 100% in Linux/UNIX, then [this article explains]("http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications") what is possible.  Remote windowing has been part of X/Windows since before I started using it.

---

### Post by Kirboosy on 2013-10-02
I would recommend checking out Virtualbox. Its super easy to install and using it is similar to VMware Workstation.

[Virtualbox Ubuntu Wiki]("https://help.ubuntu.com/community/VirtualBox")

I typically just install it by going to the Virtualbox website and installing the .deb that they provide. 

[Linux Downloads - Oracle Virtualbox]("https://www.virtualbox.org/wiki/Linux_Downloads")

They have Windows Binaries as well.

Hope that helps!
~Caboose

---

### Post by TheFu on 2013-10-02
> **Caboose885 said:**
> II typically just install it by going to the Virtualbox website and installing the .deb that they provide. 
I respectfully disagree with the suggestion to **download the .deb** file.  Package management is THE MOST IMPORTANT feature of Linux systems.  Using straight .deb files for installation is NOT something that non-experts should be doing. There are repercussions with this sort of install.

Either use the built-in version of virtualbox (synaptic has it) from the Canonical repos.
Or use the Oracle provided PPA.

I give talks on VirtualBox performance optimizations around the world (ok, only 4 countries/3 continents so far). There are a few key things to setup to [avoid terrible performance.]("http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox")

Hope this helps.

---

### Post by Kirboosy on 2013-10-02
I would advise the Oracle PPA over the built-in repository version. The packages aren't as new in the built in repo.

Don't forget, the PPA is only as good as the maintainer.

---

### Post by ikki_72 on 2013-10-04
thanks for all those suggestions

my main interest is more towards VDI

I'll check on TheFu's suggestions

---

### Post by sandyd on 2013-10-04
Also look at KVM - which can easily be managed through virt-manager

---

