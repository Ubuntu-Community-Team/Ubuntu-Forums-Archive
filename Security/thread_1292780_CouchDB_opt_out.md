---
title: "CouchDB opt out"
date: 2009-10-16
forum: Security
---

### Post by reed026 on 2009-10-16
When 9.10 is released and includes CouchDB will there be a way to opt out of using it for storing email address information? 

Other than just apt-get remove, of course. This kind of addition and SELinux kind of bother me, it's like the NSA key in the WinOS systems.

---

### Post by doas777 on 2009-10-16
please explain. 

"what you talkin' 'bout Willis?"

---

### Post by reed026 on 2009-10-16
> **doas777 said:**
> please explain. 

"what you talkin' 'bout Willis?"

Which part? 

Here's info on couchdb/ evolution sync with Ubuntu One
[http://lwn.net/Articles/356911/](http://lwn.net/Articles/356911/)

SELinux - it's already in the kernel, wrote by NSA and provided as open source. 
[http://en.wikipedia.org/wiki/Security-Enhanced_Linux](http://en.wikipedia.org/wiki/Security-Enhanced_Linux)
[http://www.nsa.gov/research/selinux/](http://www.nsa.gov/research/selinux/)

NSA Key in Windows OS
[http://en.wikipedia.org/wiki/NSAKEY](http://en.wikipedia.org/wiki/NSAKEY)
[http://www.linuxtoday.com/news_story.php3?ltsn=1999-09-06-022-06-PS](http://www.linuxtoday.com/news_story.php3?ltsn=1999-09-06-022-06-PS)

---

### Post by doas777 on 2009-10-16
well, I've been aware of the supposed NSA key since it hit all those years ago, but you have to remember the very limited set of circumstances under which it could be used to comprise your cryptography, and the lack of any kind of authoritative answer as to what/why that key was there anyway (the only link to the NSA found was that the key's debug symbol started with NSA) kinda makes me a bit meh on the topic. 

selinux has been around for years and is well reviewed. in fact it has been an option in ubuntu for many versions. 

do you feel better about novells apparmor? that is the flavor that ubuntu has choosen to use since gutsy or hardy (I forget which). 

as for ubu1, I just plan to not use it. no appeal for me. will likely uninstall it as you suggest or leave it unconfigured.

---

### Post by Chayak on 2009-10-17
I don't see how you can even think SELinux is some kind of mystical NSA backdoor.  The code has been reviewed by experts and it only does what it says it does.  That and if it's a 'secret' backdoor why release the code so every other intelligence agency in the world can review and find it for their own use?  That's not exactly a smart practice.  That same agency has contributed quite a bit of code to the Linux kernel FYI not just SELinux, so now by your logic the entire kernel is suspect.  If you want to work in absolutes then switch to [Integrity PC]("http://www.ghs.com/products/rtos/integritypc.html"), it's the only OS approved to run both Classified and Unclassified data on the same system.  Though it's not cheap at all.

---

### Post by reed026 on 2009-10-20
> **Chayak said:**
> I don't see how you can even think SELinux is some kind of mystical NSA backdoor.  The code has been reviewed by experts and it only does what it says it does.  That and if it's a 'secret' backdoor why release the code so every other intelligence agency in the world can review and find it for their own use?  That's not exactly a smart practice.  That same agency has contributed quite a bit of code to the Linux kernel FYI not just SELinux, so now by your logic the entire kernel is suspect.  If you want to work in absolutes then switch to [Integrity PC]("http://www.ghs.com/products/rtos/integritypc.html"), it's the only OS approved to run both Classified and Unclassified data on the same system.  Though it's not cheap at all.

Never said it was a backdoor, but any connection of this to the US government does make me suspect of it. Wouldn't you? 

Maybe not if the blankets are still pulled over your eyes.

---

### Post by cariboo on 2009-10-20
If you don't use Ubuntu One and Evolution, you don't need couchDB.

---

### Post by reed026 on 2009-10-21
> **cariboo907 said:**
> If you don't use Ubuntu One and Evolution, you don't need couchDB.

Yes, I figured this out shortly after I had originally posted it. Thing is though, cloud computing isn't as safe and secure as everyone thinks it is. 

[http://www.washingtonpost.com/wp-dyn/content/article/2009/10/12/AR2009101203012_pf.html](http://www.washingtonpost.com/wp-dyn/content/article/2009/10/12/AR2009101203012_pf.html)

[http://www.reuters.com/article/technologyNews/idUSTRE59E40T20091015](http://www.reuters.com/article/technologyNews/idUSTRE59E40T20091015)

---

### Post by cariboo on 2009-10-21
Have a look [here]("https://wiki.ubuntu.com/UbuntuOne/Security"), to see what Canonical is doing for security.

---

### Post by reed026 on 2009-10-22
> **cariboo907 said:**
> Have a look [here]("https://wiki.ubuntu.com/UbuntuOne/Security"), to see what Canonical is doing for security.

To be honest with you, I do not use Ubuntu One so I don't need their security. I was only pointing out the facts to people that read this thread.

What you see and believe can go bad, very bad in cloud computing. 

It's much better to get ahold of an old box and throw FreeNAS on it if you need some storage. 

But it's this and the IBM deal that has me shifting away from Ubuntu honestly. Ubuntu seemed like a good OS until it started offering intrusion type software or brainstorming ideas. 

Maybe I'm just a blast from the past, but I just wan an Operating System that doesn't spy on me. PERIOD.

---

### Post by cariboo on 2009-10-22
I don't use Ubuntu One either, I'd rather have all my data stored on my own network. It's not that I don't trust the "cloud". I'd just rather do it myself. :)

---

### Post by doas777 on 2009-10-22
> **cariboo907 said:**
> I don't use Ubuntu One either, I'd rather have all my data stored on my own network. It's not that I don't trust the "cloud". I'd just rather do it myself. :)

I'm the same way, save that I don't in fact trust the cloud.

---

### Post by reed026 on 2009-10-23
Well, all I can say is that I will soon be shifting away from ubuntu, I just need to backup my harddrive. Mr. Shuttleworth wanting to do business with IBM has me on the ropes on how he wants to move Ubuntu forward. Well the IBM deal and the fact that Google contributes to a lot of the bug fixes in the OS. 

You can call me a conspiracy theorist, but when they come knocking at your door asking questions, you'll realize what I have. You can never be too safe.

---

### Post by doas777 on 2009-10-23
> **reed026 said:**
> Well, all I can say is that I will soon be shifting away from ubuntu, I just need to backup my harddrive. Mr. Shuttleworth wanting to do business with IBM has me on the ropes on how he wants to move Ubuntu forward. Well the IBM deal and the fact that Google contributes to a lot of the bug fixes in the OS. 

You can call me a conspiracy theorist, but when they come knocking at your door asking questions, you'll realize what I have. You can never be too safe.


sounds like you;re shifting away from almost all open source then, since they contributed to GCC
[http://domino.watson.ibm.com/comm/pr.nsf/pages/news.gcc_release.html](http://domino.watson.ibm.com/comm/pr.nsf/pages/news.gcc_release.html)

good luck, and for the record, I don;t care what you have. from your sentence, I expect you to open the door in a trenchcoat. just not sure if you'll flash me or if you will produce a shotgun. either way, not interested.

---

### Post by Chayak on 2009-10-24
> **reed026 said:**
> Well, all I can say is that I will soon be shifting away from ubuntu, I just need to backup my harddrive. Mr. Shuttleworth wanting to do business with IBM has me on the ropes on how he wants to move Ubuntu forward. Well the IBM deal and the fact that Google contributes to a lot of the bug fixes in the OS. 

You can call me a conspiracy theorist, but when they come knocking at your door asking questions, you'll realize what I have. You can never be too safe.

You do realize that IBM, the NSA, DARPA,Naval Postgraduate Academy and a host of other organizations contribute to the core official Linux kernel. If you're getting paranoid over dealings with IBM then *any* linux distro you move to no matter how free and unaffiliated with any corporations they say they are build their distro base from the kernel.  If I wanted to subvert an operating system I'm pretty sure they have some guys with Dr. in front of their name that could contribute code that would get past review and still allow access at their desire.  Then again they could also have people that are part of the review process itself that people won't question.

The possibilities are endless if you go for that type of thing.

On the other side of the coin the hardware your computer runs on was probably made in Taiwan or China.  Think you can trust hardware from the country with the largest cyberwarfare program in the world?

---

### Post by reed026 on 2009-11-04
> **doas777 said:**
> sounds like you;re shifting away from almost all open source then, since they contributed to GCC
[http://domino.watson.ibm.com/comm/pr.nsf/pages/news.gcc_release.html](http://domino.watson.ibm.com/comm/pr.nsf/pages/news.gcc_release.html)

You've heard of the smart grid that IBM is working toward? Their so called petaflop as well? 

Do you not think this will happen again?
[http://www.ibmandtheholocaust.com/](http://www.ibmandtheholocaust.com/)

If you dare to forget history YOU are doomed to repeat it. 

> 
good luck, and for the record, I don;t care what you have. from your sentence, I expect you to open the door in a trenchcoat. just not sure if you'll flash me or if you will produce a shotgun. either way, not interested.

I am unsure of what you truly mean by this? I don't even own a trench coat. Maybe a nice sweater and a pair of slacks? :D

---

