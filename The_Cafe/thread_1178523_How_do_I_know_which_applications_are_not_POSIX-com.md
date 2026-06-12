---
title: "How do I know which applications are not POSIX-compliant?"
date: 2009-06-04
forum: The Cafe
---

### Post by aysiu on 2009-06-04
I'm interested in this new Ext4 thing.

I've heard about possible data loss. And I've also heard if you use certain workarounds to prevent data loss, the performance gains of Ext4 are only minimal.

The conventional wisdom seems to be that the data loss isn't Ext4's "fault" but the fault of applications that are not POSIX-compliant (whatever that means).

So I'm just curious: how do I know which applications are not POSIX-compliant? And if I don't use any of those applications, is data loss pretty unlikely?

---

### Post by collinp on 2009-06-04
This may be part of the POSIX standards, but the data loss that I have heard of mainly occurs when a person kills the power to the computer (primarily by shutting it down with the power button, but other ways will do it too). That comes from ext4's vaunted speed increases: caching into RAM.

Anyhow, there are sure to be bugs in the code that we have not discovered yet that could cause data loss. Ext4 is new, and there are many things that could go wrong. Even though I use it and have not encountered data loss, I may be lucky.

Got a little off-topic there, I /think/ these are the POSIX standards: [http://www.opengroup.org/onlinepubs/009695399/](http://www.opengroup.org/onlinepubs/009695399/)

---

### Post by cmay on 2009-06-04
> **aysiu said:**
> I'm interested in this new Ext4 thing.

I've heard about possible data loss. And I've also heard if you use certain workarounds to prevent data loss, the performance gains of Ext4 are only minimal.

The conventional wisdom seems to be that the data loss isn't Ext4's "fault" but the fault of applications that are not POSIX-compliant (whatever that means).

So I'm just curious: how do I know which applications are not POSIX-compliant? And if I don't use any of those applications, is data loss pretty unlikely?
links on the posix thinghy. 
[http://en.wikipedia.org/wiki/POSIX](http://en.wikipedia.org/wiki/POSIX)

the open groups singel specification page that is linked to at the bottom is very interesting reading also. 

i am simly too tired to refflect upon this but i think it sounds  strange that a application will have greater chance at producing data loss if it is not posix than if it is. it sounds like the file format expects a certain way of programs handling files to work right.

---

### Post by Namtabmai on 2009-06-04
Do a search for "fsync ext4", this is one of the major concerns I heard leveled at ext4.

---

### Post by baseface on 2009-06-04
why not give zfs a try?

---

### Post by .Maleficus. on 2009-06-04
> **baseface said:**
> why not give zfs a try?
Isn't ZFS only faster with larger files?

As for data loss with Ext4, improper shut-down seems to be what is causing the majority of it.  I haven't had any problems with it and I've been using it since it went to Arch's 2009.02 build.  I also haven't cut the power to my computer without actually issuing 'halt' though.

---

### Post by aysiu on 2009-06-04
I can't really think of a situation in which I'd have an improper shut down.

I have a netbook (and, yes, that is my main computer), so if the power cuts out from the plug, it'll just go to battery.

Maybe I will give it a go. I always back up my data anyway, I guess.

---

### Post by samjh on 2009-06-04
POSIX is an operating system standard, not an application programming standard.

The criticisms that Ted Tso levelled at application programmers are criticisms about lazy programming, rather than any break from standards.  Unfortunately, lazy programming occurs just about everywhere.

Not all fault can be levelled at application programmers.  The POSIX standards do not specify behaviour for system crashes, nor does it dictate how files should be safely handled.  All that application programmers have done is use the assumption (in the absence of specifications in POSIX) that their code is OK because ext3 seems to work well with their code.  Unfortunately, system programmers who create file systems have gone on to enhance performance using the delayed allocation feature and assuming that application programmers have written robust code.  Well, applications are not robustly written, and therefore: data loss.

The thing is, ext4 is not alone in using the 30 seconds delays for its delayed allocation feature.  XFS, and probably many others, use similar periods.  It's just that ext4 has had more publicity due to it being the next flagship file system for Linux.  Ted Tso has submitted his patch to reduce the delay to 5 seconds, which will alleviate the problem.  That patch has been backported to Jaunty (as well as Fedora 11's kernel, and I suspect other newly-released or soon-to-be-released distro kernels).

---

### Post by aysiu on 2009-06-04
Thank you, samjh. That makes things a little clearer.

---

### Post by Polygon on 2009-06-04
without looking at the code, there really is no way to tell. Hopefully in time people will start writing their code to anticipate delayed allocation and fsync when necessary.

---

### Post by unknownPoster on 2009-06-04
> **baseface said:**
> why not give zfs a try?

I had a ZFS drive that corrupted itself when I lost power at my house...needless to say, I don't use ZFS anymore.

---

