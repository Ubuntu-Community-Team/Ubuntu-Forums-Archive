---
title: "Multimedia device drivers &amp; virtualization"
date: 2007-10-24
forum: Virtualisation
---

### Post by vemon on 2007-10-24
Hi!

I'm setting up a HTPC running Ubuntu Gutsy with multimedia software for watching digital television and movies. I also need server functionality like a web server (apache), version control (svn) and ssh shell. It feels stupid to run these two totally different "bundles" of software in the same operating system instance.

I was thinking that maybe it would be possible to run vmware or some other virtualization solution to isolate these two functionalities to their own "partitions" so that I could easily boot the other partition (probably usually the HTPC partition) without affecting the other. I would be using ubunutu desktop installation with Xorg & Tv out in the HTPC partition and a stripped Ubuntu server installation without a graphical interface in the server partition.

I have a few questions in mind before starting this effort and I hope someone would have the answers:

- Does the setup I have in mind seem totally ridiculous or is it even possible? :)

- How do device drivers behave under virtualized environment? Do they run in the underlying operating system or in the virtual machine?

- Do the host and "parasite" operating systems have to be running the same kernel to take full advantage of multimedia (and other) devices attached to the computer?

- What are the software requirements for the underlying operating system? Can I have the virtual machines running on a very basic Ubuntu server installation?

- What is the performance impact for multimedia applications like video players (vlc, mplayer, etc.) when running in a virtual machine?

---

