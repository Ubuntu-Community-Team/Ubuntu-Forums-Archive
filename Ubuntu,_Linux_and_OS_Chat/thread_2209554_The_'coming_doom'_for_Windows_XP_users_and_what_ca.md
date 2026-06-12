---
title: "The 'coming doom' for Windows XP users and what can be done..."
date: 2014-03-06
forum: Ubuntu, Linux and OS Chat
---

### Post by knarf2 on 2014-03-06
Fellow nerds of the net,

I read the below post from 'DuckHook' and reesponded:
[COLOR=#ff0000]
[IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **DuckHook** 					[/COLOR][[COLOR=#ff0000][IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG][/COLOR]]("http://ubuntuforums.org/showthread.php?p=12804001#post12804001")[COLOR=#ff0000] 				
[/COLOR]
[COLOR=#ff0000] 				[/COLOR][COLOR=#ff0000]Just posted on another thread about this very  topic. I run XP in a VM. I will disable the VM NIC come April 2014 and  thereby sandbox XP within the VM. It won't have any further  communication with the big bad outside world and will be stuck with  whatever I've now got installed on it and nothing more. If you can *religiously*  isolate XP this way, it should be as safe as anything else on your box.  If you reconnect the NIC and decide to surf with it, all bets are off."[/COLOR]

*My response was:*


 			 		 	 If the writer of the above post (or anyone else on the forum) can answer my question, I'd be grateful. 
This sounds like an interesting idea, however forgive my ignorance, but  how does one 'sandbox' a virtual XP and disable the 'NIC' (I assume that  stands for network card?). Note I use only a single machine for use at  home (not on any network). Thanks. 				

So to anyone out there who can figure this one out, I give my top nerd award out :) Do you think this is really possible? Would a person running XP inside Linux Ubuntu REALLY be safe from the 'doom' coming in April? If so what is the easiest way to set it up?

---

### Post by buzzingrobot on 2014-03-06
He's talking about disconnecting his XP-in-a-VM from the net.  That's all. (Yes, NIC is the network card.)

The threats that are worrisome about XP are attacks that use the internet -- a network, after all -- to get at it.  The same is true of any other OS connected to a network:  It is vulnerable to attacks distributed from other machines on that same network.  

The issue with XP support ending is that Microsoft will not be distributing new updates to counter new kinds of attacks that are discovered.  Malware is mostly a professional criminal activity these days, so it is presumed those folks will seize the opportunity to devise new methods to go after all those XP machines.

If your XP installation is not connected to the internet, then you are not vulnerable to malware distributed via the internet.  If that's the case, you've already done what this guy says he is doing.

---

### Post by knarf2 on 2014-03-06
> **buzzingrobot said:**
> He's talking about disconnecting his XP-in-a-VM from the net.  That's all. (Yes, NIC is the network card.)

The threats that are worrisome about XP are attacks that use the internet -- a network, after all -- to get at it.  The same is true of any other OS connected to a network:  It is vulnerable to attacks distributed from other machines on that same network.  

The issue with XP support ending is that Microsoft will not be distributing new updates to counter new kinds of attacks that are discovered.  Malware is mostly a professional criminal activity these days, so it is presumed those folks will seize the opportunity to devise new methods to go after all those XP machines.

If your XP installation is not connected to the internet, then you are not vulnerable to malware distributed via the internet.  If that's the case, you've already done what this guy says he is doing.

Thx 4 the reply Buzz... When he says detach the NIC, does he mean PHYSICALLY detach it or thru some software? Also, if it is a single computer, NOT on a network, and used in your home is it safe to assume that NO precautions whatsoever are needed? If that is true, then this is a solution for MILLIONS of people that is free and will introduce them to Linux.  What do you recommend as the quickest, easiest way to install and run VMware Xp in a Linux Ubuntu? Also does XP run well this way?

Thanks again from a budding nerd ;)

---

### Post by monkeybrain20122 on 2014-03-06
> **knarf2 said:**
> Thx 4 the reply Buzz... When he says detach the NIC, does he mean PHYSICALLY detach it or thru some software? 

You can choose the VM, go to Settings > Network and uncheck "Enable Network Adapter" (see screenshots)

---

### Post by buzzingrobot on 2014-03-06
Dunno what "DuckHook" meant, but as long as a machine isn't connected to the net -- wired or wireless -- it isn't connected to the net. Disabling the NIC, in or out of a VM, will do the trick.  So will turning off the wifi card and/or pulling the ethernet cable.

---

### Post by monkeybrain20122 on 2014-03-06
> **buzzingrobot said:**
>   So will turning off the wifi card and/or pulling the ethernet cable.

But you don't want to kill connection for the host. :)

---

### Post by 3rdalbum on 2014-03-06
> **knarf2 said:**
> If that is true, then this is a solution for MILLIONS of people that is free and will introduce them to Linux.  What do you recommend as the quickest, easiest way to install and run VMware Xp in a Linux Ubuntu? Also does XP run well this way?

It's no solution. XP is used because its users don't like change. If they wanted to install Ubuntu, even just for a Windows VM, they would have already done it.

XP in a VM is a solution for businesses that need to use custom-written software that only works on XP, but it will almost certainly be software that requires networking. Heck, the average Windows desktop really needs an internet connection anyway. The secure part of the idea was "no networking", not "VM".

XP in a VM will run slower than on bare hardware. 3D performance: nonexistent. The overhead of running two operating systems and emulating hard drives and other devices will have an impact. Core 2 CPUs and later have special virtualization acceleration features, earlier CPUs don't.

Also, please just say Ubuntu. Not "Linux Ubuntu". Linux is not a software company.

---

### Post by monkeybrain20122 on 2014-03-06
> **3rdalbum said:**
> 
Also, please just say Ubuntu. Not "Linux Ubuntu". Linux is not a software company.

But I believe that "Ubuntu Linux" is acceptable. :)

---

### Post by alex2e1gzy on 2014-03-06
Just wondering why you still want to run XP at all? There are better OS's (like Ubuntu).

As for secure - what if a virus looked for the VM on the host PC, then decided to infect your XP install? Not beyond the realms of possibility...

---

### Post by buzzingrobot on 2014-03-06
> **knarf2 said:**
> ... is a solution for MILLIONS of people that is free and will introduce them to Linux.  What do you recommend as the quickest, easiest way to install and run VMware Xp in a Linux Ubuntu? Also does XP run well this way?

  


I don't know what kind of protections, if any, are brought to XP by running it inside a VM.  Offhand, I'd say XP-on-the-net is XP-on-the-net, in or out of a VM. Maybe someone else can chip in here.

OF course, if someone does not need net access, they can just take XP off the net.  It's not like they'll be missing access to updates after the April end-of-life.

Honestly, if someone has a requirement for Windows apps, staying on Windows is the option I recommend, whether or not they're on XP or another version. So, upgrading to Win7 or Win8 seems to me the optimum solution for an XP user who needs to stay with Windows applications. Both Win7 and Win8, properly configured, are more secure than the typical XP setup. 

Now, if an XP user does not need to stay with those Windows applications, and is willing to do some homework initially to identify Linux apps that provide enough of the functionality of those Windows apps to get the job done, perhaps also adjust some habits, then migrating to Ubuntu, or another Linux, is certainly a very good and viable alternative.

[Can't answer your question about XP performance.  Last time I used XP was in 2001 just after it was released.  When I installed it and then immediately ran the updates, via a dialup link, the machine was infected before the updates finished downloading.  That was the last time I bought Windows and a day or so away from the last time I used Windows on my own hardware.]

---

### Post by knarf2 on 2014-03-06
> **buzzingrobot said:**
> I don't know what kind of protections, if any, are brought to XP by running it inside a VM.  Offhand, I'd say XP-on-the-net is XP-on-the-net, in or out of a VM. Maybe someone else can chip in here.

OF course, if someone does not need net access, they can just take XP off the net.  It's not like they'll be missing access to updates after the April end-of-life.

Honestly, if someone has a requirement for Windows apps, staying on Windows is the option I recommend, whether or not they're on XP or another version. So, upgrading to Win7 or Win8 seems to me the optimum solution for an XP user who needs to stay with Windows applications. Both Win7 and Win8, properly configured, are more secure than the typical XP setup. 

Now, if an XP user does not need to stay with those Windows applications, and is willing to do some homework initially to identify Linux apps that provide enough of the functionality of those Windows apps to get the job done, perhaps also adjust some habits, then migrating to Ubuntu, or another Linux, is certainly a very good and viable alternative.

[Can't answer your question about XP performance.  Last time I used XP was in 2001 just after it was released.  When I installed it and then immediately ran the updates, via a dialup link, the machine was infected before the updates finished downloading.  That was the last time I bought Windows and a day or so away from the last time I used Windows on my own hardware.]

Yes, that is EXACTLY the question: IS XP in Ubuntu VM somehow safer than 'real' XP?

---

### Post by lykwydchykyn on 2014-03-06
> **knarf2 said:**
> Yes, that is EXACTLY the question: IS XP in Ubuntu VM somehow safer than 'real' XP?

Inherently, the actual XP install itself is no safer.

Such a setup would afford a few nice security-ish features:

 - You could snapshot the VM and easily roll back to a clean system if it gets trashed.
 - If your XP gets trashed, you still have the host OS to use and your computer isn't a paperweight.
 - You can do risky things like web browsing and email on the host system, and limit XP use to things that require it.

So, basically, the XP itself isn't any safer; but the overall arrangement can be used in a safer way.  Of course, the user would have to actually use it this way, there isn't really any automatic benefit.

---

### Post by buzzingrobot on 2014-03-06
> **lykwydchykyn said:**
> Inherently, the actual XP install itself is no safer.

Such a setup would afford a few nice security-ish features:

 

Interesting, but easier said than done, I'm sure.

How to get Linux and a VM onto an existing XP machine, then install XP into the VM?? 

 Could the existing XP be used in a VM? If so, they just need to clear the dual boot hurdle. (They actually wouldn't necessarily need to dual boot.  They could leave their Window data as is, perhaps shrink the Windows partition(s), install Linux as the only OS, and mount the old Windows partitions where their data lives.)

Otherwise, they are probably looking at backing up their data, installing Linux as the sole OS, using their XP install media to install and update  it in a VM, and moving over their data from backup. (Before EOL, lest they lose the updates.)

Seems to me most or all of this would be a lot to ask of a Linux newbie.  A stroll through the "Absolute Beginners" section here provides ample evidence of the problems people have installing Ubuntu in a dual boot scenario.


I'd bet many, or most, XP users do not have install media.  If they do, they'd need to do all this before the EOL or face no leaving behind every update since their install media was released.

---

### Post by lykwydchykyn on 2014-03-06
> **buzzingrobot said:**
> 
Seems to me most or all of this would be a lot to ask of a Linux newbie.

Merely answering the VM question academically.

Without a doubt, any scenario other than a single OS installed directly on the hardware is too much to ask for the vast majority of computer users.  I have rarely been able to satisfactorily make anyone outside of IT or computer hobbyist circles even understand what a VM is (though this may be my poor elocution, who knows).

Most XP era hardware I've seen won't do a VM, at least not with a modern version of virtualbox on a modern version of Linux (somehow I managed to do it back in the day, but VBox and Linux have bulked up since then).

---

### Post by buzzingrobot on 2014-03-06
> **lykwydchykyn said:**
> Merely answering the VM question academically. 

Understood.  Just ruminating.

---

### Post by David_Wright on 2014-03-07
May I ask a (potentially) dumb question:

If you continue to run a dual-boot XP/*buntu system, using *buntu for any browsing, email etc and keeping XP for XP-specific programs (say, for example, Irfanview, which I love) will you be at significant risk if you are using XP while connected (via wifi/lan) but not *actively* online?

---

### Post by lykwydchykyn on 2014-03-07
> **David_Wright said:**
> 
If you continue to run a dual-boot XP/*buntu system, using *buntu for any browsing, email etc and keeping XP for XP-specific programs (say, for example, Irfanview, which I love) will you be at significant risk if you are using XP while connected (via wifi/lan) but not *actively* online?

If your XP system isn't being used:

 - to surf the web
 - to open email
 - with removable storage that gets used by other computers
 - with a public IP or on public wifi networks

Then you've eliminated the most common avenues by which malware propegates (unless I've forgotten any).   "Safe" is a tricky concept to guage, but I'd venture to say you're reasonably safe at that point.  I can think of a few situations where a machine like that could still be compromised; for example, we had a worm hit our network several years back that propegated over file sharing.  If your XP is configured with open file shares and you are on a LAN with an infected machine, you could be compromised.

---

### Post by monkeybrain20122 on 2014-03-07
By first telling people who come to this forum asking for help to dual boot with XP that they shouldn't bother. :)

---

### Post by SurfaceUnits on 2014-03-08
letting them crash and burn and have fun with Microsoft. If you enable someone to limp along with a vulnerable OS, you are half the problem. People aren't going to change until something felinostrophic happens

---

