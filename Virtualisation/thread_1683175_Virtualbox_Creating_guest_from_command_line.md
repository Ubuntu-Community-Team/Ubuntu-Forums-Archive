---
title: "Virtualbox: Creating guest from command line"
date: 2011-02-07
forum: Virtualisation
---

### Post by ronni on 2011-02-07
Hi,

I've already tried the virtualbox community with no luck, so I hope someone here can help me.

I started out using the GUI to create my guests, but the server should not have a GUI for that purpose alone.

So I took a look at the command line, but are in doubt about some arguments.

I would like my VM Guests to be located on another partition in /data/vboxservers in stead of the default under the user creating it.
Is it correct to use --basefolder
?

--cpus <cpucount>
What should I set this to?
I have an Asus board with an Intel Atom dual core with hyperthreading.

I followed the tutorial at [http://www.howtoforge.com/vboxheadless-](http://www.howtoforge.com/vboxheadless-) ... .10-server
Using Ubuntu 10.04.
The tutorial creates a user, but it's not clear to me what the purpose of this user is.

Hope you can help.

- Ronni

---

### Post by CharlesA on 2011-02-07
Set it to 1 core.

You can always forward X over SSH and configure the VMs that way.

---

