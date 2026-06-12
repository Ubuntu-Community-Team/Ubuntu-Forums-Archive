---
title: "Windows 7 Security - Subjective Test + Tips for XP Users"
date: 2009-11-03
forum: The Cafe
---

### Post by murderslastcrow on 2009-11-03
**_The Test_**

So, we used the RTM for the 30 day trial on my family's home computer. We installed Google Chrome, left UAC at default settings, and installed avast Antivirus, along with setting up the firewall. We were determined to allow these security measures take care of themselves for 30 days without any maintenance whatsoever.

Here is a list of programs that have been installed since then. iTunes 9, Limewire, The Sims 2, Epson Scan/Drivers, GIMP, OpenOffice.org (all in order). That's it.

30 days later, I boot into an Ubuntu partition to do an external virus scan with the same antivirus software, avast. We did a thorough scan.

64 trojans, adware, spyware, and viruses (3 of them were viruses, to be fair). Deleted them all.

A few things to take note of

- Internet Use was not monitored. There's no way of knowing the sites were visited with Chrome or were safe, but this is all that I've observed when checking in.

- Limewire's network has a lot of potentially corrupted files.

- About 20 of the results listed were obviously false-positives ("corrupted" zip files, listed merely because of their extension or filename).

**_Tips for XP Users Thinking of Upgrading to 7_**

Unless you need DirectX 10 for some reason, or new hardware that won't work with XP, don't do it.

The "security" added to Windows 7 is a simple program called User Account Control. This works somewhat like sudo, except that it tests primarily install programs and programs that can access the internet.

It doesn't test standalone exes in most cases. It doesn't stop ActiveX calls that can download malicious content to your computer.

To make XP more secure than Windows 7, make sure you do the following.

1. Install a good antivirus. avast is good, especially if you plan on doing weekly scans.
2. Set up automated defragmentation for stability. [http://www.microsoft.com/windowsxp/using/setup/learnmore/tips/gehrke1.mspx](http://www.microsoft.com/windowsxp/using/setup/learnmore/tips/gehrke1.mspx)
3. Use suDown or SudoWin to have a sudo-like environment in XP (more reliable than UAC in Vista and 7). It's best if you can use a limited user account by default with this, but some programs won't run properly unless you're an administrator (sadly).
4. Set up your firewall.
5. Don't use Internet Explorer, no matter what you do.

Beyond this, there are extra tools you can use to scan, like Spybot Search and Destroy and Malware Bytes.

If you want the look and feel of Windows 7, you don't have to upgrade your hardware or switch your OS. If you're not obsessed with the fading effects or Alt-Tab switcher present in 7, then you can have everything else visually available in 7. This includes the windows shake, snap, and jump list features.

[http://www.windowsxlive.net/seven-transformation-pack](http://www.windowsxlive.net/seven-transformation-pack)

This one-time installer will give you all the cool features of Windows 7 with a minimal memory hit.

**_Final Notes_**

Do you guys think my test was subjective? Is there anything else you think we could do to help XP users deal if they aren't in a position to switch to Linux (due to program compatibility, mainly)?

We all need to save money these days, and we should all be willing to help any computer user secure their OS without thinking they have to pay out their ears to get things working. Please share your thoughts.

---

### Post by NoaHall on 2009-11-03
Which software did you use to scan? Remember, these things report a LOT of false positives. 

Also, Limewire. That's crowded with virus and malware. I'm not surprised you got those results if you were downloading things from Limewire.

---

### Post by CharlesA on 2009-11-03
> **NoaHall said:**
> Which software did you use to scan? Remember, these things report a LOT of false positives. 

Also, Limewire. That's crowded with virus and malware. I'm not surprised you got those results if you were downloading things from Limewire.

+1

Installing limewire is just asking for trouble tbh.

---

### Post by murderslastcrow on 2009-11-03
That's true- I suspect that about 20 of the results (corrupted zip files) were probably false positives.

Also, I didn't monitor web use or limewire use. I wouldn't be surprised if my Mom wanted to use Internet Explorer and if there weren't a few out-of-the-way sites visited.

I think I'll revise the post with this information, since I still have the log files. After reading it I realize that, although I was trying to be concise, it looks very biased. XD

---

### Post by NoaHall on 2009-11-03
> **murderslastcrow said:**
> That's true- I suspect that about 20 of the results (corrupted zip files) were probably false positives.

Also, I didn't monitor web use or limewire use. I wouldn't be surprised if my Mom wanted to use Internet Explorer and if there weren't a few out-of-the-way sites visited.

I think I'll revise the post with this information, since I still have the log files. After reading it I realize that, although I was trying to be concise, it looks very biased. XD

I see... I think most also regard files they can't scan as malware, and archives over 2GB.

---

### Post by ShaneR on 2009-11-03
The only secure computer is one that is turned off.

In my opinion, Vista and 7 did improve upon the security of the OS, but it still comes down to the person behind the keyboard to keep things safe.  I haven't had a virus or spyware on my windows system for longer than I can remember.  And that's mainly due to knowing where, and where not, to go.  If you install Limewire, don't talk security of the OS as you're just begging to be infected.  

And, contrary to popular belief, UAC in Vista and 7 has very little to do with end user security and more to do with corporate, another way to keep unwanted applications off of workstations.  It's not meant as an Anti-virus.

If you're on Windows.  Run a good AV, turn on the firewall, and surf with a little caution.  If you decide to run under a LUA, so much the better.

Honestly, it's very easy to keep Windows safe.  Yes, it's unfortuante It's the OS of choice for viruses, and Linux is spared that for now, but Windows can be locked down rather easily.

I'm not trying to "defend" anything here (although it sounds like it), I just simply disagree with your approach.

---

### Post by Jimleko211 on 2009-11-03
You didn't test XP in exactly the same way.

---

### Post by pwnst*r on 2009-11-03
LOL @ limewire.  who the hell uses that infested p2p?

---

### Post by H3l0 on 2009-11-03
> **shaner said:**
> the only secure computer is one that is turned off.

In my opinion, vista and 7 did improve upon the security of the os, but it still comes down to the person behind the keyboard to keep things safe.  I haven't had a virus or spyware on my windows system for longer than i can remember.  And that's mainly due to knowing where, and where not, to go.  If you install limewire, don't talk security of the os as you're just begging to be infected.  

And, contrary to popular belief, uac in vista and 7 has very little to do with end user security and more to do with corporate, another way to keep unwanted applications off of workstations.  It's not meant as an anti-virus.

If you're on windows.  Run a good av, turn on the firewall, and surf with a little caution.  If you decide to run under a lua, so much the better.

Honestly, it's very easy to keep windows safe.  Yes, it's unfortuante it's the os of choice for viruses, and linux is spared that for now, but windows can be locked down rather easily.

I'm not trying to "defend" anything here (although it sounds like it), i just simply disagree with your approach.

+1   :d

---

### Post by Giant Speck on 2009-11-03
I don't understand the reasoning behind not monitoring what websites were viewed in that thirty-day period of time.  The viruses have to come from somewhere, you know!  They don't just appear out of nowhere!

---

### Post by pwnst*r on 2009-11-03
> **Giant Speck said:**
> I don't understand the reasoning behind not monitoring what websites were viewed in that thirty-day period of time.  The viruses have to come from somewhere, you know!  They don't just appear out of nowhere!

oh, but they do!!!! it's windows ffs!!11111oneone

---

### Post by t0p on 2009-11-03
Lookee [here]("http://tech.slashdot.org/story/09/11/03/2123258/In-Test-Windows-7-Vulnerable-To-8-Out-of-10-Viruses"), someone else carried out a similar but different experiment:

> They installed Windows 7 on a clean machine — with no anti-virus protection — with User Access Control in its default configuration. They threw at it the next 10 virus/worm samples that came in the door. [Seven of them ran]("http://www.sophos.com/blogs/chetw/g/2009/11/03/windows-7-vulnerable"); UAC stopped only one baddie that had run in the absense of UAC. "Lesson learned? You still need to run anti-virus on Windows 7."

I like those last sentences: "Lesson learned?  You still need to run anti-virus on Windows 7."  Did anyone really think you *don't* need to?

---

### Post by MellonCollie on 2009-11-03
> **murderslastcrow said:**
> So, we used the RTM for the 30 day trial on my family's home computer.

Was it just the default account shared by everyone? Or did each person have their own user account?


> **murderslastcrow said:**
> We installed Google Chrome, left UAC at default settings, and installed avast Antivirus, along with setting up the firewall. We were determined to allow these security measures take care of themselves for 30 days without any maintenance whatsoever.

30 days later, I boot into an Ubuntu partition to do an external virus scan with the same antivirus software, avast. We did a thorough scan.

64 trojans, adware, spyware, and viruses (3 of them were viruses, to be fair). Deleted them all.

This doesn't pass the smell test. Did you check to see if Avast was updating properly in Windows? Edit: were these active, or just files sitting in a folder?

> **murderslastcrow said:**
> The "security" added to Windows 7 is a simple program called User Account Control. This works somewhat like sudo, except that it tests primarily install programs and programs that can access the internet.

It doesn't test standalone exes in most cases. It doesn't stop ActiveX calls that can download malicious content to your computer.

You can't install an ActiveX control without a UAC prompt. If the user gives a malicious ActiveX control the 'ok' to install, then who/what's at fault&#8212;the OS or the user?

---

### Post by NoaHall on 2009-11-03
> **MellonCollie said:**
> 

You can't install an ActiveX control without a UAC prompt. If the user gives a malicious ActiveX control the 'ok' to install, then who/what's at fault—the OS or the user?

The browser :)

---

### Post by Giant Speck on 2009-11-03
> **pwnst*r said:**
> oh, but they do!!!! it's windows ffs!!11111oneone

It's like rubbing raw chicken on your face!

---

### Post by murderslastcrow on 2009-11-03
You're right that you can't just rely on an OS for absolute security. I acknowledge your points.

I set all this up and let my family do whatever. Most Windows users I know use p2p similar to Limewire. I was planning to test a secured Windows 7 with whatever a typical family would use Windows 7 for.

So, a typical family will want to be very careful in Windows 7 compared to Linux. The truth is that, out of the box, Linux is very hard to screw up for the average family. And this has been noticed in my household.

The trial is up, so we're moving back to the Linux partition full time. I think that, if I try this again, I will include more cases than just this one. A control group (Windows 7 without any set up), and several users with different work loads and uses for their computers.

I do suspect that with the music downloads on Limewire there may have been less issues.

I don't think anyone's being defensive. :3 You all have very good points, so the next time I try something like this it will be more dependable. I guess I didn't take as many factors into account as I should have.

---

### Post by ShaneR on 2009-11-04
> **t0p said:**
> Lookee [here]("http://tech.slashdot.org/story/09/11/03/2123258/In-Test-Windows-7-Vulnerable-To-8-Out-of-10-Viruses"), someone else carried out a similar but different experiment:

Quote:
They installed Windows 7 on a clean machine — with no anti-virus protection — with User Access Control in its default configuration. They threw at it the next 10 virus/worm samples that came in the door. Seven of them ran; UAC stopped only one baddie that had run in the absense of UAC. "Lesson learned? You still need to run anti-virus on Windows 7." 

I like those last sentences: "Lesson learned?  You still need to run anti-virus on Windows 7."  Did anyone really think you *don't* need to?

Unbelievable. They have no business reporting on security with an approach like that.  They *don't* install an anti-virus and then report they were infected, and blame it on the OS? Please.  That would be like leaving your Ubuntu admin password clearly written on a sticky note, stuck to the side of your monitor, and then blaming the OS when someone sits down and wreaks havoc. 

They obviously need to read my previous post about UAC and get their facts straight.

This is why security in a Windows environment can be challenging: A lack of knowledge even when the proper information is easily available.  You can't blame any OS for a user's ignorance and lack of responsibility.  

Granted, I'll be the first to admit MS has made plenty of security blunders in the past, but,  as I said before, with a little effort and a little knowledge security concerns go away...regardless of the OS in use.

---

### Post by murderslastcrow on 2009-11-04
Quite honestly, since Windows has had this problem for so long, you'd think Microsoft would come up with some sort of useful solution by now. At the least include an antivirus with the system (or would that be against trade laws in the EU?).

Really. Honestly. This is the main detractor to Windows use. If Windows got viruses as little often as Linux, we would be on a much more even playing ground.

But, I think it would take a very creative approach to protect against viruses by still allow compatibility with Windows XP. I mean, surely XP Mode is a bit excessive? (if it works in Wine, why use VirtualBox at all?)

This is just like religious activists. Just because they're the dominant majority doesn't mean they have nothing to prove. An athiest or agnostic is merely a person who doesn't claim to assume the existence of a God (or to assume they need Windows applications). Windows still has to prove to us the divinity of its OS. But I see very little to benefit the average human being in paying for viruses.

Man, I'm a zealot. I just compared Microsoft to Christians (they probably are Christians). Sorry, that's unfair, they just want to make money and have a large mindshare in the global community...

Holy crap! THEY'RE ONE AND THE SAME!!! ILLUMINATI! XD

---

### Post by pwnst*r on 2009-11-04
> **murderslastcrow said:**
> I just compared Microsoft to Christians (they probably are Christians). Sorry, that's unfair, they just want to make money and have a large mindshare in the global community...



that's got to be the dumbest thing i've read on these forums in ages.  


congratulations.

---

### Post by MellonCollie on 2009-11-04
> **murderslastcrow said:**
> Quite honestly, since Windows has had this problem for so long, you'd think Microsoft would come up with some sort of useful solution by now. 

There is no solution so long as the end-user can install software. You can try to educate the user, but most non-techies don't seem to care.

---

### Post by murderslastcrow on 2009-11-04
I agree. I think that's probably the stupidest thing I've ever read on this forum ever. I was obviously kidding.

---

### Post by murderslastcrow on 2009-11-04
Anyway, I'll be coming up with a more scientific test in the near future. Just need a few more PCs to test on so I don't have to wait months to do all the tests on the same computer.

Sorry for all the irrational comments, by the way. I can be 'eccentric' at times. It'd be cool if a mod closed this post since I don't think it serves the purpose stated any longer.

---

### Post by pwnst*r on 2009-11-04
> **murderslastcrow said:**
> I agree. I think that's probably the stupidest thing I've ever read on this forum ever. I was obviously kidding.

you were kidding or you were being unfair?  take a stand.

---

### Post by murderslastcrow on 2009-11-04
Oh, I was a bit shortsighted with the testing, and need to conduct a more in depth study.

When it comes to the comments of money-making mind-stealing corportations/religions, I was only kidding. Impersonating people who actually think Microsoft is evil, when they're just a company (and believers are good people who want to share good virtues with others).

I mean, Microsoft's buggy operating system is no more evil than say, a video game with a lot of unfortunate glitches. Viruses are basically glitches, vulnerabilities, but in the case of an OS they can affect your personal data and financial well-being.

Linux isn't without it's share of issues, although they're a lot less serious than those presented in Windows, and I would argue much fewer. Windows has just as many hardware issues, plus the software problems. I've never encountered a kernel panic or dependency Hell.

Then again, I know of Windows users who were never explicitly targeted by malware due to their internet/program practice (the more you pirate, the more likely you are to have a virus). We're all biased. I plan to perform an experiment that compares XP and 7 in different environments. I think it's safe to say there will be very few Vista users, so I won't be testing it.

---

### Post by ShaneR on 2009-11-04
> **MellonCollie said:**
> There is no solution so long as the end-user can install software. You can try to educate the user, but most non-techies don't seem to care.

I meant to say that as well.  Security issues are never going to go away.  If it's broke, someone will exploit it; if it's not broke, they'll find a way to exploit it.

I've always been of the belief (with little to back it up) that if you take any OS exisitng now or in the future, give it as many users as Windows currently has, that OS will have just as many security issues.

Anyway...back to playing with my Ubuntu install :)

---

### Post by Mike'sHardLinux on 2009-11-04
> **murderslastcrow said:**
> **_The Test_**
We were determined to allow these security measures take care of themselves for 30 days without any maintenance whatsoever.


I am really surprised nobody has mentioned this, or maybe I skipped the post: I understand what you are trying to do, and it sounds interesting, BUT, if you do any work with security in the real world, then you should know that your premise of "take care of themselves for 30 days..." completely contradicts "security". One of the biggest problems is people want to believe security is "set-it-and-forget-it", but it is not. Not even in Linux.

---

### Post by murderslastcrow on 2009-11-04
I wonder how exactly you can exploit the need for the user to enter a password to run unauthorized code on anything important. Unless Linux changes its structure, I think we can assume any problems will be addressed as they arise. Realize that Linux has a very large following in the IT market, and this is probably where most malevolent hackers would like to establish themselves.

I don't know, but from what I've studied, it seems that there are marked differences in default Linux security (UNIX in general). But I agree that there would be a lot more motivation to exploit Linux. You would need a lot more sophisticated programmers to code malware for Linux, since it's such a ridiculously hard environment to exploit in the first place. And even then, they need the user's permission to install this stuff.

Unless people are openly installing malware or adding malware repositories to their Linux system, I see very little room for any sort of exploitation.

I suppose it's not impossible. But the way open source works is inherently secure. I just... I'm looking really hard for what could be circumvented. Unless a browser is allowed to run unauthorized code on system files somehow, which is entirely unlikely, and wouldn't be allowed or trustworthy in our community, especially with AppArmor profiles...

Yeah, I'm thinking about it. I'll have to spend more time to see how this could be exploited in the case that there are more users (majority). I don't think we can really say if it will be insecure in such a case, since we've never had any reason to believe otherwise.

---

### Post by Saghaulor on 2009-11-23
> **ShaneR said:**
> Unbelievable. They have no business reporting on security with an approach like that.  They *don't* install an anti-virus and then report they were infected, and blame it on the OS? Please.  That would be like leaving your Ubuntu admin password clearly written on a sticky note, stuck to the side of your monitor, and then blaming the OS when someone sits down and wreaks havoc. 

They obviously need to read my previous post about UAC and get their facts straight.

This is why security in a Windows environment can be challenging: A lack of knowledge even when the proper information is easily available.  You can't blame any OS for a user's ignorance and lack of responsibility.  

Granted, I'll be the first to admit MS has made plenty of security blunders in the past, but,  as I said before, with a little effort and a little knowledge security concerns go away...regardless of the OS in use.

Ubuntu doesn't require an antivirus to remain free from infection, nor should Windows.

Inherent security flaws from the design of the OS are the fault of the OS. A third party antivirus should not be required.

---

### Post by Small_Nuke on 2009-11-23
> **saghaulor said:**
> ubuntu doesn't require an antivirus to remain free from infection, nor should windows.

Inherent security flaws from the design of the os are the fault of the os. A third party antivirus should not be required.

+1

---

### Post by Diluted on 2009-11-23
> **Saghaulor said:**
> Ubuntu doesn't require an antivirus to remain free from infection, nor should Windows.

Inherent security flaws from the design of the OS are the fault of the OS. A third party antivirus should not be required.
Can you honestly say Ubuntu doesn't require antivirus when it hasn't been a target of a virus attack? You can't really say an operating system should be immune from any infection, because malicious code will always be written and users will accidentally or unknowingly execute them.

---

### Post by NoaHall on 2009-11-23
> **Diluted said:**
> Can you honestly say Ubuntu doesn't require antivirus when it hasn't been a target of a virus attack? You can't really say an operating system should be immune from any infection, because malicious code will always be written and users will accidentally or unknowingly execute them.

It has been a target. And it is immune, as long as the user doesn't do something stupid, nothing outside the users /home/ can be damaged.

---

### Post by Diluted on 2009-11-23
> **NoaHall said:**
> It has been a target. And it is immune, as long as the user doesn't do something stupid, nothing outside the users /home/ can be damaged.
So it's immune, but it's dependent on the user? That doesn't sound immune to me. Just because users don't do stupid things doesn't mean they cannot be targeted. If there was a zero-day attack on Firefox, should we blame it on the users?

By the way, isn't /home an important part of the system as well? The operating system can be reinstalled. My documents? Not really.

---

### Post by ShaneR on 2009-11-23
> **Saghaulor said:**
> Ubuntu doesn't require an antivirus to remain free from infection, nor should Windows.

Inherent security flaws from the design of the OS are the fault of the OS. A third party antivirus should not be required.

You are abosolutely right: Windows should not require an anti-virus. But it does and it's not necessarily the fault of the OS.

I see enough security patched to come down the pipe for Linux that I have to believe if someone wanted to attack Linux they could.

> **NoaHall said:**
> It has been a target. And it is immune, as long as the user doesn't do something stupid, nothing outside the users /home/ can be damaged.

Sounds like any other OS to me.

Nothing is immune.

---

### Post by sliketymo on 2009-11-23
> **murderslastcrow said:**
> Quite honestly, since Windows has had this problem for so long, you'd think Microsoft would come up with some sort of useful solution by now. At the least include an antivirus with the system (or would that be against trade laws in the EU?).

Really. Honestly. This is the main detractor to Windows use. If Windows got viruses as little often as Linux, we would be on a much more even playing ground.

But, I think it would take a very creative approach to protect against viruses by still allow compatibility with Windows XP. I mean, surely XP Mode is a bit excessive? (if it works in Wine, why use VirtualBox at all?)

This is just like religious activists. Just because they're the dominant majority doesn't mean they have nothing to prove. An athiest or agnostic is merely a person who doesn't claim to assume the existence of a God (or to assume they need Windows applications). Windows still has to prove to us the divinity of its OS. But I see very little to benefit the average human being in paying for viruses.

Man, I'm a zealot. I just compared Microsoft to Christians (they probably are Christians). Sorry, that's unfair, they just want to make money and have a large mindshare in the global community...

Holy crap! THEY'RE ONE AND THE SAME!!! ILLUMINATI! XD

 Microoift Security Essentials is now,and has been available free from  MS for quite awhile now.The only problem is,you have to actually install it on you machine to get it to work.

---

### Post by madhi19 on 2009-11-23
The main reason Windows is not secure is sitting 20 inches from the screen. You can blame Microsoft for many things and one of them is to have made the PC mainstream over the past twenty years. It not a bad thing per say it just unfortunate that the platform until recently did not put the emphasis on network security from the get go. 

So for years we have a majority of users who never learned about security until after their PC got owned and when these peoples do learn they end up learning the wrong lessons. They learn about Anti-Virus instead of learning about ditching IE6. They learn about software firewall, instead of hardware firewall. They learn about tolerating security crapware that eat up resources forcing them to upgrade their hardware every two years instead of guest accounts, OpenDNS and not installing every crap you come across the net! They learn about paying the "Geek squad" hundreds of dollars to save their files and fix the mess they make but they don't learn about free Linux liveCD!

The UAC is a step in the right direction but Microsoft would be wise to start investing in an awareness program to educate the market. Maybe put a DVD with every copy of Windows 7. Something to explain the few easy steps peoples can take to live in a virus free Internet. In other word they own the damn market it their mess to clean!

---

### Post by Saghaulor on 2009-11-23
> Can you honestly say Ubuntu doesn't require antivirus when it hasn't been a target of a virus attack? You can't really say an operating system should be immune from any infection, because malicious code will always be written and users will accidentally or unknowingly execute them.


Ubuntu can be infected. There is no denying it, however, if you were to compare the operational structure of the two OSes, you would see what I am talking about. In Windows, you're the admin by default, in Ubuntu you are not. That right there is a huge difference. The ability for malicious code to install without question or not.

But it's not just the default privilege paradigm. There are more initiatives like Apparmor that contribute to OS security. To be fair, when we're talking about Linux, we mean a distro, because Linux itself is the kernel.

> So it's immune, but it's dependent on the user? That doesn't sound immune to me. Just because users don't do stupid things doesn't mean they cannot be targeted. If there was a zero-day attack on Firefox, should we blame it on the users?

By the way, isn't /home an important part of the system as well? The operating system can be reinstalled. My documents? Not really.

Even the most fortified system is vulnerable when a human is at the helm. So yes, Linux can be conquered. 

And I'm not naive enough to assume that Linux code is flawless, however, the patch response rate is something to consider. Would you prefer your patches once a month on Tuesday, or say, as soon as they are reviewed and approved?

The way I see it, Microsoft has a very reactionary model (antivirus, antispyware, etc), but they are working towards a preventative model (applocker, firewall). I think Ubuntu is more preventative, but it doesn't hurt to have some reactionary measures.

I think prevention is better than reaction.

---

