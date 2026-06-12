---
title: "Question about IPCop"
date: 2014-05-05
forum: Security
---

### Post by linuxyogi on 2014-05-05
Hi,

I learned about IPCop which as you know is a Linux based firewall distro.

I have never used a firewall distro but I know it can do various additional things like load balancing, realtime virus detection, etc.

I am not asking about those features. What I wanna know is if IPCop is superior in terms security in comparison to something very simple like ufw under Ubuntu ?

I ask this coz both are Linux and both uses iptables. Do people use firewall distros like IPCop only for extra features they provide ?

---

### Post by ian-weisser on 2014-05-06
"Superior in terms of security" seems rather vague.
Are you asking if attackers can penetrate an IPCop box more easily than they can penetrate an Ubuntu box? No.

But they are used to address very different problems. An IPCop box runs on dedicated hardware, has no logged-in users, and runs no external services (except the admin interface). It protects a network, and it's interface is optimized for an administrator who wants to do just that with the box. Ubuntu is a general-purpose OS.

Are you asking if it's possible to set up an Ubuntu install to duplicate the complete functionality of IPCop? Probably, but I consider it rather a waste of time. If you need something like IPCop, use it.

Or are you asking if you need something like IPCop to protect your network's Ubuntu machines, or if they can protect themselves? Well, the good admins I know generally believe in multiple and layered defenses.

---

### Post by linuxyogi on 2014-05-06
> **ian-weisser said:**
> "Superior in terms of security" seems rather vague.
Are you asking if attackers can penetrate an IPCop box more easily than they can penetrate an Ubuntu box? No.


No just the opposite that is if attackers can penetrate Ubuntu more easily in comparison to IPCop.

> **ian-weisser said:**
>  Or are you asking if you need something like IPCop to protect your  network's Ubuntu machines, or if they can protect themselves? Well, the  good admins I know generally believe in multiple and layered  defenses.

I was curious about that too but problem is in most cases its a troublesome thing to run a dedicated box as a firewall in a home environment simply because of the electricity costs. I have read people discussing this issue in other forums. 

Most homes however already use multilayer security. For example all DSL routers have built in firewall but IMO these home routers are quite vulnerable coz on my own PC I find ufw blocking incoming connections despite the router's firewall being active.

I guess the main issue here is outdated firmware. Most manufacturers are reluctant to provide firmware updates and  because most home users have little or no knowledge about network security there is little action.

---

