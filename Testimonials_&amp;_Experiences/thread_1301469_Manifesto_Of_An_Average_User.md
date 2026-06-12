---
title: "Manifesto Of An Average User"
date: 2009-10-26
forum: Testimonials &amp; Experiences
---

### Post by fryser_d on 2009-10-26
Hi there! 

My name is AverageUser and I'm an average user using averagely Ubuntu every day. 

I study in programming, I'm a computer technician for 6 years and I'm using Ubuntu for 2 years now. :guitar:

I was working late that night an I saw the update window pop up. Cool! updates! /*Click*/  

I woke up tomorrow morning and BOOM! VGA Driver down. Somehow not compatible with my kernel or always another #$%*, again and again and AGAIN! For the 50th time this years you guys interfered with my work. I'll skip the part where my VGA driver is still corrupted to say this... 

...HEY! THAT'S NOT NORMAL! 

Now, let me explain that statement. 

Linux fanboys still complains and laugh at Microsoft for having shitty OS. 
Well, let me ask you something; why won't you ask Microsoft to deploy an update that will tempered or crash the system to see how many lawsuits it would bring just for fun? 

You guys have Ubuntu going for more than 5 years, somewhere at this point I'm still waiting for someone to go: "Hey! lets NOT touch someones VGA, Sound, Network... EVER, and lets the user make the changes if he wants to." 

With Windows I can have Windows xp(2001). Install on it a VGA driver for Win7(2009), have an upgrade every week for 10years for my XP, and everything would be stable like the first day I got it. 

You guys use words like (Stable, Beta) but it doesn't mean nothing anymore. 

STABLE: From "If it ain't Broken, Don't Fix It" went to "Time allowed elapsed, lets fix it." 

You are going to have to implement some kind of interface or protocol or SOMETHING to be sure that this kind of behavior won't happen again.
var=>const=>var  = OK
var=>var=>var    = WTF!


_**Back To Basic:**_
[LIST]
[*]**Law 1:** Upgrades CANNOT change the interface between Device and Software. 
[*]**Law 2:** Backup, Small changes, Test.
[*]**Law 3:** Rollback Options! (Where are we?)
[/LIST]

If you want to get into the desktop OS market, you have to be taken seriously and have a professional approach, I know I can't propose Ubuntu for one of my clients cuz they will all leave me 2 months later.

I wrote this letter not by hate but by love of Ubuntu and hopping it will not fall into deaf ears. I'm sorry for my grammar, English is not my first language but I still believe you got the general idea. 

Please feel free to respond to that letter.
Thanks for your time.

Fryser

[COLOR="Red"]****************** EDIT ******************[/COLOR]
[COLOR="Green"]
Here's my thread with the source of my kernel problem. [[SOURCE]]("http://ubuntuforums.org/showthread.php?t=1299424")
Just to let u know some support I had with the same problem.
Not just for show off, but I think is not a secret among people. [/COLOR]

**cossist**
> I'm in the same boat. I've tried installing the latest as well as previous drivers 180.44 - 190.42. Each time I get the installer complaining about the kernel source. I was hoping to wait for the new release but I might be headed for a fresh install

**scoopit**
> Actualy, creiz, I think he's right about the bitching.
While you may be right about not getting help etc. he's having a point about this video crap not working right.

Testing changes is what's it all about. 
Ubunty is not ready for the desktop while these things are still around.
You and me will find a way out, but what about the average user ?
There are lots of excuses, but if you want to conquer the desktop you have to be right every time 

...says a 9.04 64-bit user who just lost data after a kernel hang after upgrading to 2.6.28-16...
seems to be related to resume issues, I'm annoyed, it worked before...
and a few days ago it cost me alot of time to install the nvidia drivers on a 8.04 LTS system...

**frisket**
> Same here. 8.10 and 9.04 docs claim to spot the fact that I have a crappy old nVidia Geforce 4 and will install the old nv driver, but they don't. They go right ahead and install some broken driver, so now the only way into my system is via single-user mode, and I can't get a network connection in that (if it's possible, would some kind soul please explain how? using ifconfig eth0 up and /etc/init.d/networking start both fail to do anything). All the suggestions I can find all assume you can log in and that you have a net connection. 

Maybe it's time to try Fedora...

**ozzyprv**
> Same here.
I was able to fix the nVidia drivers issue with every kernel upgrade until this last one.
See what at did before here 

I tried that and did not work. I have to spend some more time goign from the begining of that post and see if that works.

In the mean time, if you find a solution please let us know (I will do the same).

**Saghaulor**
> 
+1

Although you win more with honey than you do with vinegar.

At the very least if you're going to release shoddy updates have the decency to code a warning about the risks involved before installing.

---

### Post by Elfy on 2009-10-26
Moved to testimonials, forum feedback and help is not the place for this.

---

### Post by Tamlynmac on 2009-10-26
> fryser_d
Linux fanboys still complains and laugh at Microsoft for having shitty OS. 

Is profanity really required to express this? :roll:

I don't recall reading anything about Ubuntu that stated your required to update or upgrade everytime. As with any new OS (or software for that matter) one needs to invest some time learning and understanding it's use. When Windows users migrate to Ubuntu there's a necessary learning curve, as when converting to any new OS.

Simply accepting ("Click") an update or upgrade without investigation, is IMHO a bad idea with any OS. Especially, if one doesn't understand and/or realize the potential. It's been my experience, that's how many Windows users I've known found themselves in virus or BSOD trouble. By simply accepting ("Click") everything and questioning nothing.

All our home systems have been Ubuntu Only for 3 years and rock stable. I'm not a geek or a IT guru. Just an ex-Windows user that has found Ubuntu to be a fully functional stable platform, once we learned and understood how to use it. Basic knowledge is the key. Ubuntu is not Windows and when put in perspective if one expects it to be a Windows clone or doesn't invest some time in learning, failure is imminent IMHO.

I guess that makes me an above average user. Yet, I'm not a computer geek or wizard tech. Based on the number of people on this forum, either there is quite few above average users here or your definition of "Average User" needs updating. Perhaps, you might share with us you definition of an average user and where you acquired that information/data.

As for your slang regarding Ubuntu enthusiasts (Linux Fanboys), One might also ask your definition of that term. For it's unnecessary to label peope simply because your opinions may disagree. Based on your diatribe and without knowledge of who you are, one could easily (potentially incorrectly) profile you as an MS Fanboy. :-k I suspect you might find that unpleasant and argue your point of view.

Good Luck with whatever OS you find comfort in. I've always believed that each person should use what works best for them.

---

### Post by 3rdalbum on 2009-10-26
Read The Fabulous Manual: Kernel updates will break the link with existing third-party drivers. It will almost always happen. This is by design, actually; it helps the kernel devs to be able to make huge invasive changes to the kernel in-between versions, it assists in kernel security and it gently encourages hardware manufacturers to license their Linux drivers under the GPL and get them in the kernel, so they will never break on kernel update.

A stable kernel ABI is not the only correct way to do things, you know.

There is a system called DKMS that will automatically recompile any drivers registered with it, upon kernel upgrade. Ubuntu uses this system to make sure that the drivers you install with the Hardware Drivers program stay in sync with the kernel. Nvidia's own drivers ignore DKMS, despite it being trivially easy for them to implement full DKMS support in their driver. How trivially easy? About five lines of Python, maybe twenty lines of C.

So, you have a couple of options. Use the Nvidia driver from the Hardware Drivers program; it will never break. Ask Nvidia to add DKMS support to their own driver. Stop using Nvidia proprietary drivers - the open-source ones will not break. Or manually install the Nvidia driver yourself, and manually register it with DKMS (there's a HOWTO on the forums) so it will recompile whenever you upgrade your kernel.

---

### Post by solwic on 2009-10-26
> **fryser_d said:**
> Hi there! 

My name is AverageUser and I'm an average user using averagely Ubuntu every day. 

*yap yap yap yap...*

Please feel free to respond to that letter.
Thanks for your time.

Fryser

The solution is quite simple.  Use what works.  

Honestly, is any further discussion required?

---

### Post by edin9 on 2009-10-26
You have some valid points. The xorg side of things is a total mess, regardless of blame. Exactly the same can be said of the sound side. After reading the blog post of the PulseAudio dev about how Ubuntu has apparently botched Pulse again, it only further erodes my faith in Ubuntu.
As for 'use what works for you' replies, you can only use this so many times before only the hardcore are left. Linux desperately needs to sort the xorg and sound mess once and for all.

---

### Post by HappyFeet on 2009-10-26
> **edin9 said:**
> it only further erodes my faith in Ubuntu.

Then why do you bother with it? Are you looking for sympathy? Windows does not work for me. Do you see me hanging out in windows forums complaining? If I did, I would expect to be flamed BIG TIME. But I choose not to subject myself to abuse. Others, however.......

---

### Post by edin9 on 2009-10-26
> **HappyFeet said:**
> Then why do you bother with it? Are you looking for sympathy? Windows does not work for me. Do you see me hanging out in windows forums complaining? If I did, I would expect to be flamed BIG TIME. But I choose not to subject myself to abuse. Others, however.......

I was replying to a thread. Stop being such a fanboy because someone said something you don't like.

---

### Post by MarcusW on 2009-10-26
> **edin9 said:**
> I was replying to a thread. Stop being such a fanboy because someone said something you don't like.

Fanboy? Really? Nothing fanboyish about what he said.

---

### Post by edin9 on 2009-10-26
> **MarcusW said:**
> Fanboy? Really? Nothing fanboyish about what he said.

That's a matter of opinion.

---

### Post by Tibuda on 2009-10-26
> **fryser_d said:**
> My name is AverageUser and I'm an average user using averagely Ubuntu every day. 

I study in programming, I'm a computer technician for 6 years and I'm using Ubuntu for 2 years now. :guitar:
So are you really average or are you a technician/programmer?

---

### Post by ssri on 2009-10-26
As someone stated earlier, xorg is a mess.  If something critical like your video drivers is working the way you like it, then you should lock the relevant packages in synaptic or create pinning rules in /etc/apt/sources if you are using apt.  This will prevent any updates to your working video drivers.  If it ain't broke, don't fix it.

---

### Post by edin9 on 2009-10-26
> **ssri said:**
> As someone stated earlier, xorg is a mess.  If something critical like your video drivers is working the way you like it, then you should lock the relevant packages in synaptic or create pinning rules in /etc/apt/sources if you are using apt.  This will prevent any updates to your working video drivers.  If it ain't broke, don't fix it.

To be fair xorg has improved a LOT since when I first tried Linux in 2007(ish).

---

### Post by Pasdar on 2009-10-26
Why don't you just disable updates if you don't want updates? Or only install security updates?

---

### Post by Tamlynmac on 2009-10-26
> edin9
I was replying to a thread. Stop being such a fanboy because someone said something you don't like. 	

Using terms to label someone and profile them to simplify dismissing their opinion, is so unique. I suspect you're the first to attempt this novel concept.

Please lets stop with the labels and communicate only our opinions regarding the OP's post. Notice the OP hasn't responded since their original post.

I doubt this type of flamebait thread will result in anything positive and IMHO it should be closed. The T&E team could probably use this as a prime example of how rapidly things can deteriorate in this section.

Just my $0.02

---

### Post by solwic on 2009-10-26
> **Tamlynmac said:**
> Using terms to label someone and profile them to simplify dismissing their opinion, is so unique. I suspect you're the first to attempt this novel concept.

Please lets stop with the labels and communicate only our opinions regarding the OP's post. Notice the OP hasn't responded since their original post.

I doubt this type of flamebait thread will result in anything positive and IMHO it should be closed. The T&E team could probably use this as a prime example of how rapidly things can deteriorate in this section.

Just my $0.02

+1.  All the more reason to swing that proverbial ax, if you ask me.  But, nobody did ask me, so I'll just sit back and chuckle.  :)

And I second the closing of this thread.  It was pointless the moment it was started.  

IMO, of course.  :)

---

### Post by edin9 on 2009-10-26
> **Tamlynmac said:**
> Using terms to label someone and profile them to simplify dismissing their opinion, is so unique. I suspect you're the first to attempt this novel concept.

Please lets stop with the labels and communicate only our opinions regarding the OP's post. Notice the OP hasn't responded since their original post.

I doubt this type of flamebait thread will result in anything positive and IMHO it should be closed. The T&E team could probably use this as a prime example of how rapidly things can deteriorate in this section.

Just my $0.02

A term applied after seeing multiple comments in multiple threads by the same user attacking Windows and championing Linux. Comments that are usually blind rants at best. I only label someone after seeing and experiencing their actions. If you can think of a better way I would love to hear it.

---

### Post by solwic on 2009-10-26
> **edin9 said:**
> A term applied after seeing multiple comments in multiple threads by the same user attacking Windows and championing Linux. Comments that are usually blind rants at best. I only label someone after seeing and experiencing their actions. If you can think of a better way I would love to hear it.

Show compassion and try to help rather than label people and call names?  Seems like a better way to me.  I can't speak for Tamlynmac, but I'm sure he'd agree, at least in part.  

Who is more foolish:  the fool, or the fool who calls the fool a fool?  

Something to think about.  :)

---

### Post by Tamlynmac on 2009-10-26
> iRun
Show compassion and try to help rather than label people and call names? Seems like a better way to me. I can't speak for Tamlynmac, but I'm sure he'd agree, at least in part. 

Who is more foolish:  the fool, or the fool who calls the fool a fool?  

+1

Why bother wasting time labeling or calling others names when theoretically we should commenting on the OP's post. Not to mention it's a direct assault that inspires others to respond accordingly. Unless of course that's the intent.


> 
edin9
A term applied after seeing multiple comments in multiple threads by the same user attacking Windows and championing Linux. Comments that are usually blind rants at best. I only label someone after seeing and experiencing their actions. If you can think of a better way I would love to hear it.

A better way, maybe to not apply any terms to begin with. If you believe someone is a fanboy, so be it. Doesn't necessarily require sharing. Perhaps the individual you pointed at may believe your behavior is representative of a term, thankfully he kept it to himself.

Please, lets remain focused on the OP and stop throwing inflammatory expletives around. They solve nothing and only create a hostile environment. As my original response to the OP states just because someone is an enthusiasts, doesn't necessary make them a fanboy. So, why bother even pointing it out, what's the benefit or gain? To simplify dismissing their opinion in an effort to enhance your own? Good Luck with that.

Just my $0.02

---

### Post by aysiu on 2009-10-26
> **fryser_d said:**
> 
Well, let me ask you something; why won't you ask Microsoft to deploy an update that will tempered or crash the system to see how many lawsuits it would bring just for fun? Who says it doesn't happen?
[http://www.google.com/#hl=en&source=hp&q=windows+update+broke+my+computer&btnG=Google+Search&fp=b1b3111cc2f76bc3](http://www.google.com/#hl=en&source=hp&q=windows+update+broke+my+computer&btnG=Google+Search&fp=b1b3111cc2f76bc3)

---

### Post by creiz on 2009-10-26
This is rather interesting. 

I too, am a computer technician. Started working on it, around the same time as Fryser. 

That aside, the one thing I noticed about OS's, is that NONE OF THEM ARE THE SAME. They work differently, contradictory, and not the same.

What do you do in Mac OS X to find a folder? In finder, press the "go" menu, Computer, and look for your folder. 

In windows, Press the start menu, My computer, Local Disk "whatever:\", look for your folder.

Linux, Go to your desktop manager default explorer, in this case gnome: Places, Home, look for your folder. If you need another folder not in your user space, then fire up a terminal, sudo it, call nautilus on root, and THEN look for your folder.

Except if you have shortcut icons. It works the same way on those three OS's. But you get the idea.

I cannot expect to solve a problem I had with Windows, to solve it the same way in Linux. I can be a pro technician with all iterations of Windows, but I'm a complete "n00b" in Mac and Linux. Heck, even if I'm a pro at Ubuntu, I'd rush the moment I switch to Mandriva or Slackware. It's not the same. It may be the same Unix base, but the kernels are different.

As tamlynmac said, [QUOTE=Tamlynmac]
Simply accepting ("Click") an update or upgrade without investigation, is IMHO a bad idea with any OS. Especially, if one doesn't understand and/or realize the potential. It's been my experience, that's how many Windows users I've known found themselves in virus or BSOD trouble. By simply accepting ("Click") everything and questioning nothing.[/QUOTE]

Linux is built around technical questioning. Nothing is automatic, even if there are efforts to ease the trouble. Software are a breeze to install. Fire up Synaptic, and you're good to go. Drivers, patches, and other advanced features, well, expect a lot of hacking. 

I'm personally scared to update ubuntu, every time there is a major upgrade. I always report it to at least a week or so, so I can get good documentation here and there in the forums, or whatever other website that explains some problems and their solutions.

In fact, the best solution is always to, as iRun said it so well: [QUOTE=iRun]Use what works.[/QUOTE] Or, if you need to update, then 3rdalbum has a hint for you: [QUOTE=3rdalbum]Read The Fabulous Manual.[/QUOTE] People DO write those things you know? And yes, IT CAN be helpful. If you need an excuse, then read a couple of pages each time you're going to drop a brick. At the end of the month, you'll have more knowledge than you have now.

Ssri said it to: [QUOTE=ssri]If it ain't broke, don't fix it.[/QUOTE] You CAN pin and lock drivers so nothing will update it, but again, it may very well break dependencies.

All this, in fact, to say, when you encounter a problem, it's best to stay calm, look for documentation, and try to resolve the problem as the teach showed us since day 1: [QUOTE=The Teacher]The **step by step** approach, you goddam@!%^ n00b!!! And press carriage return![/QUOTE] The best problem solving technique there is. Proven and approved.

---

### Post by fryser_d on 2009-10-26
Thx **3rdalbum **for your answer: =D>

> Read The Fabulous Manual: Kernel updates will break the link with existing third-party drivers. It will almost always happen. This is by design, actually; it helps the kernel devs to be able to make huge invasive changes to the kernel in-between versions, it assists in kernel security and it gently encourages hardware manufacturers to license their Linux drivers under the GPL and get them in the kernel, so they will never break on kernel update.

In that whole thing you're the only one who said any pertinent stuff.

Basically: 
**You create a new driver? You want new functions? You must update the kernel to make it work, thus send it back cuz of GPL**

I'm mean... COME ON! ](*,)

REALLY? These guys f$%ked top my computer because no one wants to work and advance the kernel?

Then comes the question that some putted forward: "Why did you update without thinking it might corrupt your system?"

Well that would be like answering: -Why did you let that guy at the garage change your wheels for rolls of cheese? You never thought it will bring your face to a wall? 

Well...      [SIZE="4"]NO![/SIZE]
I have that strange weakness to TRUST professional advices.

Well I won't hide the fact that **I'M** the idiot who got screwed by blindly trusted (PROPOSED)(STABLE) updates. Where, like the law(I guess), should knew BEFORE do something stupid.(I guess)

But lets be serious here for a second. We're among mature adults here...

**Is that ethically correct?**

To leave a flaw by design to keep people updating and working by force? Instead of fixing that damn thing once and for all? [-o<

---

### Post by running_rabbit07 on 2009-10-27
> **edin9 said:**
> A term applied after seeing multiple comments in multiple threads by the same user attacking Windows and championing Linux. Comments that are usually blind rants at best. I only label someone after seeing and experiencing their actions. If you can think of a better way I would love to hear it.

HappyFeet doesn't flame Windows. He does let people know Ubuntu is for him and that if it isn't for you, then move on and quit crying.

---

### Post by verv87 on 2009-10-27
> **fryser_d said:**
> 
REALLY? These guys f$%ked top my computer because no one wants to work and advance the kernel?

Ubuntu developers didn't f**k up your computer, you did.

Nobody held you gunpoint until you satisfied their sadistic demands involving installing a number of Ubuntu updates.

You haven't payed Ubuntu a dime (otherwise you wouldn't be crying here, but instead getting personal support).

Why are you reacting as if they owe you anything?
> **fryser_d said:**
> 
Then comes the question that some putted forward: "Why did you update without thinking it might corrupt your system?"

That **is** the advice that usually gets puttered forwarded.

Let's pretend that the professional advice is delivered by that 150 by 80 pixel popup messagebox! In this case, and I quote, it's "Updates Available".

So you click it. Because, hey, it's *Professional Advice*.

And then a number of things happen -- which are best explained with an analogy involving cars (slashdot tradition, classic, can't go wrong with this) and ROLLS OF CHEESE FACE PLANTS (*why?*):
> **fryser_d said:**
> 
Well that would be like answering: -Why did you let that guy at the garage change your wheels for rolls of cheese? You never thought it will bring your face to a wall? 

I agree.

> **fryser_d said:**
> 
But lets be serious here for a second. We're among mature adults here...

**Is that ethically correct?**

To leave a flaw by design to keep people updating and working by force? Instead of fixing that damn thing once and for all? [-o<
Here's the thing, sweety:

Your problem does not require extensive usage of C.

Your problem does not require hacking the kernel.

Your problem requires rolling back to a previous version of the package(s) you updated.

Your problem requires 5 minutes of your time. How much time did it take to write up a post bitching about a free service?

---

### Post by Tamlynmac on 2009-10-27
> verv87
You haven't payed Ubuntu a dime (otherwise you wouldn't be crying here, but instead getting personal support).

Why are you reacting as if they owe you anything?

+1

I've always been amazed when reading similar entitlement posts.

When put into perspective, no one is forced to install Ubuntu and there is no charge to do so. I fear that some believe simply by making the attempt they are entitled to complain. Instead of actively participating in it's improvement, they prefer to malign it.

Should I receive something for free and find it lacking, I either dispose of it or give it away. Seems illogical and a complete waste of time to complain about it, as I had no financial investment in acquiring it. 

Your response is right on target IMO. Thank You

---

### Post by absolutezero1287 on 2009-10-27
I'd just like to point out that your system may break if you're using outdated hardware. I was really pissed off when compiz stopped supporting my intel graphics card. However, there are workarounds. I used to use Archlinux until the new driver for my intel card screwed everything up.

Installed Ubuntu 9.04 and I have no more problems.

Its also recommended that you read about an update before you install it. However, I see the OP's point when he mentioned that some people blindly update everything. People trust the devs to release updates that won't pwn the system but because of issues with the GPL some drivers are locked out of the kernel and other such "BS". This is why I prefer the BSD license. No strings attached.

Another point: I love Ubuntu and despite the issues I've had with my graphics card I use it as my main OS. It is the easiest Linux distro I've ever used. OP, if you want someone holding your hand then have a look at Redhat Enterprise Linux. The Redhat Corporation offers support (for a fee) and even installs custom Redhat-based systems for businesses. As a computer tech/software engineering major I see Redhat being used A LOT in the business world. The reason being is that they pay a very large amount of money and get constant support and updates tailored to their system. I have never seen a client of mine complain because "the latest update destroyed my Redhat box."

I'd also like to point out that most people that use Ubuntu encounter few (if any) problems. With Linux, problems are usually the result of PEBCAK.

On Xorg and Linux Sound:

:: The problem of choice ::
We all love Linux because of the choice it gives (GNU foot soldiers screaming about freedom, etc. etc.) but did you know that too much choice is a bad thing? Anyone who has studied psychology knows that the more choice a person has the more likely they are to be unsatisfied with that choice. I watched a TED talk where a psychologist explained just that. To paraphrase his example: "Back when jeans first came out they were very uncomfortable. You had to wear them for a few months and break them in to get a decent fit. Back then that was all we had so you can imagine my surprise when I walked into a department store and found hundreds of different jeans. I asked the person minding the register for a new pair of size 36 jeans and he asked, "well, do you want loose, relaxed, or regular fit? Would you like acid washed or stone washed?". Long story short I left with a pair of jeans that fit a lot better than my last jeans but they weren't perfect so I blamed myself for choosing the one pair out of hundreds that wasn't perfect."

The thing with Linux in general is the huge array of choices that can be quite overwhelming to a newcomer. All those different programs that do one thing: manage audio. Why can't there be one good program for sound instead of many programs that work some of the times but not ALL of the time? The answer is clear. Due to Linux's opensource nature someone can make a fork of an existing program because they think that "they can do it better." 

I'm not saying that choice is a bad thing. However, I think the Linux community suffers from an overabundance of choice and a lack of standardization.

As for Xorg, its come a long way since being used on ancient terminals. It may be time to design something better. After all, Xorg is pretty much all Linux has got.

---

### Post by verv87 on 2009-10-27
The problem is not Ubuntu, even in comparison to Red Hat.

Users need to understand the cycle.

MS recently came out with Windows 7. How long ago was Vista released? How long ago was Ubuntu LTS released, and when will the new LTS release take place?

Do MS or Apple provide nightly snapshots? No. If you want the stability **it's there**. Install the LTS version.

I don't even use Ubuntu anymore and I'm aware of this. Don't complain if you don't know what you're doing.

---

### Post by absolutezero1287 on 2009-10-27
> **verv87 said:**
> The problem is not Ubuntu, even in comparison to Red Hat.

Users need to understand the cycle.

MS recently came out with Windows 7. How long ago was Vista released? How long ago was Ubuntu LTS released, and when will the new LTS release take place?

Do MS or Apple provide nightly snapshots? No. If you want the stability **it's there**. Install the LTS version.

I don't even use Ubuntu anymore and I'm aware of this. Don't complain if you don't know what you're doing.

I usually use the LTS versions until they make like 3 or 4 new releases and then I switch to the latest one. I understand Ubuntu's cycle but did you ever stop to think that maybe the OP's hardware has poor support?

---

### Post by solwic on 2009-10-27
> **Tamlynmac said:**
> +1

I've always been amazed when reading similar entitlement posts.

When put into perspective, no one is forced to install Ubuntu and there is no charge to do so. I fear that some believe simply by making the attempt they are entitled to complain. Instead of actively participating in it's improvement, they prefer to malign it.

Should I receive something for free and find it lacking, I either dispose of it or give it away. Seems illogical and a complete waste of time to complain about it, as I had no financial investment in acquiring it. 

Your response is right on target IMO. Thank You

What?!?!?  You mean that they (Canonical/Ubuntu) have the NERVE to make a really awesome free OS and then REFUSE to give free tech support?!?!

The nerve!!!!

---

### Post by verv87 on 2009-10-27
> **absolutezero1287 said:**
> I usually use the LTS versions until they make like 3 or 4 new releases and then I switch to the latest one. I understand Ubuntu's cycle but did you ever stop to think that maybe the OP's hardware has poor support?
That's the thing. He made a post *ranting* instead of asking for help.

We don't know anything and judging from his attitude he doesn't want to be helped.

And specifically about what you pointed out: he could have backported a  newer kernel version (no, not the latest; the one that works) instead of waging it with the latest everything.

---

### Post by absolutezero1287 on 2009-10-27
> **verv87 said:**
> That's the thing. He made a post *ranting* instead of asking for help.

We don't know anything and judging from his attitude he doesn't want to be helped.

And specifically about what you pointed out: he could have backported a  newer kernel version (no, not the latest; the one that works) instead of waging it with the latest everything.

Good point. I vote that the OP is a troll and that this thread should be closed.

---

### Post by JBAlaska on 2009-10-28
Slightly off topic, but as I read this yet another crybaby thread I find some out and out profanity and some disguised  with **'s, and just last night I used a off color word disguised with **'s and got a warning point and my post was "Jailed", ironically by a MOD who posted in this thread...Super..

---

### Post by sloggerkhan on 2009-10-28
If this is all because you updated your kernel and then panicked when you had to reinstall the non-packaged nvidia driver you installed from nvidia's website, I have no sympathy for you. Bitch as nvidia to use dkms and realize what you're doing before you do it.

---

### Post by absolutezero1287 on 2009-10-28
> **JBAlaska said:**
> Slightly off topic, but as I read this yet another crybaby thread I find some out and out profanity and some disguised  with **'s, and just last night I used a off color word disguised with **'s and got a warning point and my post was "Jailed", ironically by a MOD who posted in this thread...Super..

Well, you know what they say. MODS=GODS

I find that a lot of mods love breaking the very same rules they're supposed to enforce. These are just the rules of the internet

inb4 permab&

To any mods reading this: This really is a crybaby thread. Its getting old and crusty. Kill it with fire.

---

### Post by Tamlynmac on 2009-10-28
> JBAlaska
Slightly off topic, but as I read this yet another crybaby thread I find some out and out profanity and some disguised with **'s, and just last night I used a off color word disguised with **'s and got a warning point and my post was "Jailed", ironically by a MOD who posted in this thread...Super..I believe that's what the "Report Button" is for. ;)

---

### Post by 3rdalbum on 2009-10-28
> **fryser_d said:**
> Thx **3rdalbum **for your answer: =D>



In that whole thing you're the only one who said any pertinent stuff.

Basically: 
**You create a new driver? You want new functions? You must update the kernel to make it work, thus send it back cuz of GPL**

I'm mean... COME ON! ](*,)

REALLY? These guys f$%ked top my computer because no one wants to work and advance the kernel?

Well I won't hide the fact that **I'M** the idiot who got screwed by blindly trusted (PROPOSED)(STABLE) updates.

To leave a flaw by design to keep people updating and working by force? Instead of fixing that damn thing once and for all? [-o<

I don't think you understood what I said - or maybe I'm misunderstanding you.

My understanding is that your system didn't get screwed up. My understanding is that you installed a third-party driver from another place, that ceased to work when you installed a new kernel. As designed.

Nothing got screwed up, everything is working as it should.

A non-stable kernel ABI is not a flaw, it's a particular design feature. It enables the kernel to move quickly. It allows the kernel developers to quickly rewrite any parts of the kernel that might come under legal attack, ***without*** forcing anyone to rewrite drivers.

All you have to do is recompile the driver. You don't need to edit the source code, just run "make" and "sudo make install" again and that's it.

Better yet, register your third-party driver with DKMS and it will automatically be recompiled when the kernel changes. That's something Nvidia and ATI desperately need to do by default in their drivers, but you can do it too.

Also note that there are Nvidia and ATI drivers pre-packaged in the repositories. These will not break on kernel update, because they use DKMS. If they did break, then it would be partly Ubuntu's fault. But they won't.

---

### Post by cariboo on 2009-10-28
Lots of requests to close this thread, so be it. THis thread is closed.

---

