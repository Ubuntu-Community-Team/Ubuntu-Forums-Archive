---
title: "What's your favorite way to not run Windows XP as admin?"
date: 2008-07-29
forum: Windows
---

### Post by aysiu on 2008-07-29
I'm in talks with my school's tech department about trying to implement better security for our Windows computers, and I'd like to know all the options available. The problem, of course, is finding a balance between security and usability.

We don't want people complaining they can't do anything on their computers. We also don't want them all running as admin all the time.

Right now, the most promising thing I've found is SuRun.

Any other suggestions?

---

### Post by flytripper on 2008-07-29
the best way would be to run a domain and active directory i think.

---

### Post by aysiu on 2008-07-29
> **flytripper said:**
> the best way would be to run a domain and active directory i think.
Well, we are on a domain, actually. I don't know what active directory is, but does that allow the user to basically be limited most of the time and temporarily escalate to administrator privilege (a la Ubuntu's *sudo*)?

---

### Post by flytripper on 2008-07-29
active driectory is what you use to administer a user/permissions list. if all users are on that system and all computers connect to that domain via log in the the administrator has complete control over what can be accessed and how.

Juding by your status I see you must be linux flavoured Guru, sent to educate the masses >.<
[active directory]("http://www.webopedia.com/TERM/A/Active_Directory.html").

Hope this helps

---

### Post by mordak13 on 2008-07-29
LOL!!! My answer was to install Linux and be done with it. :cool:

---

### Post by aysiu on 2008-07-29
[quote=definition from link]A directory service from Microsoft that is a part of Windows 2000. It is an implementation of Internet standard directory and naming protocols that uses a database engine for transactional support, and also supports a variety of application programming interface standards[/quote] I don't really understand what that means. So does that allow users to be limited users and temporarily escalate to administrator privileges easily for certain tasks?

---

### Post by flytripper on 2008-07-29
apologies. thats not a very good desription.this is a bit better_[directory service]("http://www.webopedia.com/TERM/A/directory_service.htm")

---

### Post by flytripper on 2008-07-29
this may help [ gpedit.msc]("http://vlaurie.com/computers2/Articles/group_policy_editor.htm"). its host os configuration (not server based)but it does enable you to limit things for guest users.

---

### Post by aysiu on 2008-07-29
Well, I'm not understanding you or you're not understanding me. It could be both.

I appreciate you're trying to help, but talk to me as if I'm an idiot, because when it comes to administration and networking, I am, especially when it comes to Windows, as opposed to Linux.

We don't want to make everyone a limited user. We also do not want to make everybody administrator all the time. The idea is to approximate as possible the *sudo* implementation that Ubuntu and Mac OS X have, so that every user *can* administer her own machine but won't be running as administrator all the time.

The links you posted are way over my head. Do they allow for that?

---

### Post by flytripper on 2008-07-29
I see. xp simply doesnt work like that.. vista does with its "wateva" its called security nag password thing.

the AD / active directory (group policies)is what you would use to allow a users and groups of users acces to one program and not the other ,have certain menu entries and not others, be restricted from accessing the command line or not.

---

### Post by aysiu on 2008-07-29
> **flytripper said:**
> i see. xp simply doesnt work like that.. vista does with its "wateva" its called.
Yeah. It's kind of a problem with XP, which is why I wanted to throw out to the community and ask what the best workarounds are. So far, SuRun isn't looking too bad.

---

### Post by Joeb454 on 2008-07-29
Is there any significant issues with running as a Limited User & using Run as... to give elevated privileges?

Domain & Active Directory is what my old school used I believe, though I have no idea how to set it up :p

---

### Post by cardinals_fan on 2008-07-29
I used #1 back in my XP days.

---

### Post by flytripper on 2008-07-29
never saw surun before and it looks nice.... however, you are at a school and from experience if you create a weakness it will more than likely get exploited. I don't know how but kids get through the loopholes in security all the time to be able to do what they shouldn't, albeit mainly to browse sites via proxy avoidance!! i do wonder now if that may have helped with a particular program that i couldn't get to work constantly  on all the machines.. there was a permissions anomaly somewhere as it wanted to write to a place other than its own folder. hmmmm

---

### Post by Mgiacchetti on 2008-07-30
i was told once on irc that one "should not use guest" because it "causes security problems" so i just use ubuntu.

---

### Post by rickyjones on 2008-07-30
There are a lot of ways to do this and here are my recommendations.

1. Leverage a Windows Server 2003 Active Directory Domain. This will give the school central control over users, groups, computers, printers, passwords and Group Policy.

2. Create a group in Active Directory that is a member of the "Users" group on each workstation. This is controlled via a Group Policy setting (see "Restricted Groups")

3. On a master workstation determine what applications will require Administrative privileges to operate. On the necessary registry keys and program folders assign Full Control permissions to the global Active Directory group that you created.

This will take time to roll out to each workstation in use but, once applied to a master copy, then all new workstations will be ready to go.

A setup like this will allow users to to run as Limited but still use their applications. In a school environment I'm going to guess that requiring all users to remember two usernames and passwords (a standard ID and an administrative ID) might be too much. In addition what will prevent the users from just using their administrative ID to install software when they feel like it? My above recommendation will solve that headache but will require some additional administrative overhead to roll it out.

There might be third party applications that will help with this process. Group Policy might even be able to assist with assigning global permissions to registry keys and file systems, but I'm not positive on that.

I urge you to research the tools are you disposal before trying to convert to a new system. If you already have Active Directory in place then everything you need is available.

Sincerely,
Richard

---

### Post by fiddledd on 2008-07-30
I've always used a LUA in XP so I'm probably not typical. That aside, I tried Sudown and, although better than Run As, it wasn't what I was looking for, so I'm now using surun. It's about as close as you can get to Vista's UAC with XP. I can even open an Explorer windows with Admin rights without logging on as Administrator. If you haven't used surun or read how it works that last sentence might scare you a bit. Anyway, I've found nothing better than surun.

---

### Post by aysiu on 2008-07-30
I think I'm going to suggest SuRun to the tech department. As far as I know, they already have Active Directory and know how to use it, so that probably doesn't fit their purposes.

---

### Post by fiddledd on 2008-07-30
> **aysiu said:**
> I think I'm going to suggest SuRun to the tech department. As far as I know, they already have Active Directory and know how to use it, so that probably doesn't fit their purposes.

Unless there's another option I'm not aware of, I think you are making the right choice.

---

