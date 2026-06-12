---
title: "keylogger to interferret SUDO"
date: 2012-10-02
forum: Security
---

### Post by mike acker on 2012-10-02
thinking again ( oh no )

could a keylogger grab the administrator password when SUDO is used ...

this supposes the malware is carried in an HTML document -- active in an app e.g. Firefox, Chrome, Thunderbird, LibreOffice ...

to my thinking the answer is no: any app such as those mentioned here should be running in a separate storage key and hence will not be able to "see" the memory used when you open TERMINAL to run SUDO

we would hope SUDO deletes the administrator password from memory -- as soon as authentication has been requested... otherwise as memory is reallocated...

---

### Post by daslinkard on 2012-10-02
> **mike acker said:**
> thinking again ( oh no )

could a keylogger grab the administrator password when SUDO is used ...

this supposes the malware is carried in an HTML document -- active in an app e.g. Firefox, Chrome, Thunderbird, LibreOffice ...

to my thinking the answer is no: any app such as those mentioned here should be running in a separate storage key and hence will not be able to "see" the memory used when you open TERMINAL to run SUDO

we would hope SUDO deletes the administrator password from memory -- as soon as authentication has been requested... otherwise as memory is reallocated...

Interesting questions that you pose here....I did a little surfing around the Net and saw where one Ubuntu Poster felt that someone who obtained a keylogger on their Windows machine would be prone to eventually get a keylogger on their Linux machine.  I'm not for certain how much I agree with that statement being everything is seen as a file in Linux.

With that said there is *logkeys* in the Software Center which is available for download so you could put the keylogger on your Ubuntu machine.

---

### Post by MG&amp;TL on 2012-10-02
> **mike acker said:**
> thinking again ( oh no )

could a keylogger grab the administrator password when SUDO is used ...

this supposes the malware is carried in an HTML document -- active in an app e.g. Firefox, Chrome, Thunderbird, LibreOffice ...

to my thinking the answer is no: any app such as those mentioned here should be running in a separate storage key and hence will not be able to "see" the memory used when you open TERMINAL to run SUDO

we would hope SUDO deletes the administrator password from memory -- as soon as authentication has been requested... otherwise as memory is reallocated...

Yes, assuming one is used and it is working. 

Err...nope. Not unless it managed to install itself. To log keys, or indeed access memory from another process is very difficult.

I don't know exactly how *sudo* manages its memory (feel free to check out the source code and tell us!), but I would think it would scrub its sensitive segments of memory before releasing them.

---

### Post by 1clue on 2012-10-02
A well-written key logger will pull any key press on the system, or possibly even from a networked login depending on whether the remote session uses the keyboard event handler.

Google for 'javascript keylogger' and see what you get.  As to whether an html page could catch your password from sudo, it depends on whether you inadvertently type it into the browser.

If the logger is in the event chain for whatever app, yes it can read the keyboard.

You've had the first spark of fear, now it's time for you to do some research and find out for sure...

---

### Post by Hungry Man on 2012-10-02
Yes, easily. Any compromised process can read another processes keystrokes. If they share a UID they can use ptrace or other methods. 

SVG filters can be used for keylogging within a website.

---

### Post by mike acker on 2012-10-02
thanks for all the thoughtful replies!! 

we talk about an "event chain" in this thread. I take that as meaning: when a program is launched from the launcher  then the "event chain" that results will include all of the subroutines, libraries, and processes that are called pursuant to that initial launch ... these would all be operating under the same storage key. Except of course library code which is scheduled to run in "userland" -- so that a rogue program cannot modify the library code -- which will be regarded as "trusted".

when i launch a second event chain -- from the launcher -- e.g. terminal  -- then that event chain should be in another storage key (remember I'm an old MVS guy ) -- and nothing in the first event chain will have any means of "seeing" anything that  the second chain has in memory ...

now if the one event  chain stores something in the user libraries... eg a key log file -- then -- any program running under the current USER ID -- would have access to the files from disk -- but not to steal from the other event chain's memory

~~
I do have a working knowlege of "C" but I'm not sure about trying to read the source code for SUDO,-- yet. I think what I'll do is just run SUDO by itself if I use it -- which isn't often anyway .

---

### Post by Hungry Man on 2012-10-02
If they're within the same UID they can both see and interact with any other processes address space running on the same UID. This is the Windows, Linux, and OSX Security model. You can ptrace any process of the same UID as well as well as a few other things to read system calls and keylog.

Beyond that they can simple use X to keylog across UIDs, which makes the whole thing much simpler. There's no real protection against this without SELinux.

As for libraries they're just code and a rogue program probably could modify them given proper access rights but by default it would only have read and mapping access - can't be sure about that one though. There are ldso userland rootkits.

---

### Post by 1clue on 2012-10-02
"Event Chain" is my own slang and does not really refer to anything official.

Linux, Windows, Mac OS, Java, pretty much any non-real-time OS all work on an event model.

You have a kernel that sits there and either waits for interrupts or actively queries hardware regularly.  What we refer to as PC hardware, it's an interrupt.  When the interrupt happens, that's an Event.  Events have priorities.  Something like a memory page fault is fairly high priority and a keyboard event is less important.

In any case, you have a driver or similar software which handles the hardware event, basically this is the kernel activity.  Usually this thing puts an Event structure on the event queue, to be handled by a user process.  The event may have one or more listeners.  Some listeners will "consume" the event, meaning they do something but do not pass the event down the chain of listeners.  Some listeners only do some small thing or ignore it altogether, looking for something specific.

An example of a listener that does something but doesn't consume the event, think of the XEyes app which has a pair of eyes somewhere on the screen, always looking at the cursor.  It doesn't affect anything but always moves to watch the cursor.

A key logger is another event listener that doesn't consume the event.  Instead it will write the key presses and maybe the active application name to a file, and then later will zip the file and send it somewhere.

As Hungry Man implied, there are different relationships between processes.  They could be completely separate, meaning user A and user B, and in this case the only way one could read the other is if one of them is root.  They could be owned both by user A, which means they are more visible to each other.   A could be the parent of B, in which case A can see anything it wants from B, and can kill B.

Another point, if you are silly enough to run as root user, then it doesn't matter one bit if you have selinux or not.  If you run malicious code as root, you've blessed it and it can do anything it wants to try.  Linux has all sorts of protection for people who are careful and follow some common sense rules, but no protection at all for a system admin who gets stupid.

---

### Post by rookcifer on 2012-10-03
> **1clue said:**
> Another point, if you are silly enough to run as root user, then it doesn't matter one bit if you have selinux or not.

Not really true.  Both SELinux and AppArmor can confine root (a MAC system doesn't care about DAC or user/root -- it confines based on a *mandatory* system-wide policy)..  Crispin Cowan, the creator of AppArmor, [gave a talk]("https://www.youtube.com/watch?v=EgrfmSm0NWs") a number of years ago where he showed AppArmor confining root.  He had a **root **shell open and tried to run:

```
rm -rf /
```

It blocked it (fast forward to 24:00 in the video).

But, of course, I do agree it is not smart to run as root.  Better is to let DAC work with MAC.

And, of course, MAC systems are useless if the attacker has a code path the a vulnerable kernel process.  Depending on the circumstances, it might be possible for him to bypass any MAC system in use.

---

### Post by mike acker on 2012-10-03
> **1clue said:**
> "Event Chain" is my own slang and does not really refer to anything official.{/snip}

 **The event may have one or more listeners**. {/snip} 

thanks for the note:!:
it's going to take me a bit to digest it.  I'm familiar with the I/O and SVC structure -- interrupts/waits -- in System/370; somewhat in the DOS/PC -- which is quite different from the 370.

the "one or more listeners" is more like a PC than a 370-- essentially a hooked interrupt: whatever you key: let me look at it first; then I'll pass it on to you...

this of course requires that I ran a program to hook that vector... 

in this thread I was concerned about the possibility of using a key logger to steal the administrator password and thus get the ability to run SUDO

I don't see that happening -- unless -- a key logger gets  installed -- either intentionally by the system operator -- or by an attack

in Windows we have no way of knowing how many RPC call paths lead to privileged modules running in kernel mode that can be compromised by code injection.

but i don't see that happening in Linux,-- those privileged modules that are a problem in Windows should be running in "userland" as trusted programs in Linux -- which should help to reduce the paths available to an attacker.  Ideally the ONLY way to install a program is via the Official Installer -- which requires the Administrator password,-- and hopefully a digital signature authenticating the distribution-- whether o/s update, or app.

It looks to me that for most of us if we just follow Linux recommendations our systems are not likely to get hacked.

---

### Post by albandy on 2012-10-03
When you type sudo, you're invoking a setuided file. This means that sudo runs under root user and you don't have acces to root user page memory unles you're root.

Only a keylogger executed under root can read the keyboard when executing sudo.

---

### Post by mike acker on 2012-10-03
STORAGE KEY

I keep referring to this,-- it's 360/370 lingo: the supervisor ran in protect key 0 and protect keys 1 through 15 were for user partitions/regions running applications.  yep, just 16 keys were all we had ( but nobody had enough memory to run that many regions )

If I've done my homework properly the Intel x86 processors create a set of tables for memory protection -- essentially keeping track of what belongs to who -- and what privileges are allowed -- in a set of tables maintained by the kernel.

Virtual memory being and additional separate scheme...

Hopefully Linux has fully implemented the memory protection model -- which it is my understanding Windows does not 

reference: _The Rootkit Arsenal_ Bill Blunden ISBN 13:978-1-59822-061-2

see also [http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/](http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/)

( the above is a bit dated bu nonetheless insightful )

---

### Post by 1clue on 2012-10-03
> **mike acker said:**
> ...
I don't see that happening -- unless -- a key logger gets  installed -- either intentionally by the system operator -- or by an attack


That's just the deal.  If you get in the habit of just clicking "yes" and you are either root (something Ubuntu goes out of the way to disable) or you have SUDO access (the first user, for example, or anyone you give admin rights to) then you ARE vulnerable.

BTW I'm a programmer but not a UNIX programmer.  The event model I used is approximately correct, but I can't vouch for it.

> 
but i don't see that happening in Linux,-- those privileged modules that are a problem in Windows should be running in "userland" as trusted programs in Linux -- which should help to reduce the paths available to an attacker.  Ideally the ONLY way to install a program is via the Official Installer -- which requires the Administrator password,-- and hopefully a digital signature authenticating the distribution-- whether o/s update, or app.


Again, if you installed the system then it doesn't matter what your username is.  If you can type your password to install updates, then you can also (possibly inadvertently) install malware which can affect your entire system.

If you're NOT that user, you can install software in your own user space which you can compile and run, and it will have access to anything YOU have access to.  So you can thoroughly trash your own files.

> 
It looks to me that for most of us if we just follow Linux recommendations our systems are not likely to get hacked.

+10,000,000,000

The thing is, learn to look at advisories and read a few security howto's.

---

### Post by Hungry Man on 2012-10-03
> **albandy said:**
> When you type sudo, you're invoking a setuided file. This means that sudo runs under root user and you don't have acces to root user page memory unles you're root.

Only a keylogger executed under root can read the keyboard when executing sudo.
This is the case for any separate UID. X bypasses this.

---

