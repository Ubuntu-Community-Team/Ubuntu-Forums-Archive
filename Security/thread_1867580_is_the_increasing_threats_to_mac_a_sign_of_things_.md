---
title: "is the increasing threats to mac a sign of things to come for linux?"
date: 2011-10-23
forum: Security
---

### Post by OOHHOO on 2011-10-23
ok, first of all, i'm no linux expert. :) so forgive me if this is a stoopid topic. 

but i've been reading the "increasing threats" of malware to apple's osx for some time now. i don't know if this is just hype or if this is a real concern for that platform. 

personally, i think that any os could be vulnerable. if it can be coded by human hands...it can be broken into by human hands. 

so, since linux is a "cousin" to mac's os, wouldn't it be possible to have a serious virus on linux one day?

anyway, i was just curious what people here thought. 
thanks

---

### Post by marin123 on 2011-10-23
I know about Mac's "Security center" which was a virus that many users happily installed onto their systems.
Mac's have virus problems because they have had large increase in sale, and that means many new users and most of them don't know how computers work.
Of course this could happen to Linux, if we get enough users, then it will become a popular platform for viruses. But Linux is safe by default, unlike OS X and Windows, so you don't have to worry much. And if you stick to Ubuntu official repos, you are safe :)

---

### Post by rjbl on 2011-10-23
> **OOHHOO said:**
> ok, first of all, i'm no linux expert. :) so forgive me if this is a stoopid topic. 

but i've been reading the "increasing threats" of malware to apple's osx for some time now. i don't know if this is just hype or if this is a real concern for that platform. 

personally, i think that any os could be vulnerable. if it can be coded by human hands...it can be broken into by human hands. 

so, since linux is a "cousin" to mac's os, wouldn't it be possible to have a serious virus on linux one day?

anyway, i was just curious what people here thought. 
thanks

Unlikely. Linux and the other Unices have been around for decades and it has proved very hard to creat an MS-DOS style virus that actually works in any unix-like system. Good news? Maybe. The thrust of malware creation has moved onto to exploiting user-daftness and major flaws in the way the OS handles applications. There are some major conceptual vulnerabilities in the way in which Windows runs apps, and a fair amount of flakiness in the software engineering which make Windows systems a much, much easier target than either GNU/Linux or Mac OS. To be fair to MS, versions of Windows since NT4 have got progressively harder to smite. 

User daftness? Yeah ... right! Be very careful.

rjbl

---

### Post by OpSecShellshock on 2011-10-23
Currently the mobile OS space is a bit higher value (because it's easier to hit, less secure, has a consistently growing population of users, and users don't control the deployment of fixes--just to name a few things). Desktop computing as we think of it is probably going to become more and more of a niche thing, and I'd expect malware to mostly follow whatever more people end up using.

That said, it really depends on the goal of the malware distributors. A lot of it can operate just fine while confined to user space, and probably doesn't need to persist across sessions (since by now distributors may expect their target machines to be rebuilt as soon as their stuff is discovered). In that sense, you're going to want to target platforms with tendencies toward long uptimes to extract the most value. But that's only going to apply to certain types of malware.

Also, there's no reason to expect the OS itself to be targeted. There have been bots that work just fine running entirely within Java. Other kinds of malware run as invisible browser extensions. Linux won't save you from either of those things.

The fake AV style things we probably don't have to worry about, especially now that there's a for-pay section in USC. Would you pay $60US for some non-USC application that just showed up during a web browsing session screaming about malware? Wouldn't you ask about it here first?

---

### Post by Dangertux on 2011-10-23
> **OpSecShellshock said:**
> Currently the mobile OS space is a bit higher value (because it's easier to hit, less secure, has a consistently growing population of users, and users don't control the deployment of fixes--just to name a few things). Desktop computing as we think of it is probably going to become more and more of a niche thing, and I'd expect malware to mostly follow whatever more people end up using.

That said, it really depends on the goal of the malware distributors. A lot of it can operate just fine while confined to user space, and probably doesn't need to persist across sessions (since by now distributors may expect their target machines to be rebuilt as soon as their stuff is discovered). In that sense, you're going to want to target platforms with tendencies toward long uptimes to extract the most value. But that's only going to apply to certain types of malware.

Also, there's no reason to expect the OS itself to be targeted. There have been bots that work just fine running entirely within Java. Other kinds of malware run as invisible browser extensions. Linux won't save you from either of those things.

The fake AV style things we probably don't have to worry about, especially now that there's a for-pay section in USC. Would you pay $60US for some non-USC application that just showed up during a web browsing session screaming about malware? Wouldn't you ask about it here first?

These are some really good points. 

While it is completely possible to create malware that works under Linux in the perspective that it works under Windows. 

As it stands right now though, as OpSecShellShock said the mobile market is a lot more intriguing to developers at the moment. It's widespread, it's easy to compromise, and nobody really knows what to expect in terms of security updates.

I think if Linux were to gain more of a market share in the desktop space we might see a larger influx of malware. Though I think things like Mac Defender would not be the route, but more likely browser hijacking, drive by downloads and other methods to deliver malicious executables. That would just be my guess, in the end only time will tell.

I do know that if malware developers were to start targeting Linux based operating systems it would be a much more targeted approach (like we saw with mac defender) and not so much the spray and pray approach we see with Windows based malware.

Just my thoughts

---

### Post by erixnow on 2011-10-23
I have wondered this myself. Linux as an OS is a bit different though.  Since there is a huge open source community people actually take pride in contributing to it.  Open Source will always have a more progressive nature.  as an OS itself it is a bit easier to attack since most things have static locations in memory,  so stack / heap overflowing is a bit easier.  I wont go too much into detail,  but it is people like the ones on this forum and the rest of the linux world that keep things alive.  I have been into linux since slackware and plug n play were the only distro's on cd and you coudnt find em.  also using university computers and archie and veronica to search for components to build linux boxes before I could find the distro's on cd.  In all the time that I have spent with broken boxes,  it always seems that patches and kernel revisions come quickly and keeping those up to date will keep you secure.  Linux is used as more of a server solution so most adware pushers dont target it as much.... plus there are alot of flavors so targeting is more difficult then targeting a mac.

Just A rant,

-Eric Peyser

---

### Post by collisionystm on 2011-10-23
I don't think a 'virus' will ever be a threat only because of the way things are installed on linux. The ultimate destruction would be a hack into an ubuntu update server and modify a script to wipe out files during an ubuntu update. 

scripting is the thing to be feared on Linux. It is a very powerful tool that is a big part of linux life.

---

### Post by conradin on 2011-10-23
Original Virus was on an apple.
The bigest deal I think Is Ubuntu, like mac, has its firwall by defualt disabled.

---

### Post by XBMC old School on 2011-10-23
I hope i am not hijacking. But from what I have read, Linux and Mac (Unix) systems are modular in  nature (folder permissions) and windows are monolithic system (folder hierarchy). So even if Linux computers get "infected", the viruses have a vary narrow margin that it can affect and the core of the system is shielded. Were as windows virus can run a muck everywhere with out permission restrictions (Therefore, in any OS _ALWAYS _run as a USER account. Don't give viruses admin access by running as admin)

Ok, real question now. Were do i look and defend against viruses now? Where do script viruses come into play?

Do you need a firewall with a router in front?

---

### Post by Dangertux on 2011-10-23
> **collisionystm said:**
> I don't think a 'virus' will ever be a threat only because of the way things are installed on linux. The ultimate destruction would be a hack into an ubuntu update server and modify a script to wipe out files during an ubuntu update. 

scripting is the thing to be feared on Linux. It is a very powerful tool that is a big part of linux life.

Why do you think that a virus would not be able to propogate easily? 

Or are we overlooking the mass malware distribution system that package managers could be quickly become?

---

### Post by OpSecShellshock on 2011-10-23
It's important to understand the goals and the ecosystem when thinking about malware distribution. It's a business, and it's resilient, efficient, and its components are well-segmented. Pay-per-install affiliates just have to get it there, they don't necessarily have to keep it there. In that case full compromise of the system is not a requirement, nor is surviving a reboot. People on the other end are getting paid (not well, exactly, at least not at that level) either way. Similarly, it's perfectly fine if a target machine is only temporarily drafted as a node in an army of rent-a-bots. They can be replaced. It's just part of the business continuity plan. You have to assume a certain number of them will be fairly quickly discovered and cleaned, but if the vector is unknown to the user you might just be able to hit them again later.

Point is, if you're going to go as far as targeting a specific platform/OS, you might as well stick to the kinds of malicious activity that platform or OS is best suited for. Linux is great for bots. So is Java. The browser is great for financial fraud and click-fraud. Non-repository software and themes are a great vector for trojans. Linux desktops are not so good for fake AV, which lucky for us is one of the more profitable enterprises at the moment. In most modern malware scenarios that come to mind, the system-level functions are completely unaffected, which may actually be to the advantage of the malware distributors. Stability of the system is good.

---

### Post by Gawains Green Knight on 2011-10-23
In Linux there is no exe, you would have to click on download, change permissions, run as root.... to mess up linux you have to try, to mess up windows you have to give it a try.

---

### Post by Dangertux on 2011-10-23
> **OpSecShellshock said:**
> It's important to understand the goals and the ecosystem when thinking about malware distribution. It's a business, and it's resilient, efficient, and its components are well-segmented. Pay-per-install affiliates just have to get it there, they don't necessarily have to keep it there. In that case full compromise of the system is not a requirement, nor is surviving a reboot. People on the other end are getting paid (not well, exactly, at least not at that level) either way. Similarly, it's perfectly fine if a target machine is only temporarily drafted as a node in an army of rent-a-bots. They can be replaced. It's just part of the business continuity plan. You have to assume a certain number of them will be fairly quickly discovered and cleaned, but if the vector is unknown to the user you might just be able to hit them again later.

Point is, if you're going to go as far as targeting a specific platform/OS, you might as well stick to the kinds of malicious activity that platform or OS is best suited for. Linux is great for bots. So is Java. The browser is great for financial fraud and click-fraud. Non-repository software and themes are a great vector for trojans. Linux desktops are not so good for fake AV, which lucky for us is one of the more profitable enterprises at the moment. In most modern malware scenarios that come to mind, the system-level functions are completely unaffected, which may actually be to the advantage of the malware distributors. Stability of the system is good.

^^ Flawless victory.

> 
In Linux there is no exe, you would have to click on download, change  permissions, run as root.... to mess up linux you have to try, to mess  up windows you have to give it a try. 

Umm...no this is just completely false.  

As the previously quoted post point out quite well root is not needed in the grand scheme of things. 'rooting' is going to be reserved for someone who is looking at compromising your system on a permanent basis, and potentially looking to move on to other systems in your network, or an outside network. 

Truth is if you end up in a user's home directory it's game over already for 90% of desktop users. I mean really, you can still quite easily survive a reboot without having uid 0.

---

### Post by martinr on 2011-10-24
I think your greatest worry should be the user space. As written above malware operates just fine while confined to user space.

Especially the internet browser is a vector of attack. The most used browsers tend to be cross-platform. So they have a vast user-base and become very interesting to attack because of that great number of users.

Ask yourself, what do you really know about the neat plug-in or extension and what about javascript and flash and [cross-site scripting]("http://en.wikipedia.org/wiki/Cross-site_scripting") attacks? Do you really know what information a script reads from your user space and sends back to some server? Maybe reading personal data like addresses, bank accounts, social security numbers, stealing session cookies,...?

The only thing I can think of is to restart your browser or even better your user session before you start doing vulnerable stuff, but that's no real protection either of course.

I think we've come to a point where even a seasoned security expert has become vulnerable to attack if he wants to participate in on-line society.

---

### Post by rookcifer on 2011-10-24
> **erixnow said:**
> as an OS itself it is a bit easier to attack since most things have static locations in memory,  so stack / heap overflowing is a bit easier. 

I don't know how you came to that conclusion.  Most every Linux distro comes with kernel hardening features such as NX/ASLR/RELRO/FORTIFY_SOURCE, etc.  Of course, individual apps have to be compiled to utilize these features, but Ubuntu at least compiles most of the high risk apps to be hardened.  Windows now utilizes some of these features as well.

---

### Post by dfarrell07 on 2011-10-24
imho, the greatest vulnerability will always be users, and Linux generally has smart users. Sure, we are not used to battling against malware like M$ft users, but most of us still know how to not be dumb and get infected. My point is that even if malware starts targeting Linux, say because it becomes more popular, it will have a harder time because users will not download fake AVs or use untrustworthy repos. Many will keep using NoScript, ABP, and HTTPSEverywhere. There is more to attacking Linux than beating the OS.

---

### Post by OpSecShellshock on 2011-10-25
> **dfarrell07 said:**
> imho, the greatest vulnerability will always be users, and Linux generally has smart users. Sure, we are not used to battling against malware like M$ft users, but most of us still know how to not be dumb and get infected. My point is that even if malware starts targeting Linux, say because it becomes more popular, it will have a harder time because users will not download fake AVs or use untrustworthy repos. Many will keep using NoScript, ABP, and HTTPSEverywhere. There is more to attacking Linux than beating the OS.

I would love to be able to agree with this, but there are things that still worry me. There are all sorts of non-Canonical (ha! see what I did there?) sites on the web that are dedicated to exploring modifications available from third parties for users to customize their experience. Many of them involve use of PPAs, which are vetted to a degree. However, there are others that just involve running shell scripts or retrieving .deb files to perform the work invisibly to the user. The best among them (OMG, etc.) at least carry warnings about such things, but as we all know from administering Windows systems, people don't really think about them.

---

### Post by The Cog on 2011-10-25
> **conradin said:**
> Original Virus was on an apple.
The bigest deal I think Is Ubuntu, like mac, has its firwall by defualt disabled.
In my opinion, it is a very big deal that Ubuntu doesn't need a firewall by default because there are no services for malware to connect to.

---

### Post by rookcifer on 2011-10-25
> **The Cog said:**
> In my opinion, it is a very big deal that Ubuntu doesn't need a firewall by default because there are no services for malware to connect to.

^ This.  People are too used to Windows where there are numerous services listening to the Internet at large that cannot be turned off.  That's why a firewall is a must on Windows.  On Ubuntu, not so much.

---

### Post by fishfisting on 2011-10-25
This is just my personall guess and I guess its fine to disagree. Firstly I do not belive Linux to be a good choice for security, unless linux is understood by the one installing it and know most of its weaknesses and strenghts.


I've had some limited experience with Linux now and only did some basic programming on it. I've noticed that Linux is pretty easy to molest in a default install. But that Linux can be configured to be secure, is my general view after testing Linux.

Personally I think Linux users are worse secured than windows users in general. Why?

Simply becuse the users are unafraid and think "hey my os is secure by default", while its not. Knowlege is from my experience best defence and how many Linux users know where to look for a virus? Or know how to detect an infection? They probably don't even notice and I bet there is many infected ubuntu users on this page right now.

Windows is also moving away from its old "plug and play" approatch and todays viruses to Windows usually has to be activated by a click and passing a UAC prmopt, that is if the file makes it through the antivirus, smart screen filter and hips etc and settings in Windows are today protected.

Personally I think Windows 8 will give people a shock, it will be more safe (by default) than Linux, and have almost no viruses. Things were already pointing to this in Windows vista: [http://www.zdnet.com/blog/ip-telephony/microsoft-less-vulnerabilities-in-vista-and-xp-than-mac-ox-tiger/2101](http://www.zdnet.com/blog/ip-telephony/microsoft-less-vulnerabilities-in-vista-and-xp-than-mac-ox-tiger/2101)

Sure one can call that marketing, but it holds some (statistic) truth to it. I think while Linux seems to develop stuff with mainly usability in mind, Windows is doing it with security in mind and Windows 8 will be the time when Windows is surpasses Linux security is my guess.

---

### Post by fishfisting on 2011-10-25
> **The Cog said:**
> In my opinion, it is a very big deal that Ubuntu doesn't need a firewall by default because there are no services for malware to connect to.

People don't run just a core. And if they do then that may hold true.

But people tend to install everything from servers to music/video players, torrent downloader, games and list goes on.

After some user customisation I bet it makes as much sense to have a firewall in Linux as it does in Windows.

I may be wrong tho as I'm fairly new to Linux. But I guess there is a reason why NSA and the like reccomend you to configure IPtables.

---

### Post by Dangertux on 2011-10-25
> **fishfisting said:**
> People don't run just a core. And if they do then that may hold true.

But people tend to install everything from servers to music/video players, torrent downloader, games and list goes on.

After some user customisation I bet it makes as much sense to have a firewall in Linux as it does in Windows.

I may be wrong tho as I'm fairly new to Linux. But I guess there is a reason why NSA and the like reccomend you to configure IPtables.

+++++++10000 

I haven't seen you post before but I freaking LOVE YOU!!!

No seriously, you are absolutely 100% correct. It DOES make as much sense to use a firewall in either environment.

---

### Post by mr-woof on 2011-10-25
Personally, I always activate the firewall after an install, install clamav for scanning any files that will be going to windows machine. I also then install some ff addons, no script, flash block, adblocking and then privoxy for use with firefox. 

I'd like to use Apparmor as well for Firefox, but I havent got my head round it as yet.

---

### Post by Reddoug on 2011-10-25
If the kernel.org website can be hacked, seems to me a users computer could be hacked. I would think they would have a lot of security. I am just trying to learn more about Linux security.

Doug

[http://www.linuxfordevices.com/c/a/News/Kernelorg-hacked/](http://www.linuxfordevices.com/c/a/News/Kernelorg-hacked/)

---

### Post by Thewhistlingwind on 2011-10-25
> **fishfisting said:**
> 
Sure one can call that marketing, but it holds some (statistic) truth to it. I think while Linux seems to develop stuff with mainly usability in mind, Windows is doing it with security in mind and Windows 8 will be the time when Windows is surpasses Linux security is my guess.

Doubt it.

Also, most people seem to think the opposite, that Windows lets usability get in the way of security and that Linux pulls in the reigns.

Speaking of activating your firewall... (I forgot to do that this install.)

The real truth of the matter though is that if you use a web browser, or flash, or use a PDF viewer, or any multitude of things, your at risk, if it really worries you, use a MAC. (Mandatory access control, not the brand.)

---

### Post by The Cog on 2011-10-26
> **fishfisting said:**
> People don't run just a core. And if they do then that may hold true.

But people tend to install everything from servers to music/video players, torrent downloader, games and list goes on.
And if they've enabled inbound blocking in the firewall, what happens? Their newly installed web server doesn't work until they go into the firewall configuration and re-open the port again. Their shared printing service doesn't work until they go into the firewall configuration and re-open the port again. The list goes on. 

So apart from making sure that newly installed services don't work until you've wasted time figuring out what's wrong with it, what has the firewall done for you? What is it doing after you got your newly installed service working - it's protecting all the other ports that don't accept connections anyway. 

Firewalls do have their uses - if you want to only allow communication with specific addresses or subnets, then you need a firewall and you will know exactly what rules you want to put in. 
But just running a firewall for the sake of it will simply waste more time reopening the ports again when you choose to install a web server, allow remote printing, allow SSH remote admin etc.

---

### Post by fishfisting on 2011-10-26
> **Thewhistlingwind said:**
> Doubt it.

Also, most people seem to think the opposite, that Windows lets usability get in the way of security and that Linux pulls in the reigns.

Maybe you can explain how so? A thought isn't necessarily right just cus many have thought it or are thinking it. Give some hard facts to this please or why you/they think so and maybe you convince people. Windows has latley lowered the root (admin) account premissions greatley. And many settings are restricted and harder to alter. Windows from what I've seen has just added more and better inbuilt security with each version. Their webbrowser is even running with lower privilegies and things has changed dramatically.

But maybe I'm missing something?

> **The Cog said:**
> And if they've enabled inbound blocking in the firewall, what happens? Their newly installed web server doesn't work until they go into the firewall configuration and re-open the port again. Their shared printing service doesn't work until they go into the firewall configuration and re-open the port again. The list goes on. 

So apart from making sure that newly installed services don't work until you've wasted time figuring out what's wrong with it, what has the firewall done for you? What is it doing after you got your newly installed service working - it's protecting all the other ports that don't accept connections anyway. 

Firewalls do have their uses - if you want to only allow communication with specific addresses or subnets, then you need a firewall and you will know exactly what rules you want to put in. 
But just running a firewall for the sake of it will simply waste more time reopening the ports again when you choose to install a web server, allow remote printing, allow SSH remote admin etc.

Yes, a firewall requires configuration to run and be functional and yes it can prevent good stuff. But this isn't just a firewall thing, its the famous: usability for secuirity tradeoff.

Ovbiously some Linux distrubutions goes for lower security just so user will find it convinience and the old myth: secure by default gets you far.

Yet I have read quite many in just this forum who are struggeling with breakins. And I think I'm not alone having read that. And those are just the people who noticed their infection/attack. From what I heard it took the experts hosting the kernel a long time to notice their breakin, just imagine how easy it would be for a regular Linux user running no firewall and caring little/nothing about logging to notice and take action. :popcorn:

As for the firewall: when you lower files premissions, folder premissions and tries to prevent certain actions (as Linux does) it comes with a price too and many applications require you to make changes to settings for them to work. The price for security is almost always the usability aspect. While a firewall (just like apparmour or SELinux) can prevent wanted actions to take place it also can be used and prevent many bad things from happening and prevent an intruder from gaining controll. If a firewall is such a hassle then why stop there? Maybe Ubuntu 12 can be the best of all worlds and just skip the firewall, skip the passwords, skip any restrictions and run the user(s) as root so users dont have to waste more time then nessesary when installing a server.

The firewall is usefull and that's why any facility that I've seen who needs any security configures one. And that's why its reccomended to be active by organisations such as the NSA, cus its gives a true "extra" layer of protection if configured. And Linux isn't considerd secure by default. This is shown by the fact that almost no (professional) organistaion would run a default Linux install without tweaking it - a lot. And Linux just continue to push more bloat in all its distros in the name of usability and the manual for stuff to remove from Linux today is just continusly expanding. The approatch is: release it and fix it when problems is noticed. Thats why I think Windows 8 will be the time when Windows is up to pair with Linux security (if it isn't already). Linux will continue to push usability and add buggy stuff to look and feel fresh, security will come second is my prediction. Mac is probably just a hint of what to come since Linux has close to zero detection by default and many don't even run a firewall it seems.

---

### Post by Dangertux on 2011-10-26
There were some good points in the last post, but the Windows vs Ubuntu security debate is still essentially flawed.

The reason being that BOTH operating systems encourage the wrong thing. They are both trying to save uneducated people from themselves. You can't do this, you need to educate someone on the principles of securing a system. You can not do that unless the individual is aware of what is actually threatening the system's security in the first place.

UAC and sudo do not security make. Neither does a firewall, nor do MAC,  or a guidebook from NSA.

Security is a process, a learning experience and a battle. A battle most will lose simply because they are looking for a catch-all operating system, application, permissions set, or policy. This doesn't exist, all of them change on a by-threat basis. Ultimately your security is as limited as your knowledge of the threat.

---

### Post by fishfisting on 2011-10-26
> **Dangertux said:**
> .... BOTH operating systems encourage the wrong thing. They are both trying to save uneducated people from themselves. You can't do this, you need to educate someone on the principles of securing a system. You can not do that unless the individual is aware of what is actually threatening the system's security in the first place.


Good point and I think you are correct. 

Education is (by far) one of the best defences. There are so many common attacks that I can think of that can be avoided (or at least much harder to pull through) by simply having the user somewhat educated.

Having said that I can honestly admit that my Linux understanding is very limited (especially compared to my Windows understanding).

And this is making me petrified when connecting my Linux configuration to the internet. But I'm learning new stuff almost every day since I know that that is my best way and probably my only way to have some additional security and limit my risk of becoming another linux victim.

I personally think best practices should be reccomended even to new user and when they know enought then they can relax their security. Even if its hard to prove I seriously belive that the user is by far the biggest issue and the reason why security usually fail (not the OS even if things may have sounded that way). The issue is that the security education has to be seeked for and people are too lazy to learn. If every user had like ONE week in school where professionals educated them about viruses/passwords/social engineering/hackers/etc then I bet viruses spreading would almost die and hacking a hotmail wouldn't be so easy. Cus today a upgraded OS is somewhat hard to touch unless user interaction makes things possible, (almost) gone are the days when a user just visits [www.dangerousurl](www.dangerousurl) and ended up infected due to the browsers being so insecure, today it usually requires the user to at least klick run. Even a somewhat educated user would cancel that, and a somewhat educated user would keep software updated and so on.... Having said that, I also think its unrealistic to belive normal users will be computer educated anytime soon so the OS and the security provided/offered do play a big role..

---

### Post by Dangertux on 2011-10-26
> **fishfisting said:**
> Good point and I think you are correct. 

Education is (by far) one of the best defences. There are so many common attacks that I can think of that can be avoided (or at least much harder to pull through) by simply having the user somewhat educated.

Having said that I can honestly admit that my Linux understanding is very limited (especially compared to my Windows understanding).

And this is making me petrified when connecting my Linux configuration to the internet. But I'm learning new stuff almost every day since I know that that is my best way and probably my only way to have some additional security and limit my risk of becoming another linux victim.

I personally think best practices should be reccomended even to new user and when they know enought then they can relax their security. Even if its hard to prove I seriously belive that the user is by far the biggest issue and the reason why security usually fail (not the OS even if things may have sounded that way). The issue is that the security education has to be seeked for and people are too lazy to learn. If every user had like ONE week in school where professionals educated them about viruses/passwords/social engineering/hackers/etc then I bet viruses spreading would almost die and hacking a hotmail wouldn't be so easy. Cus today a upgraded OS is somewhat hard to touch unless user interaction makes things possible, (almost) gone are the days when a user just visits [www.dangerousurl]("http://www.dangerousurl") and ended up infected due to the browsers being so insecure, today it usually requires the user to at least klick run. Even a somewhat educated user would cancel that, and a somewhat educated user would keep software updated and so on.... Having said that, I also think its unrealistic to belive normal users will be computer educated anytime soon so the OS and the security provided/offered do play a big role..

Umm...Browser vulnerabilities are one of the most commonly exploited vulnerabilities regardless of platform.

I think I'm just going to leave this thread before I have a coronary.

---

### Post by haqking on 2011-10-26
> **Dangertux said:**
> Umm...Browser vulnerabilities are one of the most commonly exploited vulnerabilities regardless of platform.

I think I'm just going to leave this thread before I have a coronary.

:lolflag:

I feel your pain ;-)

---

### Post by dFlyer on 2011-10-26
If you have any concerns about your system - search shields up on google and test your system. It should come back totally stealth.

---

### Post by Thewhistlingwind on 2011-10-26
> **Dangertux said:**
> Umm...Browser vulnerabilities are one of the most commonly exploited vulnerabilities regardless of platform.

I think I'm just going to leave this thread before I have a coronary.

> **Thewhistlingwind said:**
> 

The real truth of the matter though is that if you use a web browser, or  flash, or use a PDF viewer, or any multitude of things, your at risk,  if it really worries you, use a MAC. (Mandatory access control, not the  brand.)


Also, someone asked me why I "doubt" windows 8 will surpass Linux in security, simple.

Past history.

> **dFlyer said:**
> If you have any concerns about your system -  search shields up on google and test your system. It should come back  totally stealth.

1. Routers throw off tests.

2. Shields up is a classic site, with all the things classic tech writing holds.

In particular, the concept of a "stealth" port has no basis in reality. 

Theres a deny rule, which drops packets and doesn't respond. But that doesn't necessarily make you invisible.

---

### Post by Dangertux on 2011-10-26
> **dFlyer said:**
> If you have any concerns about your system - search shields up on google and test your system. It should come back totally stealth.

The following is a brief demonstration I just did, you may test this yourself if you'd like. It is a screenshot of an nmap scan on a default Ubuntu 10.04.3 Installation. The first scan has no iptables rules and ufw is disabled. The second scan has the following iptables rule

```

iptables -P INPUT DROP

```

Stealth ports don't exist. The only thing Steve Gibson proved is that he can sell Zone Alarm...

P.S: I should have left this thread when I said I was going to...

---

### Post by fishfisting on 2011-10-27
> **Dangertux said:**
> Umm...Browser vulnerabilities are one of the most commonly exploited vulnerabilities regardless of platform.

I think I'm just going to leave this thread before I have a coronary.

Did I say that browsers isn't one of the most commonly exploited thing out there?

I said: (almost) gone are the days when a user just visits [www.dangerousurl](www.dangerousurl) and ended up infected due to the browsers being so insecure. Browsers are not secure yet so to speak and probably never will be due to the forcing nature of implementing new stuff all the time.

But a browser Like IE9 will block more than 90% of the malicious downloads, just like that. And everything in the (major) browsers are getting more and more restricted and secure, meanwhile windows is also becoming more and more secure. 

Having visited several thousands of malicious links myself I can only say that today the risk of a malicious link really doing some magic installation woodo is close to zero. What is common on the other hand are the site issuing a download and asking you to run some plugin or install some codex or even a fake antivirus. But installation almost never happen automatically unless the browser is really old. At least from my personal experience I would like to think that todays browsers are pretty dam* secure if keept updated and that the weak link is usually the user panicing or not paying attention and clicking, "run".

> **Thewhistlingwind said:**
> Also, someone asked me why I "doubt" windows 8 will surpass Linux in security, simple.

Past history.


Its called past history for a reason. How about recent history:

Recent history shows that Windows is having less and less security holes and may already have less vulnerabilities than Linux. LINK -> [http://www.gizmodo.com.au/2008/01/microsoft_says_vista_more_secure_than_xp_osx_and_linux-2/](http://www.gizmodo.com.au/2008/01/microsoft_says_vista_more_secure_than_xp_osx_and_linux-2/)

Recent times also suggest that Windows is faster than the alternatives (linux/mac) to fix security holes: [http://bink.nu/news/black-hat-who-patches-security-holes-faster-microsoft-or-apple.aspx](http://bink.nu/news/black-hat-who-patches-security-holes-faster-microsoft-or-apple.aspx) Link2: [http://news.cnet.com/Study-Windows-has-fewest-security-holes/2100-1002_3-6169956.html](http://news.cnet.com/Study-Windows-has-fewest-security-holes/2100-1002_3-6169956.html)

---

### Post by Dangertux on 2011-10-27
> 

I said: (almost) gone are the days when a user just visits [www.dangerousurl]("http://www.dangerousurl/")  and ended up infected due to the browsers being so insecure. Browsers  are not secure yet so to speak and probably never will be due to the  forcing nature of implementing new stuff all the time.

But a browser Like IE9 will block more than 90% of the malicious  downloads, just like that. And everything in the (major) browsers are  getting more and more restricted and secure, meanwhile windows is also  becoming more and more secure. 
Internet Explorer 9 
-------------------------

CVE-2011-1998
CVE-2011-2000
CVE-2011-2001
CVE-2011-1993

All 4 vulnerabilities allowed remote code execution and were patched this month. (less than 2 weeks ago)

Firefox
----------------

CVE-2011-2364
CVE-2011-2365
CVE-2011-2374

Again all recent and all allowed remote code execution.

Chrome
--------------

CVE-2011-2761
CVE-2011-3880
CVE-2011-2837
CVE-2011-2841

(there were about a dozen more from the past 2 months, but you get the idea) Again remote code execution...

So what was that about modern browsers?


> 
Having visited several thousands of malicious links myself I can only  say that today the risk of a malicious link really doing some magic  installation woodo is close to zero.
Several thousand? Really?I'm absolutely sure that you CAN initiate code execution without user interaction and would be happy to illustrate this if google can not lead you to the answer in regards to that.

This comes back to the education thing I was talking about earlier in this thread. In addition to education, there also needs to be a serious cutback on misinformation...

Also -- for those waiting in the wings to point out that the Chrome and Firefox vulnerabilities were for Windows. Realize it doesn't take long to load up a debugger and find a new return address. (assuming the code is flawed in the same method which it usually is)

One more thing, about that chart showing vulnerability numbers across operating systems. That is nice, but it doesn't factor the severity. How many of those vulnerabilities that remain unfixed are denial of service versus vulnerabilities that allow a complete compromise. Statistics are easy to fiddle with. 

> 
Recent times also suggest that Windows is faster than the alternatives (linux/mac) to fix security holes: [http://bink.nu/news/black-hat-who-pa...-or-apple.aspx]("http://bink.nu/news/black-hat-who-patches-security-holes-faster-microsoft-or-apple.aspx") Link2: [http://news.cnet.com/Study-Windows-h...3-6169956.html]("http://news.cnet.com/Study-Windows-has-fewest-security-holes/2100-1002_3-6169956.html")
Recent history also shows that Microsoft's poor implementation of ASLR/DEP (statically loading DLL's into executable memory) forces them to.

Best Regards

---

### Post by fishfisting on 2011-10-27
> **Dangertux said:**
> Internet Explorer 9 
-------------------------

CVE-2011-1998
CVE-2011-2000
CVE-2011-2001
CVE-2011-1993

All 4 vulnerabilities allowed remote code execution and were patched this month. (less than 2 weeks ago)

Firefox
----------------

CVE-2011-2364
CVE-2011-2365
CVE-2011-2374

Again all recent and all allowed remote code execution.

Chrome
--------------

CVE-2011-2761
CVE-2011-3880
CVE-2011-2837
CVE-2011-2841

(there were about a dozen more from the past 2 months, but you get the idea) Again remote code execution...

So what was that about modern browsers?


What you are basically saying is that there isn't perfect browser security. And you are certainly right.

I only speaked from my own very limited experience. To share my real life experience with one small portion of the wide area of computer security, and how browsers behave when meeting one, what I belive to be - common way of getting a trojan/virus/whatever.

> **Dangertux said:**
> 

Several thousand? Really?I'm absolutely sure that you CAN initiate code execution without user interaction and would be happy to illustrate this if google can not lead you to the answer in regards to that.

This comes back to the education thing I was talking about earlier in this thread. In addition to education, there also needs to be a serious cutback on misinformation...

Also -- for those waiting in the wings to point out that the Chrome and Firefox vulnerabilities were for Windows. Realize it doesn't take long to load up a debugger and find a new return address. (assuming the code is flawed in the same method which it usually is)

One more thing, about that chart showing vulnerability numbers across operating systems. That is nice, but it doesn't factor the severity. How many of those vulnerabilities that remain unfixed are denial of service versus vulnerabilities that allow a complete compromise. Statistics are easy to fiddle with. 

Recent history also shows that Microsoft's poor implementation of ASLR/DEP (statically loading DLL's into executable memory) forces them to.

Best Regards

A **few** thousands at least. There was a time when I was downloading between 250 - 1400 malwares a day, I'm not sure how many I tested against IE9 (but it was more than a thousand in total), and against firefox I have tested even more "bad links".

The links and any file provided hardly ever does any damages to a patched system unless allowed to do their thing from what I've seen. Usually once there is a vulnerability attempt (and this isn't that often compared to the volume) this attempt is directed at just ONE browser, like IE so Firefox users would pass that one (if they were unlucky enought to visit the link in the first place and it has yet to be blacklisted that is). And even then the site is probably just new but hosting some old vulnerability, (this I guess happen and still work since people are not allways updating their software).

I'm not sure precisley what you mean when you (challange me?) and say: "initiate code execution without user interaction and would be happy to illustrate this".

I don't claim to be a know it all security expert and capable of lunching (what sounds like) attacks. Neither do I see how that would be rellevant?

My best regards.

---

### Post by OpSecShellshock on 2011-10-27
Let's not forget the plugins when we're discussing browser security. Just looking at the vulnerabilities in the browser itself does not tell us everything we need to know. While we're at it, we'll want to look at server-side vulnerabilities that lead to code injections, whether in CMS platforms or in third-party ad networks. I can't possibly be the only one who looks at a packet capture for an exploit request and then looks at a previous request almost expecting to find an advertising script. This stuff happens really often.

Also, note that the recent report sent out/commissioned by Microsoft itself from the Your Browser Matters site deliberately excludes drive-bys while touting protections against trojans that require user interaction. Drive-bys are a huge business, and they generally will lead to packs that cycle through exploits imperceptibly and quickly before running their local code.

There's more, and I could talk about it all day, but looking at the clock it appears to be the time when I actually have to go deal with it for several hours...

---

### Post by The Cog on 2011-10-27
> **fishfisting said:**
> Yes, a firewall requires configuration to run and be functional and yes it can prevent good stuff. But this isn't just a firewall thing, its the famous: usability for secuirity tradeoff.

Ovbiously some Linux distrubutions goes for lower security just so user will find it convinience and the old myth: secure by default gets you far.

You still haven't said how a firewall will confer greater security to a computer that doesn't have any open ports and therefore won't accept incoming calls anyway.

Yes you see lots of posts from people who had breakins. But in general these are a result of installing a VNC or SSH service. If they had a firewall running, they would of course also had to open the port in the firewall to get it working, in which case they end up in exactly the same state anyway. In the end, the PC is refusing calls except to the one they've installed the server for.

How does a firewall improve the security of a computer that won't accept incoming calls? I'm getting lots of "Everybody knows you need a firewall" stuff from you, but no explanation why. You are not on windows now, there are no unstoppable services to protect. That's the big issue to me, as I said earlier. 

By default, Ubuntu doesn't need a firewall. Not needing a firewall in the first place is a big thing. You don't **have** to install a firewall, so you don't **have** to then punch holes in it to allow just the ports you want. There are no other holes that you need to keep covered up. In general, if you install a firewall and then install a service, you will just have to open the firewall again to make your new service work.

I don't see how having a firewall that closes all the ports that are already closed, and permits access to all the services that you choose to install makes any difference.

---

### Post by fishfisting on 2011-10-27
> **The Cog said:**
> You still haven't said how a firewall will confer greater security to a computer that doesn't have any open ports and therefore won't accept incoming calls anyway.

Yes you see lots of posts from people who had breakins. But in general these are a result of installing a VNC or SSH service. If they had a firewall running, they would of course also had to open the port in the firewall to get it working, in which case they end up in exactly the same state anyway. In the end, the PC is refusing calls except to the one they've installed the server for.

How does a firewall improve the security of a computer that won't accept incoming calls? I'm getting lots of "Everybody knows you need a firewall" stuff from you, but no explanation why. You are not on windows now, there are no unstoppable services to protect. That's the big issue to me, as I said earlier. 

By default, Ubuntu doesn't need a firewall. Not needing a firewall in the first place is a big thing. You don't **have** to install a firewall, so you don't **have** to then punch holes in it to allow just the ports you want. There are no other holes that you need to keep covered up. In general, if you install a firewall and then install a service, you will just have to open the firewall again to make your new service work.

I don't see how having a firewall that closes all the ports that are already closed, and permits access to all the services that you choose to install makes any difference.

Your question are very valid I guess. Here are some (possible) scenarios: User runs "badfile" (or someone else does), the bad file is successful and installs a service that tries to connect through Port 1337. A firewall can prevent that badfile from connecting to "badperson" if configured somewhat restricted to filter outgoing traffic. This offers an additional layer. And if you only have a few ports open then chances are that a remotley executed file **failes** to find a open port is quite big and the hacker simply ends up thinking: "hey my hacking didn't work".

Thats an inside out scenario. As for incoming: A firewall can be tuned to prevent diffrent sorts of unwanted traffic even on the open ports. Maybe a user needs to be able to remote controll his/her PC and has to open port number xxx for that communication, the Firewall can here offer additional security through smart filters such as IP adress restriction. This can make the port look closed and as if there is no service running for the hacker trying to probe from a none allowed IP, a firewall also offers fine tuning of diffrent protocols that may be supported by default by the application but may not be needed by the user. A firewall lets user fine tune traffic to some degree and this helps to further enchant security.

Firewall's can also be set to prevent some malformed packages and such and prevent DDOS attacks (or at least make them harder). Generally the firewall can make the computer harder to adress and understand to some degree (and it can also prevent your information from leaking).

I'm not saying that the firewall is the best defence there is. However it offers an extra layer and should probably be used. And are currently reccomended by security experts and various security organisations. And in use by BIG BIG organsations, but I guess those are just ignorant.:)

---

### Post by SparTacux on 2011-10-27
> **The Cog said:**
> You still haven't said how a firewall will confer greater security to a computer that doesn't have any open ports and therefore won't accept incoming calls anyway.

Yes you see lots of posts from people who had breakins. But in general these are a result of installing a VNC or SSH service. If they had a firewall running, they would of course also had to open the port in the firewall to get it working, in which case they end up in exactly the same state anyway. In the end, the PC is refusing calls except to the one they've installed the server for.

How does a firewall improve the security of a computer that won't accept incoming calls? I'm getting lots of "Everybody knows you need a firewall" stuff from you, but no explanation why. You are not on windows now, there are no unstoppable services to protect. That's the big issue to me, as I said earlier. 

By default, Ubuntu doesn't need a firewall. Not needing a firewall in the first place is a big thing. You don't **have** to install a firewall, so you don't **have** to then punch holes in it to allow just the ports you want. There are no other holes that you need to keep covered up. In general, if you install a firewall and then install a service, you will just have to open the firewall again to make your new service work.

I don't see how having a firewall that closes all the ports that are already closed, and permits access to all the services that you choose to install makes any difference.

If you have a restrictive outgoing policy then you cannot open other ports and make a connection from within. A rogue program might try to open a port and make a connection out.  You also might have IP blocking on certain traffic. My Firewall will only let me connect to my email server and no other. My NTP server is only allowed to connect to the NTP server I say and so on.   Same with my DNS servers.

I suppose If you don't do internet surfing to Chinese web sites then you could potentially block all outgoing traffic to Known Chinese telecoms providers list of IP's or any other Foreign telecoms providers list of IP's. This would reduce chances of compromises and your data going to Foreign Lands.  It would be interesting if there are list available of IP's used by Foreign Telecomms providers.

You would have in effect the Great Firewall of China ;-)
Mind you - I've got a feeling a great Firewall of Silcon Valley might prove to be just as useful. :0) 

I've got a recent version of Firefox making one or two interesting links. Links are blocked going out until I've got to the bottom of it. Yup - A Firewall is very useful as long as you watch and maintain them.
If you have Firewall logs then you can observe traffic going out and make an instant decision about suspicious traffic there and then. It's better than having no choice.

---

### Post by dannodan2008 on 2011-10-27
> **conradin said:**
> Original Virus was on an apple.
The bigest deal I think Is Ubuntu, like mac, has its firwall by defualt disabled.
  Realy ?

---

### Post by haqking on 2011-10-27
> **dannodan2008 said:**
> Realy ?

kind of, elk cloner was the first major outbreak of malware.

[http://en.wikipedia.org/wiki/Timeline_of_computer_viruses_and_worms](http://en.wikipedia.org/wiki/Timeline_of_computer_viruses_and_worms)

---

### Post by MG&amp;TL on 2011-10-27
I would say that if linux was suddenly to become the world's favourite OS, then we'd have as many viruses as windows very shortly. As long as you use an obscure OS, you're safe(-ish).

And if Linux became a virus-fest, then a) Ubuntu would have a better firewall, and b) I'd be moving to BeOS, ReactOS, Unix or something similiarly obscure.

---

### Post by lisati on 2011-10-27
> **Dangertux said:**
> You can not do that unless the individual is aware of what is actually threatening the system's security in the first place.
A similar principle holds when choosing and using security tools. For example, an AV scanner can't protect or clean your system if it doesn't "know" about a particular threat. Even if it's database is kept fully up to date, it usually takes time for the signature for new a threat to be included in the scan.

---

### Post by haqking on 2011-10-27
> **lisati said:**
> A similar principle holds when choosing and using security tools. For example, an AV scanner can't protect or clean your system if it doesn't "know" about a particular threat. Even if it's database is kept fully up to date, it usually takes time for the signature for new a threat to be included in the scan.

hence the questionability of AV on linux, not that it shouldnt be used, but if a new one was to occur then the linux AV is likely not to find it anyways, where is with windows AV it protects to a degree against still often used malware from years passed.

However the fact that most people blindly trust these apps is the real security flaw as they dont understand what they are protecting against

---

### Post by Dangertux on 2011-10-27
> **lisati said:**
> A similar principle holds when choosing and using security tools. For example, an AV scanner can't protect or clean your system if it doesn't "know" about a particular threat. Even if it's database is kept fully up to date, it usually takes time for the signature for new a threat to be included in the scan.

Good point, bad example in my opinion. Although the example is hugely relevant to Linux. This example leaves out something important. Heuristics, which are used to determine if a program is doing something malicious, regardless of its signature. For instance if an application is trying to hook system calls, it's essentially probably bad. Though this can lead to false positives in terms of things like drivers, or applications that make extensive use of kernel level functionality.

That being said this point is great, because heuristic based detection is all but non-existent in Linux. For some reason only Windows AV gets that.

---

### Post by Thewhistlingwind on 2011-10-27
> **Dangertux said:**
> 
That being said this point is great, because heuristic based detection is all but non-existent in Linux. For some reason only Windows AV gets that.

[https://en.wikipedia.org/wiki/Rkhunter](https://en.wikipedia.org/wiki/Rkhunter)

I'm not sure if that counts. It just doesn't advertise as an AV.

---

### Post by haqking on 2011-10-27
> **Thewhistlingwind said:**
> [https://en.wikipedia.org/wiki/Rkhunter](https://en.wikipedia.org/wiki/Rkhunter)

I'm not sure if that counts. It just doesn't advertise as an AV.

a rootkit is not a virus, rkhunter is for detecting rootkits/backdoors etc.

AV solutions can detect trojans which often contain rootkits or backdoors but that is not the same thing IMO.

besides it doesnt negate the fact that Linux AV has no heuristic technology and is only as good as its at the minute definition/signature database

---

### Post by Thewhistlingwind on 2011-10-27
> **haqking said:**
> 
besides it doesnt negate the fact that Linux AV has no heuristic technology and is only as good as its at the minute definition/signature database

> wrong permissions, hidden files, suspicious strings in [kernel modules]("https://en.wikipedia.org/wiki/Kernel_module"), and special tests for [Linux]("https://en.wikipedia.org/wiki/Linux") and [FreeBSD]("https://en.wikipedia.org/wiki/FreeBSD").It sounds like it's doing limited testing outside of the signature database.

Of course, I'm sure dangertux was thinking of something with a bit more power behind it when he made the statement.

---

### Post by haqking on 2011-10-27
> **Thewhistlingwind said:**
> It sounds like it's doing limited testing outside of the signature database.

Of course, I'm sure dangertux was thinking of something with a bit more power behind it when he made the statement.

yeah that is true, but rkhunter is not a AV solution.

there are no current viruses in the wild for linux though there could be.

there are however 240+ or so (i havent checked the current count recently) rootkits.

---

### Post by Dangertux on 2011-10-27
I was referring to something more...Aggressive. For instance decent heuristics will monitor program execution. In a simple case will notice an rwx function getting hooked, during run time. 

Applications like rkhunter are looking for file changes AFTER the fact. So while this is still technically a heuristic behavior, it doesn't quite qualify for what I meant. Also as it was stated this is not a generalized AV or anti-malware solution.

---

### Post by Ex-windows on 2011-10-27
Wow   that one person almost sounds like a Microsoft Salesperson lol ( No offense intended)
However I am here to share that  I dont know  much more than 1/2 of an iota of all the technical issues involved  but the only reason windows is getting any safer ( IF they indeed are) is probably due to that merger/takeover or whatever it was with "Novell"   I for one will stick with linux with whatever faults it may have or may develope.
:popcorn:

---

