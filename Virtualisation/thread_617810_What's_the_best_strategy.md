---
title: "What's the best strategy?"
date: 2007-11-19
forum: Virtualisation
---

### Post by SuperMike on 2007-11-19
What's the best strategy for this scenario?

Imagine you have a newbie Linux admin who sort of knows his way around with Bash and some commands, and knows to type ifconfig to find the NIC settings. He can also install Ubuntu Server and do apt-get for other items. That's about the extent of it. Currently, I have a lot of potential customers like this coming to my website, which is why I mention this type of person.

Anyway, I want to market a web app product to them, but I want it such that I give them a CD, they boot up on it, and can run the web app in production. If they make changes in the web app, it remains in some hard drive partition and yet doesn't disturb their hard drive. In other words, the LiveCD detects they have EXT3 and creates a new directory where it stores its stuff. That way, on reboots, their info remains intact. And, because it caches stuff to the EXT3 partition, it runs much faster than a normal LiveCD.

Okay, another strategy could be that I implement a VM or OpenVZ kind of environment. The risk there, however, is that I want this to be extremely easy for the newbie Linux admin to set up. I don't want them to have to do a whole lot of steps or have to know how to build a VM server.

I've also heard rumblings about JeOS but I suspect it's only a thing for VMWare?

In essence, whatever I give the end user, they get a bootable CD or a VM that's a snap for them to use without much fuss, and can put it on their own hardware. That way, I don't have to start thinking of building expensive server appliances (hardware solutions) for my customers and can merely sell the CDs. (Note, it's a F/OSS project, but I will have some things that I sell, such as the bootable server and VM CDs.)

So, what's the best approach in your opinion?

---

### Post by SuperMike on 2007-11-20
Nobody can offer any advice?

---

### Post by smartbei on 2007-11-20
Since your target people know basic bash commands and have figured out how to install with apt-get, why not package the application as a deb and offer/sell it via internet?

That way, they would not need to restart the computer, wait the somewhat lengthy time for the livecd to boot, and then not be able to use anything on the computer while this is running. With a livecd you are also runnign the risk of not recognizing user's hardware, etc.

Have you considered this option and decided against it or is there a specific reason this would not work for you?

---

### Post by SuperMike on 2007-11-20
smartbei - you make some excellent points. I'll have to consider this.

---

