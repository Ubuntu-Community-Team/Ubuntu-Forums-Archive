---
title: "Advice for computer lab?? Mail? Backup?"
date: 2014-05-06
forum: Server Platforms
---

### Post by owemeacent on 2014-05-06
I'm a 2-year linux user, I usually use Arch/Gentoo for desktops, but whenever I want to something that involves servers, of couse I would use Ubuntu. 've only did an ubuntu web server once, and that time I had to use the IP because I didn't know how to set a local domain name. Anyways, a private school I used to go to has asked me to set up their computer lab because it has no one to administer it and it uses XP. Since they are very old computers, I plan to put Lubuntu on them, for it has low memory consumption and an XP-like interface. I'm also planning to have one server that will backup all their things. I know I'm going to use SSH somehow for backup, but I'm not sure how, and I need to automatically have a standard backup schedule. Another thing is that I want to be able to send mail to users on the computer. Would that be possible? and if so, how? 

PS: Any extra advice would be greatly appreciated :-)

---

### Post by CharlesA on 2014-05-06
Rsync over SSH would work for the backups, but you'd have to create a script for it or something.

If you are going to be doing a deployment over a lot of the same hardware, you can use clonezilla to clone one machine and then restore that image to each of the other machines.. might save time even if you need to change the hostname and some other things.

---

### Post by owemeacent on 2014-05-06
What about mail? Like if I wanted to send out a message to every user on every computer, would I be able to do that?

---

### Post by CharlesA on 2014-05-06
Not sure. You can run local mail, but I don't think that would do what you want to do.

---

