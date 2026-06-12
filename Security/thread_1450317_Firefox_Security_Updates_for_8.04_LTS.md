---
title: "Firefox Security Updates for 8.04 LTS"
date: 2010-04-08
forum: Security
---

### Post by dschaller on 2010-04-08
Does anyone know when we'll see Firefox 3.0.19 packaged for 8.04 LTS? I'm still stuck at 3.0.18. And what will happen after this? My understanding is that after .19 Mozilla is dropping support for FF 3.0.

Upgrade policies not withstanding, I find it rather annoying when an "LTS" release doesn't keep up with the most security-critical package in the distro, the browser. 8.04 LTS should have moved to FF 3.5+ a *long* time ago. Now it seems it will be forced to do so or else just forget about browser updates for the last year of 8.04?

I know I can install the current Firefox with ubuntuzilla, I just keep wishing Ubuntu would do it for me.

---

### Post by lovinglinux on 2010-04-09
I'm curious to know what's gonna happen. I guess they will upgrade to 3.5, since Hardy is supported until April 2011. 

There are a lot of threads about the new major-minor update policy, due to the new Mozilla update scheme. So I guess they will upgrade.

---

### Post by Linuxforall on 2010-04-09
I have added the mozilla stable ppa to all my Hardy LTS installs, this way I stay with the latest browser which is much better designed for today's hacks.

---

### Post by Jigen on 2010-04-09
However, version 3.0.19 is still unavailable even in 9.04. It seems also that 3.5.9 for 9.10 is unavailable. I really don't know what's going on, mozilla team released these new versions (due to several critical vulnerabilities!) 9 days ago :shock:

---

### Post by Bachstelze on 2010-04-09
> **Jigen said:**
> However, version 3.0.19 is still unavailable even in 9.04. It seems also that 3.5.9 for 9.10 is unavailable. I really don't know what's going on, mozilla team released these new versions (due to several critical vulnerabilities!) 9 days ago :shock:

Feel free to submit a package for FF 3.5.9.

---

### Post by Jigen on 2010-04-09
> **Bachstelze said:**
> Feel free to submit a package for FF 3.5.9.

If I was a developer/programmer, I would try to do it with pleasure. Unfortunately, I am not.

---

### Post by FuturePilot on 2010-04-09
> **lovinglinux said:**
> I'm curious to know what's gonna happen. I guess they will upgrade to 3.5, since Hardy is supported until April 2011. 

There are a lot of threads about the new major-minor update policy, due to the new Mozilla update scheme. So I guess they will upgrade.

They may just maintain it themselves like they did with Firefox 1.5 on Dapper.

---

### Post by snowpine on 2010-04-09
You misunderstand how "long term support" works and what it means. Ubuntu 8.04 with Firefox 3.0.x will be fully supported by Canonical through April 2011. If a vulnerability is discovered, Canonical releases an update to 3.0.x with the security patch. This usually takes about a week.

If you prefer to use a more recent Firefox, you can add the mozilla ppa, use ubuntuzilla, or simply download it directly from mozilla.com.

The whole idea of using a stable, long term support distro is that you are never forced to upgrade any application, package, library, or kernel to a new version if you don't want to. New versions may fix old bugs, but they introduce new bugs, so it's better in many situations to keep the old version and patch the bug. Ubuntu, Debian, Red Hat, CentOS, Fedora, SUSE, etc. all follow this approach and are used by many security-conscious institutions and corporations.

Here is a good explanation of the process: [www.redhat.com/advice/speaks_backport.html](www.redhat.com/advice/speaks_backport.html)

---

### Post by lovinglinux on 2010-04-09
> **snowpine said:**
> You misunderstand how "long term support" works and what it means.

I don't think the OP didn't misunderstood how a LTS works. What he/she really wants to know is what's gonna happen after Mozilla drops the support for Firefox 3.0.x. 

> **snowpine said:**
> Ubuntu 8.04 with Firefox 3.0.x will be fully supported by Canonical through April 2011. If a vulnerability is discovered, Canonical releases an update to 3.0.x with the security patch. This usually takes about a week.

How they are going to that if Mozilla will stop releasing patches for Firefox 3.0.x? I know Firefox is open source and anyone could patch it, but I doubt Ubuntu devs will do that or even be allowed to keep the branding with an unsupported version.

---

### Post by snowpine on 2010-04-09
> **lovinglinux said:**
> I don't think the OP didn't misunderstood how a LTS works. What he/she really wants to know is what's gonna happen after Mozilla drops the support for Firefox 3.0.x. 

How they are going to that if Mozilla will stop releasing patches for Firefox 3.0.x? I know Firefox is open source and anyone could patch it, but I doubt Ubuntu devs will do that or even be allowed to keep the branding with an unsupported version.

You are assuming this is a unique situation that nobody has ever dealt with before. :)

Ubuntu Dapper supported Firefox 1.5 through June 2009.
Debian Etch supported FF2.0 through Feb. 2010.
Red Hat 5.x will support FF3.0 through 2014.

Shall I go on? ;)

---

### Post by Soul-Sing on 2010-04-09
> 

Shall I go on? ;)

please do it is very informative.

---

### Post by snowpine on 2010-04-09
> **leoquant said:**
> please do it is very informative.

[http://distrowatch.com/search.php](http://distrowatch.com/search.php)

:)

---

### Post by Objekt on 2010-04-09
I'm not sure I understand the thread starter's question.

Are you simply asking how to install a more current version of Firefox?  There are a few ways to do that.  You are not stuck with whatever version Canonical puts in the repository for your variant of Ubuntu.

---

### Post by snowpine on 2010-04-09
> **dschaller said:**
> I know I can install the current Firefox with ubuntuzilla, I just keep wishing Ubuntu would do it for me.

This.

---

### Post by cdenley on 2010-04-09
> **Objekt said:**
> I'm not sure I understand the thread starter's question.

Are you simply asking how to install a more current version of Firefox?  There are a few ways to do that.  You are not stuck with whatever version Canonical puts in the repository for your variant of Ubuntu.

Ubuntu 8.04 is still supported, so the version that is in the repository should be kept current with all known vulnerabilities patched. As the thread starter pointed out, this is not currently the case, and he was asking when this might be fixed.

---

### Post by lovinglinux on 2010-04-09
> **snowpine said:**
> You are assuming this is a unique situation that nobody has ever dealt with before. :)

Ubuntu Dapper supported Firefox 1.5 through June 2009.
Debian Etch supported FF2.0 through Feb. 2010.
Red Hat 5.x will support FF3.0 through 2014.

Shall I go on? ;)

All right then. :)

---

### Post by FuturePilot on 2010-04-09
Looks like it's been uploaded to the repos. [http://www.ubuntu.com/usn/USN-920-1]("http://www.ubuntu.com/usn/USN-920-1")

---

### Post by Jigen on 2010-04-10
> **FuturePilot said:**
> Looks like it's been uploaded to the repos. [http://www.ubuntu.com/usn/USN-920-1](http://www.ubuntu.com/usn/USN-920-1)

yes, now I feel safer, I was really worried about these vulnerabilities, in fact it has been shown that they also affect ubuntu systems [http://www.ubuntu.com/usn/USN-921-1](http://www.ubuntu.com/usn/USN-921-1) [http://www.ubuntu.com/usn/USN-920-1](http://www.ubuntu.com/usn/USN-920-1)
  let's hope nobody was victim of active exploits of the vulnerabilities (especially the one regarding privilege escalation) during the last days :(

---

### Post by dschaller on 2010-04-10
I'm the thread starter here. Sorry if I raised any hackles. I didn't mean to. Yes, my main question was what's going to happen after upstream support for FF 3.0.x has been dropped. I (apparently wrongly) assumed that once there was no upstream, there would be no more security updates. If Ubuntu will keep on patching 3.0.x themselves, then I'm fine with it, although I do hope the updates will be a little more timely than the recent 10-day delay for 3.0.19.

---

### Post by Jigen on 2010-04-10
> **dschaller said:**
> If Ubuntu will keep on patching 3.0.x themselves, then I'm fine with it, although I do hope the updates will be a little more timely than the recent 10-day delay for 3.0.19.

Yes, I totally agree. I really respect the work of Ubuntu's developers and I'm very grateful to them for all their efforts , but I cannot refrain from saying that a 10-day delay in fixing critical vulnerabilities of the default web browser is a rather worrying issue. Let's hope it was just an isolated case because of the work overload due to the incoming release of Lucid ;)

---

### Post by Pjotr123 on 2010-04-10
> **snowpine said:**
> You misunderstand how "long term support" works and what it means. Ubuntu 8.04 with Firefox 3.0.x will be fully supported by Canonical through April 2011. If a vulnerability is discovered, Canonical releases an update to 3.0.x with the security patch. This usually takes about a week.

If you prefer to use a more recent Firefox, you can add the mozilla ppa, use ubuntuzilla, or simply download it directly from mozilla.com.

The whole idea of using a stable, long term support distro is that you are never forced to upgrade any application, package, library, or kernel to a new version if you don't want to. New versions may fix old bugs, but they introduce new bugs, so it's better in many situations to keep the old version and patch the bug. Ubuntu, Debian, Red Hat, CentOS, Fedora, SUSE, etc. all follow this approach and are used by many security-conscious institutions and corporations.

Here is a good explanation of the process: [www.redhat.com/advice/speaks_backport.html](www.redhat.com/advice/speaks_backport.html)

Excellent explanation, and a useful link. Thanks. :)

---

