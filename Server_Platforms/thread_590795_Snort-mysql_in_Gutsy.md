---
title: "Snort-mysql in Gutsy?"
date: 2007-10-25
forum: Server Platforms
---

### Post by donad on 2007-10-25
Hello everyone,

    I was trying to install Snort, mysql and base on my gutsy installation.

I have never setup all of this together before and used this guide for feisty.

[http://ubuntuforums.org/showthread.php?t=483488]("http://ubuntuforums.org/showthread.php?t=483488")

My main problem is Snort-mysql itself.  Whenever I start the service or just run via snort -c /etc/snort/snort.conf the processor immediatly goes to 100 and memory goes up until the machine freezes.

I also tried portscanning the machine while snort was running.  I get no alerts doing this.

I was just wondering if anyone has snort working under gutsy and if so are there any tips you could offer?

Thanks!

---

### Post by donad on 2007-10-25
Just a little update.  I installed feisty fawn in a VM and then installed snort using the same steps...  Everything is fine and snort is showing alerts!

I think it may have more to do with the snort version than just gutsy itself.  Gutsy has Snort 2.7 and Feisty is 2.3.  Is there anyway to install an older version of snort on Gutsy using repos?  If not what would be the best solution to get things going on gutsy.

Thanks!!!

---

