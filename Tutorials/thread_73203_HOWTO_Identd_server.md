---
title: "HOWTO: Identd server"
date: 2005-10-08
forum: Tutorials
---

### Post by LokeDK on 2005-10-08
A small guide to install identd server, and get rid of the ~ in front of your username at irc (was annoying me, couldn't get on efnet).
First of all you need to open port 113/TCP in your router.
Then

sudo apt-get install oidentd

You should get
Starting ident daemon: oidentd.
when finishing installing it.
else you can manually start it by typing
/etc/init.d/oidentd start
in a terminal

That should be it.
--
If you are using the Firestarter firewall, remember to add port 113 to your rules.
--

Enjoy :D

---

### Post by umbke on 2006-03-08
If you can't get any identd to work, use xchat auth
[http://xchat.org/auth/](http://xchat.org/auth/)

---

### Post by ryu kun on 2006-12-04
But,

1. How do I use random idents?
2. How do I mask my IP?

I've been searching and trying for many hours but couldn't find anything useful.

---

### Post by Death4Life on 2008-02-20
I'd like to know this too.

I've got rid of the ~ by installing pidentd and forwarding 113.
Now i'm getting random names :/

---

### Post by Beren Camlost on 2008-02-21
Well, so far none of the ident servers I've tried have helped me a single bit. The case here is, quakenet has G-lined my ISP altogether, so only way to connect is by using an ident server. I tried on my windows install earlier and it worked a charm. However, how to set this up in linux totally eludes me. I've tried pidentd, midentd and oidentd, none of which seems to be able get me anywhere.

I seem to find generally very little info regarding ident servers (and how to operate them for linux), so I'm kinda stuck in a limbo here. This is kind of important to me as one project I signed up for recently are using quakenet as irc host, and I would really really really hate dualbooting simply due to the fact that I seem to be unable to set up a linux ident server properly.

Thanks in advance, and as this is an issue that have been bugging me for quite a while (I had to leave a few irc channels behind when I changed ISP), so I'm really hoping someone can shed some light on this.

---

### Post by MechaMechanism on 2010-10-24
Thank you for the how-to.  Worked great for me.

---

### Post by temporizer on 2011-12-18
Sorry to bump an old thread, but nothing seems to be working in ubuntu 11.04 to get rid of the ~ in irc
Any help would be nice.

---

