---
title: "Doing Study: Need PROOF Need Links RE: Virus, Spyware, Firewall &amp; Defragging..."
date: 2005-10-11
forum: The Cafe
---

### Post by vbgunz on 2005-10-11
Hello Everyone,

To most, the major points of the Ubuntu OS is no viruses, no spyware, no firewall and no defragging... No one needs anyone to post a reply confirming this all to be true. Proof is needed, and in fact required for this to be true so please provide links to *why* it is true. Why is the Linux OS immune to these threats? Why is Windows a breeding ground to these threats?

Links to EITHER/OR would be great!

Please understand, anyone can say anything. No one is asking for a monster reply thread of peoples opinions. Everyone's opinion is valued *but* right now an opinion is as good as an anal probe on the elbow. This thread needs links to show and *prove* Linux to be one of the finest OS choices to date as of October 11th, 2005 in regards to viruses, spyware, firewalls and defragmentation.

Please also post reasons missed. It has to be a strong reason accompanied by *PROOF* and not just your opinion. Is Linux better by design and function on more fronts than the ones mentioned? Please advise *but* please provide links of proof. Thank you!

---

### Post by nocturn on 2005-10-11
Boy, you're in for a challenge...

[QUOTE=vbgunz]
To most, the major points of the Ubuntu OS is no viruses, no spyware, no firewall and no defragging... No one needs anyone to post a reply confirming this all to be true. Proof is needed, and in fact required for this to be true so please provide links to *why* it is true. Why is the Linux OS immune to these threats? Why is Windows a breeding ground to these threats?
[/quote]

On the subject of fragmentation, you should refer to the documenation of the biggest Linux filesystems, being ext3 and Reiser.  
They do fragment, mind you, but fragmentation is extremly low.  This is caused in part by the kernel allocating slack space for files.  
Note: These documents can be very technical.

On Firewalls.  Do an nmap scan against a WinXP machine and count the open ports.  Now do the same against Ubuntu.  Ubuntu has no open ports on a default install, hence there is nothing to protect by the firewall.

On Virusses
For malware to be a virus, it must have automated replication.  In windows this is typically achieved by exploiting either one of the open ports above (fully automated) or by using some scripting host (visual basic for applications) to deliver a payload via E-mail or a webpage.
Ubuntu simply does not have that kind of services running and most apps like Mailclients do not support scripts.

Virusses and Spyware
Ubuntu encourages users to use regular accounts to work in and requires special privileges for system access.  Windows install defaults to users being local admin, this greatly increases the impact of malware because it has full system access. (check with google for installation defaults)

---

### Post by nocturn on 2005-10-11
One additional thing you could look up.

Windows was originally designed to be a single-user system (a grahpical shell on MS-DOS to be precise).   There were no permissions or things like memory seperation built in because everything locally was trusted (run by the one user)

Linux/Unix was designed from the ground up as a multi-user system.  It had the reality of different users running stuff on the machine with different levels of access.  

With WinNT, this requirement changed. But to date, Windows still behaves a lot like a single-user open system with the multi-user layer retrofitted on top of it.  

There are many articles on this if you google for them.

---

### Post by GeneralZod on 2005-10-11
I tackled a few of these issues in my (as yet unfinished!) opus :)

[http://ubuntuforums.org/showthread.php?p=395155#post395155](http://ubuntuforums.org/showthread.php?p=395155#post395155)

Bear in mind that I have no training in security or somesuch; these are the words of a layman.

Hope this helps,
Simon

Edit:

Also, I don't offer up any links in my posts, so maybe you should skip it :)

---

### Post by vbgunz on 2005-10-13
> On Firewalls. Do an nmap scan against a WinXP machine and count the open ports. Now do the same against Ubuntu. Ubuntu has no open ports on a default install, hence there is nothing to protect by the firewall.I went to a friends house and he had XP and the latest in updates running. I had him disconnect his cable modem from the router and had him plug directly to the net. I then went to the following site and scanned all ports [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2). All ports came back "closed", not open. The results were pretty much what I had expected. I popped in the Ubuntu live CD and booted up. I went to the same site and scanned all ports. The results looked exactly equivalent to XP just a minute ago. I heard Linux in general was a firewall and didn't exactly require one. If so, I expected the results to return stealth *but* this was not the case. How exactly does Ubuntu differ from Windows on this issue?> On the subject of fragmentation, you should refer to the documenation of the biggest Linux filesystems, being ext3 and Reiser.
They do fragment, mind you, but fragmentation is extremly low. This is caused in part by the kernel allocating slack space for files.I was actually curious about this issue as I did not find (after exhaustive searching in Ubuntu) a defragment utility. So I googled for one or the issue of *why* Ubuntu and Linux in general did not have one or need one. I did find information stating that Linux did fragment but so little that it was almost completely unnecessary to even bother thinking about it. I found this to be efficient in my search for reasons to try a Linux distro and it added just another tool to the arsenal. Outside of opinion if possible, is fragmentation such an issue that requires almost no worry? After constant use of Ubuntu, is it really *unnecessary* to think about it *because* a user would see almost no improvement *if* they did somehow defragment the system?

I can see how viruses/spyware/malfunctional & malicious software will have virtually no chance of thriving in a Linux environment. I believe I saw this just just after working with Ubuntu for a day. It pretty much seemed common sense to be honest. I was asked for a password so much that I actually considered by any means necessary to somehow log in as an admin and just &%$^ it all up... I then googled as to why Ubuntu kept asking for a password and how although it might have seemed a pain at first, how it helped to protect the user from themeselves... I now honestly embrace the idea and am so happy *because* being an admin just requires just so much responsibility...

In the end, the deal with my search for *links* to this information is a personal one. Everyone and anyone can tell you something positive *but* I just need proof outside of some simple feedback. I in no way question anyones knowledge but *proof* would be links to hugely publicized articles in which would not  exist if they we're wrong. For example, it would be hard to not believe some truth from a magazine which had a professional staff and a huge user base. Most of these sites have comments and feedback displayed below the article and I am certain if an article was just hot air, someone would point it out...

So, if no one has any links can someone please point out some hugely popular Linux sites that *might* touch on these points? All the thanks in the world for your help!

PS. Nocturn, thank you for pointing out that multiuser issue. Believe it or not I found an article last Tuesday morning and it touched very much on this point and at lunch with my wife that day I told her, "The more I learn about Linux, the more I get scared of Windows...".

PSS. GeneralZod, thank you for that link. I read the article and it is indeed interesting and touches on the firewall issue. Thank you!

---

### Post by tageiru on 2005-10-13
[QUOTE=vbgunz]I went to a friends house and he had XP and the latest in updates running. I had him disconnect his cable modem from the router and had him plug directly to the net. I then went to the following site and scanned all ports [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2). All ports came back "closed", not open. The results were pretty much what I had expected. I popped in the Ubuntu live CD and booted up. I went to the same site and scanned all ports. The results looked exactly equivalent to XP just a minute ago. I heard Linux in general was a firewall and didn't exactly require one. If so, I expected the results to return stealth *but* this was not the case. How exactly does Ubuntu differ from Windows on this issue?[/QUOTE]
There is no formal requirement that a firewall must stealth ports.

Anyways, the difference between Ubuntu and Windows is that Ubuntu does not have any listening ports (well, locally but not globally), therefor there is nothing to connect to -> no firewall needed. This is of course invalidated if you install daemons that listens to some port.

If you are interested in firewalling you should look into iptables.

---

### Post by hashimoto on 2005-10-13
Curiosity killed the cat. I went to Symantec pages and did a search. This is what came up regarding viruses & vulnerabilities in linux. Much of this is history, I guess.

[http://securityresponse.symantec.com/avcenter/venc/data/linux.simile.html](http://securityresponse.symantec.com/avcenter/venc/data/linux.simile.html)
[http://securityresponse.symantec.com/avcenter/venc/data/linux.rst.b.html](http://securityresponse.symantec.com/avcenter/venc/data/linux.rst.b.html)
[http://securityresponse.symantec.com/avcenter/venc/data/linux.jac.8759.html](http://securityresponse.symantec.com/avcenter/venc/data/linux.jac.8759.html)
[http://securityresponse.symantec.com/avcenter/venc/data/linux.svat.html](http://securityresponse.symantec.com/avcenter/venc/data/linux.svat.html)
[http://securityresponse.symantec.com/avcenter/venc/data/linux.hyp.6168.html](http://securityresponse.symantec.com/avcenter/venc/data/linux.hyp.6168.html)
[http://securityresponse.symantec.com/avcenter/venc/data/linux.slapper.worm.html](http://securityresponse.symantec.com/avcenter/venc/data/linux.slapper.worm.html)
[http://securityresponse.symantec.com/avcenter/venc/data/linux.lion.worm.html](http://securityresponse.symantec.com/avcenter/venc/data/linux.lion.worm.html)
[http://securityresponse.symantec.com/avcenter/venc/data/linux.hijacker.worm.html](http://securityresponse.symantec.com/avcenter/venc/data/linux.hijacker.worm.html)
[http://securityresponse.symantec.com/avcenter/venc/data/linux.millen.worm.html](http://securityresponse.symantec.com/avcenter/venc/data/linux.millen.worm.html)
[http://securityresponse.symantec.com/avcenter/venc/data/trojan.linux.jbellz.html](http://securityresponse.symantec.com/avcenter/venc/data/trojan.linux.jbellz.html)

Other possily interesting stuff:
[http://linux.slashdot.org/article.pl?sid=05/09/21/1252213&tid=154&tid=172&tid=106](http://linux.slashdot.org/article.pl?sid=05/09/21/1252213&tid=154&tid=172&tid=106)

[http://linux.slashdot.org/article.pl?sid=05/01/26/219201&tid=133&tid=172&tid=220&tid=201&tid=106](http://linux.slashdot.org/article.pl?sid=05/01/26/219201&tid=133&tid=172&tid=220&tid=201&tid=106)

---

### Post by GeneralZod on 2005-10-13
Just stumbled upon this link from linux.org:

[http://www.vnunet.com/vnunet/news/2143697/grisoft-warns-linux-virus](http://www.vnunet.com/vnunet/news/2143697/grisoft-warns-linux-virus)

Edit:

Actually, scratch that - it is devoid of content ("Linux will get viruses because...because...well, it's just a matter of time, isn't it?!") and comes from a source that would benefit from some fear-mongering :)

---

### Post by bjweeks on 2005-10-13
I just scanned my windows box with nmap it found

135/tcp open msrpc
139/tcp open netbios-ssn
445/tcp open microsoft-ds
9/udp    open|filtered discard
123/udp  open|filtered ntp
137/udp  open|filtered netbios-ns
138/udp  open|filtered netbios-dgm
445/udp  open|filtered microsoft-ds
500/udp  open|filtered isakmp
1025/udp open|filtered blackjack
1900/udp open|filtered UPnP
4500/udp open|filtered sae-urn

oops my bad that was just the tcp ports lol

---

### Post by ygarl on 2005-10-13
Interesting that every single one of the viruses on this list would only work when run as ROOT, on distros over 3 years old, and the very last one on Symantec's site (which also is very old, and would not affect any up-to-date system) can ONLY affect a single users /home directory.

None of the others would affect a modern, decently updated system...

Guess that says it all really. The newest one is from 2002. Symantec gets dozens of new ones *every day*

How's that for proof?

Ah, also the Slashdot reference referring to running WINE virii - I don't think a virus which only affects your Windows emulated drive which does not affect the rest of the Linux system really could be described as 'affecting Linux' - do you? I call that good emulation myself. Especially as it is limited to the WINE directory...

---

### Post by az on 2005-10-13
[QUOTE=vbgunz]Hello Everyone,

To most, the major points of the Ubuntu OS is no viruses, no spyware, no firewall and no defragging... [/QUOTE]

Well, there is also the point that  it is free.  And not only in cost, but in freedom (Free Libre Open Source)

The fact that there are many more eyeballs looking at the code tends for security problems to be uncovered and reported readily.  It also promotes the improvement of the code by those who use itm, which is why it is a powerful development model.

The fact that the software is not property also attracts users to it, but that is not your question.

---

