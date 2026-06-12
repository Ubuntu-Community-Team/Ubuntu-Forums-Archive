---
title: "What makes ubuntu secure?"
date: 2020-05-05
forum: Security
---

### Post by darkmatter2020 on 2020-05-05
I have often heard that Ubuntu/Linux is a secure OS. Being a non expert on security, to my mind, I am not able to understand why?
I understand that traditional windows viruses are more difficult to execute in Ubuntu due to executable permissions. 
Also, I understand that it is difficult to get malware installed on your system for two reasons:

1) The apt process verifies that software is installed from official repositories.

2) Even if malware gets downloaded or installed on your system, the creators of the malware have a chance of getting caught as the IP address of the site from where the malware was downloaded is known.

(Please confirm to me if the above two points are correct.)

However, suppose that malware does get installed on your system despite the above two points, perhaps by accident. I find that there is very little in Ubuntu to prevent this malware from causing serious damage. For eg.:

1) A malware can log keystrokes, and can also capture your system password if you happen to enter it while its running in the background.

2) Having obtained the sudo password, it can now run other programs as root. It can even modify existing programs and replace them with its own infected versions of those programs.

Hence, such a malware effectively has the capacity to do great damage. 

If the above points are valid, then why do we consider Ubuntu to be a secure OS?

---

### Post by EuclideanCoffee on 2020-05-05
Ubuntu is a downstream project from Debian.

Debian is a project that provides stable builds of software.

This software is checked for licensing requirements and are accurately documented.

The software is largely open source, unless marked as contrib or non-free.

Open source software allows many organizations to audit the code base, which is a typical requirement in all organizations to ensure security compliance. Therefore you have many security engineers contributing to the same project.

Debian provides reproducible builds, which verify each build is the same bit-for-bit in their repositories. These repositories are typically copied over into universe for Ubuntu.

Ubuntu verifies each package, each repository, and each upload with GPG keys.

The GPG keys are distributed to your device offline via the ISO you verified with the ISO hash Ubuntu provides on its homepage.

From all of these checks, it is nearly impossible for Ubuntu to have a problem in the security of its supply chain. Though there are weaker points in various layers, they're mitigated in later or earlier parts of the distribution layer that gets to you.

At this point, the security checks on your system are made.

By default, software will not execute (or run) unless flagged to do so on your computer. When you download software, by default it is not flagged to be able to run on your computer until you explicitly do so.

Another layer of security is that once an application is flagged, it cannot be done for the "root" user unless the root user has given permission as well.

The root user is the user that can access both kernel and user space configuration files. These files determine how applications manage your system. If the root doesn't provide access for some applications, those applications cannot configure your computer system-wide, something which malware typically aims to do.

This does not cover you from these attacks however. And you'd need to rely on application security, such as Firefox or Thunderbird or Steam to protect you from these attacks.

1. Tracking of your browsing history (on other websites).
2. Recording your Skype calls (depends on privacy policies).
3. Malware that install themselves to your Firefox agent and stay permanently inside your Firefox cache, but only run while you browse, like crypto miners.
4. Applications that you download that do weird things, like upload stuff in your home directory, or possibly download hidden stuff and then upload these files elsewhere.

You are responsible for what applications can run on your computer and how they operate.

Linux provides you with the platform that makes this easier to do.

Good luck.

---

### Post by darkmatter2020 on 2020-05-05
Thanks for the comprehensive response, Euclidean. I would appreciate it if you can give me a clarification on one point below which I mentioned in my first post.

I mentioned an attack like the below:

1) A malware can log keystrokes, and can also capture your system  password if you happen to enter it while its running in the background.

2) Having obtained the sudo password, it can now run other programs as  root. It can even modify existing programs and replace them with its own  infected versions of those programs.

Is such a kind of scenario possible in Ubuntu? Or are there features which protect it from this?

---

### Post by jdeca57 on 2020-05-05
One reason remains valid over time: Linux desktop simply has no important market share so there are fewer attempts to break a system that doesn't have a lot of followers. You can  make your system vulnerable but that takes an effort. By the way, all the mistakes one can make - divulging bank information, pin codes or personal info over the internet - are independent of the OS. As always, the problem is the user...

---

### Post by EuclideanCoffee on 2020-05-05
> 
Is such a kind of scenario possible in Ubuntu?                  


Yes, of course. As it is anywhere.

> 
Or are there features which protect it from this?


See above. You cannot protect from each attack specifically, but each layer prevents such a malicious application to occur natively.

---

### Post by crip720 on 2020-05-05
One other thing is that malware needs to written for linux and most would need to be installed by user to run.  Windows malware can be on your system, but only be bloat.  Linux is also updated very often to patch any holes.  On any OS the best or worst security is the person using the system.  Be aware of what is out there and what you can do.

---

### Post by EuclideanCoffee on 2020-05-05
> 
One other thing is that malware needs to written for linux and most would need to be installed by user to run.


For example, IoT malware is written for Linux, which has created the largest bot network ever.

[https://krebsonsecurity.com/2016/10/source-code-for-iot-botnet-mirai-released/](https://krebsonsecurity.com/2016/10/source-code-for-iot-botnet-mirai-released/)

[https://en.wikipedia.org/wiki/Mirai_(malware)](https://en.wikipedia.org/wiki/Mirai_(malware))

> 
**Mirai** ([Japanese]("https://en.wikipedia.org/wiki/Japanese_language"): &#26410;&#26469;, [lit.]("https://en.wikipedia.org/wiki/Literal_translation") 'future') is a [malware]("https://en.wikipedia.org/wiki/Malware") that turns networked devices running [Linux]("https://en.wikipedia.org/wiki/Linux") into remotely controlled [bots]("https://en.wikipedia.org/wiki/Internet_bot") that can be used as part of a [botnet]("https://en.wikipedia.org/wiki/Botnet") in large-scale network attacks.  It primarily targets online consumer devices such as [IP cameras]("https://en.wikipedia.org/wiki/IP_camera") and [home routers]("https://en.wikipedia.org/wiki/Home_router").


The art of security is to maintain Linux or any machine to preserve safe operation. All operating systems are vulnerable.

---

### Post by kurt18947 on 2020-05-06
What I do is not Linux specific but Linux sure makes it easier. I have an install on a small partition. I have a minimum of add-ons and drivers. I only go to high value sites such as financial sites or where I have to enter sensitive info with that install. By itself that's no panacea but it's another layer that the people of ill will have to deal with. I figure the less time that install is online the less time it's exposed to risks. I also like the philosophy of fixing flaws rather than using yet more software to try and cover the flaw. Kind of like repairing a leaky roof rather than smearing it with some sort of tar and hoping.

---

### Post by DuckHook on 2020-05-06
Let me add a different perspective.

What you've heard about Ubuntu/Linux misses the point. In fact, claiming that a desktop OS is "secure" is a pretty meaningless claim in the real world. Note that I did not say it is *inaccurate*; I said that it is *meaningless*.

[list=1]
[*]Firstly, security is a vague and ambiguous concept. It means different things to different people.
[*]Secondly, OSes all have their own strengths and weaknesses.
[*]But the biggest thing of all is: modern OSes, in and of themselves, play a very small role in desktop security.
[/list]
Perhaps a quantification will help. The numbers that follow are by no means accurate; I am using numbers in the service of creating a sense of proportion that illuminates the more fundamental issue:

Desktop security is roughly 90% user behaviour and 10% the OS. Therefore, even if an OS is hardened as much as possible, it will only take you to 10% of your goal. A poor OS can be close to zero (Windows XP was close to that level), yet could still be relatively safe if the user practised excellent user hygiene. Conversely, a super-hardened, über-OS cranked all the way up to eleven cannot fend off a simple trojan if the user foolishly and actively installs it.

Given that 90% of the problem is the user, focusing on the OS is more often than not a misallocation of resources.

That said, a good OS can start a user off with a better fighting chance. It offers the tools and the fundamentals that will help users become more secure *provided that users are willing to learn and are dedicated to using them*. More often than not, this entails strict self-discipline, a considerable learning curve, irritating inconvenience and, most of all, a large dose of self-denial. It is these demands that most people cannot abide. This is why security is sub-optimal in most installations. It has little to do with the OS.

A further illustration, this time, a personal anecdote: in our household, my security practices are highly hardened; Mrs DuckHook's are not. Since I look after all of the IT, I make sure that we share the same OS, the same firewall, the same infrastructure, the same NASes, network and router—yet my installation is orders of magnitude more secure than hers. Why? Because I am willing to go through the learning curve and put up with the inconveniences that accompany ultra-hardened computing; she is not. And because I love her to bits, can't stand seeing her frustrated or disheartened, and know who's the boss around here, I set up her computing so that it is far less secure but also far less intrusive. I rely on religious backups and absurd redundancies to guard against mishaps, but what I must accept is that she will never have the same respect/deference for security that I have.

Your question is a good example of addressing the wrong problem. As EuclideanCoffee has already noted, of course a keylogger will compromise your entire install. And no OS in the world can save you from such a malicious app.

The real question should not be whether Ubuntu has a magical resistance to such malware (it doesn't); rather, the real question should be why such malware would find its way onto your system in the first place. It almost never gets there "by accident", even in operating systems that are far worse than Ubuntu.

---

### Post by 1clue on 2020-05-06
What makes an OS secure is education, care, prompt thoughtful updates, and testing.

There is a collection of databases for bugs and vulnerabilities and the applications and operating systems they're found on. The white-hat hackers in the world populate this database frequently. Offending code is found and modified, tested, and then committed back to the central repositories. This is done by software providers around the world.

You as a system administrator are responsible for keeping your system up-to-date and secure. Your involvement might start out to be a complete trust of the system and simply accepting every update that comes along. Eventually you might start reading the change log on those updates, and maybe browse the CVE database periodically. Eventually you may decide to choose which updates to apply immediately and which to leave out for awhile.

There is only so much delaying that can be done by an end user. But you can choose which branch of an OS you want to adopt, thereby choosing the group of experts you trust based on your needs for this specific installation.

Finally there's the education and care taken by users. There is no way to secure a system against an idiot at the keyboard. Under the best of circumstances you need to educate yourself to new and ongoing risks, and know how to mitigate them. There is no way to do this without getting your hands dirty and learning something.

---

