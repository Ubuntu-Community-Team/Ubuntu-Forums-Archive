---
title: "Latest Security Threat?"
date: 2009-07-19
forum: Security
---

### Post by drifter2502 on 2009-07-19
Is this true? Can anyone confirm this and if so...Is it being dealt with?...... attack exploits fully-patched Linux kernel   [http://www.theregister.co.uk/2009/07/17/linux_kernel_exploit/](http://www.theregister.co.uk/2009/07/17/linux_kernel_exploit/)

---

### Post by kostkon on 2009-07-19
I think *Ubuntu* does not use *SELinux* by default (it uses *AppArmor* instead).

Also, a *PulseAudio* security update came a couple of days ago that it may have something to do with the exploit; as I can see the article mentions *PulseAudio*, saying that this exploit works also when *PulseAudio* is present in the system.

But, I don't really know. Its [page]("http://www.ubuntu.com/usn/usn-804-1") doesn't say much.

---

### Post by newbie2 on 2009-07-20
'NULL pointer' bug plagues even super max versions :
[http://www.theregister.co.uk/2009/07/17/linux_kernel_exploit/](http://www.theregister.co.uk/2009/07/17/linux_kernel_exploit/)
:rolleyes:

---

### Post by TuckLive on 2009-07-20
Interesting article.  Thanks for the link.

---

### Post by Sef on 2009-07-20
merged threads: same article.

---

### Post by Arup on 2009-07-20
From what I read, it affects newer 2.6.30 kernel which only few distros use currently like Sidux, Ubuntu is still on older kernel.

---

### Post by lensman3 on 2009-07-20
Seems gcc optimized away a !tun test, as the tun->xxx?? was already assigned.

---

### Post by grayn0de on 2009-07-20
Doesn't the article state that the exploit relies on setuid? It seems to me that this would be a design flaw, rather than a kernel vulnerability. Either way, it *would* be nice to know if anyone is working to mitigate this risk.

---

### Post by movieman on 2009-07-20
Indeed: what I've read implies  that the 'exploit' requires root access (via setuid or otherwise) in order to insert new kernel modules. If an attacker can insert new modules into the kernel, then your security is toast anyway.

It's a bug and ought to be fixed, but everything appears to show that it's a minor issue which has no real impact on security on 99% of systems (some might not crash when accessing a NULL pointer in the kernel).

---

### Post by bodhi.zazen on 2009-07-20
> **grayn0de said:**
> Doesn't the article state that the exploit relies on setuid? It seems to me that this would be a design flaw, rather than a kernel vulnerability. Either way, it *would* be nice to know if anyone is working to mitigate this risk.

The ubuntu forums are not the best place to follow such security bugs. Try #ubuntu-security (IRC) and launchpad. If you file a bug report on LP, identify it as a security flaw, you will have all the follow up you desire =).

---

### Post by bodhi.zazen on 2009-07-20
> **movieman said:**
> Indeed: what I've read implies  that the 'exploit' requires root access (via setuid or otherwise) in order to insert new kernel modules. If an attacker can insert new modules into the kernel, then your security is toast anyway.

This subtle point is most often missed or over looked in threads such as this.

---

### Post by grayn0de on 2009-07-20
> **bodhi.zazen said:**
> The ubuntu forums are not the best place to follow such security bugs. Try #ubuntu-security (IRC) and launchpad. If you file a bug report on LP, identify it as a security flaw, you will have all the follow up you desire =).

Heh.. I keep forgetting about IRC for such things. I'll check and see if Launchpad has a bug report already. I'm not really interested in filing a bug myself, since it takes root access to 'exploit' the kernel, anyway. I can just imagine the feedback for that. ;)

---

### Post by movieman on 2009-07-20
> **grayn0de said:**
> I'll check and see if Launchpad has a bug report already. I'm not really interested in filing a bug myself, since it takes root access to 'exploit' the kernel, anyway. I can just imagine the feedback for that. ;)

It appears to be fixed in the latest kernel release anyway, so no distribution with any sense will ever ship with this bug (I don't believe anyone is currently shipping the kernel versions where it exists).

---

### Post by TDK800 on 2009-07-20
"Having SELinux enabled actually weakens system security for these kinds of exploits," he wrote. 

So this is why the NSA was so "helpful" with SELinux to "increase security".

---

### Post by movieman on 2009-07-20
> **TDK800 said:**
> So this is why the NSA was so "helpful" with SELinux to "increase security".

No tinfoil hat required, I'm afraid.

It's not SELinux per se that makes you less safe, it's SELinux policies which are configured to allow any application to map data into page zero, rather than just privileged applications.

This is probably the most interesting part of this 'exploit': I'm not sure who decided that allowing any application to map things into page zero was a really good idea, but this is a good kick up the butt to get distributions to change those policies.

---

