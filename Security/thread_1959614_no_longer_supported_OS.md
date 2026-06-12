---
title: "no longer supported OS"
date: 2012-04-16
forum: Security
---

### Post by christon74 on 2012-04-16
Hello everybody  
I have a very simple and straightforward question:
What are the risks users run when they decide not to upgrade to Ubuntu 11 (or 12) and decide to stick to Maverick Meerkat (10.10) ?

Thank you in advance for any piece of information.

C;NAUD

---

### Post by MG&amp;TL on 2012-04-16
Nothing; except they have to stick with the versions of software that they had when the release went out of date. Sometimes they might miss a security fix because of this.

---

### Post by unspawn on 2012-04-16
> **MG&TL said:**
> Nothing; (..) Sometimes they might miss a security fix because of this.
I wouldn't classify missing security fixes as "nothing". besides there are no compelling reasons for regular users to run obsolete versions of any Linux distribution.

---

### Post by Grenage on 2012-04-16
> **unspawn said:**
> there are (..) compelling reasons for regular users to run obsolete versions of any Linux distribution.

See what I did there? ;)

Security updates would indeed be the biggest issue when using a version no longer supported; along with guides for more recent versions not matching what one has, or repository software being behind the times are other factors.

Most people should be running a supported version, unless they have a very good reason.

---

### Post by MG&amp;TL on 2012-04-16
Thanks Grenage. ;)

Yes, maybe I should have put more weight onto security updates. Security updates are VERY important.

Also, what reason is there to run out of date software, when you could have the new, shiny version?

---

### Post by movieman on 2012-04-16
> **unspawn said:**
> besides there are no compelling reasons for regular users to run obsolete versions of any Linux distribution.

Unity and Gnome 3.

Unity is OK on my netbook, but sucks on my laptop. Gnome 3 sucks everywhere.

I'm not even sure which version I'm running on the laptop now other than it's the one before Gnome 3 became compulsory. Once it's obsolete I'll have to switch to another distro unless Ubuntu supports MATE or one of the other sane Gnome-style UIs.

---

### Post by CharlesA on 2012-04-16
Even Gnome 3 classic?

---

### Post by Ms. Daisy on 2012-04-16
OK, I'd really like to discuss the reasons you would want updates pushed to you.  And what are the consequences if you don't get updates? This question has come up enough that it's not wasted effort to fully answer it IMO. 

I partially know the answers, but I'd like to hear more on the topic. There are obviously **security updates** that are pushed out when a vulnerability is discovered and patched.  So if you don't use an OS that gets updates, the vulnerabilities will continue to be found but they won't get patched. That means that ultimately you are increasing your odds of getting compromised as time goes on.  I will say that in my pen testing class, the first OS we cracked was a really old (unsupported) one BECAUSE IT'S EASIER TO CRACK.  

What about **hardware compatibility**? For instance if you buy a new printer and try to plug it into your no longer supported 10.10, it may work, it may not. But what exactly happens?  This is where I get fuzzy on the details. Does it mean that drivers specifically become hard to find (or are they portable from other versions)? I suppose if the technology changes enough then you wouldn't have backwards compatibility necessarily.

And **software compatibility**.  I imagine that new software wouldn't necessarily run well on an unsupported OS, but can anyone intelligently comment on the details?

Finally the **main reason to stick with an unsupported OS **(I'm guessing here): Say you have a low spec or old computer and all the hardware & software works. You've tried some newer versions & distros but they always break something. So stick with what works for as long as it still works?

I'm gonna hang myself out there: it's NOT a good reason to use an unsupported OS so that you can avoid a new desktop environment.  There are hundreds of tutorials out there to show you how to switch away from Unity & Gnome 3 using the newer Ubuntu versions. Or just switch distros. *But dear god please let's please not turn this into a unity flame fest, pretty please.*

---

### Post by CharlesA on 2012-04-16
> **Ms. Daisy said:**
> *But dear god please let's please not turn this into a unity flame fest, pretty please.*

What she said.

If you have a low-spec or older system - ditch Gnome and run something like XFCE or LXDE - both are lighter weight than either Gnome or KDE. Even if you don't want to use a flavor of Ubuntu on such a system, there are a ton of other distros that run well on low spec boxes.

---

### Post by Dangertux on 2012-04-16
> **Ms. Daisy said:**
> OK, I'd really like to discuss the reasons you would want updates pushed to you.  And what are the consequences if you don't get updates? This question has come up enough that it's not wasted effort to fully answer it IMO. 

I partially know the answers, but I'd like to hear more on the topic. There are obviously **security updates** that are pushed out when a vulnerability is discovered and patched.  So if you don't use an OS that gets updates, the vulnerabilities will continue to be found but they won't get patched. That means that ultimately you are increasing your odds of getting compromised as time goes on.  I will say that in my pen testing class, the first OS we cracked was a really old (unsupported) one BECAUSE IT'S EASIER TO CRACK.  

What about **hardware compatibility**? For instance if you buy a new printer and try to plug it into your no longer supported 10.10, it may work, it may not. But what exactly happens?  This is where I get fuzzy on the details. Does it mean that drivers specifically become hard to find (or are they portable from other versions)? I suppose if the technology changes enough then you wouldn't have backwards compatibility necessarily.

And **software compatibility**.  I imagine that new software wouldn't necessarily run well on an unsupported OS, but can anyone intelligently comment on the details?

Finally the **main reason to stick with an unsupported OS **(I'm guessing here): Say you have a low spec or old computer and all the hardware & software works. You've tried some newer versions & distros but they always break something. So stick with what works for as long as it still works?

I'm gonna hang myself out there: it's NOT a good reason to use an unsupported OS so that you can avoid a new desktop environment.  There are hundreds of tutorials out there to show you how to switch away from Unity & Gnome 3 using the newer Ubuntu versions. Or just switch distros. *But dear god please let's please not turn this into a unity flame fest, pretty please.*


While generally speaking this is true, there is a small logical fallacy here.  

For instance saying an "unsupported/out of date OS" is easier to crack, is ultimately not necessarily a universal truth. You likely used a "slightly" older OS. I'm guessing for Windows it would be 2000 or XP and I'm guessing for Linux Ubuntu was represented with 8.04. These are great targets because both had a poor or non-existant implementation of basic memory protections that a current operating system take for granted.

For instance -- the simple SEH you likely learned about in Windows won't fly on 2008 R2/ Windows 7. Or even Windows XP service pack 3. However for basic exploit development the underdeveloped architecture of the two OS'es I previously mentioned (8.04 , XP) give a great starting point. Unfortunately as operating system technology and memory protections advanced we're given much more complex themes like return-oriented-programming, ret2libc/plt/reg etc , heap sprays etc.. And different methods for memory manipulation. Those are more advanced and likely were not covered in an introductory class. Quite frankly they're not perfectly reliable and a pain in the butt to engineer.

My point in saying this is that a counterpoint to the example would be that a VERY old and rather unsupported operating system would not be "easy to crack" and does not have canned exploit code for it. I would like to introduce you to mp eix. This OS was one of the first (way ahead of it's time) to introduce enterprise class DEP In the form of seperate registries for data and executable bits as well as hardware enforced bounds checking. You would not, despite it running a "vulnerable" service be able to exploit this system traditionally (if at all). 

Additionally, in the afforementioned case that an older and "unsupported" operating system MUST be maintained. Linux has a distinct advantage in this field. The ability to backport your own patches. If it were a necessity one could forgo the fancy package manager and get back to basics and start modifying source code to meet the need of the system.

Now is this effective? That's a cost that needs to be weighted against the need to stay frozen at x, y or z version. Ultimately, I don't think disliking Unity is that reason. Why? You can easily install a different desktop environment on top of a minimal or server install. Or even a standard desktop install if you're interested in fighting with LightDM.

Ultimately, there are options but a "supported" OS is always preferable particularly in a non sensitive desktop environment where stability isn't quite as crucial as it would be in a high security production environment.

To add to this briefly -- one must also understand their environment. Hardening a desktop OS can summarily be regarded as hardening (if any) running services, and the possible code injection platforms (browsers, chat clients, office applications etc) most of these have easy to use update channels that can carry an OS long past Canonical's official EOL date.

Hope this helps.

-DT

---

### Post by Ms. Daisy on 2012-04-17
@ Dangertux: thanks for the explanation :) I always learn so much from your posts. 

Would the following be fair to say:* The old OS we owned were not  updated, thus making them easier to own.  In general as an OS gets older  and no longer receives security updates, the vulnerabilities will  increase for some time.*

And good point about updating all your software as well. 

And to all: what about software & hardware considerations? How does  OS updating affect those?  What are you missing if you don't update the  OS?

---

### Post by Jonathan L on 2012-04-17
Hi Christon and all

It is simply not the case than an older piece of software is a worse one.  What follows is a perspective on the topic.

As far as bugs go, you'll find that as a generalisation, an older program has _known_ bugs where a new one has _different but unknown_ bugs.  For many situations, known bugs are easily preferable, as they are likely to have known fixes and workarounds.  For many applications, predictability is essential.

As far as, for example, compatibility with new devices such as printers.  This is a reason to choose _protocols not products_.  For example, if your printer uses PostScript 2 over LPD over TCP/IP over 10baseT ethernet, then it is likely to work forever.  If it is Manufactuer Model 2012z and requires a special driver, you're going to need contemporaneous OS and hardware.

_Security updates_ are important, but again it depends on what the system is for.  A banking web server has a completely different level of exposure, value, and cost to repair to a print server or corporate file server or wiki.  Don't simply consider "security updates" a trump card, as security is not a simple and monolith subject.

_Software compatibility_ is a tricky subject.  As a matter of design, Linux relies heavily on dynamically loaded libraries and modules, and "depedencies" are rather generious in many packages.  (By which I mean that a package A is marked as depending on B when actually it doesn't or isn't that specific about versions.) This can lead to a rather deep tree of library dependencies.  If systems are updated, with very large dependency trees, you can find a clash in the requirements, and despite everybody's best intentions (and hard work) this can easily cause non-functioning software.  (The contrasting approach is to lean a little less heavily on dynamic loading, which is more typical on, for example FreeBSD.)  With the exception of security updates, many people will have no _need_ whatsoever to update their software, even if many _desire_ it.

Finally, one of the single most important things about Ubuntu is the existence of the Long Term Support versions, which for many of us is the _single deciding factor in choosing Ubuntu_ over other distributions.  So, security updates are available for a long time -- five years for server, three for desktop.  Which may be a very good reason for using 10.04 LTS, not 10.10.

Hopefully a useful perspective for this subject.

Kind regards,
Jonathan.

---

### Post by movieman on 2012-04-17
> **CharlesA said:**
> If you have a low-spec or older system - ditch Gnome and run something like XFCE or LXDE - both are lighter weight than either Gnome or KDE. Even if you don't want to use a flavor of Ubuntu on such a system, there are a ton of other distros that run well on low spec boxes.

Someone was claiming that there was no compelling reason for anyone to stick to an old version of Ubuntu. I suggest that the sudden elimination of established desktop environments is by far the most compelling reason for people sticking to old versions of Linux distros at this point. If an Atom with integrated graphics can run the latest Ubuntu OK then anything newer than a Pentium-3 can, it's not a performance issue.

You can ignore that if you want, but there are many people looking for a way to continue to get new versions of Linux without having to dump Gnome 2. At this point it looks like switching to Mint is the only option once support expires for whatever version of Ubuntu we're stuck on.

---

### Post by MG&amp;TL on 2012-04-17
> **movieman said:**
>  At this point it looks like switching to Mint is the only option once support expires for whatever version of Ubuntu we're stuck on.

Mint has ditched Gnome2 too-a tweaked Gnome3 is now the default environment. There is MATE as well, but inevitably that will not be supported (IMO) as well as the gnome2 was.

Sorry, but Gnome2 is dead. Much missed, but hopefully something even better will some through. :)

---

### Post by Dangertux on 2012-04-17
> **Ms. Daisy said:**
> @ Dangertux: thanks for the explanation :) I always learn so much from your posts. 

Would the following be fair to say:* The old OS we owned were not  updated, thus making them easier to own.  In general as an OS gets older  and no longer receives security updates, the vulnerabilities will  increase for some time.*

And good point about updating all your software as well. 

And to all: what about software & hardware considerations? How does  OS updating affect those?  What are you missing if you don't update the  OS?


I would say no that it is not fair to say. I'm not trying to be pendantic but there is a misconception that updating software makes it more secure. Truthfully it makes it more like running through a mine field. The more you move the more likely you are to step on a mine.

Think about it. If you stick with one version of the software and you KNOW it's vulnerabilities, you can take the necessary precautions to mitigate those vulnerabilities. Where as if you're constantly updating out of one vulnerability and into another it doesn't necessarily mean the mitigations you were using previously will work in this case.

What I'm trying to impress here is this : Just because a piece of code is flawed (most are in SOME way) does not mean you can't run it or must update out of it immediately.

There needs to be a logical process (this is risk management) where you assess the risk, if it is unacceptable, you will need to establish additional controls. Whether that is the use of mandatory access controls to mitigate risk, or the decision to ultimately update to a (hopefully) less vulnerable version, that part doesn't matter. What is important is the understanding of the threat and the application of a positive control to mitigate the risk generated by it.

To say that it was "easier to exploit" because it was old, sure in that sense it would be correct. An older operating system had many fewer tools to mitigate the effect of a standard overflow. So in that sense it's true (in many cases). However, on the converse side of that, a tried and examined piece of software may have 2 - 3 well documented vulnerabilities in which case controls can be implemented to affect their level of risk. Versus, the "unknown evil" which could have no vulnerabilities or hundreds of criticially unmitigatable vulnerabilities. So the real suggestion here is RESEARCH. Old is not necessarily bad.

Hope this helps.

---

### Post by Hungry Man on 2012-04-17
The difference between an unpatched piece of software and a patched piece of software is usually the same difference between an exploit and a vulnerability. Proper patch management is important. Will you ever get rid of all bugs? No. But if you patch the old ones it's now up to the attacker to come up with new ones. 

Patching is just another way to drive up the cost of exploitation. Depending on the software and the situation it may be incredibly effective (browsers) or not at all (Java.)

When you don't patch for a while the amount of known and working exploits that now belongs to the hackers arsenal grows. You are simply making their lives easier. It makes something like Apparmor less effective because an attacker can not only use an exploit to get onto the system but also potentially make use of another exploit (because they'll have many) to bypass your local MAC security.

So can you make up for an unpatched program? Sure, even apparmor alone will do it. But can you make up for multiple programs and the kernel not being patched in a long time? Not without a ton of work and even then it's just a matter of chaining the right exploits.

In a live situation we're usually only ever dealing with 1-2 exploits. If you've got year-old unpatched software the hacker might have 100 working exploits for your system. 

I see no way to truly properly secure ones self while running unpatched software + kernel, and even with the great deterrents provided by Linux (MAC) it wouldn't be enough.

---

### Post by Dangertux on 2012-04-17
> **Hungry Man said:**
> The difference between an unpatched piece of software and a patched piece of software is usually the same difference between an exploit and a vulnerability. Proper patch management is important. Will you ever get rid of all bugs? No. But if you patch the old ones it's now up to the attacker to come up with new ones. 

Patching is just another way to drive up the cost of exploitation. Depending on the software and the situation it may be incredibly effective (browsers) or not at all (Java.)

When you don't patch for a while the amount of known and working exploits that now belongs to the hackers arsenal grows. You are simply making their lives easier. It makes something like Apparmor less effective because an attacker can not only use an exploit to get onto the system but also potentially make use of another exploit (because they'll have many) to bypass your local MAC security.

So can you make up for an unpatched program? Sure, even apparmor alone will do it. But can you make up for multiple programs and the kernel not being patched in a long time? Not without a ton of work and even then it's just a matter of chaining the right exploits.

In a live situation we're usually only ever dealing with 1-2 exploits. If you've got year-old unpatched software the hacker might have 100 working exploits for your system. 

I see no way to truly properly secure ones self while running unpatched software + kernel, and even with the great deterrents provided by Linux (MAC) it wouldn't be enough.

Then truthfully you're failing to see how MAC work. There is no "getting on the system" with properly configured MAC. The exploit will fail (usually due to lack of mmap() access).

Hope this helps.

---

### Post by Ms. Daisy on 2012-04-17
OK, well let's back up then.  Dangertux, why should I update my operating systems as a typical desktop user?  If I'm not receiving security benefits unless I can implement the risk management you mentioned, then what will the updates do for me?

This is like every other security measure, isn't it? You can't be secure unless you understand it.  You can't boil it down, except to say something mildly useless like "updating is a good idea."

---

### Post by Dangertux on 2012-04-17
You're over simplifying a topic that can't really be simplified that way.

Look at it like this -- the concept of a "supported" OS is that someone else is making those patch management decisions for you. For the uneducated end user this is an "easy button"

However, what I'm trying to point out is the other side of the coin. IF you have a need to freeze your system in a certain configuration, you can always upgrade around it, via alternate update channels. The "support" you're getting is essentially just someone packaging software as it is released, this isn't particularly something you couldn't do yourself if the need were great enough.

In the OP's case (you know because staying on topic is pertinent even in security threads) they had a "desire" moreso than a need. Some people just want to do things their way, and that is fine. I was presenting them with a myriad of alternatives as opposed to the securistappo party line of UPDATE UPDATE UPDATE (k... you know what is worst for system security then not updating? Updating into regression, which happens more often then most devs would like to admit)

I'm also trying to point out the logical fallacy in "as it becomes older it becomes more vulnerable". Example :

```

#include <stdio.h>
#include <string.h>

int main(int argc, char** argv)
{
             char vulnerbuffer[4096];
             strcpy(vulnerbuffer, argv[1]); 
             return 0;
}

``` 

This function's usage will be just as vulnerable 10 years from now as it is right now. So if for some reason my program is taking this input instead of from the CLI argument but from a socket this would be remotely exploitable now...5 minutes from now, 10 years from now, in the exact same way it is right now (give or take any oddball compiler optimizations that change it's vulnerability).

Someone isn't going to "discover" a new exploit for this, they don't need to they need to dump 4097 bytes into it.

See my point now?

Hope this helps.

---

### Post by Ms. Daisy on 2012-04-17
> **Dangertux said:**
> You're over simplifying a topic that can't really be simplified that way.

Look at it like this -- the concept of a "supported" OS is that someone  else is making those patch management decisions for you. For the  uneducated end user this is an "easy button"
Yup, I think I figured that out as you were typing your reply (see my edit above?)  

Your patience with me is commendable ;)

---

### Post by Dangertux on 2012-04-17
> **Ms. Daisy said:**
> Yup, I think I figured that out as you were typing your reply (see my edit above?)  

Your patience with me is commendable ;)

oh well it was also for the greater good of the thread, but yeah that's what I'm saying. It's a stop-gap but until you truly understand what you're updating into or out of that's all it is.

---

### Post by Hungry Man on 2012-04-17
> **Dangertux said:**
> Then truthfully you're failing to see how MAC work. There is no "getting on the system" with properly configured MAC. The exploit will fail (usually due to lack of mmap() access).

Hope this helps.
There have been AppArmor/SELinux bypasses in the past. I'm not talking about bypassing it through design flaws (ie: the profile had a hole) I'm talking about bypassing it through race conditions etc / exploitation of the kernel.

A MAC can only be so tight - the program needs to function. So if my program X needs access to program Y and there are further exploits in Y yada yada yada you can have a MAC bypass.

Tons of programs need mmap. Every browser, for example, will use mmap to load up cached files etc. The MAC depends on the program. 

> This function's usage will be just as vulnerable 10 years from now as it is right now. So if for some reason my program is taking this input instead of from the CLI argument but from a socket this would be remotely exploitable now...5 minutes from now, 10 years from now, in the exact same way it is right now (give or take any oddball compiler optimizations that change it's vulnerability).
True, but the initial cost of exploitation is higher than every subsequent cost (ie: as knowledge of the vulnerability spreads usage of the vulnerability will increase.)

As soon as there's a metasploit module letting every skiddy with internet access have a look that vulnerability becomes a widespread exploit.

Shoulda used strn! lol

---

### Post by BigD77 on 2012-04-27
The reason I haven't updated to 11.10 in either Ubuntu, Lubuntu, or Xubuntu, is because I tried to do a fresh install while dual booting with XP.  And while either the Live CD or Live USB works great, once it's installed and the laptop is restarted, I get this hazy slpit screen image, with the display going down 2/3 of the screen and starting over, and going 2/3 of the screen from left to right.  This happend with all three variants mentioned.

So I went back to Ubuntu 10.10.  Everything works, period.

---

