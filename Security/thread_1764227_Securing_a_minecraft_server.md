---
title: "Securing a minecraft server"
date: 2011-05-21
forum: Security
---

### Post by Calcipher on 2011-05-21
Hello security people, I wanted to ask a few questions on securing a minecraft server, though I doubt it would have to be specific to minecraft.  Let me detail what I have, what I have already done, and what I need help with and then open this up to any other suggestions.

**What I have:**
1. A copy of the minecraft_server.jar sitting in a folder in /opt/minecraft_server/one (the one is because this is the first world my server will be running, there may be more than 'one' eventually).
2. UFW set to deny any incoming connection except ones I've specifically allowed and only allowed ssh (on my internal network only) and Minecraft (world accessible).

** What I have done to secure it:**
1. I changed the default port.  I realize this isn't *much* added security, but it is a little extra.
2. I changed /opt/minecraft_server to be owned by root.root
3. I changed /opt/minecraft_server/one to be owned by root.games and chmodded it to 775
4. I changed everything in /opt/minecraft/server/one to be owned by games.games and chmodded it to 775
5. I set the startup script for minecraft to su to games before running the jar file

**Where I want to go, need help with, and need to know if it is worth it:**
I want to chroot jail the minecraft_server.  The thing is, I'm not exactly sure how to do this.  I think I would need to make another java install *somewhere* and then set the root for minecraft to that location.  I'm not exactly sure how to do all of this and not entirely clear if the minecraft_server/one folder would then need to reside below this chrooted folder; I'm guessing it would.  

So, my questions.  1. Is it worth it to chroot minecraft?  2. How do I accomplish chrooting minecraft (even if the answer to #1 is no, this is more out of curiosity than anything else)?  3. Anything else I can do to secure the minecraft server?

Thanks!

P.S. I don't seem to find any good tutorials on securing minecraft, so I plan to write one up after all of this.  Would it be helpful to post such a tutorial for anyone?

---

### Post by OptiDash on 2011-05-25
A guide sounds pretty useful to me, I actually found this thread while searching for a Minecraft hardening guide. :eek:

---

### Post by Calcipher on 2011-05-25
> **OptiDash said:**
> A guide sounds pretty useful to me, I actually found this thread while searching for a Minecraft hardening guide. :eek:

Unfortunately, I never got a response from anyone on if it is feasible and/or reasonable to chroot Minecraft.  I think the issue with that is you'd have to have two copies of java sitting around.  I suppose I can write up the minor things I've done already at some point.

---

