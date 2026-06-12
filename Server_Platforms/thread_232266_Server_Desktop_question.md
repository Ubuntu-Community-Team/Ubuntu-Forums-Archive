---
title: "Server Desktop question"
date: 2006-08-08
forum: Server Platforms
---

### Post by jreid08 on 2006-08-08
Hi, this is my second question to the forums.  I'm new to Linux and working on about a week with Ubuntu.  Before that I was farting around with SLES before I decided it was way to big for me being a newbie and all.

My question is this.  I'm concerned about security now that I've installed the desktop on my Ubuntu LAMP server.  I couldn't help but notice all of the extra services now running, not to mention that my server is now seeing my internal home network.  I'm assuming this is not good since I eventually want to make this my production server for the web.

What's the fix for this?  Or should I reinstall LAMP and leave the desktop alone?  Maybe it doesn't matter if there's a desktop or not since I'm so new to Linux maybe there was a way to my home network for example but I just didn't know it.

Thanks!
JR

---

### Post by x64Jimbo on 2006-08-08
Just make sure you're running a good firewall. Try installing firestarter from synpaptic. That should get you started. You can then get as nitpicky about your security as you want. Also, if you have a router between you and the internet, I'd recommend going in there and configuring manual port forwarding on only the ports you want for your LAMP stuff to your desktop machine. I have a friend who runs his entire website off his desktop that has a full KDE GUI, VNC, etc. You just have to be cautious about your security, that's all. It'll be a good experience for you.

---

### Post by jreid08 on 2006-08-08
I'm running IPCop with a Netgear router on the "green" network.  I also have a Netgear switch on the "orange" network for when I eventually make the server public.

Is that good enough?  

Perhaps I'm too paranoid but I'm wondering if people will still be able to find a backdoor because of the desktop running on my server even though I have ports 80 and 22 and so on activated and nothing else at my firewall.

Thanks,
JR

---

### Post by printmkr on 2006-08-08
Another great option is Smoothwall, particularly if you have a REALLY old box and a few NICs around. [http://www.smoothwall.org/]("http://www.smoothwall.org/") Rock solid, great GUI and documentation, and a real supportive community on the forums. I run it on a box I picked up for $20!

---

### Post by x64Jimbo on 2006-08-08
There are always risks involved when you are running any software, period. It's not like you're running the IRS website or anything, so I am pretty sure you don't have anything to worry about.

---

### Post by jreid08 on 2006-08-09
> **x64Jimbo said:**
> There are always risks involved when you are running any software, period. It's not like you're running the IRS website or anything, so I am pretty sure you don't have anything to worry about.

I know, I read alot and I don't want to become part of some zombie network.

Thanks for the help,
JR

---

### Post by x64Jimbo on 2006-08-09
Don't listen to the Microsoft anti-Linux propoganda. Zombie nets are made up of Windows machines.

---

### Post by Viruk on 2006-08-09
> I'm running IPCop with a Netgear router on the "green" network. I also have a Netgear switch on the "orange" network for when I eventually make the server public.


from that description it sounds like theres a smoothie there already...

---

### Post by jreid08 on 2006-08-10
> **Viruk said:**
> from that description it sounds like theres a smoothie there already...
Yes, there is security there - It sounds like I'm good to go and I appreciate the comments.

Thanks all
JR

---

