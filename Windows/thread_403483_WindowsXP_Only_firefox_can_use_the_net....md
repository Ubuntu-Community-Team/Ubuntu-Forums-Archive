---
title: "WindowsXP: Only firefox can use the net..."
date: 2007-04-07
forum: Windows
---

### Post by GSF1200S on 2007-04-07
Yeah, this is a windows XP problem.. I figure you guys might be able to help me with this one.

I booted up XP to play BF2 online, but it failed to connect. I tried Mozilla Thunderbird.. failure to connect to pop server. I tried IE7, and it failed to load anything. Yet, for some strange reason, firefox works without a hitch.. 

I know, the first thing I thought of was my firewall, but thats not it.. I shut it down and I still have the same problem. I know that Nod32 isnt doing it, so what the hell? Ive seen a lot of crap with XP but nothing like this. Ubuntu can access the internet freely using any program...

Thanks for any help...

---

### Post by aysiu on 2007-04-07
I've moved your thread to the Windows Discussions subforum, so people don't get confused.

I'm not really good at troubleshooting internet stuff, but I do have a few questions--the answers to which might help those who *do* know about troubleshooting internet connectivity issues.

1. Has it always been this way since you installed XP, or did something happen recently?

2. Does this problem apply to all users? If you haven't tried it yet, try creating a new test user and seeing if the test user experiences the same problem.

3. Does Opera work, too? Or just Firefox?

---

### Post by GSF1200S on 2007-04-07
> **aysiu said:**
> I've moved your thread to the Windows Discussions subforum, so people don't get confused.

I'm not really good at troubleshooting internet stuff, but I do have a few questions--the answers to which might help those who *do* know about troubleshooting internet connectivity issues.

1. Has it always been this way since you installed XP, or did something happen recently?

2. Does this problem apply to all users? If you haven't tried it yet, try creating a new test user and seeing if the test user experiences the same problem.

3. Does Opera work, too? Or just Firefox?

Oh dang.. I thought that this would be cool in General.. sorry bout that..

1) Windows XP used to work fine.. this happened recently. To be honest, Ive been using Ubuntu so much that I dont even know when this started.
2) Ill have to check this out. Im using administrator account on Windows, so Ill have to create a guest account and try that out. Ill edit this post after I try it..
3) Opera wont load anything either. Its strange.. ONLY firefox seems to work. When I booted up though, Nod32 said that it had successfully updated its kernel, meaning it must have connected to the internet.

Thanks for any help...

**Nope, a new user doesnt change anything either. When my firewall is up (Zone Alarm), it shows my other programs accessing the internet just fine, but they dont. This is a weird one..

---

### Post by aysiu on 2007-04-07
Have you tried temporarily disabling Zone Alarm? Maybe it's a Zone Alarm configuration (even though it *shows* other programs getting through).

---

### Post by GSF1200S on 2007-04-07
> **aysiu said:**
> Have you tried temporarily disabling Zone Alarm? Maybe it's a Zone Alarm configuration (even though it *shows* other programs getting through).

Yeah.. I completely disabled Zone Alarm.. I even hunted to see if it left processes behind in the task manager, which it didnt.

Its weird.. only firefox??? WTF?! I dont understand how this could be the case, unless for some reason the registry got messed up when I installed ZA because I had firefox open (ubuntu forums, go figure). Honstly the registry is the one thing on Windows I never had the balls to mess around with..

---

### Post by aysiu on 2007-04-07
I don't know either. I'm hoping someone who is an internet connectivity expert in Windows might jump in and help. Have you also posted in a Windows forum?

---

### Post by GSF1200S on 2007-04-07
> **aysiu said:**
> I don't know either. I'm hoping someone who is an internet connectivity expert in Windows might jump in and help. Have you also posted in a Windows forum?

Haha.. a windows forum- grrreeaaattt...... Ill give it a try and see if anyone helps.. :) 

To be honest, I would consider MYSELF a connectivity expert in Windows. Ive set up networks, configured firewalls by IP address/program, etc.. Either im just being a dunce right now, or this is a really weird one..

---

### Post by M$LOL on 2007-04-07
Have you checked IE to see if it is configured correctly? Tools -> Options and check Connection Settings IIRC.

---

### Post by GSF1200S on 2007-04-07
> **M$LOL said:**
> Have you checked IE to see if it is configured correctly? Tools -> Options and check Connection Settings IIRC.

Yeah.. everything was good.. Its not just IE7 though... Battlefield 2 cant connect, Opera cant connect, Windows media player cant connect, and amazingly, not even MOZILLA Thunderbird will connect.

Nod32 and Firefox seem to work fine (scratches head)...

---

### Post by igknighted on 2007-04-07
Not to be a downer, but I had the same issue a while back on my parents computer (except it was Opera that was the only thing that would connect).  I never could fix it, so I ended up reformatting and reinstalling.  That computer needed it anyway tho, so it was a good excuse :).

---

### Post by GSF1200S on 2007-04-07
> **igknighted said:**
> Not to be a downer, but I had the same issue a while back on my parents computer (except it was Opera that was the only thing that would connect).  I never could fix it, so I ended up reformatting and reinstalling.  That computer needed it anyway tho, so it was a good excuse :).

I wouldnt have a problem with this if the disc I got with my computer wasnt a recovery disc. If I use the recovery disc, Id have to repartition and reinstall Ubuntu as well as windows.

---

### Post by Hex_Mandos on 2007-04-07
I thought it could be blocked ports until you said Opera isn't connecting either. Something similar happened to a friend, who subsequently switched to Ubuntu.

---

### Post by LookTJ on 2007-04-08
Have you had the balls to mess with group policy? and edit the connections settings?

---

### Post by mister_p_1998 on 2007-04-08
Strangely I had this exact problem in one of our support units after XP updated to IE7, it kept asking for a proxy IP. I rolled back to IE5 and all was well in the world again.
Try that.
Steve

---

### Post by GSF1200S on 2007-04-08
> **mister_p_1998 said:**
> Strangely I had this exact problem in one of our support units after XP updated to IE7, it kept asking for a proxy IP. I rolled back to IE5 and all was well in the world again.
Try that.
Steve

I thank you all for the comments.. All I can say is, dont EVER trust Zone Alarm. I even had closed ZA and kill any remaining processes, and nothing would work.

Finally, I decided to completely uninstall ZA, and wham, everything works. I think maybe I should just run Nod32 and leave it alone...

**Hell, I had Outpost firewall dictating what ports the programs could use, and ZA was set at medium with no port control or rules. ZA has really gone downhill...

---

