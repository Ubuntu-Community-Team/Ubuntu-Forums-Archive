---
title: "Anyone poke around with Nexenta yet?"
date: 2007-02-28
forum: The Cafe
---

### Post by izanbardprince on 2007-02-28
[http://www.nexenta.com/]("http://www.nexenta.com/")

It's based on Ubuntu, but instead of the Linux kernel it uses Solaris.

I played around with it in a virtual machine, but didn't really get into it much.

Is Solaris compatible with Linux?

---

### Post by spockrock on 2007-02-28
I downloaded it, I haven't gotten around to installing it.

---

### Post by izanbardprince on 2007-02-28
I didn't want to install it because I really didn't feel like hosing my Ubuntu install or partitioning or anything, I don't really know what benefit there would be to using Solaris instead of Linux anyway, I know Solaris qualifies as UNIX under the Single UNIX Specification, but Linux is the de-facto standard pretty much anyway.

---

### Post by Bagboy23 on 2007-02-28
Sun Solaris is where it all began for me. :guitar:

---

### Post by Quillz on 2007-02-28
What do you mean by compatible? I believe Solaris is a fully certified UNIX kernel, whereas Linux is only UNIX-like.

---

### Post by izanbardprince on 2007-02-28
> **Quillz said:**
> What do you mean by compatible? I believe Solaris is a fully certified UNIX kernel, whereas Linux is only UNIX-like.

Right, Linux is kind of off doing it's own thing, thats why FreeBSD needs a Linux compatibility layer, I was just wondering how interoperable Linux and Solaris would be.

---

### Post by Trespasser on 2007-03-06
I've tried Nexenta Alpha 6 a month or two back. It uses Ubuntu Dapper Gnome as its OS but with a Solaris kernel. Installed fine but some of my hardware (like sound for instance) did not work and I found it extremely slow. It was interesting but you soon grow tired of all the problems you encounter. This distro has a long, long way to go before it will appeal to anyone. Alpha 7 test 1 is out. Will probably try it tomorrow to see if there are any improvements.

Later...

---

### Post by G Morgan on 2007-03-07
> **izanbardprince said:**
> Right, Linux is kind of off doing it's own thing, thats why FreeBSD needs a Linux compatibility layer, I was just wondering how interoperable Linux and Solaris would be.

Note that FreeBSD isn't a certified UNIX(r) either, it does not match up to the Single Unix Specification from The Open Group. Fact is both *BSD and Linux move to fast to justify consistent recertification. Each distro in Linux would have to be certified on it's own, for Ubuntu they would have to certify all the various branches and all the various releases in isolation. It just isn't viable so they don't even bother. Besides it is meaningless.

Also note that if you did follow the standard it doesn't guarantee binary compatibility in any case. The standard says little about the shape of the IVT. Without getting too technical Linux passes arguments to interrupts by setting a pre-defined register, BSD passes arguments by pushing the arguments onto the stack. This means you will never have out of the box binary compatibility with BSD and have to use a compatibility layer. The same would be true of certified Unix.

---

### Post by Sporkman on 2007-09-07
I'm interested in how this thing plays out. The idea of having a choice of ubuntu with different kernels is an appealing idea.

---

### Post by urukrama on 2007-09-07
Shouldn't this be in the "Other OS" forum?

---

