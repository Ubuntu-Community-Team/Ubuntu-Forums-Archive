---
title: "The (serious) Ubuntu Virus Thread"
date: 2007-09-10
forum: The Cafe
---

### Post by tyggna1 on 2007-09-10
I do tech-support, for a living to help put me through school, and today I encountered my first virus call with Windows Vista.  I guess, up to this point, that the black-hat hackers had decided that Vista's bugs were enough to torment computer users.  This particular virus forced Vista to use it's "auto-repair" feature every 5 seconds, leaving only 4 seconds of usable time out of every 30.  Real nasty bugger--even prevented us from reinstalling the OS because of, again, the way Vista proceeds with a reinstall is supposed to be "user-friendly."   What a pain!

Anyway, why I'm posting, is I want to open a thread to brainstorm possible Ubuntu threats for viruses.  Granted: most black-hats don't see much reward for coding a virus in Linux, and despite their lack of moral codes, they often will over-look Linux out of professional courtesy (since many of them wrote programs that aided in the development of Linux, and use Linux to test their windows viruses before releasing them).

I know that the forums recommend not downloading from "shady repositories," and that's easy enough to avoid.  Ideally, when Ubuntu hits mainstream, very few users will ever have to add repositories at all.

I think the biggest threat to Ubuntu would be a key-logger virus.  It doesn't require admin rights to run, and it would just have to be bundled with a seemingly legitimate piece of software, and then start itself on boot-up.

Cures for this attack:  Check your preferences, "sessions" after every few installs, and see if anything is starting up that you don't want to.

What other attacks would Ubuntu be vulnerable to, and how can we plug them before they're a problem?

---

### Post by lisati on 2007-09-10
The only sure-fire protection I know of for ANY system is to leave the computer completely disconnected from the real world

---

### Post by st33med on 2007-09-10
I would doubt it, since most programs that use root access that can do major damage use a password. Anyways, a drive-by download won't work. You have to tell it a password in order to install.

---

### Post by tyggna1 on 2007-09-10
That's what I was referring to.  If you download from a "shady repository", and a virus is really bundled in another program, then it requires your password to install.  After that, it comes on after every boot, and logs all the keys you type and sends them to the author.  You wouldn't know it was on there, unless you checked your "sessions."  Of course, deleting the software out of add/remove would fix the problem.

I know Ubuntu isn't vulnerable to "drive-by" downloads like windows.  Heck, it's even resilient against "noob downloads," because most users who aren't security conscious likely don't know how to add repositories.

---

### Post by isaacj87 on 2007-09-10
> **tyggna1 said:**
> That's what I was referring to.  If you download from a "shady repository", and a virus is really bundled in another program, then it requires your password to install.  After that, it comes on after every boot, and logs all the keys you type and sends them to the author.  You wouldn't know it was on there, unless you checked your "sessions."  Of course, deleting the software out of add/remove would fix the problem.

I know Ubuntu isn't vulnerable to "drive-by" downloads like windows.  Heck, it's even resilient against "noob downloads," because most users who aren't security conscious likely don't know how to add repositories.

What would you guys say is a "shady repo?" I don't think I've ever come across one....

---

### Post by diatribe on 2007-09-10
not necessarily, rootkits exploit security holes without requiring input of a password

---

### Post by lisati on 2007-09-10
> **isaacj87 said:**
> What would you guys say is a "shady repo?" I don't think I've ever come across one....

I'm not aware of any either, but the *possibility* still exists. Having said that, we still have the freedom to exercise good sense (and caution) when checking out stuff from places with which we are unfamiliar

---

### Post by tyggna1 on 2007-09-10
> **isaacj87 said:**
> What would you guys say is a "shady repo?" I don't think I've ever come across one....

They're purely hypothetical--as far as I know.  There's potential for one though.  Take the user, Dfreer, for example.  He has his own repo that he uses to distribute emulators and other things like that.  Dfreer is really awesome, and his repo is great! but someone else could setup their own repo and advertise it as "great multimedia apps" or something, and really have viruses embedded in each program.  Of course, he'd be discovered really quickly and taken down after one or two victims posted something in the forums.  Heck, if it became a problem, Ubuntu could come with a "blacklist" of bad repos coded in, so that even gullible people can't get stooped, and they could just update that list with the Ubuntu updates periodically.

For now, I don't know of any, personally.  Of course, someone else could post the link to one in this thread if they have found one.

---

### Post by flatwombat on 2007-09-10
Since we're dealing with Open Source software, the code would be available and any nasty codes would be exposed and could be traced.  Presumably, with the skill of many linux users, any such site and package would have a very short life-span and the payload for the creator would be very, very low and the risk very, very high.  Remember that if this site is posting 'new' software, developers are going to be the first on the scene and checking the code immediately to see the new tweaks.

Now, perhaps I'm being naive about this, but you'd think that if the criminal element thought there was a payday available, someone would have already tried such an attack.  Might be easier ways to earn a dishonest buck!

---

### Post by bodhi.zazen on 2007-09-10
tyggna1 : I understand what you are saying, but there are some subtle points I would make to you ;)

First Linux == Windows

Seems obvious I know, but what I am saying is that much of what you know about windows secuity is applicable, but much is not. In addition there are some unique aspects to Linux ...

As has already been mentioned, it is difficult to install software in Linux without the admin password. In your example of a shady repo, you are giving root access to a program, so anything is possible. The entire system is open to the malicious code.

Check out this link [Install evilmalware](http://www.gnu.org/fun/jokes/evilmalware.html)

To run without entering the admin password or obtaining the root password is referred to by "root-kit".

With this said, opensource is the major difference. With opensource the code is available for all to examine. Everyone says windows is more of a target the Linux, perhaps so, but each "virus" takes advantage of a hole in the code and Microsoft is not so fast to close the holes.

The Open source community is much faster to close the holes, keep your system up to date, especially security updates.

If you want to learn Linux security, start here : [[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

Then read either a hardening linux book or online review :

[http://www.puschitz.com/SecuringLinux.shtml](http://www.puschitz.com/SecuringLinux.shtml)

[http://www.apress.com/book/bookDisplay.html?bID=395](http://www.apress.com/book/bookDisplay.html?bID=395)

[http://www.securityfocus.com/infocus/1539](http://www.securityfocus.com/infocus/1539)

[http://www.bastille-linux.org/](http://www.bastille-linux.org/)

As you can see this is a broad topic ....

Enjoy, and welcome to Ubuntu

---

### Post by VraiChevalier on 2007-09-10
A related question if I may?

Coming from a security paranoid Windows user (mostly former user) I am still getting the hang of this Ubuntu/Linux thing. I did quite a bit of reading to learn about Windows XP and in one of my books there is a list of services one may expect to see running or enabled in a default out-of-the-box install.

Is there a similar list of processes or services one may expect from a fresh, "default" Ubuntu install? I get concerned about unwittingly enabling some kind of daemon or something and exposing my system by mistake.

---

### Post by Buffalo Soldier on 2007-09-10
> **tyggna1 said:**
> They're purely hypothetical--as far as I know.  There's potential for one though.  Take the user, Dfreer, for example.  He has his own repo that he uses to distribute emulators and other things like that.  Dfreer is really awesome, and his repo is great! but someone else could setup their own repo and advertise it as "great multimedia apps" or something, and really have viruses embedded in each program.  Of course, he'd be discovered really quickly and taken down after one or two victims posted something in the forums.  Heck, if it became a problem, Ubuntu could come with a "blacklist" of bad repos coded in, so that even gullible people can't get stooped, and they could just update that list with the Ubuntu updates periodically...

I really like the blacklist idea. But I'm no security expert. Who knows it might have more cons than pros.

But in general, I really like the idea of activitely thinking how linux security could be thwarted and being ready before the attacks happen.

---

### Post by tyggna1 on 2007-09-10
thanks for the links Bodhi!  I'm still reading them all.

---

### Post by blithen on 2007-09-10
This is a great thread. I have read every post, and I am not scared of a virus anymore. Man, open source is great.

---

### Post by isaacj87 on 2007-09-10
> **VraiChevalier said:**
> A related question if I may?

Coming from a security paranoid Windows user (mostly former user) I am still getting the hang of this Ubuntu/Linux thing. I did quite a bit of reading to learn about Windows XP and in one of my books there is a list of services one may expect to see running or enabled in a default out-of-the-box install.

Is there a similar list of processes or services one may expect from a fresh, "default" Ubuntu install? I get concerned about unwittingly enabling some kind of daemon or something and exposing my system by mistake.

No, I'm pretty sure there isn't. Well, not like the ones found on Windows Systems. But you do bring up an interesting question...

Anyone who has better knowledge of this care to shed some light on this? :)

---

### Post by isaacj87 on 2007-09-11
> **bodhi.zazen said:**
> 

With this said, opensource is the major difference. With opensource the code is available for all to examine. Everyone says windows is more of a target the Linux, perhaps so, but each "virus" takes advantage of a hole in the code and Microsoft is not so fast to close the holes.

The Open source community is much faster to close the holes, keep your system up to date, especially security updates.



And like bodhi says...I doubt the developers would leave Ubuntu so vulnerable to daemon/background processes

---

### Post by VraiChevalier on 2007-09-11
> **isaacj87 said:**
> And like bodhi says...I doubt the developers would leave Ubuntu so vulnerable to daemon/background processes
But who's gonna protect me from myself?:lolflag:

It took a while for me to understand what "free-open source" really means but I slowly came to truly appreciate it. This thread serves to solidly confirm it.

---

### Post by isaacj87 on 2007-09-11
> **VraiChevalier said:**
> But who's gonna protect me from myself?:lolflag:

It took a while for me to understand what "free-open source" really means but I slowly came to truly appreciate it. This thread serves to solidly confirm it.

Haha...that's true..

I don't know, I'm still a little paranoid about spyware, security issues/vulnerabilities and malware/viruses. I've been trying to read as many security question threads as possible to calm my windows XP condition mind, but to no luck. :neutral:

---

### Post by tyggna1 on 2007-09-11
After reading bodhi's links (yes, it took me that long, there was a lot of info), I've installed logwatch to get a feel for "normal" computer use.  

After trying to absorb all that, I'm starting to gain a new excitement for Ubuntu.   I've always agreed with the statement:
> security is not a passive thing

And it seems like Ubuntu has all the tools available to take security into your own hands and, with about an hour of reading, surpass what any windows "security" program could do.

I still like the idea of a "black repository" list, however.  If for no other reason than it's a deterrent for malicious programmers to even try--and another selling point on Ubuntu that window's users will find appealing.   It's like saying, "not only are we virus free, but in the rare chance that a virus is developed and works on Linux, we'll keep the non-developer-level user safe from their own ignorance."

Also--Ubuntu will likely have to make some political concessions in the future, so that game developers and certain software developers can keep some of their trade secrets from the normal user.   After all, I would hate to get slided off on the greatest physics engine-based FPS game of all time, despite my willingness to pay, simply because I couldn't look at the source.  That's a risk that me, and my wallet, are willing to take--and a lot of users will feel the same way.  A "commercial repository" would have to hide its source just to stay competitive and give us the latest-and-greatest DVD burning utilities (or games, or photo-editing, or you name it software).  And if Ubuntu wants to make it as big as it deserves to be, then the development of such a concept is inevitable, and will heighten the risk of a "shady repository."

---

### Post by isaacj87 on 2007-09-11
> **tyggna1 said:**
> After reading bodhi's links (yes, it took me that long, there was a lot of info), I've installed logwatch to get a feel for "normal" computer use.  

After trying to absorb all that, I'm starting to gain a new excitement for Ubuntu.   I've always agreed with the statement:


And it seems like Ubuntu has all the tools available to take security into your own hands and, with about an hour of reading, surpass what any windows "security" program could do.

I still like the idea of a "black repository" list, however.  If for no other reason than it's a deterrent for malicious programmers to even try--and another selling point on Ubuntu that window's users will find appealing.   It's like saying, "not only are we virus free, but in the rare chance that a virus is developed and works on Linux, we'll keep the non-developer-level user safe from their own ignorance."


A black-list is definitely a great idea. It's kind of sad to think that some of our own kind would potentially poison our systems...

P.S. I'd still like to hear something about the background processes in Ubuntu...any of them potentially dangerous?

---

### Post by tyggna1 on 2007-09-11
> **isaacj87 said:**
> 
P.S. I'd still like to hear something about the background processes in Ubuntu...any of them potentially dangerous?

If it's such a concern, check out System->preferences->Sessions and click on the  "current session" tab.  That will show you the running processes (they have a gear next to them if they are actively doing something).

Bugs and holes in the programming code are what make vulnerabilities.  If any of those have holes in them that can be exploited--then they are potentially dangerous.

But, let's compare this to windows:  
Vista: 62 processes running, and roughly 200 services, at a more buggy rate than Linux
XP    : 30 processes actively running, and about 80 services, each about as exploitable as a Linux program (sad, but not inaccurate)
Linus: 10 items running actively, and 8 or so at idle, at roughly the same exploitation rate as windows XP--only difference is that the system base was originally designed and widely developed by hackers, who knew all the common tricks.

So, in short, at the very worst, you are 1/10th as likely to be exploited through a process.   Also, keep in mind that less than 2% of the hacker population would be creative enough to get into your system (whereas 90% of them would be intelligent enough to hack some part of windows effectively).

You're not perfectly safe in Ubuntu--but you're at significantly less risk.

---

### Post by tyggna1 on 2007-09-11
One down-side to "free-and-open-source" is that the black-hat hacker (I am a very crappy white-hat myself) will be able to directly examine the code, and it would take him less time to find vulnerabilities.  Fortunately, there are more white-hat hackers than black, and all of them look at Linux source code.  In addition, most all of the white-hats are more universally talented than black-hats (as black-hat hackers only want credit-card information now, and don't overly concern themselves with abstract learning. Anything beyond stealing money or valuable information isn't of interest to them, and most of them found that social engineering was a much easier route to take).

Also, white-hats prefer Linux, and have contributed a lot to the source over the years.  Microsoft employs mostly developers, and only a few hackers to develop their OS--where as Linus Torvald and his associates (most with hacker-type experience) have formed the backbone of our operating system for years.

So, the safety is in the design, and in what you know.

---

### Post by Buffalo Soldier on 2007-09-27
> **isaacj87 said:**
> A black-list is definitely a great idea. It's kind of sad to think that some of our own kind would potentially poison our systems...

i'm not worried about "our own" because "our own" wont be poisioning the well. It's those that pretends to be one of us, being all friendly and helpful at first. Then when no one notices, secretly insert harmfull stuff into his personal yet widely-used repo.

I really hope someone has already forwarded the blacklist idea to the Devs.

---

### Post by RAV TUX on 2007-09-27
I reinstall my Operating Systems so often a virus would be useless.

---

### Post by conehead77 on 2007-09-27
> **VraiChevalier said:**
> A related question if I may?

Coming from a security paranoid Windows user (mostly former user) I am still getting the hang of this Ubuntu/Linux thing. I did quite a bit of reading to learn about Windows XP and in one of my books there is a list of services one may expect to see running or enabled in a default out-of-the-box install.

Is there a similar list of processes or services one may expect from a fresh, "default" Ubuntu install? I get concerned about unwittingly enabling some kind of daemon or something and exposing my system by mistake.

Installing "Battle Of Wesnoth" opened a port at my computer (started a server daemon (?)). Im no security expert, so i dont know how bad this is, but looks strange to me.

Take a look at this thread for more details:
[http://ubuntuforums.org/showthread.php?p=3437658#post3437658]("http://ubuntuforums.org/showthread.php?p=3437658#post3437658")

---

### Post by p_quarles on 2007-09-27
The repository blacklist might be useful for new/uncareful users (provided that suspicious repos start showing up). 

That said, no one uses so many repos that they can't keep track of them. In a situation like that, whitelisting just works better, and takes a lot less work. The sources.list file in Debian/Ubuntu already effectively functions as a whitelist. 

Plus, given how quickly the OSS community would act upon a bad repo, I think the real threat is phishing/man-in-the-middle type attacks. With the current setup of APT, it would take some serious innovations among the bad guy set to get this to work, but I wouldn't put it past them.

My advice is to use repos with GPG keys. If you install something from a repo that doesn't, comment it out after you've gotten what you want.

---

### Post by g2g591 on 2007-09-28
> **tyggna1 said:**
> 
Vista: 62 processes running, and roughly 200 services, at a more buggy rate than Linux
XP    : 30 processes actively running, and about 80 services, each about as exploitable as a Linux program (sad, but not inaccurate)
Linus: 10 items running actively, and 8 or so at idle, at roughly the same exploitation rate 
You're not perfectly safe in Ubuntu--but you're at significantly less risk.

Well I count 17 on my Kubuntu Gutsy beta :popcorn:
 but still safer than windows due at least in part  beacuse if you look around you can find out what those programs actually do, unlike windows where the only possible source are obscure sites and those are pretty cryptic, although to be fair, some of the linux sites are obscure, but at least we do have official documentation
ps: I also like the "blacklist" idea

---

### Post by Wolfie Lee on 2007-09-29
> **VraiChevalier said:**
> But who's gonna protect me from myself?:lolflag:

It took a while for me to understand what "free-open source" really means but I slowly came to truly appreciate it. This thread serves to solidly confirm it.

YES, Good point, Im in the same boat, and after reading this thread, I AM more scared of ME than any "Black Hat".....:) I have TOTALY screwed up some old windows installs so badly, there was NO hope for them.......!! I am a HACK, NOT a HACKER!!!

---

### Post by Wolfie Lee on 2007-09-29
> **p_quarles said:**
> The repository blacklist might be useful for new/uncareful users (provided that suspicious repos start showing up). 

That said, no one uses so many repos that they can't keep track of them. In a situation like that, whitelisting just works better, and takes a lot less work. The sources.list file in Debian/Ubuntu already effectively functions as a whitelist. 

Plus, given how quickly the OSS community would act upon a bad repo, I think the real threat is phishing/man-in-the-middle type attacks. With the current setup of APT, it would take some serious innovations among the bad guy set to get this to work, but I wouldn't put it past them.

My advice is to use repos with GPG keys. If you install something from a repo that doesn't, comment it out after you've gotten what you want.


Excellent advice, and I will foolow it, but I am SUCH a NOOB that, while I know how to comment/uncomment, I DON"T know what GPG keys are....shed a little light?  Is ther a list of linux / Ubuntu acronyms, with NOOB - level descriptions somewhere?

---

### Post by bodhi.zazen on 2007-09-29
> **Wolfie Lee said:**
> Excellent advice, and I will foolow it, but I am SUCH a NOOB that, while I know how to comment/uncomment, I DON"T know what GPG keys are....shed a little light?  Is ther a list of linux / Ubuntu acronyms, with NOOB - level descriptions somewhere?

GPG = GNU Privacy Guard

see this link as a start :

[uwiki]GnuPrivacyGuardHowto[/uwiki]

---

### Post by p_quarles on 2007-09-29
GPG = Gnu Privacy Guard. It's an encryption key that insures you're connecting to the site you think you're connecting to. 

A good example is the [Medibuntu repository]("https://help.ubuntu.com/community/Medibuntu"). In my experience, most repositories, like this one, provide step-by-step directions for adding both the repo itself as well as the key. If it doesn't, that probably means they don't have a key. 

I don't know of any comprehensive lists of acronyms, but you can certainly find a lot of them through the search engines or by asking here.

---

