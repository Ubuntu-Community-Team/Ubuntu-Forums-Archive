---
title: "*rant warning* HELP: How do I come to terms with systemd?"
date: 2024-06-21
forum: Ubuntu, Linux and OS Chat
---

### Post by egorFiNE on 2024-06-21
[COLOR=#252C2F][FONT=&amp][FONT=inherit][FONT=inherit][FONT=inherit]Help me get over it.

I hate it. I hate everything about it. 

I'm far from being a luddite either: I love new things. Upgrading dependencies in my company is done daily. I run bleeing edge hardware and software since nineties and ubuntu since version 6.

But all I can see in systemd is cancer. It seems to me they are on a constant lookout for the most stable things that worked perfectly well for **decades** - and they break it. 

I do not understand `ps ax` anymore.

Having said that, I have to admit that there are many serious arguments in favor of systemd infrastructure. Some of the classic systemd complaints are no longer true and some of reasons why systemd things were invented are indeed valid. systemd as PID1 was a good idea. I like it. I won't go back to sysv scripts.

Problem is, even PID1 is swelling. We now have timers, mounts, socket activations and other things I couldn't even think of would become a part of init system. Up next: systemd-ls. Don't cringe yet: nobody could have imagined systemd going after `sudo` or tmp files garbage collector either.

Now, I perfectly realize I cannot be smarter than the absolute majority of Linux distro devs. They choose systemd-* time and again despite the fact that it goes against everything Linux was loved for. systemd-$SOMETHING is notoriously known to be so much broken yet it is included in the default Ubuntu install release after release.

So my question is: how do I get over it and come to terms with the world of ever growing systemd?

I'm sure I'm not the only one who shared this view and changed and came to love (tolerate) systemd. Please help me change.

PS: No, running a systemd-free distro is not an option anymore in 2024.
PPS: Is [this]("https://gist.github.com/egorFiNE/30ee7910ca4b7b9b706d385e432764e0") is the right approach?
[/FONT]
[/FONT]
[/FONT]
[/FONT][/COLOR]

---

### Post by Tadaen_Sylvermane on 2024-06-21
While there are many perspectives on the whole systemd thing, and forward movement in general none are particularly right or wrong. Let's look at it from a practical point of view.

--

Does systemd in this case have any real effect on your operation of your computer at home? (this is mainly home users around here so I target them). Does it even matter when 99.99% of users don't even have any reason to interact directly with it?

Yes things are bloating a bit, but hardware is growing exponentially faster. At what point is worrying about "bloat" a concern worth any thought in normal day to day operation?

Growing pains are normal. People are generally resistant to change. While the majority of us are armchair enthusiasts with Linux, and in some cases at the professional level do any of us really fully understand this stuff? Linux has been taken over by big business, we just benefit from it. Linux users outside of the professional world are little more than a rounding error. As such do we have any real right to demand or fight against something that has probably had countless studies and changes done to it by these same companies who have infinitely more of their livelihood riding on this software?

If systemd in this case is such a big problem there is nothing stopping people from forking everything and going down another path with it. Divergence happens. The problem is that there simply aren't enough people interested in removing systemd for this to work. Is it really okay for that small minority to demand that the companies who primarily financially back the software we all use daily add this extra work for themselves with little to no real benefit to them?

--

I don't have a personal preference. I just use what I use. I don't interact with systemd myself outside of an initial installation where I put my backup service  and timer in place. So I don't have a dog in the fight or argument. But these things are philosophical and can get emotional for some reason. Take the emotion out of the decision. Look at it strictly from a practical point of view. I neither hate it nor like it. It makes my computer work, that is all I need to know.

---

### Post by #&amp;thj^% on 2024-06-21
> **egorFiNE said:**
> Help me get over it.

I hate it. I hate everything about it. 


Some other suggestions then: [https://itsfoss.com/systemd-free-distros/](https://itsfoss.com/systemd-free-distros/)

I remember feeling the very same way you now feel, but i chose to go along with it. (Now it's not so bad for my use)

Tadaen_Sylvermane has a fresh persepctive above.

---

### Post by HermanAB on 2024-06-21
Simple, install Devuan and go on with your life.

---

### Post by ajgreeny on 2024-06-21
*Thread moved to **Ubuntu, Linux and OS Chat**.* which is more appropriate for the discussion and should be a better fit.

---

### Post by grahammechanical on 2024-06-21
You have identified the reason a lot of Debian developers did not want systemd to be part of Debian. There was a big argument about it. Redhat is the developer of systemd and Redhat developers working on Debian pushed for its adoption. Ubuntu developers working on Debian were ordered to stay out of it. The Redhat developers won the argument and the Debian developers who lost forked the code and produced Devuan.

Ubuntu inherited systemd from Debian.

Regards

---

### Post by TheFu on 2024-06-21
For large installations, systemd solves (or more accurately, tries to solve) issues related to boot time by doing things in parallel that weren't done in parallel before.  For small installation with just a few HDDs connected and just a few NICs, this was never really an issue, but in some corporate environments, I've seen hundreds of disks mounted over a SAN to a single server. Booting those systems tool forever.

Additionally, the udev development team was burned out, so they found some people (the systemd folks) to take over their project.  Since nobody else stepped up to do the work to keep udev going separately, it was only reasonable for the systemd guys to put their particular "stamp" of design ideas into udev.  

Think of the init and udev systems like a 200 yr old house that had been redone every 50 yrs or so.  You never know what's behind the walls until you open them up. Sometimes when looking behind the walls, you find treasures and sometimes you find a termite colony that has been ignored, but needs to be removed.  As with all pest control companies, they each have different ideas for how to solve issues and as systemd started interfacing with more and more of the init things inside Linux, I'm positive they found some nasty code and other beautiful stuff.  

Sometimes when you find a post behind a wall, it isn't easy to tell if it is just a spacer/decorative or if it is what holds that section of the house up.  Same with Linux code. The people who created all that old code weren't dumb, but perhaps they didn't clearly document things in a way that younger people would understand?  The loss of "institutional knowledge" happens everywhere. It happened with init and with X/Windows.  Sometimes rather than try to modify code that you don't fully understand, it is better to start over and bring consistency to a new, active, project for code styles, documentation, and interfaces.

All that sound reasonable?

Now for my real feelings.  I think systemd is an abomination that must be stopped.  I disagree with most of the added interfaces and bloat.  I've deathly fearful that we'll never really get away from systemd in my lifetime as it takes on more and more whims for what could be possible.  I'm actually more afraid of Canonical's Snap packages, but that's a different issue.  

OTOH, journald is a work of art. That is part of the systemd project and it makes so many things related to logging so much better.  About a year ago, I came across a distro that wasn't creating text-based log files in /var/log/ any more.  At first, it was a little shocking, then I used journalctl to get the information I needed and found it was all there, stored more efficiently, easier to find just the stuff I wanted, and very easy to setup a remote log server.

I was happy with init.  I understood how to make the start/stop/status/restart scripts and how to handle dependencies.  It all "just worked" for me and for my needs. I miss it.  I find the systemd Unit files obtuse and hard to get to do what I intend. Seems there are too many options for dependencies built in.  Perhaps someone with a better understanding for specifying the dependencies in Unit files would make it do exactly what they desire.  I've never had that luck.

I'd add netplan yaml files to the list of "what the heck were they thinking" list.  It took them 2 yrs after it became the default for non-trivial network setups to be possible AND actually work.  Because it is tied into the cloud-init too, which is another abomination, it is now a core requirement for any Ubuntu Server.  A little over a year ago I started moving from Ubuntu to other distros in a concerted way. Started with a desktop and it has been fine.  My new servers and upgrades as Ubuntu system support ends will be migrating to alternate, but stable, distributions to avoid snaps and netplan.  I'd like to avoid systemd-resolved and systemd-timed as well. Today, I manually purge those last 2 and install tools that actually work.  

Perhaps in 10 more years, systemd will be stable enough for use in production.  It took about 12 yrs for PulseAudio to become stable ... and now it is being replaced.  Hopefully, we don't have to wait so long for systemd to be yanked from distros and for the Gnome project to stop dumbing down and bloating up their project.

I don't know if you feel better, but I do. Thanks!

---

### Post by #&amp;thj^% on 2024-06-22
> **TheFu said:**
> 

I don't know if you feel better, but I do. Thanks!

I needed this smile today, I love a well said rant.

---

### Post by VMC on 2024-06-22
..."I'm actually more afraid of Canonical's Snap packages, but that's a different issue"  ** Yes** &
"OTOH, journald is a work of art."  **Yes**!

---

### Post by egorFiNE on 2024-06-24
Thank you for the insightful reply!

> **Tadaen_Sylvermane said:**
> At what point is worrying about "bloat" a concern worth any thought in normal day to day operation?

When I have a server or an instance and I have no idea what it is busy with. When I type ps ax and I cannot comprehend what's up. When I pull my hair out for an hour trying to move sshd to other port only to discover that they have changed sshd to socket activation and did that sneakily in a multitude of ways.

> **Tadaen_Sylvermane said:**
> 
do any of us really fully understand this stuff? 


Good point. One of the things that hurts is that I used to understand like everything in Linux. Before that - everything in MS-DOS. Everything in programming. But as systems grow and complexity grows a single cannot even be expected to understand everything in any single package except perhaps gzip. So following this line of thinking I guess maybe it's time to give up on the notion that an OS has to be transparent to me and `ps ax` along with networking configuration and cronjobs has to make sense to me. What do you think? 

> **Tadaen_Sylvermane said:**
> 
companies who have infinitely more of their livelihood riding on this software?


Well *I am* a company having livelihood on Linux. Not until recently I have managed a few thousands of physical servers. This is why I want insight and transparency because a mere 1% increase in performance means a hundred more servers is now available to take on more customers.

> **Tadaen_Sylvermane said:**
> 
The problem is that there simply aren't enough people interested in removing systemd for this to work. 


And this is where we circle back to my original point: I cannot comprehend why the majority of server folks are okay with systemd cancer. Practically. Why? Netplan is worse than ifupdown and systemd-resolved has been designed like a plastic wrap left on the dashboard of a new car meant to be removed by the owner.

> **Tadaen_Sylvermane said:**
> 
But these things are philosophical and can get emotional for some reason. Take the emotion out of the decision.


True. It's just hard for me when another metastasis of systemd breaks things that both were working perfectly well and working for decades.

> **Tadaen_Sylvermane said:**
> 
Look at it strictly from a practical point of view. I neither hate it nor like it.

And that's my main take away from this conversation. Simple words, they did help me. Thank you.

---

### Post by egorFiNE on 2024-06-24
> **TheFu said:**
> For large installations, systemd solves (or more accurately, tries to solve) issues related to boot time by doing things in parallel 


I full agree that as PID1 systemd is way better than the init scripts. I won't go back to sysv init anymore. Problem is: once developers created a perfect init, they were bored and started to look around and that's precisely where bad things started to happen. 

> **TheFu said:**
> 
I've seen hundreds of disks mounted over a SAN to a single server. Booting those systems tool forever.


I had something similar in production. The trick is extremely simple: you don't bring that up with an init system. You just don't. Let the init system up the system, up the networking, start ssh and let go. Then you are free to start up your business layer in whatever ways required.

> **TheFu said:**
> 
Sometimes when you find a post behind a wall, it isn't easy to tell if it is just a spacer/decorative or if it is what holds that section of the house up.
[]
All that sound reasonable?


Very good point. 

> **TheFu said:**
> 
Now for my real feelings.  I think systemd is an abomination that must be stopped. 


Ah, we share the same feelings.  

> **TheFu said:**
> 
I'm actually more afraid of Canonical's Snap packages, but that's a different issue.  


Oh, snaps are cancer over cancer. Thankfully at this time they are just a nuisance and easy to remove from the server environment. I have no doubt in a few years they will become a bigger problem for Ubuntu because their developers won't stop, just like systemd folks won't. 

> **TheFu said:**
> 
OTOH, journald is a work of art. 


I see no reason to run it while depriving myself of the decades of experience the world has invested in Unix command-line tools (awk/grep/etc). Text logs are comprehensible and searchable in countless ways. journalctl has counterintuitive things going on. IIRC, `journalctl -f` is not enough to follow logs, you have to ask it more nicely than that. I may be wrong on this one, but a problem of a similar vibe killed my desire to look into it further when I have tried to embrace it. 

> **TheFu said:**
> 
found it was all there, stored more efficiently, easier to find just the stuff I wanted, and very easy to setup a remote log server.


I fully agree with you that this might well be the case.

However journald, like the rest of systemd-* was a solution in search of a problem that didn't exist in the first place. Remote syslog was a thing for decades and it does the job. 

> **TheFu said:**
> 
Seems there are too many options for dependencies built in.


This was swollen to a point they had to come up with special tools to analyze and debug dependencies. Incomprehensible, opaque.

> **TheFu said:**
> 
I'd add netplan yaml files to the list of "what the heck were they thinking" list. 


That's my main rant: I genuinely don't understand why would they choose a solution that is so much worse than the existing one. And force it on everyone. 

> **TheFu said:**
> 
it is now a core requirement for any Ubuntu Server. 


I'm not sure about that. See my linked script: netplan is easily removed and replaced with ifupdown package and it does work. 

> **TheFu said:**
> 
I'd like to avoid systemd-resolved and systemd-timed as well. Today, I manually purge those last 2 and install tools that actually work. 
 

Those two packages were designed to be destroyed. Like a purposely left packaging wrap on the dashboard of a new car when delivered to the owner.

> **TheFu said:**
> 
PulseAudio to become stable ... and now it is being replaced. 


That's the problem with kids: once something work it means it's boring and boring has to be messed with. Yeah, I sound like a hardcore luddite, which I am definitely not at all. Again, I like the core systemd as PID1. 

> **TheFu said:**
> 
Hopefully, we don't have to wait so long for systemd to be yanked from distros 


LP and the team are inevitably going to grow up and fingers crossed systemd will be abandoned as well. Fingers crossed.

> **TheFu said:**
> 
I don't know if you feel better, but I do. Thanks!

Thank you!

---

### Post by 909mjolnir on 2024-07-01
I had pretty good results with recent and modern distros without systemd.  Some of them were advertised as being better without it, others offered it as a alternative boot option.  Either way, I used those systems of Linux without problems.  

The only thing that gets me is I don't really yet know how to manage system tasks without it.  
Nevertheless, from what I've read, systemd thrashes the hard drive, etcetera.  
There's actually a modern movement to ditch systemd, and it's caught on, so I think we'll all be OK.  

I think even MX Linux ships with a kernel mode without systemd.  
I think I maybe also ran Devuan without systemd.  
It's fine, just do your homework about it.

---

### Post by TheFu on 2024-07-02
Users can be grouped into 2 types.

Home users who only have to maintain a few systems, usually less than 5 
and
all other users who may be corporate or home or for non-profit organizations with hundreds to many thousands of systems.

If you need to manage just a few systems, then you can do it all yourself and you can pick from any distros you like, or even create your own.  The effort in doing this won't ruin your vacation.

But if you have a non-trivial number of systems to maintain, then you'll need help from people who are either paid or volunteers for the same organization.  Those people want/need to have skills that translates into a paycheck and putting kids through college along with all the other necessary things locally required.  Heck, the last 25 yrs. I've been paying more in taxes every year than I was paid in salary for my first career job just out of University (and it was a good job in my field of engineering).

So there are effectively "hobbyist" and professionals.  Hobbyists can go their own way and it won't impact the world, their job, their ability to pay taxes, etc.  Everyone else has limited "life" bandwidth and has to prioritize where they will waste money/time.  For me, I'm willing to have a single 1-off system for my personal use, but every other system for which I'm responsible needs to be as standard as possible.  As much as I will complain about systemd, it has won the init choice and every professional will expect to use it on every "server" system.

Of course, there are exceptions, but those happen 1/1000th of the time.  There are companies that only use Gentoo or Arch, but that's because their owner/CTO made a choice, often decades ago about doing that ... or they have such large scale deployments that the distro used was always going to be customized for their needs (google/facebook).

So, for all my rants about snaps and systemd  AND my claims that I won't be using it on desktops, that is really just 1 system.  My production servers will stay on 1 of the main 5 distros deployed in corporations.  Today, that is a mix of Ubuntu and Debian, with more and more Debian deployments happening as systems are upgraded.  Debian uses systemd, but it doesn't mandate snaps.

There are places where I think using snap packages **is** very smart.  That's for IoT device deployments.  If you are selling a small computing device and need to easily maintain the OS and programs it can run, using snaps is a smart thing compared to almost any other available option.  I have a few IoT-like devices (raspberry pi computers running a media center player).  They are patched weekly for much of the year and it is a bit of a hassle compared to doing nothing at all.  In the fall when life gets really busy, I stop updating those player devices for a few months if they are working great already.  Right now they are all working really, really, really well.
```
$ uptime
 11:48:41 up 11 days, 17:24,  1 user,  load average: 0.43, 0.39, 0.36
```
We had some heat-related power outages here ... er ... 11 days ago. Thankfully, power has been perfect since. Looks like the power company used those few days of opportunity to do maintenance across lots of other nearby equipment.  We've have longer, hotter, days all last week without even a chirp of a power hiccup.

Systemd has lots of controls that can be enabled or tuned.  If you think it is "thrashing" your storage, why not fix it by using caches?  You can even turn off systemd touching the storage, except to read unit files. All logs and temp files can go to pseudo-file systems (i.e. RAM) and you can limit how much RAM can be used.  Systemd has lots of documentation explaining these things.

---

### Post by egorFiNE on 2024-07-02
> **TheFu said:**
> Users can be grouped into 2 types.
But if you have a non-trivial number of systems to maintain, then you'll need help from people who are either paid or volunteers for the same organization.  Those people want/need to have skills that translates into a paycheck and putting kids through college along with all the other necessary things locally required. 


And this is where systemd comes in. The people behind it sure made it complicated enough to achieve a job security for themselves. Consequentially, every sysadmin who somehow decided to go with systemd timers instead of cron, will now have to learn this and of course being a more complicated technology, systemd requires more billable time to manage the servers. So, job security and all. Complicate all the things!


> **TheFu said:**
> Everyone else has limited "life" bandwidth and has to prioritize where they will waste money/time.

This is why I'm in rage every time I see another systemd metastasis. Okay, I understand its developer had to secure their job by growing another monster, but why is it now shoved down my throat so that now I have to spend more time supporting servers instead of doing my job or spending time with kids?

> **TheFu said:**
> 
As much as I will complain about systemd, it has won the init choice and every professional will expect to use it on every "server" system.


systemd as PID1, sure. It's a battle totally lost a long time ago, so yes. I'm not gonna go back to sysv init myself.

It's absolutely not the same with systemd-everything-else which typically is a pure evil, ranging from systemd-resolved to journald.

> **TheFu said:**
> 
If you think it is "thrashing" your storage, why not fix it by using caches? 


The best fix would be not to break things in the first place. crontabs worked **for decades,** just like sshd was perfectly capable of listening on its own port.

> **TheFu said:**
> 
Systemd has lots of documentation explaining these things.

See, I don't want to read the documentation on a new LP's masterpiece. I don't want anything from their team to exist at all. They have demonstrated their approaches and attitude so many times that it's not feasible to expect any good product coming from that source. All they do is craft a solution and then create a problem for the solution by breaking something that actually worked. I don't know of any product except /usr/sbin/systemd that is actually a good thing and not a monster.

> **TheFu said:**
> 
There are places where I think using snap packages **is** very smart.  That's for IoT device deployments.  If you are selling a small computing device and need to easily maintain the OS and programs it can run, using snaps is a smart thing compared to almost any other available option. 


Rant aside, now I genuinely want to know more. I have very limited understanding of what are they. Could you please elaborate more on that, how are they good for the job?

---

### Post by egorFiNE on 2024-07-02
> **909mjolnir said:**
> 
There's actually a modern movement to ditch systemd, and it's caught on, so I think we'll all be OK. 

I don't think there is. I cannot envision Ubuntu or Fedora making things simpler, because simple things are for old people and they don't generate income in consulting fees.

Besides, there is already a generation of people grown up in a systemd-only world, just like young people in russia have never seen the world without putin. And these kids, they totally believe systemd is normal, because they haven't seen better. 

Go teach unix philosophy to someone who had their logs stored in journald for their whole life...

---

### Post by 909mjolnir on 2024-07-08
Just a few days ago I was test driving ArtiX and it's pretty nice.  There's a choice of 2-4 different init's, I think s6, runit, openrc, and mabye one other.  A few other distros have those choices too.  
On the down side, I think it was Thunar or something which crashed without systemd to fall back on.  I was bummed because I like the spectre of a seriously barebones system that's ready to customize for pro audio.  Nevertheless it otherwise ran fine.  Maybe some other DE could be installed, but it was sobering that regular Thunar was choking without systemd.  

I think I tried s6 for the speedy boot time.  It was fine.  
Also, I think Devuan is non systemd too.  It was a good distro also.  ArtiX is Arch-based, Devuan is like Debian.  
I don't use them as my main system, though, due to odd errors from missing DLL's or something.  

As for Snap, why not just AppImages, instead?

---

### Post by egorFiNE on 2024-07-09
> **909mjolnir said:**
> 
Also, I think Devuan is non systemd too.


It's as close to mainstream as you can get. Unfortunately, not close enough to get security updates ASAP. 

> **909mjolnir said:**
> 
As for Snap, why not just AppImages, instead?

Why anything? Docker did the job of isolation.

---

### Post by TheFu on 2024-07-09
> **egorFiNE said:**
>  
Go teach unix philosophy to someone who had their logs stored in journald for their whole life...

Ok. read this: [https://en.wikipedia.org/wiki/Unix_philosophy](https://en.wikipedia.org/wiki/Unix_philosophy)
There are lots of YT videos on the subject too. Some look old even to me, from before I'd ever touched any computer.  AT&T has one that is a very basic introduction.  In short, it says, make tools that do one thing well, and let users build the specific tools to get the results by putting those different tools together easily, and give users the ability to automate running of those tools.

journald does logging really well.  Rather than adding in awk, grep, cut, paste, to reformat the possible output like we did with text logs (btw, text is just a very common binary format, just like journald logs are a binary format), we can ask journalctl to find and output only the things we want from the processes we want during the times we want.  That's usually better for people who don't know extended regex patterns.

---

### Post by 909mjolnir on 2024-07-09
because you just download the AppImage, enable execute and run it whenever you want it.  
it's so much easier and you only have to hold one file.

---

### Post by egorFiNE on 2024-07-10
> **909mjolnir said:**
> because you just download the AppImage, enable execute and run it whenever you want it.  
it's so much easier and you only have to hold one file.

With all its dependencies and security vulnerabilities conveniently packed together and independent of the OS and un-upgradeable. Thanks, no.

---

### Post by egorFiNE on 2024-07-10
> **TheFu said:**
> 
journald does logging really well.  Rather than adding in awk, grep, cut, paste, to reformat the possible output like we did with text logs

This is precisely what's wrong with it. We have used grep & awk (or whatever you liked) for **decades** until journald came in and stripped that possibility from us.

> **TheFu said:**
> 
we can ask journalctl to find and output only the things we want from the processes we want during the times we want.

I see it as exactly the opposite and I am strongly holding that opinion.

We could do what you describe with text logs (again, for decades and sorry for using this point so much) and we cannot do that with journalctl. Journalctl forces us into its own kingdom of search tools and paradigm instead of what worked incredibly, unbelievably well if you think about it. With text logs I can "find the things I want from the processes I want during the times I want". With journalctl I cannot because every time I try to do this, I find that it does not output everything that's greppable in the same text logs. Because - of course - that one process is called "sshd" but in fact it's "systemd" pretending to be sshd in order to make people pull their hair, so you cannot see its logs when querying systemd and vice versa. 

And lots of things of that nature.

Thankfully, journald is still optional on Ubuntu and unlike init, syslog is not going anywhere. So journald with all their cleverness can absolutely take a hike. At least for now. Once it's gone, I'm going to replace it with journalctl -f >> /var/log/system.log right away or build a syslog from sources or something. I absolutely refuse to learn its query language and then rely on its mercy to actually show me what I wanted to see and not hiding things LP thinks needs to be hidden.

Despite the fact that journald does a pretty good job being apparently convenient, it is still pure evil compared to the working solution that covered 100% of any usage scenario you can imagine.

PS: While I was writing this message I decided to tail journalctl on one of the boxes. journalctl | tail -1000 takes forever and never finishes, because somehow this Ubuntu still has logs from last autumn while text logs were properly rotated. In order to tail with journalctl I have to read the manual and maybe, *just maybe* LP and his team graciously implemented this feature. Or maybe they did not, because they deem it unnecessary.  Thing is, I don't want to learn it. And I don't want them to have any say. I have tail and I had it for ... here we go again. So, yeah.

---

### Post by TheFu on 2024-07-10
> **egorFiNE said:**
> With all its dependencies and security vulnerabilities conveniently packed together and independent of the OS and un-upgradeable. Thanks, no.

If the app isn't networked and is a single-purpose app that you use once a month, what does that matter?  
OTOH, for networked apps, those definitely need to be run under some sort of constraints.  I use a video editor that is packaged in multiple ways, but I prefer the AppImage.  Same for a MindMapping tool.  These aren't networked and seldom used.  Who cares if they have a 10 yr old copy of GTK+?  I don't.  

Plus, it is my choice, unlike so many other security issues where we have no choice.  Like these: [https://www.propublica.org/article/cyber-safety-board-never-investigated-solarwinds-breach-microsoft](https://www.propublica.org/article/cyber-safety-board-never-investigated-solarwinds-breach-microsoft)

There are few black and white answers, just shades of gray.

---

### Post by TheFu on 2024-07-10
> **egorFiNE said:**
> This is precisely what's wrong with it. We have used grep & awk (or whatever you liked) for **decades** until journald came in and stripped that possibility from us.

You can tell journalctl to output everything, then use grep, awk, sed, as much as you like.  
You can tell journalctl to do the equivalent of **tail -f**.
Is learning 2 different options REALLY that hard?  Just create an alias or a tiny script, if you must, just like we've done for getting specific information from log files for decades.

Your prior usage was limited by what those tools allowed. You don't realize that?

Systemd status/error stuff is pretty useless for the most part.  We are told just that some daemon didn't start which is certainly important, but not very useful for WHY it didn't start.  A few days ago, I was trying to figure out why lxd and lxc didn't start.  Had to change 2 things until the bugs are corrected.  Sadly, one of those things prevented rolling back to an older release because the lxd DB had been moved from v23 to v24 and that change couldn't be undone.  Once I saw that, I knew I had to force a specific version of lxd to be used.  Nowhere in the systemd status did it say *incompatible DB version (v24 being used) with a filename listed.* Not helpful. That got it to start.  Then lxc wouldn't start.  Random web-searching found a kernel boot option to use an older style of memory layout.  I have two nearly identical systems. Both lxd/lxc tools stopped working with the update.  The LXD fix worked on both, but until I set the kernel boot option, neither lxc would start.  Hard to manage lxc containers without lxc.  BTW, my redundant LAN DNS servers run inside LXC containers on 2 physically separate systems and both were down.  That makes all sorts of things break on my LAN.  Stupid snap packages.

---

### Post by egorFiNE on 2024-07-10
> **TheFu said:**
> If the app isn't networked and is a single-purpose app that you use once a month, what does that matter?  
OTOH, for networked apps, those definitely need to be run under some sort of constraints.  I use a video editor that is packaged in multiple ways, but I prefer the AppImage.  Same for a MindMapping tool.  These aren't networked and seldom used.  Who cares if they have a 10 yr old copy of GTK+?  I don't. 

Having AppImages with ancient and vulnerable GTK versions on a desktop is a straight nightmare fuel.

> **TheFu said:**
> 
There are few black and white answers, just shades of gray.

True, true.

---

### Post by egorFiNE on 2024-07-10
> **TheFu said:**
> You can tell journalctl to output everything, then use grep, awk, sed, as much as you like.

True. I'd like to go just a tiny step further and remove journald from that workflow as it is not needed here. 

> **TheFu said:**
> 
You can tell journalctl to do the equivalent of **tail -f**.

Except it has some quirks I don't fully understand. Like, it doesn't tail everything. 

> **TheFu said:**
> 
Is learning 2 different options REALLY that hard? 


Why? I don't need journald whatsoever for that. It solves a problem that did not exist and nobody called for. 

> **TheFu said:**
> 
Your prior usage was limited by what those tools allowed. You don't realize that?


Except I see it exactly as the opposite: my usage was unlimited by the tools and is now heavily limited by a tool forced down my throat. 

The hell with it. Again: thankfully it's redundant and not needed and easily removable from Ubuntu. I see no value in journald whatsoever.

---

### Post by TheFu on 2024-07-10
First hint, use **journalctl**, not journald.  Bet that will help a bunch.

Second hint, **journalctl -f**.

I get that complaining can feel good. I do it a bunch.  Often, I'm taught things to make many of my complaints go away.

---

### Post by 909mjolnir on 2024-07-11
It's not hard to update an AppImage:  

1) download the new AppImage (version 2.0)
2) test to make sure it works (enable execution)
3) delete the old AppImage
4) put the AppImage where you want it.  DONE--that's it.  

Now, when you upgrade your system, you don't have DLL hell issues.  
To me, that's worth it.  Hands down.

5) if the program fails, just select it and delete it--DONE!  so easy.

---

### Post by egorFiNE on 2024-07-11
> **909mjolnir said:**
> It's not hard to update an AppImage:  

1) download the new AppImage (version 2.0)

With the same ancient libraries full of security vulnerabilities because it's convenient for the developer.

> **909mjolnir said:**
> Now, when you upgrade your system, you don't have DLL hell issues.  


Except it's the opposite: you now have an endless abyss of DLL hell issues. Because instead of a single supported and updated system shared library you now have them all over the place, all random versions with random build settings.

---

### Post by egorFiNE on 2024-07-11
> **TheFu said:**
> Second hint, **journalctl -f**.

You are missing my point. My point is that everything worked just fine for decades. I don't need journald, it solves no problem, thus it deserves no learning at all. And 

> **TheFu said:**
> I get that complaining can feel good. I do it a bunch.  Often, I'm taught things to make many of my complaints go away.

I'd love for journald to go away instead. Again, because it's an irritation and an artificial bump in the otherwise flat road of logging.

Complaining makes me feel bad actually. I'm more agitated after discussing systemd cancer than just ignoring it. I hate those kids' creation with passion.

---

### Post by TheFu on 2024-07-11
> **egorFiNE said:**
> With the same ancient libraries full of security vulnerabilities because it's convenient for the developer.
Depends on the developer. Some choose to use the latest versions of support libraries that haven't been included in distros yet.

I was a commercial developer for over a decade. There are smart reasons developers do things and there are dumb reasons. If you aren't in the room when some change is discussed and don't have access to the change board documents, you'll never really know what the considerations were.  For example, where I worked, I was on the development lead with about 20 developers. Besides coding myself, I assigned features and bugs to be worked to the team members. During the prioritization of anything, we'd consider how many customers it would impact, whether our sales team would be impacted, and how much things would cost to implement. There were other things involved, but we didn't upgrade third-party libraries on a whim. It was always a question of impact and risk.  Some of our clients complained whenever any update was required.  Others always wanted to be on the latest because they confused "new" with "bug free" - which is never the real situation. New just means "new bugs" that nobody has found yet.   

Some customers begged us to help them only run the number of purchased license copies they'd bought. Others thought that any restriction was unnecessary and an added hassle.  It was clear by legal jurisdiction which clients were where.  US-based clients wanted help with license restrictions.  Asian companies didn't.

I recall one feature was added specifically to prevent batch versions of our software from being used for web sites.  The start up of the batch processing was already slow - perhaps 45 seconds and this was on IBM SP AIX servers, so not little PC servers.  The startup delay in the batch system made website use impractical, then we introduced a new "web-engine" license type that cost 100x what a single fat client cost.  The engine would start and make connections, but not die. It had an API for handling requests in a multi-threaded way.  Lots of MT code is expensive to create and debug.  At the time, very few programmers had the expertise to write MT code.  We also added a license type for batch processing which was less cost, but had a long startup period.  Some businesses still use batch processing overnight, even these days.

> **egorFiNE said:**
> 
Except it's the opposite: you now have an endless abyss of DLL hell issues. Because instead of a single supported and updated system shared library you now have them all over the place, all random versions with random build settings.

What?  Looks as though you have no idea how AppImages work at all.  Might want to correct that issue.

---

### Post by denz on 2024-07-11
Interesting, so Red Hat has more say than Ubuntu??

---

### Post by 909mjolnir on 2024-07-11
Not all devs pack old stuff into the AppImages.  They just pack stuff together is all, so you don't have to entangle your system.  And if the app has functionality and works right, there's no reason to complain.  Which AppImage is giving you a hard time?

---

### Post by currentshaft on 2024-07-11
You think systemd is bad? How about the complete POS that is snap?

I install updates today, suddenly my firewall has cupsd listening on port 631. Strange, I thought, because I uninstalled cupsd when I provisioned the machine. apt-get purge "cups*" ... sure enough it's not installed. Yet there's a cupsd process listening.

So snap just decided to install a new networking listening daemon and enable it, without any prompt or confirmation.

Needless to say, I am removing this dangerous software from all of my computers.

---

### Post by egorFiNE on 2024-07-12
> **TheFu said:**
> During the prioritization of anything, we'd consider how many customers it would impact

And that inevitably leads to "never upgrade anything" attitude, because shipping features always has priority over upgrading dependencies and it's perfectly clear why.

Except when it becomes critical to update a library and it's plain impossible because the current one lags two major versions behind, is 12 years old and requires upgrading virtually everything else which calls for a major refactoring of the project with substantial risks and new bugs that actually will impact customers.

Security patches? Even less priority, because security is totally invisible, unmeasurable and not sellable*.

In my companies I require devs to track dependencies daily. Granted, in a world of frontend web development it takes all the running you can do to keep in the same place, but we upgrade the OS-related things as well. And sure enough I strongly resist bundling dependencies for our desktop product in an AppImage or snap or flatpak or whatever is in trend today; because this way we're doomed: no one will ever upgrade glibc or opencv. Running on the bare host OS kind of forces our business to not lag behind.

> **TheFu said:**
> Some of our clients complained whenever any update was required.

Sure, because they're in the same position: why upgrade if it works. Hence we have Ubuntu LTS with 12 years of support after which the project requiring ancient OS version is practically doomed. On the extreme side of things we have American banks who wouldn't even consider any software unless it's already EOL.

[SIZE=1]* Of course you can put whatever words you want on the web about security and make it a selling point. Absolutely doesn't have to be true. Again, unmeasurable.[/SIZE]

---

### Post by egorFiNE on 2024-07-12
> **909mjolnir said:**
> Not all devs pack old stuff into the AppImages.  They just pack stuff together is all, so you don't have to entangle your system. 

And that entangles the system because I now have gigabytes of the same glibc in different versions. And I don't trust app developers to properly track glibc changes and security patches. No one should, not even the developers should trust themselves doing that. 

 > **909mjolnir said:**
> And if the app has functionality and works right, there's no reason to complain. 

Until there is and it's too late. I'm talking about security vulnerabilities carefully packed into a plethora of different AppImages on a single host. This is a convenient way to make sure that a properly updated and secure host OS system has no say in the vulnerabilities being exploited.

---

### Post by egorFiNE on 2024-07-12
> **currentshaft said:**
> 
Needless to say, I am removing this dangerous software from all of my computers.

My script does that. Forget snap.

---

### Post by lammert-nijhof on 2024-07-17
I love systemd concept, that is how you design a modern kernel, but systemd complicates software design. 

 I have my doubts about its current implementation, because there are maintainers, that miss some of the issues of parallel processing. Too often I seem to run in time dependent issues during the system start-up.  For a long time in Ubuntu 24.04 and 24.10 on my Ryzen CPU (4C4T; 3.7GHz), the first boot failed, and the second boot succeeded. This type of errors occurs, when people did miss to deal correctly with data shared between two processes or threads. In this case I expect the mismatch was between VirtualBox 7.0.18 kernel modules and the 6.8 Linux kernel. 

I have some feeling for these types of issues, because I designed an OS for 16-bit minicomputers almost 50 years ago.  And yes, my age is halfway between Trump and Biden and the photo is from 1946 :)

---

### Post by #&amp;thj^% on 2024-07-17
> **lammert-nijhof said:**
> I love systemd concept, that is how you design a modern kernel, but systemd complicates software design. 


+1
But just like all software it has it's strengths and weakness. We just do our best to stay on top of things.

As I've said earlier I flat hated it at first, now I've just embraced it and push forward... There is plenty of drama world wide as it is, no need to borrow anymore.

---

### Post by egorFiNE on 2024-07-23
> **1fallen said:**
> +1
As I've said earlier I flat hated it at first, now I've just embraced it and push forward... 

systemd itself is finally a nice piece of software and LP's concerns about PID1 were totally legit.

The problem with systemd is the metastasis they have spread throughout the ecosystem. It's almost like the developers are actively looking for things to destroy. resolved, timesync, timers, run0 and others are just plain cancer and products of the incredibly defiant attitude started and promoted by LP. Again, those are replacement for things that worked perfectly well for decades.

---

