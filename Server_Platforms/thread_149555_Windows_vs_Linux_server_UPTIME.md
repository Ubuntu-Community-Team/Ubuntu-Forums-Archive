---
title: "Windows vs Linux server UPTIME"
date: 2006-03-24
forum: Server Platforms
---

### Post by ashrack on 2006-03-24
I've already asked this on a Windows dedicated forum but strangely received no answer:???: 

I fail to see how can a WINDOWS SERVER have an uptime of 6months?? Since just installing those Windows Updates requires a restart at least once per 2months...

---

### Post by dermotti on 2006-03-24
Well, you could have a cluster. So you update one server at a time. So the downtime is transparant to the end-user.

---

### Post by gmclachl on 2006-03-24
AFAIK Windows won't count a reboot from having to install updates as downtime. So their figures are flawed. 

George

---

### Post by LordHunter317 on 2006-03-24
[QUOTE=gmclachl]AFAIK Windows won't count a reboot from having to install updates as downtime. So their figures are flawed. 

George[/QUOTE]Uhh yes, they do.  What the hell would ever give you that idea?

First, not all updates that are released *once a month* require a reboot.

Second, on Windows or Linux or any other OS, if you want 100% uptime, you use a cluster.  End of story.  Then, the uptime of a single box is generally rather meaningless.

---

### Post by gmclachl on 2006-03-24
I heard it on a podcast so it must be true :-#

---

### Post by peanut butter on 2006-03-24
an ibm sponsored survey says that linux has less incidents but it takes longer to resolve them. the results are somewhere on thispage
[URL="http://www-1.ibm.com/linux/competitive/windowsToLinux.shtml"]
http://www-1.ibm.com/linux/competitive/windowsToLinux.shtml[/URL]

---

### Post by ashrack on 2006-03-26
[QUOTE=LordHunter317]Uhh yes, they do.  What the hell would ever give you that idea?

First, not all updates that are released *once a month* require a reboot.[/quote]
Almost every 2months I must restart Win2k3 server for them updates. That is way I usually install them only when the server needs a restart.What is the worse thing WU wont even tell U if the update you are about to DL will require a restart

> Second, on Windows or Linux or any other OS, if you want 100% uptime, you use a cluster.  End of story.  Then, the uptime of a single box is generally rather meaningless.
Im only interested in how can surveys compare Windows vs Linux uptime if Windows must be restarted once per 2months just for them updates??

---

### Post by LordHunter317 on 2006-03-26
[QUOTE=ashrack]Almost every 2months I must restart Win2k3 server for them updates.[/quote]My point is they come out once a month, so barring huge security issues, that's the maximum frequency of reboots.  12 a year.

> What is the worse thing WU wont even tell U if the update you are about to DL will require a restartA competent administrator would look up the issues online, which normally tell you.  WU does tell you that.

> Im only interested in how can surveys compare Windows vs Linux uptime if Windows must be restarted once per 2months just for them updates??Linux must be restarted on similiar intervals, frequently.

And as I said, they're looking at specific installations and with a cluster on almost any OS, 100% uptime is possible.

---

### Post by ashrack on 2006-03-26
[QUOTE=LordHunter317]My point is they come out once a month, so barring huge security issues, that's the maximum frequency of reboots.  12 a year.[/quote]
So the UPTIME that magazines mesaure is not the total uptime at all. I thought when they say a LINUX os has an uptime of ex.:2years whilst a Windows os has it around eg.:1.5 years it means that they were UP without any reboots and stuff like that. Am I correct in this logic?

> A competent administrator would look up the issues online, which normally tell you.  WU does tell you that.
WU doesn't tell U. WU only says that the UPDATE might require a restart. Which WU says for nearly half of the UPDATES. And lots of the updates that say they might require a restart DON'T!!! SO I quess the only thing that U really can do is look up on the internet?

> Linux must be restarted on similiar intervals, frequently.
Why?

---

### Post by LordHunter317 on 2006-03-26
[QUOTE=ashrack]So the UPTIME that magazines mesaure is not the total uptime at all.[/quote]No, it is.  But you're assuming those installations went patched (they very well may not have).

You're also assuming they're looking at single boxes.  They're probably not.  If they're looking at a cluster, you track the uptime of the entire cluster, which means every node in the cluster must fail for it to be down.

> Am I correct in this logic?Yes.  But that's meaningless anyway, which is besides the point.  I don't care if the box is still up and Apache went down.  Means nothing to me.

> WU doesn't tell U.Yes, it tells you the KB number for all the updates.

>  WU only says that the UPDATE might require a restart. Which WU says for nearly half of the UPDATES.I never said it did.

> And lots of the updates that say they might require a restart DON'T!!!Right, because they require a restart only in certain configurations.

> SO I quess the only thing that U really can do is look up on the internet?Which is what I said.  But if you're too incompetent to manage that, then you have no business managing computers.

[quoteWhy?[/QUOTE]Kernel updates.  On certain installations, it's policy anyway for core updates and frequently eaiser and safer.

And as I said, if I have to shut all my services down to provide a patch to them, my uptime just went to zero even if the box wasn't rebooted.  The uptime of the box isn't important, the uptime of the services are.  Unfortunately, no one measures that.

---

### Post by anti-net on 2006-03-26
You'd be suprised how many admins don't update there services and just hope for the best.

---

### Post by skirkpatrick on 2006-03-26
It also depends on what your server is doing and where it is located.  My RH8 server has only been rebooted once in the last year (I accidently hit the reset button of it instead of the machine next to it) and I haven't had to restart a service that entire time.  That machine is behind my router/NAT, is a Samba server for music/videos/misc for my house, and runs Apache and MySQL which gets used at least a couple of times a week.  Ever since Redhat quit supporting RH8, I haven't updated it as it is working and I haven't needed to worry about security updates.

If I remember correctly (and I may not), the longest uptime tracked on a Linux server is for a server that is running kernel 1.x on a 286 and is nothing more than a DNS server.

---

### Post by localzuk on 2006-03-26
[QUOTE=ashrack]So the UPTIME that magazines mesaure is not the total uptime at all. I thought when they say a LINUX os has an uptime of ex.:2years whilst a Windows os has it around eg.:1.5 years it means that they were UP without any reboots and stuff like that. Am I correct in this logic?
[/quote]

They probably mean that in a certain time period - say 2.2 years, the Windows box has been up 1.5 years and Linux 2 years (those numbers are more than likely *way* out

> 
WU doesn't tell U. WU only says that the UPDATE might require a restart. Which WU says for nearly half of the UPDATES. And lots of the updates that say they might require a restart DON'T!!! SO I quess the only thing that U really can do is look up on the internet?


Windows Update informs you of what the patch is fixing, so you can research it on the Knowledgebase site for the possibility of needing a restart. The reason some updates require a restart and others don't (even though it says it might need one) is down to the particular set of components you have installed on your windows box.
> 
Why?
Kernel updates, HAL updates - there are a variety of parts of a linux distro that need a full restart to update.

---

### Post by localzuk on 2006-03-26
> 
And as I said, if I have to shut all my services down to provide a patch to them, my uptime just went to zero even if the box wasn't rebooted. The uptime of the box isn't important, the uptime of the services are. Unfortunately, no one measures that.


This is true but again it would be a red herring really - as that would be measuring the uptime of the specific service, on that specific distro, rather than the uptime of a linux distro.

So if this was measured, you would end up with a lot of different values, depending on a lot of variables.

---

### Post by LordHunter317 on 2006-03-26
[QUOTE=localzuk]Kernel updates, HAL updates - there are a variety of parts of a linux distro that need a full restart to update.[/QUOTE]Strictly speaking, the only thing that requires a system restart is the kernel.

> This is true but again it would be a red herring really - as that would be measuring the uptime of the specific service, on that specific distro, rather than the uptime of a linux distro.No, it isn't.  It's the only interesting parameter.  The red herring is trying to measure the uptime of a distro; it's a totally meaningless value.

---

### Post by localzuk on 2006-03-26
> 
No, it isn't. It's the only interesting parameter. The red herring is trying to measure the uptime of a distro; it's a totally meaningless value.


But do you take into account the uptime of the distro when measuring it? If so, then measuring the distro's uptime is not a red herring. What I am trying to say is that in order to measure the uptime of a specific service, you must take into account all its dependencies. This would vary depending on the distro so would not be an easily benchmarkable tool. For practical usage it is only specific to your environment, but then we aren't discussing the practicalities of uptime measurement here - more their usage as a benchmarking scheme.

---

### Post by LordHunter317 on 2006-03-26
Vbulletin makes me sad.

---

### Post by LordHunter317 on 2006-03-26
[QUOTE=localzuk]But do you take into account the uptime of the distro when measuring it?[/quote]No.  As I said, it means absolutely nothing.   I don't even know how to define that.

> If so, then measuring the distro's uptime is not a red herring.Non-sequitur, circular logic.  Something isn't a red herring simply because we measure it?  And because we measure something, it must not be a red herring?

> What I am trying to say is that in order to measure the uptime of a specific service, you must take into account all its dependencies.No, you don't.  Either the service is up or down.  Why it went down is irrelevant, as is what caused it to go down.

> This would vary depending on the distro so would not be an easily benchmarkable tool.Yes it is.  The definition is as simple above.

The service is either up or down.   End of story.

>  more their usage as a benchmarking scheme.They're totally useless and no we weren't.

---

### Post by localzuk on 2006-03-26
First can I ask that you try and be a little more polite - I do not appreciate people being so blunt and seemingly confrontational.

Second, in response to your stating that we weren't talking about benchmarking schemes - I have never seen a magazine (as the original poster talked about) mentioning uptimes in a non-benchmarking manner.

My point is that if your server goes down due to a kernel upgrade do you take that into account for your service downtime - as it is not directly a problem with your service but one with the kernel. This is where I believe we differ - you are talking about practical applications whereas I believe myself and the original poster were talking about the way the 'uptime' is used as a benchmark (even though, as you say, it is kind of meaningless) by people comparing operating systems.

---

### Post by LordHunter317 on 2006-03-26
[QUOTE=localzuk]My point is that if your server goes down due to a kernel upgrade do you take that into account for your service downtime[/quote]**Yes, the service is down. *Why is irrelevant.***

All service uptime measurements are done like this.

> - as it is not directly a problem with your service but one with the kernel.It doesn't matter.  My service is down.  I'm loosing money.  That's all anyone cares about.

> This is where I believe we differ - you are talking about practical applications whereas I believe myself and the original poster were talking about the way the 'uptime' is used as a benchmarkAnd I explained how it is used.  It's measured by uptime of the oeprating system and nothing else.  As long as the hardware is booted and the kernel hasn't KP'd, the box is up.  And it's not measured on a per-box basis in the event of a cluster.  It's measured as the uptime of the cluster.

---

