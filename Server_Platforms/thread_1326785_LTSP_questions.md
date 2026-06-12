---
title: "LTSP questions"
date: 2009-11-14
forum: Server Platforms
---

### Post by wirefly on 2009-11-14
Hiya

I've been playing with 9.10 and setting up a LTSP for the home.  I have some questions that I can't seem to find answers too.

Some background, I've setup 9.10 ubuntu server from the installation CD, then installed the ltsp-server-standalone, build the image and I have a working setup.

Now I want to add a gnome desktop to the clients but not have it available on the server machine.  I've played around and I did an aptitude install of it from a client machine, but it seems to have installed on the main server rather than just in the ltsp chroot area /opt/ltsp/i386 ?

or.... does this area serve another purpose.

I did a fresh install and chroot'd to this directory, then did a aptitude install ubuntu-desktop in the chroot.  Updated the client image which then displayed the gdm login but wouldn't authenticate any users.  Maybe I missed something there.

So how do I make the ubuntu-desktop only on the clients and not on the server itself ?  Or isn't that how LTSP works ?  I'm a bit of a newbie to this, but love the idea of a single installation that everyone uses.

Thanks for your input, feedback and ideas.

---

