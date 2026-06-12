---
title: "[SOLVED] Pros and cons of running server and desktop on same comp? (share opinions)"
date: 2006-07-26
forum: Server Platforms
---

### Post by RavenOfOdin on 2006-07-26
Just wanna see what y'all think about this idea and hopefully get some input from people who have multiple computers and the freedom to dedicate them to different duties.

I can think of a couple right now:

Pro: Easier to switch between different tasks.
Con: For whatever kernel model you're using, one task just doesn't fit.

Pro: Better if you're strapped for cash and can't afford two computers.
Con: If your server gets compromised, you may lose everything from your office documentation to the pr0n folder sitting right next to it.

:D

(LATE EDIT: Oops, didn't notice where this was posted. If its better off in the Servers forum, then move thusly please.)

---

### Post by LordHunter317 on 2006-07-26
I'm not sure the first pro/con is really true.

Virtually every OS but Linux gets by with only two kernels per arch: SMP and non-SMP. If there are more, it's usually not due to performance or feature related-issues.  It's generally due to features at the kernel core some CPUs don't support (e.g., ACPI).

That doesn't mean that you couldn't get better performance by specializing, but I do believe from a overall perspective the complexity in management caused by having custom or different kernels is too high to be worth it.  The performance gain just usually isn't enough.

As to be relevant to the forum, the only real disadvantage for having your desktop be your server is that the XOrg server is waking security nightmare.  Other than that, it doesn't matter so much.

---

### Post by RavenOfOdin on 2006-07-26
> **LordHunter317 said:**
> 
As to be relevant to the forum, the only real disadvantage for having your desktop be your server is that the XOrg server is waking security nightmare.  Other than that, it doesn't matter so much.

I'll remember that, but shouldn't I be able to get by disallowing connections to the X server through port 6000?

---

### Post by LordHunter317 on 2006-07-26
Not really, as that's not what I meant.

Xorg has a terrible architecture w.r.t. privilege seperation.  The OpenBSD folks have done some, but not exhaustive, work on fixing that.

It also has a terrible security track record w.r.t. security and virtually every exploit for it is a root exploit.  

Running X could very well give an attacker an easy local-root exploit, FWIW.

---

### Post by sysops on 2006-08-22
well, i know the thread's quite old but i'll contribute 2 cents anyway.

Pros.

Everything's right here on the local machine, publishing content to web/ftp/nntp, etc servers is just a matter of copying files to the right directories.

You are pretty much logged on all the time, you have first hand, immediate 'knowledge' of activity on the server (provided you have that functionality setup). Viewing logs, testing, debugging etc is easier and that's why it's recommended you have your own local server to test content on before you publish it on/to the internet.

Cons.

The Processor/Memory Load of processes of the console user(s) can (most definitely will) get in the way of the essential 'server' services. But i shall assume that your presence on the machine isnt too detrimental to the functioning of these services, otherwise you surely would have used a purpose-oriented dedicated machine as the 'server'.

The installation and use of some insecure non-server applications like X/Xorg/XCDMP etc, etc potentially open your machine up to the internet. I assume you don't mind if 'hackers' on the internet atempt to compromise your machine and destroy your data, otherwise you surely would have used a secure dedicated machine as the 'server'.

Overall, it's a good thing running a server/desktop as one, you learn a lot about the workings of your server and desktop at the same time but if you err on the side of safety (paranoia actually) you can always take that old 486/12MB RAM and install ubuntu LAMP on it and leave it running in the corner. ;)

Cheers,

Sysops

---

