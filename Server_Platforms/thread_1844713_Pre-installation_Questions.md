---
title: "Pre-installation Questions"
date: 2011-09-15
forum: Server Platforms
---

### Post by BEEDO on 2011-09-15
Being new to Ubuntu, Linux, and servers, I am planning my installation. Soon to install a LAMP, I am inclined to also install Webmin which would probably do everything I want it to. Yet I also would like to install phpmyadmin. Will they peaceably co-exist?

---

### Post by ibutho on 2011-09-15
Hi and welcome to the forum.

Yes, phpmyadmin and webmin can co-exist on the same system.

---

### Post by BEEDO on 2011-09-15
Thanks for the welcome and your quick response!

Another Question I have is about which Ubuntu server version will be best for me, 11.04 server or 10.04.3 LTS server? I am inexperienced in many areas and will use the server to help me test/design websites while learning how to do that better, using various OS's on my home network. I would like the server to be as trouble free as possible since I have plenty of other challenges.

---

### Post by ibutho on 2011-09-15
It's up to you really. If you are just using it to learn and test websites, then either version will do.

---

### Post by BEEDO on 2011-09-15
I like reading other people's opinions, since until I get experience they are my compass...

Next question: Unless I am swayed to Ubuntu 10.04.3 server, I will be installing the 11.04 server. During the install I expect to see a Software Selection screen and am planning to check the Open SSH server and LAMP server options. After the install I want to add Webmin and phpmyadmin. Is that combo a harmonious mix?

Another question: A friend is giving me a computer he has salvaged and this will be the one for this project. All I know is that it will have MS XP Pro when I get it. I intend to add Photoshop and Illustrator to that since I am familiar with them. When installing Ubuntu I will be manually partitioning the drive. So... one for XP, one for Ubuntu, one for swap space... any others? Assuming the worst and most likely scenario, I expect an 80Gb drive. How much should I allot for each partition? (Swap space = RAM)

---

### Post by ibutho on 2011-09-16
You should be okay with the software selections you suggested above. As for partitioning, again this depends on an individual and what the system is for. There is no set partitioning scheme, but make sure you have ample space for your needs. On my server which has 512MB ram, I have a swap space of 1024MB, but it's hardly used.

---

### Post by BEEDO on 2011-09-17
Now that I am getting closer to the actual installation (I will probably have the hardware in my possession tomorrow) I have to wonder if it is risky to the existing OS (Windows XP Pro with whatever interesting programs my generous friend may have included -he salvages computers so it is hard to say what hardware I'll end up with) to partition the drive for Ubuntu server.

To be clear: Will partitioning the drive while installing Ubuntu server put the existing XP OS at risk?


Also: Thanks ibutho for the feedback. I look forward to achieving my first small plot of functionality in this unfamiliar terrain!

---

### Post by maverickaddicted on 2011-09-17
Hi Beedo,

Since you are installing the Ubuntu 11.04 Server edition and moreover, this is your first Server experience, I think that this would help you a lot while configuring your first server

[http://www.server-world.info/en/note?os=Ubuntu_11.04&p=install](http://www.server-world.info/en/note?os=Ubuntu_11.04&p=install)

This guide had helped me a lot, since I am also new to Ubuntu and had configured my first server using this guide only.

---

### Post by ibutho on 2011-09-17
> **BEEDO said:**
> Now that I am getting closer to the actual installation (I will probably have the hardware in my possession tomorrow) I have to wonder if it is risky to the existing OS (Windows XP Pro with whatever interesting programs my generous friend may have included -he salvages computers so it is hard to say what hardware I'll end up with) to partition the drive for Ubuntu server.

To be clear: Will partitioning the drive while installing Ubuntu server put the existing XP OS at risk?


Also: Thanks ibutho for the feedback. I look forward to achieving my first small plot of functionality in this unfamiliar terrain!
If you make the right choices during partitioning (and resizing if you are gonna resize the Windows partition in order to make space for Linux), then you won't be putting your Windows partition at risk. The partitioning tools are pretty straight forward, so I doubt that you will have any difficulties. You can even download system-rescue-cd or gparted live cd to have a look at the partitioning tools.

---

### Post by BEEDO on 2011-09-18
It's always good to hear encouraging words! I received the hardware an hour ago. It has an Athlon 64 X2 so as soon as I "reply" I'll be downloading the 64 bit version of Ubuntu 11.04 server. I don't have the power cord, though, so I'll have to wait to find out how big the drive is. I need the only cord that fits for the download!

A Question: Why is one (32 or 64)- bit version "recommended" over another?

downloaded system-rescue-cd or gparted live cd earlier -confidence is high!

---

