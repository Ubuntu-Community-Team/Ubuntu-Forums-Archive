---
title: "server or desktop edition for testing website on vmware"
date: 2012-04-18
forum: Server Platforms
---

### Post by kev670q on 2012-04-18
I'll be installing a new wiki website on an Ubuntu server running 8.10, but first i want to test the installation on a local machine before I do it properly.

So I'll be installing Ubuntu on VMWare player which is running on windows 7. My question is should i install the desktop edition with a GUI so I'll be able to see localhost to confirm its working on a web browser or should i install it on the server edition which is only command line, but is the edition that it will be running on when i install it properly... If i install it on the server edition is there any way to test the installation on the local machine

Thanks

---

### Post by sj1410 on 2012-04-18
ubuntu 8.10 is end of life, so you will not be able to get any updates. Even ubuntu 8.10 repositories are not available so installing a new package/software will be a problem. I would suggest using a LTS edition, and 10.04 is stable and a good choice. 

For your requirement server edition is good as it is lite. You can install LAMP using tasksel to prepare your server for apache, mysql & php.

---

### Post by Cheesemill on 2012-04-18
> **sj1410 said:**
> ubuntu 8.10 is end of life, so you will not be able to get any updates. Even ubuntu 8.10 repositories are not available so installing a new package/software will be a problem. I would suggest using a LTS edition, and 10.04 is stable and a good choice. 

For your requirement server edition is good as it is lite. You can install LAMP using tasksel to prepare your server for apache, mysql & php.

+1

Also set up your VM to use bridged networking and give it a static IP address, you can then test the website from your Win 7 machine.

---

### Post by kev670q on 2012-04-18
Thanks a lot. the only reason im using 8.10 is becuase that's what is installed on the server that im eventually going to have to install this wiki on unfortunately i have no control over that... thanks for the help and the tasksel bit aswell. much appreciated

---

### Post by Cheesemill on 2012-04-18
> **kev670q said:**
> Thanks a lot. the only reason im using 8.10 is becuase that's what is installed on the server that im eventually going to have to install this wiki on unfortunately i have no control over that... thanks for the help and the tasksel bit aswell. much appreciated

I would have a talk with whoever does have control over the OS and ask them to change it. Running a web server that doesn't get security updates is a huge risk, there could be known exploits that would let any attacker gain complete control over the machine.

---

### Post by Jonathan L on 2012-04-18
Hi Kev

Given that you don't have control over the OS, use the one they have running, ie 8.10 server: from what you've said, your goal is to have a practice run at the real thing, so you need to know what problems you might have, if any, sourcing the right packages, how to test from browsers and so on.  (On the topic of testing, I can recommend learning about wget for basic testing from the command line.)

If you choose to have a discussion with them about their choice of OS version, I'd recommend the various long-term support versions, as they last for a long time: 8.04, for example, is still in support. 10.04 still good; 12.04 available in a week or so.  I know if I asked someone to install some wiki software and they told me I had to upgrade the OS I might regard them as bringing more problems than they're solving, so go gently !

Kind regards,
Jonathan.

---

