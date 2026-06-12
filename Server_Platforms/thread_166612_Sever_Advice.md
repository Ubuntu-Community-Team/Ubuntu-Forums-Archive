---
title: "Sever Advice"
date: 2006-04-26
forum: Server Platforms
---

### Post by Socratez on 2006-04-26
I spent the better part of a day setting up my server and I am now getting down to the nitty gritty. The machine is a DUAL AMD 1600MP machine with 512MB of ECC DDR. I am going to try and run 3 virtual Host on this machine using GSX Server. I will be getting more ram in the near future but for now I am preying that a fine tuned Ubuntu server console will suffice.

I made sure i had SMP Kernel and the prelinking was installed. Besides that I am not sure what else I have to do to fine tune this puppy. I have 3x80GB doing a RADI5 array via Software. I have a 45GB doing the OS and virtual host partions. What I want to do is make sure that I am not starting any uneccessary services at startup time. I assume I need LVM for the RAID, cron for scheduling but besides that I am lost. I honnestly have no cluw how to even check at what is starting. 

Anybody lend me a hand with this one? If you need more of a background you can check out the blogg I started to keep track of this. Check out [http://cshowe80.blogg.com/]("http://cshowe80.blogg.com/")


Socratez

---

### Post by LordHunter317 on 2006-04-26
[QUOTE=Socratez]I spent the better part of a day setting up my server and I am now getting down to the nitty gritty. The machine is a DUAL AMD 1600MP machine with 512MB of ECC DDR. I am going to try and run 3 virtual Host on this machine using GSX Server. [/quote]You will find that very, very painful.

> I made sure i had SMP Kernel and the prelinking was installed. Besides that I am not sure what else I have to do to fine tune this puppy.Quadruple the RAM.  I'm not even joking.

> What I want to do is make sure that I am not starting any uneccessary services at startup time. I assume I need LVM for the RAID, cron for scheduling but besides that I am lost. I honnestly have no cluw how to even check at what is starting. Why do you care?  Ubuntu doesn't start much beyond what is required, and stuff that's not needed won't consume any resources.

---

### Post by Socratez on 2006-04-27
What do you suggest beyond that as a solution? I have ordered an additional 1GB of RAM for the machine. I did setup a 1.5GB Swap but that isn't gonna do much in way of helping me run the HOSTS. Is there a better virtualization server for my perticular setup? I tried using the ESX Server but it gave me a stop error. 

At this point I am either gonna replace the machine or add the Ram and prey I can make it work. 

Any additional input anybody??

Soc

---

