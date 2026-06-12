---
title: "Just Curious about security from Nation States ..."
date: 2015-01-24
forum: Ubuntu, Linux and OS Chat
---

### Post by cwmoser on 2015-01-24
Just curious if Software Updates to Ubuntu is free from influence by Nation States.
Remember when America's NSA secretly got Laser Printer manufacturers to imprint
the Printers Serial Number and Model in a yellow dot sequence that could not be
detected by the human eye?  That was indeed a creative "hack" :-)

I just allowed a software update to my Ubuntu this morning and got to thinking
how easy it would be for someone - be it a Nation State or a hacker - to install
a key logger, virus, or other mischievous software.

What Nation States are the most likely to secretly collaborate with Ubuntu updates
like the NSA did with Printer manufacturers?

Just pondering, so, what protections do we have?

---

### Post by Sef on 2015-01-24
> [COLOR=#000000]Just pondering, so, what protections do we have?[/COLOR]

Being Open Source. Malware cannot be hidden when anyone can look at the code.

---

### Post by tgalati4 on 2015-01-24
The printer hack was an attempt to track color printers used for counterfitting currency--this is a valid threat against any nation.  Of course hacking firmware of any hardware (a TV, a cable box,a  thermostat, a microwave) is relatively easy once you get into the details.  

But yes, open source code presumably has some eyes looking through it for code that does not perform its primary operating system function.

Several countries have "branded" versions of Linux for use in their country.  I would be rather suspicious of those distros.

---

### Post by cwmoser on 2015-01-24
Several nations have very talented staffs looking at ways to secretly hack into 
computers.  Personally I would think that Microsoft products could easily be 
compromised since the Source Code and the Updates are not open for viewing.

With Linux, perhaps a 3-rd party piece of software can avoid being detected - what do you think?
How about a rouse update masquerading to look like an official update targeting at a specific person?

Disclaimer:  Not hiding anything, just a curious IT person pondering about all the Cyber Hacks going on.

---

### Post by yancek on 2015-01-24
It is much easier to do that with proprietary code simply because so few people see it.  If a government can coerce or convince a company that writes software to put specific code in it then basically the people who write it or a skilled hacker are the only ones who will know it or detect it.  As stated above, anyone can view open source code and the programmers who write the code for Ubuntu and any other Linux have their own repositories and they check them on a regular basis.  Other programmers not associated with any distribution also do this and if they find something nefarious, they let people know and are complimented on their skill.

Almost all "viruses" and malware are on proprietary code.  Someone who finds malware in proprietary code will often get negative results, be called a hacker or criminal even when all they are doing is pointing out a weakness and not taking advantage of it.  A company in this situation will generally start by denying it exists then when too many skilled people concur with the problem the company will say they were aware of it and are working to resolve it.  Then they will hope people will forget about it.  This has happened countless times in the last few decades.

Far less likely to have any nefarious code on open source than proprietary code.

---

### Post by ian-weisser on 2015-01-24
> **cwmoser said:**
> Just pondering, so, what protections do we have?

For every post here we get about how big-Ubuntu-is-spying-on-us,
we get another about how Ubuntu-is-a-buggy-mess-that-doesn't-work.
I think the two pretty much cancel out. The implanted malware must be hamstrung by the bugs.

What 'influence' does any nation have with Canonical or Ubuntu? Ubuntu sells nothing, operates nothing. Canonical's HQ in London is small; it's customers and workforce are scattered across the world.

There are _many_ protections in Debian and Ubuntu to prevent the nefarious upload of a malware-containing binary, or the inclusion of malware in source code. None of these protections are perfect.

We encourage ordinary (non-developer) people to get involved with the Ubuntu community to help improve the protections, to create better tests, to audit code, to test mirrors, to test binaries for unexpected behaviors (like 'calling home'), etc.

---

### Post by ofnuts on 2015-01-24
To answer some of the posts above: 


[LIST]
[*]National distros have about as much to do about spying on local citizens as they have about preventing a foreign state to spy on the locals.
[*]People can check the source code, but how many check that the delivered binaries are actually from the public source code? In fact the security of OSS mostly applies if you can build your own system from scratch and if you are able to perform decent source code audits. Few people can do all these. Otherwise you have to rely on some big organization (state, or private company such as RedHat or Canocial) which can have its own agenda.
[/LIST]

---

### Post by rcp.paulson@gmail.com on 2015-01-24
When you download your initial binary version of the live disk for burning, at the ubuntu.com site, you should notice the webpage is not https: meaning secured with an SSL encrypted protocall. Why is that? But if you go here: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) this page is ssl secured. If your system of download has a corrupted SSL private/public key that has been transferred to a corrupted router (man in the middle) then you can be spoofed by having the router redirect the download request to some bogus (nsa, china, russa etc) site whereby you download a corrupted backdoor version of ubuntu. (Or, your current system could have a rootkit infected machine that does this explicitly > and could easly make the md5 hash read right too.) 

However,  using [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes), you have a secure webpage where you read the md5 hash (e.g.119cb63b48c9a18f31f417f09655efbdis hash for ubuntu-14.04.1-desktop-amd64.iso ) to compare with the one you get from running the command in terminal:  
md5sum (file name)

then compare this to the https ssl secured webpage. This is essential since the iso download is not secure (is ssl really safe?)

Routers have beeen comprimised all over in huge numbers forming the potential of redirection of webpage requests. It's very hard to detect if your router is corrupted. 
There is no rkhunter to run. Your could even corrupt you https page with the md5 hashes, if it had your private key (an unintended live disk boot exploit could get this and pass it to your corrupt router)..
You could reflash it sometimes with DD-WRT. This is what hackers want for you to be unable to scan/verify it.

If however, you have a clean system with secure ssl private key, all updates to the repository should be 99% secure.
 However, the NSA could have intercepted any disk drive package shipments to ubuntu/canonical and replaced the firmware 
(they can hack the western digital drives dev team too. This has been done, see dasspeigle website.)
Now this firmware can recognise the iso's and when read replace it, or it could just replace the kernal with a rootkit and control everything.

Good luck, this world is a mess.

see:
[https://tails.boum.org/about/index.en.html](https://tails.boum.org/about/index.en.html)

---

### Post by rcp.paulson@gmail.com on 2015-01-24
**Some facts; **
Cur.tech can rewrite hard drive firmware, bios firmware (which you can detect), can redeesign HID (keyboard, USB chips etc), backdoor FSB memory controls, DMA etc to access memory,IO, stored data etc. Wifi is an even larger mess. Off-line machines can be intercepted and modified in-shipment  RF to network ( by court FISA order).

Cur.tech can intercept your hardware mail shipments under Patroit can and replace your hardware in transit if you are a target: infrastructure providers (VPN SSTP etc) 

Patriot act makes it legal and confirmed by FISA court ruling demanded by admin of NSA (protecting them from congress/ jail) and requires them to execute per exec order.

They had a policy of encypting all US citizen data while keeping the meta-data inter-realtionships to allow targeting of individuals (everyone, so asto backtrace) suspected of "terrorism" per Patriot another act re marshall law passed quietly Jan 2002. All eyes outward by NSA were open.

Once rewritten an on-drive controller can replace the MBR, impersonate grub, load a corrupt rootkit kernal, allow ssh, rdp, and still keep virgin code to pass rootkit scans.

Once you have a rootkit, rkhunter can scan OS files by reading the exploited diskdrive and firmware can passback the unpatched code resulting in a good signature hash all the while being totally corrupted internally and 99% out of oversight. In-memory scans can be circumvented as well. Encrypted Flash drives are difficult to inspect by rev-engr. Private keys can be programmed into logic instead of open in flash data making them near impossible to reverse.

A rootkit comprimised kernal can read your SSL private key generated and pass it to your corrupted router which can have all kinds of exploits running 24/7 unobserved.
....(since you left the router's admin passwrds open, plus reflash backdoors, imagine DD-WRT reworked exploits with splash screen identical to your model)
 
When the rootkit wants to hide, it just boots the original code (but can be made active from user procs too)  from the harddrive with the unpatched kernal leaving no trace.

Custom malware program can talk to the harddrive firmware to reestablish rootkit functions or load exploits remotely into hard drive processor (ARM) or as linux apps.

You can trueCrypt the harddrive but won't matter since the kernal loads before the true crypt, so if corrupt, the rootkit always gets your truecrypt key which HDD controller can internally use to crypt/decrypt drive internally.

If you attemt to look at the harddrive with a live CD, the drive knows it did not boot and presents the linux system 100% true.

You cannot SSH into the HD (through sata, onboard jtag or serial debug port) as you don't have the key.

They can put a metal layer over the hd controller flash/rom so you can't reverse engineer the code (flash charge imaging) and they can add SOC custom instructions that you cannot decyhper even if you could read the rom (ARM varient or other SOC toolkit processor).

Power supply monitors have some ability to detect modified controllers but this can be hidden if uncorrupted controllers have constant chip current operations.

The trend toward SSD drives replacing slow IOP  hard drives make spreading exploits easier due to demand.

Hardware corruption makes any distro a target. Any VPN, CA, data centers or security infrastructure is still a target well within the ability to comprimise.

The ability to encapsulate code into hardware gives plausible denability to manufactures and the high compute power of SOC's make development much easier (Mentor SOC tools etc).

Man-in-the-middle are everywhere a router is corrupted--huge worldwide.

We need open source hardware more than software because malware can hide without detection in hardware. Open verilog anyone?
And, if you can corrupt the storehouse of code, be a MITM of network comms local to every private network, open source doesn't stand a chance.

With System C, and other verilog logic generators, C code can be compiled into hardware. Try to reverse engineer that!

The political debate and ramifications, goes far beyond this (out of our scope) --good or bad. This I will not debate.

It is here, like it or not, and _**it's not a secret.**_ 

 (PS I don't believe NSA can crack current long key encryption, definately not real time, not without quantum computer.)

NSA is not alone, who knows what china is/will be shipping in dirt cheap comprimised products (EPS8266 etc) that we wreaklessly deploy?

---

### Post by buzzingrobot on 2015-01-24
I don't believe any government will ever allow use of any technology that allows communications that is impossible for them to intercept. If some technology actually resists interception, then legislatures will either criminalize its use, if enforceable, or mandate severe penalties for its use in the execution of a crime. E.g., make use of encryption in communications planning a crime a felony.  

The general public will support this.

Many people seem overly paranoid and not to recognize the difference between being specifically targeted and being one grain of uninteresting internet sand on a very, very large beach.

---

### Post by bashiergui on 2015-01-24
> What Nation States are the most likely to secretly collaborate with Ubuntu updates
like the NSA did with Printer manufacturers?It's odd that you focused so narrowly on Ubuntu updates. That does not require collaboration with Ubuntu. Plus, it's only one attack point that would require the nation to do MITM and then inject malicious binaries. It's possible but there are too many other attack points that would be much simpler to exploit.> Just pondering, so, what protections do we have?Frankly, nothing. If a nation state wants in your computer they will get in your computer. No advice you find on free forums will protect you from a nation state.

Best thing you can do is encrypt all your traffic wherever possible (ssh, https, email).

---

### Post by rcp.paulson@gmail.com on 2015-01-24
Very well put and goes to the center of the issue that I must  conceed; yet  Stallman or Linus would object on some  principle--tough. This is what is now and their efforts have failed to create free software but  advanced the world greatly by their efforts. This goes to policy which scares the crap  out of me. The majority public is apathetic, uninformed, and goes along with most anything especially if we seem to have the upper hand. Truth is there is no unchanging upper hand and so we need forward looking gaurdians to protect our interest and secure our technology.

Technology is an (uncontrolable?) exponentially growing force,  more powerful each day, not easy to grasp, and information is it's lifeblood. It will be used or misused no matter what so it is up to the defenders. True freedom may be impossible (meaning perfect information privacy) and incompatible with a the disasterous missuse of tech which is unstoppable. So, there is no time for heavyhanded "rightousness" of some ideal. This stuff is serious and GNU and open source needs to get real.

I just say what is. Open source is unlikely to ever stand on open hardware and the whole idea that an imperfect person can build machines that can't be misused by devious design is false.

As an engineer, not laywer, policy maker, I do not attempt to debate policies as to interests of right, wrong, nations, privacy, security, nor even the implications of technologies. Being a hardware and software engineer, I was puzzeled by open source, by encryption labled by gov to be a muntion, especially when I understood that the line between hardware and software was very indeterminate. I watched clever social engineering steal passwords (bitcoins) and I thought to rely on encryption is foolish unless you can do it in your head (or in a armed vault)  as that is the only hardware you can truely control as you must trust it's components. No man is an island in this complex world. 

Everything else depends on trust given that humans need hardware to compute. Most people cannot even put long random keys to memory so how can any of this work for average people? People are misled by claims of data security (maybe a good thing). These are constantly evolving and transformational tools and people make the mistake in thinking progress can be based on hiding information. Hiding is a defense.  We better figure this out soon as a race. True progress is based upon cooperation in positive useful workable directions when I build things but always subject to misuse. It's questionalble whether the world judges tech as progress if they see where it may lead. Automation has the ability to free us from drudgery or enslave us no doubt. But this decision is made by powers that be. 

Stallman's GNU and open initatives seem to have an air of "rightous sentiment", of power to make software open and free and he worked dammed hard at it.  Within people doing the right things, for the right reasons, is where free software should reside as a means to enhance our technology.You cannot make a machine free because you really can't see into it's implementation. People can design bugs that output exploits so you think you have freedom while pooring over open code--good luck. Man is imperfect. Seeing into hardware is even worse since I can tune a circuit to misfire logically and fool you in a controlled way. You have ideal computation and you have imperfect and potentially devious implementations--hard or soft. 

Stallman stands up and says I have the ability to make software free if the people demand it. And others, say I have the power to use technology to enslave or enforce correct behavior as a means of policy because technology has the ability to destroy us all. I do think people are enamoured and afraid of technology, at least the thinking ones. The paranoid point to of standing upon "rights" without knowing what they don't know they don't know is even possible. I hate it.

---

### Post by Tadaen_Sylvermane on 2015-01-24
Well I don't see anyone topping that answer... /thread.

---

