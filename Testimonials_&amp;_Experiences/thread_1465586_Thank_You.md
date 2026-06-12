---
title: "Thank You"
date: 2010-04-29
forum: Testimonials &amp; Experiences
---

### Post by Hman242 on 2010-04-29
I would just like all the people that work on Ubuntu and the people on these forums thank you, thank you for the Linux Experience. Since using Linux/Ubuntu I have learned so much. The process of switching was painless, and the one hickup I had was tended to by the great community. 

Unfortunately I'm not currently using Linux/Ubuntu. I have bought a new laptop and when I tried to put Ubuntu on it, it made Windows unbootable. Me, the community, or HP customer support could fix the problem. I sent it back and got a replacement. I need Windows for a few things still, so I need to keep it around. I'm afraid that if I try again, even with taking precautions, it might mess it up once more. The reason I would be so worried about that, is that maybe I won't get a replacement for the laptop. April 29 has rolled around and there is now Ubuntu 10. I'm wanting to try Ubuntu on this machine once more, but even if I don't, I won't forget Linux/Ubuntu or the things it has taught me.

---

### Post by lisati on 2010-04-29
Sorry to hear of the troubles you experienced. Did you accidentally tell the installer to use the entire disk? Did you check out the "Try ubuntu without installing it" option?

---

### Post by Hman242 on 2010-04-29
No, I could still see the Windows partition in Gparted, and Windows was still there. It wouldn't boot however. I used a Windows 7 repair disk and still couldn't get the OS to boot. I think I might know what I did wrong, although I can really articulate my thoughts without making it confusing. Like I said, I will most likely be trying Ubuntu 10 on this system again.

You don't really need to be apologizing, I was thank the Ubuntu devs and the community. That includes you :P

---

### Post by Hman242 on 2010-04-30
The problem is what I thought it was, I'm not dual-booting Ubuntu 10 :) Man have I missed it.

---

### Post by WinterRain on 2010-04-30
If you tried to dual boot before the 29th, there was a widely publicized problem with grub not seeing other OS's which has been fixed in the final release of lucid. And a last minute fix at that.

You also could have done:
```
sudo update-grub
```
which would have fixed it.

Another option is to wipe windows altogether and run it in virtualbox. About the only thing you can't do with it is high end gaming. My xp install in vbox actually runs better than my native install. Go figure.

---

### Post by sixthwheel on 2010-04-30
> **WinterRain said:**
> If you tried to dual boot before the 29th, there was a widely publicized problem with grub not seeing other OS's which has been fixed in the final release of lucid. And a last minute fix at that.

You also could have done:
```
sudo update-grub
```
which would have fixed it.

Another option is to wipe windows altogether and run it in virtualbox. About the only thing you can't do with it is high end gaming. My xp install in vbox actually runs better than my native install. Go figure.

Actually I've been reading up on this in another thread, and it has not been fixed for some.
As a matter of fact, most are still having problems dual booting Win 7...However the good news is that 10.04 made the scheduled release date.

---

### Post by Hman242 on 2010-05-01
> **WinterRain said:**
> If you tried to dual boot before the 29th, there was a widely publicized problem with grub not seeing other OS's which has been fixed in the final release of lucid. And a last minute fix at that.

You also could have done:
```
sudo update-grub
```which would have fixed it.

Another option is to wipe windows altogether and run it in virtualbox. About the only thing you can't do with it is high end gaming. My xp install in vbox actually runs better than my native install. Go figure.
The problem was that I had four partitions and when I tried to make a fifth for Ubuntu, it made the four others secondary partitions. I could start the boot process of Win7 but it would restart the computer halfway into it.

---

### Post by WinterRain on 2010-05-01
> **Hman242 said:**
> The problem was that I had four partitions and when I tried to make a fifth for Ubuntu, it made the four others secondary partitions. I could start the boot process of Win7 but it would restart the computer halfway into it.

I subscribe to the KISS principle. Backup all your stuff on drives dedicated to storage. Then get 2 drives you want to dual boot with. Install windows on the drive of your choice, and shut down. Unplug the windows drive and install ubuntu/linux on the other drive. Shut down. Once both drives are plugged back in, just hit F12 or something similar to choose boot device. Easy.

---

### Post by Hman242 on 2010-05-01
Like I said I fixed the problem, so there's no need.

---

### Post by WinterRain on 2010-05-01
> **Hman242 said:**
> Like I said I fixed the problem, so there's no need.

I'm not trying to fix your problem at this point. Don't worry about it. Don't you realize that sometimes threads take on a life of their own?

---

