---
title: "Having a Dabble With KVM"
date: 2021-07-30
forum: Virtualisation
---

### Post by jackdusty on 2021-07-30
Hi

As some of you will know I am very new to Ubuntu - I have had to drop down to Unbuntu 18.04 as I could not get 20.04 working with my external monitors. I am relying on using my WiFi connection at this moment in time although that may change in future. Reading the instruction I need to edit a file to bridge my Virtual machine network to to the adaptor on my physical machine.

Could some kind sole please tell me in simple terms what file need editing and what I would need to put in to bridge the network to my WiFi network.


Many thanks 


Jack

---

### Post by MAFoElffen on 2021-07-30
Well, technically speaking, there is difference between in a Bridge (br0) and Virtual Bridge (virbr0)... 

On a Bridge, basically it points and takes over a physical Network Interface Card (NIC), meaning Wired... The KVM Doc's say that doing this to an WiFi Card is impossible. I have done it... but then it takes total control over it and you don't have access to it from your host for it's use... I have done that where I had both Wired and Wirelesss attached to a laptop...

At one period I lived somewhere where there was no wired internet possible. The ways to get around that in a physical wired NIC is make it shared through SR-VIO... I did this to one of my NIC's and bonded it to my Wireless card, so that direct from my host was wireless, and bridge was going through the wired NIC and rerouted through my wireless... I had to do many things to make that work.

It took about 3 days to get it worked out and working. It was very ugly. I did this both for Windows Hyper-V and for Ubuntu Qemu/KVM. I documented everything I repeat that I did document everything I did very carefully... and even though I did that, when I got a wired connection back to where I was living, it took a complete clean re-install of both OS'es to get back to normal again.

My recommends? Stay with the default installed virbr0 until you get a wired connection into where you live.

---

### Post by ajgreeny on 2021-07-30
Just out of interest, why is it important for you to have a bridged connection and not use the default NAT connection, which in my experience works easily and is quick and simple to set up?

---

