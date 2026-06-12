---
title: "Command-line resource monitoring?"
date: 2008-07-16
forum: Server Platforms
---

### Post by onezero on 2008-07-16
Hi all.  I have a server running apache, a few samba shares and a few other things, nothing too special.  I'm running it in MS Virtual Server 2005 if it matters at all.

Anyhow, I'm looking for some kind of command-line resource monitors to monitor CPU usage, network usage, memory, etc.  Something similar to gkrellm, but for the command-line.  Anyone have any suggestions?

Thank you in advance!

---

### Post by 505 on 2008-07-16
You can use the command 'top' for CPU, memory, swap etc, but it doesn't monitor the network.

---

### Post by 47_MasoN_47 on 2008-07-16
You can install htop and try that one also.  I like it a little better myself.  It still doesn't do network monitoring to my knowledge.

---

### Post by onezero on 2008-07-16
Ah, thank you both very much.  This covers everything but networking, as you both said.  Still looking for something that will cover that, if anyone has any ideas.

---

### Post by Yannick Le Saint kyncani on 2008-07-16
Yep, top for process, cpu and memory and iftop for network interfaces.

---

### Post by onezero on 2008-07-16
Ah, iftop!  I should have guessed. :P  Thank you all very much, these are exactly the tools I needed.

---

### Post by windependence on 2008-07-16
You can also use ntop.

-Tim

---

### Post by ilrudie on 2008-07-16
give jnettop a try.  iftop looks real nice too.

---

