---
title: "Dumb question of the day:  Why is Linux more stable/secure than Windows?"
date: 2007-05-19
forum: The Cafe
---

### Post by diablo75 on 2007-05-19
I'm writing an FAQ about Ubuntu that will be targeted towards Windows users, and I want to have a easy to understand, not-so-technical description of why Linux does not need things like a virus scanner or firewall software (although I know you can use both kinds on Ubuntu if you'd like).  I have a tech support website of my own that I use for business promotional purposes, and I'd like to start going to peoples houses to install Ubuntu on their PC's so they can move away from Microsoft.

Any input would be greatly appreciated.  Thanks!

---

### Post by tompickles on 2007-05-19
I think the main reason would be the open source philosophy. any one can view whats written down in the code, so therefore noone can hide junk inside it, whereas Windows is all closed source so its all behind closed doors.

annother reason could be the 'limited' audience a potential intruder would have. windows is so popular across the globe that more damage can be done by one windows based virus!

---

### Post by starcraft.man on 2007-05-19
Ummmm, I guess it is a combination of things. First off I don't think Ubuntu is invulnerable from exploits/viruses. I mean otherwise we wouldn't get security updates. That said, every Ubuntu install does have a firewall active by default, it is configured via the iptables and nothing is let in by default. That is a very good means of keeping everything unwanted out of the OS. 

There is however a reason why it is much more difficult to make a virus for Linux/Ubuntu, because by default the user is never logged in with administrator powers, thus he cannot modify anything important. Any attempt to modify a system or process that is important must be verified by the administrator password, and when the prompt is brought up everything else is prevented from continuing.

A very good [explanation]("http://www.psychocats.net/ubuntu/security") is here by Aysiu :). 

Hope that all helps, I just gave a quick sum up. There is also a significant factor I suppose that most malware authors wish to target a large audience and thus pick windows, not to mention I guess they code for what they know and maybe they all like windows?

It's lots of things, Ubuntu is more secure (you can't turn off the UAC for instance, at least not as easily as in Vista in the control panel).

Hope that helps, off to other threads to help :D.

Edit: tom, while you are right that nothing can really be hidden in open source, there are still exploits and bugs that may not always be seen first second or even third time through... thus it is no guarantee against exploits.

Double Edit: HAX! Someone moved me while I was midposting... sneaky mods :p.

---

### Post by tompickles on 2007-05-19
no, true, but generally, nasty things like virus etc go against the open source ideals. what i meant was rather than holes and bugs which could be exploited are found and fixed, but rather that holes and exploits were purpusly put into software is harder due to the openess

---

### Post by starcraft.man on 2007-05-19
> **tompickles said:**
> no, true, but generally, nasty things like virus etc go against the open source ideals. what i meant was rather than holes and bugs which could be exploited are found and fixed, but rather that holes and exploits were purpusly put into software is harder due to the openess

I would agree with you there and add. One of the most promising things I have seen with Open source is the turn around time for patches to exploits and bugs. MS for instance spent almost 6 months or more fixing the ANSI exploit (to prevent incompatibility and such), and apple has been known to take a somewhat shorter but still long time to fix its problems. Ubuntu however seems to me to have the fastest turn around for patches I've seen, it could just be perception but I believe it.

---

### Post by diablo75 on 2007-05-20
I think another factor would likely be the fact that Microsoft is a monopoly that makes a lot of money to sell their crap software.  There are likely a lot of programmers out there who would love to give Microsoft a hard time, not just because they're greedy, but because their poor quality software is almost asking to be insulted by an embarrassing exploit from time to time.

---

### Post by starcraft.man on 2007-05-20
> **diablo75 said:**
> I think another factor would likely be the fact that Microsoft is a monopoly that makes a lot of money to sell their crap software.  There are likely a lot of programmers out there who would love to give Microsoft a hard time, not just because they're greedy, but because their poor quality software is almost asking to be insulted by an embarrassing exploit from time to time.

lol, well I don't know of anything that can vouch for that unless you actually went out and surveyed the malware authors, or psychicly know what their thinking. I do know there are incentives for malware authors to create large botnets (zombified machines that don't act funny, they simply report to an IRC channel and await command), and the easiest way to get the largest amount is to target window since its 90% of computers still. What may be even more shocking that you may want to know, is that some estimates have placed the number of machines in botnets around the world at roughly 150 million computers. Then the owners of the botnets find a client who has a use for them (or uses them for himself) and makes money. Thats the reason why viruses and worms today don't usually seek to destroy your computer or data, rather they want to take control of it without you being aware.

---

### Post by Kvark on 2007-05-20
This is what I'd write:
There is no need to tinker with Ubuntu's built in firewall because no ports are open by default so there is nothing to block.

The only time you need to worry about someone breaking into your computer from the network is if you install a server program to allow other computers to access shared folders, printers or anything else on your Ubuntu computer. Then make sure you read up on how to set up that server program in a secure way so you don't accidentally for example let anyone write (potentially dangerous) files in shared folders on your computer without a password.


There is no need for an anti virus program because pretty much all viruses target Windows. The techincal details around why there has been almost no viruses that can taget Ubuntu has been discussed endlessly but why doesn't matter. The fact is that the risk of running into a virus that targets Ubuntu is close to zero.

But it's best to avoid downloading programs from unknown websites or repositories. Try to only use programs from sources you can trust, such as Synaptic's default repositories.


PS. I think it's the administrators and not the OS that makes the difference when it comes to viruses. Many Windows computers are administred by clueless home users who have no idea how to keep a computer secure. Most servers on the Internet runs Linux but they are administred by proffesionals. Some companies use Linux on their workstations too but they also have proffesional administrators and the very few home users that use Linux on their own are mostly geeks.

---

### Post by Adamant1988 on 2007-05-20
> **diablo75 said:**
> I'm writing an FAQ about Ubuntu that will be targeted towards Windows users, and I want to have a easy to understand, not-so-technical description of why Linux does not need things like a virus scanner or firewall software (although I know you can use both kinds on Ubuntu if you'd like).  I have a tech support website of my own that I use for business promotional purposes, and I'd like to start going to peoples houses to install Ubuntu on their PC's so they can move away from Microsoft.

Any input would be greatly appreciated.  Thanks!

Linux is a more secure kernel to start with, because it was designed for multiple users right from the get go.  So, the permissions based system would severely limit the damage a malicious piece of software could do on it's own.  Windows, in contrast, was designed as an off-line single user system. 

 Windows actually, would probably be much more secure going the route that they're going with Vista, UAC.  However, the UAC on the system is poorly implemented and annoying, but that's besides the point.  Windows would be infinitely more secure if the user accounts had access to administrator privileges on a case by case system, and true administrator accounts were not the status quo.  

Honestly, security problems are going to exist no matter what you use, and almost every single time the flaw can be traced back to a user doing something stupid and creating a vulnerability in their system.  I could even write a malicious bash script that executes 'sudo rm -rf /' which, by itself, does nothing and to a normal user does nothing.  But you'll get an idiotic user with administrative access to a computer who thinks that the file is worth running, and will knowingly execute it. 

You want to help people make their Windows boxes more secure? Educate them, don't switch them to something else.

---

### Post by darklemming54 on 2007-05-20
> **diablo75 said:**
> I'm writing an FAQ about Ubuntu that will be targeted towards Windows users, and I want to have a easy to understand, not-so-technical description of why Linux does not need things like a virus scanner or firewall software (although I know you can use both kinds on Ubuntu if you'd like).  I have a tech support website of my own that I use for business promotional purposes, and I'd like to start going to peoples houses to install Ubuntu on their PC's so they can move away from Microsoft.

Any input would be greatly appreciated.  Thanks!


windows is just as secure as linux if you use it right (not being admin). You don't need a virus scanner because its a waste of time for people to target .5% of users

---

### Post by darklemming54 on 2007-05-20
double post

---

### Post by trunks14 on 2007-05-20
These are a quotes from the "Linux for Dummies" book:

"To the casual observer (and some corporate IT decision-makers), Linux appears to be a freak mutation - a rogue creature randomly generated by anarchy. How, after all, can somethin so complex and discipline-dependent as a computer OS be developed by a loosely knit band of volunteer computer geeks from around the world?

Just as science is constantly attempting to classify and explain everything in existence, technology commentators are still trying to understand how this open source model can create superior software. Often, the reasons have much to do with the usualhuman desire to fill a need with a solution..."

And:

"In fact, any human resource expert will tell you that people who choose to do a job of their own free will produce the highest quality products."


I just wanted to share them :)

---

