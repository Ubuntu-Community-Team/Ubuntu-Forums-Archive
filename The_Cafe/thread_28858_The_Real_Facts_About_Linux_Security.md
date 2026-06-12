---
title: "The Real Facts About Linux: Security"
date: 2005-04-21
forum: The Cafe
---

### Post by The Producer on 2005-04-21
Hello!

I'm currently researching several Linux topics in preparation for a project...potentially a large one...that I want to do.  Once the project becomes more mature, i'll post a link to it...

However, I want to know about Linux security.  I know it's ages ahead of Windows security, but just how secure is it?  How hard is it for a hacker to damage a Linux system?  How much would it take for a hacker, or hackers to do serious damage to a Linux system, if it was possible at all?

Thanks in advance!

---

### Post by poofyhairguy on 2005-04-21
[QUOTE=The Producer]
However, I want to know about Linux security.  I know it's ages ahead of Windows security, but just how secure is it?  How hard is it for a hacker to damage a Linux system?  How much would it take for a hacker, or hackers to do serious damage to a Linux system, if it was possible at all?
[/QUOTE]

As with any system, its only as secure as the admin that runs the computer.

Here is a link you need to read:

[http://en.wikipedia.org/wiki/Security-Enhanced_Linux](http://en.wikipedia.org/wiki/Security-Enhanced_Linux)

---

### Post by The Producer on 2005-04-22
Ok....nice, I'll need to bookmark this reference.

So...in a nut shell, it IS theoretically possible (without getting too techincal...) for a hacker, or group of hackers, with the right equipment, to hack into a Linux system?

---

### Post by TravisNewman on 2005-04-22
I don't care how sophisticated any computer system is-- someone can get into it. That's the unfortunate truth about anything.

---

### Post by HungSquirrel on 2005-04-22
Depends on what software the system is running, and if the machine is kept up-to-date.  The fewer listening network services, the lower the chance of a remote exploit.

There's no need for a 'theoretically' there.  Linux systems get compromised all the time, especially if the lazy admins don't update the system.  My host got cracked a few months ago because they were still running RedHat 9.

---

### Post by heimo on 2005-04-22
[QUOTE=The Producer]Ok....nice, I'll need to bookmark this reference.

So...in a nut shell, it IS theoretically possible (without getting too techincal...) for a hacker, or group of hackers, with the right equipment, to hack into a Linux system?[/QUOTE]

Uh. Have you stopped hitting your wife? (yes|no) _
EDIT: I understand my analogy is off. I was merely frustrated of the vagueness of your question.

Yes, it's perfectly possible to break (crack) into computer running Linux - most of the time using holes in software which is not part of Linux kernel. It happens all the time all around the world. All you need to do is install for example some older RedHat with everything on and leave it on the network with default settings for couple days. Someone will use some very old vulnerability to get root access to that computer.

Are you serious about doing study or research on computer security or specifically on Linux security? You need to check what The Honeynet project has done and you need to read about Bastille (something that's planned to be in Ubuntu some day, I guess). Securityfocus is nice place - and it's also very entertaining to read all those independent studies at Get the Facts campaign by Microsoft (I wouldn't mention this if the campaign didn't target Linux).

And yes, post a link when you can - I'm sure there's lots of people who'd like to look at it.

---

### Post by The Producer on 2005-04-22
> Are you serious about doing study or research on computer security or specifically on Linux security? 

OK, I guess I'll have to reveal it early...

I'm writing a story that's possibly going to be used in a cartoon/anime series, based around a possible future technology crisis.  One of the major factors of that story is Linux and the Open Source world....mainly it's security claims.

---

### Post by TravisNewman on 2005-04-22
nice! You must let us know when it's done.

---

### Post by poofyhairguy on 2005-04-22
[QUOTE=The Producer]
I'm writing a story that's possibly going to be used in a cartoon/anime series, based around a possible future technology crisis.  One of the major factors of that story is Linux and the Open Source world....mainly it's security claims.[/QUOTE]


If you would have given me a thousand guesses to figure out what you were needing the info for, that would be #436

---

### Post by heimo on 2005-04-22
[QUOTE=The Producer]OK, I guess I'll have to reveal it early...
 
I'm writing a story that's possibly going to be used in a cartoon/anime series, based around a possible future technology crisis. One of the major factors of that story is Linux and the Open Source world....mainly it's security claims.[/QUOTE]
 
Great! I love the subject. Lots of possibilities there. And I like that you're doing background study - probably to make it sound more plausible? Interesting subject, indeed. It's awful to watch movies which are able to get all the technology related facts wrong. Probably "the great audience" won't notice a thing, but anyone with any experience on subject will feel uncomfortable and will be unable to enjoy. At least I'm like that. Details matter.

---

### Post by ubuntu_demon on 2005-04-22
a fully updated linux without running services open to the internet is very hard to crack. They would have to exploit something before the cure is found (find the exploit themselves or be really really fast when it gets known). So this is not possible for scriptkiddies. Only advanced hackers can do this.

But as the amount of running services open to the internet increases the risk of being hacked. (still this would be a good hacker unless you have misconfigured something)

this risk increases in two ways :
1) you will become a more interesting target because they think they have more chance
2) they have more chance

not fully updating / misconfiguring / running a lot of services open to the internet .. those are the real problems. These things are not the case in a default install of ubuntu. But you have to do your updates! Running a firewall also helps a little but isn't even sctrictly necessary for a default install. (I like to run one because I'm paranoid  and I have a couple of ports open:-P)

---

### Post by defkewl on 2005-04-22
If you want the real secure OS, you should go to OpenBSD

Only one remote hole in the default install, in more than 8 years!

Haha. I think linux was made to give a choice for users that don't want windows or can't afford to buy windows.

---

### Post by nautilus on 2005-04-22
I've never had a server (under my care) exploited, and they have all been Linux servers..

That said, since I'm a software developer I primarily run my own software on my servers, and common-sense tells me the most secure way to run services would be by way of chroot or dropping of permissions, both of which I regularly employ.

As for workstations... Well, never had a problem there either.

Sure, latest patches is fine and nice, but in the end the answer is not running services you don't understand, or software in general for that matter.

Here's an idea of what my workstation has 'available' to be prodded by the outside world:

```
tcp        0      0 0.0.0.0:5000            0.0.0.0:*               LISTEN     27174/vtund[s]: wai
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN     6294/master
tcp6       0      0 :::80                   :::*                    LISTEN     27238/lhttpd2
tcp6       0      0 :::22                   :::*                    LISTEN     6412/sshd
tcp6       0      0 ::1:25                  :::*                    LISTEN     6294/master

```

now, vtund is a VPN program, which i co-develop, master is some smtp thing that ubuntu comes with, but it's not available publically, sshd is openssh which is trash, and in thinking about it i should really install dropbear, and lhttpd2 is a webserver i wrote..

so now, is my network stack all secure?  hmm... well, i haven't seen any exploits in the kernel lately, so it's secure enough for me.

okay, so these are vague blanket answers, but in summary i've never had a problem, and i feel far more confident with my linux system than any other OS (except Syllable) available.

one more note; a well-admined Win2k server may be more secure than a poorly-admined Linux server.  i'm still debating that point, though..

---

### Post by plb on 2005-04-22
[QUOTE=defkewl]If you want the real secure OS, you should go to OpenBSD

Only one remote hole in the default install, in more than 8 years!

Haha. I think linux was made to give a choice for users that don't want windows or can't afford to buy windows.[/QUOTE]

Great OS for security, although performance is not up to par with say linux or FreeBSD, also doesn't make the best desktop enviroment either imho

---

