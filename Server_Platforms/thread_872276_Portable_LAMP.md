---
title: "Portable LAMP?"
date: 2008-07-27
forum: Server Platforms
---

### Post by The Titan on 2008-07-27
I switched to Ubuntu a while ago and i have always had a separate computer on my network used strictly as a LAMP server.  Well that computer was destroyed and now i need to install a LAMP on my computer but i don't want it to be running all of the time...

     When I used windows I had apache2triad and it worked really well for me, i was wondering if there were any applications simliar to this on that i could use on ubuntu.

---

### Post by scragar on 2008-07-27
this is a simple apache script I whipped up to turn apache on or off easily(this is actually version 1.0 of it, I've made a lot of edits in my latest testing version, not for public use yet - the thing actually crashes about once every 5 or 6 runs, so yeah, needs a few fixes yet)

Download, make executable, then make a launcher to run something like
```
sudo ~/bin/apache_monitor.txt
```The "sudo" part is essential, be aware of that.

be sure to set it to be: "application in terminal" in the drop down, easily done.

---

### Post by The Titan on 2008-07-27
Worked great, thanks much buddy :)

---

### Post by scragar on 2008-07-27
ooh, can I add that lamp will run automaticly on a restart, although there are ways to make it so it doesn't(if that makes sense). easiest way is via: System>Administration>Services


Oh, and don't use the **C** option on my script unless it's on a secure box, that grants all perms to all users to the /var/www directory, USE AT YOUR OWN RISK!

---

### Post by tinny on 2008-07-27
> **The Titan said:**
> I switched to Ubuntu a while ago and i have always had a separate computer on my network used strictly as a LAMP server.  Well that computer was destroyed and now i need to install a LAMP on my computer but i don't want it to be running all of the time...

     When I used windows I had apache2triad and it worked really well for me, i was wondering if there were any applications simliar to this on that i could use on ubuntu.

As soon as I read "Portable LAMP" I thought virtualization!

Have you considered running this server in virtualization? E.g. You could create a VMWare image (On Ubuntu, Windows whatever) and choose when to start / stop the virtual server. This virtual server image is also portable, its just a folder on your disk that you can move to other machines that have a VMWare Server / Workstation install. Also because the LAMP server is now just a folder on a disk you can VERY easily back it up.

[http://vmware.com/](http://vmware.com/)

How to...
[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

---

### Post by The Titan on 2008-07-27
> Have you considered running this server in virtualization?

I actually did think of this....   The problem is i have a very slow computer =/.   So unless i don't understand this could be an issue...   I have a P4 1.6  512 ram.

---

### Post by tinny on 2008-07-27
> **The Titan said:**
> I actually did think of this....   The problem is i have a very slow computer =/.   So unless i don't understand this could be an issue...   I have a P4 1.6  512 ram.

The processor could be ok (not great, but ok), but you should have at least 1GB RAM.

---

### Post by The Titan on 2008-07-27
> **tinny said:**
> The processor could be ok (not great, but ok), but you should have at least 1GB RAM.
I wish....  but i live in the boonies....  it would cost like 100 bucks in gas just to go to the nearest best buy and i work at dairy queen.  =/  and i don't have a credit card or bank account for newegg or something....

---

### Post by tinny on 2008-07-27
> **The Titan said:**
> I wish....  but i live in the boonies....  it would cost like 100 bucks in gas just to go to the nearest best buy and i work at dairy queen.  =/  and i don't have a credit card or bank account for newegg or something....

Ummmm, plug your head into the laptop??? :guitar:

---

