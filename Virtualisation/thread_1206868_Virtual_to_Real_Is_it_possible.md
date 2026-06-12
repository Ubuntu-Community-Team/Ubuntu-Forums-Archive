---
title: "Virtual to Real? Is it possible?"
date: 2009-07-07
forum: Virtualisation
---

### Post by blackxored on 2009-07-07
Hello everybody.
I'm using a software-based virtualization strategy for installing linux servers. I'm using virtualbox-ose under ubuntu9.04. My point is, that I'm configuring the servers virtually, then booting from network on a real system, installing, and recreating the system based on the virtual one (assigning hostname, copying config files, etc.). What I need is a solution that let's me get this Virtual Box hd media files, into a real harddrive, for deploying. I know it may sound hard to say, that's why I'm posting. Seeking for advice.

Best regards.

---

### Post by blackxored on 2009-07-08
Well, it seems like noone has a clue yet. 
My second question then, as a workaround, there are easy resources to learn how to develop a software applicance such as those for turnkey, which I can use and configure and then deploy?

---

### Post by Cheesemill on 2009-07-08
Remastersys may be what you need, you can use it to create a bootable installation CD from an already installed system (including settings, apps, etc..)

---

### Post by PilotJLR on 2009-07-15
So "real" system means a physical server? You want to do a V2P migration... another option is netcat. Like so:
[http://virtualizationinformation.com/?p=36](http://virtualizationinformation.com/?p=36)

---

### Post by blackxored on 2009-07-20
Can you provide a little more specific info?
Here the scenario I will always do with. 
I'll install ubuntu-server-8.04 or turnkey-linux-core on VBox, then after configuring & testing, I need to make them physical, since management says so. So, can you tell me what to do?

---

### Post by PilotJLR on 2009-07-20
Did you get a chance to read through the link I posted? It contains step by step instructions. I'm not sure how this could be more specific...

---

