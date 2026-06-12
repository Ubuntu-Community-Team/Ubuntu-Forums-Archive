---
title: "Very basic question on  ubuntu server"
date: 2010-05-17
forum: Server Platforms
---

### Post by waheedrafiq on 2010-05-17
Hi guys, I did tried to search for my answer but fail

I recently lost my job and I want to learn Linux administration 

Would you say that learning Ubuntu server is the right path or should I choose Red hat instead?


my second question is I have downloading the Ubuntu server edition 64bit , would this also work on a 32bit x86 edition PC 


your advice and guidance would be much appreciated
:guitar:

---

### Post by arrrghhh on 2010-05-17
Some of the concepts you'll learn with Ubuntu administration will play over to other Linux OSes, but for the most part enterprises use other distro's if they have Linux servers.  Red Hat or SuSE are probably the most popular, I know all our Linux servers are SuSE-based.

Ubuntu is a great place to start, it's just the way certain things are done in Ubuntu are done differently in RPM-based distros.

---

### Post by TheStroj on 2010-05-17
I recommend Ubuntu, since all the servers i know are running it and it turns out to be really good :)

---

### Post by waheedrafiq on 2010-05-17
Okay it seems I have started a debate here , in simple terms 

what are the key different between lets say Suse based and Ubuntu

Both of you have confirm that you know many companies running this software can you name me few so I can compare. I really need to invest in the right software to get a job in UK 


and what about this X64 bit download of Ubuntu would this work on 32bit X86 system ?
:popcorn:

---

### Post by cascade9 on 2010-05-17
> **waheedrafiq said:**
> Would you say that learning Ubuntu server is the right path or should I choose Red hat instead?

my second question is I have downloading the Ubuntu server edition 64bit , would this also work on a 32bit x86 edition PC 


1- if you only have the time/resources to learn one, probably go for fedora/red hat. But its not a bad idea to learn as much as you posible can. 

2- nope, if your CPU is x86 only (not x86_64) then 64bit wont work. Check your CPU though, sometimes people get a nice suprise when they realise that the system they thought was x86 only turns out to be 64bit capable.

Edit- good luck ;)

---

### Post by dudumomo on 2010-05-17
Suse is indeed widely used. But Ubuntu too (at a different level)

You might start by the one of the easiest (Ubuntu) and then try Suse, as it will quite similar anyway.

For your second question, no, a 32b architecture cannot run a 64b OS. But, in some case, a 32b OS can emulate a 64b OS (If the CPU is 64b and with VT)

---

### Post by BobVila on 2010-05-17
If it's server sysadmin work, I'd like to throw CentOS into the mix. I love Ubuntu Server and use it at home, but our servers are all either RHEL or CentOS. Any way you go, you'll pick up a lot of useful knowledge. It's just the little things like /etc/network in Ubuntu and /etc/sysconfig/network-scripts/ in RHEL/CentOS that'll hang you up from time to time. A quick google will get you over those humps, though.

---

### Post by waheedrafiq on 2010-05-18
Thanks guy's for replying back so fast to this tread , I am going to study ubuntu first as I am used to the GUI side of things . is there a 32bit Server edition of Ubuntu ? if so where can i download it from because I can't seem to find it on here.

---

### Post by Jakob Lundberg on 2010-05-18
Go to [http://www.ubuntu.com/getubuntu/download-server](http://www.ubuntu.com/getubuntu/download-server)
an open the 'Alternative download options'. There you can choose 32 bit

---

### Post by arrrghhh on 2010-05-18
> **waheedrafiq said:**
> Thanks guy's for replying back so fast to this tread , I am going to study ubuntu first as I am used to the GUI side of things . is there a 32bit Server edition of Ubuntu ? if so where can i download it from because I can't seem to find it on here.

You're going to want the ubuntu-desktop download rather than the -server download if you want a GUI!

---

