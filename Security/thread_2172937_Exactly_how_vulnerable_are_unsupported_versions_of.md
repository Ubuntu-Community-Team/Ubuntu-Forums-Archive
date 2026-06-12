---
title: "Exactly how vulnerable are unsupported versions of Ubuntu?"
date: 2013-09-07
forum: Security
---

### Post by Hylas de Niall on 2013-09-07
The purpose of this thread is to enlighten both myself and other users about the frequently mentioned dangers of running versions of Ubuntu that are past their 'end of life'.

Many folk (myself included) still have hardware that can't run newer Ubuntu releases, but which can run older versions with ease. We are always reminded of the 'vulnerabilities' of out of date releases, but what exactly are the dangers? Is it really all that hazardous? 

I'd *love* to keep running Lucid on a couple of my machines.

Thanks in advance.
:)

---

### Post by grahammechanical on 2013-09-07
It is your machine. It is your decision. Canonical agreed to supply security patches for a specific amount of time and they have kept to their agreement. That is about it really. How vulnerable was Lucid at the time those security patches were being supplied?

The Ubuntu Weekly Newsletter always supplies a list of Updates and Security updates for all the in-life Ubuntu releases. Links are provided to emails that explain (or not) why the patch needs to be applied. Judge for yourself how necessary they are. But these patches are available and it is good that we get them. I value the way Linux and Ubuntu developers are continually keeping the distribution up to date. This is a better way than waiting until there is a major breach in security and then rushing out a fix which some users may not apply and so open a vulnerablity to other machines running the same OS.

The fact is that life moves on. Newer Linux kernels are developed and support for older kernels is dropped. What kernel do you have in Lucid? Linux 2.6? Well, Saucy Salamander has Linux kernel 3.11.

Regards.

---

### Post by mörgæs on 2013-09-07
Why do you want to take the risk if you can just install Lubuntu 13.04? 

The single most effective means in keeping safe is using updated software (not thereby saying it's the only step you need).

---

### Post by vasa1 on 2013-09-07
> **Hylas de Niall said:**
> The purpose of this thread is to enlighten both myself and other users about the frequently mentioned dangers of running versions of Ubuntu that are past their 'end of life'.

Many folk (myself included) still have hardware that can't run newer Ubuntu releases, but which can run older versions with ease. We are always reminded of the 'vulnerabilities' of out of date releases, but what exactly are the dangers? Is it really all that hazardous? 

I'd *love* to keep running Lucid on a couple of my machines.

Thanks in advance.
:)
"Exactly" in the title and body of your question would be related to each vulnerability and whether the OS version is affected or not. 

Anyway, without any official figures, I'd hazard a guess that most of the "issues" arise because of "social engineering". In other words, two people, both with exactly the same outdated software and hardware may be affected differently. One opens dodgy emails and responds to "Congratz: you have won a billion dollars". The other user doesn't.

---

### Post by Rob Sayer on 2013-09-07
As far as security goes, I'd take a no longer updated version of ubuntu over a current version of windows anytime.

---

### Post by newb85 on 2013-09-07
As far as *anything* goes, I'd take an EOL version of Ubuntu over a current version of Windows any time.  :)

It's really hard to say "exactly".  Exactly what kind of answer were you looking for?  A percent chance you'll regret the decision?

Vasa1 makes an excellent point--basically, it depends on your interaction with the outside world.  If you're aware of the risk you're taking and you're extra careful, it will take your risk down somewhat.

As a side note, there are other things to consider in the decision whether or not to upgrade.  For one thing, the more out-of-date you become, the harder it becomes to get support from the forums.  Everyone else moves on, and your issues become ancient history.  Also, support for interaction with the outside world can become an issue (flash support comes to mind, but I know there are others).

Lubuntu has been recommended.  If you'd rather not jump from Gnome2 (which is no longer supported) to LXDE, though, I would suggest you use MATE.  It's a fork of Gnome2 that is still supported (though not by the Canonical team).  It's used by Linux Mint, so it's probably not going away any time soon.  More at [http://mate-desktop.org/](http://mate-desktop.org/)

---

### Post by tgalati4 on 2013-09-07
I'm running Linux Mint Mate 14 on some older machines.  It will give you a similar environment to 10.04.  In some respects older kernels and hardware are less vulnerable--security by obscurity.  If there is a massive Android infection, are your machines going to be infected?  Probably not.  Even if there is an exploit on a newer linux system, the fact that the frameworks have changed so much means that the exploit may not work on older systems.  

I agree, social engineering is more of a problem, regardless of your operating system.

So keep running your systems until they burn up, cease to boot up, or they no longer do what you want them to do.  Some people still use typewriters.  They can certainly type faster on a typewriter than on an iPad.

If you have several machines, take just one and put a newer distro on it.  RAM is key.  You will need to buy some RAM to max out older hardware.

I'm replying to this post on a 2005 Dell Inspiron 600m laptop.  Cracked bezel and dodgy battery.  Runs Linux Mint Mate 14 (based on 12.10) just fine.  I just updated the kernel to 3.5.0.40.  Of course, I put in more RAM, from 512MB to 2 GB, the maximum.  So if you can find RAM for an older machine, you can run current distros and at least have the illusion of being secure.

---

### Post by buzzingrobot on 2013-09-07
The vulnerabilities are impossible to quantify.  Unsupported systems, by definition, are vulnerable to exploits created after their EOL.  

Linux, of course, is targeted much less. 

If you can stay current with the apps used to access the net -- browser, mail, etc. -- you will decrease your vulnerability.  These things are easily installable from files provided by Mozilla/Google/Opera/etc and typically can update themselves.

If you have the skills and patience, you can backport kernel and other patches yourself.
  
Red Hat maintains a 2.6 series kernel for RHEL 6 that is very well-patched. It's available from the CentOS repos.  Dunno if it would work with Ubuntu releases of the same vintage as RHEL6,  but it might be an amusing experiment. And, you could always try a current Ubuntu mainstream kernel.

Still, the best, the only, way to get the Gnome 2 interface on a current supported base is to install Mate.  Some name changes were needed but it's the old Gnome 2 base recompiled and massaged for 2013.

---

### Post by Hylas de Niall on 2013-09-13
> **Rob Sayer said:**
> As far as security goes, I'd take a no longer updated version of ubuntu over a current version of windows anytime.

In essence that was what i was asking about.

With the impending EOL of Win XP there will be a lot of hardware that won't be capable of running newer releases (due to driver support in newer kernels) even of lightweight distros. It would be a shame for them to go to landfill when they can still be run efficiently with older Ubus.

To refine my original question - bearing the above premise in mind - would running out-of-date Ubus be as safe as running XP (even while it's supported)?

Thanks,

---

### Post by BBQdave on 2013-09-13
> **Hylas de Niall said:**
> With the impending EOL of Win XP there will be a lot of hardware that won't be capable of running newer releases (due to driver support in newer kernels) even of lightweight distros.

An old desktop that my Mom was using had Windows XP - wiped it long ago and installed Linux for her. When she updated to a new desktop a few years ago, I took her old desktop - 256 Mb of RAM - and it is now an Ubuntu 12.04LTS file server :)

With old hardware, I think it is a choice of repurposing. I could max out the RAM to 1 Gb, and run Lubuntu or Xubuntu nicely - but the original machine with original hardware, works nicely as a file server.

---

### Post by buzzingrobot on 2013-09-13
> **Hylas de Niall said:**
> In essence that was what i was asking about.

With the impending EOL of Win XP there will be a lot of hardware that won't be capable of running newer releases (due to driver support in newer kernels) even of lightweight distros. It would be a shame for them to go to landfill when they can still be run efficiently with older Ubus.

To refine my original question - bearing the above premise in mind - would running out-of-date Ubus be as safe as running XP (even while it's supported)?

Thanks,

Unless drivers are removed from the kernel, I'm not sure how adding new drivers means old hardware can't run newer kernels.

I think your "as safe as" question is impossible to answer in any measurable way.  That said, most attacks on PC's depend on operator error to let them in.  Almost all of those attacks target Windows users. If someone continues to use XP after it's sell-by date, that's a pretty good indicator they are not very security aware (ditto using XP now). So, that kind of user *is*, I'd think, more likely to allow his or her machine to be attacked than someone using an unsupported Ubuntu release. 

And, if that XP user is security aware, they'd still have much better odds with that old Ubuntu. 

All this is down to user behavior and the web environment, not the OS.  Unsupported software is vulnerable to attacks created after support ended.  Avoiding those attacks depends on user behavior.

(Expect all kinds of malware-infesting "Make XP Secure Forever" sites to appear as it nears its drop-dead date.)

---

### Post by Mephisto Pheles on 2013-09-13
I've used XP for a long time, until a year ago actually, I stayed away from Internet Explorer and refused to use Outlook from the very beginning, those were the attack vectors even on Win 95/98/ME. already 
  I never had any problems and I visited a lot of very dodgy sites through the years, using Opera mostly. 
It's not XP itself that is so insecure, despite the perception, it's all the other Microcrap that creates most of the the problems.
And Adobe (Flash and Reader) and Oracle (Java).
 Stay away from Microsoft Software (IE, Outlook, Office), remove Java and keep Flash updated and you'll be able to run it for another 10 years even after EOL.
Anyway I'm on Linux now so..

As for your question, what is the security you're talking about? Or rather what is the security you need?
What would be the worst case scenario? That's how you have to define your "vulnerability".
If you're just an occasional surfer, checking your occasional personal emails and your facebook page and watching some youtube videos what's the risk?
  If you're processing company data, running a business, working for one, or are responsible for the websites of your clients, that's an entirely different situation.

And don't forget that it's always the users and their own intelligencce, or lack thereof, and not the platform, that are the main problem.
 If you're dumb enough to click on everything and believe everything that might show up in your inbox or on your facebook page.. then you're it.
 Or as Beeb Birtles wrote it for the Little River Band... "Curiosity killed the cat."
Even on linux with the best firewall and anti-virus and whatnot else.

 It's also good to remind yourself sometimes that the computer security industry is a big industry.
They like to promote themselves in a lot of ways since there's a lot of money to be made.
Even dumb old Bush was smart enough to know that fear sells.
  It's easier and more profitable to sell some security software, a lot of it useless and pointless as every expert that doesn't have anythng to sell you will tell you, than to educate people to use their brains.

 I read a couple of articles recently about how pointless and useless anti-virus software really is. I'll see if I can find some links
Anti-virus products are rubbish, says Imperva
[http://www.theregister.co.uk/2013/01/01/anti_virus_is_rubbish/](http://www.theregister.co.uk/2013/01/01/anti_virus_is_rubbish/)
The School of Hacking
[http://www.thedailybeast.com/newsweek/2008/09/12/the-school-of-hacking.html](http://www.thedailybeast.com/newsweek/2008/09/12/the-school-of-hacking.html)
The Antivirus Era Is Over
[http://www.technologyreview.com/news/428166/the-antivirus-era-is-over/](http://www.technologyreview.com/news/428166/the-antivirus-era-is-over/)
Is Traditional Anti-Virus Software Really This Bad?
[http://techtalk.pcpitstop.com/2013/01/04/is-traditional-anti-virus-software-really-this-bad/](http://techtalk.pcpitstop.com/2013/01/04/is-traditional-anti-virus-software-really-this-bad/)

An interesting story from an insider
Why Antivirus Companies Like Mine Failed to Catch Flame and Stuxnet
[http://www.wired.com/threatlevel/2012/06/internet-security-fail/](http://www.wired.com/threatlevel/2012/06/internet-security-fail/)

Your biggest security threats don't come from your own computer or your own OS but from some of the sites you might be using, especially when you're using credit cards etc online.
That should be a far bigger worry than your outdated OS missing out on some security patches.
That doesn't mean you should not consider upgrading to xubuntu 12.04 LTS if your old box can run it.

---

### Post by whitesmith on 2013-09-13
> **Hylas de Niall said:**
> To refine my original question - bearing the above premise in mind - would running out-of-date Ubus be as safe as running XP (even while it's supported)?A supported version of Windows is just one that doesn't BSOD too frequently. And one that hasn't received excessive knocks from security specialists. Recent revelations indicate that American tech companies are working hand-in-hand with the NSA to implement back doors in software and hardware. Any back door intended to thwart illegal activity can be detected by bad guys and used to implement it. If you believe Windows is acceptably secure, you must also believe that politicians never lie. Go with Linux--any time, any version, full stop.

---

### Post by whitesmith on 2013-09-13
To **Mephisto Pheles**: ...**dumb old Bush** and...**Nietzsche**? My dear sir, you sound like one critical of established belief, a doubter of jingoistic slogans. Better be careful of what you say or the NSA will put you on the list of those needing Special Attention by the Thought Police. Oh, wait a minute, they already have. A tip of my hat to free-thinkers everywhere!

---

### Post by buzzingrobot on 2013-09-13
"...back door intended to thwart illegal actvity..." misconstrues the intent of a back door.

---

### Post by Mephisto Pheles on 2013-09-13
> **whitesmith said:**
> If you believe Windows is acceptably secure, you must also believe that politicians never lie. Go with Linux--any time, any version, full stop.

   I wouldn't take such a statement at face value. I doubt it that there are no backdoors in Linux. Despite the whole open source philosophy and the source code checking and so on and so forth. There's enough room to cheat, and enough people smart enough to get away with it. I wouldn't make any bets on it. But I won't lose any sleep over it either. 

And as for politicians.. I think I better skip that one :P

---

### Post by whitesmith on 2013-09-13
> **Mephisto Pheles said:**
> I wouldn't take such a statement at face value. I doubt it that there are no backdoors in Linux. Despite the whole open source philosophy and the source code checking and so on and so forth. There's enough room to cheat, and enough people smart enough to get away with it. I wouldn't make any bets on it. But I won't lose any sleep over it either.I trust FOSS because there is no central source for a government to coerce into complicity. Say, for instance, you're the NSA and you want to compromise implementation of the PKS in Linux. Who do you turn to for help? Linux is the work of a community, not a company, so carrots and sticks are useless. Even--and this is probably the extreme limiting case--you could persuade Torvalds to cave in the name of "national security" or some such bugaboo, that would have no effect on developers around the world tasked with maintaining the PKS piece. Compare that with the NSA's "black room" at AT&T's San Francisco switch. The NSA asked. AT&T complied. All traffic carried by that network went through the filter, whose existence only became public knowledge after the Justice Department mistakenly put defense lawyers on a cc list in an unrelated FOIA matter. Central points of management are easily exploited. Distributed management makes funny business immeasurably more difficult. That is what I like about Linux.

---

### Post by buzzingrobot on 2013-09-13
Regardless, people need to remember that the net is about publishing, not point-to-point communication.  The net is not private and is not meant to be a means of secure, private, communication. That includes email.

If you can't risk it being seen, don't use the net.

One point is that the NSA grabbed net traffic,  The more important point is that it is so easy, within the capabilities of many, many people.

---

### Post by Bucky Ball on 2013-09-13
*Thread moved to **Security Discussions**.*

---

### Post by Mephisto Pheles on 2013-09-13
> **buzzingrobot said:**
> Regardless, people need to remember that the net is about publishing, not point-to-point communication.  The net is not private and is not meant to be a means of secure, private, communication. That includes email.

If you can't risk it being seen, don't use the net.

One point is that the NSA grabbed net traffic,  The more important point is that it is so easy, within the capabilities of many, many people.

Good point, doesn't matter what you use the net with, the fact that you're using it already "exposes" you.

---

### Post by Mephisto Pheles on 2013-09-13
> **whitesmith said:**
> I trust FOSS because there is no central source for a government to coerce into complicity. Say, for instance, you're the NSA and you want to compromise implementation of the PKS in Linux. Who do you turn to for help? Linux is the work of a community, not a company, so carrots and sticks are useless. Even--and this is probably the extreme limiting case--you could persuade Torvalds to cave in the name of "national security" or some such bugaboo, that would have no effect on developers around the world tasked with maintaining the PKS piece. Compare that with the NSA's "black room" at AT&T's San Francisco switch. The NSA asked. AT&T complied. All traffic carried by that network went through the filter, whose existence only became public knowledge after the Justice Department mistakenly put defense lawyers on a cc list in an unrelated FOIA matter. Central points of management are easily exploited. Distributed management makes funny business immeasurably more difficult. That is what I like about Linux.

I'm not saying I don't trust FOSS. I'm saying there's no guarantee of anything, however unlikely it may seem you can not exclude the possibility.
If even some "standard" encryption algorithms have been compromised how can we know anything for sure?

And maybe I should have said: I doubt it that there are no backdoors **ON** Linux instead of **IN **Linux.
Let's assume linux itself is "safe". How can I be sure that Opera, the browser I'm writing this in is not compromised? How do I know my filezilla isn't? How can I find out if my router is? How about my nvidia drivers? My flash player? Maybe some of the chips on my mobo even? My networking card/chips? There are so many variables that it's impossible to know anything for sure.

 How can I feel so much more secure on Linux now that we know that SSL/https and the whole shebang is already compromised? Now that we know AT&T/intel/google/facebook/microsoft/yahoo ... the list goes on... are all in bed with "the enemy"?
 Being on Linux may give a lot of people a false sense of security, just like running viruscheckers, anti-malware programs and a lot of other security measures do. Encrypting my drive or some directory knowing that the encryption is probably compromised doesn't make me feel more secure anymore. So why would I even bother anymore?

 Linux is just one element in this complicated and complex equation.

And let's be honest and realistic, linux and ubuntu also have their share of security fixes and therefore security issues, despite all the code monitoring and all the checking and double checking that would - according to you - protect us.
Never underestimate the enemy ;)

---

### Post by Hylas de Niall on 2013-10-08
Right. Thanks to all.

From all the above, i gather that - as long as a user surfs safely and conscientiously - an unsupported old version (eg 10.04) is perfectly fine to use on older machines that simply won't run the newer builds (whether because of updated kernels' dropped support for certain hardware, or the increased resource needs of later versions).

I think my question has been answered :)

---

### Post by buzzingrobot on 2013-10-08
> **Hylas de Niall said:**
> ...

From all the above, i gather that - as long as a user surfs safely and conscientiously - an unsupported old version (eg 10.04) is perfectly fine to use on older machines that simply won't run the newer builds (whether because of updated kernels' dropped support for certain hardware, or the increased resource needs of later versions).
 

Surfing safely can reduce risk.  But, it can't eliminate vulnerability. By staying with unsupported code, you are assuring, if nothing else, that you will receive no fixes for new attacks developed to exploit weaknesses in code on your machine. 

Unless you are prescient, you can't know the risks that will appear tomorrow.

---

### Post by newb85 on 2013-10-08
Current versions of lighter variants of Ubuntu should mitigate that vulnerability while not exceeding the power of the machine you have running 10.04, and still meet your needs.

---

### Post by buzzingrobot on 2013-10-08
> **newb85 said:**
> Current versions of lighter variants of Ubuntu should mitigate that vulnerability while not exceeding the power of the machine you have running 10.04, and still meet your needs.

Plus, any version of any distribution can be made to require fewer resources by avoiding unecessary startup applications and services, and by running applications with fewer resources demands. Don't take the word of other people or random web posts.  Make changes to your system and measure the differences.  A great deal of Conventional Wisdom exists about this subject.  Most of it seems to be unvalidated echo chamber noise.

---

### Post by mörgæs on 2013-10-08
> **Hylas de Niall said:**
> Right. Thanks to all.

From all the above, i gather that - as long as a user surfs safely and conscientiously - an unsupported old version (eg 10.04) is perfectly fine to use on older machines that simply won't run the newer builds (whether because of updated kernels' dropped support for certain hardware, or the increased resource needs of later versions).

I think my question has been answered :)

You had decided to follow that path even before writing the initial post, hadn't you? No problem, you are of course free to do what you want on your own computers but please don't encourage others to use unsupported versions (not thereby saying that you have done so).

---

### Post by Bucky Ball on 2013-10-08
> **mörgæs said:**
> ... please don't encourage others to use unsupported versions (not thereby saying that you have done so).

+1. Also not insinuating that has been done. ;)

---

### Post by Hungry Man on 2013-10-08
If you are running an unpatched system you are not secure. If you think otherwise you're fooling yourself.

---

### Post by Hylas de Niall on 2013-10-10
> **mörgæs said:**
> You had decided to follow that path even before writing the initial post, hadn't you? No problem, you are of course free to do what you want on your own computers but please don't encourage others to use unsupported versions (not thereby saying that you have done so).

Not at all.

All my machines are running up-to-date Debian derivatives.

Rather than trying to encourage others to use unsupported OS's I was hoping to help assure them that their old XP machines - and there are very many of those which may be as much as ten years old - need not be sent to the dumpster. Such machines couldn't even run the lightweight spins of recent releases, as you know.

So what are those folks's options for replacing XP? A modern, command-line only Ubuntu (which is likely all many of those machines could run) to replace a full (though defunct) GUI in XP - or an older version of a more secure system than they had?

If you would rather let folk believe their old machines are of no more use when XP reaches OEL next April, with respect that's up to you. I believe in keeping my machines running for as long as possible, as far as is possible.

As i clearly don't understand - as a layman - what the big deal is, i started this thread to try to find out. I thought my question had been answered. It seems not.

---

### Post by buzzingrobot on 2013-10-10
Well, "the big deal" is that if you run software that no longer receives security patches then that software is, at the least, vulnerable to attacks created after support ended for that software. Browsing habits, safe surfing, and all that are fine.  But, they aren't a substitute for software patched to block a specific attack.

XP users, after its EOL, would gain some, unknowable, degree of security if they moved to even an unsupported Linux, given the reduced number of attacks targeting that OS. So, in an absolute sense, they'd be better off.  They'd certainly avoid the flood of XP attacks we're likely going to see after XP support ends. (I'd also bet we will see scammers pushing $49.95 "lifetime security" kits for XP, too.)

Whether on old XP machine can run any modern Linux desktop depends, of course, on the hardware.  Only one way to find out.  If that old machine really can't run Linux, then their best option is to unplug it from the net.

---

### Post by deadflowr on 2013-10-10
> **Hylas de Niall said:**
> Not at all.

All my machines are running up-to-date Debian derivatives.

Rather than trying to encourage others to use unsupported OS's I was hoping to help assure them that their old XP machines - and there are very many of those which may be as much as ten years old - need not be sent to the dumpster. Such machines couldn't even run the lightweight spins of recent releases, as you know.

So what are those folks's options for replacing XP? A modern, command-line only Ubuntu (which is likely all many of those machines could run) to replace a full (though defunct) GUI in XP - or an older version of a more secure system than they had?

If you would rather let folk believe their old machines are of no more use when XP reaches OEL next April, with respect that's up to you. I believe in keeping my machines running for as long as possible, as far as is possible.

As i clearly don't understand - as a layman - what the big deal is, i started this thread to try to find out. I thought my question had been answered. It seems not.

If a machine can handle XP, then there is no reason it couldn't handle even the most lightest desktop variant of Ubuntu, or Debian.
A ten year old machine is still within the Pentium 4 era. Which is still plenty capable with modern Os's.

Now a machine from 15 to 20 years back may have some troubles.
But from my own recent experience, I know you run Lubuntu on a Pentium 3 based system, quite well.

It's less that the machines cannot handle the newest versions of the Os's, it is that the machines are more likely to fall apart from age.

---

### Post by cariboo on 2013-10-10
This thread has veered way off topic. Can we get it back on topic again.

---

### Post by newb85 on 2013-10-10
> **buzzingrobot said:**
> XP users, after its EOL, would gain some, unknowable, degree of security if they moved to even an unsupported Linux, given the reduced number of attacks targeting that OS.   That's an interesting point.  Microsoft's ten-year life cycle tends to make one forget Windows has an EOL.  (At least those of us who aren't responsible for Windows machines :p)

---

### Post by Hylas de Niall on 2013-10-11
> **buzzingrobot said:**
> Well, "the big deal" is that if you run software that no longer receives security patches then that software is, at the least, vulnerable to attacks created after support ended for that software. Browsing habits, safe surfing, and all that are fine.  But, they aren't a substitute for software patched to block a specific attack.

XP users, after its EOL, would gain some, unknowable, degree of security if they moved to even an unsupported Linux, given the reduced number of attacks targeting that OS. So, in an absolute sense, they'd be better off.  They'd certainly avoid the flood of XP attacks we're likely going to see after XP support ends. (I'd also bet we will see scammers pushing $49.95 "lifetime security" kits for XP, too.)

Whether on old XP machine can run any modern Linux desktop depends, of course, on the hardware.  Only one way to find out.  If that old machine really can't run Linux, then their best option is to unplug it from the net.

And that's all i was trying to establish. Thank you :)

---

