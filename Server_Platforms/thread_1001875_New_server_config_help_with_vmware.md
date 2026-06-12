---
title: "New server config help with vmware"
date: 2008-12-04
forum: Server Platforms
---

### Post by xkaliburx on 2008-12-04
clean server install q's from new Ubuntu user.

Pretty simple q's that should take the right person/people sec's, so basically been a redhat/suse for 5+ years, need to put up a VM server for some remote testing.  Was really pushed to use Ubuntu Server, so giving it a try.  Server install went fine, only selected Virtual Server out of all the options.  After completion it leaves you rebooted at RL3, so I assume there is no RL5, no biggie, but just checking.

Next, can't find good doc's on the server itself.  I am sitting logged in, don't see any type of vm items.  I am familiar and use vmware but this seems not to be the VMware application but their own flavor.

So with that, the easiest question... how do you setup the vmware server, install clients, etc?   A link to some better server doc's, a quick answer, everything is appreciated..

Lr

---

### Post by lykwydchykyn on 2008-12-04
Ok, I'll try to answer a few questions, but it sounds like you're having a classic case of culture shock here.  Things are a bit different in the Debian/Ubuntu world.
 - You're actually in runlevel 2 by default, but it's of little consequence.  Debian based distros default to rl2 rather than rl5.  Apart from single user, reboot, and shutdown the other runlevels aren't really configured any differently.  The RH/Suse convention of rl3 is CLI and rl5 is GUI don't apply.
 - Ubuntu server doesn't install a GUI by default.  If your network connection is all set up, you can install one pretty easily, though most people around here don't recommend it.  Just install xorg, xdm|gdm|kdm, and your favorite DE/WM package using apt-get and you should be set with a minimal GUI. 
 - "Virtual server" installs kvm.  If you'd rather use vmware, you have to download that from vmware's website. VirtualBox is also in the repositories.

General advice:
 - get to know aptitude.  It's your package manager at the CLI (you can use apt-get, but aptitude has an ncurses GUI).  If you understand the APT system, you understand about 50% of admin'ing a Debian or Ubuntu box.
 - Here's the documentation: [https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)
 - write back if there's anything you want more specifics on.

---

### Post by xkaliburx on 2008-12-04
lol, I think "Culture Shock" was a good line.  I am definitely more of a cli guy, so I will listen to the masses and not do the gui.

But.. I think kvm was the key word I was looking for... I don't mind trying/learning the ubuntu way of virtualization, just need a kick in the right direction so I can at least google around kvm, etc. 

VM1 was the local app, VM2 nice and browser based, so just need to see how to get the ball rolling. Server is running (love the ssh welcome message with server stats) but now I want to say, ok, start the admin console, create a new virtual machine, stuff like that.  I tried poking on the box for open ports, as I just wanted some way of getting started, so thanks for the head turn, at least I am facing the right way now!

---

