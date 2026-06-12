---
title: "Check to see if vboxdrv is loaded before running a command"
date: 2011-03-16
forum: Virtualisation
---

### Post by CharlesA on 2011-03-16
Hiya,

I'm trying to figure out the best way to check to make sure vboxdrv is loaded before running a series of commands.

Background:
I've got VirtualBox installed on my Ubuntu box and I've got a script written up to start up a couple virtual machines after a reboot.

Most of the time it works fine, but sometimes it doesn't work, since the kernel module isn't loaded when the script runs.

I need a way to check to make sure that the module is loaded before trying to start the VMs back up, but I'm not sure of the most efficient way to do it.

I thought to try using this command:

```
lsmod | grep vboxdrv
```

Then using an if statement to test if the value is 0 or not, but I'm also thinking of just running VBoxHeadless and seeing it errors out and run the test that way.

Does anyone have any ideas on this one?

---

### Post by JKyleOKC on 2011-03-17
Have you looked at vboxtool on sourceforge? It integrates vbox into the upstart sequence to automagically load as many VMs as you want, under a user id that you define, and takes care of saving their state when you power down the host. It's written in perl (as I recall) so a look at its source ought to provide the info you ask for, but I've been using it for almost a year and find no need for other home-grown scripts. It does run the VMs that it loads in headless mode, which might be a problem if you want to retain the vbox menus and control capability without using VBoxManage, though, and puts each VM on its own vrdp port...

---

### Post by CharlesA on 2011-03-17
First time I've heard of it, actually. Does it work with VBox 4.0?

I've been using phpvirtualbox for a while now, and the only thing that is lacking so far is an auto-start/auto-save function.

---

### Post by JKyleOKC on 2011-03-17
I've not tried it with vbox 4; after trying vbox 4 on a test machine, I pinned vbox to 3.12 on all my production systems. The new interface and directory structure simply turned me off...

However since VBoxManage apparently still works about the same in 4 as it does in 3.x, I would expect vboxtool to work the same. It's actually a wrapper around VBoxManage, plus the scripts necessary to integrate with upstart.

A quick Google search turned up this: [http://sourceforge.net/tracker/index.php?func=detail&aid=3151695&group_id=239993&atid=1111629](http://sourceforge.net/tracker/index.php?func=detail&aid=3151695&group_id=239993&atid=1111629) which indicates that some major changes are required for compatibility with vbox 4, due to changes in the vbox syntax...

---

### Post by CharlesA on 2011-03-17
Thanks. I'll poke around the source and see how it compares to the scripts I wrote up.

---

