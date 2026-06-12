---
title: "Windows Authorization Crap"
date: 2007-04-23
forum: Windows
---

### Post by GSF1200S on 2007-04-23
Hey all.. Ive a few political questions about the money hungry competing OS, Microsoft.

I have a dual boot setup with XP on one partition, and Ubuntu 7.04 on the other. Recently, I installed WinXP on virtualbox. It works fine...

My question is about the activation. Of course, the windows on my virtual box is pestering me about "activating" windows within 30 days. So, is it legal by there terms to use MY purchased copy of Windows twice on the same machine (actual install and virtual install)? If not, what can I do to run this virtual machine after the 30 days? Im sick of MS's crap.. all im doing is using my own copy of Windows in a virtual environment... Will I have to reactivate my actual install after I validate the virtual one?

Any info would be great..

**Edit** What do I tell MS when I call to activate it? Will I have any issues when going back and forth between my real install and my virtual one, due to MS recognizing 2 versions with the same CD key being used?

---

### Post by azkehmm on 2007-04-23
I haven't read the windows license agreement very caregully, so I'm not sure if I'm right. But.. as far as I know, a windows license allows you to use you window copy on 1 machine. I have no idea if it says anything in the eula about a virtual machine, but if it doesn't, it should be legal to use it in a virtual enviroment, since you're still on the same physical machine. Now, to convince microsoft to let you activate your copy, that's another story :)

---

### Post by jpatton on 2007-04-23
azkehmm is correct, the license allows you to use one copy per machine, the end.

My question would be, if XP works fine under virtualbox, cool app btw, then why not wipe XP off your drive, let Fiesty have the whole drive and run XP under virtualbox only? It will tell you the product has already been activated, then just call up and say you wiped it off your main drive and are running it under a virtual environment. They should give you an updated key that will allow that copy to activate and have access to the Windows Genuine stuff like updates ;)

btw, that would also work under the current config, the only problem is that when booted into the non-virtual XP, at some point it will announce that this copy isn't genuine. 

To avoid going on too much longer, when I was an instructor I had heard that a few students had called MS and stated that they were in school and as part of the class were required to reinstall windows on a regular basis and if there were a way to unlock it. But I can't verify that option.

Good Luck!

---

### Post by GSF1200S on 2007-04-23
Ughhhh.. If I only wasnt into computer games. I need the actual copy for playing games, and thats the only reason.

So, I cant have 2 copies in the same machine.. that sucks and its BS. God forbid I even mention this, but can I crack the virtual install? I mean dang.. its my copy of windows. 

Let me get this straight as well.. If I were to call them and tell them I had to reinstall windows on the same machine with different hardware, then all would be good until one of them popped up with a message that my windows isnt genuine?

Do they have some kind of messaging service within the OS that checks MS servers to see if the same CD Keyed XP is being used twice? Can I block it with a firewall?

I dont even understand how they manage to figure out that the OS is being used twice.

If absolutely necessary, I can block all internet traffic in and out of the virtual machine with the exception of my shared folder connection, and d/l any program needed for XP in Linux and transfer it over.. I figure that way as soon as I get it activated, blocking all internet connectivity will prevent my master (actual installed partition version) from popping up with a "not genuine" version, while still allowing me to use both. Will this work?

Sorry if I seem a little angry.. I hate how EXTREME they are with their greed, especially after getting used to  Linux's freedom approach.. Thanks for the responses.. hopefully Ill get this figured out,

BTW.. I know there is 2 stages of this verification crap. The first one requires you to "activate" the copy of Windows, and other is installed onto windows via the updates. My virtual machine doesnt have any updates installed at ALL! It doesnt seem dangerous because Windows is just another port using bandwith to Linux.. Anyways, since I havent updated the virtual machine with the second stage of their WGA crap, does this change anything?

---

### Post by m.musashi on 2007-04-23
For what it's worth, the activation data is only kept for about 6 months. After that if you install on a different computer it doesn't seem to care. I only get hit with problems when doing to many reinstalls in a short amount of time. I installed my copy of XP in vmware and activated it without issue. In fact, I even had to reinstall it when I fried vmware it still worked.

Also, EULA says one machine but doesn't preclude VMs (for XP). I bet you can make a case that since only one copy can run at any time and it's the same computer that it doesn't violate the EULA. Now if you put on other computers in a VM I think you would have problems.

---

### Post by matthinckley on 2007-04-23
have you tried activating the VM over the internet? only if it doesn't work will you have to call MS, and they usually won't give you any gruff.  If they do just tell them you had to replace your hard drive.  As far as your copy that is installed already, if it has been activated already you don't have anything to worry about.  The install should not be marked as not genuine unless the key has been flagged by Microsoft as not genuine.  They usually do not do this to legitimate keys unless the key has been reactivated way too many times within a short period of time.  Most of the time the not genuine keys are old volume license keys that have expired.

---

### Post by mips on 2007-04-23
As far as I know you are only allowed one instance of XP per machine. You have installed one on the Physical PC & one on the Virtual PC. MS requires you to have multiple licenses for this setup. Those installs are technically speaking on two seperate 'machines'

Do a google search about MS OS & Virtualization and you will get the idea why so many people are bitching about this.

---

### Post by GSF1200S on 2007-04-23
> **m.musashi said:**
> For what it's worth, the activation data is only kept for about 6 months. After that if you install on a different computer it doesn't seem to care. I only get hit with problems when doing to many reinstalls in a short amount of time. I installed my copy of XP in vmware and activated it without issue. In fact, I even had to reinstall it when I fried vmware it still worked.

Also, EULA says one machine but doesn't preclude VMs (for XP). I bet you can make a case that since only one copy can run at any time and it's the same computer that it doesn't violate the EULA. Now if you put on other computers in a VM I think you would have problems.

Hmm.. excellent point. Let me just confirm: youre dual booting and you have a Virtual install? You dont have any issues with having to activate either the virtual or actual install? That last point is gold.. I will give it a shot- I mean whats the worst they can do? Tell me I can only use one or the other? Hell even if they said I couldnt use Windows anymore it wouldnt break my heart..lol :).

Id still really like to know how the hell they keep track of the fact that 2 copies of Windows are running!?

---

### Post by GSF1200S on 2007-04-23
> **mips said:**
> As far as I know you are only allowed one instance of XP per machine. You have installed one on the Physical PC & one on the Virtual PC. MS requires you to have multiple licenses for this setup. Those installs are technically speaking on two seperate 'machines'

Do a google search about MS OS & Virtualization and you will get the idea why so many people are bitching about this.

Dang! Im on it now.. whatever I find out Ill post back here.

If anyone can add on to this, or knows a way for me to crack it (I will isolate internet and move all files in via cdrom and the shared folder network), great...

---

### Post by m.musashi on 2007-04-23
> **GSF1200S said:**
> Hmm.. excellent point. Let me just confirm: youre dual booting and you have a Virtual install? You dont have any issues with having to activate either the virtual or actual install? That last point is gold.. I will give it a shot- I mean whats the worst they can do? Tell me I can only use one or the other? Hell even if they said I couldnt use Windows anymore it wouldnt break my heart..lol :).

Id still really like to know how the hell they keep track of the fact that 2 copies of Windows are running!?

Confirmed. I have a legally purchased copy of XP installed on my computer and also installed in Ubuntu via vmware. The physical install is close to a year old and when I installed in vmware I activated with no hassles. I did have to call MS some years ago after reinstalling too many times and they just asked a few questions and that was that. If you bought an actual CD this is much easier than if you are using an OEM. MS doesn't allow you to move an OEM install to a different computer. If it's been a while since you activated I doubt you will have any trouble. I doubt you will have any problems - of course I can't guarantee. If you do, just call them and explain. The worst they will say is you can't do it. I really don't think they can take your XP away. 

I'm pretty sure we would get in trouble if we try and tell you how to crack the activation but google is your friend here.

---

### Post by GSF1200S on 2007-04-23
> **m.musashi said:**
> Confirmed. I have a legally purchased copy of XP installed on my computer and also installed in Ubuntu via vmware. The physical install is close to a year old and when I installed in vmware I activated with no hassles. I did have to call MS some years ago after reinstalling too many times and they just asked a few questions and that was that. If you bought an actual CD this is much easier than if you are using an OEM. MS doesn't allow you to move an OEM install to a different computer. If it's been a while since you activated I doubt you will have any trouble. I doubt you will have any problems - of course I can't guarantee. If you do, just call them and explain. The worst they will say is you can't do it. I really don't think they can take your XP away. 

I'm pretty sure we would get in trouble if we try and tell you how to crack the activation but google is your friend here.

Ha.. sorry about the crack question.. anger will fuel left field questions...

Unfortunately, it is an OEM disc/install. And when I got the computer 2 months ago, I did have to activate it.. Ill have to see what the specifics are on this with Google...

---

### Post by m.musashi on 2007-04-23
> **GSF1200S said:**
> Ha.. sorry about the crack question.. anger will fuel left field questions...

Unfortunately, it is an OEM disc/install. And when I got the computer 2 months ago, I did have to activate it.. Ill have to see what the specifics are on this with Google...

No worries. I totally understand. I'd like to answer but I'm trying to be a good member of the community. :)

Given the OEM version I think your options are limited. If it activates great. If not, I doubt MS will be very accommodating.

Another option, with vmware you can make a recovery image (I forget their word for it). You could make the image on day 1 of the 30 days and then just revert to the image on day 29. Obviously all changes would be lost but if that fits your needs it's an option.

---

### Post by GSF1200S on 2007-04-23
> **m.musashi said:**
> No worries. I totally understand. I'd like to answer but I'm trying to be a good member of the community. :)

Given the OEM version I think your options are limited. If it activates great. If not, I doubt MS will be very accommodating.

Another option, with vmware you can make a recovery image (I forget their word for it). You could make the image on day 1 of the 30 days and then just revert to the image on day 29. Obviously all changes would be lost but if that fits your needs it's an option.

Not a bad idea at all.. I use virtualbox which takes "snapshots." I made a snapshot, booted windows and changed a bunch of stuff, then discarded changes and resumed from the snapshot. When I did, all the stuff I changed was back. It doesnt take ANY time to resort to the saved snapshot.. that will work nicely! 

Its definitely going to suck when I start having alot of applications to install. I guess I could revert back on the snapshot and install everything I need installed right away, then create another snapshot. Good idea?

Well, at least ive gotten somewhere!

---

### Post by GSF1200S on 2007-04-23
One other thing and this should be wrapped up nicely.

Does windows ever "phone in" to microsoft at a random basis to validate itself? If so, then I would still have to be worried about my partition install of windows requiring reactivation all the time because of the virtual machine "phoning in."

It sucks that this stuff has got to be so complicated.. Its my copy of windows, and its running on the same computer! I dont want to break any laws in the process (my crack comment was angered and unwarranted)...

---

### Post by jpatton on 2007-04-23
Yes it phone's home during an update process, it will verify that it is still windows genuine.

---

### Post by lakersforce on 2007-04-23
> **GSF1200S said:**
> So, I cant have 2 copies in the same machine.. that sucks and its BS. God forbid I even mention this, but can I crack the virtual install? I mean dang.. its my copy of windows. 

Let me get this straight as well.. If I were to call them and tell them I had to reinstall windows on the same machine with different hardware, then all would be good until one of them popped up with a message that my windows isnt genuine?

There is a copy of XP out there refered to as "Student Edition" or "Study Edition" or something simillar. It does not require activation and WGA runs without notifying Microsoft. Its a genuine copy where Microsoft removed the activation requirements. Of course they did not mean for it to circulate the internet, but fortunately for us it has.

---

### Post by GSF1200S on 2007-04-23
> **jpatton said:**
> Yes it phone's home during an update process, it will verify that it is still windows genuine.

What if I never do updates and I have automatic updates turned off? I dont care how up to date the virtual is... its gotta get signal through Linux anyways.. I can always setup Snort and ClamAV to "sniff" my connection if necessary...

---

### Post by jpatton on 2007-04-23
If updates are off...to the best of my knowledge, updates are THE only connection back to MS.

---

