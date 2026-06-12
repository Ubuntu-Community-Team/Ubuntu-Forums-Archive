---
title: "Securing Minecraft: protecting against malicious mods"
date: 2012-08-05
forum: Security
---

### Post by jonnyboysmithy on 2012-08-05
I've been running  minecraft server with mods.  After reading of some troubles with mods I don't trust them. I want to set it up in a way that if the mods are malicious that my system remains unaffected.

Options I'm considering:
1. Use apparmor.
2. Modify my minecraft launcher script to run it a as a different user (would that work?).

As far as I know right now my system could be compromised. Yup, paranoid much.. :D
I think the easiest way to secure it is to run the launcher.sh and minecraft under a different username. The idea being that if something goes wrong its confined to that particular user.

---

### Post by Hungry Man on 2012-08-05
Both of things would work and they're both a good idea.

I wrote a guide to run Pidgin in another user.
[https://insanitybit.wordpress.com/2012/08/01/creating-a-new-user-account-for-pidgin/](https://insanitybit.wordpress.com/2012/08/01/creating-a-new-user-account-for-pidgin/)

You can do the same thing with Minecraft or anything else. It's simple. For a server you probably don't need X11 access.

Setting up apparmor should be simple as well.

---

### Post by jonnyboysmithy on 2012-08-05
That was very helpful.
Thanks Hungry_man . :)

---

