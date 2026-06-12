---
title: "Clean up rootkit / check firmware integrity"
date: 2013-04-01
forum: Security
---

### Post by Vidar30 on 2013-04-01
Hello.

I'm in the unfortunate position of having my laptop hijacked. How do I know? The intruder told me. Initially he powered off my laptop 10-15 times (in a single day), then he injected (subtle) messages in my browser, revealing that he's looking at me through the webcam.

Anyway - format and clean install did nothing. He's still there, so it's storing code in expansion rom (firmware) or BIOS.

I'll attempt the following strategy:

Test integrity of all firmware and BIOS, and reflash those whose been altered. 

I'm fairly technically minded but have no extended computer background. So, my question is: How do I do it? Any useful links for example?

---

### Post by tgalati4 on 2013-04-02
There are tutorials on the web for creating a bootable CD with freedos and the flashing program.  You download the correct ROM and spin a Live CD that boots into freedos.  Run the flashing program and hope that the new ROM loads OK.  Put some tape over your camera.

---

### Post by cariboo on 2013-04-02
I would probably help, if you let use know what version of Ubuntu you are using.

---

### Post by unspawn on 2013-04-02
> **Vidar30 said:**
> (..) he powered off my laptop 10-15 times (in a single day), 
Please note powering off a device abruptly may be caused by a lot of things, none necessary malicious.


> **Vidar30 said:**
> (..) he injected (subtle) messages in my browser 
Can you give a few examples of those "subtle" messages? How were these messages phrased?


> **Vidar30 said:**
> (..) format and clean install did nothing. 
Also note that re-installing an OS from scratch (conveniently) removes all "evidence" (if any), hence it's not the preferred approach.


> **Vidar30 said:**
> He's still there, so it's storing code in expansion rom (firmware) or BIOS.
Define "still there"? What (anomalous) behavior does the machine exhibit?

---

### Post by Soul-Sing on 2013-04-02
Had the 'intruder' fysical access to your computer?

---

### Post by Vidar30 on 2013-04-03
It is a targeted attack. He's not been malicious so far and I don't expect any "violent" behavor. I believe the intruder has personal motive and is financially resourceful. My Android phone is also hijacked btw but never mind that.

Does my strategy overall make sense? Is it secure? Any suggestions? 

I've been reading about these kind of rootkits. Some suggest that you can't get rid of it: That the RK may reside in memory while I'm flashing and copy itself back after I'm done. And - I've been reading about attacks which utilize bugs in intel cpu. For all I know, this could be relevant although I don't think so. Google "cpu bug rootkit kris kaspersky" without quotes.

Should I direct my effort into attempting to identify exactly the nature of the intrusion first? When the RK is active, it must occupy memory space so a memory dump followed by analysis could be helpful. I'm prepared to spend time learning whatever necessary. I want to know what has happened and to be able to safeguard myself in the future, at least being able to detect it without doing network traffic analysis. 

How do I spend my energy wisely?


tgalati4:
Thank you. Tape is applied.

unspawn:
Give it a rest. Think of it like a hypothetical if you're inclined to doubt it. The intruder dumped a joke concerning the poweroffs. They happened on a 2 days old computer, and only on that particular day, never thereafter. I'm not concerned with evidence as he conceal himself. He hasn't communicated explicitly but through contextual signaling revealing intimate knowledge about me. It's called being subtle. A screendump wouldn't ring you any bells you as you'd need intimate knowledge about me to interpret it.

Did you know cosmic radiation theoretically can cause a shutdown on your laptop?

cariboo907:
Ubuntu 12.10 - but by time you read this it will be 13.04. It's a Sony Vaio laptop model SVE14A1S1EB. I've deleted the UEFI partition, using legacy BIOS. 

Soul-Sing:
No physical access. I believe the attack surface to be js.

---

### Post by matt_symes on 2013-04-03
Hi

> **Vidar30 said:**
> Test integrity of all firmware and BIOS, and reflash those whose been altered. 

> **Vidar30 said:**
> No physical access. I believe the attack surface to be js.

Please don't think i'm being rude as you may well have been compromised. However these two statements make no sense.

Kind regards

---

### Post by Vidar30 on 2013-04-03
matt_symes:

Not sure I follow you. 

The first sentence said (in context) that my strategy will be to check whether firmware/bios has been changed by someone and restore any changes back to default. 

Second sentence said intruder never had any physical access to my laptop and I believe he managed to get into my system through javascript (js).

---

### Post by matt_symes on 2013-04-03
Hi

The point that i was trying to make is the BIOS does not run js.

Certainly reflash the BIOS if you think that will help, however your BIOS will not run java script. 

It may be able to read it but i don't think it can write it.

At least not that i have ever seen.

Kind regards

---

### Post by Vidar30 on 2013-04-03
matt_symes:

While I'm the one needing help here, I will of course answer all questions to the best of my ability. Not attempting to be rude, but it'd be more smooth if you just ask instead of producing suggestions about something I doubt you know very much about.

When someone is talking about "attack surface" it mean the point of entry, which most commonly is javascript. You're quite right, you can't flash bios from js - but, if you manage to exploit js to install malware on a target, then in the following move you may use your new found freedom to execute code to reflash bios. I'm not sure if bios can be altered by a user land rootkit, but it may certainly be done from kernel mode. Ask yourself, how would anyone in the first place get access to run code in kernel mode? If it's a remote attack, that point of entry may very well be js. It's more often js than not, I believe.

---

### Post by matt_symes on 2013-04-03
Hi

> Not attempting to be rude, but it'd be more smooth if you just ask  instead of producing suggestions about something I doubt you know very  much about.

Thanks for that. 

I am senior C/C++ software engineer and i have been currently working on the Microblaze and Arm platforms. I have been doing this job for 13 years and i have been into computers since the spectrum 48K and BBC micro.

But anyway, i appreciate your desire to fortify your PC.

So the only thing you really can do is reflash your BIOS' and reinstall the OS. Everything after that is just hardware.

Kind regards

---

### Post by Vidar30 on 2013-04-04
matt_symes:

Yeah, you're right. The tone of my wording wasn't friendly, as it should be. Peace bro.

---

### Post by KaosuX on 2013-04-06
> **Vidar30 said:**
> Hello.


I'm in the unfortunate position of having my laptop hijacked. How do I know? The intruder told me. Initially he powered off my laptop 10-15 times (in a single day), then he injected (subtle) messages in my browser, revealing that he's looking at me through the webcam.


Anyway - format and clean install did nothing. He's still there, so it's storing code in expansion rom (firmware) or BIOS.


I'll attempt the following strategy:


Test integrity of all firmware and BIOS, and reflash those whose been altered. 


I'm fairly technically minded but have no extended computer background. So, my question is: How do I do it? Any useful links for example?


You don't give enough information that allows anyone to actually assist you and there are too many variables which seem to be assumed by the posters involved in this topic. While it is possible that a rootkit can live in a wide array of devices with EPROM chips, it is not very likely and the malware would - in most cases - need to be specifically targeted for your hardware, otherwise it would likely render the device unusable. You usually won't see anything like this outside of an extremely high-profile and targeted attack (Government, Fortune 500, R&D, etc.) and it isn't something that could be spread to the masses. Do you truly believe someone with this level of skill is specifically targeting you? I don't believe so, because if someone were then why would they give their presence away so easily?


Please humor me for a moment and let's look at this case rationally before we jump to any real conclusions. The likely cause of your security breach is likely due to a security vulnerability within a package that you keep installing after reformatting. You never told us any of the following:


A) Are you running any Internet-facing services?
B) Are you using semi-public Internet access (Shared with family/friends, shared with other people in your apartment complex, etc.)?
C) What specific OS are you using? What is the specific version? What version kernel? etc.
D) Does anyone have physical access to your computer that you know of? Does anyone you know ever use a flash drive or similar on your computer? Do you use a flash drive or similar on other computers?
E) Do you keep your OS fully up-to-date right after the installation or do you sometimes wait a little while before getting around to applying them?
F) Do you have any system logs that might be beneficial to the given situation?


The list just keep going. As you can see, you have not even scratched the surface of this possible security breach and you're adding insult to injury when you simply try to find a quick "solution" by removing the same logs and evidence that is likely the key needed to put this puzzle together. 


When you step back for a moment and look at it from this vantage point, it becomes obvious that the issue likely lies within something you're doing on your end (or lack thereof). 


My recommendation to you would be to simply collect all of the information that you can regarding this situation and use that information to find any possible security breach.  A simple way to get started would be to back up all of your logs, save a memory dump of the live system to an external media so you can later run through the system using forensic software to help gather more useful information about a compromised image of the system. Once you have backed up all of the useful information, then you could reformat your drive and reinstall your OS, making sure to fully patch the system before doing anything else. Once this is complete, start recording system logs (remotely if possible, so someone is not able to modify them) and start verifying them against the logs you backed up to find any obvious clues. Secondly, if the attacker does this again, you can check your logs to see what is going on right at that moment and then verify them against the logs you have stored remotely all week, day, whatever. This would give you far more insight to the situation than anything else without much effort.


Keep in mind, reformatting does mean you lose your ability to keep all evidence regarding the breach. Leaving the system as-is and examining it carefully would be your best option if you knew what to kind of look for. However, if you're not real familiar with your system or this type of audit, then my above suggestion would be the "noob-friendly" version of trying to get a bigger picture of what is going on.

---

### Post by Vidar30 on 2013-04-09
KaosuX,

I appreciate your attention and willingness to help. Regarding current malware technology I'm afraid you're a little behind the curve. Regarding BIOS malware not being generic, take for instance a look at the comment at the bottom of <a href="http://security.stackexchange.com/questions/22912/award-bios-security?rq=1">this link</a> by endrazine (Jonathan Brossard, a computer expert). 

Don't blame you, I used also to think that this would never happen with an insignificant person like myself. Now, I'm inclined to believe that hardware based attacks are more common than we are told it is. 

Anyway, here is what I'm certain of, and why.

Premise 1: 
My computer had a rootkit installed. 

Premise 2: 
I did a cold boot, full format and reinstalled OS with clean cd (downloaded and burned from my university network)

Premise 3: 
Rootkit still present after fresh install. 

Conclusion:
It must store a copy of itself in BIOS or expansion ROM. 

I used to have similar thoughts as you do - those things only happen to big shots, with big bucks involved. I'm leaving out some of the story here because I want the discussion to be a technical one. As I mentioned in post #6, I believe the intruder has personal motive and to be financially resourceful.

Two specific questions:

1. My BIOS is reported to the following:

SMBIOS 2.7 present.
[    0.000000] DMI: Sony Corporation SVE14A1S1EB/VAIO, BIOS R0260V4 03/05/2012
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    1.261987] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.787477] ATOM BIOS: THAMES

It's AMI BIOS R0260V4. I can't find this BIOS on the net. Guess I'll have to install Windows and use the Sony utility for updating BIOS. 

Question 1: When I update BIOS, will the whole BIOS be overwritten?

Question 2: 
How can I make a list of all expansion rom's in my system, e.g all the possible storage points for the malware?

---

### Post by mike acker on 2013-04-09
if you google for "malware in bios" you will get a nasty list of reports.  
~~

Yours could be a very nasty fix. 
first off you will need to get a bios reflash .cap and or .rom file for you mother board from the OEM
just re-flashing the bios might not -- and IMHO -- probably will not clear the problem as i suspect the infection in your o/s will simply re-infect the bios. reloading the o/s will have the same problem: the bios will re-infect the o/s

i would start by re-flashing the bios from a USB drive.  Next:  low-level formatting the hard disk from a Ubuntu LIVE CD. this should put the hard drive out of service.  then using the LIVE CD reformat your hard drive and re-install your O/S. you have to low-level format the disk so that it replaces the Master Boot Record -- another place hackers like to install malware. the key is in getting the BIOS re-flashed and then correcting the hard drive without letting it boot up.

the critical question though that I would like to ask is simple: Linux, i would not think -- would allow an application program to update the BIOS .  However a 3d party app that you install might contain a module that gets installed into the root and thus run in kernel mode

this is why we are recommended to use only approved software

what, if any -- 3d party software have you added to your system -- from other than the Ubuntu Software Library ? IMHO it is highly unlikely that JavaScript did this damage. Java -- maybe, but any Java you are running should be running strictly in userland as an application.  someting installed is the most likely culprit.

---

### Post by Stonecold1995 on 2013-04-10
This sounds more like a script kiddie-type attack than a well funded hacker.  No hacker with that level of skill in their right mind would "tell" you that they're able to access your system, they'd lay low and do what they want.

I suspect the method of hijack is simpler than you think.  Such as, getting access via SSH (either through your router, or directly if you're running any kind of server) and messing with things that way.  That would explain why they would be able to maintain access even after re-installing.  It's far more likely at least than a rootkit as you're suspecting (or at least, a BIOS rootkit).

As for saying javascript is the culprit, I highly doubt it.  Javascript is usually sandboxed (which browser are you using?  If you're using Chrome, then I call bullsh*t that the attacker broke out of the sandbox and gained root with mere Javascript), and it would take one hell of an exploit to do.  There are so many other posibilities and variables which you have failed to disclose.  I'm willing to bet that your conclusion that the BIOS was infected is simply incorrect.

Anyways, for my suggestion:
Just do as everyone else has told you, and provide more information.  It is very hard to help without knowing anything about the computer you're using, or the way you're connected.

Also, in responce to your comment about cosmic radiation causing computer shutdowns, that shouldn't even be considered as a posibility.  According to Wikipedia, "computers typically experience about one cosmic-ray-induced error per 256 megabytes of RAM per month".  So the chances that in one day your computer shut down 15 times is very unlikely.  Assuming you have 4 GB of RAM, there is rougly a 53% chance your computer will experience a cosmic-ray-induced error on any given day.  Now, I don't know the specifics, but I'm willing to bet modern CPUs have very advanced mechanisms to make sure that such glitches don't cause significant problems.  So the chances that any glitch will get through is exceedingly low.  Now the chances that it will specifically cause a shutdown rather than simply a kernel panic (or more likely, an unnoticable glitch, like a single pixel on the screen being the wrong color for 1/60th of a second) are even smaller.  So I'm willing to think it's more likely that a monkey will jump through your window with a flamethrower and melt your computer than your computer being knocked out by radiation...

Oh and one other thing.  I *do* think a screencap would be a good idea (just point out where the modified text is.  Is it even modified text?  A pop up?  An image?).  Because if he simply injected text into your browser, that could merely be a sign that he has access to your Wi-Fi.  It's trivial to do such a thing if you have the WEP/WPA password (don't use WEP btw, even an old laptop can brute-force litterally any WEP password in minutes) but that doesn't indicate that he's actually IN the computer itself, only that he can read/modify Wi-Fi information (which is called a man-in-the-middle attack).

Can he modify secure websites (i.e. those that have http**s**:// in the URL)?  If not, that's an even surer sign that he only have access to your Wi-Fi.  Plus the fact that he's managed to hijack your phone (assuming it's using the same Wi-Fi).  That doesn't explain the poweroffs though.

---

### Post by unspawn on 2013-04-11
I'm afraid the problem this person faces is not the type of problem that is induced by or can be solved by the use of (any) computer technology.

---

### Post by matt_symes on 2013-04-11
> **unspawn said:**
> I'm afraid the problem this person faces is not the type of problem that is induced by or can be solved by the use of (any) computer technology.

Agreed. This is not a technological issue.

---

