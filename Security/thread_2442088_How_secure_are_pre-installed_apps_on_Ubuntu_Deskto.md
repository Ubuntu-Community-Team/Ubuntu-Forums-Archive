---
title: "How secure are pre-installed apps on Ubuntu Desktop?"
date: 2020-04-29
forum: Security
---

### Post by darkmatter2020 on 2020-04-29
I was planning to install the latest version of Ubuntu desktop. However, I see that the install comes with a lot of pre-installed applications. Are these verified to be secure? Can I be sure there is no malware in these applications?

---

### Post by ActionParsnip on 2020-04-29
There is no malware in any Ubuntu distribution....

If you want to reduce packages you can install Ubuntu Minimal then install the desktop of your choice (Not using the metapackage) like lxde or even just a window manager like openbox (for a super light OS).

You will need to install something like lightdm or gdm to get a graphical log in.

---

### Post by darkmatter2020 on 2020-04-29
I would like to do the normal installation. Is there any scope for malware in any of those applications which come pre-installed?

---

### Post by EuclideanCoffee on 2020-04-29
If you want the most secure distribution, you would need to inspect each  compiled software at all phases. Because this is impossible to do  individually, we trust that the developers are following best practices  like deterministic builds.

Ubuntu is a downstream distribution of Debian, which follows the deterministic build principle. Each binary will have the same binary as the distribution, which means all packages are verified to be built under the best conditions as possible.

Further reading: [https://wiki.debian.org/ReproducibleBuilds](https://wiki.debian.org/ReproducibleBuilds)

We trust that the distributed packages contain no malware.

You can further improve the security of your Ubuntu install. Here's a helpful guide on determining your risk and mitigating it.

[https://www.ncsc.gov.uk/collection/end-user-device-security/platform-specific-guidance/ubuntu-18-04-lts](https://www.ncsc.gov.uk/collection/end-user-device-security/platform-specific-guidance/ubuntu-18-04-lts)

---

### Post by DuckHook on 2020-04-29
Please read the link in my sig: "Security Basics".

No one can guarantee you 100% security perfection. Such perfection does not exist in our imperfect world. This includes the apps in the repos and it includes the Ubuntu distro itself. And even with the best of intentions, holes are regularly discovered in Linux itself and the foundational utilities and libraries that make it useful. This is why we update and patch.

Nonetheless, I have confidence in my install and the apps from the repos. I take reasonable precautions and don't do stupid things.

It bears mentioning that the vast majority of security problems that users run into are the result of their own unwise or uninformed actions. Holes in the OS itself are a tiny fraction of the problem. The problem that most users have trouble wrapping their heads around is their own silly behaviour. Most, especially general users coming from the Windows world, think that security is app-based and not behaviour-based.

Ages ago, I wrote a response to a similar question. Aside from a few outdated references, it has aged surprisingly well. No point in my repeating myself, so if you are interested: [https://ubuntuforums.org/showthread.php?t=2184758&p=12833795#post12833795](https://ubuntuforums.org/showthread.php?t=2184758&p=12833795#post12833795)

---

### Post by EuclideanCoffee on 2020-04-29
I would like to respectfully disagree on keeping the status quo advice.

There have been huge improvements made to the kernel to mitigate the attacks documented in this article.

[https://www.forbes.com/sites/daveywinder/2020/04/07/linux-security-chinese-state-hackers-have-compromised-holy-grail-targets-since-2012/#60aaae282086](https://www.forbes.com/sites/daveywinder/2020/04/07/linux-security-chinese-state-hackers-have-compromised-holy-grail-targets-since-2012/#60aaae282086)

In the past, we did not recommend apparmor, and now it's included with many profiles on every new install.

Today we can also implement kernel lockout, which was a Red Hat exclusive patch for a long time.

Security does change. And there is a lot to learn about it.

The biggest question is what is your use case and how much do you need to ensure complete compliance to a security model.

Edit.

I would like to say that Ubuntu is one of the most security-focused operating systems out there. Perhaps not the best, but it's very good.

Let us do a case study. Gentoo had a supply chain attack. [https://github.com/cncf/sig-security/pull/284](https://github.com/cncf/sig-security/pull/284)

What prevents this in Ubuntu are two teams. Security on Debian is a community-ran operation, which some paid employees making security changes for organizations paying them to create those changes.

Ubuntu has a main and security repository that maintain Ubuntu specific security patches. These patches are the second filter for the user, where patches are typically applied both ways, with the Ubuntu team focusing on specific repositories and applying patches as vulnerabilities are made known.

Gentoo lacked that infrastructure.

---

### Post by Frogs Hair on 2020-04-29
Unlike the proprietary software that comes with and for Windows the source code for default applications in Linux is publicly available for inspection. Malware that is designed  for Mac and Windows simply won't run on Linux. Clam AV is available if you are share files with Windows. See the basic security link in my signature. 

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[https://linux.oneandoneis2.org/LNW.htm](https://linux.oneandoneis2.org/LNW.htm)

---

### Post by darkmatter2020 on 2020-04-30
Thank you for your responses. Probably my question was not properly understood. What I really wanted to understand was if Ubuntu has any security review process in place while deciding which pre-installed apps to include with their OS distribution. How can we be sure that there is no malware in these pre-installed apps?

Now, I am just a regular user of Ubuntu desktop. I mainly do browsing and some programming too. However, I am concerned about any malware recording my keystrokes and stealing my passwords.

---

### Post by EuclideanCoffee on 2020-04-30
Check the ISO hashes.

Example:

md5sum *ubuntu-20.04-desktop-amd64.iso

Should be the same as here:

[URL="https://releases.ubuntu.com/20.04/MD5SUMS"]https://releases.ubuntu.com/20.04/MD5SUMS

[/URL]The same can be done for each package installed. [http://archive.ubuntu.com](http://archive.ubuntu.com)

[https://manpages.ubuntu.com/manpages/bionic/man1/debsums.1.html](https://manpages.ubuntu.com/manpages/bionic/man1/debsums.1.html)

---

### Post by ActionParsnip on 2020-04-30
There is none of that in the packages in the OS. To do so would harm the OS and users who peruse the code would flag it up quickly as a security bug. Nothing in the default install will "steal your passwords" or "record keystrokes"

---

### Post by mrdc76 on 2020-04-30
> **darkmatter2020 said:**
> Thank you for your responses. Probably my question was not properly understood. What I really wanted to understand was if Ubuntu has any security review process in place while deciding which pre-installed apps to include with their OS distribution. How can we be sure that there is no malware in these pre-installed apps?


A Linux distribution does not have a wall of separation between "pre-installed apps" and the OS. There are only packages of software that constitute the distribution. You are thinking in Windows terms there.

---

### Post by EuclideanCoffee on 2020-04-30
No one should blindly trust the OS.

> 
There is none of that in the packages in the OS. To do so would harm the OS and users who peruse the code would flag it up quickly as a security bug. Nothing in the default install will "steal your passwords" or "record keystrokes"


It is wrong to assume that the files you have are correct until you check.

The OS has many tools that do this automatically, but here is how they work.

Ubuntu does some automated checks. When you run $ apt update and $ apt upgrade, Ubuntu will check a list from a remote repository. It checks the hashes of the repository and the packages you install against the public repository.


[LIST=1]
[*]The repository has the correct GPG signature.
[*]The hashed files match the repository index.
[/LIST]

However we need to trust the GPG signature of the remote repository. Ubuntu distributes keys on the ISO that allows us to trust this source without needing to manually validating.

What then is the root value you should validate _**to know**_ that your software is secure.

Check the ISO hash. This will tell you if the hash you received is correct.

Reasons the hash would be incorrect.

[LIST=1]
[*]Temporarily, your traffic was intercepted and modified to give you the wrong file.
[*]Someone has hacked this mirror and is distributing the wrong file.
[*]Your memory failed to write the file to hard drive.
[*]You didn't install the correct file.
[/LIST]

You will never know until you check. Check the hashes of the files you download.

> 
A Linux distribution does not have a wall of separation between "pre-installed apps" and the OS. There are only packages of software that constitute the distribution.


This is wrong.

The application on the ISO are pre-installed. There is no question about it. You install it onto the partition that installs the same packages to your new Ubuntu computer.

> 
You are thinking like a Windows user there.


This is impolite. Please remove this from your post.

---

### Post by DuckHook on 2020-04-30
@darkmatter2020

At the risk of piling on, some of the previous posts have been at cross purposes. I'm contributing my two pennies in the hope that it clarifies rather than further confuses.

I don't think mrdc76 meant anything condescending with his/her statement: > You are thinking in Windows terms there.Rather, I suspect what was meant was something along the following lines:

[list]
[*]In the Windows world, users have been conditioned to download everything from third-party sites the majority of which they, frankly, know next to nothing about.
[*]The Linux world differs crucially from this highly insecure practice in that apps are housed in repos. Moreover, they are not simply housed there opaquely (as is the case in proprietary app stores), but compiled from source. This crucial element of transparency means that malicious code has a very high barrier to surmount before it can sneak into the repos. Not impossible, but very difficult.
[*]It is worth noting that Snaps do not go through the same vetting process. They are almost entirely the reponsibility of their individual devs and the vetting process by Canonical is less thorough. In this regard, they are sort of halfway to being PPAs. Their big saving grace is that the Snap architecture is, by design, a sandbox. Therefore, rogue apps are still more likely to be contained. Such containment is not a magic bullet (see below).
[*]
[/list]
> What I really wanted to understand was if Ubuntu has any security review process in place while deciding which pre-installed apps to include with their OS distribution. How can we be sure that there is no malware in these pre-installed apps?
Your question might sound simple, but your concern cannot be addressed monolithicly. Malware can make it into your system in any of the following ways:

[list=1]
[*]An actively malicious developer foists it upon an unwary or insufficiently vetted app store. This is what happens all the time in the proprietary app stores. As already explained above, forcing authors to upload source code under FOSS-type licenses to properly guarded repos alleviates most of these concerns.
[*]A careless but well-meaning developer writes an app that has security holes which are subsequently exploited by bad actors. This is also somewhat mitigated by code transparency, though not as much as Linux advocates like to think (search for "Heartbleed").
[*]Good solid apps with transparent code housed in reputable repos are nonetheless sideswiped by a site hijack, or a MitM attack, or a supply chain poisoning. This threat is very real and is highly dependent on good site hygiene, download hygiene and certificate hygiene. These are the measures that EuclideanCoffee has covered off so well.
[*]You do something stupid. This is by far the number one malware vector. It is so far out in front of the others as to leave them eating its dust. It is also the vector of which people are most deluded about themselves: for example, wasting hours of time installing anti-virus apps while choosing auto login.
[/list]
So, to directly answer your question:

[LIST=1]
[*]For apps in the repos, we rely on a huge community of knowledgeable users to go through the source code and sniff out bad stuff. Bad stuff can be anything from intentional malice to sloppy code. This is possible only because, in the FOSS world, the code is open to inspection. This very transparency serves to discourage malicious code in the first place. If this is not good enough for you, then there is no further practical solution and you had best avoid using Ubuntu.
[*]The usual suggestion to "compile your own apps from source" I find to be unconvincing. If one takes the attitude that Canonical itself is suspect, then what advantage is there to compiling from source? If the compiler itself is corrupted, then even clean source code will yield a corrupt binary. At some point, you have to trust someone.
[*]For apps in the Snap store, you are well advised do your research. If they are in turn transparent, open to inspection and reliably compiled, then it is not worth worrying about. However, be aware that there is a greater danger with the Snap store than with the repos.
[*]To be safe, don't trust anything from outside the official repos/Snap store.
[*]Do NOT add PPAs. If you absolutely must, then sandbox them in a VM or a container. If you know the PPA author well and decide that s/he is trustworthy, then the question of trust is rendered irrelevant.
[*]People who do not practice good user hygiene are the authors of their own misery and all of the foregoing is just wasted breath.
[/LIST]
Further to the above point, have a look at [this old thread]("https://ubuntuforums.org/showthread.php?t=2170638"). In it, hakermania outlines a scenario where users can be keylogged without any root compromise. His scenario reinforces the observation that the primary user weak point is not malware, but the guy/gal in the mirror.

Good Luck and Happy Ubuntu-ing.

---

