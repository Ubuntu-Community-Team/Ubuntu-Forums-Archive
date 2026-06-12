---
title: "Installation trouble... 11.04"
date: 2011-11-01
forum: Ubuntu Studio
---

### Post by Risingfate on 2011-11-01
Okay so i'm trying to determine a couple things for my new system. First of all i'll give you information on my current setup.
 
I'm currently running a dual-boot between Vista and Ubuntu 11.10, using a dedicated partition for my /home so I can have all my documents from each system in the same place. The Laptop is a Dell Inspiron 1525 (ancient one, eh oh well) with 160gb hard drive. 20 for each operating system and 80 for the /home folder. So anyway. I have an extra partition for ubuntu studio set up so that I can get my triple boot workstation finally up and running. 
 
Okay so no problems at all installing vista and ubuntu ocelet. Got burg/grub all set up and no problems there either. Internet and everything works great. But when I try to install ubuntu studio 11.04 it can't set up the dhcp network. And then it doesn't install the packages that it should, and then it finishes the installation and reboots up to a plain black screen with just a blinking _ cursor. So something isn't working right. I'm just not sure what... 
 
So first I need to know: How can I set up the DHCP network when i have a wep key on my wireless internet. And could the be the cause of my installation trouble?
 
And Second: Which version of ubuntu studio should I be installing anyway. I had 11.10 running in this partition and it installed and worked fine. But I just hate xfce. So I want to run either 11.04 or 10.10 or 10.04. I really like the idea of a real time kernel since i do alot of recording. But i'm not sure if that is worth the trouble. So i was thinking about 10.10 and the preempt kernel. But then I saw that natty fixes alot of networking issues so i thought that would be an easier route for me.
 
Anyway any help you can provide would be great! thanks alot!

---

### Post by jejeman on 2011-11-01
You don't need network for installation. Just unplug all network related stuff.

And for the vesion, well, I can say 10.04 works fine. If you don't mind to setup network by hand.

---

### Post by Risingfate on 2011-11-01
So should I go for 10.04? And use the rt kernel? How stable is it?

---

### Post by jejeman on 2011-11-01
For me 10.04 works good. And the default preempt kernel is stable, no need for rt kernel.
I can't say that you would be satisfied also.
Only when I'm to lazy to compile I wish for newer version...

---

### Post by Risingfate on 2011-11-14
Thanks so much!

---

