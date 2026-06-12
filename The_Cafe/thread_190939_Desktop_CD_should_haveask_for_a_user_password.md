---
title: "Desktop CD should have/ask for a user password"
date: 2006-06-06
forum: The Cafe
---

### Post by Jucato on 2006-06-06
... even if the password is just "ubuntu".

Probably not many users are aware of the fact that the Desktop CD has normal user with no password. The user name is "ubuntu", while the password is blank. This fact only becomes known/visible if you log out or end the current session, without shutting down or restarting. Whenever you do something that requires root privileges, you are automatically accepted as root, because the password is blank. While this is very convenient, I think it should not be the case.

My suggestion stems from three things:

1. The Desktop CD is a sort of preview or glimpse of Ubuntu and Linux in general. As such, it should contain the spirit and features of Ubuntu. And one of those is the advocacy of the use of sudo. We've heard countless debates about root/su vs. sudo, yet Ubuntu has not wavered on it's stand. So why should the Desktop CD act differently? Also, the Desktop CD give new/potential users the chance to get know how Ubuntu does things, like no built-in MP3 support. Similarly, new users should be informed of the fact that Ubuntu does things the sudo way and how to do it. This might also make their transition into Ubuntu a lot easier. As the Desktop CD gets more popular and the Ubiquity installer (hopefully) gets more refined, more new users will be using it to try out Ubuntu, rather than directly installing it using the Alternate Install CD. A simple note on the download site, or on the login background telling the user what the user name and password and that this is the Administrator password should be enough. Then once logged in, they can go and investigate this matter further.

2. It is just as easy to commit fatal errors using the Desktop CD as it is on an intalled system, especially when it comes to disk drives. Asking for the user password (which is the same as the Administrator password) could give a visual clue/reminder that what they will be doing will have a permanent impact on the system. We can't assume that everyone using the Live CD will absolutely know what they are doing. In fact, the Live CD is meant to be used by new users, who might also be new to Linux. Not mounting all drives/partitions by default (unlike in KNOPPIX) might be a good safety measure, but that isn't enough.

3. This is probably the least important factor: it gives users a chance to actually see the login/KDM/GDM screens. I just can't imagine why we have beautiful login screens, but don't normally see them on the Desktop CD. Unless of course you log out. But how many people would do that?

I might be the only one to feel this way, but I still think that the Desktop CD should really capture the Ubuntu spirit and way of doing things. I wonder, though, if this thing is important enough to actually file for a sort of "wish list" report.

---

### Post by aysiu on 2006-06-06
I can see where you're coming from, but I completely disagree.

Having *sudo* doesn't give a preview of security if you broadcast the password to the world or make it such a simple one to guess as *ubuntu*.

The live CD does not preview Ubuntu in every way--for one thing, it's a lot slower, since it runs out of your computer's RAM.

It does not pose the same security risk, since the hard drives are not mounted unless you go out of your way to mount them during the live CD session.

If users want to see the login screen, they can log out during the live session. They'll automatically be logged back in again after ten seconds... and the login screens really aren't that great-looking, but that's just my opinion.

---

### Post by Jucato on 2006-06-06
(Wow, I guess this would be the first time I would be disagreeing with the great aysiu! :D)

[QUOTE=aysiu]Having *sudo* doesn't give a preview of security if you broadcast the password to the world or make it such a simple one to guess as *ubuntu*.[/QUOTE]
Neither does having a root user with a password of root "root". But MEPIS does it, and I don't think they have an issue with it. I'm not sure about KNOPPIX. I might try it out later. Don't get me wrong, I'm not saying that sudo in the Desktop CD gives a preview of security per se. I'm saying that it gives a preview of how Ubuntu implements security.

> The live CD does not preview Ubuntu in every way--for one thing, it's a lot slower, since it runs out of your computer's RAM.

True. But then that's also true for all other Live CDs. What I'm saying is that it at least should give a glimpse of *how* Ubuntu implements stuff, not how fast or well Ubuntu performs on a system. If the Desktop CD does not mount partitions by default or does not have a root account, both of which are Ubuntu-only implementations, why not implement sudo as well?

> It does not pose the same security risk, since the hard drives are not mounted **unless you go out of your way to mount them during the live CD session**.

And that is, in one way or another, opening a risk. It may not be a security risk, but it's a risk nonetheless. But not just with mounting partitions, it could also tell users that doing something that requires root privileges and a password will have an impact on their system. This goes for things like display drivers and some other stuff. And I'm also not just talking about GUI-based apps, but CLI-based as well, like pppoeconf, for example.

> If users want to see the login screen, they can log out during the live session. They'll automatically be logged back in again after ten seconds... and the login screens really aren't that great-looking, but that's just my opinion.

How many people will actually log out just to see the login screens? How many new users (new to Ubuntu or new to Linux) would know that they're even there? In fact, how many people using the Desktop CD would even have the need to logout (aside from resetting the X server). Also, getting logged back in after 10 seconds is GDM only. Kubuntu doesn't have that, last I remember. Ok maybe the artwork isn't entirely "wow" material, but it's something that people work hard for. But like I said, that's just a minor consideration.

My main consideration is actually what Live CDs are for: to give you a chance to try a distribution out and to see what it has to offer. Having a password enabled in the Desktop CD will allow people to see how Ubuntu works/does things, the Ubuntu-way, so to speak. 

But then again, that's personal opinion. :D

---

### Post by aysiu on 2006-06-06
[QUOTE=Fenyx](Wow, I guess this would be the first time I would be disagreeing with the great aysiu! :D)[/quote] No sweat. We all have different opinions about stuff.

> 
Neither does having a root user with a password of root "root". But MEPIS does it, and I don't think they have an issue with it.  I had an issue with it when I was a Mepis user. I just thought it was dumb. Why make a password if it's so easy to guess? But I may be the minority in that opinion. > I'm not sure about KNOPPIX. Knoppix does not ask for a password and, like Ubuntu, doesn't have a login screen either. 

I think you bring up some good points, Fenyx. I think you have a good line of reasoning... I just personally don't agree with it.

---

### Post by Jucato on 2006-06-06
Well, from a security point of view, I guess it is stupid to publicize a password. But security should be the least of your worries when using a Live CD, right?

I forgot to mention one more thing. Not asking for a password gives the impression that you are running as root or that the default user is root, just as you would in Windows XP. But Linux is different. 

If other Live CD's don't ask for passwords, then maybe I'm totally off the mark. Anyway it was just a suggestion. I might, or might not, file it in Launchpad.

Btw, I never liked KNOPPIX's artwork anyway, so I don't mind not seeing it login screen. I wonder if KNOPPIX has a user with a blank password, or is running as root. If it is, that's another thing that would make me dislike KNOPPIX more. :p

---

