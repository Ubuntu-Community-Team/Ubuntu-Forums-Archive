---
title: "[SOLVED] isnt windows multi-user"
date: 2008-07-12
forum: Windows
---

### Post by dexter.deepak on 2008-07-12
i understand multitasking, but i have always a problem understanding multiuser concepts, and unluckily, wikipedia is not of much help to me this time.
this is what i came across here:
[http://wiki.answers.com/Q/What_is_meant_by_multiuser](http://wiki.answers.com/Q/What_is_meant_by_multiuser)
> All time-sharing systems are multi-user systems,
this seems ambiguos with the multitasking concepts.
> The most obvious example is a Unix server where multiple remote users have access (via Telnet or Ssh) to the Unix shell prompt at the same time. Another example uses multiple X sessions spread across multiple monitors powered by a single machine.
though i have never tried telnet/ssh , i have heard windows user use telnet too.

i have also seen tomcat as a user in the windows system...i.e ,all the servlets/jsp i run on a windows system are run by the user named tomcat (although it has not got a login shell).
these points shake off my concepts (probably i have none:mad:)

or is it that the multi-user thing is just a matter of licence ??

---

### Post by geraldm on 2008-07-12
Early Operating Systems were single-tasking, where an application was run as a portion of the single task.  Then the application finished, and the system reboots.
Later, OS developed into multi-tasking, able to execute many different tasks simultaneously.  
As part of multi-tasking, there would be programs which allow a user to log into the system and execute tasks.  
Multi-user means that there can be more than one user, each able to execute his separate tasks. 

Gerald

---

### Post by dexter.deepak on 2008-07-13
this is what i have been reading in the manuals ...i want some practical examples, and the clarification of my above question.

---

### Post by lisati on 2008-07-13
**Multitasking** is about having more than one thing going on in the computer at the same time,
**multi-user** is about who is allowed to use the computer, and CAN mean letting allowing more than one person to use the computer at the same time.

**Time sharing** is about dividing up the time between different users (or programs), and has nothing to do with holiday properties.

Yes, Windows has multitasking and remote connection capabilities.

---

### Post by p_quarles on 2008-07-13
Moved to Windows Discussions.

Yes, Windows is a multi-user system.

---

### Post by txcrackers on 2008-07-13
"Multi-user" is actually kind of a squishy subject - it's usually defined by what a vendor is trying to sell you.

Generally, a multi-user, multi-tasking system is one that allows more than one person to be executing tasks/programs at the same time. Example: I can use SSH to log onto my wife's laptop, while *she's* using it and "do stuff" without interrupting whatever she's doing.

Servers and server-based applications tout multi-user meaning more than one user can use the software at the same time (Microsoft Exchange is probably a familiar example.) However, you're not "doing stuff" on the same physical system as your office mate, but you're both accessing the server application through your mail clients.

As for licensing, it **can** be based on a "per-user" basis (see Exchange above) or, well, pretty close to zero cost for any number of users (e.g. Linux distributions).

Windows is not really "multi-user" in the sense of the first term (which is the more technically correct definition) since it's tied so heavily to a GUI. It's geared around only allowing one person at a time to use it.

---

### Post by p_quarles on 2008-07-13
> **txcrackers said:**
> Windows is not really "multi-user" in the sense of the first term (which is the more technically correct definition) since it's tied so heavily to a GUI. It's geared around only allowing one person at a time to use it.
That's true to an extent, but remote desktop does allow for simultaneous users. Still, the multi-user Windows is more Windows Server rather than XP or Vista. And at a very basic level, XP and Vista are designed to be used primarily as self-sufficient workstations rather than multi-user systems, so the multi-user aspect is more of a capability than a primary usage.

---

### Post by dexter.deepak on 2008-07-13
thanks to all of you.
what i had earlier said , i have no doubts over multitasking but only over multiuser concepts.
if both unix and windows are both multiuser, why's there so much hype in unix world over the "multiuser" thing ?? is it just because windows introduced this feature later than unix ?

and is it "legal" to have a remote login from linux to windows ?

---

### Post by lisati on 2008-07-13
> **dexter.deepak said:**
> 
and is it "legal" to have a remote login from linux to windows ?

As long as the admin and/or user of the windows machine is ok with it, I don't see a problem.

 It might also be argued that it makes sense to use a linux machine to login to a windows machine, because of the lower risk of Linux being hurt by its contact with Windows than if you'd used another Windows machine to do the job....

I regularly use my Linux machine to monitor & control my Windows machine

---

### Post by fiddledd on 2008-07-13
AFAIK Unix, which Linux has it's roots in, was designed as a Multi User OS from the start. Windows, however, was designed as a Single User OS and added the Multi User capabilities later.

I can see no reason why a Remote Login from Linux to Windows would be illegal, unless you are trying to hack into it. But I'll happily be corrected if I'm wrong.

---

### Post by gordonh on 2008-09-05
> **fiddledd said:**
> AFAIK Unix, which Linux has it's roots in, was designed as a Multi User OS from the start..

Very late response, but in fact, Unix was originally a single user version of a multi user OS called Multix (or something like that).

When it became popular multi user capability was added into unix and so since then it's been a misnomer.

---

### Post by fballem on 2008-09-05
An observation that _may_ add some clarity to the original question from someone who has used Microsoft operating systems since the days of DOS and has been exposed to Unix systems since curses.

The major difference between the two lies in their roots.

DOS/Windows started life as an operating system for a personal computer. When the computer was started, the expectation was that it was a single user and that they had full access to their computer. Even to-day, unless you specifically limit the user, most users run with Administrator privileges on their workstation. They can easily install applications and gain access to any part of the computer that is physically attached to the computer. This high level of access is one of the reasons why viruses and other bad things can easily happen on windows. As computer needs became more sophisticated, features were added to Windows, but at the core, it is an operating system that is specifically geared for a user running a workstation.

Unix started life as an operating system for servers and connected workstations. In that environment, users are generally given specific permission to access specific resources on the computer. In order to have full access to the computer, the user must have administrative privileges, which is not the norm. GUIs and other applications (including GNU/Linux) were developed, but still worked within the core paradigm of user privileges, even on a workstation. This is the reason why you have to log in as root (or use sudo) to install/update applications. This structure is why it is more of a challenge for viruses and other bad things to happen on a Linux system.

There are advantages to each approach (ease of use in Windows, security in Linux) and there are strategies to mitigate the disadvantages to each approach (Antivirus, etc. to improve Windows security, GUIs for Linux to make applications easier for users).

Hope this helps, and if I've made errors in the observations, then I would appreciate any additional clarity.

Thanks,

---

