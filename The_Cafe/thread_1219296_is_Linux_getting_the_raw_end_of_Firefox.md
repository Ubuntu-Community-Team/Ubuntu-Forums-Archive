---
title: "is Linux getting the raw end of Firefox?"
date: 2009-07-21
forum: The Cafe
---

### Post by Ascenti0n on 2009-07-21
Is anyone else starting to getting the impression that Linux's version of Firefox, is not getting the same attention, love and care as it's Windows counterpart?

I'm seeing more stories/blogs that suggest this is the case, particularly in the area of performance.

---

### Post by Yes on 2009-07-21
I've heard that the MSVC (Windows) compiler is much faster than GCC (Linux) compiler.  I'm guessing a lot of the performance differences can be attributed to that.

---

### Post by avacomputers on 2009-07-21
Are you guys, using the latest version of FF? It seems to be working fine here.

---

### Post by blur xc on 2009-07-21
working fine and performance are two different things.

BM

---

### Post by Ascenti0n on 2009-07-21
I am using FF 3.5.

One report I read recently com[ared performance and said that windows version of FF under Wine, was faster than Linux's native version under Linux.

---

### Post by Yes on 2009-07-21
> **Ascenti0n said:**
> I am using FF 3.5.

One report I read recently com[ared performance and said that windows version of FF under Wine, was faster than Linux's native version under Linux.

That seems to support what I said, that the version compiled using Microsoft's compiler is faster because it's a "better" compiler than what's used in Linux.

---

### Post by Kosimo on 2009-07-21
I kind of felt that as well... Now I'm using Firefox under Mac Os X and performance looks the same than in Windows.

---

### Post by swoll1980 on 2009-07-21
> **Ascenti0n said:**
> Is anyone else starting to getting the impression that Linux's version of Firefox, is not getting the same attention, love and care as it's Windows counterpart?

I'm seeing more stories/blogs that suggest this is the case, particularly in the area of performance.

I love when people say "I read an article that said it was slower".
If you couldn't tell a speed difference, without an article telling you so, then it's probably not as big of a deal as your making it out to be.

---

### Post by Jimleko211 on 2009-07-21
If it really is slower, which I haven't really noticed, can you blame the developers?  There is a mass difference in market share between Linux and Windows, and that includes in Firefox usage.

---

### Post by Ozor Mox on 2009-07-21
I used to think this was the case back with Firefox 2, but I think that was mostly because the Flash plugin used to crash Firefox quite a lot. These days I have no problems with Firefox on Windows or on Ubuntu.

---

### Post by bodhi.zazen on 2009-07-21
> **Ascenti0n said:**
> Is anyone else starting to getting the impression that Linux's version of Firefox, is not getting the same attention, love and care as it's Windows counterpart?

I'm seeing more stories/blogs that suggest this is the case, particularly in the area of performance.

Ever consider performing speed tests ?

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by .Maleficus. on 2009-07-21
> **Jimleko211 said:**
> If it really is slower, which I haven't really noticed, can you blame the developers?  There is a mass difference in market share between Linux and Windows, and that includes in Firefox usage.
The code is cross-platform C++, they don't write a Windows version, then Linux version and then an OS X version.  It's compiled from the same source.

Firefox on Linux is "slower" than on Windows, there's no doubt about it.  Whether or not you can tell the difference is for you to decide, but I personally can't.  Like Yes said, I imagine it's that MSVC is creating more optimized binaries.  If you really care that much, compile Firefox for your architecture using platform-specific flags.  Even better, if you use an Intel processor use ICC.

Or use it in Wine.

---

### Post by itreius on 2009-07-21
Right now, there's a small difference in performance that I've noticed when doing tests between Firefox 3.5/Ubuntu 32-bit and Firefox 3.5/Windows. I agree with Maleficus that the difference really isn't noticeable when you're just browsing sites. Tests are needed to establish a true difference between the Linux 32-bit and Win 32-bit builds.

However, if you're using 64-bit and Firefox 64-bit, then you have every reason to complain. Firefox 3.5 for 64-bit does NOT have the improved TraceMonkey engine, which means you are not getting any of the 'awesome' speed improvements that everyone talks about when transferring from 3.0.x to 3.5.

---

### Post by Yvan300 on 2009-07-21
Yes firefox does suck under linux and that is why I use epiphany.

---

### Post by keiichidono on 2009-07-22
> **.Maleficus. said:**
> The code is cross-platform C++, they don't write a Windows version, then Linux version and then an OS X version.  It's compiled from the same source.

Firefox on Linux is "slower" than on Windows, there's no doubt about it.  Whether or not you can tell the difference is for you to decide, but I personally can't.  Like Yes said, I imagine it's that MSVC is creating more optimized binaries.  If you really care that much, compile Firefox for your architecture using platform-specific flags.  Even better, if you use an Intel processor use ICC.

Or use it in Wine.

Quoted for truth.

---

### Post by bryonak on 2009-07-22
The Windows version of Firefox is compiled with PGO (profile guided optimisation, one test run and a final compilation), while the Linux version is not.
PGO is a compiler technique in which all ICC, MSVC and GCC are proficient, yet for some reason the Debian package maintainers decided not to use it.

Since this has been happening for quite some time now, one can indeed say that Linux is getting the raw end of Firefox.

Architecture specific optimisation yields 0-20% speed improvements (very roughly speaking), while PGO improves the performance by 30-50%.
I recently compiled Firefox 3.5.1 with PGO on my machine, and it starts up in 2-3 seconds as compared to the usual 6-7 with 3.5(.0).
It's also much more responsive when creating a new tab with 30 long-history tabs already open.

Too bad TraceMonkey isn't ready for 64bit yet...

---

### Post by Ozor Mox on 2009-07-22
> **.Maleficus. said:**
> The code is cross-platform C++, they don't write a Windows version, then Linux version and then an OS X version.  It's compiled from the same source.

I have no doubt that this is true, but what about the subtle differences between the versions?

[LIST]
[*]On Windows, preferences are in Tools > Options. On Ubuntu they are in Edit > Preferences.
[*]Windows has the "keyhole" back and forward buttons, Ubuntu has the standard buttons.
[*]Various differences in the way windows look.
[/LIST]

Is this Mozilla setting compile options? Ubuntu customising Firefox? Differences in window widgets on Windows and Ubuntu? All of the above?

---

### Post by froggyswamp on 2009-07-22
> **Yes said:**
> I've heard that the MSVC (Windows) compiler is much faster than GCC (Linux) compiler.  I'm guessing a lot of the performance differences can be attributed to that.

1) GCC is slower than MSVC is a half truth.
2) Firefox is built off cross-platform C++ is another half truth.
3) Considering market share - it's natural that Mozilla pays (much) less attention to Linux.
4) Some people don't notice the difference between a sledge and a pen, Firefox is slower on Linux by about 15% to 40% depending on what you're benchmarking.

More comments:
1) I did a quick test with a usual big "for" loop on my dual booting machine and it turned out to execute faster on Linux. Unless you do the tests a la M$ - where it suits you best to prove your point - you'll agree that blaming GCC is a hoax.

2) Digg the code - there's different areas where the Firefox code _has_ to be platform specific, i.e. rendering.

3) This is where "market share" kicks in - something that some Linux "fans" try to downplay as saying market share doesn't affect the quality of the overall experience - it does.

---

### Post by Mornedhel on 2009-07-22
> **.Maleficus. said:**
> The code is cross-platform C++, they don't write a Windows version, then Linux version and then an OS X version.  It's compiled from the same source.

Ever try to write a truly cross-platform application ?

You *always* end up developing it for one platform, hoping that it doesn't break on the others, and then spend your time fixing what has broken there, hoping that your fixes don't break the main platform.

It's like saying Unreal Tournament 2004 is cross-platform (it is) and they don't write a Windows version, then a Linux version. The Linux version was very much an afterthought, built by a team of two or three guys on their free time. Obviously Mozilla works with Linux in mind more than Atari does, but you get the point.

(Sorry for the nitpicking, but you seemed to be assuming that because it's C++ and cross-platform it can be expected to work the same under every platform.)

---

