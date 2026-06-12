---
title: "The ubuntu is 100% safe  promise"
date: 2012-11-02
forum: Security
---

### Post by Soul-Sing on 2012-11-02
Hi, could we, as a loCo, come with this promise for an out-of-the-box desktop system? Because of:
- Ubuntu has SUDO
- Ubuntu has TRUSTED SOFTWARE SOURCES
- Ubuntu has no significant listening services: NO OPEN PORTS
- Malware is written for Windows
- There are no Linux viruses active in "the wild"

I am aware of this excellent guide: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) with his myth and reality way of explaining security. But for an average beginner, it is technical, and deterrent.(imho)
How can we best inform en educate beginners in security related matters?
Is it just a "relax and enjoy", or is there more to say?

regards
S.

---

### Post by ibjsb4 on 2012-11-02
If ubuntu is 100% safe why do we have security updates?

Edit: Nevermind, I just found out why.

[http://www.linuxsecurity.com/](http://www.linuxsecurity.com/)

---

### Post by pkadeel on 2012-11-02
> **Soul-Sing said:**
> Hi, could we, as a loCo, come with this promise for an out-of-the-box desktop system? Because of:
- Ubuntu has SUDO
- Ubuntu has TRUSTED SOFTWARE SOURCES
- Ubuntu has no significant listening services: NO OPEN PORTS
- Malware is written for Windows
- There are no Linux viruses active in "the wild"

I am aware of this excellent guide: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) with his myth and reality way of explaining security. But for an average beginner, it is technical, and deterrent.(imho)
How can we best inform en educate beginners in security related matters?
Is it just a "relax and enjoy", or is there more to say?

regards
S.
Just imagine that you live in a place where no other living being capable to hurt you (the viruses in Wild Wild Web) can be found within a radius of 200 miles. Would or should you consider your self 100% safe. What if you travel 200 miles just to invite a serial killer (a computer killer virus) for a dinner at your home. Should you consider the presence of a gun (an anti virus) in your pocket as a 100% safety measure. ;)

---

### Post by Soul-Sing on 2012-11-02
> **ibjsb4 said:**
> If ubuntu is 100% safe why do we have security updates?

Edit: Nevermind, I just found out why.

[http://www.linuxsecurity.com/](http://www.linuxsecurity.com/)

Thank you I wasn't aware of any security updates, and the linkage you gave.:)

---

### Post by Soul-Sing on 2012-11-02
> **pkadeel said:**
> Just imagine that you live in a place where no other living being capable to hurt you (the viruses in Wild Wild Web) can be found within a radius of 200 miles. Would or should you consider your self 100% safe. What if you travel 200 miles just to invite a serial killer (a computer killer virus) for a dinner at your home. Should you consider the presence of a gun (an anti virus) in your pocket as a 100% safety measure. ;)

Exact the 200 miles? Not 300 miles? Sure?

---

### Post by |{urse on 2012-11-02
Also the laptop models that have acpi fan control 'issues', all that repeated overheating is definitely not safe or good for your cpu/hardware.

Acer 5532 for example.

Other than that, be safe and informed and imho Ubuntu will meet you halfway in most all cases.

---

### Post by Hungry Man on 2012-11-02
There is security in theory and security in practice. Security in practice is a temporary state, it means nothing - you're in a negative state of "not being attacked". Security in theory is a matter of risk analysis and reactions to it, you are secure regardless of your state.

Most users really only care about being secure in practice. The wiki is there for those who want to be secure in theory.

---

### Post by CharlesA on 2012-11-02
> **Hungry Man said:**
> There is security in theory and security in practice. Security in practice is a temporary state, it means nothing - you're in a negative state of "not being attacked". Security in theory is a matter of risk analysis and reactions to it, you are secure regardless of your state.

Most users really only care about being secure in practice. The wiki is there for those who want to be secure in theory.

This ^. That wiki page is still a good one, even if it is a bit "techy."

---

### Post by QIII on 2012-11-02
Your second to last comment is patently untrue.

You can quibble about the last item.  The recent spate of Java exploits, although not technically "viruses", showed that even Linux is not safe and the Java vulnerability allowed targeting of Linux just as easily as Microsoft and Apple.

Guaranteeing 100% safety is, well, misleading and rather foolish.

---

### Post by OpSecShellshock on 2012-11-02
I would feel pretty comfortable saying that the risk of getting malware is considerably lower even without taking any additional steps aside from installing Ubuntu as the OS. Since a lot of people think of a lower malware risk as security, it would probably be good enough for them, and they wouldn't have to know anything more technical than that if they didn't want to.

The risk of everything other than malware is probably about the same as other modern operating systems, but everything other than malware combined is still tiny compared to malware as far as problems an average user is likely to encounter on the web.

So yeah that doesn't have quite as much punch as saying 100% secure, but it's the best I can do.

---

### Post by mike acker on 2012-11-02
> **Soul-Sing said:**
> Hi, could we, as a loCo, come with this promise for an out-of-the-box desktop system? Because of:{snip}

How can we best inform en educate beginners in security related matters?
Is it just a "relax and enjoy", or is there more to say?

regards
S.

I think this is a Most Excellent question and I'd like to help in any way I can.

The First Thing I'd add to what we have now would be to put Firefox under AppArmor -- "out of the box"  It's simple enough to disable the profile in case of trouble.  I noticed that an AppArmor profile for Firefox came with Ubuntu

the profile came disabled.  last night i enabled it and put it in complain mode.  just now, checking, I got one error
```

Reading log entries from /var/log/syslog.
Updating AppArmor profiles in /etc/apparmor.d.

Profile:  /usr/lib/thunderbird/thunderbird.sh
Execute:  /bin/which
Severity: unknown


(I)nherit / (P)rofile / (C)hild / (N)ame / (U)nconfined / (X)ix / (D)eny / Abo(r)t / (F)inish
bill@ACKER4:/etc/apparmor.d$ 

```I didn't know what to do with this flag so I selected "Finish"; perhaps there will be a comment on this ??

A Study of hack attacks clearly shows that for the desk-top/client end-point computer,  browser attacks are #1. E/mail would be #2 but these would include "phishing" attacks which attempt to persuade the user to make a bad move.  This is another topic which requires a study of reputable sources and hopefully PGP Trust Models.

So: My initial contribution is (1) distribute Ubuntu with Firefox and Thunderbird under AppArmor, and (2) Caution every new user: stick to the stuff in the Ubuntu Software Library

I think if we do a little more work on Software Recommendations we can improve that last part.

This is really a very important thread.  It has been 10 days now since I moved my Win7 system to the basement and shifted my daily activity to Ubuntu

So far the 2 programs that I feel I've had to take downgrades on are MusicBee and CDBurnerXP.  I'm using Audacious and K3B

Offering a system that is difficult to hack and has good programs is huge.  And I think we're getting there.  Dell is already offering systems with Ubuntu installed,-- my brother's business selected that option!
~~~~~
Amendment

in protecting the browser we should ask: what are we protecting:  "droppers" -- which attempt to install some kind of RAT into your O/S (Linux won't allow this ) -- or (2) snooping/exfiltrating sensitive data ?  this latter will be a harder question as we must prevent installation of any type of plug-in modification to the browser

---

### Post by Ms. Daisy on 2012-11-02
> **Soul-Sing said:**
> Hi, could we, as a loCo, come with this promise for an out-of-the-box desktop system? Because of:
- Ubuntu has SUDO
- Ubuntu has TRUSTED SOFTWARE SOURCES
- Ubuntu has no significant listening services: NO OPEN PORTS
- Malware is written for Windows
- There are no Linux viruses active in "the wild"

I am aware of this excellent guide: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) with his myth and reality way of explaining security. But for an average beginner, it is technical, and deterrent.(imho)
How can we best inform en educate beginners in security related matters?
Is it just a "relax and enjoy", or is there more to say?

regards
S. OMG ARE YOU SERIOUS?!?!?!? You can't be. This has to be trolling. 

You can't call it 100% secure BECAUSE IT'S NOT!!!!!!!!!!!!!!!!

Proof:
[ATTACH]226608[/ATTACH]
That is a list of 2,423 vulnerabilities associated with Ubuntu. Not all of them can be exploited, but a vast majority of them can. (If I get any push-back on this point, then I'll give you a screen shot of the oodles of canned exploits for Ubuntu available in Metasploit). You need beginner to moderate skills to use more than 50% of those exploits using open source & easily obtained tools.

It is intolerably irresponsible to suggest 100% security to anyone with any operating system.  Aside from the fact that users notoriously fail to install every security patch as soon as they're available, you cannot know when someone will find & exploit a new vulnerability that no one knew about.

The whole purpose of the Basic Security Wiki was precisely to address the question you ask.  What's appropriate security for each individual user can only be determined by that user when they've understood some basic principles. 

There is no short cut to security.
There is no short cut to security.
There is no short cut to security.

---

### Post by Ms. Daisy on 2012-11-02
> **OpSecShellshock said:**
> I would feel pretty comfortable saying that the risk of getting malware is considerably lower even without taking any additional steps aside from installing Ubuntu as the OS. Since a lot of people think of a lower malware risk as security, it would probably be good enough for them, and they wouldn't have to know anything more technical than that if they didn't want to.

The risk of everything other than malware is probably about the same as other modern operating systems, but everything other than malware combined is still tiny compared to malware as far as problems an average user is likely to encounter on the web.

So yeah that doesn't have quite as much punch as saying 100% secure, but it's the best I can do.
Well said. 
Many exploits happen through the browser, which has nothing to do with the operating system. It's an important point, but many many non-technical users won't understand the differentiation. It all gets lumped into one category.

---

### Post by CharlesA on 2012-11-02
> **Ms. Daisy said:**
> 
There is no short cut to security.
There is no short cut to security.
There is no short cut to security.

+1. Security is a process not a product. Even though *nix is supposedly more secure than Windows, most of the stuff I have run into have been targeting the browser, not the OS.

NoScript is awesome to have, as it stops most of these before they can run. AppArmor for confining firefox and the like helps prevent the damage it can do should something malicious be executed.

The only one to be 100% secure is to be disconnected from the internet and buried in a block of cement at the bottom of the ocean (and you still have to worry about those wifi eels...)

---

### Post by Soul-Sing on 2012-11-03
After 6/7 years of giving support on a forum and on IRC, we have never seen a person being "surprised" by malware, or an other severe security issue. I must say, admit even, our focus isn't very much security related matters, although we a rather up-to-date wiki. But we very rarely deal with security related questions.
I also have the impression that most cases here, on this forum: "i am being under attack?" etc, etc, in the most cases are false positives. (rkhunter alarms about rootkits.)
Second, no I am not trolling, as a person I am huge fun of the myth-reality approach of the security wiki. I uses ufw with inbound and outbound rules, apparmor, etc. My personal focus lays very much on security related matters.
This is the core question:

[SIZE="3"]How can we best inform en educate beginners in security related matters?
Is it just a "relax and enjoy", or is there more to say?[/SIZE]

thx

---

### Post by zombifier25 on 2012-11-03
We can't give our users a false sense of security, because it's only a matter of time before Ubuntu gets more attention and, gets exploited. When Microsoft released Windows 98 (or 95), they made a solid statement that Windows 98 can't be breached. I take that you know the rest of the story.

The most important aspect in computer security is the users, and if we make the users think they don't need to secure themselves, then they're doomed. We need to tell the average users to "stay safe, don't do anything shady, etc. etc. and you'll be able to take advantage of Ubuntu's security features".

---

### Post by Soul-Sing on 2012-11-03
> The most important aspect in computer security is the users, and if we make the users think they don't need to secure themselves, then they're doomed

This.

But on the other hand, if "we" give them the tools/security tools, and they don't know how to use them, or how to read the outcome. There is a lot of [COLOR="Red"]f[/COLOR]ear is this subforum. Do read all the items about the outcome of rkhunter, chkrootkit files and warnings. There is also a lot of [COLOR="Red"]d[/COLOR]oubt is this subforums among users, and in recommendations: "plaese format you never know who/or whats in your system". And most of all a lot of [COLOR="Red"]u[/COLOR]ncertainty how to interpret te results of security tools.

Is there a way how to learn users how to interpret results of all this security tools? Do we know how to interpret all the results of security tools presented here by users? What is fear, and what are facts.

thx

---

### Post by mike acker on 2012-11-03
> **Ms. Daisy said:**
> Well said. 
Many exploits happen through the browser, which has nothing to do with the operating system. It's an important point, but many many non-technical users won't understand the differentiation. It all gets lumped into one category.

The browser is probably the #1 attack vector. It is interesting to note that compromising the browser may be sufficient for the attacker's purpose.  He may wish to exfiltrate information from your system particularly banking credentials

The browser should consist of several parts:

[LIST]
[*]the binary executable code
[*]plug-ins
[*]working set data for each current active tab
[/LIST]
the binary code should be obtained from the root library and should be running in "userland" -- thus not real easy to tamper with


the plug-ins though -- the browser picks those up under each user-id. but you don't need SUDO to add a plug-in to your browser... which could mean a rogue script could add one silently


the browser should act somewhat like a vm supervisor executing each open tab as a separate problem program.  if this is done properly it will be difficult for a script running in one tab to exfiltrate data from another tab: each tab should have its own memory protection structure (I think each tab has to run as a separate process in your system to make this happen)


thinking about this it occurred to me the AppArmor profile is probably a good idea.  I have the one written by Jamie Strandboge that came with the system running in complain mode now.  I didn't get any errors from it this morning but I'll run it again after I finish all my morning site visits.
~~~

the #2 attack vector is probably "phishing" : conning the user into installing a bad program

for this latter we all need to further our understanding of PGP Trust Models.  I am not satisfied that the current method -- your browser supplies a list of x.509 certificates -- is adequate or proper.

the missing part is that, at a minimum, I need to generate a PGP Keypair and then sign (e.g.). Verisign's certificate.  once that's done, items signed and counter signed by Verisign will get the green light on my system; anything countersigned by some other CA will list as "untrusted".  which is the right way for this to be done.

---

### Post by OpSecShellshock on 2012-11-03
A big part of the reason that there's so much fear is that risk analysis is boring but someone else taking control of your system without you knowing is scary and exciting.

Tools like chkrootkit and rkhunter are completely useless to anyone who doesn't already know what's supposed to be there in the first place. Tools like tcpdump and wireshark are useless to anyone who doesn't know how to make sense of a packet capture. A user who is afraid something bad has happened on their system won't be reassured by the output of a tool they don't understand.

Also, there seems to be disproportionate fear of things like rootkits and keyloggers, which are bad, sure, and are possible, sure, but are also not necessary for getting at the most valuable (in terms of being able to sell it) data from people. Most data breaches are completely outside the control of the people whose data gets breached. Most malware is installed by people who get paid tiny commissions for every installation, which creates the incentive to target Windows and occasionally OSX. Most exploits and compromises of Linux systems are written, tested, and used by security enthusiasts to demonstrate that it can be done and to find ways to prevent it or create incentives to patch.

Anyway, getting more into the theory stuff. Basically I think it's more constructive to discuss the outcomes users are concerned about rather than the specific mechanisms.

---

### Post by Soul-Sing on 2012-11-03
> Anyway, getting more into the theory stuff. Basically I think it's more constructive to discuss the outcomes users are concerned about rather than the specific mechanisms.

So show the facts (the outcome/logs/etc.) and not only the fears. I was looking into that direction too.
We can easily feed fear, and become very technical about security. But "we" can help analyze outcomes/logs/the facts, etc.

I am into skipping the rkhunter/chkrootkit software on my system. Are you able to read the outcome? Has it ever shows a positive on this security subforum? I have never seen a positive on our forum. The outcome of "rootkithunters" is often that obscure, we can only support the outcome with a:"try google".

---

### Post by Ms. Daisy on 2012-11-03
Sure, Ubuntu boxes have been owned. We've seen evidence of that on this forum. They're usually poorly configured servers though, I haven't personally seen any desktops without services getting owned on this forum.
[QUOTE=OpSecShellshock]Tools like chkrootkit and rkhunter are completely useless to anyone who  doesn't already know what's supposed to be there in the first place.  Tools like tcpdump and wireshark are useless to anyone who doesn't know  how to make sense of a packet capture. A user who is afraid something  bad has happened on their system won't be reassured by the output of a  tool they don't understand.[/QUOTE] +10,000

Again, the whole purpose of the [Basic Security Wiki ]("https://wiki.ubuntu.com/BasicSecurity")was to address these precise points that the OP raised. [1. How can we give the average user a sense of security without getting too technical?]("https://wiki.ubuntu.com/BasicSecurity") [2. How can an average user set up a reasonably secure Ubuntu box?]("http://ubuntuforums.org/showthread.php?t=1871177") [3. Can we introduce slightly more complex ideas to the new user?]("https://wiki.ubuntu.com/BasicSecurity/NoScript") [4. Can we give the average user some guidance in reading logs when they think they've been owned?]("https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned")

The major problem we encountered when creating those documents is that security IS technical. It cannot be distilled into easy-to-digest sound bytes for non-technical users. If we are going to be really, truly honest, the fact is you need to understand a threat before you can say you're properly defending against it. So an uneducated user can never say they're 100% secure. 

For us to say "relax and enjoy" to me says "don't worry about anything, click on anything, don't bother with updates." And that's patently untrue. Unfortunately at this point in time, the user bears some of the responsibility in remaining secure.  Perhaps one day the industry will improve and be able to secure non-technical users in spite of themselves. But for now it just doesn't work that way.

---

### Post by mike acker on 2012-11-03
> **OpSecShellshock said:**
> {snip}Basically I think it's more constructive to discuss the outcomes users are concerned about rather than the specific mechanisms.

I think everyone has a right to be able to compute without a hacker adjusting their activity.

This is going to start with UEFI, which I think is a wonderful idea. I should have bought a UEFI motherboard but I thought those were for Windows only. Looks like starting 12.10 we will be able to use UEFI also.

---

### Post by CharlesA on 2012-11-03
> **Ms. Daisy said:**
> Sure, Ubuntu boxes have been owned. We've seen evidence of that on this forum. They're usually poorly configured servers though, I haven't personally seen any desktops without services getting owned on this forum.

I've seen a few desktop boxes owned due to VNC, but nothing lately.

As for the rest of your post +1. I know we had a lot of help from some security professionals when working on that wiki page and it really shows.

It all goes back to security being a process not a product. ;)

---

### Post by Soul-Sing on 2012-11-03
> I know we had a lot of help from some security professionals when working on that wiki page and it really shows

And I'am very very grateful for their contributions. In content and the way of explaining stuff. Again grateful for that.
And indeed security, getting involved into security, is a proces and not an product. Bodhi, Dangertux and many others, they did guide many members in the possibilities of securing Ubuntu in a great way. But, as I know from my own experience, the learning curve becomes soon very steep. Although there is a difference between being silly and well informed. :)
At that moment in time many members loss the interest in the proces of securing computers, imho. When "security" becomes a never ending, tiresome, ratrace against the "bad" outside world. Tolerance of risk, as said in the security wiki is a true phrase.
But in my experience, at that moment, the makers of great guides, the makers of great howto's, doesn't bring the goodness to many members. Members get tired. (of it)
I would like to thank everyone for the input. Any other input into the discussion is always welcome.
I hope that my input is somewhat understood. The balance between fear and facts for instance. I don´t want security to be in the fear, panic corner, but in the corner of cool and collected thinking, as written in the security wiki.

thx for now

---

### Post by OpSecShellshock on 2012-11-03
> **Soul-Sing said:**
> So show the facts (the outcome/logs/etc.) and not only the fears. I was looking into that direction too.
We can easily feed fear, and become very technical about security. But "we" can help analyze outcomes/logs/the facts, etc.

I am into skipping the rkhunter/chkrootkit software on my system. Are you able to read the outcome? Has it ever shows a positive on this security subforum? I have never seen a positive on our forum. The outcome of "rootkithunters" is often that obscure, we can only support the outcome with a:"try google".

I don't use any rootkit detection, anti-malware, or file integrity monitoring software on my computers. It's too high maintenance. In order to get any use out of them you need to run them once on a system when it's first built to establish a baseline, then again after every intentional system configuration change and software update. Who is realistically going to do that on their home systems? I am a security professional and I think it's tedious and useless.

On this forum I only recall one time that I saw an indication that someone's system was owned that was not a either a server or running VNC or poorly secured SSH, and that was someone who installed a desktop theme they got off a website and happened to contain some extra stuff.

---

### Post by CharlesA on 2012-11-03
> **OpSecShellshock said:**
> I don't use any rootkit detection, anti-malware, or file integrity monitoring software on my computers. It's too high maintenance. In order to get any use out of them you need to run them once on a system when it's first built to establish a baseline, then again after every intentional system configuration change and software update. Who is realistically going to do that on their home systems? I am a security professional and I think it's tedious and useless.

Likewise. I don't even bother running rkhunter or whatever on my home server because I know it is locked down and only accessible remotely from a couple IP addresses, but I still check logs off and on to be sure. :p

> On this forum I only recall one time that I saw an indication that someone's system was owned that was not a either a server or running VNC or poorly secured SSH, and that was someone who installed a desktop theme they got off a website and happened to contain some extra stuff.

Same here. I think the majority of cracked boxes were either poorly security SSH or having a VNC server open to the internet (with no password). The other ones could be considered trojans because something was downloaded and excecuted under the guise of a desktop theme for example (gnomelook or some such thing, a while back).

---

### Post by OpSecShellshock on 2012-11-03
> **Soul-Sing said:**
> And I'am very very grateful for their contributions. In content and the way of explaining stuff. Again grateful for that.
And indeed security, getting involved into security, is a proces and not an product. Bodhi, Dangertux and many others, they did guide many members in the possibilities of securing Ubuntu in a great way. But, as I know from my own experience, the learning curve becomes soon very steep. Although there is a difference between being silly and well informed. :)
At that moment in time many members loss the interest in the proces of securing computers, imho. When "security" becomes a never ending, tiresome, ratrace against the "bad" outside world. Tolerance of risk, as said in the security wiki is a true phrase.
But in my experience, at that moment, the makers of great guides, the makers of great howto's, doesn't bring the goodness to many members. Members get tired. (of it)
I would like to thank everyone for the input. Any other input into the discussion is always welcome.
I hope that my input is somewhat understood. The balance between fear and facts for instance. I don´t want security to be in the fear, panic corner, but in the corner of cool and collected thinking, as written in the security wiki.

thx for now

There's a reason why keeping backups was one of the first things we came up with when working on the security wiki. Being able to do a quick recovery  in the event something bad happens is far easier than trying to head off everything that could possibly go wrong (which will always fail because it's constantly changing).

---

### Post by KaosuX on 2012-11-03
> **Soul-Sing said:**
> Hi, could we, as a loCo, come with this promise for an out-of-the-box desktop system? Because of:
- Ubuntu has SUDO
- Ubuntu has TRUSTED SOFTWARE SOURCES
- Ubuntu has no significant listening services: NO OPEN PORTS
- Malware is written for Windows
- There are no Linux viruses active in "the wild"

I am aware of this excellent guide: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) with his myth and reality way of explaining security. But for an average beginner, it is technical, and deterrent.(imho)
How can we best inform en educate beginners in security related matters?
Is it just a "relax and enjoy", or is there more to say?

regards
S.

A 100% guarantee is not practical, possible or even remotely plausible. Once the developers/maintainers of Ubuntu begin touting off a "you're safe, we promise!" philosophy then that is the first step to their demise. I can appreciate your sentiment, but you just have to understand that it isn't realistic.

To be extremely truthful, Ubuntu is not as secure as you think with a default installation. The default installation is suitable for most real-world desktop machines and you likely won't run into too many issues, but it is not configured around any sort of real security policy, outside of some very basic security principals.

I do understand how easy it is to simply look on the surface of a problem like this and have a feeling of being safe in comparison to other platforms or distributions out there. However, don't fall victim to complacency. Too many people think that if the machine has no Internet-facing services enabled then they are safe, and that is simply not the case. As previously stated by another poster, the recent Java vulnerabilities are a perfect example of this.

Since a large part of my day is reverse engineering user-land applications, components of various operating systems and some pieces of hardware for the sole purpose of finding and patching security vulnerabilities, I tend to see the overwhelming amount of zero-day's (Read as: unpatched vulnerability) that are actively being exploited by all kinds of nefarious people.

Again, while the default Ubuntu installation is fine for most people, it isn't all that secure in nature. I am glad that it follows a few basic security principals that do make average users much safer. However, no operating system or piece of software can ever offer a 100% guarantee when it comes to security.

Your other argument is that even the Wiki is too technical for the average user. Well, sometimes two things just don't mix well together. Security (practical or theoretical) just isn't a topic an average user should delve into without expecting some learning curve on their part. **When knowledge is your greatest weapon, you can't expect to intentionally disarm yourself and still achieve such a high margin of security**.

The bold text is the exact reason why security is a process and not a state that can truly be achieved. Things change almost daily and the only defense you can truly rely on is your knowledge. Even then, your knowledge is not infinite and will always be limited to some degree. Therefore, 100% security is not achievable within the scope of the original poster's argument.

> Ubuntu has SUDO
Sudo has had many security-related problems in the past and should not be seen as a fool-proof measure. Here is a link that illustrates a good amount of security-related issues with Sudo. Most of them in the form of Ubuntu Security Bulletins:

[http://packetstormsecurity.org/search/files/?q=sudo%20exploit](http://packetstormsecurity.org/search/files/?q=sudo%20exploit)

> Ubuntu has TRUSTED SOFTWARE SOURCESAll software repositories fall victim to the same underlying problem: They cannot verify every last bit of code that is eventually submitted and then pushed through these official repositories. Most will operate under a "safe enough" assumption. 

Don't get me wrong, this is fine and acceptable. However, it would not be impossible for a malicious payload to be hidden within a large project.

> Ubuntu has no significant listening services: NO OPEN PORTSThis is not the only attack vector. Also, if an average user felt that they were guaranteed 100% security, they become more likely to start up services themselves instead of being cautious about it.

> Malware is written for WindowsI am sorry, but this is just flat-out misinformation. While it may not be as rampant, and you might not be as vulnerable as you would be on Microsoft Windows, it is still just wrong to think that "malicious software is written for Windows"

> There are no Linux viruses active in "the wild"That depends on your definition of "in the wild". As previously stated, malware is still a threat in the *nix world, it is just a slightly different kind of threat.

When using Microsoft Windows, malware is usually the cause of a breach. When using *nix, malware is usually the product of a breach.

---

### Post by mike acker on 2012-11-03
> **KaosuX said:**
> {snip} Security (practical or theoretical) just isn't a topic an average user should delve into without expecting some learning curve on their part. **When knowledge is your greatest weapon, you can't expect to intentionally disarm yourself and still achieve such a high margin of security**.{snip}

I have been fascinated learning the process of security in Ubuntu/Linux

[ This Report ]("http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/") -- although a little dated really piqued my interest and resulted in my creating my first U-box out of an old Dell the kids had left me,-- and now -- building my own ASUS based system

so that is some background

Today I find it interesting to reflect on the question: what should be "in the box" ?  Security wise.

I'm running the AppArmor profile written by Jamie Strandboge in fail mode now and it seems to be fine.  I wish I knew more about this profile.  The thing that worries me most about a browser is un-authorized updates to the browser plug-ins. On windows every other day we got hit with another bonk-bar of some type. Hopefully the AppArmor means no updating the browser

MSFT has attempted to address this same question in Win8,-- adding UEFI and their updated Windows Defender. and more ASLR, DEP.  ASLR/DEP is no substitute for running re-entrant code on exec only memory though...

nonetheless it's relevant as "what's in the box" seems to be a current question

I like the notes in our sticky re A/V, Firewalls, and AppArmor and am trying to learn to use AppArmor  

UEFI is also very interesting. I'll be looking for more news from the 12.10 release relevant to this.  Hopefully the ASUS motherboards will provide a keyring with Canonical as well as MSFT public keys.

---

### Post by chadk5utc on 2012-11-03
interesting bit of reading on UEFI
[http://www.zdnet.com/blog/open-source/linus-torvalds-on-windows-8-uefi-and-fedora/11187](http://www.zdnet.com/blog/open-source/linus-torvalds-on-windows-8-uefi-and-fedora/11187)
[http://www.zdnet.com/blog/open-source/linux-foundation-proposes-to-use-uefi-to-make-pcs-secure-and-free/9827](http://www.zdnet.com/blog/open-source/linux-foundation-proposes-to-use-uefi-to-make-pcs-secure-and-free/9827)

---

### Post by cariboo on 2012-11-04
> **KaosuX said:**
> Sudo has had many security-related problems in the past and should not be seen as a fool-proof measure. Here is a link that illustrates a good amount of security-related issues with Sudo. Most of them in the form of Ubuntu Security Bulletins:

[http://packetstormsecurity.org/search/files/?q=sudo%20exploit](http://packetstormsecurity.org/search/files/?q=sudo%20exploit)

All software repositories fall victim to the same underlying problem: They cannot verify every last bit of code that is eventually submitted and then pushed through these official repositories. Most will operate under a "safe enough" assumption. 



Just a couple of things you may not know about, the PacketStorm security notices about sudo, leave out half of the information. These notices are are published when a fix is released for the problem. Have a look [here]("http://www.ubuntu.com/usn") for more information.

There are very few people that have direct access to the repositories, for those that don't have direct access, they need a sponsor in order to have the package included in the repositories, one of the sponor's duties is to check the source code, and the packaging, to make sure they fall with the ubuntu packaging guidelines. Have a look [here]("http://askubuntu.com/questions/16446/how-to-get-my-software-into-ubuntu"), as it has most of the info needed in one place.

This isn't to say that any of your information is wrong, but is just to help you gain a little more knowledge about the way Ubuntu works.

---

### Post by whatthefunk on 2012-11-04
If any OS promised 100% safety, there would be people lining up to find exploits in order to sue them for all they're worth.  Not a good idea at all, especially since nothing on earth is 100% safe.

---

### Post by Soul-Sing on 2012-11-04
> **KaosuX said:**
> A 100% guarantee is not practical, possible or even remotely plausible. Once the developers/maintainers of Ubuntu begin touting off a "you're safe, we promise!" philosophy then that is the first step to their demise. I can appreciate your sentiment, but you just have to understand that it isn't realistic.

To be extremely truthful, Ubuntu is not as secure as you think with a default installation. The default installation is suitable for most real-world desktop machines and you likely won't run into too many issues, but it is not configured around any sort of real security policy, outside of some very basic security principals.

I do understand how easy it is to simply look on the surface of a problem like this and have a feeling of being safe in comparison to other platforms or distributions out there. However, don't fall victim to complacency. Too many people think that if the machine has no Internet-facing services enabled then they are safe, and that is simply not the case. As previously stated by another poster, the recent Java vulnerabilities are a perfect example of this.

Since a large part of my day is reverse engineering user-land applications, components of various operating systems and some pieces of hardware for the sole purpose of finding and patching security vulnerabilities, I tend to see the overwhelming amount of zero-day's (Read as: unpatched vulnerability) that are actively being exploited by all kinds of nefarious people.

Again, while the default Ubuntu installation is fine for most people, it isn't all that secure in nature. I am glad that it follows a few basic security principals that do make average users much safer. However, no operating system or piece of software can ever offer a 100% guarantee when it comes to security.

Your other argument is that even the Wiki is too technical for the average user. Well, sometimes two things just don't mix well together. Security (practical or theoretical) just isn't a topic an average user should delve into without expecting some learning curve on their part. **When knowledge is your greatest weapon, you can't expect to intentionally disarm yourself and still achieve such a high margin of security**.

The bold text is the exact reason why security is a process and not a state that can truly be achieved. Things change almost daily and the only defense you can truly rely on is your knowledge. Even then, your knowledge is not infinite and will always be limited to some degree. Therefore, 100% security is not achievable within the scope of the original poster's argument.


Sudo has had many security-related problems in the past and should not be seen as a fool-proof measure. Here is a link that illustrates a good amount of security-related issues with Sudo. Most of them in the form of Ubuntu Security Bulletins:

[http://packetstormsecurity.org/search/files/?q=sudo%20exploit](http://packetstormsecurity.org/search/files/?q=sudo%20exploit)

All software repositories fall victim to the same underlying problem: They cannot verify every last bit of code that is eventually submitted and then pushed through these official repositories. Most will operate under a "safe enough" assumption. 

Don't get me wrong, this is fine and acceptable. However, it would not be impossible for a malicious payload to be hidden within a large project.

This is not the only attack vector. Also, if an average user felt that they were guaranteed 100% security, they become more likely to start up services themselves instead of being cautious about it.

I am sorry, but this is just flat-out misinformation. While it may not be as rampant, and you might not be as vulnerable as you would be on Microsoft Windows, it is still just wrong to think that "malicious software is written for Windows"

That depends on your definition of "in the wild". As previously stated, malware is still a threat in the *nix world, it is just a slightly different kind of threat.

When using Microsoft Windows, malware is usually the cause of a breach. When using *nix, malware is usually the product of a breach.

Thank you for your explanation and time to elaborate the points given in my first post.

- Ubuntu is known for its fast security updates. Also security isue's related to SUDO. But thats makes SUDO as an important security instrument not worthless imho. Nor extremely vulnerable.

- Imo the trusted software sources are not very vulnerable. Its rather academic that they are a security issue, although it is possible. Imo the software sources are the most important security instrument Ubuntu has. But it isalso the achilles heel of Ubuntu, people installing software from untrusted sources. The first important security factor is therefore the user.

- No open ports promise. Or the "zero open ports" story.
Personal I rate this proposition as somewhat "poor". 
Also the " no significant listening services " story. What
is significant, and what is not significant? (local ports?) A listening service is a listening service.

[SIZE="3"]Question. What can we promise our members, beginners? Could you elaborate this? What is myth and what is real(ity) Have we nothing in our hands to promise to our members?[/SIZE]

---

### Post by mike acker on 2012-11-04
> **chadk5utc said:**
> interesting bit of reading on UEFI
[http://www.zdnet.com/blog/open-source/linus-torvalds-on-windows-8-uefi-and-fedora/11187](http://www.zdnet.com/blog/open-source/linus-torvalds-on-windows-8-uefi-and-fedora/11187)
[http://www.zdnet.com/blog/open-source/linux-foundation-proposes-to-use-uefi-to-make-pcs-secure-and-free/9827](http://www.zdnet.com/blog/open-source/linux-foundation-proposes-to-use-uefi-to-make-pcs-secure-and-free/9827)

"Platform Key":confused:
this smacks of MSFT locking IE as the Windows Internet Browser. The court told them to shape up and the same thing needs here:

GnuPG(PGP) provides a KEYRING --not a "Platform Key" and you can have bunches of keys on the Keyring.

In terms of UEFI we would need keys for MSFT, Red Hat, Canonical ... so the board would boot with whatever you like to use

as you know when you receive a GnuPG signed message the system will find the Public Key that is needed to verify the message

same thing applies here

once again we have people who should know better trying to pull the wool over our eyes because they think we don't understand GnuPG(PGP).

It does leave us with needing to understand the PGP Trust Model though.  But this is not hard: you generate your own key and you verify the fingerprint on the other keys you want to trust -- and then sign those keys. after that you will get a VALID,TRUSTED,GOOD signature on your message

but we all know these things; I'm preachn' to the choir (again). but it looks like we have to beat these UEFI clowns with a broke down Mac until they put this right.

right now it looks like they are simply using UEFI to lock out their competition instead of to provide computer security

---

### Post by mike acker on 2012-11-04
> **Soul-Sing said:**
> {snip}

- Imo the trusted software sources are not very vulnerable. Its rather academic that they are a security issue, although it is possible. Imo the software sources are the most important security instrument Ubuntu has. But it isalso the achilles heel of Ubuntu, people installing software from untrusted sources. The first important security factor is therefore the user.[SIZE=3]{snip}[/SIZE]

installed apps have become a favorite vector for malware, particularly on the android/smartphones. but malware has been discovered even in the "firmware" integrated into devices. hackers will study with great diigence the question: what must i do to get credentialed?

IMHO this is why UEFI may be the most important development in security so far in the 21st Century: Bruce Scheneier has reminded us that security consists of detection and response as well as prevention.

UEFI could be the Key to Detection and Response as the Fundamental Concept new with UEFI is that software has to pass the signature test before we load it into memory

If you think about this you will see this has the possibility of providing a Continuous Software Audit, starting at POST,-- and continuing through normal operation.

I only just built my first U-box so I think I'll just run this one and continue learning about AppArmor at least through the end of the year

---

### Post by KaosuX on 2012-11-04
> **cariboo907 said:**
> Just a couple of things you may not know about, the PacketStorm security notices about sudo, leave out half of the information. These notices are are published when a fix is released for the problem. Have a look [here]("http://www.ubuntu.com/usn") for more information.

There are very few people that have direct access to the repositories, for those that don't have direct access, they need a sponsor in order to have the package included in the repositories, one of the sponor's duties is to check the source code, and the packaging, to make sure they fall with the ubuntu packaging guidelines. Have a look [here]("http://askubuntu.com/questions/16446/how-to-get-my-software-into-ubuntu"), as it has most of the info needed in one place.

This isn't to say that any of your information is wrong, but is just to help you gain a little more knowledge about the way Ubuntu works.

I won't dispute your first point. I was not linking to those bulletins as active security issues, because I was afraid that might go against the forum guidelines. It was just the first hit on Google to illustrate that SUDO does have a **history** of some security-related issues. It was not to say that it has a poor security track, etc. I am just pointing out that some people put way too much faith in it, and it is not immune to security vulnerabilities.

I am familiar with Ubuntu's packaging policies. It is true that the code should be reviewed before being pushed into the repository. I am not trying to play some overly paranoid hand by saying it is insecure in nature. I am just, again, pointing out that it is **possible** that a malicious payload could sneak in. Especially when you take large projects into consideration. It becomes harder and harder to accurately review larger bodies of code, because it is so easy to hide a malicious payload with clever programming techniques.

I do appreciate the information you have provided. I just wanted to clarify my points to make sure they were not taken out of context, as I believe they were.

[QUOTE=Soul-Sing]
[SIZE=3]Question. What can we promise our members, beginners?  Could you elaborate this? What is myth and what is real(ity) Have we  nothing in our hands to promise to our members?[/SIZE][/QUOTE]

The only responsible thing a beginner could be promised is that Ubuntu will use a sane default installation configuration, and do its best to enhance these defaults where possible to provide the end-user with an overall better experience. However, other than this, there is very little that is guaranteed. Well, except for death and taxes, of course.

---

### Post by whatthefunk on 2012-11-04
> **Soul-Sing said:**
> [SIZE="3"]Question. What can we promise our members, beginners? Could you elaborate this? What is myth and what is real(ity) Have we nothing in our hands to promise to our members?[/SIZE]

Nothing.  Ubuntu cant even promise that it will run because it doesnt run on every bit of hardware out there.  It runs on most, but it doesnt do well with some.  I suppose Canonical could make some sort of promise with hundreds of little asterisks in it and pages upon pages of legal jargon to protect themselves, but this would be pointless.  What do we need a promise for anyways?

---

### Post by CharlesA on 2012-11-04
> **whatthefunk said:**
> Nothing.  Ubuntu cant even promise that it will run because it doesnt run on every bit of hardware out there.  It runs on most, but it doesnt do well with some.  I suppose Canonical could make some sort of promise with hundreds of little asterisks in it and pages upon pages of legal jargon to protect themselves, but this would be pointless.  What do we need a promise for anyways?
This x 9000.

---

### Post by Ms. Daisy on 2012-11-04
> **whatthefunk said:**
> Nothing.  Ubuntu cant even promise that it will run because it doesnt run on every bit of hardware out there.  It runs on most, but it doesnt do well with some.  I suppose Canonical could make some sort of promise with hundreds of little asterisks in it and pages upon pages of legal jargon to protect themselves, but this would be pointless.  What do we need a promise for anyways? Whatthefunk speaks the truth.

---

### Post by Soul-Sing on 2012-11-05
> **whatthefunk said:**
> Nothing.  Ubuntu cant even promise that it will run because it doesnt run on every bit of hardware out there.  It runs on most, but it doesnt do well with some.  I suppose Canonical could make some sort of promise with hundreds of little asterisks in it and pages upon pages of legal jargon to protect themselves, but this would be pointless.  What do we need a promise for anyways?

Because people are sick and tired of The Other Op System? Sick and tired of viruses,security leaks,slow computers etc, etc.? So we have nothing in our hands to promise. From the Ubuntu website:

> You can surf in safety with Ubuntu &#8212; confident that your files and data will stay protected. A built-in firewall and virus protection are available. And if a potential threat appears, we provide automatic updates which you can install in a single click. You get added security with AppArmor, which protects your important applications so attackers can&#8217;t access your system. And thanks to Firefox and gnome-keyring, Ubuntu helps you keep your private information private. So whether it&#8217;s accessing your bank account or sharing sensitive data with friends or colleagues, you&#8217;ll have peace of mind when you need it the most.

---

### Post by rookcifer on 2012-11-05
> **KaosuX said:**
> I am familiar with Ubuntu's packaging policies. It is true that the code should be reviewed before being pushed into the repository. I am not trying to play some overly paranoid hand by saying it is insecure in nature. I am just, again, pointing out that it is **possible** that a malicious payload could sneak in. Especially when you take large projects into consideration. It becomes harder and harder to accurately review larger bodies of code, because it is so easy to hide a malicious payload with clever programming techniques.

That could happen upstream.  Who's to say that Linus Torvalds hasn't turned evil and started backdooring the kernel code?  Who's to say the Apache developers haven't slipped in some malicious payload in their software?  You see where I am going.  If a malicious actor can subvert the code upstream, there is no reason to try and get past Ubuntu's repository security.

My point is, you have to trust someone unless you wrote (or audited) every LOC yourself.  This goes for Windows, OSX, Linux and every other OS in human history.

---

### Post by whatthefunk on 2012-11-05
> **Soul-Sing said:**
> Because people are sick and tired of The Other Op System? Sick and tired of viruses,security leaks,slow computers etc, etc.? So we have nothing in our hands to promise. From the Ubuntu website:

Yes, but they cant promise anything.  Ubuntu is not 100% immune to malware.  It is not 100% immune to viruses.  It can be hacked.  Stupid user habits can lead to thousands of security problems.  If you were in charge of Ubuntu, would you promise that your system was 100% safe when it isnt?  That only thing that can be 100% guaranteed is that if Ubuntu made some sort of promise like this, they would end up in a lawsuit.

---

### Post by Soul-Sing on 2012-11-05
> Stupid user habits can lead to thousands of security problems. 

Indeed, but what would that mean for Ubuntu as a product in a lawsuit?

> You can surf in safety with Ubuntu &#8212; confident that your files and data will stay protected. A built-in firewall and virus protection are available. And if a potential threat appears, we provide automatic updates which you can install in a single click. You get added security with AppArmor, which protects your important applications so attackers can&#8217;t access your system. And thanks to Firefox and gnome-keyring, Ubuntu helps you keep your private information private. So whether it&#8217;s accessing your bank account or sharing sensitive data with friends or colleagues, you&#8217;ll have peace of mind when you need it the most.

So if we analyze this quote:
- surf in safety in Ubuntu is a myth
- files and data safely protected is a myth, although we have the tools for encryption
- we have virus protection is a myth
- we have firewall protection is not true, we have the tools available for great firewall protection
- apparmor is an extra level of protection, but never will guarantee your safe
- access your bankaccount is at your own risk

---

### Post by whatthefunk on 2012-11-05
> **Soul-Sing said:**
> Indeed, but what would that mean for Ubuntu as a product in a lawsuit?

It means that their product is not 100% safe as guaranteed.  It means that Ubuntu broke its promise and could be sued.  If somebody in America can sue McDonalds for serving hot coffee, then they can certainly find someway to sue Ubuntu for failing to fullfill its 100% safe promise.

---

### Post by mike acker on 2012-11-05
the coach doesn't tell the team "we can't beat these guys" and it is also wrong to say "hackers cannot be beaten"

while we may not be able to stop hacking completely we should be able to control it on a practical level

what does it mean to "control hacking on a practical level"? It means this: we make hacking hard enough to take the profit out of it. at that point the hackers are beaten. not stopped, they just give up.

we already know it is important to prevent ad hoc software installs. and i think there has been real progress along that line.

the next big issue will be preventing the injection of malware into the software assembly process.  For example: I have MSFT C++ assembly package. When I compile a program I know what I have in *my* code. But what about all the stuff that thing links in when I do the Compile and Link thing ( which combines my module with a bunch of stuff from the library and produces a finished executable ) .

The answer of course is that this is a ZERO DEFECTS problem: each step in the process is responsible for defect checking.  In my case all I can do is make sure that the signatures check on my compiler and library *

signatures check?

yep. one of the things that is of critical importance is that everyone learn about digital signatures and trust models.  Phil Zimmerman's original essay is the place to start but we need to get this incorporated into our Computer Science Curricula
~~~~
*Amendment
Another new topic involves Detection and Response. I think an advanced version of UEFI could help; I have discussion of that idea on the thread with UEFI in the title.  While the Compiler and Library may have been "OK" when I installed them have they been compromised somehow since ? extending the concept of UEFI we might check the signature on every module as it is loaded into memory.  Or we might settle for a Periodic Audit.

---

### Post by Soul-Sing on 2012-11-05
Amendment
> Another new topic involves Detection and Response. I think an advanced version of UEFI could help; I have discussin of that idea on the thread with UEFI in the title.

I have seen that, And reading it. thx.

> while we may not be able to stop hacking completely we should be able to control it on a practical level
indeed theory and practise are in a way two worlds

---

### Post by mike acker on 2012-11-05
> **whatthefunk said:**
> It means that their product is not 100% safe as guaranteed.  It means that Ubuntu broke its promise and could be sued.  If somebody in America can sue McDonalds for serving hot coffee, then they can certainly find someway to sue Ubuntu for failing to fullfill its 100% safe promise.

if i recall correctly software has been exempt from product liability law since this whole computer thing started

I did a quick check on this: evidently software is considered a service not a "good" under the law

amendment

looks like most of us agree to a disclaimer when we accept software

---

### Post by mike acker on 2012-11-05
> **Soul-Sing said:**
> 
> while we may not be able to stop hacking completely we should be able to control it on a practical level
indeed theory and practise are in a way two worlds

it is critical to recognize this essential fact!

just like the Coach on Friday Night before the Big Game: "Let's get 'em boys!! "

---

### Post by whatthefunk on 2012-11-05
> **mike acker said:**
> if i recall correctly software has been exempt from product liability law since this whole computer thing started

I did a quick check on this: evidently software is considered a service not a "good" under the law

amendment

looks like most of us agree to a disclaimer when we accept software

If I remember correctly, when you install Ubuntu you at some point get a screen with a disclaimer saying that Canonical is not liable.  Cant remember at what point I saw this though.  Anyway, certainly cant have that and have a promise at the same time.

---

### Post by tlu on 2012-11-05
> **KaosuX said:**
> 

All software repositories fall victim to the same underlying problem: They cannot verify every last bit of code that is eventually submitted and then pushed through these official repositories. Most will operate under a "safe enough" assumption. 

Don't get me wrong, this is fine and acceptable. However, it would not be impossible for a malicious payload to be hidden within a large project.

Yes, it's true that there is no 100% guarantee. However, new/modified packages not only go to Ubuntu - they also go to the other distros. Thus, a lot of people will check new code, and I assume that at least the big distros like Red Hat and SuSe (with a large number of paying corporate customers) are doing this very carefully (and probably also by applying automated tests). Consequently, the probability that malicious/insecure code will be detected should be very high. But again, nothing is perfect ;)

A general remark: More relevant than Ubuntu getting hacked are internet related threats like XSS, Clickjacking or CSRF which are not related to the OS you're using. But you can protect yourself by using, e.g., Noscript in Firefox, and Chrome also has some protection against XSS (via its XSS Auditor) and Clickjacking.

---

### Post by tlu on 2012-11-05
> **Soul-Sing said:**
> 
So if we analyze this quote:
- surf in safety in Ubuntu is a myth
- files and data safely protected is a myth, although we have the tools for encryption
- we have virus protection is a myth
- we have firewall protection is not true, we have the tools available for great firewall protection
- apparmor is an extra level of protection, but never will guarantee your safe
- access your bankaccount is at your own risk

That sounds a bit apodictic ;) I mean: There is no 100% security. Nowhere! Nobody can guarantee that a meteorite won't beat you to death some day. 

But you can say that Ubuntu is *reasonably* secure as far as one can tell. [This]("https://wiki.ubuntu.com/Security/Features") site shows that they have done a lot in the past to protect you. And you can be sure that new security features/countermeasures will be introduced: AppArmor will get [new features]("http://wiki.apparmor.net/index.php/AppArmor_versions#Versions_of_AppArmor_under_Development"), seccomp2 will certainly play a bigger role and possibly also [PIE]("https://wiki.ubuntu.com/Security/Features#Built_as_PIE"). Just to name some examples.

---

### Post by Soul-Sing on 2012-11-05
> There is no 100% security. Nowhere! Nobody can guarantee that a meteorite won't beat you to death some day. 

But sometimes many meteorites are shown in path of Mother Earth Ubuntu. Very technical possibilities and frightning, Hollywoodlike scenerio's. Brrr. Indeed there's no 100% guarantee of security, but the text on Ubuntu's website comes very near to it in imho.
My [COLOR="Red"]what__are__real__facts__and__fear(s), theory and practice[/COLOR] approach leeds to nothing really. I am starting to repeat myself. Soi.
Enjoy Ubuntu :)

---

### Post by |{urse on 2012-11-05
Well, it's neither '100% safe' nor '100% secure'. That's incredibly misleading. How about 'safer and more secure than windows, so long as you're not an idiot, promise.'?

---

### Post by Hungry Man on 2012-11-05
> **rookcifer said:**
> That could happen upstream.  Who's to say that Linus Torvalds hasn't turned evil and started backdooring the kernel code?  Who's to say the Apache developers haven't slipped in some malicious payload in their software?  You see where I am going.  If a malicious actor can subvert the code upstream, there is no reason to try and get past Ubuntu's repository security.

My point is, you have to trust someone unless you wrote (or audited) every LOC yourself.  This goes for Windows, OSX, Linux and every other OS in human history.
You also have to verify the compiler you use to compile the code hasn't been tampered with. See: trusting trust.

There's a point where you have to throw it all out and just write your own OS - either that or you accept you can never always know.

Is Ubuntu secure? To an extent - it's still incredibly prone to use error, it's still behind in terms of shipping PIE +s binaries, and the Linux kernel is slacking in terms of security due to Linus not giving a **** and upstream generally having no concept of security. As with every desktop OS (except OS possibly) it provides very little security to third party code unless that code opts into the security built in.

Windows suffers from a lot of those issues as well - instead of having people like Linus holding the kernel back we have a series of developers who act behind closed doors.

tl;dr it is not even slightly fair to call Ubuntu 100%, you can barely call it "secure" unless you add quite a few words like "secure from most malware in the wild". Security with qualifiers just... seems lame.

---

### Post by Ms. Daisy on 2012-11-05
> **Soul-Sing said:**
> My [COLOR=Red]what__are__real__facts__and__fear(s), theory and practice[/COLOR] approach leeds to nothing really. I am starting to repeat myself. Soi.
Enjoy Ubuntu :)
What's fact vs. fud, what's theory vs. practice... it all totally depends on what you are going to do with your computer & your network. There are **so **many variants. If you keep your software up-to-date all the time and you only visit your personal banking websites from your home ethernet on a network you control, then the real risks to you are miniscule.

If you're a bit slow to install all the updates, if you're a bit lazy about what you click on, if you use public wifi for all sorts of personal accounts, then your risk goes up. How much? It depends.

If you never update, download/torrent illegal media, run several services with bad configurations, then it's not if you'll get owned, it's when.

How can anyone possibly answer your question when the reality is just a continuum of risk totally depended on each individual user?  It's frustrating that we can't write a one-paragraph "how to stay 100% secure" document.  I wish we could and have it not be a useless collection of words.

---

### Post by CharlesA on 2012-11-05
Basically, all security boils down to is finding the  "acceptable amount of risk" for the situation, task and scenario.

For example, for a home user, using a strong password and not allowing VNC or the like open access to the internet might be as much security as they need in order to not get their box owned. While those things help prevent brute force attacks, the machine could still get owned if the browser if the user is careless on what they click and isn't running either AppArmor or something like NoScript.

For a production server, however, the accessible amount of risk could be near zero - lock down any services that need access to the internet, ensure no non essential services are running or installed (more packages installed = no change of stuff needing security updates). Thirdly, would be separation of services because it isn't if you are going to get owned, it is ***when*** and when that happens, you do not want your web server, database, and email server compromised all at once. Run a separate box for the web server, one for the database and one for the email server, with different logins and whatnot.

tl,dr: Nothing is 100% secure and "accessible risk" varies depending on the environment/situation.

---

### Post by tubbygweilo on 2012-11-06
You can I expect lock down the code side of things save some zero day exploits but with a bit of social engineering you can crack the user and have them open their system and allow a bad guy to do things. If you can convince the user to give you sudo access then it could well be game over with Ubuntu code still intact.

Ubuntu can be 100% safe but the user not.

---

### Post by OpSecShellshock on 2012-11-06
Yeah I think if you want to talk about Ubuntu regarding how it fits in to most home users' security concerns, you're going to ultimately arrive at the conclusion that the operating system doesn't actually have much to do with those concerns.

For example, if people are worried about their credit card and banking details being exposed, they should understand that compromising the computer, particularly at the OS level, is not a requirement. The one time it happened to me it was because I went out to eat at the wrong place on the wrong night. I had some really spectacular firewall rules, but they didn't do me much good, because I wasn't at home and I wasn't on my computer.

I guess my main point is that for the risk categories that home users tend to be most worried about, the OS has little to do with it.

---

### Post by Soul-Sing on 2012-11-06
> If you never update, download/torrent illegal media, run several services with bad configurations, then it's not if you'll get owned, it's when.

Indeed, and be aware of some vulnerable software as Java also. Java is notoriously late/slow with patches. And seems to be intrinsic unsafe. The alertness not to install software (java?) you do not need.
About services. By default I reduce as many services as possible. And [COLOR="Red"]possible[/COLOR] vulnerable "features" as dnsmasq, avahi, etc.

> I guess my main point is that for the risk categories that home users tend to be most worried about, the OS has little to do with it.
Point taken.

---

### Post by Ms. Daisy on 2012-11-06
> **OpSecShellshock said:**
> I guess my main point is that for the risk categories that home users tend to be most worried about, the OS has little to do with it.
There it is Soul-Sing. That's about as distilled as it can get.

---

### Post by zombifier25 on 2012-11-06
Agree. The single most successful method of infiltration does not rely on security holes, but on asking very nicely: [Social engineering](https://en.wikipedia.org/wiki/Social_engineering_%28security%29).

I'm sure most of us are familiar with [the story of a Wired writer who had his ENTIRE digital life destroyed (e.g., his Google account hacked, all of his Apple devices remotely wiped, his Twiter account defaced, etc etc) thanks to social engineering](http://www.wired.com/gadgetlab/2012/08/apple-amazon-mat-honan-hacking/all/), but in case you aren't, then you should read it, because holy crap.

---

### Post by Merisi on 2012-12-08
I found this thread when searching about security and read it entirely and I must say even though it may seem negligent, I think it's great for someone to have said what the OP has said.  In the year or so since I joined this forum I have noticed an air of anxiety arising that Linux isn't secure and although we can try our best that really it isn't good enough if someone really wants to hack, infect etc your computer.

I appreciate that having a false sense of Linux security isn't helpful and acting like you'll be fine to use torrents and use dodgy websites (like certain Mac users I know...) is going to get you into trouble.  I think maybe that we've gone too far into that direction and that we're probably going to be ok as long as we update regulalry use the right web browser add ons.  I think for new users being overwhelmed with creating your own AppArmor profiles can be off putting.  I tried learning about it and I couldn't make sense of it and I've opted to trust the profile that comes with 12.04 to harden FireFox.  I also think it can put people off if they think there is a huge lack of security when relatively there isn't and that Windows users hearing this will feel more comfortable with their AV or tools such as Sandboxie and EMET.

While an education in a good security mindset is important I think to an extent Linux should just be enjoyed.  If someone is going to get through my computer despite what I've done then really there's nothing I can do about it and I'm not sure if endlessly worrying about will be helpful.  I guess like most users I just have to trust other people to find a solution and hope for the best.

---

### Post by offgridguy on 2012-12-08
Interesting thread.

---

