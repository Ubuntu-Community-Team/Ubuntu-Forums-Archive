---
title: "Security of repositories"
date: 2010-03-18
forum: The Cafe
---

### Post by BobJam on 2010-03-18
It just now occurred to me.

In the Update Manager, you are requested to enter your password in order to install the updates.

I automatically do this quickly, as a matter of course WITHOUT thinking.

But what about if somebody hacked into the repository servers, and in fact you are downloading malware?

I suspect this is unlikely, but nevertheless possible . . . isn't it?

And if it is possible, then I suspect the "word" would get out soon and Canonical would withdraw the updates until it was "fixed".  (Wait a minute . . . if a hacker put out the updates, how could Canonical withdraw them?  OK, thinking out loud here, I guess Canonical would have to shut down the server entirely).  Nevertheless, the first ones to do this would still get malware.

Granted, linux malware is rare, and perhaps even rarer in the wild.  Plus, I expect a hacker would have to spend quite a bit of time trying to figure out how to hack into a repository server (which I would imagine has industrial strength security anyway).  Considering the market share of Linux, that hacker would either have to be flat out stupid or extremely dedicated.  I expect if s/he spent the same amount of time doing a Windoze hack, s/he would get a bigger bang for their buck.

In any case, my question stands.  It is possible, isn't it?  And if so, is there any way to defend against it?

(The only way I would think to defend against it would be to decline giving the password, thus cancelling the entire update, and wait to see if any "word" of a breach was broadcast.  I use to do this with Windoze updates, especially considering they were frequently buggy.  But doing this with Linux/Ubuntu seems like it would be overkill.  As I see it right now, the concern is minimal, but it seems like declining the password request is designed ONLY for this circumstance.  Not so?)

---

### Post by undecim on 2010-03-18
The update servers are pretty secure. If they weren't they would have been comprimised already.

Of course, any time you download and run software, you are trusting that the people giving it to you aren't giving you malware.

If you are really paranoid, you can disable updates, avoid malicious websites, and install noscript and adblock onto firefox. Or maybe just use Lynx to browse the web.

EDIT: now that I think about it, some way to delay updates for, say, 12 hours might be useful. The package manager would need to download the packages immediately, otherwise it would do no good.

---

### Post by spiderbatdad on 2010-03-18
I believe what you describe is the thing next to impossible. You would certainly get apt security warnings. See apt security for more details:
[http://wiki.debian.org/SecureApt](http://wiki.debian.org/SecureApt)

---

### Post by ankspo71 on 2010-03-18
Hi,
I think all packages have to be approved before they make it into the list of available updates. Not only that, but the majority of software available in the repos is open source, and that means that any developer can sumbit a fix to bad software. We all have access to the sources of open source software, so it is there if anyone wants to look through the sources to make sure they aren't malicious before installing.
Hope this helps.

---

### Post by tom.swartz07 on 2010-03-18
> **ankspo71 said:**
> Hi,
I think all packages have to be approved before they make it into the list of available updates. Not only that, but the majority of software available in the repos is open source, and that means that any developer can sumbit a fix to bad software. We all have access to the sources of open source software, so it is there if anyone wants to look through the sources to make sure they aren't malicious before installing.
Hope this helps.

+1

The software repos are extremely secure. Its practically impossible to hack into, upload malicious code, and get others to download the updates without having security warnings going off.

As long as you know that the repo is safe, it will stay that way.

---

### Post by louieb on 2010-03-18
Cafe stuff: In 4 years of using Ubuntu I've had my system break after an update once - that was an xorg update to  v6.06 Dapper.  -  That update broke a lot of systems - had the forum buzzing. - A workaround was quickly posted  - how could this happen. - In this case it was an upstream bug fix that had not been thoroughly tested.

For a while after that a lot of us would let xorg and kernel updates sit a day or two and look for post to see if the latest update was good to use.

---

### Post by BobJam on 2010-03-18
The consensus seems to be much as I had posted:  Concern about this is overkill.

However, there also seems to be some consensus on waiting for a few days.  Seems prudent even if ihacking is unlikely.  I doubt very much there are any zero-day exploits for Linux!

Not really paranoid about this, so I don't need to tediously examine source code (not that I would know how to do this anyway).  Being as waiting for a few days would not involve any rigorous technical skills, it seems that would be easy enough to do, even for me.

---

### Post by master5o1 on 2010-03-18
The package lists and most (if not all) information about a repository are signed by a PGP key.  This probably gives it enough security as if the list doesn't authenticate with the signature then the repository can't be used by apt.

Then there are the checksums :)

---

### Post by Post Monkeh on 2010-03-18
very unlikely, you'd be more likely to get something if you had 3rd party repositories in use and just downloaded updates without checking, but in theory i suppose any system could be compromised. 
just do what i do and don't download updates for a few days to wait and see if anyone else is complaining ;)

---

### Post by snova on 2010-03-18
> **BobJam said:**
> It just now occurred to me.

In the Update Manager, you are requested to enter your password in order to install the updates.

I automatically do this quickly, as a matter of course WITHOUT thinking.

But what about if somebody hacked into the repository servers, and in fact you are downloading malware?

I suspect this is unlikely, but nevertheless possible . . . isn't it?

Anything is possible. It would be the equivalent of hacking Microsoft's update servers, except once you get there, the layout of the archive is well known and documented. I hope it's hard though.

> Granted, linux malware is rare, and perhaps even rarer in the wild.  Plus, I expect a hacker would have to spend quite a bit of time trying to figure out how to hack into a repository server (which I would imagine has industrial strength security anyway).  Considering the market share of Linux, that hacker would either have to be flat out stupid or extremely dedicated.  I expect if s/he spent the same amount of time doing a Windoze hack, s/he would get a bigger bang for their buck.

On the contrary. Writing malware is not hard- it's getting it onto the target system(s) and providing it with sufficient privileges to do something that's hard. But millions of Ubuntu users regularly download and install software updates, with full root permission, every day. Assuming you replace a package popular enough to see its way through most of the users, the resulting botnet would rival even Conficker in terms of size. That sounds like an extremely lucrative target to me.

> (The only way I would think to defend against it would be to decline giving the password, thus cancelling the entire update, and wait to see if any "word" of a breach was broadcast.  I use to do this with Windoze updates, especially considering they were frequently buggy.  But doing this with Linux/Ubuntu seems like it would be overkill.  As I see it right now, the concern is minimal, but it seems like declining the password request is designed ONLY for this circumstance.  Not so?)

How would you know? How would anyone know? I could write software now to trigger a payload in, say, June. With proper patching of the system it would be virtually invisible.

The way software updates work now, I think the only thing you can do is trust Canonical to maintain the servers well.

---

### Post by snova on 2010-03-18
On further thought- I believe packages are cryptographically signed, so modifications would be difficult to introduce without triggering validation errors.

But in the "anything can happen vein"- *someone* has the key, and *someone* knows the password. It's possible, but there are few who could do it. Someone who knows more about how this system works should give input, though.

Edit: And apparently I didn't read the whole thread; both spiderbatdad and master5o1 pointed that out already. Oh well.

---

### Post by themarker0 on 2010-03-18
> **snova said:**
> Anything is possible. It would be the equivalent of hacking -snip-

The way software updates work now, I think the only thing you can do is **trust** Canonical to maintain the servers well.

Thats what it all comes down to. My dad doesn't trust anyone. He and his friend are doing self patches for a freebsd 4. Its weird/sad, that they won't update or anything. They just don't trust the updates.

---

### Post by swoll1980 on 2010-03-18
What if someone hacked into your email provider?. What if someone hacked into your ISP? What if someone hacked into Youtube? What if someone hacked into UF? What if someone hacked into the Pentagon? What if some one hacked into the communication satellites? What if someone hacked into a service that disables vehicles? Oh wait that happened today. The point here; is you could continue for the rest of your life asking these questions, and still be only half done. Crap happens, no use in worrying about it.

---

### Post by the yawner on 2010-03-18
I believe some other distro found a vulnerability in that one of their mirrors could be hijacked.

Edit:
Found an [article]("http://arstechnica.com/security/news/2008/08/red-hat-fedora-servers-infiltrated-by-attackers.ars"). It was Red Hat/Fedora.

---

### Post by srs5694 on 2010-03-18
> **BobJam said:**
> But what about if somebody hacked into the repository servers, and in fact you are downloading malware?

I suspect this is unlikely, but nevertheless possible . . . isn't it?

It's theoretically possible. My hunch is that it's more easily done than some here suggest, but that's based on my general attitude about such things, not on any inside knowledge of the security of the servers. Certainly phrases such as "practically impossible" don't apply here. There are security breaches at banks and government agencies that deal with highly sensitive data. I find it hard to believe that Canonical and its many mirror server operators have security that's so much better than that as to merit a judgment that they're "practically impossible" to break into.

Note that there are many servers for Ubuntu packages, most of them outside of Canonical's direct control. If you open up Synaptic, select Settings->Repositories, and then select "Other" in the "Download From" field, you'll see a list of repository mirrors you can use. Many of these are run by educational institutions and hosting companies. I can easily imagine some disgruntled employee or perhaps even a student surreptitiously planting some malware in one of these servers. Of course, malware planted in this way would affect only a tiny fraction of the Ubuntu installed base, since I imagine a lot of people never select a mirror in this way, and of those who do, only a small number will select any specific mirror.

Overall, I don't think it's worth getting too worried about this, but that's because damage in, say, a one-year period is *unlikely,* but not "practically impossible." Damage from less malicious sources, such as program bugs, is far more likely. I've had to clean up such damage myself several times within the past year.

> Considering the market share of Linux, that hacker would either have to be flat out stupid or extremely dedicated.  I expect if s/he spent the same amount of time doing a Windoze hack, s/he would get a bigger bang for their buck.

IMHO, this is the single biggest reason why there's so little malware for Linux.

> As I see it right now, the concern is minimal, but it seems like declining the password request is designed ONLY for this circumstance.  Not so?)

No, the password entry is required because package management is a system operation that requires superuser (root) privileges, and Ubuntu relies heavily on sudo and its GUI equivalents rather than a password-enabled root account for security. Thus, to perform superuser actions (install or remove packages, modify user accounts, reconfigure the boot loader, etc.), you must enter your user account password at some point or other. There are other ways to decline updates.

---

### Post by snova on 2010-03-18
> **srs5694 said:**
> Note that there are many servers for Ubuntu packages, most of them outside of Canonical's direct control. If you open up Synaptic, select Settings->Repositories, and then select "Other" in the "Download From" field, you'll see a list of repository mirrors you can use. Many of these are run by educational institutions and hosting companies. I can easily imagine some disgruntled employee or perhaps even a student surreptitiously planting some malware in one of these servers.

Granted I do not fully understand how the system works, but it is my impression that the mirrors do not change anything. Tampering with them would still invalidate the file signatures, which ultimately originate from the official repository. So they are not necessarily any more vulnerable.

The question is not just how to break into the servers; it's also how to make apt-get accept your packages as genuine.

On the other hand, if it is not an Ubuntu repository, I do not think there is much you can do.

---

