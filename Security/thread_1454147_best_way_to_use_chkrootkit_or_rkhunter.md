---
title: "best way to use chkrootkit or rkhunter"
date: 2010-04-14
forum: Security
---

### Post by Rubi1200 on 2010-04-14
Hi,
can anyone tell me what the best method is for checking for rootkits? I have heard that it is best not to install and run these programs on the distro itself. Would it be possible to install them on another distro/partition and then use them to check for rootkits on my main partition/distro (Ubuntu)?
Thanks

---

### Post by HermanAB on 2010-04-14
The best way to find them?  Probably tcpdump and ngrep.

---

### Post by bodhi.zazen on 2010-04-14
> **Rubi1200 said:**
> Hi,
can anyone tell me what the best method is for checking for rootkits? I have heard that it is best not to install and run these programs on the distro itself. Would it be possible to install them on another distro/partition and then use them to check for rootkits on my main partition/distro (Ubuntu)?
Thanks

The best way to use these tools is to read the documentation.

I know that sounds like "rtfm", but in this case it is true.

In general this is not Windows and you almost certainly do not need to use these tools.

---

### Post by Rubi1200 on 2010-04-15
I appreciate the response, but I feel that I must also make a comment about what you said. With all due respect, you have been involved with Linux for at least 4 years; I have been using Ubuntu for 1 month. Secondly, I am sure that there are many people who come to Linux and find it hard to rid themselves of a Windows mentality; in this case, I think you might try to be slightly less dismissive when people ask questions which for you are no longer relevant, but which for me (and others) may help us understand what Linux is all about. I have already done quite a lot of reading, and although I understand that viruses are basically not an issue, I did read that rootkits are a potential issue. Therefore, as a complete beginner, I asked the question. Moreover, a lot of Linux security discussions involve the use of methods/approaches which are quite daunting to those taking their first steps. In my innocence/ignorance, I thought that a tool like rkhunter might be a potential solution. Having **now **read some of the documentation, I understand that it is better not to use something like this unless one is capable of understanding both the risks as well as the implications. In any event, I do appreciate that Linux is not Windows, and I am trying, slowly but surely, to wean myself away from the kind of Windows paranoia that seems to be rather annoying to a number of people on this forum.

---

### Post by OpSecShellshock on 2010-04-15
While rootkits are often described as a known risk, it's not a big risk. A lot of people are just looking for something to point to when discussing security issues (there are plenty of bigger risks to point to, but none of them involve unauthorized access/software being placed on your machine).

It makes little sense to check regularly for rootkits since there are no reports of a home user's desktop being compromised as far as I know, nor does anything on the order of a web based "exploit pack" exist in production that targets Linux desktops. People run things like rkhunter and chkrootkit when they notice odd connections, data loss, or suddenly missing logs on systems they're very familiar with. It's not the kind of thing you do on a daily basis.

---

### Post by Rubi1200 on 2010-04-15
Thank you for a brief and lucid explanation on this subject; much appreciated!
:)

---

### Post by LeeDaugherty on 2010-04-15
Long story short, relax.  You aren't on Windows anymore.  While not impossible, comparitively to a Windows machine, being comprimised (without doing something really stupid), isn't going to happen.  And in any case, the time it takes to comprimise a Linux box, isn't good for business.  And as for rootkits, I'll bet you a case of beer you will never see or meet anyone that has seen one the rest of your life.  They exist, they are evil, they are nasty, and if you are holding on to such valuable information someone is going to spend the time it takes to hook a linux kernel, they might need it more than you.  Chkrootkit and rkhunter have become (in my opinion...don't shoot me!) almost novelties.  The programs are there for people to feel safer.  The rootkits they scan for are techy-campfire stories (it was a dark and stormy night, and the FU rootkit crept in the....).  So take a deep breath, and realize it's nice to relax and use a computer without firewalls, anti-virus, spyware scanners, updates, killbits, defragging, other stuff (not to imply those aren't all fun to have)...so have fun...get creative...and laugh at your friends who lay awake at night because there computer makes funny noises.

---

### Post by Rubi1200 on 2010-04-15
I must admit that I feel safer using Linux than when I still had Windows (I completely dumped it by the way). I think that part of the concern comes from using something new and unfamiliar. But, from the reading I have been doing I feel confident that Linux offers a more stable and secure computing experience; one that I am thoroughly enjoying so far.
I appreciate the candid and helpful response.
Thanks!

---

### Post by LeeDaugherty on 2010-04-15
We all came from the darkside, so I know what it's like.  It took me a long time, and there was no reason for my behavior.  It takes time to start trusting computers again, but it'll happen in time :P  So have fun, and welcome to freedom ! yay!

---

### Post by Rubi1200 on 2010-04-15
I agree with you about the taking time thing. I think that we were so used to dealing with Windows and its problems that we forgot to enjoy the experience. I have already discovered that I can do everything I could in Windows, if not more, and without most of the hassles. Of course, no OS is perfect and Linux has its quirks, but all in all, I am glad I made the switch. As you say, time to relax and release the hold of the Windows mentality.

---

### Post by Kinstonian on 2010-04-15
If you don't regularly monitor your box, then how do you know it's not hacked?  How do you trust it?  How do you know your controls are working?  How do you know what controls are appropriate?  Security monitoring plays a huge role in security... yes it's possible to go overboard with monitoring just like anything else, but everyone needs at least some monitoring.  For example, people should be familiar with normal processes and network connections.  However, without something like rkhunter to test whether there is a rootkit installed, how do you trust the ps/netstat output?

It's obviously always best to detect an attack at the earliest stage possible.  However, that usually doesn't happen.  If you fail to detect the recon, and then fail to detect the actual exploit, something like rkhunter can play an important role in detecting some of the post-compromise activity and can give you at least an idea as to how much you can trust your OS.

---

### Post by LeeDaugherty on 2010-04-15
Valid point, but it just simply doesn't happen.  Could it?  Yes!  In a production enviroments I run appropriate measures.  intrusion detection, pentest/vulnerability testing, name-it it's probably out there.  But at home?  Monitoring must give way to be studious and alert.  It's hard to sit here and say I know I didn't get hacked because I use Linux.  Cause that's only most of it.  There are times that this kind of behavior and action is neccessary.  And it isn't at home.  Rootkits do not exist for the home user, hackers do not exist for the home user, there is no such thing as a linux virus a linux trojan and I'll go ahead and said there is no such thing as a linux worm...now there are some obvious "technical" errors in that statement...but you have to get my gist.  I want people to be paranoid and watch out, but to sit here and read these posts, everyone needs to take a chill pill.  And I need to write a sticky about how things really work in the world.  Because for some reason everyone thinks that their family photos on their hard drive is the target of a huge global communist espionage hijack.

---

### Post by bodhi.zazen on 2010-04-15
> **Rubi1200 said:**
> I appreciate the response, but I feel that I must also make a comment about what you said. With all due respect, you have been involved with Linux for at least 4 years; I have been using Ubuntu for 1 month. Secondly, I am sure that there are many people who come to Linux and find it hard to rid themselves of a Windows mentality; in this case, I think you might try to be slightly less dismissive when people ask questions which for you are no longer relevant, but which for me (and others) may help us understand what Linux is all about. I have already done quite a lot of reading, and although I understand that viruses are basically not an issue, I did read that rootkits are a potential issue. Therefore, as a complete beginner, I asked the question. Moreover, a lot of Linux security discussions involve the use of methods/approaches which are quite daunting to those taking their first steps. In my innocence/ignorance, I thought that a tool like rkhunter might be a potential solution. Having **now **read some of the documentation, I understand that it is better not to use something like this unless one is capable of understanding both the risks as well as the implications. In any event, I do appreciate that Linux is not Windows, and I am trying, slowly but surely, to wean myself away from the kind of Windows paranoia that seems to be rather annoying to a number of people on this forum.

No reason to be hostile. I am not being dismissive. In fact you followed my advice, did some reading, and now have our answer. IMO this is the best possible outcome in security.

As with any OS you need to learn how it works and what is "normal". This is what Kinstonian and others are advising as well.

On windows one does not run antivirus or antispyware software and blindly delete every file found, or if they do they will often be faced with a re installation.

This is true on Linux as well.

As a new user you should start with the security sticky (it is a sticky for a reason) as well as the sticky on Intrusion detection and apparmor (these are also stickies for a reason). And you also need to start with learning at least the basics of system administration, including reading the logs.

These first steps are critical, otherwise you have no experience on which to judge if an anomaly is a hardware problem, misconfiguration problem, or security threat.

If you follow the advice in the security and apparmor stickies you will be fine, in fact you are probably fine without doing anything.

There are security threats in Linux, and if you are interested I would encourage you to become more security aware. As with any OS this takes time and experience and a bit of reading on your part.

FYI: I am working on updating the security stickies for the upcoming release of Ubuntu 10.04. This will include replacing the current sticky on Intrusion detection with two stickies, one on snort (NIDS) and a second on HIDS.

The stickies are currently posted as drafts for staff review.

---

### Post by Kinstonian on 2010-04-15
> **LeeDaugherty said:**
> Valid point, but it just simply doesn't happen.  Could it?  Yes!  In a production enviroments I run appropriate measures.  intrusion detection, pentest/vulnerability testing, name-it it's probably out there.  But at home?  Monitoring must give way to be studious and alert.  It's hard to sit here and say I know I didn't get hacked because I use Linux.  Cause that's only most of it.  There are times that this kind of behavior and action is neccessary.  And it isn't at home.  Rootkits do not exist for the home user, hackers do not exist for the home user, there is no such thing as a linux virus a linux trojan and I'll go ahead and said there is no such thing as a linux worm...now there are some obvious "technical" errors in that statement...but you have to get my gist.  I want people to be paranoid and watch out, but to sit here and read these posts, everyone needs to take a chill pill.  And I need to write a sticky about how things really work in the world.  Because for some reason everyone thinks that their family photos on their hard drive is the target of a huge global communist espionage hijack.

Speaking of the real world, here's data from a real incident involving a desktop honeypot.  Not Ubuntu, but it could of been.

> 
/.help/ss: Linux.RST.B-1 FOUND
/.help/ips: Linux.RST.B-1 FOUND
/.help/ss2: Linux.RST.B FOUND
/.help/b.pl: Trojan.Perlbot FOUND
/.help/threads: Linux.RST.B-1 FOUND
/rk/bin/encrypt: Trojan.Rootkit-117 FOUND
/rk/bin/pg: Trojan.Rootkit-119 FOUND
/rk/bin/syslogd: Trojan.Rootkit-115 FOUND
/rk/bin/slocate: Trojan.Rootkit-116 FOUND
/rk/bin/ssh-only.tgz: Trojan.Rootkit-114 FOUND
/rk/bin/sz: Unix.Lion FOUND
/rk/bin/pstree: Trojan.Rootkit-118 FOUND
/rk/bin/ssh: Trojan.Rootkit-114 FOUND
/rk/bin.tgz: Trojan.Rootkit-115 FOUND
/rk/vadimII: Linux.RST.B-1 FOUND
/bin/ping: Linux.RST.B-1 FOUND
/bin/mktemp: Linux.RST.B-1 FOUND
/bin/mount: Linux.RST.B-1 FOUND
/bin/umount: Linux.RST.B-1 FOUND
/bin/hostname: Linux.RST.B-1 FOUND
/bin/netstat: Linux.RST.B-1 FOUND
/bin/cpio: Linux.RST.B-1 FOUND
/bin/setserial: Linux.RST.B-1 FOUND
/bin/gawk: Linux.RST.B-1 FOUND
/bin/ed: Linux.RST.B-1 FOUND
/bin/basename: Linux.RST.B-1 FOUND
/bin/pgawk: Linux.RST.B-1 FOUND
/bin/grep: Linux.RST.B-1 FOUND
/bin/chgrp: Linux.RST.B-1 FOUND
/bin/cat: Linux.RST.B-1 FOUND
/bin/ash.static: Linux.RST.B-1 FOUND

[21:19:43] Warning: SHV4 Rootkit                             [ Warning ]
[21:19:44]          File '/etc/ld.so.hash' found
[21:19:44]          File '/lib/libext-2.so.7' found
[21:19:44]          File '/lib/lidps1.so' found
[21:19:44]          File '/usr/sbin/xntps' found
[21:19:44]          Directory '/lib/security/.config' found
[21:19:44]          Directory '/lib/security/.config/ssh' found


And even around here, it's somewhat common for people to get hacked.  Desktop or not, you got to be careful.

---

### Post by LeeDaugherty on 2010-04-15
Sweet!  I miss my nepenths honeypot...had to get rid of it spent too much time watching it...if memory serves me correct though, while I get giddy and excited at even seeing an attempt on a linux box, the rst dates back 2002...and what is Lion and I don't know the perl one...not saying it doesn't happen, but I don't want to see people jump the windows ship and spend what should be a joyous moment self-consumed with the trojan threat around every corner.  I'm just encouraging people to take a breath before they get paranoid that they got compromised.  Cause on this side of the fence, it is very rare in non-production enviroments.

---

### Post by Kinstonian on 2010-04-15
> **LeeDaugherty said:**
> Sweet!  I miss my nepenths honeypot...had to get rid of it spent too much time watching it...if memory serves me correct though, while I get giddy and excited at even seeing an attempt on a linux box, the rst dates back 2002...and what is Lion and I don't know the perl one...not saying it doesn't happen, but I don't want to see people jump the windows ship and spend what should be a joyous moment self-consumed with the trojan threat around every corner.  I'm just encouraging people to take a breath before they get paranoid that they got compromised.  Cause on this side of the fence, it is very rare in non-production enviroments.

It wasn't nepenthes, it was a high interaction honeypot.  I'm well aware that there hardly any malware for Linux compared to Windows and that people are better off using Linux as far as security goes.  However, monitoring should be and is part of not just good management, but security...  because believe me, Linux can be hacked too.

BTW you're right that it is old malware that still shows up every once in a while today.

---

### Post by LeeDaugherty on 2010-04-15
Made my day...I haven't seen or heard of those in years...it's probably not something to be proud of that I feel giddy now...I agree with monitoring, I just don't want to see home users bogged down with the threat around every corner attitude you have to have when you use windows.  This community is quicker to respond, Firefox has a stellar record, and you know what, it's easy to write off and say MS is attacked becasue of market share, but it does take a higher-level of will power and knowledge to walk into a linux box.  You can't just fire metasploit up and walk in.  You gotta know what you are doing.  And people that know that, don't come around to often :P  While Windows compromises are typically exploits, Linux breaches are typically poor password/brute force attacks.  Session hijacking can happen to anyone, so that's beyond the scope.  XSS/driveby/flash, can nail anyone, but that's where the numbers games kick in.  You are better going after IE, than trying to negate FF.

---

### Post by Kinstonian on 2010-04-15
> **LeeDaugherty said:**
> Made my day...I haven't seen or heard of those in years...it's probably not something to be proud of that I feel giddy now...I agree with monitoring, I just don't want to see home users bogged down with the threat around every corner attitude you have to have when you use windows.  This community is quicker to respond, Firefox has a stellar record, and you know what, it's easy to write off and say MS is attacked becasue of market share, but it does take a higher-level of will power and knowledge to walk into a linux box.  You can't just fire metasploit up and walk in.  You gotta know what you are doing.  And people that know that, don't come around to often :P

I love the open source community, and benefit from it every day.  The thing is that most of the attacks around here seem to be due to a mistake that the user made.  For example not knowing a service was installed, choosing a poor password, a misconfiguration, etc.  Regardless of how it happened, monitoring is beneficial.  As the saying in security goes prevention is ideal, detection is a must.

---

### Post by LeeDaugherty on 2010-04-15
They say that at the free clinic too

---

### Post by Kinstonian on 2010-04-15
> **LeeDaugherty said:**
> They say that at the free clinic too

lol see, it's true. :)

---

### Post by bodhi.zazen on 2010-04-15
> **Kinstonian said:**
> And even around here, it's somewhat common for people to get hacked.  Desktop or not, you got to be careful.

Let's not feed the paranoia =)

You are talking about a honey pot, which is a system specifically designed to track these kinds of things.

A honey post is not the same as a Desktop installation.

In pawn2own 2009 Ubuntu was not cracked, both Windows and OSX were.

[http://blogs.zdnet.com/security/?p=995](http://blogs.zdnet.com/security/?p=995)

People dismiss the results often dismissed nobody was interested in cracking Ubuntu, I would not dismiss a 10,000 prize so fast, but you can decide for yourself.

The most common "crack" on these forms by far is people running VNC.

Do you have any data to support your claim that Ubuntu desktops are frequently cracked ?

The last time I looked, the average "survival time" of an unpatched Windows installation was 40 minutes.

I have not seen any data that Ubuntu systems are cracked with any regularity.

---

### Post by Kinstonian on 2010-04-15
> **bodhi.zazen said:**
> Let's not feed the paranoia =)

You are talking about a honey pot, which is a system specifically designed to track these kinds of things.

A honey post is not the same as a Desktop installation.

In pawn2own 2009 Ubuntu was not cracked, both Windows and OSX were.

[http://blogs.zdnet.com/security/?p=995](http://blogs.zdnet.com/security/?p=995)

People dismiss the results often dismissed nobody was interested in cracking Ubuntu, I would not dismiss a 10,000 prize so fast, but you can decide for yourself.

The most common "crack" on these forms by far is people running VNC.

Do you have any data to support your claim that Ubuntu desktops are frequently cracked ?

The last time I looked, the average "survival time" of an unpatched Windows installation was 40 minutes.

I have not seen any data that Ubuntu systems are cracked with any regularity.

The honeypot was a misconfigured desktop just like the desktops of people who show up here because they've been cracked.  I said "somewhat" common. :)  I wouldn't say it happens frequently here, but it's certainly not unheard of for there to be a post here or on other forums with people requesting advice on what to do after they've been compromised.  I would think there are a lot more incidents that go undetected because some people don't think monitoring is important so they don't bother with it.

---

### Post by youWho on 2011-02-07
> **Rubi1200 said:**
> I appreciate the response, but I feel that I must also make a comment about what you said. With all due respect, you have been involved with Linux for at least 4 years; I have been using Ubuntu for 1 month. Secondly, I am sure that there are many people who come to Linux and find it hard to rid themselves of a Windows mentality; in this case, I think you might try to be slightly less dismissive when people ask questions which for you are no longer relevant, but which for me (and others) may help us understand what Linux is all about. I have already done quite a lot of reading, and although I understand that viruses are basically not an issue, I did read that rootkits are a potential issue. Therefore, as a complete beginner, I asked the question. Moreover, a lot of Linux security discussions involve the use of methods/approaches which are quite daunting to those taking their first steps. In my innocence/ignorance, I thought that a tool like rkhunter might be a potential solution. Having **now **read some of the documentation, I understand that it is better not to use something like this unless one is capable of understanding both the risks as well as the implications. In any event, I do appreciate that Linux is not Windows, and I am trying, slowly but surely, to wean myself away from the kind of Windows paranoia that seems to be rather annoying to a number of people on this forum.

To be honest, dear Bhodi.zazen your expert advice is very much appreciated, but it does seem true that you have forgotten how daunting GNU/linux can be at first. I've been a *very* happy user since early last Summer, though frankly there were a few times when I had basically no idea what to do. I can honestly say that since then I've actually posted more posts on these forums offering help (as far as I was able, essentially trying to offer tips to people even noobier than I) than posts asking for help, but no kidding, the first steps, even on Ubuntu, can include weirdly extreme "issues". Why, just a month ago I was trying to go from Lucid Ubuntu Studio to Maverick and upon installing the (proprietary) nvidia driver I had an absolutely non-functioning display. I managed to figure it out all by my lonesome, and yes I then posted my tips on how I solved it. But I just wanted to say this, as gently as possible too: if you could please be a little patient with those of us who don't yet know as much as you do, but who are sincerely learning, it would be helpful. And no kidding, thanks again for your obviously advanced advice.

---

### Post by Soul-Sing on 2011-02-07
> **Rubi1200 said:**
> Hi,
can anyone tell me what the best method is for checking for rootkits? I have heard that it is best not to install and run these programs on the distro itself. Would it be possible to install them on another distro/partition and then use them to check for rootkits on my main partition/distro (Ubuntu)?
Thanks

Hi,
Ubuntu and linux is great, its by default more secure than Windows.
But imo Ubuntu has one achillesheel (maybe two :) ) and that is its softwaresources. People tend to install third party software, software with bad licenses. Be very critical bout that, stick to the off. softwaresources, set critical/security updates on auto, and you dont need chkrootkit and rkhunter.
(rkhunter: installs a deamon-like service exim-4 by the way)

---

### Post by bodhi.zazen on 2011-02-13
Thread closed at OP request.

---

