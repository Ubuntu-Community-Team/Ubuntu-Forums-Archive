---
title: "New to Ubuntu ISO guidance for creating a &quot;basic&quot; IDS."
date: 2011-07-20
forum: Security
---

### Post by stevennlv on 2011-07-20
&#65279;Hi everyone,

I'm new to *nix. I've been here for less than a week now.

I've been tinkering with computers as a hobby for about 30 years. (I remember trash 80's.) But I am most definitely an end user. I couldn't code my way out of a wet paper bag. I've been on windows since '94, so not quite 20 years now.

I just got a shiny new box two months ago from dell with lots of bells and whistles.

And I've spent the last two months pulling my hair out. I have been infected / re-infected with RATs, MRWs, key loggers, rootkits, adware, spyware and on and on ~ every two weeks like clockwork. I've zeroed the partition and flushed RAM at least 6 times in the last two moths.

And yes, I know how to "harden" a windows system. What a joke! And I practice safe computing. My old XP system, which gave up the ghost when the power supply failed, was nearly bullet proof for five years before I started having any real problems with it. (And then I had a backed up clean “base state” on disk to fall back on.) I skipped Vista. The new box has 7.

After two months of pulling my hair out I have to come to the conclusion that the arms race has been lost on the windows side of the game. I believe that the bad guys have advanced far enough that there is now no way possible for an end user to adequately protect a windows box that connects directly to the net.

So I gave up. Time to change the game plan. I am in the process of building an Ubuntu VM to act as my default web surfer.
And I'm almost done.

I think I've come quite a ways in less than a week. But, the last step is going to be the big one. And I'm going to need some help.

So far I've got a fairly default install of 10.04LTS. The only non-security related stuff I've installed is Google Earth and some streaming video plug ins. I have True Crypt so that when I'm finished I can store an encrypted copy of my resume on the VM for job hunting. 

I did not enable Unity or file / folder sharing in the VM; nor did I bridge the network connections. When I have to move files between the two machines I mail them to myself at yahoo. First I scan them in the VM with clam. Then yahoo will scan with NAV, then I'll scan with my win AV before opening. If that misses a payload I don't know what else to do?

On the Unbuntu system security side I've added firestarter and used it to configure my firewall to block all inbound connections. I have clamav installed with a gui frontend. I am running in the default install user mode. I have a strong password. I have turned off IPV6 and made sure that remote desktop connection is off as well. I have a lot of security and privacy scripts in FF; like NoScripts and Adblock. I have configured FF for granular cookie control.  I've implemented some of the security tweaks in the Stricter Defaults documentation. 

On the windows side my only connection is wireless. I've setup my router to not broadcast it's SSID and to only accept connections from my MAC address. I have also blocked all of the remote network administration protocols that the drop down lists in the routers GUI would let me block. And I have set both my router and my virtual network cards to use a remote secure DNS server for DNS resolution.  

I also have the win machine AV and firewall monitoring (at least some what) all of the traffic on the virtual network card.  The AV has a root certificate which allows it to scan encrypted traffic. And there is at least some pass-through at this level between the two machines. I had to install the certificate in to the VM version of FF to be able to establish secure connections.  I also have the win FW set to block all inbound connections from the VM.

The win machine almost never connects to the net. When it does it's only when absolutely necessary and only to the certain secure sites. And then only with FF set up the same way listed above. Except on the win machine FF is also in a software sandbox that automatically flushes itself on close.

Also I will be building an XP VM for streaming video. I refuse to do without netflix.

I think I've got every thing covered except for two things: I'm going to setup up some kind of VPN on the win machine side. Not sure what yet. I'll have to learn more about it.

Last but not least, and what I need you guys help with: Setting up some kind of basic IDS on my VM. I've read through the stickies at the top. To be honest a lot of it is over my head. I'm willing to read and learn. But, I'm not really sure if all of that really applies to me?

I'm looking for one simple thing: I want to be alerted when someone is knocking on my back door so I can close the VM. Firestarter will do that. But, I've read that I should not be running it all the time because it runs in root and opens up holes in the process.

Ideally I'd like a nice big pop up, a right in my face kind of thing that says basically: High, someone is trying to get in through the back door!!!!!! I mean IP addresses and all that stuff are nice and I would love to have it. But, at this point even something as simple as my machine flashing a generic text alert message would be fine.  But I have no idea how to implement something like that. I'll keep reading, but any advice would be greatly appreciated.

And last, but not least, assuming I get all of the above worked out; can you think of any thing I missed for setting up a home machine that has a reasonable chance of letting me pay bills, look at the news, watch movies, shop on line, look up recipes, get directions and phone numbers  and do all the everyday general use stuff without some 12 year old in Yugoslavia ruining my life?

I greatly appreciate any and all help.

Thanks.

---

### Post by bodhi.zazen on 2011-07-20
Welcome to Ubuntu, it takes a few months to transition to a new OS, including your understanding of security.

Keep reading the stickies and asking questions about things you do not understand.

While it is a good start, your Windows security knowledge does little or nothing to increase your Ubuntu security.

1. Firestarter is depreciated.

2. Use ufw or gufw.

3. You are better off reading about iptables so you understand you are blocking incoming new connections, and not all incoming established or related connections, or udp traffic on port 53

4. But since there are not open ports by default, and I assume you are using a router, adding a firewall without understanding how the firewall works did very little.

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

5. No known active viruses on linux, so feel free to scan all day long. All you will find is false positives or infected files on your windows partitions. Since viruses are not a significant threat, running antivirus does little, if anything, to increase your security.

If you want to increase security,

1. Read the security stickies.
2. Learn to use apparmor. Confine all network aware applications (firefox) with an apparmor profile.
3. Use NoScript.

Once you feel more comfortable, read up on tcpdump and snort.

[http://danielmiessler.com/study/tcpdump/](http://danielmiessler.com/study/tcpdump/)

Then, just for fun, review this:

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

Aye, that is a ton to digest, welcome to a new OS.

The good news , you can relax and take all the time you need to learn as a default installation of Ubuntu is hardened enough out of the box you probably do not need to do much beyond installing and enabling the apparmor-profiles and using NoScript.

---

### Post by stevennlv on 2011-07-21
> **bodhi.zazen said:**
> Welcome to Ubuntu, it takes a few months to transition to a new OS, including your understanding of security.

Keep reading the stickies and asking questions about things you do not understand.

While it is a good start, your Windows security knowledge does little or nothing to increase your Ubuntu security.

1. Firestarter is depreciated.

2. Use ufw or gufw.

3. You are better off reading about iptables so you understand you are blocking incoming new connections, and not all incoming established or related connections, or udp traffic on port 53

4. But since there are not open ports by default, and I assume you are using a router, adding a firewall without understanding how the firewall works did very little.

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

5. No known active viruses on linux, so feel free to scan all day long. All you will find is false positives or infected files on your windows partitions. Since viruses are not a significant threat, running antivirus does little, if anything, to increase your security.

If you want to increase security,

1. Read the security stickies.
2. Learn to use apparmor. Confine all network aware applications (firefox) with an apparmor profile.
3. Use NoScript.

Once you feel more comfortable, read up on tcpdump and snort.

[http://danielmiessler.com/study/tcpdump/](http://danielmiessler.com/study/tcpdump/)

Then, just for fun, review this:

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

Aye, that is a ton to digest, welcome to a new OS.

The good news , you can relax and take all the time you need to learn as a default installation of Ubuntu is hardened enough out of the box you probably do not need to do much beyond installing and enabling the apparmor-profiles and using NoScript.

I truly appreciate all the info.

Tonights 7 hours crash course marathon session will be devoted to GuFw and AppArmor. And your reply has been booked marked.

But, I'm not sure that you understand what I'm trying to achieve. This is still primarily a win7 box by design. But, I've come to the conclusion that as an end user I no longer have the skill level to adequately secure any windows install that connects directly to the internet. Personally I think the bad guys have won and that no windows end user can feel truly secure on a strictly win box any more. At least not if they have even the most basic understanding of computers.

And I do have a good set of basic computer skills. I'm one of those folks that believes you shouldn't own a car if you can't change the oil, do a tune up, and change a tire. I can't rebuild an engine or a tranny. But I won't get stuck on the side of the road waiting for AAA either.  I feel the same way about computers. 

I understand that *nix is by nature more secure than windows. I also understand that lot's of people smarter than I have worked hard to make the Ubuntu distro even more secure and usable for folks like myself. And I appreciate it very much.

However, IMHO Ubuntu is still not up to a level of ease of use that would make me comfortable using it as my primary OS or even dual booting. A perfect example is clamav. On the windows side of the box it took me 10 minutes to install and configure my AV. It took me a seven hour marathon session of reading, tinkering, testing, trying and retrying and asking for help to get clam AV installed to Ubuntu.

But, I do feel that at this point in its development / cross referenced with my skill level that an Ubuntu VM will make an excellent security tool for my win7 install. That is why I chose Ubuntu to protect my win install from the net.  

So, what I am attempting to do is create a hybrid system with what I feel to be the best of both worlds. I am building an Ubuntu virtual machine to act as my "agent" so to say on the internet. Basically the whole purpose of my UVM is act as a "super-duper" sandbox for my net connection. I actually don't plan on getting real deep in to Ubuntu. No farther than I have to achieve to my desired result. The windows side of the box will still be getting plenty of use for other things and be my primary concern.

And to be honest I'm really not all that worried about the UVM per se becoming corrupted. Once I feel it's done I'll just back all the files up to DVD on the win side of the machine. And be done with it other than keeping it up to date. If it takes a poop I'll just drag and drop the back up in to the appropriate folder and re-run the updates. Viola! 

However, I am concerned about such things as DLing an e book in a malformed .pdf carrying a windows executable payload on the UVM (where I know it will have no effect). Then emailing it to my win machine side of the box so that I can drop it on my e-reader. That could cause lots of problems. Hence I will use clam to scan it in the UVM, then yahoo will scan it with NAV, then on the win side I'll scan it again. If a payload gets through all that then I don't know what else to do. And I know that's a lot of work. But, I feel it's worth it.

And please don't say just take the plunge and switch over. I'm not ready to go there and may never be.  

I didn't know about AppArmor. But I learn quick. Sounds a lot like a sandbox. I didn't even think to look for one. Thanks for the tip.

The only thing I feel that I'm missing on the UVM now is some sort of basic alarm system. 

Remember the whole purpose of the UVM is to protect the win7 install. I don't want someone who knows 10k times more than I do walking through the back door of my UVM and right in to the heart of my "real" machine.

Even if you think such a thing is not necessary I'd like it for peace of mind, if nothing else. I know you said not all inbound connections are bad. I disagree. If for no other reason than the way I have this thing set up right now there is absolutely no legitimate (i.e. need it for something to work) reason for an inbound connection to be seeking me out. Hence, by default, they are all bad.

And, as I've done some more reading I don't think I really need an IDS.

What I need is much simper: A graphical tool that does not run in root that will monitor my firewall and notify me of the IP of any inbound connection attempts. Then I can run a who is on the IP and decide if I want to end the UVM session to protect my win install.

I think something like that that plus AppAmor and taking out FS / adding GuFW will finish my UVM and then I can start building an XP VM to watch netflix. :)

Any suggestions on a tool that would do that job for me?

---

### Post by Chayak on 2011-07-21
You're concerned about malicious PDFs, which I can only assume are pirated ebooks, and you're trusting anti-virus?

Please allow me to explain something to you.  Anti-virus aside from a few exceptions relies on signature based detection.  That means that malware will only be detected if someone has created a signature for that specific piece of compiled code.  No signature, no detection outside of the few behavioral based systems such as Symantec's Sonar and Kasperksy.  One more thing, a malicious binary can easily be changed so the old signatures don't detect it anymore.

Now for some reality.  I'm a malware analyst so I deal with quite a bit of it daily.  The majority of samples that I get are PDF based.  I've got a rather large queue to look at and I only look at the known malicious files that get past a large gauntlet of anti-virus engines, hence my poor opinion of them.  If someone's already worked a sample I'm not going to waste time and duplicate effort.  Can you guess where we get the majority of our undetected samples from?  They get scraped off of torrents and file sharing sites.

If you've been looking at pirated ebooks with a windows computer then there is a good chance your system is already infected.  If the malware binary in it was custom compiled and obfuscated for that file then it's very likely that it may never get looked at by an analyst and no signature will get made since it will only infect a small number of machines.

There's a concept called C2 that we follow.  It's called compartmentalized computing.  The base operating system is as stripped down and bare as possible except for essential tools and never touches the internet for anything other than updates.  Everything is done in virtual machines.  I have four running at the moment, one for collecting samples, one for general use, an analysis one, and a corporate desktop.  The corp and general ones have their own NIC ports that are bridged and the other two share a port on the dirty network which is where all malware is handled and we have Netwitness units monitoring everything.

It may seem a bit extreme but I've lost count of the number of times I've had to revert to known clean snapshots.  It's not a big deal on the dirty network, it's expected.

---

### Post by stevennlv on 2011-07-21
> **Chayak said:**
> You're concerned about malicious PDFs, which I can only assume are pirated ebooks, and you're trusting anti-virus?



NO!

Just because I'm paranoid does not mean that they are not out to get me (as the saying goes) or that I'm a thief! What part of "practice safe computing" did you not compute? I've picked so much crap from so many "legitimate" places I've lost count. I was just using the malformed .pdf as an example. I picked up a trojan not long ago DLing a .pdf of sausage dish recipes from the web site of the sausage manufacturer!

I'm just trying to figure out how to keep my box clean!

Since you're some kinda guru hows about insteada shoutin fire in a crowded theater or screaming THIEF! You actually contribute something to the conversation so that a poor pathetic little moron like me can get some edumactions!

I've already figured out that I need a VM! Or did you not read the whole thread?

Once again:

Does anybody know of a graphical tool that does not run in root that will monitor my firewall and alert me to inbound connection attempts?

---

### Post by bodhi.zazen on 2011-07-21
> **Chayak said:**
> There's a concept called C2 that we follow.  It's called compartmentalized computing.  The base operating system is as stripped down and bare as possible except for essential tools and never touches the internet for anything other than updates.  Everything is done in virtual machines.  I have four running at the moment, one for collecting samples, one for general use, an analysis one, and a corporate desktop.  The corp and general ones have their own NIC ports that are bridged and the other two share a port on the dirty network which is where all malware is handled and we have Netwitness units monitoring everything.

Nice.

@ stevennlv Indeed I misunderstood you. For some reason I thought you had given up on Windows, but you are still running it as your primary OS. This despite the realization your box has been sacked. Amazing, now that is faith.

If you need windows support, please use a windows forums.

If you want a secure OS, install Ubuntu or Fedora (or most any Linux or BSD).

---

### Post by stevennlv on 2011-07-21
> **bodhi.zazen said:**
> Nice.

@ stevennlv Indeed I misunderstood you. For some reason I thought you had given up on Windows, but you are still running it as your primary OS. This despite the realization your box has been sacked. Amazing, now that is faith.

If you need windows support, please use a windows forums.

If you want a secure OS, install Ubuntu or Fedora (or most any Linux or BSD).

OK, startin to get a little mad here.

Are you guys not reading what I'm saying?

I am not looking for windows support here!

I have created a full fledge UBUNTU VIRTUAL COMPUTER INSIDE MY WINDOWS INSTALL!! IT HAS TWO OF MY EIGHT AVAILABLE CORES AND A GIG OF RAM!

I am seeking assistance with the Ubuntu virtual machine. On your advise, last night I installed the default profiles for AppArmor.

The whole point of the UVM is to protect my windows machine from the web: A super-duer sandbox if you will. IT'S MY LIFE, DON'T TELL ME HOW TO LIVE IT.

I can handle the win side of the machine with out any help at all, thank you very much.

But I would really appreciate some help w/ Ubuntu w/o everybody telling me I'm stupid, go away or calling me thief!

Jeez, I thought the whole point of Ubuntu was to empower people!

Y'all sure have a funny way of showing it!

So, one last time:

_***DOES ANYBODY KNOW OF A GRAPHICAL TOOL WHICH WILL MONITOR MY FIREWALL, DOES NOT RUN IN ROOT AND WILL ALERT ME TO INBOUND CONNECTION ATTEMPTS OR NOT?***_

---

### Post by CandidMan on 2011-07-21
Surely the Windows 7 OS has ultimately handles all of the computer's traffic. Therefore, running Ubuntu in a VM won't protect you from server vulnerabilities, only client ones. Attackers will be directed to your Windows 7 install. Personally, I'd swap the OS roles around

---

### Post by stevennlv on 2011-07-21
> **CandidMan said:**
> Surely the Windows 7 OS has ultimately handles all of the computer's traffic. Therefore, running Ubuntu in a VM won't protect you from server vulnerabilities, only client ones. Attackers will be directed to your Windows 7 install. Personally, I'd swap the OS roles around

Ah, but you see the win machine never connects to the net directly!
The UVM acts a filter of sorts. When I'm on the web all they see on the other end is *nix. Not win anything. So, the idea is bad stuff will have to get through *.nix to get to my "real" machine.

And I don't want Ubuntu as my primary OS. It's too hard to administrate the system, in my opinion.

So once again:

Can we get over how I choose to run my computer yet or not?

Does anybody know of a graphical tool which will monitor my firewall, does not run in root and will alert me to inbound trafifc?

---

### Post by bodhi.zazen on 2011-07-21
> **CandidMan said:**
> Surely the Windows 7 OS has ultimately handles all of the computer's traffic. Therefore, running Ubuntu in a VM won't protect you from server vulnerabilities, only client ones. Attackers will be directed to your Windows 7 install. Personally, I'd swap the OS roles around

I am not convinced you can protect the host OS from a virtualized guest, read Chayak's most recent post again. There is a very good reason the host OS is as minimal as possible and not Windows (or Ubuntu desktop for that matter) ;) Desktop functionality is provided entirely from the guests.

IMO each is responsible for it's own security, you need to treat each guest the same as you would a physical machine.

You can try to isolate a machine by using a firewall (this functionality is probably best offered by a "router" rather then running Ubuntu as a VM and routing your Windows traffic through it) or a proxy, such as squid, which would run antiviurs, but we have already learned earlier in this thread the limitations of this approach.

My advice still stands, if you want to run a secure os, use Linux or BSD.

> **stevennlv said:**
> Ah, but you see the win machine never connects to the net directly!
The UVM acts a filter of sorts. When I'm on the web all they see on the other end is *nix. Not win anything. So, the idea is bad stuff will have to get through *.nix to get to my "real" machine.

We see.

> And I don't want Ubuntu as my primary OS. It's too hard to administrate the system, in my opinion.

Then these are not the proper forums to be using and you should be off posting on a Windows security forums as we can not increase your windows security here.

> So once again:

Can we get over how I choose to run my computer yet or not?

Run what you want, it is your computer. But we do not support windows here, so if you choose windows, that implies seeking advice on a windows forums.

Edit: We will support the Ubuntu guest, but, the Ubuntu guest can not increase the security of the Windows host.

> Does anybody know of a graphical tool which will monitor my firewall, does not run in root and will alert me to inbound trafifc?

Now what kind of a tool do you want. Windows -> ask on a windows forms.

Ubuntu, see the stickies:

[http://ubuntuforums.org/showthread.php?t=1477696](http://ubuntuforums.org/showthread.php?t=1477696)

[http://ubuntuforums.org/showthread.php?t=1477662](http://ubuntuforums.org/showthread.php?t=1477662)

You can look at [OpenVAS](http://www.openvas.org/) , which is covered in the links above, but my guess,based on your posting style, is that it is somehow not going to interest you.

IMO your best options are: 

1.  Learn to use ubuntu in the VM and when you are ready, use it as your primary OS. Expect 3-6 months to transition, longer or shorter depending on how fast you learn. You may dual boot for a while ;)

2. Learn to secure Windows.

We can help with #1 , not with #2 .

---

### Post by Chayak on 2011-07-21
> **stevennlv said:**
> OK, startin to get a little mad here.

Are you guys not reading what I'm saying?

I am not looking for windows support here!

I have created a full fledge UBUNTU VIRTUAL COMPUTER INSIDE MY WINDOWS INSTALL!! IT HAS TWO OF MY EIGHT AVAILABLE CORES AND A GIG OF RAM!

I am seeking assistance with the Ubuntu virtual machine. On your advise, last night I installed the default profiles for AppArmor.

The whole point of the UVM is to protect my windows machine from the web: A super-duer sandbox if you will. IT'S MY LIFE, DON'T TELL ME HOW TO LIVE IT.

I can handle the win side of the machine with out any help at all, thank you very much.

But I would really appreciate some help w/ Ubuntu w/o everybody telling me I'm stupid, go away or calling me thief!

Jeez, I thought the whole point of Ubuntu was to empower people!

Y'all sure have a funny way of showing it!

So, one last time:

_***DOES ANYBODY KNOW OF A GRAPHICAL TOOL WHICH WILL MONITOR MY FIREWALL, DOES NOT RUN IN ROOT AND WILL ALERT ME TO INBOUND CONNECTION ATTEMPTS OR NOT?***_

I apologize if I was off the mark on my assumption, but when you describe frequent malware issues and are worried about pdf ebooks it's a logical assumption for me.  Then again I do deal with the dark side if the internet most of the time.

I did contribute to the thread though even if you filter everything I posted down to one thing.  Anti-virus only protects you from old malware.  The new stuff can be out there for quite a while and not get detected even in high security systems, stuxnet being the perfect example.

I gave you a real world example of a hardened setup using VMs that's been proven under fire.  You asked for secure so I gave you a secure example.

You say the windows machine never connects to the net directly and you're going through the UVM, please elaborate on your network setup.  Is your machine connected directly to the internet or do you have a router with NAT between the two?  Is the VM's network interface bridged or NAT?

I know you want a graphical alert for the firewall, and I don't know of any.  I understand that it gives a sense of security, but if you deny new inbound by default and make sure there are not exceptions.
```
sudo ufw default deny
```
The box won't reply to outside requests and at that point you can consider it as secured as practically possible to an outside probe or attack attempt.  That just leaves something you do to compromise it.

If you want to protect a windows machine from the internet then you need some kind of hardware between the two.  A firewall from a security suite is only token protection.

If you want a firewall that's worth a damn then buy a Cisco ASA, Juniper Netshield, Mikrotik Routerboard, or some other commercial grade firewall.  If you want to roll your own build yourself a Vyatta, Mikrotik x86, Astaro, Smoothwall, etc box.  Then the most important bit is to keep them updated.

What about the consumer firewalls?  They're built as cheaply as possible, and the code running them is generally quick and sloppy. If you tell them to deny all new incoming by default they'll offer some security. If it has anything touchable from the internet side (and all ISP provided routers can be, how do you think they manage them?) they'll likely be cracked by a dedicated attacker.

I'm sorry if it's not what you want to hear, but you asked for security help and from what I've read what's been given is the reality of it.

You need to make an honest risk assessment.  It seems to me your problem is just malware and not remote exploitation.  It's your actions that infect the machine so take a good look at what you're doing and stop doing it that way.

---

### Post by stlsaint on 2011-07-21
> DOES ANYBODY KNOW OF A GRAPHICAL TOOL WHICH WILL MONITOR MY FIREWALL, DOES NOT RUN IN ROOT AND WILL ALERT ME TO INBOUND CONNECTION ATTEMPTS OR NOT?


Hey i see your frustration as you were given alot of various answers but here is my two cents...

When bodhi was saying ubuntu is mostly secure out of the box, that is exactly what it is! Ubuntu comes with no open ports so with no ports you have NO incoming connections because there is nothing to connect to?! ;) 

Catch what im saying? That command above with ```
ufw deny....
``` is just really beating a dead horse for your ubuntu system! 

The default firewall for ubuntu is called iptables. Now if you are looking for a frontend to that then you might be interested in [Shorewall]("http://www.shorewall.net/"). There are others and a google search will give you more on them!

Not once did anyone call you stupid or mean to. You posted a very long post on various subjects and for us forum personnel we are used to addressing many subjects while offering our best advice for what works based off our diverse experiences!:popcorn:

---

### Post by stevennlv on 2011-07-22
OK guys, here's the deal:

I'm a security guard at one of the largest communications companies in the world. Some of our terminals only connect inside to each other. Some terminals only connect to the out side world. A few select terminals are allowed to do both. I operate one of those. Due to the nature of my job I need access to both the inside world and the outside world.

My terminal is armored with a really spiffy, really expensive program. When I click on a short cut it automagically creates a virtual linux environment that the web browser runs inside of. Then when the session is closed the virtual environment is completely destroyed. It is recreated from scratch every time we open the browser.

I don't have hundreds of thousands of dollars to licenses that program. And it's not available to the end user any way.

So after I decided that I could no longer protect my win box at home from a direct internet connection I decided to monkey see / monkey do what the IT department set up at work the best I could with free ware.

I used the free Virtual Machine Player to create a virtual computer inside my windows install. When I installed VM Player it downloaded several GB worth of tools and automagically built a computer inside my computer for me. It also allowed me to install Ubuntu from an ISO as the computer was being "built". Or I could have built a computer with no OS and gone back and installed one later.

 I still use the win install for lots of stuff (games, etc) but it almost never connects directly to the net. Meaning that I almost never open a web session inside the windows install. And when I do it is only to certain secure sites. Then the downloads are scanned before I do anything with them.

I am talking to you from inside of the Ubuntu virtual machine itself. As far as I understand it is a full fledged computer unto itself. It has its own isolated virtual processor which is hosted on two cores of my "real" chip. It has a gig of it's own RAM. It has a 20 GB (virtual) hard drive. It has it's own virtual network card which is hosted on my "real" card. And everything inside the virtual machine is run in separate memory processes which are isolated from the OS of the host machine. At least that's the way I understand the documentation from VM Player. 

There are options in the VM Player to integrate the "two" machines much more closely than I have. They are called "unity" and shared folders. Shared folders are obvious. "Unity" kind of "merges" the two machines together so that the from the desktop they appear to be seamless and you're not supposed to be able to tell where one ends and the other begins. At least that's the idea.

I do not have unity or shared folders enabled. According to VM Players documentation the only exploits that have seen are based on those two features. Supposedly, if you do not enable them then nothing is SUPPOSED to be able to cross over from the virtual machine to the host machine.

When I want to get on the net I have to boot the host, then boot the VM so I connect to the net with firefox from inside the VM.

_***All of the questions I am asking here relate to Ubuntu only!!!!!!***_

My goal is to make my virtual computer as hardened as possible to make it as hard as possible for something bad to cross over from my VM to my real machine. 

There is some deep level of interaction between the "two" machines. But, where and exactly how that takes place is beyond my skill level. All I know is a lot of folks a whole lot smarter than me wrote a free program called VM Player, which is the freeware version of their enterprise virtual machine software and they claim that as long as unity and shared folders are not enabled bad crap will not pass through that inner deep connection from the virtual machine to the host machine.

Now you guys can poo-poo on the strategy all you want. I'm just trying to imitate, as best I can, what the IT dept at one of the largest communications companies on the planet is doing.

If you think it's a crappy idea let them know. I'm sure that they could explain it better than I can.

_***In the mean time though: Does anybody know of a good graphical *!*UBUNTU*!* tool that does not run in root that will monitor my firewall for me and alert me to attempted inbound connections?***_

I know you guys say that is beating a dead horse, but it will help me sleep at night; OK?

Last, but not least I have some questions about AppArmor. But I'm almost afraid to start a new thread for it!

Edit: Oh, and in answer to questions above: No, the network connections are not bridged and my host machine has an NAT router between me and the outside world. And I have the DNS resolver turn off in windows and have both the virtual network card and the NAT router set up to use a remote / secure DNS resolver service.

---

### Post by stevennlv on 2011-07-22
> **Chayak said:**
> 
If you want to protect a windows machine from the internet then you need some kind of hardware between the two.  A firewall from a security suite is only token protection.

If you want a firewall that's worth a damn then buy a Cisco ASA, Juniper Netshield, Mikrotik Routerboard, or some other commercial grade firewall.  If you want to roll your own build yourself a Vyatta, Mikrotik x86, Astaro, Smoothwall, etc box.  Then the most important bit is to keep them updated.

I've heard of a smoothwall. But how in the world would I set a physical machine between a host an a virtual machine? Or are you talking two separate physical machines?

> What about the consumer firewalls?  They're built as cheaply as possible, and the code running them is generally quick and sloppy. If you tell them to deny all new incoming by default they'll offer some security. If it has anything touchable from the internet side (and all ISP provided routers can be, how do you think they manage them?) they'll likely be cracked by a dedicated attacker.I have both the host fire wall and the VM firewall set to deny all inbound.

> I'm sorry if it's not what you want to hear, but you asked for security help and from what I've read what's been given is the reality of it.I' d rather hear the straight truth than have it sugar coated any day brother.

> You need to make an honest risk assessment.  It seems to me your problem is just malware and not remote exploitation.  It's your actions that infect the machine so take a good look at what you're doing and stop doing it that way.Yes and no: the malware is opening up the opportunity for the remote exploitation. 

And I am changing the way I'm doing things: that' what this whole exercise is all about.

I know enough to know that "bad stuff" can be injected in to "good sites" and then install in the background through IE w/o knowledge or consent. That's why when the win side of the box does connect it is with FF in a sandbox.

I'm doing everything I can think of.

I'm just not ready to take a full plunge in to *nix.

But, so far my current scheme is working. I've been on the net for a week with no nasties getting in my system.

But, in anther week or two I'll have this thing set up just the way I want on both sides of the box.

At which point I'll back up a system ISO to DVD.

Then WHEN, not if I get borked (all this trouble is basically to slow down the borking long enough to get tweaked and backed up) then I can just return to state and run my upadates :)

But, that is a discussion for a win forum.

Here, I'm just looking for help to harden my Ubuntu VM.

---

### Post by stevennlv on 2011-07-22
@ [[COLOR=#339900]**stlsaint**[/COLOR]]("http://ubuntuforums.org/member.php?u=814785")

I think shorewall is deeper than I'm looking to get right now.

@ [[COLOR=#980101]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054")

I'd say the same thing for HIDS and Snort. 
(And BTW, I do know how to "harden" windows. But, anymore that's just the punch line to a bad joke. The bad guys have won that war. They are so far ahead of the end user now it's not even funny. Even the IT dept at work decided that they could not harden a win terminal to the outside world. That's why they just went out and spent hundreds of thousands of dollars on that spiffy program.)

  Shorewall, HIDS and Snort all look like great stuff. But are currently way over my head.

(And unless or until stuff like that is not way over my head I won't be doing a full plunge in to *nix. Windows may be crappy, but at least I understand it!)

Plus, I don't know how much computing power that would take. The way I have the VM set up now I'm probably running on the equivalent of an old P4 Prescott w/ 1 GB RAM. According to the Ubuntu system monitor I am already pushing it pretty hard just web surfing. I multi-task a lot. And I don't want to take away anymore resources from the host because after this VM is done I will be copying / isolating / encrypting it to another instance that will be used only for banking. And I'll also be building an XP VM for just netflix since moonlight won't do DRM.

If you guys say that the current Ubuntu firewall is tight enough I'll take your word for it and just keep everything up to date.

I'd just really love to have a pop up that tells me when someone is scanning me for open ports. Even if they don't exist. I'd still like to be told by my Ubuntu VM when somebody is knocking at the back door even if they can't get in.

Like I said above: It'll help me sleep better at night.

I'm just looking for something quick and simple that any noob could dl / install / configure in under 10 minutes and will not open up holes when running.

---

### Post by Chayak on 2011-07-22
> **stevennlv said:**
> I've heard of a smoothwall. But how in the world would I set a physical machine between a host an a virtual machine? Or are you talking two separate physical machines?

I'm talking physical but it is possible to do it virtually.  Though you can't do it with VMware player, you would have to use VMware Workstation. In a more complicated setup you can create teams that have their own complex private network setups.

You create a virtual machine, the virtual router, with two network interfaces set one interface to host only networking and the other to bridged.  You'll have to set up the virtual router with the addresses of the host only network and then point your host to it as a gateway.  When you have that working you can go into your network properties in windows and uncheck everything but the VMware driver.  This will basically kill the host OS's ability to use that port for TCP/IP networking, but VMware machines will still be able to use it in bridged mode.  That puts the virtual router between the host OS and the internet.

With teams you can get really complex and lay out network links, speeds, and packet loss.  If you put virtual routers in to connect those links and what you can create is only limited by your imagination.  I've used teams to prototype setups, create honeypot networks, pentesting playgrounds, or just general experiments.

ESXi is free, you can put that between your machine and the internet and create the virtual router in there and if you want even go as far as a multilayer defense.

---

### Post by bodhi.zazen on 2011-07-22
> **stevennlv said:**
> I'd just really love to have a pop up that tells me when someone is scanning me for open ports. Even if they don't exist.

Well, with that mentality, run this script:

```
zenity --warning --text "Alert you are being scanned right now! "
```

I think it is safe to say, if you are connected to the internet you are being scanned.

The question is what are you going to do about it ? Watching pop - ups or logs for suspect network traffic is an exercise in futility. This is where you need a tool like snort.

Snort monitors your traffic and alerts you to traffic you need to be concerned with. Take note: more often then not you will see false positives.

If you are not willing to take the time to learn a tool such as snort, well what is it you are expecting us to do for you ?

You are not running Ubuntu as a primary OS, and several very experienced users have provided you with information.

You can lead a horse to water, but it is up to you to follow through.

---

### Post by stevennlv on 2011-07-22
> **bodhi.zazen said:**
> Well, with that mentality, run this script:

```
zenity --warning --text "Alert you are being scanned right now! "
```I think it is safe to say, if you are connected to the internet you are being scanned.

The question is what are you going to do about it ? Watching pop - ups or logs for suspect network traffic is an exercise in futility. This is where you need a tool like snort.

Snort monitors your traffic and alerts you to traffic you need to be concerned with. Take note: more often then not you will see false positives.

If you are not willing to take the time to learn a tool such as snort, well what is it you are expecting us to do for you ?

You are not running Ubuntu as a primary OS, and several very experienced users have provided you with information.

You can lead a horse to water, but it is up to you to follow through.


You know dude, it is really sad that you ended up being the guy with the keys to the kingdom. You have to be one of the most condescending people it has ever been my displeasure to talk to on the net. And that is saying a lot.

I never once said that I wasn't willing to learn.

And I wasn't complaining about the documentation on AppArmor. It looks great. Well very done. Lot's of information. I DON'T UNDERSTAND IT!

Dude, (and I'm thinking you're a guy cuz I've never met a woman as arrogant as you) I'm a security guard.

When you get right down to it I'm observant, loyal, honest and true. Kind of like a dog with opposable thumbs that can do things that are a little spiffier than fetch.

Um, MR, I"m all zen, Try this one one for size: I have my place in the world too. And believe it or not I'm actually &%$%^ good at what I do.

I'm sorry that does not include having a two bazillion IQ and being able to instantaneously comprehend the deep mystical inner workings of a computer. Or the ability to pick up an entire new, highly complex language (computer code) in like three seconds flat.

I've been in a point and click world for 20 years. It's what I know.

And I hate to break it to you, but I AM THE FAMILY IT GUY.

I take care of the computers for my dad, mom, grandma, sister, little brother and several nieces and nephews. To use the car analogy again: when somebody needs a carb rebuilt they bring it to me so they don't have to drop $500 at a shop. If I can't fix it then you have to go to the mechanic.

And I know tons of guys like that.

If you really want to save the computing world you're going to have to climb down off of your high horse and put this stuff in terms that people like me can understand. Because until you do I'm not going to put it my computer as the primary OS. And I'm sure as heck not going to put it on my grandma's computer. Not even as a VM. She's doing good to e mail.

I still have questions about AppArmor.

But I'm not even going to bother asking you.

I'm obviously way out of my league here.

I'm going back to the general forums where I belong.

Sorry I got mud on your carpet. I'm sure it will come out though.

Somebody please put this thread to sleep.

I won't be back.

I'm not doing anything here but spinning my wheels.

---

### Post by Thewhistlingwind on 2011-07-22
> **stevennlv said:**
> I truly appreciate all the info.

Tonights 7 hours crash course marathon session will be devoted to GuFw and AppArmor. And your reply has been booked marked.

But, I'm not sure that you understand what I'm trying to achieve. This is still primarily a win7 box by design. But, I've come to the conclusion that as an end user I no longer have the skill level to adequately secure any windows install that connects directly to the internet. Personally I think the bad guys have won and that no windows end user can feel truly secure on a strictly win box any more. At least not if they have even the most basic understanding of computers.

**The bad guys don't have to "win" if they were never losing in the first place. There was a time when windows broadcasted your home directory as a file server to the world!**

I understand that *nix is by nature more secure than windows. I also understand that lot's of people smarter than I have worked hard to make the Ubuntu distro even more secure and usable for folks like myself. And I appreciate it very much.

**While I don't count myself among those people, thanks.**

However, IMHO Ubuntu is still not up to a level of ease of use that would make me comfortable using it as my primary OS or even dual booting. A perfect example is clamav. On the windows side of the box it took me 10 minutes to install and configure my AV. It took me a seven hour marathon session of reading, tinkering, testing, trying and retrying and asking for help to get clam AV installed to Ubuntu.

[B]Hint: Never download programs from the net run sudo apt-get.

sudo apt-get clamav, should have done it.
[/B]
But, I do feel that at this point in its development / cross referenced with my skill level that an Ubuntu VM will make an excellent security tool for my win7 install. That is why I chose Ubuntu to protect my win install from the net.  

**It's the only way to use windows IMO.**

So, what I am attempting to do is create a hybrid system with what I feel to be the best of both worlds. I am building an Ubuntu virtual machine to act as my "agent" so to say on the internet. Basically the whole purpose of my UVM is act as a "super-duper" sandbox for my net connection. I actually don't plan on getting real deep in to Ubuntu. No farther than I have to achieve to my desired result. The windows side of the box will still be getting plenty of use for other things and be my primary concern.

**Just to note, Ubuntu's much faster than the VB. Once you "get it" your attitude will change.**

And to be honest I'm really not all that worried about the UVM per se becoming corrupted. Once I feel it's done I'll just back all the files up to DVD on the win side of the machine. And be done with it other than keeping it up to date. If it takes a poop I'll just drag and drop the back up in to the appropriate folder and re-run the updates. Viola! 

**K then.**

However, I am concerned about such things as DLing an e book in a malformed .pdf carrying a windows executable payload on the UVM (where I know it will have no effect). Then emailing it to my win machine side of the box so that I can drop it on my e-reader. That could cause lots of problems. Hence I will use clam to scan it in the UVM, then yahoo will scan it with NAV, then on the win side I'll scan it again. If a payload gets through all that then I don't know what else to do. And I know that's a lot of work. But, I feel it's worth it.

**If I'm a virus writer, and I write your malformed pdf. It's very easy to go "Huh, they're blocking me now. Better recompile!" and the ID process for the virus starts all over again. If you are running windows, and you've visited any site out of say, the narrow band of 100% trust sites, assume you have been infected, period.**

And please don't say just take the plunge and switch over. I'm not ready to go there and may never be.  

**I won't.**

Remember the whole purpose of the UVM is to protect the win7 install. I don't want someone who knows 10k times more than I do walking through the back door of my UVM and right in to the heart of my "real" machine.

**Normally it's just "A smidgeon in the wrong direction." more than you do.**

Even if you think such a thing is not necessary I'd like it for peace of mind, if nothing else. I know you said not all inbound connections are bad. I disagree. If for no other reason than the way I have this thing set up right now there is absolutely no legitimate (i.e. need it for something to work) reason for an inbound connection to be seeking me out. Hence, by default, they are all bad.

**Well, I'm going to be honest here, if you have no listening services, I fail to see how your going to get cracked. I think you want this classic site: ****<Link removed>**

And, as I've done some more reading I don't think I really need an IDS.

What I need is much simper: A graphical tool that does not run in root that will monitor my firewall and notify me of the IP of any inbound connection attempts. Then I can run a who is on the IP and decide if I want to end the UVM session to protect my win install.

**If your firewalls done right, they can sling bits all day and it won't make any difference.**

I think something like that that plus AppAmor and taking out FS / adding GuFW will finish my UVM and then I can start building an XP VM to watch netflix. :)

**Netflix, ah, the bane of Linux users everywhere.**

Any suggestions on a tool that would do that job for me?

**It's unnecessary, IMO.**



My responses in bold, seriously though dude, you are doing more than 99% of windows users on the net.

EDIT: *shrug* I have no problem with Mr. Zazen, it seems like some people read internet voices in a more condescending tone than others.

Edit2: regardless, if you find someone condescending on a tech forum, thats a common occurrence, ignore that person as best you can..

Edit3: As I suspected that sites classic for a reason.

The point is here is that unless you have something akin to SSH server running, a firewall shouldn't be letting anyone connect at all. (Or even if you DO have these services running!)

---

### Post by bodhi.zazen on 2011-07-22
> **stevennlv said:**
> I DON'T UNDERSTAND IT!

Well, your problem is that you insist on running windows, which we both agree is insecure, and you are new to Ubuntu.

Most new users migrating from windows do not believe it, but, if you want to run a secure OS, all you need to do is run Ubuntu.

Ubuntu is secure out of the box, you do not need to do anything to harden it.

If you feel you must do something , install NoScript in firefox.

You can enable your firewall if you want, but as there are no significant open ports doing so adds little.

```
sudo ufw enable
sudo ufw default deny
```

No antivirus, no spy ware scanning, no graphical firewall to monitor your network traffic, check all those tools at the door, they are completely unnecessary.

You can learn things such as snort, apparmor, and similar tools, but there is no need, you are secure enough without them.

The most common cracks / intrusions we see on these forums are due to :

1. Weak passwords.
2. VNC (desktop sharing). This is an insecure protocol, if you need this functionality use FreeNX (rather then the default VNC server).
3. ssh, but again this is almost always due to using ssh with a weak password.
4. Infrequent social engineering (hey if you run this [code] ... ). The solution here, don't run code from untrusted sources.

Yes there is a learning curve with a new OS, takes 4-6 months. You were not born knowing Windows, you learned windows, and you can learn Ubuntu too.

If you have a question on need Ubuntu support, ask.

So far you have been asking questions which are complex and, despite your years of Windows experience, you do not yet have the background and experience to grasp. You can learn, but I would say you should start first by familiarizing yourself with your new OS. Once you are comfortable with using Ubuntu you can look at security, but when it comes to security, students are expected to do a ton of self learning.

You have been treated with exceptional kindness from the security group here.

---

### Post by MiniT on 2011-08-21
Hello all.
I [COLOR=SeaGreen]edited[/COLOR] this post.

To the original poster (though you said you wouldn't be back) :
I hope you give this community a further chance, though this issue clearly did not leave you filled with [COLOR=Orange]happiness[/COLOR].
  
_Advantage of delving into the [COLOR=Sienna]Ubuntu[/COLOR]/[COLOR=Orange]Linux[/COLOR] world, and giving it the time/effort it deserves_:
The Linux community - as goofy and problematic as it  can be - is free to respond and change and reshape itself in ways that  better suit the needs of security than is Microsoft, or any of its fellow for-profit companies.  In contrast, here there are unpaid  coders and weekend warriors, and projects for corporations that turn  into open source tools. Here are highly dedicated folks whose  accomplishments are taken for granted by many users - as well they  might, because the earth, strong and solid beneath our feet, is ignored  unless it becomes unstable.

I don't know whether the OP was right to  be so cheesed off or not.  I suspect you're right [COLOR=Purple]Bodhi[/COLOR], that  experience is the best teacher for most.  I also suspect that the OP was  a man after my own heart.  A pronouncement from the security guru is a  bit intimidating, and we all react differently.  In this case, there are  alot of security gurus about. :)  That's both extremely [COLOR=Orange]awesome[/COLOR], and  highly intimidating.

Secure is  relative, as has been said by smarter people than me many times.  And the weakest link is often the [COLOR=Silver]human[/COLOR].

I'm proud of participants in this [COLOR=Sienna]Ubuntu community[/COLOR].
Fact of life: not everyone will get the answer that makes them happy.

peace 
yall rock
MiniT :idea::!::cool:

---

