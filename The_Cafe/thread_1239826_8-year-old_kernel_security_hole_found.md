---
title: "8-year-old kernel security hole found"
date: 2009-08-13
forum: The Cafe
---

### Post by Foster Grant on 2009-08-13
[http://www.theregister.co.uk/2009/08/14/critical_linux_bug/](http://www.theregister.co.uk/2009/08/14/critical_linux_bug/)
> Linux developers have issued a critical update for the open-source OS after researchers uncovered a vulnerability in its kernel that puts most versions built in the past eight years at risk of complete takeover.

The bug involves the way kernel-level routines such as sock_sendpage react when they are left unimplemented. Instead of linking to a corresponding placeholder, (for example, sock_no_accept), the function pointer is left uninitialized. Sock_sendpage doesn't always validate the pointer before dereferencing it, leaving the OS open to local privilege escalation that can completely compromise the underlying machine. . . .

"This passes my it's-not-crying-wolf test so far," said Rodney Thayer, CTO of security research firm Secorix. "If I had some kind of enterprise-class Linux system like a Red Hat Enterprise Linux...I would really go check and see if this looked like it related, and if my vendor was on top of it and did I need to get a kernel patch."

Gotta figure new kernel updates coming into the repos, maybe as soon as tonight ...

---

### Post by Methuselah on 2009-08-14
Good.
Open source doesn't have the benefit of 'security through obscurity'.
Since the code is open for public scrutiny best practices must be followed and it makes for better software overall.

---

### Post by gletob on 2009-08-14
> **Foster Grant said:**
> [http://www.theregister.co.uk/2009/08/14/critical_linux_bug/](http://www.theregister.co.uk/2009/08/14/critical_linux_bug/)


Gotta figure new kernel updates coming into the repos, maybe as soon as tonight ...
Great.  This is not good for my server uptime.  But security fixes are good.

---

### Post by MaxIBoy on 2009-08-14
If you've read slashdot recently, you'll know that kernels going all the way back to 2.4.x have had a [security vulnerability](http://blog.cr0.org/2009/08/linux-null-pointer-dereference-due-to.html) which was recently discovered. This includes most architectures (i.e. if you use a PPC or something, don't assume you're safe!)

This vulnerability is trivial to exploit. A malicious program can easily use it to gain kernel-level permissions.

**[This issue has been fixed](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=e694958388c50148389b0e9b9e9e8945cf0f1b98)**. If you are capable of doing so, I recommend downloading a git snapshot kernel and compiling it. 

If you are unable to compile a kernel, be a bit more cautious for the next few days. As far as I know this can only be exploited through compiled programs, so you don't have to worry about malicious javascript in web-pages or anything like that. Also the repositories are still safe, I think you'll be fine if you don't install anything outside the repos. This patch will probably get applied to old kernels soon and you'll be seeing it as an update.

---

### Post by hellmet on 2009-08-14
Thanks for letting us know.

---

### Post by samjh on 2009-08-14
Good thing they've found the error.  Bad thing is this will give Linux's opponents ammunition about how using amateurs programmers and volunteers result in poor security, and how FOSS's community development model is not secure.

---

### Post by Eisenwinter on 2009-08-14
> **samjh said:**
> Good thing they've found the error.  Bad thing is this will give Linux's opponents ammunition about how using amateurs programmers and volunteers result in poor security, and how FOSS's community development model is not secure.
Because of one exploit that's been discovered? Microsoft has **hired** programmers to develop its products, yet many exploits are continously being discovered for them, even though the source is **closed**.

---

### Post by Bachstelze on 2009-08-14
> The bug involves the way kernel-level routines such as sock_sendpage react when they are left unimplemented. Instead of linking to a corresponding placeholder, (for example, sock_no_accept), the function pointer is left uninitialized. Sock_sendpage doesn't always validate the pointer before dereferencing it, leaving the OS open to local privilege escalation that can completely compromise the underlying machine. . . .

Someone should have paid more attention in C classes. That's really basic stuff: **never** leave a pointer uninitialized...

---

### Post by Bachstelze on 2009-08-14
> **samjh said:**
> Good thing they've found the error.  Bad thing is this will give Linux's opponents ammunition about how using amateurs programmers and volunteers result in poor security, and how FOSS's community development model is not secure.

"Amateur" and "volunteers" don't necessarily mean "incompetent". Some of the most highly regarded security experts are free software developers.

---

### Post by rookcifer on 2009-08-14
From [The Register]("http://www.theregister.co.uk/2009/08/14/critical_linux_bug/"):

> Linux developers have issued a critical update for the open-source OS after researchers uncovered a vulnerability in its kernel that puts most versions built in the **past eight years** at risk of complete takeover.

The bug involves the way kernel-level routines such as sock_sendpage react when they are left unimplemented. Instead of linking to a corresponding placeholder, (for example, sock_no_accept), the function pointer is left uninitialized. Sock_sendpage doesn't always validate the pointer before dereferencing it, leaving the OS open to local privilege escalation that can **completely compromise** the underlying machine.


More at the source linked above..

Be on the lookout in coming days for the patch to hit the repos.

---

### Post by kernelhaxor on 2009-08-14
> **Methuselah said:**
> Good.
Open source doesn't have the benefit of 'security through obscurity'.
Since the code is open for public scrutiny best practices must be followed and it makes for better software overall.

Ah good point.  A lot of FOSS people argue that there is no such thing as 'Security through obscurity' and FOSS is more secure because its open source, a lot more eyes read the code, somebody or the other would spot vulnerabilities and they would be fixed ..
I think its a never-ending debate ..
I think there is some sense in both arguments, neither is totally right IMO ..

---

### Post by t0p on 2009-08-14
> **HymnToLife said:**
> Someone should have paid more attention in C classes. That's really basic stuff: **never** leave a pointer uninitialized...

That should be *several someone*s.  The dev who wrote the code, and the various eyes who reviewed the code before it went into the kernel.

Still, never mind.  I don't think anyone malicious has taken advantage of it in the past 8 years to bother a box.   There's just a proof-of-concept attack, written by the vuln's discoverer Tavis Ormandy, and I don't think anything nasty will result from that as [Linus has already written a patch]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=e694958388c50148389b0e9b9e9e8945cf0f1b98").  As long as every potentially vulnerable machine has that patch applied when it's released.  Which is nicely taken care of round here by Ubuntu's Update Manager.

---

### Post by Swagman on 2009-08-14
IS this why "update" has borked ?

[img]http://www.upload3r.com/serve/140809/1250248136.jpeg[/img]

---

### Post by Bachstelze on 2009-08-14
> **kernelhaxor said:**
> Ah good point.  A lot of FOSS people argue that there is no such thing as 'Security through obscurity' and FOSS is more secure because its open source, a lot more eyes read the code, somebody or the other would spot vulnerabilities and they would be fixed ..
I think its a never-ending debate ..
I think there is some sense in both arguments, neither is totally right IMO ..

It basically depends on who gets to read the code. The NSA, for example, have some of the world's best cryptographers behind their walls, so they can afford to keep their algorithms secret. The average company releasing closed source products, however, doesn't, so it would be foolish to buy their products and expect them to have a high level of security.

Then again, open source isn't a guarantee of security either, as this thread demonstrates. Once again, it depends who gets to read the code. I don't mean to offend anyone, but I don't think thousands of Joe Averages make that much of a difference.

---

### Post by Arup on 2009-08-14
Compared to Win and Mac, its really nothing.

Dereferencing uninitialized pointer is worse than a null pointer because one can get valid address easily. Its poor programming and there is no excuse for it.

---

### Post by ice60 on 2009-08-14
> **samjh said:**
> Good thing they've found the error.  Bad thing is this will give Linux's opponents ammunition about how using amateurs programmers and volunteers result in poor security, and how FOSS's community development model is not secure.i know this is going a bit OT, but it made me think of these videos - it's far cooler being an amateur when what you do beats all the best professionals -
[http://www.youtube.com/watch?v=ml6KT5MArC8](http://www.youtube.com/watch?v=ml6KT5MArC8)
[http://video.google.com/videoplay?docid=4180590980863004593](http://video.google.com/videoplay?docid=4180590980863004593)

---

### Post by samjh on 2009-08-14
> **Eisenwinter said:**
> Because of one exploit that's been discovered? Microsoft has **hired** programmers to develop its products, yet many exploits are continously being discovered for them, even though the source is **closed**.

> **HymnToLife said:**
> "Amateur" and "volunteers" don't necessarily mean "incompetent". Some of the most highly regarded security experts are free software developers.

My point is the perception of FOSS by Linux's opponents, and the risk-averse corporate IT and general IT consumers at large.

For many years, FOSS proponents have pushed the argument of having better security because of "more eyes" reading the code.  If this error took **eight** years to discover, this argument certainly seems flawed, particularly considering that this isn't the first serious hidden security vulnerability in FOSS projects (remember the OpenSSH key generation vulnerability not so long ago?).

---

### Post by Bachstelze on 2009-08-14
> **samjh said:**
> For many years, FOSS proponents have pushed the argument of having better security because of "more eyes" reading the code.

My point exactly. It depends how good the people reading the code are, not how many people do. ;) When I said that some of the most highly regarded security experts are free software developers, I should have added that of course, they don't work on Linux.

> (remember the OpenSSH key generation vulnerability not so long ago?).

Yes, I laughed quite hard. :p There was also another exploit that allowed any user to gain root access 1/2 years ago. And of course the udev one...

---

### Post by Steve H on 2009-08-14
Yeah, I just read that on El Reg.

A bit embarrassing as it's the second one that has been found in as many months !

Will Ubuntu be rolling out the patch as part of the Update Manager?

---

### Post by mihai.ile on 2009-08-14
The best of all security bugs in my opinion was the one made by ubuntu in which you could get the password in plain text from the install logs. This is the real spirit of open source where even the root password was available... open source in plain text :D

But of course what's most important is that it got fixed.

Oh and by the way... paying a programmer to write code will not make it a better programmer and less susceptible in writing bugs. So the number of critical bugs found in open source in my opinion is less or equal to the ones found in closed source.
If a company needs to use a piece of code from open source, could easily hire some specialists to inspect the code and certify it, but I have doubts about the closed source where you have to trust the selling company, which is not nice at all...

This is in my opinion the real difference between the two in terms of security.

---

### Post by Bachstelze on 2009-08-14
There's already a thread on this topic, and besides, this is a support forum.

Threads merged.

---

### Post by Uluru on 2009-08-14
So what's being done about this, I dont mean to be arrogant at all, but I read about the Exploit @ the groovy "MVP hangout", calendar of Updates[http://www.calendarofupdates.com/updates/index.php?showtopic=22012]("http://www.calendarofupdates.com/updates/index.php?showtopic=22012")
Obviously the point must be made that this vulnerability has existed for eight years and has only just been let out of the bag.
Most importantly I can't fix this, anyone working on it :lolflag:

---

### Post by Bachstelze on 2009-08-14
> **Uluru said:**
> So what's being done about this, I dont mean to be arrogant at all, but I read about the Exploit @ the groovy "MVP hangout", calendar of Updates[http://www.calendarofupdates.com/updates/index.php?showtopic=22012]("http://www.calendarofupdates.com/updates/index.php?showtopic=22012")
Obviously the point must be made that this vulnerability has existed for eight years and has only just been let out of the bag.
Most importantly I can't fix this, anyone working on it :lolflag:

You can expect a fix to appear in the Ubuntu repos in the coming hours. Unlike other distros, Ubuntu has alway been quick to fix that sort of thigs, you gotta at least admit that.

---

### Post by Arup on 2009-08-14
> **HymnToLife said:**
> You can expect a fix to appear in the Ubuntu repos in the coming hours. Unlike other distros, Ubuntu has alway been quick to fix that sort of thigs, you gotta at least admit that.

One of the most important aspects that makes me stick to Ubuntu for good.

---

### Post by Uluru on 2009-08-14
> You can expect a fix to appear in the Ubuntu repos in the coming hours. Unlike other distros, Ubuntu has alway been quick to fix that sort of thigs, you gotta at least admit that.
Now everyone knows about this I'm sure it'll be patched very quickly, and as you say available in the Repos. I just hate to see the hopelessly incompetent MS MVP's giggling at a Linux exploit :(
Surprised they have time to pull themselves away from their Malware cleaning to even notice what's going on in the "Real World".
No offence intended, even if it has to be implied :lolflag:

---

### Post by Bad Penguin on 2009-08-14
Anyone have any idea when an updated kernel might become available?  I have searched far and wide and cannot even find a bug report on it, searching for CVE-2009-2692.

And FYI, the bug is not because some developer's bad coding.  From my limited understanding of the kernel coding voodoo, the null pointers were accounted for.  It is gcc compiler optimization that removed the checks after compiling the kernel.  Source code looked fine, the bug only shows up in the finished product.  The kernel code monkies are damn good, but I don't think they have jedi abilities like diff'ing source and binary code ;)

---

### Post by Steve H on 2009-08-14
Well, at least it looks good if Ubuntu get it patched nice and quickly!!

:)

---

### Post by Bad Penguin on 2009-08-14
> **Steve H said:**
> Well, at least it looks good if Ubuntu get it patched nice and quickly!!

:)

It is not patched, at least in dapper server LTS.  I just confirmed by running the exploit posted here:

[http://seclists.org/fulldisclosure/2009/Aug/0180.html](http://seclists.org/fulldisclosure/2009/Aug/0180.html)

---

### Post by Steve H on 2009-08-14
> **Bad Penguin said:**
> It is not patched, at least in dapper server LTS.  I just confirmed by running the exploit posted here:

[http://seclists.org/fulldisclosure/2009/Aug/0180.html](http://seclists.org/fulldisclosure/2009/Aug/0180.html)

I did say "IF" !!

:)

---

### Post by days_of_ruin on 2009-08-14
> **samjh said:**
> Good thing they've found the error.  Bad thing is this will give Linux's opponents ammunition about how using amateurs programmers and volunteers result in poor security, and how FOSS's community development model is not secure.

Yes because getting commit access to the linux kernel source code is only slightly harder than editing wikipedia.

---

### Post by Bad Penguin on 2009-08-14
> **Steve H said:**
> I did say "IF" !!

:)

I just filed a bug report since I couldn't find an existing one.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/413656](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/413656)

I posted a rather lame mitigation workaround in the bug...

---

### Post by moljac024 on 2009-08-14
Doesn't anyone find it interesting that it WASN'T discovered for 8 years ?
No harm done there then...but still, leaving a pointer uninitiliazed is crazy

---

### Post by MaxIBoy on 2009-08-14
I think I can be justified to bump this, as it really is important.

---

### Post by decoherence on 2009-08-14
> **moljac024 said:**
> Doesn't anyone find it interesting that it WASN'T discovered for 8 years ?


Yes! I'm telling Theo de Raadt and he's going to personally beat them all with the AUDIT STICK.

Uh... once he stops laughing that is... :biggrin:

---

### Post by Xbehave on 2009-08-14
the vulnerability only appears if your kernel was compiled with GCC 4.x so old (compiled/installed before GCC4.x was in use) kernels are fine. And as best i can tell it only disabled selinux/apparmour, an attacker still needs to exploit a running service and they gain access to an unrestricted service as whatever the service was running (often root as people have become too reliant on selinux/apparmour)

---

### Post by Xbehave on 2009-08-14
> **moljac024 said:**
> Doesn't anyone find it interesting that it WASN'T discovered for 8 years ?
No harm done there then...but still, leaving a pointer uninitiliazed is crazy
It hasn't been around for 8 years
GCC4.0 wasn't released until April 20, 2005, so at most its been around for 4 years.

Its also not crazy when doing pointer logic at the kernel level, there is a gcc compile flag to disable the optimisation for specifically that reason. What's crazy is gcc removing code without notifying the user!

---

### Post by FuturePilot on 2009-08-14
It doesn't even work on 8.04 or later according to the bug report
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/413656]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/413656")

```
$ ls
exploit  exploit.c  run  run.c  run.sh
$ ./run
padlina z lublina!
mprotect: Cannot allocate memory

```

---

### Post by grahamsaa on 2009-08-14
This brought my attention to another issue -- I can't seem to get the "patch" command to work (using Ubuntu 8.04 LTS).  I've copied the patch file into /usr/src/linux-headers-2.6.24-16-server/ and when I run the following command:

patch -p1 < patch-2.6.31-rc6

nothing happens.  I've tried doing this with the -verbose flag as well, and then I just get program output information.  I don't get any output about assembling hunks, etc.

Anyone know what's wrong?

I know that this issue shouldn't be a problem for 8.04 users, but being able to patch a kernel seems fairly important to me.  Is the command broken in ubuntu?  Am I doing something wrong?

Thanks,
Graham

---

### Post by juancarlospaco on 2009-08-14
I like that Linux you know what a security hole does, and how much,
different from Microsoft that never fixed Microsoft RDP protocol,
i sucessfully make a Man-in-the-middle RDP attack,
hijacking an account trought *"secure"* RDP.

Since that day i never use MS RDP again, 
but i still ear people that say is secure.

I deny all connections on all ports, 
only SSH port allowed*(not 22)*, and tunneling from there.

**Well nice patching job Linux Hackers!!!** :)

---

### Post by hyperdude111 on 2009-08-14
[http://news.softpedia.com/news/Newly-Discovered-Linux-Kernel-Vulnerability-Affects-All-Versions-Since-2001-119281.shtml](http://news.softpedia.com/news/Newly-Discovered-Linux-Kernel-Vulnerability-Affects-All-Versions-Since-2001-119281.shtml)

---

### Post by kernelhaxor on 2009-08-14
> **moljac024 said:**
> Doesn't anyone find it interesting that it WASN'T discovered for 8 years ?
No harm done there then...but still, leaving a pointer uninitiliazed is crazy

Doesn't mean it wasn't discovered .. it just wasn't reported ..
may be few did discover it and took advantage and didn't want to report to have the advantage

---

### Post by Xbehave on 2009-08-14
> **kernelhaxor said:**
> Doesn't mean it wasn't discovered .. it just wasn't reported ..
may be few did discover it and took advantage and didn't want to report to have the advantage

It's possible but i suspect admins would start noticing when their selinux profiles fail completely (ofc because selinux is pretty complex its possible that they didn't) but still unlikely! This is why you should never rely on anything being fullproof, even with selinux running you still need to limit privileges using su/setuid/etc, check for rootkits, use append only flags when possible, maintain a firewall on any server you maintain!

---

### Post by MikeTheC on 2009-08-14
> **Foster Grant said:**
> [http://www.theregister.co.uk/2009/08/14/critical_linux_bug/](http://www.theregister.co.uk/2009/08/14/critical_linux_bug/)


Gotta figure new kernel updates coming into the repos, maybe as soon as tonight ...

So does this mean we can stop bitching about Apple's lack of perfectly and instantly addressing every single niggly goof or hole? ;)

---

### Post by juancarlospaco on 2009-08-14
> **MikeTheC said:**
> So does this mean we can stop bitching about Apple's lack of perfectly and instantly addressing every single niggly goof or hole? ;)

No, because you dont have something like SELinux on Apple OS.
:)

---

### Post by BarfBag on 2009-08-14
I'm not knowledgeable enough to understand exactly what this exploit is.  What does this mean to the average Joe Linux user?  What would a user have to do in order for this exploit to be taken advantage of?

---

### Post by mmix on 2009-08-15
[http://forums.fedoraforum.org/showthread.php?t=228225](http://forums.fedoraforum.org/showthread.php?t=228225)

[quote="Gödel"]  
This one pwns just about every current kernel, test on your system

[http://grsecurity.net/~spender/wunderbar_emporium.tgz](http://grsecurity.net/~spender/wunderbar_emporium.tgz)

Code:

$ tar xvf ~/Download/wunderbar_emporium.tgz
$ cd wunderbar_emporium/
$ chmod u+x wunderbar_emporium.sh
$ ./wunderbar_emporium.sh

 [+] MAPPED ZERO PAGE!
 [+] Resolved selinux_enforcing to 0xc0a0ce58
 [+] Resolved selinux_enabled to 0xc089b444
 [+] Resolved security_ops to 0xc0a0b62c
 [+] Resolved default_security_ops to 0xc089af64
 [+] Resolved sel_read_enforce to 0xc053f03a
 [+] Resolved audit_enabled to 0xc09d534c
 [+] Resolved commit_creds to 0xc044b55d
 [+] Resolved prepare_kernel_cred to 0xc044b3be
 [+] got ring0!
 [+] detected 2.6 style 4k stacks
...

 [+] Disabled security of : SELinux
 [+] Got root!

sh-4.0#


if you have mplayer you'll see an ascii video.

This works even on current fedora systems with a "fixed" selinux policy! (a bug fix for mmap_min_addr in unconfined domains was recently provided, but this exploit bypasses it)

[http://lwn.net/Articles/347006/](http://lwn.net/Articles/347006/)[/quote]

---

### Post by Ranax on 2009-08-15
You can use this vulnerability to setup a booby trapped apt: that forkbombs anyone who clicks it.

---

### Post by change_mode on 2009-08-16
So, will it take another 8 years until we get an update?

---

### Post by tom66 on 2009-08-16
The fix is surprisingly simple:

```

--- a/net/socket.c
+++ b/net/socket.c
@@ -736,7 +736,7 @@ static ssize_t sock_sendpage(struct file *file, struct page *page,
        if (more)
                flags |= MSG_MORE;
 [COLOR="Red"]
-       return sock->ops->sendpage(sock, page, offset, size, flags);[/COLOR][COLOR="SeaGreen"]
+       return kernel_sendpage(sock, page, offset, size, flags);[/COLOR]
 }
 
 static ssize_t sock_splice_read(struct file *file, loff_t *ppos,

```

---

### Post by change_mode on 2009-08-16
> **tom66 said:**
> The fix is surprisingly simple

That's why it shouldn't take so long. Feels like Microsoft was in charge...

---

### Post by Bachstelze on 2009-08-16
> **change_mode said:**
> That's why it shouldn't take so long. Feels like Microsoft was in charge...

You obviously don't know what you're talking about.

---

### Post by change_mode on 2009-08-16
> **HymnToLife said:**
> You obviously don't know what you're talking about.

Are you saying Ubuntu is not affected by this bug?

---

### Post by FuturePilot on 2009-08-16
> **change_mode said:**
> Are you saying Ubuntu is not affected by this bug?

It's not. Look at the bug report that was posted a few pages back. None of these exploits even work in 8.04 or later.

---

### Post by change_mode on 2009-08-16
If that's the case, instead of bitching at me for not reading pages of kernel talk, **HymnToLife**, you could do something useful like editing the first post to let people know that Ubuntu is not affected.

---

### Post by Frak on 2009-08-16
> **HymnToLife said:**
> Someone should have paid more attention in C classes. That's really basic stuff: **never** leave a pointer uninitialized...
But it's like Russian Roulette!

---

### Post by Bachstelze on 2009-08-16
> **Frak said:**
> But it's like Russian Roulette!

Yeah, with a barrel loaded with 6 bullets.

---

### Post by Steve H on 2009-08-16
Forgive my ignorance, but can someone clear up whether this affects Ubuntu Jaunty and if so what are we supposed to do about it. Not all of us are versed in C and so I'm finding hard to decipher what is going on here.

Anyone willing to give a layman's answer? please?!

:)

---

### Post by zekica on 2009-08-16
Let me try to explain this in a simple way:

Dereferencing an uninitialized pointer enables an attacker to execute arbitrary code (in this case in unprotected kernel mode). It allows someone who has user access on the system to gain root access, and writing such an exploit when you know the vulnerability is easy for anyone who understands how some pretty basic stuff works.

However, in Ubuntu 8.04 and newer versions, default value of something called **mmap_min_addr** prevents this form happening, and if you are not running SELinux which is not turned on by default, the exploit fails to allocate the part of memory it needs to work, and fails.

There might be another workaround for this issue, but I haven't managed to successfully run the exploit on any of my machines running 9.04 with 2.6.28 and 2.6.30 kernel versions.

---

### Post by zekica on 2009-08-16
update: It looks like the second version of the exploit works :(

---

### Post by Harper45 on 2009-08-16
If you are unable to compile a kernel, be a bit more cautious for the next few days. As far as I know this can only be exploited through compiled programs, so you don't have to worry about malicious javascript in web-pages or anything like that. Also the repositories are still safe, I think you'll be fine if you don't install anything outside the repos. This patch will probably get applied to old kernels soon and you'll be seeing it as an update. 		                   		  		  		 		 			 				________

---

### Post by Steve H on 2009-08-16
So how long do we reckon for an update through the repos?

:confused:

---

### Post by Bachstelze on 2009-08-16
```
firas@iori wunderbar_emporium % ./wunderbar_emporium.sh
 [+] Personality set to: PER_SVR4
Pulseaudio does not exist!

```

[http://packages.debian.org/changelogs/pool/main/l/linux-2.6/linux-2.6_2.6.30-6/changelog](http://packages.debian.org/changelogs/pool/main/l/linux-2.6/linux-2.6_2.6.30-6/changelog)

It was fixed in Debian. That's funny, Debian is usually behind Ubuntu on security fixes.

---

### Post by Bachstelze on 2009-08-16
> **Steve H said:**
> So how long do we reckon for an update through the repos?

:confused:

Why does it bother you so much? Are you running a server, or a machine with untrusted users (school, library, etc.)?

---

### Post by Steve H on 2009-08-16
I dunno, I guess I just scare easy!

---

### Post by Bachstelze on 2009-08-16
This exploit seems dumb. Apparently, you're immune to it if you don't run PulseAudio:

```
firas@aoba:~/wunderbar_emporium$ uname -a
Linux aoba 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux
firas@aoba:~/wunderbar_emporium$ ./wunderbar_emporium.sh
 [+] Personality set to: PER_SVR4
Pulseaudio does not exist!

```

---

### Post by FuturePilot on 2009-08-16
> **HymnToLife said:**
> This exploit seems dumb. Apparently, you're immune to it if you don't run PulseAudio:

```
firas@aoba:~/wunderbar_emporium$ uname -a
Linux aoba 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux
firas@aoba:~/wunderbar_emporium$ ./wunderbar_emporium.sh
 [+] Personality set to: PER_SVR4
Pulseaudio does not exist!

```

It doesn't even work if you have PulseAudio installed either. It's relying on another vulnerability in PulseAudio that was already patched a while ago.

```
$ ./wunderbar_emporium.sh
 [+] Personality set to: PER_SVR4
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
UNABLE TO MAP ZERO PAGE!

```

---

### Post by Frak on 2009-08-16
> **HymnToLife said:**
> Yeah, with a barrel loaded with 6 bullets.
Nobody said it was fair.

---

### Post by ibuclaw on 2009-08-17
> **FuturePilot said:**
> It doesn't even work if you have PulseAudio installed either. It's relying on another vulnerability in PulseAudio that was already patched a while ago.

```
$ ./wunderbar_emporium.sh
 [+] Personality set to: PER_SVR4
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
UNABLE TO MAP ZERO PAGE!

```

This does appear to be a "big media" bug than a critical linux bug.

Either way, I was able to gain root access via the exploit, so I patched as appropriate.
```

jstdio@jstdio:~/wunderbar_emporium$ uname -a
Linux jstdio 2.6.29.4-rt15-tazo #2 SMP PREEMPT RT Sun Aug 16 21:09:33 BST 2009 i686 GNU/Linux

jstdio@jstdio:~/wunderbar_emporium$ ./wunderbar_emporium.sh 
 [+] Personality set to: PER_SVR4
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
 [+] MAPPED ZERO PAGE!
 [+] Resolved selinux_enforcing to 0xc0a107fc
 [+] Resolved selinux_enabled to 0xc0a107f8
 [+] Resolved security_ops to 0xc0a0bfc0
 [+] Resolved default_security_ops to 0xc07dc3c0
 [+] Resolved sel_read_enforce to 0xc03ae090
 [+] Resolved audit_enabled to 0xc093e304
 [+] Resolved commit_creds to 0xc0257cb0
 [+] Resolved prepare_kernel_cred to 0xc0257ec0
unable to find a vulnerable domain, sorry
^C

jstdio@jstdio:~/wunderbar_emporium$ # exploit owned :)

```

Yes, this current exploit seems to attack pulseaudio than anything else (my audio stopped working momentarily after running this).

I'm sure there are other ways into it via setuid binaries, but the patch can be applied in 3 seconds flat manually, and compilation done in 30 minutes. No sweat. :)

But, more and to the point, if you are running a server, why on earth would you have:
1) PulseAudio running on it.
2) A compiler installed.

Onion layers, people. You have to think in Onion layers. ;)

Regards
Iain

---

### Post by FuturePilot on 2009-08-17
> **tinivole said:**
> 
But, more and to the point, if you are running a server, why on earth would you have:
1) PulseAudio running on it.
2) A compiler installed.


I can understand not having PulseAudio installed on a server, but whether or not you have a compiler installed makes no difference in my opinion. There's nothing stopping an attacker from compiling the exploit beforehand.

---

### Post by heyyy on 2009-08-17
being a newbe i ask:
does this security hole implies to the regular home user who doesnt have a server running?

---

### Post by Bachstelze on 2009-08-17
> **tinivole said:**
> 
But, more and to the point, if you are running a server, why on earth would you have:
2) A compiler installed.

Let me guess, to compile software? Not everything is available in the repos (not to mention that some people use a source-based distro, like Gentoo).

By the way, how are people supposed to compile a patched kernel without a compiler?

> **heyyy said:**
> being a newbe i ask:
does this security hole implies to the regular home user who doesnt have a server running?

It depends. Do you trust that the people using your computer won't run the exploit on it?

---

### Post by heyyy on 2009-08-17
> **HymnToLife said:**
> Let me guess, to compile software? Not everything is available in the repos (not to mention that some people use a source-based distro, like Gentoo).

By the way, how are people supposed to compile a patched kernel without a compiler?



It depends. Do you trust that the people using your computer won't run the exploit on it?

so this implies only if it is an "inside" activity?(for me)

---

### Post by Bachstelze on 2009-08-17
> **heyyy said:**
> so this implies only if it is an "inside" activity?(for me)

Yes. This is a local security hole, meaning that in order to gain root access, an attacker *must* have a user access on the system.

---

### Post by 3rdalbum on 2009-08-17
> **MikeTheC said:**
> So does this mean we can stop bitching about Apple's lack of perfectly and instantly addressing every single niggly goof or hole? ;)

No.

When it's possible to root a Linux box just by sending dbus commands from the terminal, and the developers responsible for the bug fix it 4 years after being notified by one of their own security experts, THEN we can stop bitching about Apple.

---

### Post by 3rdalbum on 2009-08-17
I tried the exploit code and it was quite disturbing.

Not so much that the code worked and that it got root, but that **I didn't give it execute permission!**

I extracted the archive in File Roller, switched to the new directory and ran ./wunderbar_emporium.sh **and it ran**. That should never happen!

---

### Post by Bachstelze on 2009-08-17
> **3rdalbum said:**
> That should never happen!

Why?

---

### Post by rudihawk on 2009-08-17
> **HymnToLife said:**
> Why?

+1 

I don't understand either.

---

### Post by samjh on 2009-08-17
> **3rdalbum said:**
> I tried the exploit code and it was quite disturbing.

Not so much that the code worked and that it got root, but that **I didn't give it execute permission!**

I extracted the archive in File Roller, switched to the new directory and ran ./wunderbar_emporium.sh **and it ran**. That should never happen!

The file might already have had execute permission enabled.  Happens all the time when transferring files from a FAT or NTFS formatted file system.

---

### Post by Bad Penguin on 2009-08-17
Allow me to apologize for spreading some of my own apparent confusion ;)

There are two different vulnerabilities being discussed in this topic.  The original vulnerability being discussed was [CVE-2009-1895](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2009-1895), which has been fixed in ubuntu by [USN-807-1](http://www.ubuntu.com/usn/USN-807-1).  This is the vulnerability that uses pulseaudio to exploit it, i.e. the wunderbar_emporium code.

Anyone who has applied the latest ubuntu security updates is supposed to be ok on this vulnerability.

The second vulnerability, which I was discussing, is [CVE-2009-2692](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2009-2692).  There is no ubuntu update for it yet, nor an ubuntu security notice, currently it is being addressed in [bug 413656](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/413656).  This bug does not involve pulseaudio, it involves the exploit [posted here](http://seclists.org/fulldisclosure/2009/Aug/0180.html).

As far as this vulnerability, if you are running ubuntu 8.04 or above, you are ok as long as your /proc/sys/vm/mmap_min_addr is not 0 (zero).  Apparently installing the wine and/or dosemu packages can alter mmap_min_addr back to 0, so you should follow the work-around instructions in the bug.  If you are running dapper, you have to run through some hoops to disable the protocols that expose the attack vector, again this is covered in the bug...

---

### Post by 3rdalbum on 2009-08-17
> **Bad Penguin said:**
> 

As far as this vulnerability, if you are running ubuntu 8.04 or above, you are ok as long as your /proc/sys/vm/mmap_min_addr is not 0 (zero).  Apparently installing the wine and/or dosemu packages can alter mmap_min_addr back to 0, so you should follow the work-around instructions in the bug.

Hahaha, rocking, thanks for the information. Issuing this command:

```
sudo su
echo 65536 > /proc/sys/vm/mmap_min_addr

```

stops the exploit code from working! And it doesn't stop Wine from working either, so that's good.

(the number "1" works as well, but 65536 is apparently what Ubuntu comes set as)

---

### Post by sydbat on 2009-08-17
If I am looking in the right place (filesystem > proc > sys > vm), my mmap_min_addr file is empty. As in there is nothing in it. Properties show 0 bytes.

I take it that this is bad??

---

### Post by Bachstelze on 2009-08-17
> **sydbat said:**
> If I am looking in the right place (filesystem > proc > sys > vm), my mmap_min_addr file is empty. As in there is nothing in it. Properties show 0 bytes.

I take it that this is bad??

Use the terminal, Luke!

```
cat /proc/sys/vm/mmap_min_addr
```

---

### Post by sydbat on 2009-08-17
> **HymnToLife said:**
> Use the terminal, Luke!

```
cat /proc/sys/vm/mmap_min_addr
```Thank you Obi Wan!

It is 65536. YAY!!!

---

### Post by rarsa on 2009-08-17
> **HymnToLife said:**
> Let me guess, to compile software? Not everything is available in the repos...
By the way, how are people supposed to compile a patched kernel without a compiler?Who said no compiler? I read "No compiler in the production server". You compile in your test box, you deploy only compiled and tested code.

Makes sense now?

---

### Post by Frak on 2009-08-17
> **rarsa said:**
> Who said no compiler? I read "No compiler in the production server". You compile in your test box, you deploy only compiled and tested code.

Makes sense now?
We run compiler front-ends on our production servers. Take that sir.

---

### Post by Bachstelze on 2009-08-17
> **tinivole said:**
> This does appear to be a "big media" bug than a critical linux bug.

Either way, I was able to gain root access via the exploit, so I patched as appropriate.
```

jstdio@jstdio:~/wunderbar_emporium$ uname -a
Linux jstdio 2.6.29.4-rt15-tazo #2 SMP PREEMPT RT Sun Aug 16 21:09:33 BST 2009 i686 GNU/Linux

jstdio@jstdio:~/wunderbar_emporium$ ./wunderbar_emporium.sh 
 [+] Personality set to: PER_SVR4
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
 [+] MAPPED ZERO PAGE!
 [+] Resolved selinux_enforcing to 0xc0a107fc
 [+] Resolved selinux_enabled to 0xc0a107f8
 [+] Resolved security_ops to 0xc0a0bfc0
 [+] Resolved default_security_ops to 0xc07dc3c0
 [+] Resolved sel_read_enforce to 0xc03ae090
 [+] Resolved audit_enabled to 0xc093e304
 [+] Resolved commit_creds to 0xc0257cb0
 [+] Resolved prepare_kernel_cred to 0xc0257ec0
unable to find a vulnerable domain, sorry
^C

jstdio@jstdio:~/wunderbar_emporium$ # exploit owned :)

```

Yes, this current exploit seems to attack pulseaudio than anything else (my audio stopped working momentarily after running this).

I'm sure there are other ways into it via setuid binaries, but the patch can be applied in 3 seconds flat manually, and compilation done in 30 minutes. No sweat. :)

But, more and to the point, if you are running a server, why on earth would you have:
1) PulseAudio running on it.
2) A compiler installed.

Onion layers, people. You have to think in Onion layers. ;)

Regards
Iain

> **rarsa said:**
>  I read "No compiler in the production server".

You're seeing things. The word "production" does not appear anywhere.

---

### Post by ivze on 2009-08-17
(First of all, i am a desktop user and the whole situation interests me just because of curiosity). IMHO, the best exploit, i have seen, is "proto_ops". The URL follows.
[http://www.frasunek.com/proto_ops.tgz](http://www.frasunek.com/proto_ops.tgz)
This exploit don't need pulseaudio.

---

### Post by geekygirl on 2009-08-17
I would imagine that an 8 year old kernel would have more than just security issues if you were to use it today....

---

### Post by szirakitamas on 2009-08-18
> **ivze said:**
> This exploit don't need pulseaudio.

Yes, 'cos the pulseaudio is only for the multimedia presentasion. :)

---

### Post by SunnyRabbiera on 2009-08-18
Well no OS is fully idiot proof, or bugproof.

---

### Post by rudihawk on 2009-08-18
> **SunnyRabbiera said:**
> Well no OS is fully idiot proof, or bugproof.

+1:guitar:

---

### Post by 3rdalbum on 2009-08-18
It looks like a bit of a media beatup on this story.

Firstly, a stock install of Ubuntu is not exploitable. The underlying kernel problem is there, but it's not possible to take advantage of it due to the mmap_min_addr security.

Secondly, in order to be vulnerable, you must have installed Wine or Dosbox, which changes the kernel settings.

Thirdly, although the underlying problem affects all Linux architectures, it's highly unlikely that you can perform the exploit on real non-x86 systems, because of course they don't have Wine, so their mmap_min_addr is still the secure 65536.

Fourthly, even if you have Wine installed, you still need a build environment and either a malicious user or a program that has already been taken over by an attacker.

---

### Post by Bachstelze on 2009-08-18
> **3rdalbum said:**
> Firstly, a stock install of Ubuntu is not exploitable.

Linux != Ubuntu

> **3rdalbum said:**
> you still need a build environment and either a malicious user or a program that has already been taken over by an attacker.

All you need is a malicious user. He can very well build the exploit at home and bring it on your system on his USB stick. And we all know most users can't really be trusted.

---

### Post by Bad Penguin on 2009-08-18
> **3rdalbum said:**
> Firstly, a stock install of Ubuntu is not exploitable. The underlying kernel problem is there, but it's not possible to take advantage of it due to the mmap_min_addr security.

Secondly, in order to be vulnerable, you must have installed Wine or Dosbox, which changes the kernel settings.

Thirdly, although the underlying problem affects all Linux architectures, it's highly unlikely that you can perform the exploit on real non-x86 systems, because of course they don't have Wine, so their mmap_min_addr is still the secure 65536.

Fourthly, even if you have Wine installed, you still need a build environment and either a malicious user or a program that has already been taken over by an attacker.

If you consider a "stock" install of ubuntu to be a fresh install from an ubuntu installation cd, with no security updates applied, then yes, you are vulnerable.  As a matter of fact you would be vulnerable to the much nastier vulnerability [USN-807-1](http://www.ubuntu.com/usn/USN-807-1), which allows the attacker to bypass mmap_min_addr, and all other security configurations (SELinux, etc..).

Only until you do a dist-upgrade and install the latest kernel from the security updates repositories are you safe from that first exploit.

Then at any time in the future if you install packages such as wine or dosemu (only two specifically mentioned) you might or might not still be exposed to the second vulnerability (proto_ops).  At least until an updated kernel package is ready...

And you don't need a build environment, all you need is a way to transfer the compiled binaries to the target host (wget, scp, ftp, lynx, firefox, bittorrent, etc).

---

### Post by ukripper on 2009-08-18
> **3rdalbum said:**
> Hahaha, rocking, thanks for the information. Issuing this command:

```
sudo su
echo 65536 > /proc/sys/vm/mmap_min_addr

```

stops the exploit code from working! And it doesn't stop Wine from working either, so that's good.

(the number "1" works as well, but 65536 is apparently what Ubuntu comes set as)

Changing 0 to 65536 means we don't require any other patch? One of my machine is running wine and i do need it for something rather important. I have just changed 65536 from 0 on that machine. I wonder how secure is that?

---

### Post by FuturePilot on 2009-08-18
> **ukripper said:**
> Changing 0 to 65536 means we don't require any other patch? One of my machine is running wine and i do need it for something rather important. I have just changed 65536 from 0 on that machine. I wonder how secure is that?

The underlying problem is still there and it does need patched, however because of what Ubuntu has that set to (65536) the exploits get blocked.

---

### Post by ukripper on 2009-08-18
> **FuturePilot said:**
> The underlying problem is still there and it does need patched, however because of what Ubuntu has that set to (65536) the exploits get blocked.

Thanks mate! Changing it to 65536 has any knock-on effect on something else?

---

### Post by FuturePilot on 2009-08-18
> **ukripper said:**
> Thanks mate! Changing it to 65536 has any knock-on effect on something else?

65536 is the default value so it shouldn't have a negative effect on anything; wine and dosbox being the exception since they change this value so I'm not sure how it would affect either of those programs.

---

### Post by Bad Penguin on 2009-08-18
> **ukripper said:**
> Changing 0 to 65536 means we don't require any other patch? One of my machine is running wine and i do need it for something rather important. I have just changed 65536 from 0 on that machine. I wonder how secure is that?

I would advise you to read the workaround noted in the [bug](https://bugs.launchpad.net/ubuntu/dapper/+source/linux-source-2.6.15/+bug/413656), as opposed to taking advice of unknown quality from various forum users, myself included ;)

Note the bug says "sudo apt-get purge wine dosemu", then makes no mention of re-installing wine/dosemu/qemu afterward...  I take that to mean that if you install packages like wine or dosemu that have to alter mmap_min_addr to function correctly, you are vulnerable to the exploit, until updated packages come out.

And I wouldn't go setting mmap_min_addr to 1 either, I assume it needs to be on a byte boundary.  Like I said, rely on what is stated as the work around in the bug report for now...

For more info on the wine issues:

[https://lists.ubuntu.com/archives/ubuntu-devel/2008-July/025805.html](https://lists.ubuntu.com/archives/ubuntu-devel/2008-July/025805.html)

[http://james-morris.livejournal.com/26303.html](http://james-morris.livejournal.com/26303.html)

[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

---

### Post by 3rdalbum on 2009-08-19
Yes, I stand corrected: You need to have not installed the updates AND installed Wine/Dosbox AND not changed your mmap. You don't need a build environment.

BadPenguin, I think the reason why they recommend purging Wine and Dosbox is because any automatic updates to those packages will reset the mmap value to zero. Wine appears to work after setting the mmap value back to 65536.

Still, I remember an 8-year-old root security hole on the Mac OS. It was exploitable just by issuing a single Applescript command (it could be done on the terminal) and Apple fixed it about four years after one of their own engineers warned them.

The Linux vulnerability is not so bad on Ubuntu, because it's still only really opened by software from Universe. I've heard that Fedora comes vulnerable, but then most Linux users aren't using Fedora.

---

### Post by ukripper on 2009-08-19
I guess i'll just be careful when wine updates hit repos. i 'll make sure to put the value back.

---

### Post by ukripper on 2009-08-19
just noticed my 65536 value doesn't stay after reboot. I have added following to my rc.local so changes get picked up on every reboot.


```
echo 65536 > /proc/sys/vm/mmap_min_addr
```

And also I've disabled any wine updates until this issue is patched upstream.

---

### Post by t0p on 2009-08-19
> **HymnToLife said:**
> 
All you need is a malicious user. He can very well build the exploit at home and bring it on your system on his USB stick. And we all know most users can't really be trusted.

Dude, if I were worried about a malicious user with physical access to my computer, the last thing on my mind would be exploits he might have on a usb drive.  Hell, he could install a hardware keylogger and steal my passwords.  He could do a [cold boot attack]("http://en.wikipedia.org/wiki/Cold_boot_attack") to grab my encryption keys.  He could whip out the hard drive and image the disk.  He could smash up the machine with a sledgehammer!

If a malicious user has physical access to your computer, then your computer is insecure.  No matter what kernel (or operating system) it runs.

---

### Post by Bachstelze on 2009-08-19
> **t0p said:**
> Dude, if I were worried about a malicious user with physical access to my computer, the last thing on my mind would be exploits he might have on a usb drive.  Hell, he could install a hardware keylogger and steal my passwords.  He could do a [cold boot attack]("http://en.wikipedia.org/wiki/Cold_boot_attack") to grab my encryption keys.  He could whip out the hard drive and image the disk.  He could smash up the machine with a sledgehammer!

If a malicious user has physical access to your computer, then your computer is insecure.  No matter what kernel (or operating system) it runs.

I'm fully aware of that, thank you very much. The problem is that smashing the machine with a sledgehammer makes a little more noise than transferring an executable file from an USB stick and running it.

---

### Post by Bad Penguin on 2009-08-19
> **3rdalbum said:**
> BadPenguin, I think the reason why they recommend purging Wine and Dosbox is because any automatic updates to those packages will reset the mmap value to zero. Wine appears to work after setting the mmap value back to 65536.

I believe the reason you have to --purge is because wine installs config files that will change the mmap_min_addr back to 0 after a reboot.  So just manually setting mmap_min_addr to 0 is not enough, you have to actually purge the package and any config files it installed.  Just doing an apt-get remove wouldn't have done the trick...

> **3rdalbum said:**
> The Linux vulnerability is not so bad on Ubuntu, because it's still only really opened by software from Universe. I've heard that Fedora comes vulnerable, but then most Linux users aren't using Fedora.

Wine and dosemu are just two packages that have been mentioned, there might be more that alter mmap_min_addr, like qemu.  Kind of irrelevant now though, the kernel updates have been released...

---

### Post by ukripper on 2009-08-19
> **Bad Penguin said:**
> I believe the reason you have to --purge is because wine installs config files that will change the mmap_min_addr back to 0 after a reboot.  So just manually setting mmap_min_addr to 0 is not enough, you have to actually purge the package and any config files it installed.  Just doing an apt-get remove wouldn't have done the trick...


Or as I suggested above including 65536 into your rc.local would put the value back after every reboot and you don't have to purge the wine configs.

---

### Post by cariboo on 2009-08-19
New patched kernels for almost every version were released [today]("http://www.ubuntu.com/usn/usn-819-1"), go get it now.

---

