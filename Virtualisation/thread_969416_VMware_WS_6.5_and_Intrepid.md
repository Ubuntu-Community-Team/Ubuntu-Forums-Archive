---
title: "VMware WS 6.5 and Intrepid"
date: 2008-11-03
forum: Virtualisation
---

### Post by pvravi on 2008-11-03
Hi folks, 

I had 8.04 with VMWare WS 6.0.5, running an XP guest. Everything was OK. 

When I upgraded to 8.10 Intrepid, 6.0.5 no longer worked since I could not find a compatible vmnet (and 2 other) modules. I upgraded to VMWare WS 6.5.0, and started my XP virtual machine. 

Although the machine starts, I find that I am unable to connect to the network. 

I check through the command prompt and see that my DNS resolution is OK. The Network Status indicates everthing correctly. I even unlocked (un firewalled) the network connection. Still I am unable to browse, and unable to connect to outlook (although that is on the intranet). I am able to ping my outlook server. 

I checked and saw that my proxies are setup correctly, in short, it should work but it isn't.

I am using a bridged connection.

Help, please!

Thanks
pvravi

---

### Post by darco on 2008-11-04
I am running Linux Mint as host and XP Pro as guest. XP works fine. I added Vista and it too would not connect to the internet even though I had an ip and I could ping any website. I deleted Vista then added another vm, Windows 7. I get the exact same problem!  On top of that, after it installs , the OS is fine (expect network access) but after a reboot, my entire system freezes up and I must do a hard reboot. I booted up my XP vm and it gave me an error about vmnet0 . I deleted the network adapter then re added it and that seemed to fix the XP issue. I have not attempted to start up W7 as I dont feel up to having to hard boot it....
Running VM WS 6.5

darco

---

### Post by ninocass on 2008-11-04
bridged networking is a no go here as well :(

---

### Post by ninocass on 2008-11-04
it seems bridged networking works over wired but not wireless, im almost 100% sure that wireless briding was working in hardy

---

