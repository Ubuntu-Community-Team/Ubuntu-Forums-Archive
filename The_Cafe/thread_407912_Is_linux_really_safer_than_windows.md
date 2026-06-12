---
title: "Is linux really safer than windows?"
date: 2007-04-12
forum: The Cafe
---

### Post by Praill on 2007-04-12
If I envision a world where linux is the main-stream OS, I also envision a world where the problems in windows are duplicated over to linux.

Say I am a software developer looking for a way to install spyware on a linux-users computer. It would be easy.
I could write a bash script that say.. set up someones wireless.. or configured their totem player to play all formats. These operations would, of course, require the user give me their root password and then I have full access to the system.
I could now add my own malicious repositories to their APT and install whatever I wanted from it. Also, if I ever want to change what is installed on their computer.. I have APT's nice little update interface to do it in.

For the non-tech user, it seems to me that linux is at least as spyware prone as windows.

---

### Post by FuturePilot on 2007-04-12
That's the thing though. If it's open source then anyone could look at the code and someone would notice something malicious in it. And it would be impossible to get it into a repo without someone noticing malicious code. I just do see that being possible.

---

### Post by aysiu on 2007-04-12
Yes, if a user is stupid enough to install anything and give away her password for anything, then system security means nothing. Read more here:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by aysiu on 2007-04-12
> **FuturePilot said:**
> That's the thing though. If it's open source then anyone could look at the code and someone would notice something malicious in it. And it would be impossible to get it into a repo without someone noticing malicious code. I just do see that being possible.
It doesn't have to be in a trusted repository. It could be in a third-party repository.

It doesn't even have to be in a repository. It could just be a .deb file. Download it, double-click it, enter your password... now that .deb can do anything it wants.

If you have an indiscriminate user who will install anything, I doubt seeing the source code will be of any benefit to that person. And not all .deb files are open source. Plenty aren't, actually... like a lot of stuff in Multiverse or Medibuntu. Skype, Acrobat Reader, and Opera are all closed source programs--they all have a .deb files, and they're all in one repository or another.

The problem is that some people regard "safer" to mean "invulnerable" or "safe regardless of who's using it." Read the link I posted earlier and scroll to the bottom. Then you'll understand why "safe" means nothing if you have a dumb (from a security standpoint) user.

P.S. This thread can go on for a while, but eventually I'll merge it in with [this one](http://ubuntuforums.org/showthread.php?t=323028), just for historical purposes.

---

### Post by rufius on 2007-04-12
The security of one's computer regardless of operating system is directly related to the intelligence of the user. If your user is an idiot, which often they are, your user will have a less secure system. The best way to secure a system is to train the user to be an intelligent user.

---

### Post by aysiu on 2007-04-12
> **rufius said:**
> The security of one's computer regardless of operating system is directly related to the intelligence of the user. If your user is an idiot, which often they are, your user will have a less secure system. The best way to secure a system is to train the user to be an intelligent user.
How can you explain coherently in three sentences what it took me more than ten sentences to explain badly?

---

### Post by Redache on 2007-04-12
The old line of "There's no such thing as a stupid computers, just stupid users" also applies.

Security should be in the hands of the user. How many people scream out their pin numbers? zero. How many people give out their passwords? hundreds.

It's pathetic that people think computers need to do all the security for them. Pull the other one.

---

### Post by josephus on 2007-04-12
> The security of one's computer regardless of operating system is directly related to the intelligence of the user. If your user is an idiot, which often they are, your user will have a less secure system. The best way to secure a system is to train the user to be an intelligent user.

Is it true then that system security is inversely proportional to ease of use? 

By dumbifying an OS does that inherently make it less secure?

---

### Post by aysiu on 2007-04-12
I'd say security is inversely proportional to convenience, which is not necessarily the same thing as ease of use.

---

### Post by elephant007 on 2007-04-12
I think everyone is really missing the point.  The reason there are viruses/trojans/worms/etc is because of the dislike of Microsoft and their product(s).  
Not to mention the fact that these malicious software were written to expose the security holes in Microsoft Software.  Remember programs are only as secure as the operating system they're hosted on.  
  Anyone remember CDC? [Cult of the Dead Cow]("http://en.wikipedia.org/wiki/CDc_communications")??  I'm sure there are other groups out there, I can't remember their names though... one of them actually put out patches to Microsoft Windows before Microsoft does!!!
  OR it could all be a conspiracy!!!  
Microsoft purposely leaves holes in their OS and sells the information to an anti-virus/anti-trojan/anti-etc supplies to keep them selling products while receiving a share of the profits...  did I lose credibility?  Another theory is that with the cost of Microsoft Windows, it would be expected that the operating system be more secure and it is being exposed for the faulty product that it is... 
  Basically Microsoft's dominance of the OS world has a lot of users upset with the strangle hold they have on the world... So this is a way some are fighting back with...
of course this is all of my own opinion and I'm sure at least one other person would agree... 
I HOPE!!!

---

### Post by SunnyRabbiera on 2007-04-12
well not many people focus spyware and viruses for linux, this is because linux is not on top of the market... Windows is.
Linux can get spyware, addware, and be killed and hacked but what gives it the advantage is that linux is not a target for spyware like windows, and patches on linux tend to be much more effective then the ones for windows.
No OS is 100% safe, the only way to be 100% safe is to unplug your OS from the net and not allow anyone to use your hard disks....

---

### Post by BoyOfDestiny on 2007-04-12
As it is now, Ubuntu comes with lots of great apps, trusted repositories, and no ports open by default (where as with Windows it's expected to do some hunting, unless it already came pre installed and/or trial ware. Not to mention open ports and some holes for the NSA.)

You set up an ssh server on port 22, and leave the machine connected to the net with no firewall. There is a good chance someone is going to attempt to break in.

If you download random debs, and install and then run as root, you'd be no better off than an XP user running as admin.

Any closed source software on any platform. You really can't be sure what it does. It's a nice little black box, and this has been abused by malware writers and even certain large corporations ;).

What makes Linux and Free Software a tad different?

The source is there. Doesn't always make it easier to find out if it's doing something naughty, but at least it's possible without reverse engineering. It's transparent. No security by obscurity.

The other thing, is Windows is homogeneous. Many of the flaws old versions have may apply to the next as well...

Meat of my argument right here:

Let's say Linux dominates. Are all users running native 32-bit or native 64,-bit how about some other platform out of dozens. Is everyone running the same kernel version. Are they using the same browser? How about the same Desktop environment. How about X?

The point is, there is diversity. It is not like Windows. Worms won't effect a huge number of machines like they can with Windows. A trojan written in assembly isn't very portable. It can't effect every Linux user on the net.

This article is from last year, but illustrates the point nicely.

Of Windows and Boll Weevils
[http://www.linux-watch.com/news/NS9351245770.html](http://www.linux-watch.com/news/NS9351245770.html)

Figure I'd add a more recent link to echo the problem of Windows security.

Microsoft and the Clippy of death
[http://www.cbronline.com/article_news.asp?guid=CFE81578-B0A5-42DA-9567-29E6BE17BB81](http://www.cbronline.com/article_news.asp?guid=CFE81578-B0A5-42DA-9567-29E6BE17BB81)

"Microsoft has issued five new critical security bulletins, offering patches for 14 vulnerabilities in Windows products, including one that could allow the much-derided Clippy software assistant to take full control of a PC on behalf of a bad guy."

---

### Post by rufius on 2007-04-12
> **josephus said:**
> Is it true then that system security is inversely proportional to ease of use? 

By dumbifying an OS does that inherently make it less secure?

By "dumbifying" an OS, you tend to make the system less restricted. This can make it more insecure, but its not necessarily the case. Ubuntu may be dumbified to some extent but that doesn't make it less secure than Windows Vista. The key thing is to **educate the user**.

To aysiu: I'm a man of few words, I say no more than is needed to get my  point across :).

---

### Post by jrusso2 on 2007-04-12
The reason that Microsoft windows is so much more effected is because of stupid decisions made by the company that sacrificed security for usability.

These "features" include running all users with administrators privileges, and using active x with the ability to pretty much do anything on the users system.

So I really don't buy this "Big Target" ideology.

True it is a big target but the first hacker to bring down millions of OS X users or Linux users is guaranteed instant fame.

Jeanette

---

### Post by FuturePilot on 2007-04-13
> **aysiu said:**
> It doesn't have to be in a trusted repository. It could be in a third-party repository.

It doesn't even have to be in a repository. It could just be a .deb file. Download it, double-click it, enter your password... now that .deb can do anything it wants.

If you have an indiscriminate user who will install anything, I doubt seeing the source code will be of any benefit to that person. And not all .deb files are open source. Plenty aren't, actually... like a lot of stuff in Multiverse or Medibuntu. Skype, Acrobat Reader, and Opera are all closed source programs--they all have a .deb files, and they're all in one repository or another.

The problem is that some people regard "safer" to mean "invulnerable" or "safe regardless of who's using it." Read the link I posted earlier and scroll to the bottom. Then you'll understand why "safe" means nothing if you have a dumb (from a security standpoint) user.

P.S. This thread can go on for a while, but eventually I'll merge it in with [this one](http://ubuntuforums.org/showthread.php?t=323028), just for historical purposes. I see what you mean. And that's probably one of the reasons that Windows gets so many viruses and stuff, because people go around downloading random things from random sites and they don't know what they do.

---

### Post by kragen on 2007-04-13
> **rufius said:**
> The security of one's computer regardless of operating system is directly related to the intelligence of the user. If your user is an idiot, which often they are, your user will have a less secure system. The best way to secure a system is to train the user to be an intelligent user.

Not necessarily - yes if a user is an idiot, then they are more at risk, but steps can be taken to reduce that risk, even for users who aren't security conscious. 

For example: Windows vista finally requires some confirmation before allowing the user to perform administrative tasks, but they've made a huge mistake - they now ask for confirmation so often that it becomes meaningless. Soon enough many users will mindlessly click through the warning boxes and malware will get installed anyway. Ubuntu, on the other hand, only asks for confirmation when its absolutely necessary. There is clearly identifiable logic behind when the password dialogue appears, and probably most importantly it's also a password dialogue, so it should be clear to the user that they are giving administrative privileges to some application or process, unlike in vista where a security dialogue is just another "are you sure you want to do this?" box, where users who are used to wading through notification after notification would easily give privileges to something without realising.

---

### Post by amohanty on 2007-04-13
To second kragen, yes to a degree a stupid user will definitely contribute to breaches in the integrity of the system, however its really easy to shoot yourself in the foot if someone hands you a loaded 12 guage shotgun. 

The *nix philosophy (as I understand it) has usually been - sure we will give you the gun, but you are going to have to find the directions to the gun shop, figure out a way to get there, remember to take the money, buy the pellets, know how to load the gun and _then_ pull the trigger to shoot yourself in the foot.

Used to be that, that did keep away some terminal fearing beings from jumping ship, but even in the gui world, the separation between what the OS does and what the user does (something that the NT architects 'borrowed' from the *nix world) is still so hard that its not quite that easy to mess up. 

And that's the whole point. Don't make security so cumbersome that users click through ala Vista nor make it so easy that they keep killing themselves ala winxs priot to 2k. Its a fine balance to maintain and a not so easy one. Its not that linux distros always manage to strike it, but because of the *nix pedigree, for better or worse its hard for them to screw up.

At the end of the day security is the user's reponsibilty and requires active partiticipation on their part, but making it a wee bit harder to mess up also helps.

AM

---

### Post by aysiu on 2007-04-13
> **amohanty said:**
> 
The *nix philosophy (as I understand it) has usually been - sure we will give you the gun, but you are going to have to find the directions to the gun shop, figure out a way to get there, remember to take the money, buy the pellets, know how to load the gun and _then_ pull the trigger to shoot yourself in the foot. That may have been so in the past, but with the advent of GDebi, all a dumb user would need is an email saying, "Download this cool program!" with a link to a malicious .deb (these don't exist yet, but they easily could in the future). Click on the link. Double-click the .deb, enter your password. Ta-da! Your system's screwed. Just as easy as in Windows XP almost...

---

### Post by kragen on 2007-04-13
true, but if users associate installing programs with searching for them in synaptic and letting synaptic fetch them, then its less likely to happen than it is in windows, where users associate installing programs with searching for them in google, and downloading exe's from any website that doesn't look too dodgey :)

That's one of the things that makes the synaptic / apt-get may of doing things so great, and I bet that with a little bit of thought most users can be protected from a wide variety of scams in similarly subtle ways.

---

### Post by amohanty on 2007-04-13
> That may have been so in the past, but with the advent of GDebi, all a dumb user would need is an email saying, "Download this cool program!" with a link to a malicious .deb (these don't exist yet, but they easily could in the future). Click on the link. Double-click the .deb, enter your password. Ta-da! Your system's screwed. Just as easy as in Windows XP almost...

Agreed and that's why I don't always like the sudo approach that ubuntu takes. However the other options are not really any better or worse. Everyone of them has its pros and cons. 

The way I look at it is that security is really a reactive issue with some pre-emptive aspects. I would consider security to be good enough when it can let you know as soon as something bad happens and then allow you to find out what happened and fix it. In that scenario linux is so much better at not only logging what happened and the plethora of tools to let you fix the problem, not to mention giving the pre-emptive options some teeth that its far easier to protect the stupid user and recover from catastrophic actions than with windows. 

Moreover so far the implementations of security models are fairly unintrusive as far as the user experience is concerned. Something to also keep in mind is that most security discussions only talk about escalation of privileges and root access. What is lost in that is some people value the data in userland more than a borked system, which sort of of throws out this entire thread anyway :) beacuse a user can always mess up their own data.

Ultimately an informed user is the best hope, however in light of the commoditized computer, that is not a reasonable expectation, and all system developers can hope for is to strike the right balance between security and usability. IMO so far (as of right now) distros like ubuntu have been able to strike that balance quite well.

AM

---

### Post by nocturn on 2007-04-13
> **Praill said:**
> If I envision a world where linux is the main-stream OS, I also envision a world where the problems in windows are duplicated over to linux.

Say I am a software developer looking for a way to install spyware on a linux-users computer. It would be easy.
I could write a bash script that say.. set up someones wireless.. or configured their totem player to play all formats. These operations would, of course, require the user give me their root password and then I have full access to the system.
I could now add my own malicious repositories to their APT and install whatever I wanted from it. Also, if I ever want to change what is installed on their computer.. I have APT's nice little update interface to do it in.

For the non-tech user, it seems to me that linux is at least as spyware prone as windows.

The main difference is in delivering your payload.  Windows default to running as admin, so any old browser exploit can plant malware.

Linux is hugely different, not to mention that you get most of your software from repositories which are signed with a PGP key.  So even sneaking malware on the download servers would not be sufficient.

In the windows world, everything is downloaded as a binary file (setup.exe) form sites that employ no cryptographic checks on content...

---

### Post by jlk on 2007-04-13
You can actually explain security coherently in two sentences.

> The security of one's computer regardless of operating system is directly related to the intelligence of the user. The best way to secure a system is to train the user to be an intelligent user.

---

### Post by Tsen on 2007-04-13
To sum up what's been said and add my two cents:

Windows and *nix systems differ in security greatly, and NO, it isn't because of market share.  *nix systems treat administrative actions very differently from Windows.  Windows is designed with the philosophy, "You're too stupid to know what you're doing, so we'll assume the programmer does and let the program do whatever the hell it wants with your system settings."  It's ridiculously easy to weedle your way into administrative rights in Windows.  *nix, on the other hand, requires explicit root access (usually via a password prompt) before it can do anything.  Programs can't skirt around this--they NEED you to enter that password (or run it as root, which requires that you previously entered the password) to do anything to system files or settings.
Now, if you have a stupid user, all that's for waste.  I always shake my head and walk away when I see a Windows user downloading from Limewire while simultaneously asking me why they have so many viruses.  Linux isn't immune to stupid, it just doesn't have that problem to the same extent as Windows because typically, stupid people don't even know what Linux is.

---

### Post by 3rdalbum on 2007-04-13
Yes, *nix has unprivileged users and compartmentalisation. It even has an "executable" permission, which means that a really dumb user will not be able to run a random binary (apart from a native package) and a smarter user who has the knowledge will know not to run them.

But:

It's really the operating system's community which holds the key to Linux's security and Windows' insecurity. Linux users always educate new users about proper security practice; why things are done the way they are, and what not to do. However, the typical Windows user's approach to computer security is "Install a firewall and an anti-virus package". If someone is asking about how they can prevent themselves from getting viruses, a Windows user will suggest "Install McAfee".

In other words, proactive security practice is something that is passed down from generation to generation of Linux user, stopping threats from reaching the computer. Windows users pass down REACTIVE security from generation to generation; trying to contain threats once they arrive at your computer. Once a threat reaches your computer, your security system is exposed as stinking smeg. That's the difference between Windows and Linux users, and between WIndows and Linux.

---

