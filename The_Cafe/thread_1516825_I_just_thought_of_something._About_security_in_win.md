---
title: "I just thought of something. About security in windows &amp; linux."
date: 2010-06-24
forum: The Cafe
---

### Post by dragos240 on 2010-06-24
In linux, we are taught to never login as root and to use a non-privileged user, for security reasons. In windows, people use an administrator account all the time. Which gets the most viruses? See where I'm going with this?

---

### Post by Bachstelze on 2010-06-24
Yeah, and when Windows tries to fix that with UAC, people just disable it because it's "annoying". See where I'm going with this?

---

### Post by dragos240 on 2010-06-24
> **Bachstelze said:**
> Yeah, and when Windows tries to fix that with UAC, people just disable it because it's "annoying". See where I'm going with this?

Yeah. But why don't people just make a limited account to use, and when they install a program they use "run as adminstrator". Seems much safer.

---

### Post by matchett808 on 2010-06-24
windows users want everything to 'just run' so the get annoyed when all thier viruses 'just run'....I think that this conversation could go on all day...

---

### Post by dragos240 on 2010-06-24
> **matchett808 said:**
> windows users want everything to 'just run' so the get annoyed when all thier viruses 'just run'....I think that this conversation could go on all day...

Yeah, if people listened to reason, they wouldn't have so many problems with their computers.

---

### Post by Marlonsm on 2010-06-24
I've used Windows 7 for quite some time now, and I have to say, it's much better now.
UAC is not THAT annoying anymore. Not more annoting than having to type the root password in Linux, at least.
Windows might be more insecure for other reasons, but that is not one of them anymore.

---

### Post by Lucradia on 2010-06-24
Windows is "mainly" insecure because A.) It is almost all closed-source; and B.) Because it has the majority of market share.

If each platform had 1/3 market share (less if there are more platforms), virus makers would have a hard time on what to choose to infect.

However, virus makers would probably still choose windows due to its closed-source.

---

### Post by dragos240 on 2010-06-24
> **Marlonsm said:**
> I've used Windows 7 for quite some time now, and I have to say, it's much better now.
UAC is not THAT annoying anymore. Not more annoting than having to type the root password in Linux, at least.
Windows might be more insecure for other reasons, but that is not one of them anymore.

There are still attack sites, that will attack if you are on an admin account. And to my knowledge, that hasn't stopped.

---

### Post by matchett808 on 2010-06-24
just to put in a small contraversial point - just because something is closed sourced doesn't *always* make it insecure....but yeah it contributes to windows crapiness....

---

### Post by mcphargus on 2010-06-24
The market-share thing is a falacy. There are more servers on the web running linux, and those servers make a much more *ahem* interesting target for a malicious user

Consider that they're linked to other linux servers containing databases that hold information that's more useful to ID thieves.

The market-share Linux has as a platform for larger datastores makes it an enourmous target.

---

### Post by ubunterooster on 2010-06-24
> **mcphargus said:**
> The market-share thing is a falacy. There are more servers on the web running linux, and those servers make a much more *ahem* interesting target for a malicious user

Consider that they're linked to other linux servers containing databases that hold information that's more useful to ID thieves.

The market-share Linux has as a platform for larger datastores makes it an enourmous target.
Also, consider also the the first Virii were on Unix not Windows.

---

### Post by MCVenom on 2010-06-24
> **Lucradia said:**
> Windows is "mainly" insecure because A.) It is almost all closed-source; and B.) Because it has the majority of market share.

If each platform had 1/3 market share (less if there are more platforms), virus makers would have a hard time on what to choose to infect.

However, virus makers would probably still choose windows due to its closed-source.
Mac OSX is closed sourced too; they could choose to attack it just as well. :P

But then you consider that closed isn't always inherently insecure, (and open isn't always inherently more secure) and Linux's server marketshare, and they become a target too. We'd all receive about equal *interest*, I should think.

---

### Post by Lucradia on 2010-06-24
> **BlackOtaku said:**
> Mac OSX is closed sourced too; they could choose to attack it just as well. :P

Not the kernel.

---

### Post by dragos240 on 2010-06-24
Closed source doesn't make something insecure. It's just a way of developing, and while I prefer open to closed, the end result is generally the same.

---

### Post by MCVenom on 2010-06-24
> **Lucradia said:**
> Not the kernel.
Fine, OSX is mostly closed but has open source parts. Updates to these parts are pushed out at Apple's discretion though, and I would point out that Apple seems wholly ashamed of pushing routine updates. :P

Still if you read the post you'd see that the point I made still stands. There's no reason why the attackers en masse would choose Windows over Mac if they had the same market share; and IMO Mac is just as vulnerable as Windows.

---

### Post by MCVenom on 2010-06-24
> **dragos240 said:**
> Closed source doesn't make something insecure. It's just a way of developing, and while I prefer open to closed, the end result is generally the same.
This. +1

---

### Post by dragos240 on 2010-06-24
> **BlackOtaku said:**
> Fine, OSX is mostly closed but has open source parts. Updates to these parts are pushed out at Apple's discretion though, and I would point out that Apple seems wholly ashamed of pushing routine updates. :P

Still if you read the post you'd see that the point I made still stands. There's no reason why the attackers en masse would choose Windows over Mac if they had the same market share; and IMO Mac is just as vulnerable as Windows.

Actually, OSX is mostly open, most of it's core components are open source, it's gui and such are closed, but that doesn't count for much.

---

### Post by MCVenom on 2010-06-24
> **dragos240 said:**
> Actually, OSX is mostly open, most of it's core components are open source, it's gui and such are closed, but that doesn't count for much.
Alright OSX is mostly open. Back to the topic at hand; it's hard to change the users habit's sometimes. I think UAC was a great leap in the right direction.

---

### Post by dragos240 on 2010-06-24
> **BlackOtaku said:**
> Alright OSX is mostly open. Back to the topic at hand; it's hard to change the users habit's sometimes. I think UAC was a great leap in the right direction.

Agreed. UAC was good, It's just that stubborn average computer user. When microsoft does something right, people just figure out a way to disable it.

---

### Post by Johnsie on 2010-06-24
Linux servers are hacked all the time. Usually it's more profitable to hack a Linux server then a Linux desktop. 

For example:

If you hacked one Ubuntu repository server you could spread malware to hundreds of desktop users.

If you hacked a download site for a windows app you could spread your malware to hundreds of Windows users,


Also, People seem to think that a user account on Linux is rather weak compared to the admin account. Never underestimate the power of a user account.

Without being an admin a user can:

-Send mass emails
-Connect to various websites or other internet protocols to spread spam
-Add something to that users gnome session (gnome startup) that starts up every time the user logs in
-Install and run scripts in the users home area
-Access file systems on usb sticks
-Send large numbers of packets to other machines


And to do this all the hacker needs to do is exploit something in the web browser or another program.

Check out [http://ubuntu.com/usn](http://ubuntu.com/usn) for a list of some of the vulnerabilities that could allow a hacker to execute evil scripts.

---

### Post by samalex on 2010-06-24
> **dragos240 said:**
> In linux, we are taught to never login as root and to use a non-privileged user, for security reasons. In windows, people use an administrator account all the time. Which gets the most viruses? See where I'm going with this?

Linux and also Unix were written for multiple users, so they can share resources much more efficiently.  Plus it's common place to install applications within your profile or even within a common area that doesn't require many permissions.  Windows on the other hand was originally written for a single user, so even though modern versions of Windows are trying to get more multi-user friendly with locked down admin accounts, so many programs still want to use those admin-only features or write to C:\Program Files.  

It's like their solution is to just bug you for an Admin password with everything, which most people do disable ... or just run as admin to get around it.  Until Microsoft can make this more transparent, or move to a Unix-style OS like everyone else, I don't see them fixing this anytime soon.  And yeah, running as Admin will open them up to all types of critters.

Sam

---

### Post by pwnst*r on 2010-06-24
> **dragos240 said:**
> In linux, we are taught to never login as root and to use a non-privileged user, for security reasons. In windows, people use an administrator account all the time. Which gets the most viruses? See where I'm going with this?

So brilliant.

---

### Post by cascade9 on 2010-06-24
> **ubunterooster said:**
> Also, consider also the the first Virii were on Unix not Windows.

Viruses, not virii- 

[http://web.archive.org/web/20040208152350/www.perl.com/language/misc/virus.html](http://web.archive.org/web/20040208152350/www.perl.com/language/misc/virus.html)

I should make that my sig....if I ever make one, I cant be bothered with sigs in 99.99% of cases.

---

### Post by mcphargus on 2010-06-24
> **dragos240 said:**
> When microsoft does something right, people just figure out a way to disable it.

Hence the Microsoft mindset. Which is a little off, IMHO.

"I don't care if I didn't write it, I paid for it, it's mine; it should behave the way I want it to behave."

As opposed to the Ubuntu (or larger open-source community mindset)

"This thing isn't behaving the way I think it should behave."(User files a bug, dev's triage but lo-pri the bug, so the user fixes it herself, and then submits a patch. Dev's review it for security issues, find one, and compromise on a solution.)

Security holds to a certain degree. User is happy; developer is happy.

---

### Post by MCVenom on 2010-06-24
> **pwnst*r said:**
> So brilliant.
Hmm? Your point sir?

---

### Post by dragos240 on 2010-06-24
> **BlackOtaku said:**
> Hmm? Your point sir?

He's your forum troll. ;)

He's a regular here.

A regular Troll :lolflag:

---

### Post by ubunterooster on 2010-06-24
> **cascade9 said:**
> Viruses, not virii- 

[http://web.archive.org/web/20040208152350/www.perl.com/language/misc/virus.html](http://web.archive.org/web/20040208152350/www.perl.com/language/misc/virus.html)

I should make that my sig....if I ever make one, I cant be bothered with sigs in 99.99% of cases.
Oops.

---

### Post by kamaboko on 2010-06-24
Both of my parents are set up as limited users on their Windows computers.  I've had zero...nada...zilch...problems with it setup that way.  They're using MS Essentials for anti-virus, and it's a great program; very light and you don't even know it's there, but effective.  I have absolutely no concerns about them getting hacked or a virus, trojan, etc.

---

### Post by cascade9 on 2010-06-24
> **ubunterooster said:**
> Oops.

LOL, common mistake. 

Probably less common than running windows 2K/XP in 'admin' mode though....which is far worse than misusing a dead language ;)

---

### Post by dragos240 on 2010-06-24
> **cascade9 said:**
> LOL, common mistake. 

Probably less common than running windows 2K/XP in 'admin' mode though....which is far worse than misusing a dead language ;)

In normal circumstances. But if someone had 100,000 nucular warheads planted underground across the world, and he had the detination button in his hand, and asked you how to pronounce virus (plural). Of course that's very unlikely, but it would be much worse.

---

