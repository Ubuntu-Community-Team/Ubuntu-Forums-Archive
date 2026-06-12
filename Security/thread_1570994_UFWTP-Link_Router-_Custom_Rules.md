---
title: "UFW/TP-Link Router- Custom Rules"
date: 2010-09-09
forum: Security
---

### Post by Vigh on 2010-09-09
Hi I know this isn't 100% to do with Ubuntu, but I have set up some custom outbound deny rules for my firewall but would like to have the rules set up across the entire network rather than just for my computer. I am using a TP-Link Router and I want to block some specific IPs and ports, I can add the settings into router so that the rules apply to the entire network using the router firewall but unfortunately when I apply the outbound rules to the router it completely resets itself wiping out all saved configuration settings. Could this be due to me blocking a port necessary for the router to function? I can provide the port numbers. I understand I could apply the rules to each computer using ufw. But unfortunately I am the only one in the house using UNIX, the other members of the household use windows and thus setting up settings on the router would be easiest.

---

### Post by BkkBonanza on 2010-09-09
Are you sure it "resets itself" or do you mean it becomes "dead" and you have to do a hardware reset manually to get back in again?

---

### Post by Vigh on 2010-09-09
No hardware resetting or pinhole pushing involved at all. For some strange reason when u add your custom block settings into the router it literally erases its memory and configuration settings and you have to set everything up from scratch again. Only happens when applying custom firewall settings. I have updated to the latest version of firmware, still happening.

---

### Post by oliwek on 2010-10-14
" you have to set everything up from scratch again"

... you noticed it is possible to save your TP-Link router settings in a file on your computer, then reload them with one click from the router interface if everything is erased, didn't you?

I hope you don't write everything manually each time you alter your port settings and it resets ](*,)


edit : sorry, hadn't noticed last post was a month ago...

---

