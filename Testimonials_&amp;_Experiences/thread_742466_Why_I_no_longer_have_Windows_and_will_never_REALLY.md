---
title: "Why I no longer have Windows and will never REALLY have windows!!!"
date: 2008-04-01
forum: Testimonials &amp; Experiences
---

### Post by Lichig0 on 2008-04-01
I was thinking it should be in serious discussion but i put it here

Ok it started out with my hard drive failing. And I had Windows installed on lets say HDD1 and Linux installed on HDD2. Now the hard drive that is failing is HDD2. Of course I like Linux more than Windows. So what my plan was to, Back up my MOST important files like my Downloads folder(do no porn I don't need nor the time to watch that) and my Science Labs. i saved some hard to get ROMS too. Either way it was hard to get it to fit on a DVD.
   After all that was backed up I Installed Ubuntu on HDD1 right over Windows so I would no longer have it. My intention was to install Windows on the failing HDD(HDD2) assuming I would use it less(it was/is the little motor that spins the disks that is failing, you can here it from a mile away). Any ways after I had Ubuntu installed(might I add is a pain in my *** because it uses a resolution my crappy monitor cant display so I have to find an much older and uglier monitor to install it) I would copy the rest of my files to HDD1. There for I could install Windows without data loss.
  My "favorite" part, installing Windows. I figure everything is all good to go and windows is scanning my hardware and it finally asks if I want to Install, Repair, or quit. I choose install. then it asks me what partition to install on. Now take note that there is a large size difference in size between HDD1 and HDD2. HDD1 is 160gigs and HDD2 is 40gigs. So don't be a jack *** and say I selected the wrong drive, I KNOW I DIDN'T I WENT THROUGH THIS 3 TIMES, 5 IF YOU INCLUDE THE PAST REINSTALLS!!! I select drive D: (HDD2). Now the first time I thought it was going to format the drive I chose, D:, but then it goes and asks if I want to format drive C: (HDD1). so i choose yes. when that was done I realize it just formated HDD1 because of the size. Reinstall Linux on HDD1. I go for it again. This time I double checked which drive I selected. It still insisted to format dive C: (HDD1). So when it asked me that I chose my only other option, quit. After that I was pissed to find that Windows yet again did something to drive C: (HDD1). So I again had to install Ubuntu. what is really weired is that HDD2 still had its Linux folder on it, but it wouldn't boot, thats when I figured at some point in the Windows installation it changed how the HDD's are read, so that previous install was unnecessary. Now I was desperate. I open up my computer and swap the positions of my HDD's(assuming Windows wants C: ) so i swap their positions AND their jumpers. This time not caring how Linux will react to that nor how grub will react to that. everything is all good and then it gets to the select partition. Nothing is there. about 2-3 seconds after that, BLUE ******* SCREEN. I go back, checked the cables and jumpers. there are tight, and in the right spot. Same result. Well maybe I have them too tight. Same results...I did playing around with that about 4,no 5 times...I gave up.
   I swap the HDD's back and find that my computer isn't booting anything. Now I think I may have ****** up my IDE or power supply. But before I jumped to conclusions I through in the Ubutnu disk, it installs no problem. When I was installing I took note of three things. I wasn't asked how much of the HDD I wanted to take up, both HDD's were their, and i wasn't asked what I wanted to import from the other OS. That can only mean that both the HDD's where wiped clean from the god damn blue screen. You can say that all my memory was wiped, 130 gigs of data(4 years worth), because that the other HDD could not be in right but, remember, it showed up in the installation of Ubuntu.
   I now refuse to let Windows have any control. so now i have it contained in a Virtual Machine....VMware player. 
Let me know if I missed a detail...or if I have to explain something that I didn't screw up.

---

### Post by dark_harmonics on 2008-04-02
I wholheartedly agree with  your decision to use it in a VM. Virtualbox is my VM of choice but VMware player works too. The only thing i wanted to mention is that you can use the alternate install ISO to install in text mode and possibly avoid that seperate monitor, if that still doesnt work, try the different video modes. that way maybe you wont need to hook up a second monitor.

---

### Post by mister_pink on 2008-04-02
The windows XP installer is a nightmare. I always have to unplug all my other drives to ensure it doesn't touch them. It seems to only need one drive to install on but if there's others there it insists on extracting files onto them, and it seems to totally disregard which drive you want to put it on too.

---

### Post by LowSky on 2008-04-02
I always install windows first (and disconnect every other drive), then linux... boots much happier

---

### Post by Moop on 2008-04-02
Windows always wants to put the boot files on what it decides is the first hdd even if you're installing it to another hdd. 

I'd guess that your partition table was messed up and your data would be recoverable if you haven't already overwritten it.

---

### Post by N1N31NCHN41L5 on 2008-04-02
Had similar issues and after a few reinstalls of windowes and ubuntu - found that if i installed windows and then ubuntu - and put it on the SAME drive as windows using a new partion n- then both OS's peacfully co-existed.

---

### Post by ugm6hr on 2008-04-02
Not a support request, so moved to Testimonials.

---

