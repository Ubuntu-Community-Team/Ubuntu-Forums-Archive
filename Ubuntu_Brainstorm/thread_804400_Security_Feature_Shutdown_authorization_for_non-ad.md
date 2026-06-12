---
title: "Security Feature: Shutdown authorization for non-admin users"
date: 2008-05-23
forum: Ubuntu Brainstorm
---

### Post by irrdev on 2008-05-23
Let me recreate a scenario which has so far happened to me twice:
**1.** A user with administration privileges logs into Ubuntu. After some work, the user locks the screen and leaves.
**2.** A second user comes to the (locked) computer, and clicks "Switch User" to login to their own account, which does not have administration privileges.
**3.** After some work, the second user is finished. They have forgotten that the somebody was already logged onto the computer, however, and blissfully click "Shut Down". Ubuntu quietly kills all the processes still running by the first user, and shuts down.

The way Ubuntu is currently configured, any user can shut down the system at any time, no matter how many users are logged on or how many other processes are running. In the above scenario, if the first user was running any critical administration processes, such as software upgrades, there is a strong possibility that the computer will be messed up. This very situation has unfortunately occurred to me, and I was lucky that I had performed a backup the previous day. 
I am suggesting that non-administrative users are unable to shutdown the computer when a administrative user is still logged on. This would ensure that any critical processes would not be suspended/killed incidentally. While some users may never encounter this situation, the possibility still exists. Any thoughts or ideas on this matter?

---

### Post by chrisccoulson on 2008-05-23
If any non admin user is logged in locally to your machine, then you can't stop them from shutting down the machine. It doesn't matter how hard you try - all they have to do is pull the plug or press and hold the power button, and that is likely to do more damage than shutting down correctly.

I don't think it's a good idea.

---

### Post by insane_alien on 2008-05-23
i think this is a brilliant idea. though, if the non admin user is the only one logged in then they should be allowed to execute a shutdown. if other people ar logged in then it shouldn't shutdown for anyone but admin.

---

### Post by CrazyGuy123 on 2008-05-23
I agree with chris - a local user should always (by default) have shutdown priviliges because otherwise they'll pull the plug or hit the reset button doing more damage.  A warning would be good to have though.

It is already possible to configure this - see system > administration > authorisations > org.freedesktop.hal.power-management.shutdown-multiple-sessions

---

### Post by chrisccoulson on 2008-05-23
I agree with CrazyGuy about the warning. The framework is already in place really to be able to provide that. A warning is sufficient to stop most people from going further and shutting down the system, but still gives the local user the opportunity to make a decision. A sensible persion will decide to leave the system running when they see the warning, but a really determined person will shut it down regardless of whether you try to stop them - and pulling the plug is much worse than a clean shutdown.

---

### Post by pdwerryhouse on 2008-05-23
> **CrazyGuy123 said:**
> I agree with chris - a local user should always (by default) have shutdown priviliges because otherwise they'll pull the plug or hit the reset button doing more damage.  A warning would be good to have though.

There are ways to stop this. When I was the sysadmin at a university, we'd buy desks that locked the PC case away from the user. All they could get to was the screen, keyboard and mouse.

I did not ever want students taking it upon themselves to shut down PCs.

---

### Post by chrisccoulson on 2008-05-24
> **pdwerryhouse said:**
> There are ways to stop this. When I was the sysadmin at a university, we'd buy desks that locked the PC case away from the user. All they could get to was the screen, keyboard and mouse.

I did not ever want students taking it upon themselves to shut down PCs.

Alt+SysRq+O -> Shut off system

I only need access to the keyboard then

---

### Post by pdwerryhouse on 2008-05-24
> **chrisccoulson said:**
> Alt+SysRq+O -> Shut off system

I only need access to the keyboard then

That is easily disabled.

---

### Post by PmDematagoda on 2008-05-24
> **pdwerryhouse said:**
> That is easily disabled.

Not completely, if you want to do that completely, then you need to recompile a kernel with magic SysRq keys turned off.

But for the current use case, it will be sufficient.

---

### Post by chrisccoulson on 2008-05-24
> That is easily disabled.
But it isn't disabled by default, shouldn't be disabled by default, and likely won't be disabled by default. Which means that if any other attempt to restrict which users can shut down the system would end up being a half-assed attempt. This is worse than nothing.

Having computers locked away in a cupboard isn't typical of most installations. If you want to try and stop ordinary users from shutting the machine down, then please change the policies on your systems to do so (changing DBUS policies, disabling Alt+SysRq by compiling your own kernel, locking computers away, locking away all parts of the mains supply etc). Ubuntu should not implement a half-assed attempt to do this (which is what it would end up being)

---

### Post by lswest on 2008-05-24
It might be something worth considering for later releases, that is: at least prompt when shutting down that other users are logged in, so that if they do forget, they're reminded.

---

### Post by pdwerryhouse on 2008-05-24
> **chrisccoulson said:**
> But it isn't disabled by default, shouldn't be disabled by default, and likely won't be disabled by default. Which means that if any other attempt to restrict which users can shut down the system would end up being a half-assed attempt. This is worse than nothing.

Any serious system administrator who cares about his or her servers would do so, in a university environment. Students screw things up. If you don't take such precautions, you end up wasting time cleaning up broken machines that could be better spent improving the network.

---

### Post by chrisccoulson on 2008-05-24
> **pdwerryhouse said:**
> Any serious system administrator who cares about his or her servers would do so, in a university environment. Students screw things up. If you don't take such precautions, you end up wasting time cleaning up broken machines that could be better spent improving the network.

But how does doing this stop people from breaking things and screwing things up? It doesn't! 

If you're worried about people screwing things up, then there are more important things to focus your energy on as opposed to artificially restricting who can cleanly shut down a system.

In a university environment, each user has physical access to the machine (this is certainly the case in every educational establishment that I've been in). In this scenario, if a user wishes to shut down the machine, then all they have to do is pull the plug or press the power button

---

### Post by pdwerryhouse on 2008-05-24
> **chrisccoulson said:**
> But how does doing this stop people from breaking things and screwing things up? It doesn't!

Eh? Magic Sysreq keys turned off, computer locked away, and the user only has access to the keyboard, mouse and screen. If a user can break the machine in a situation like that, then there is something very wrong with the operating system.

---

### Post by chrisccoulson on 2008-05-24
> **pdwerryhouse said:**
> Eh? Magic Sysreq keys turned off, computer locked away, and the user only has access to the keyboard, mouse and screen. If a user can break the machine in a situation like that, then there is something very wrong with the operating system.

Like I said, machines locked away is not the norm. In every educational establishment I've visisted, in every public library and in every place I've been employed - I have yet to find a machine that is locked away. People have physical access to the machine. Home users have physical access to the machine. Most of Ubuntu's target audience have physical access to the machine that they're accessing, which is why this idea is all wrong.

If system administrators want to implement this type of policy, then they can (assuming that they've got all other bases covered). But it shouldn't be default, as it would end up just being a half-arsed attempt (like I have already said).

And disabling the magic SysRq combination by default is never going to happen anyway

---

### Post by pdwerryhouse on 2008-05-24
> **chrisccoulson said:**
> Like I said, machines locked away is not the norm. In every educational establishment I've visisted, in every public library and in every place I've been employed - I have yet to find a machine that is locked away. People have physical access to the machine. Home users have physical access to the machine. Most of Ubuntu's target audience have physical access to the machine that they're accessing, which is why this idea is all wrong.

If libraries aren't doing it, then it's because their administrators are probably amateurs. Universities should be locking them away, because I've seen just how screwed up machines become when students can get at them. There's nothing worse than being remotely logged into a machine and having some clueless kid  power it off.

I'm not talking about home users here. I was merely responding to your initial statement "It doesn't matter how hard you try - all they have to do is pull the plug or press and hold the power button", because it is patently not correct. As I have pointed out, there are things - physical things - you can do to stop it.

---

### Post by Gina on 2008-05-26
I believe a warning should be given where another user is still logged on.  This is the case with the most popular OS and much as I hate to say so - I think this is very sensible!

Of course you can't stop anyone determined to shut down but a warning would stop inadvertently upsetting another user's work by shutting down, as has been said.

---

