---
title: "How to run Linux in Windows with limited access/rights"
date: 2008-10-22
forum: Resolution Centre
---

### Post by Lazy-buntu on 2008-10-22
I had a thread here: [http://ubuntuforums.org/showthread.php?t=955552](http://ubuntuforums.org/showthread.php?t=955552)

Which was closed because: "This is possible, but it sounds very much like you are trying to do something on a private network you should not be doing.

This kind of activity is not supported on these forums and I would direct you to your network administrator."

I can assure you that I am not doing anything fishy or even border line fishy. I would just like to use Linux in a University computer lab. I've got multiple hours between courses and I am looking for something to do. I have checked with the network policies, and this does not violate them:

[To respect the privacy of other users.

To respect the rights of other users.

To respect the legal protection provided by copyright and licensing of data and programs.

To respect the intended use of resources.

To respect the intended use of systems for electronic exchange, such as email.

To respect the integrity of the system or network.

To respect the financial structure of a computing or networking system.]

I'm sure that most of the community prefers Linux to Windows and I don't see how running Linux in a virtual box would be harmful. If there is a harmful use, don't mention it. I don't even want to read it.

---

### Post by KiwiNZ on 2008-10-22
I suggest that if this is OK you should consult the University IT department for assistance not here

The fact that you are asking for assistance on these forums adds weight to the belief that what you are attempting is un-authorised

---

### Post by Lazy-buntu on 2008-10-22
I have all ready emailed the IT department, and I am waiting on a reply.

But isn't that just like a person to assume the worst.

I posted on these forums because the Ubuntu community is a knowledgable, helpful, and active community...I.E. I don't have to wait for someone getting paid $7.50/hour to reply to my email and tell me they don't know wtf I'm talking about.

---

### Post by jdong on 2008-10-22
I agree with KiwiNZ here, and I'll add a bit of technical reasoning behind this:

All of the reasonable speed methods of doing what you want to do requires installing a system-level virtualization package which requires administrative access.

The alternative is a CPU simulator like QEmu in userspace, which would take like 20 minutes to boot Puppy and react to mouse clicks in 5 seconds, which I'm sure is probably not what you want :)


As a result, what you are asking to do is almost certainly going to go down the road of "how to get administrative rights when I don't have them". The alternative to this, of course, is to consult the system administrators of your network and try to work with them to make a virtualization solution available for you to use as a limited user (i.e. have them deploy a copy of VMWare or similar software on the system).

---

### Post by Lazy-buntu on 2008-10-22
These computers are pretty damn new. I don't think it would take 5 full seconds for a click. I've run linux in a virutal box at my high school, in a class nonetheless, where the teacher encouraged it. Those computers are probably closer to a decade older than these computers (they were running Windows 2000), and it didn't take 5 seconds to respond to a click when running XP in the virtual box! So I don't see how Puppy Linux, which is light and snappy on a 15 year old computer would have a 5 second lag on a damn near new computer.

I don't want administrative rights, and I fail to see how running a virtual box of puppy linux off a USB flash drive would allow you to access anything on the host box aside from hardware (i.e. cd/dvd drive).

---

### Post by KiwiNZ on 2008-10-22
You have asked the IT department, wait for their response

This is not the place for this .

---

### Post by Lazy-buntu on 2008-10-22
What do you mean this isn't the place to talk about it?

Absolute beginner talk: "The perfect starting place to find out more about computers, Linux and Ubuntu."

---

### Post by KiwiNZ on 2008-10-22
I mean Ubuntu Forums

---

### Post by Lazy-buntu on 2008-10-22
Like a quoted before "Absolute Beginner Talk: The perfect starting place to find out more about computers, Linux, and Ubuntu."

My question is about running Linux on a computer as opposed to Windows. It doesn't violate anything from [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy) and I don't see why you won't allow the community to reply to my thread.

---

### Post by Lazy-buntu on 2008-10-22
Like a quoted before "Absolute Beginner Talk: The perfect starting place to find out more about computers, Linux, and Ubuntu."

My question is about running Linux on a computer as opposed to Windows. It doesn't violate anything from [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy) and I don't see why you won't allow the community to reply to my thread.

---

### Post by jdong on 2008-10-22
> **Lazy-buntu said:**
> These computers are pretty damn new. I don't think it would take 5 full seconds for a click. I've run linux in a virutal box at my high school, in a class nonetheless, where the teacher encouraged it.



You didn't listen -- VirtualBox is virtualization software that requires direct access to priviledged CPU calls. You must install it as an administrator, and the virtualization engine installs drivers that run as the administrator on behalf of a limited user. You do not have such access so you cannot install software such as VirtualBox, Virtual PC, or VMWare that perform fast virtualization.

You are stuck using QEmu which fully emulates a computer as a software application.  And that is slower often by a factor of 100x, which is far more than what "15 years" of computing has been able to advance processing power.

---

### Post by Lazy-buntu on 2008-10-22
Sorry double post, you cant delete the one before it.

---

### Post by jdong on 2008-10-22
The answer to your question is you cannot virtualize Linux within Windows without administrator rights (i.e. privileged access to the CPU). There is no further answer than this.

---

### Post by Lazy-buntu on 2008-10-22
Why couldn't you let the community answer that for me then, instead of accusing me of doing something I shouldn't be, then telling me that a thread concerning Linux doesn't belong in a forum for Linux.

---

### Post by KiwiNZ on 2008-10-22
From the Code of conduct 

unauthorisded access to systems is contrary to law in most countries that is why we do not allow it

This is not a crack site , its a professional IT Support site

"You agree not to post any abusive, obscene, vulgar, slanderous, hateful, threatening, sexually-orientated material or any other material that may violate any applicable laws. Doing any of these may lead to you being temporarily or permanently banned from these forums (and your service provider may also be informed). 


if a post or thread contains spam (unsolicited advertising) it will be moved to the forum jail and the poster may be banned. Active users in good standing are allowed to have links to personal sites in their signatures, in their profile, and may post them in threads on occasion (just not often, please) as long as the content of those links does not include abusive, obscene, vulgar, slanderous, hateful, threatening, sexually-orientated material or any other material that may violate any applicable laws."

---

### Post by Lazy-buntu on 2008-10-22
I didn't ask for, nor do I want a crack.

I asked for a method of running a Linux distribution from within Windows.

Maybe your mind goes directly to 1337 h4xx0rs and all of that, but I'm pretty sure running Linux from a USB stick within Windows isn't illegal. It's probably possible for someone to get into a sticky situation that way, but there's plenty of bad things you can do from within Windows too. I'm not intending to do either.

My original post: "How to run Linux in Windows with limited access/rights

How could you run Linux (like Puppy Linux) on a computer running Windows, but here's the thing:

1. Live Media is a no go (network boot)
2. You cannot install VMware or any other .exe (but portable apps--.paf.exe--from portableapps.com work for some reason)


I was wondering if this was even possible. Maybe run virtual box/VMware off a USB stick if that's possible.

Any ideas?"

---

### Post by Lazy-buntu on 2008-10-22
Might I add explicity: 

How to run Linux in Windows with limited access/rights **(without doing anything illegal, gaining additional system rights, or anything else that falls in the shady area).**

How could you run Linux (like Puppy Linux) on a computer running Windows, but here's the thing:

1. Live Media is a no go (network boot)
2. You cannot install VMware or any other .exe (but portable apps--.paf.exe--from portableapps.com work for some reason)


I was wondering if this was even possible. Maybe run virtual box/VMware off a USB stick if that's possible.

Any ideas?

---

### Post by jdong on 2008-10-22
Again, both KiwiNZ and I have gave you a thorough explanation why the thread will remain closed. As far as I am concerned this manner is over and done with. This is not a Linux question as much as it is a Windows question at this point for you to address with your network administrators.

---

### Post by Lazy-buntu on 2008-10-22
Then move it to the Windows section.

---

### Post by jdong on 2008-10-22
Ok *fine*, I am tired of arguing this. I have moved and re-opened the thread to the Windows discussion but will continue to monitor it. At any signs of illegal activity the thread will be taken offline and involved parties will be issued the appropriate infractions.

---

### Post by Lazy-buntu on 2008-10-22
Thank you could you link its new location please.

---

### Post by Lazy-buntu on 2008-10-22
Never mind. It's the same link as the original. Thanks again.

---

