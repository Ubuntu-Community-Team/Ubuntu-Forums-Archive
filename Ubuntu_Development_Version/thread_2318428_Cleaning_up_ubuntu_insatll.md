---
title: "Cleaning up ubuntu insatll"
date: 2016-03-26
forum: Ubuntu Development Version
---

### Post by krishnan t s on 2016-03-26
Hiall,

Apologiesif i'm posting it in the wrong forum. I had installed ubuntu 16.04daily builds on my spare laptop to test unity8, elementary osloki(ppa) and few other de's like cinnamom, gnome-shell and kde.There might have been others but i don't remember what they were atthe moment.
Ithink i've messed up my ubuntu install a lot. At the moment, it'staking upto 5 minutes to startup and get to lightdm(machine with 8gbram), a further 3 minutes to get to a working desktop and apps likefirefox and chromium are taking too long to open(almost 2 minutes).I've purged all desktop environments with the exception of thedefault unity7 and the unity8-desktop-session-mir package. My laptopis  dual AMD graphics and uses the open source raedon graphicsdrivers(though i dont know how to switch between the two AMD graphicscard)

Isthere anyway i can speed up ubuntu? I havent installed manyapplications but in the event speeding up is not possible i'll nukethe system and go for a fresh install though i would like to take abackup of all my installed applications and their data(especiallygames-non steam)
Also,i'm using elementary os freya as a dual boot with ubuntu. Even thatis slow but not as slow as ubuntu.

Inthe event i have to format my hdd, i have a few questions regardingthat:
1.Is there any way i can completely erase everything on it permanently?I mean nothing on the hard drive.. a great big blank
2.Is there anyway i can take backup of my installed applications andtheir data? I havent maintained a separate /home. Everything isunder/
3.Can i replace my laptop hdd with an ssd? If so, how do i do it?should i give it to a computer store and ask them to do it for me?Also, can i transfer data from old hdd to          new ssd?

Iplan to use this laptop to learn programming and make software for myown startup with a friend soon.
Thanksin advance for your reply and have a nice day :)

---

### Post by mörgæs on 2016-03-26
> **krishnan t s said:**
> 
1.Is there any way i can completely erase everything on it permanently?I mean nothing on the hard drive.. a great big blank


Yes, just do a new install and choose 'use entire drive' in the process.

---

### Post by zika on 2016-03-26
> **mörgæs said:**
> Yes, just do a new install and choose '_**use entire drive**_' in the process.That would eliminate positive answer ad 2. I suppose, that is also possible, just being careful... ;)

---

### Post by grahammechanical on 2016-03-26
I have 2 installs of 16.06 (xenial xerus). One install I use as my daily driver and I do not experiment in that installation. The other install is where I mess with things like unity8 session. I have just house cleaned that installation by installing another daily ISO image into the partition.

I see a fresh install as a way to clean up messy installations. It does help that I have all my data on a separate partition. And because it is not my main install I do not have to pay the price of installing all my useful applications. 

You have an opportunity to re-order the way you work. One installation that is the main working Ubuntu and you do not mess with that. A second installation where you experiment before installing software on the main install. When this installation gets messed up just re-install. Do not forget to create a partition for data. The priced paid in time now will save a lot of stress later.

Oh, by the way, there will be no AMD proprietary video drivers in 16.04

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fgl](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fgl)

[https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/](https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/)

[http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04](http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04)

Regards.

---

### Post by krishnan t s on 2016-03-26
I originally wanted to have separate partitions but its very difficult to set up in an EFI system. I spent a day and a half setting up  dual boot of elementary os and ubuntu. I think i'm gonna erase everything and install only ubuntu from scratch. But i am running on a broadband connection that'll lose to a snail.. by light years.. Thats why i wanted to take backup of most of my installed programs.

---

