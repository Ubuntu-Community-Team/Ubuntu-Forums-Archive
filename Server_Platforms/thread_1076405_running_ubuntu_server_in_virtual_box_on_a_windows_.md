---
title: "running ubuntu server in virtual box on a windows server"
date: 2009-02-21
forum: Server Platforms
---

### Post by garethsimpsonuk on 2009-02-21
I'm in the process of upgrading my Windows Home Server which gives me the oppourtunity to get rid of my LAMP test box and run it virtual on my WHS.

I tried virtual pc but it wouldn't boot ubuntu. i'm now trying sun's virtual box and ubuntu is working fine.

I've never run a virtual machine before so i would like some advice.

the ubuntu os has access to the network card but i dont think its talking to my DHCP. The ip address is set at 10.0.2.15 which is not in a range that my router gives out.

i also cant see the ubuntu os from other systems. does anyone have any idea how i can get the virtual os to appear as a physical system on my network? or at least educate me on how virtual machines work?


thanks

---

### Post by toolfan2k4 on 2009-02-21
I have had a lot of trouble trying to setup networking properly on Sun xVM. That is not to say it cannot be done. I found it much easier to download VMware server. You can get a free CD key from VMwares website, so long as you don't mind filling out a form. They haven't even spammed me. LoL. Anyway, VMware server works right out of the box so to speak...no need to mess with configuring the network interfaces. I then set my router to assign a specific IP to that VM's MAC address. Wham...easy setup...with a static IP.

---

### Post by garethsimpsonuk on 2009-02-22
thanks for the reply.

yes i had a lot of trouble. it's much esier when you plug in another NIC. I set which card for it to use, choose the right setting (something about host interface, cant remember now) and it worked!

it's obviously gonna be beneficial having a dedicatd NIC anyway.

thanks for the help.

---

### Post by toolfan2k4 on 2009-02-22
Great idea, the reason I did not want to do this was because I had already setup my network to run gigabit so that I had the bandwidth to use only one card....at that point I had too much money into my project to just decide to use a second NIC. At any rate...glad to see you figured it out! Welcome to the world of Ubuntu.

---

### Post by RealPSL on 2009-02-22
By default Virtual Box uses a NAT configuration. If you enable "Host Interface" instead your VM will get an IP address from your DHCP server and serve up network requests just like any other server on your network without further configuration.

Select you VM choose General -> Network -> (Adapter 1)Attached to Host interface -> OK.

---

