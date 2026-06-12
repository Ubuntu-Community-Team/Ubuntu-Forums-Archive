---
title: "Vector smash protection.   What is it."
date: 2016-02-29
forum: Ubuntu, Linux and OS Chat
---

### Post by poorguy on 2016-02-29
Hello All,

Can someone explain  "Vector smash protection" I see it when using Firefox from within the terminal.
Does it make my web use any more secure.  
Google doesn't really explain what it is.

Thanks.

---

### Post by poorguy on 2016-03-01
Wow!

What a stumper.
I couldn't find anything out about what it is.

Perhaps it may be a bug.
It also appears when using Elinks Web Browser.
Still uncertain what it may be other than a stumper.

Thanks.

---

### Post by grahammechanical on 2016-03-01
I really do not know enough to give a specialist answer. For it is a specialist question. But from the very little reading that I have done on this subject I have worked out an explanation that satisfies me. So, on the understanding that I am most likely completely and utterly ill-informed, this is my explanation:

It is all to do with stack overflow. A stack is a section of memory where applications put data. A badly written application may push too much data into the stack causing it to overflow or to use the technical term, "smash the stack." A stack overflow will cause the application to crash.

Stack overflow has the potential to be an attack vector. A malicious person may introduce code on to the machine that deliberately causes a stack overflow which allows the malicious person to take control of the program that is running for his own purposes.

Smash Protection is a way of stopping an application from causing a stack overflow. And since stack overflow or stack smash, as we say in the trade, is an attack vector then vector smash protection being enabled in an application such as a web browser is good.

Well, it is answer that satisfies me even if it is completely bonkers.

Regards.

---

### Post by poorguy on 2016-03-01
[**[COLOR=#000000][URL="http://ubuntuforums.org/member.php?u=1087323"][B][COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323")[/COLOR][/B][COLOR=#000000][/COLOR][/URL]Hey grahammechanical,

What you come up with actually makes more sense then what I was able to figure out or find.
I started using Elinks Web browser and that is where I started seeing it.
I definitely appreciate your wisdom on this as I wasn't doing any good with my searches.

As you mentioned in your post and I agree "Well, it is answer that satisfies me".

Thank You.

---

### Post by mc4man on 2016-03-01
Maybe from flash - 
> :~$ strings  /usr/lib/flashplugin-installer/libflashplayer.so  | grep smash
Vector smash protection is enabled.

---

### Post by Mike_Walsh on 2016-03-02
Hey, poorguy.

This is the only reference I've been able to find with regards to 'vector smash protection'.

[http://www.vbforums.com/showthread.php?802991-vector-smash-protection-is-enabled](http://www.vbforums.com/showthread.php?802991-vector-smash-protection-is-enabled)

4th post down. Something to do with Java, videos, and denying access to certain websites...


Mike. ;)

---

### Post by vasa1 on 2016-03-02
Does what you see happen every time or is it associated with a particular type of site?

[http://stackoverflow.com/questions/32058697/flash-movie-only-renders-in-chrome-not-webbrowser-control](http://stackoverflow.com/questions/32058697/flash-movie-only-renders-in-chrome-not-webbrowser-control)
[https://forum.palemoon.org/viewtopic.php?t=9279](https://forum.palemoon.org/viewtopic.php?t=9279)

---

### Post by vasa1 on 2016-03-02
> **Mike_Walsh said:**
> Hey, poorguy.

This is the only reference I've been able to find with regards to 'vector smash protection'.

[http://www.vbforums.com/showthread.php?802991-vector-smash-protection-is-enabled](http://www.vbforums.com/showthread.php?802991-vector-smash-protection-is-enabled)

4th post down. Something to do with Java, videos, and denying access to certain websites...


Mike. ;)

Do you see the little bug moving around near the bottom right of posts by dday9 in your link?

---

### Post by Mike_Walsh on 2016-03-02
Yep, certainly did. Seen it before, too; can't remember **where **off the top of my head, though.....


Mike. ;)

---

### Post by grahammechanical on 2016-03-02
> **Buffer overflow protection** refers to various techniques used during software development to enhance the security of executable programs by detecting [buffer overflows]("https://en.wikipedia.org/wiki/Buffer_overflow") on [stack]("https://en.wikipedia.org/wiki/Call_stack")-allocated variables, and preventing them from causing program misbehavior or from becoming serious [security]("https://en.wikipedia.org/wiki/Computer_security")  vulnerabilities. 

A stack buffer overflow occurs when a program writes  to a memory address on the program's call stack outside of the intended  data structure, which is usually a fixed-length buffer. Stack buffer  overflow bugs are caused when a program writes more data to a buffer  located on the stack than what is actually allocated for that buffer.  This almost always results in corruption of adjacent data on the stack,  which could lead to program crashes, incorrect operation, or security  issues.


> Typically, buffer overflow protection modifies the organization of stack-allocated data so it includes a *[canary]("https://en.wikipedia.org/wiki/Stack_canary")*  value that, when destroyed by a stack buffer overflow, shows that a  buffer preceding it in memory has been overflowed. By verifying the  canary value, execution of the affected program can be terminated,  preventing it from misbehaving or from allowing an attacker to take  control over it. Other buffer overflow protection techniques include *[bounds checking]("https://en.wikipedia.org/wiki/Bounds_checking")*, which checks accesses to each allocated block of memory so they cannot go beyond the actually allocated space, and *tagging*, which ensures that memory allocated for storing data cannot contain executable code.

> Stack-smashing protection is unable to protect against certain forms of attack.

[https://en.wikipedia.org/wiki/Buffer_overflow_protection](https://en.wikipedia.org/wiki/Buffer_overflow_protection)

I think the mention of Canary values is a reference to the use of live canaries by coal miners to detect the presence fire damp gas. When the little bird falls off its perch dead, then you know that explosive gas is around. Although this practice was rendered obsolete by the invention of the miner's safety lamp by Humphrey Davy it seems that computer programmers are still finding some use for canaries. :)

Regards

---

### Post by poorguy on 2016-03-02
> **vasa1 said:**
> Does what you see happen every time or is it associated with a particular type of site?

[http://stackoverflow.com/questions/32058697/flash-movie-only-renders-in-chrome-not-webbrowser-control](http://stackoverflow.com/questions/32058697/flash-movie-only-renders-in-chrome-not-webbrowser-control)
[https://forum.palemoon.org/viewtopic.php?t=9279](https://forum.palemoon.org/viewtopic.php?t=9279)

When I open Elinks Web Browser  Vector smash protection appears upper left hand corner and it is all the time / everytime.
Seems I do remember reading something about streaming videos and flash with  Vector smash protection being a bug and creating an error.

---

### Post by poorguy on 2016-03-02
> **vasa1 said:**
> Do you see the little bug moving around near the bottom right of posts by dday9 in your link?

Not always but sometimes.

---

### Post by poorguy on 2016-03-02
> **Mike_Walsh said:**
> Hey, poorguy.

This is the only reference I've been able to find with regards to 'vector smash protection'.

[URL="http://www.vbforums.com/showthread.php?802991-vector-smash-protection-is-enabled"]http://www.vbforums.com/showthread.php?802991-vector-smash-protection-is-enabled

[/URL]

4th post down. Something to do with Java, videos, and denying access to certain websites...


Mike. ;)

Hey Mike, 

Your link above is where may have read about the streaming of videos with this issue.
Yeah there doesn't seem to be a lot to be found about it.

What is strange it only pops up when I am using Elinks WEb Browser.

---

### Post by mariobalotelli on 2016-09-16
i have same problem. vector smash protection is enabled and auto close my firefox.
anyone can fix that?

---

