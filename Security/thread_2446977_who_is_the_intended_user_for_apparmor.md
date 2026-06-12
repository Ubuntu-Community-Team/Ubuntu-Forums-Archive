---
title: "who is the intended user for apparmor"
date: 2020-07-10
forum: Security
---

### Post by goodstuff9 on 2020-07-10
[COLOR=#242729][FONT=Arial]Ubuntu 18.04.2.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I am not a technically trained person, pretty much just a regular layman who uses Ubuntu.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I've been reading about apparmor, and struggling to understand its benefit.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I understand that once the profiles are set up, apparmor kind of "isolates" an application, limiting what it can do - and thereby limiting any damage it could cause.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]A lot of the literature I've read has been praising the great benefit apparmor provides a system.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]But, my system has only a few profiles in apparmor, so I am struggling to see how apparmor is doing much if any good for my system. Yes, it is protecting my system from like 20 applications, but my system has FAR more applications that apparmor is doing nothing with. So, I think, what is this great benefit that apparmor is providing my system?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]In addition - For a "normal" user like me, who still cannot understand how to wisely create a profile for an application, what, if anything, did the creators of apparmor expect someone like me to do with apparmor? I never do anything with it, because I don't know what I'm doing.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]In summary, my two questions:[/FONT][/COLOR]

[LIST=1]
[*][FONT=inherit]How does apparmor benefit my system when it has profiles for only a handful of applications; and,[/FONT]

[*][FONT=inherit]What interaction with apparmor is a layman user expected to have?[/FONT]
[/LIST]

---

### Post by TheFu on 2020-07-10
apparmor is for admins and nerdy power-users.  
Only 2 times have I needed/wanted to change stuff.  

For sandboxing, I use a mix of virtual machines (kvm type), LXD containers and **firejail**.  In general, firejail has the most fine-grained controls for each application.

---

### Post by goodstuff9 on 2020-07-10
Thank you.  

In a way, I am glad to hear that you never bother much with apparmor either.  I am not a nerdy power user, so I guess I won't pay attention to apparmor.  

I had looked into firejail, but I saw many, many, many complaints about it causing lots of problems, so I thought it probably isn't for me.

---

