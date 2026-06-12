---
title: "Firestarter gui not working"
date: 2005-04-14
forum: Server Platforms
---

### Post by artio on 2005-04-14
I've seen a few Firestarter problems in the forums but not this one...

Firestarter seems to be running (I installed it with synaptics), i.e. typing sudo firestarter -p at a command line stops it and sudo firestarter -p starts it.

But when I select Firestarter from the Appllications->System Tools menu, I get a window telling me: 

"Error: A proper configuration for Firestarter was not found. If you are running Firestarter from the directory you built it in, run 'make install-data-local' to install a configuration, or simply 'make install' to install the whole program.

Firestarter will now close."

Anybody knows where the configuration is when installing it with Synaptic?

(Incidentally, this is my biggest complaint about Ubuntu: compliance with directory standards is tenuous at best)

---

### Post by 8086 on 2005-10-16
Of course this is WAY to old a post to actually have any use for the original poster, but maybe someone will have some use for this:

I also got the above message when upgrading my distro from "Hoary" to "Breezy". 
I tried removing and then installing Firestarter to no avail - just like the poster. To fix it you have to remove the firestarter directory from /etc.

```

cd /etc
sudo mv firestarter firestarter.old

```

Probably the newer version is choking on the old config files.:???:

---

