---
title: "Ubuntu server 11.04 - hangs on reboot"
date: 2011-07-27
forum: Server Platforms
---

### Post by stando007 on 2011-07-27
Hi,
I installed ubuntu server 11.04 32bit version on my old HP Notebook NX6110 with Intel Pentium M CPU. I know this is not server HW, but I want this notebook to act as NAS server for sharing files. The notebook is not so powerful to be a "desktop use" so I decided to give it a try with ubuntu server.
Installation went fine. Everything looks to be working except I can't reboot the system.

With "sudo reboot" command or "sudo reboot -f" command it hangs on "Restarting system" message and then I am only able to shutdown it by pushing the power button.
Shutdown is fine - the same messages print on the console, then shutdown so I assume nothing is hanging there.

I tried to put "reboot=bios" or "reboot=acpi" or "reboot=kbd" and some other options to kernel on the startup, but nothing really helped.

Any idea why reboot is not possible and how to fix this?

---

### Post by varunendra on 2011-07-27
Hi stando007,
This isn't exactly an answer to your question, but if NAS is all you want from your laptop, why don't you try FreeNAS? It is dedicated to this cause and is quite popular these days. However, given your laptops specs, choose 7-series instead of the latest 8. You can download it from here: [http://sourceforge.net/projects/freenas/files/FreeNAS-7-Stable/](http://sourceforge.net/projects/freenas/files/FreeNAS-7-Stable/)

If there's something Ubuntu-specific that you like in your NAS, then I'd suggest to try 10.04 server, as 11.04 is relatively new and may not be as much stable yet.

---

### Post by stando007 on 2011-07-27
varunendra: I already tried Free Nas 7 :) From my basic tests, I must say it is amazing - works perfectly, a lot of services, easily configurable, low HW requirements...

Why I choosen Ubuntu? I use ubuntu as my primary desktop OS and despite I am can't consider myself as a very skilled linux user, I know couple of stuff around it already. So I thought installing ubuntu + installing packages what I need would lead to much more opened system. I mean if I want some extra functionality, then I think ubuntu has more possibilities, packages, etc... Or am I wrong?

Currently I am installing Ubuntu Server 10.04 - will check if there is a problem with reboot too.
Before I choosen 11.04 because "it is the newest" - I did not think much about the versions and which one to choose.

---

### Post by stando007 on 2011-07-27
OK, so Ubuntu Server 10.04 LTS reboots correctly on my HP nx6110 :) I will give it a chance.

I do not know if I should mark this thread as solved - basically Ubuntu Server 11.04 has the problem. So I probably keep this opened.

---

### Post by varunendra on 2011-07-27
> **stando007 said:**
> varunendra: I already tried Free Nas 7 :) From my basic tests, I must say it is amazing - works perfectly, a lot of services, easily configurable, low HW requirements...

Why I choosen Ubuntu? I use ubuntu as my primary desktop OS and despite I am can't consider myself as a very skilled linux user, I know couple of stuff around it already. So I thought installing ubuntu + installing packages what I need would lead to much more opened system. I mean if I want some extra functionality, then I think ubuntu has more possibilities, packages, etc... Or am I wrong?

Currently I am installing Ubuntu Server 10.04 - will check if there is a problem with reboot too.
Before I choosen 11.04 because "it is the newest" - I did not think much about the versions and which one to choose.
I think choosing ubuntu is correct decision if you want to do something 'extra' with it in near future. Free NAS is definitely good, but just a NAS! :)

As for the 'latest' thing, 'stability' is the prime concern for servers, and 'latest', especially in Ubuntu, is not something considered as stable. At present, 10.04 is supposed to be stable and good for most of the users. But there are always exceptions. Like users who complain about 10.04 but are comfortable with other versions (even Jaunty for their server). There's a popular saying (I think in BSD community) - "Don't fix it if it is not broken!!:P

> **stando007 said:**
> OK, so Ubuntu Server 10.04 LTS reboots correctly on my HP nx6110 :) I will give it a chance.

I do not know if I should mark this thread as solved - basically Ubuntu Server 11.04 has the problem. So I probably keep this opened.Yeah, it should be 'solved' once 11.04 or a later one becomes stable. Or maybe there's already some fix which we didn't even try to look for. So I'll post back here if I found some potential fix for the original problem with 11.04.

---

### Post by stando007 on 2011-07-28
Btw, I found couple of threads on web forums describing the same or similar issue on certain HW. But I do now know is some of ubuntu developers know about it.

---

