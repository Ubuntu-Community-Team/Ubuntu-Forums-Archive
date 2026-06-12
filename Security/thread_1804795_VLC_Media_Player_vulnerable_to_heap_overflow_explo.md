---
title: "VLC Media Player vulnerable to heap overflow exploits"
date: 2011-07-15
forum: Security
---

### Post by jtarin on 2011-07-15
[Security Advisory 1106]("http://www.videolan.org/security/sa1106.html")

Summary           : Heap overflow in AVI demuxer
Date              : 12 July 2011
Affected versions : VLC media player 1.1.10 down to 0.5.0
ID                : VideoLAN-SA-1106
CVE references    : CVE-2011-2588

---

### Post by uRock on 2011-07-15
Moved to *Security Discussions*.

---

### Post by bodhi.zazen on 2011-07-15
> **jtarin said:**
> [Security Advisory 1106]("http://www.videolan.org/security/sa1106.html")

Summary           : Heap overflow in AVI demuxer
Date              : 12 July 2011
Affected versions : VLC media player 1.1.10 down to 0.5.0
ID                : VideoLAN-SA-1106
CVE references    : CVE-2011-2588

So what ? Security alerts are a dime a dozen.

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

Keep your system up to date and use apparmor or selinux.

What is your question.

---

### Post by Soul-Sing on 2011-07-15
It isn't patched. Mind, Ubuntu in general patches sec. issues fast.
I did add an PPA for VLC to get the newest stuff faster.
[https://launchpad.net/~n-muench/+archive/vlc](https://launchpad.net/~n-muench/+archive/vlc)

(i am not a fan of PPA's in general by the way)

---

### Post by bodhi.zazen on 2011-07-15
> **leoquant said:**
> It isn't patched.

Has it been exploited ? A vulnerability is not the same as an exploit.

Edit: This is why we use apparmor or selinux, "zero day exploits"

---

### Post by uRock on 2011-07-15
I thought I had recently witnessed an update for VLC, but that might have been on the machine I ran a clean install on.

---

### Post by ester4 on 2011-07-17
> **bodhi.zazen said:**
> Has it been exploited ? A vulnerability is not the same as an exploit.

Edit: This is why we use apparmor or selinux, "zero day exploits"

Bodhi, is apparmor setup on people's machines for VLC? I like the idea of apparmor, but only people like you who are awesome computer dudes know how to use it.

I've looked over apparmor, I still have no idea how to utilize it. It's way over my head. So how realistic is it to tell people to be using it? If it isn't set up for us by the developers, it's probably not going to get used by the majority of non-technical computer users like me. By the way, I'm considered a "computer genius" by my friends and family--so my point is that the majority of people don't have the knowledge to be able to use it.

---

### Post by jtarin on 2011-07-17
> **bodhi.zazen said:**
> Has it been exploited ? A vulnerability is not the same as an exploit.
Has it been exploited? I dunno...let me take a poll. :P  
It says "A _vulernability _to an exploit", which means the possibility exist at the time for it to be exploited. 


> **bodhi.zazen said:**
> Edit: This is why we use apparmor or selinux, "zero day exploits"
Do you imagine everyone using VLC or some other affected application has implemented Apparmor or much less know what it is.I'm afraid most newbies do not......better to be on the safe side than not. I'm not some security nut-job crying wolf, but I deal with a lot of .avi's and I'm sure there are others. Which should come first...the accident or the warning?

---

### Post by bodhi.zazen on 2011-07-17
> **jtarin said:**
> Has it been exploited? I dunno...let me take a poll. :P  
It says "A _vulernability _to an exploit", which means the possibility exist at the time for it to be exploited. 



Do you imagine everyone using VLC or some other affected application has implemented Apparmor or much less know what it is.I'm afraid most newbies do not......better to be on the safe side than not. I'm not some security nut-job crying wolf, but I deal with a lot of .avi's and I'm sure there are others. Which should come first...the accident or the warning?

With security you can not have your cake and eat it too.

Sounds as if:

1. You do not know the difference between a vulnerability and an exploit.

2. You can not complain about potential vulnerabilities and then refuse to learn to use the appropriate security tool.

Apparmor is covered in the stickies in the security section, if you would take the time to read them.

Vulnerabilities are listed on several web sites, I already gave you a link for Ubuntu, but will give it to you again:

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

Security is not a matter of install it and forget it, it is a matter of learning to educate yourself.

I am closing this thread now as these vulnerabilities are listed, and managed elsewhere (Launchpad, bug reports -> mark as a security issue), not on the forums, not with polls on the forms, and not by an unwillingness to learn.

Feel free to start a new thread once you have done some reading and have some questions, otherwise relax and enjoy Ubuntu ;)

---

