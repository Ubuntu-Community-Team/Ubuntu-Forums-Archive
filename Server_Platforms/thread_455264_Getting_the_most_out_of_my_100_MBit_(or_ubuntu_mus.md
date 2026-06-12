---
title: "Getting the most out of my 100 MBit (or ubuntu must not be the bottleneck)"
date: 2007-05-26
forum: Server Platforms
---

### Post by johnman145 on 2007-05-26
I am running an amd1800+ (512MB ram) with ubutntu 7.04  which will connected to my 100 MBit connection soon. It will not only be a server with firewall but also a router for my personal desktop. Just to test the efficiency of ubuntu i uploaded some big files to my server (80-95 MBit upload speed) which needed 20% of the cpu. When i start snort, it needs something like 30% on its own (during the ftp transfer).
So i'm wondering, is my linux save "enough" without snort and with a pretty strict firewall? I don't want ppl abusing my 100 MBit connection so if snort is 'needed' then i can live with it, but i prefer not to loose 30% of my processor performance. Since my expertise is not really with linux i hope someone can give his "professional" opinion. I'm a bit worried if my server is busy my desktop internet connection might deteriorate.

---

### Post by craigp84 on 2007-05-26
I'm not convinced by using snort in this kind of situation. But i see both sides to the argument and if you feel you need it then fine, go for it.

The CPU usage is probably about right from what you describe - i don't think you have anything to worry about with the internet connection though, your box is plenty beefy to act as a complex, deep packet inspection firewall, with your snort installation and still act as a filer etc. for a small lan of computers.

Offtopic: or this kind of activity, i find Solaris 10 wins hands down for speed. If load becomes an issue and you can't move to different hardware, consider giving sol10 a try.

---

### Post by johnman145 on 2007-05-26
On closer inspection i noticed the ftp server only takes 20%+ but the server system has a load of 70-90%. I can't see what part of the system is taking up the other 50%. Anyway, i don't have much spare cpu room under heavy load so i don't think i will use snort unless i absolutely need it.

But you suggest solaris and the only thing i know pretty good is winXP. The thing i am looking for is a lamp+ftp box with superb security. A webmin sort of interface is nice, but nut absolutely needed. Do you think solaris is a good alternative for my demands ?
Although ubuntu is adequate, its not exactly the clean out the box, ready to run, plug and play LAMP what i was really looking for so im still open for alternatives :D.

---

### Post by craigp84 on 2007-05-26
> On closer inspection i noticed the ftp server only takes 20%+ but the server system has a load of 70-90%.

When you run "top" and order by cpu usage (the default) you should see what's consuming CPU. Also look for the kernel (which includes your iptables firewall) usage in the %sys readout at the top (next to %user).

> Anyway, i don't have much spare cpu room under heavy load so i don't think i will use snort unless i absolutely need it.

I wouldn't be too concerned about maxing the CPU at 100% - it just means all the CPU time slices are being allocated - nothing more and nothing less. It's not the all encompassing signifier of system usage that the term may suggest it is.

There are other indicators you should look to: keep an eye on the run queue, if you see processes beginning to back-up then yeah, you're possibly too loaded (so long as they're not backing up on I/O etc.), but otherwise, keep chuckin stuff at it :-) it can handle it ;).

I would ditch snort anyway, for other reasons though.

> But you suggest solaris and the only thing i know pretty good is winXP.

Maybe winxp's the way to go then (or win server). It really depends on how much blood sweat and tears you're willing to throw at the problem you're solving. There's one thing that's sure about linux, it's different from windows.

It doesn't matter what gui's, front ends and other niceties you throw on there, it just works differently - and despite all the "user friendly" hype, it's a pretty steep learning curve for someone coming from a different OS - there's a lot of learning, you've gotta be sure it's worth it. Put a dollar figure on the problem and each possible solution is my boss's usual answer when i'm grouching out loud. To be fair he's kinda right, you just have to be aware that the lowest dollar figure is not always the correct choice (but i'll be damned if he'll take on board that argument!).

> The thing i am looking for is a lamp+ftp box
Trivial to setup, anything can do that (well, without the L in Lamp obviously :) - even windoze). Solaris Express Developer Edition comes with this setup out of the box, and thanks to the new "Secure by Default" policy, only SSH is visible over the network after install.

> with superb security
Someone (i forget who) once said, "security is a journey, not a destination". If you can get your head around that - and it's not as trivial as it first appears - then you're on the right path.

I guess what i'm saying here is that "superb security" is not a check-box item. It's rooted in your approach rather than the product you're using. Even Windoze can be secure - i used to look after some windoze servers, i guarantee they're more secure than some ubuntu boxes i see :(

> A webmin sort of interface is nice

Really? I don't like that at all :( You can't grep an interface, and that's where it all falls apart for me. The command line (ksh or above) is really way too powerful a tool. It takes some learning though which is it's main detractor.

> Do you think solaris is a good alternative for my demands ?

It's six and half a dozen to be honest. Any major OS will fill your need here - Linux (almost any distro), Windows XP or Server 2003, Solaris etc. etc. Solaris 10 probably wins out on performance and general rock-solidness. It's still going to be a learning curve, and if you've no prior experience with either, then Ubuntu wins just because of the size of the community - which translates to lots of people who can help you by answering your questions, or writing up their experiences when they did what you're trying to do.

> Although ubuntu is adequate, its not exactly the clean out the box, ready to run, plug and play LAMP

Yeah, it's more of a desktop distro at this point to be honest. Sure you can mould it to be a server, but that's time you're going to have to invest. What about going for one of the dedicated LAMP distros?

I see so many posts on here about "i want to make a file server with Ubuntu & SAMBA, but i find it tough because i don't understand X and Y just doesn't work, also my version of Z doesn't have feature P compiled in and i need to recompile but i don't know how to". Clearly it's a case of "new hammer" syndrome - Ubuntu is the hammer, and every computer related problem is the nail. I always refer them to [www.openfiler.com](www.openfiler.com) - but i appreciate no one is ever going to heed that advice. OpenFiler isn't a hyped up hammer of the week - well not this week anyway :(

> ready to run, plug and play LAMP what i was really looking for so im still open for alternatives

Speak to some hosting providers. Sure it'll cost some cash, but it'll be ready to run, and easy to look after. It boils down to that dollar figure thing again, remember cheapest doesn't always mean best.

Hope this helps,

-c

---

### Post by johnman145 on 2007-05-27
> When you run "top" and order by cpu usage (the default) you should see what's consuming CPU. Also look for the kernel (which includes your iptables firewall) usage in the %sys readout at the top (next to %user).
Yes, i always thought that to, since top only shows a usage of 20-30% for proftp. But now i use htop, somehow the kernel uses a lot more cpu%  but i can't see which thread is causing this:
[http://img483.imageshack.us/img483/2438/puttyuo1.png](http://img483.imageshack.us/img483/2438/puttyuo1.png)

> I wouldn't be too concerned about maxing the CPU at 100% - it just means all the CPU time slices are being allocated - nothing more and nothing less. It's not the all encompassing signifier of system usage that the term may suggest it is

There are other indicators you should look to: keep an eye on the run queue, if you see processes beginning to back-up then yeah, you're possibly too loaded (so long as they're not backing up on I/O etc.), but otherwise, keep chuckin stuff at it it can handle it .

I would ditch snort anyway, for other reasons though.


My server will soon do some other stuff also, and i expect the cpu becoming a bottleneck. I want apache to perform some heavy calculation. I tried it in php and the cpu took 2 minutes (100% load amd2800+ )for a small job. I hope i can reduce this by using a custom made c program (although i still don't know how to let apache execute shell commands), but my guess is that the processor will be the bottleneck. So im saving up my cpu cycles as much as possible :D.

> Maybe winxp's the way to go then (or win server). 

Well, actually my point was that although i don't know linux very good, i still managed to have it running with firewall ssh and everything i want it to have. But since i dont know linux, i have no problem switching to solaris in a blink of an eye if i think that could help.

> Trivial to setup, anything can do that 
I tested 4 distro's and installed linux 9 times before i was satisfied. Maybe its me but my first real encounter with linux was not trivial.

> Someone (i forget who) once said, "security is a journey, not a destination".
I read that a lot, but i don't really agree. If you have to update the linux server every week/month it seems to my it just isn't save. I see it like a fault in the bank. If some repair man has to come by every week with some glue to fix the lock on the main fault because the lock keeps falling off, i think its insecure by design. I was hoping my ubuntu box would be safe now and for years to come even if i don't update anything. But seeing all the topics about snort/firewall's and servers which' security have been compromised i'm not sure its any saver then a reasonably good configured win box.

> It's six and half a dozen to be honest. Any major OS will fill your need here 
Maybe it helps to explain this a little more elaborate.  If i configure my router's firewall i can just click a couple of buttons to block everything and then use NAT to allow http+ftp acces to my server. Nothing difficult, just a plain easy webinterface. 
When i configured the firewall of linux i had to do all sorts of things to get it to work. after hours and hours experimenting and reading i found out i should run a kernel module called ip_conntrack_ftp. Until then i wasn't even aware of the concept of a kernel module for something as basic as allowing ftp access. In my router i just enable some options in Stateful Packet Inspection and im done. No fuss, no kernel modules or ip-tables. I also tried to use the documentation of the shorewall firewall, and i have to say it is horrible from an average user's point of view. I have never ever had any real problems configuring a firewall, until that moment. And when you screw it up a little, the firewall goes into safe mode and blocks everything.  And that is JUST the configuration of the firewall. My router's firewall also provides protection against "IP Spoofing, Land Attack, Ping of Death, IP with zero length, Smurf Attack, UDP port loopback, Snork Attack" etc etc so i thought i want that too in my linux box and i ended up with snort. Im still not sure exactly what it does, but it's documentation is 130 pages !. I have heard that you are closer to the hardware with linux and i think that is true. The ip-tables firewall is a nightmare to configure the first time if all you want to do is allow ftp+http access.  Sometimes linux makes me feel like i have to pick up my casio handcalculator and help it do all the math. 

> [quote]A webmin sort of interface is niceReally? I don't like that at all  You can't grep an interface, and that's where it all falls apart for me.[/quote]
With webmin i can SLOWLY learn linux and how it works. With webmin i have the choice to point and click or to use a terminal (i always have both when i work on my server). This makes the transition a lot smoother if you don't know any commands at all. It's just like shortcut's in program's. Its nice to have them and it can improve the working speed a lot but only when it is an option besides the the normal interface. Imagine how word would be if you could only use shortcuts. First you have to learn the os/program or whatever and then you can learn how to use it efficiently. IMO the immensely steep learning curve of linux is partly caused by the lack of easy point and click systems. If you get stuck with linux (broken GUI for example) you are REALLY stuck, while in windows i just go in safe mode, install a new driver or remove the old one. I also think the linux forums are not a 'feature' but more as an nessecity exactly because of these kind of problems. 


> What about going for one of the dedicated LAMP distros?
I tried suse and my xserver (is that what the gui is called?) was broken after 30 minutes when i used the nvidia driver and after 3 hours of trying to repair it i removed it again. The reason why i updated the drives was because the font looked horrible and i thought that might help. I have also centos  and some other but i only wanted a lamp and ubuntu somehow got my choice. If i would have to decide again, i would go for the good old stable debian release. But since i haven't tried that one i don't know how good it is.

> Speak to some hosting providers. 
I already bought myself a domain+ 3GB space & 60 GB traffic. But i like to try a little of everything :D. With a 100 Mbit connection coming out of my wall i can also host myself.

---

### Post by Wim Sturkenboom on 2007-05-27
If you want to setup a server, you don't need a GUI so you don't have to worry about video-card drivers.
For servers, I suggest that you have a look at Slackware. I'm happily running Slack 10.1 (at work) and Slack 10.2 at home.

If I see the questions here about lamp servers and see how easy it was to set one up in Slackware (without prior knowledge), I definitely prefer Slackware.

---

### Post by craigp84 on 2007-05-27
You are quite severely misguided, but i don't have the time to explain it all.

I really suggest you go back to windows for now, Linux will *not*, it cannot solve your problems. Your problems are not technical. Go back to what you know, you have a fighting chance there but you are clearly out of your league here. Ordinarily i would say keep plugging away, you'll get there. But you don't read manuals, you expect the software to be your sysadmin (i.e. do your job).

Do not, go live with a Linux box in production, you are only going to contribute to the "hacked" statistics.

There is no product in the world will make you a sysadmin, you must learn that skillset. Invest in some classes.

-c

---

### Post by johnman145 on 2007-05-27
I have studied a couple of years computersciende university level, its not that i dont know anything about computers. In fact i DO read manuals, and i read them a lot. But before i dive in i usually ask a pro beforehand where i will finish. If that is not what i had in mind i save myself a lot of trouble. I have developed on many systems, linux and windows and  even fpga's and also in many many programming languages so i do have some experience with computer "stuff". 

Currently i need a very good lamp box and i think linux is still the best option, even though the documentation isn't that good.   

And if my assumptions are wrong, i wouldn't mind if you or anyone else can correct them ;)

---

### Post by leexgx on 2007-05-27
with the regards to CPU use most network cards do not have hardware TCP offload so CPU kernel use can be high when sending large amount of data fast (if you can get it to do it) should have an look for network cards that have hardware offload intel and 3com come to mind but there are others

---

### Post by johnman145 on 2007-05-28
> **leexgx said:**
> with the regards to CPU use most network cards do not have hardware TCP offload so CPU kernel use can be high when sending large amount of data fast (if you can get it to do it) should have an look for network cards that have hardware offload intel and 3com come to mind but there are others

That is exactly what i thought, but when i browsed on a dutch forum a lot of ppl posted 3com has even a worse cpu load then the realtek cheapo cars i am using. Intel cards are pretty good from what i read. Anybody got some hands on experience about the cpu% i can save with an intel card on ubuntu ?

@ wim im using the ubuntu server edition without gui. Although i hated it at first since i dont know the commands very good, i think webmin and ssh are working together pretty good and im actually beginning to like the terminal interface since i then can connect to it from my own personal computer on my desk. I havent looked at slackware but i'll have a look now to see if it fancies me :) (im downloading it now, 3.7 GB seems kind of big for a lamp)

---

### Post by Wim Sturkenboom on 2007-05-28
I assume it's Slack 11. I don't have experience with that one, but you probably could have settled for the first disk (CD) only.
Further you don't have to install everything, just the stuff that you need.

The 'official' slackware forum is on LinuxQuestions.org ([linux distributions >> slackware](http://www.linuxquestions.org/questions/forumdisplay.php?f=14))

---

### Post by Chayak on 2007-05-28
If you're serious about that kind of connection speed along with a firewall you need to look at a Cisco's integrated services routers.  The 1800 series should cover your needs.

---

