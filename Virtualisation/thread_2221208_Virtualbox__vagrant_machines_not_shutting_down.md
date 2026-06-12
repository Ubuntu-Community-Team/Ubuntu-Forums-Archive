---
title: "Virtualbox / vagrant machines not shutting down"
date: 2014-05-01
forum: Virtualisation
---

### Post by George_Lund on 2014-05-01
When I shut my Ubuntu PC down, it seems to hang, waiting for my virtualbox machines (created using vagrant) to go away. (It's a networking component that hangs.)

This is described by someone else at [http://askubuntu.com/questions/457329/shutting-down-all-virtualbox-vagrant-vms-in-one-easy-to-use-bash-command-that](http://askubuntu.com/questions/457329/shutting-down-all-virtualbox-vagrant-vms-in-one-easy-to-use-bash-command-that)

It seems to me that the solution would be for the virtualbox Ubuntu port to add a shutdown script, like the one in the answer to that question, to rc6.d.

But I'm new to ubuntu, and have no idea how the package management round here works, and who would be responsible. Or maybe this is just a problem that has to be dealt with by the virtualbox guys, and I should submit a bug report them.

I want to help: anyone get me started?

thanks
George

---

### Post by TheFu on 2014-05-03
IT is a vagrant issue, IMHO.  If you want external power-management signals to be accepted inside a VM (and this may not be desired), then install the apci package.

I should say that I do NOT use vagrant and would never use virtualbox for anything other than desktop-on-desktop testing needs.  Servers should be deployed on more stable VM platforms, IMHO.

---

