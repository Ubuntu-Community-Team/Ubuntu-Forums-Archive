---
title: "Slashdot post - Package Managers As Achilles Heel"
date: 2008-07-10
forum: Security
---

### Post by lemuriaX on 2008-07-10
Wondering if anyone else saw this Slashdot post yet. About University of Arizona researchers' study of package manager vulnerabilities...

[http://it.slashdot.org/it/08/07/10/227220.shtml](http://it.slashdot.org/it/08/07/10/227220.shtml)

---

### Post by Dr Small on 2008-07-10
Who doesn't read Slashdot? ;)

---

### Post by lemuriaX on 2008-07-10
Yeah, /. rules :)
So any thoughts on that other than their suggestions?

---

### Post by kevdog on 2008-07-11
What's slashdot? :confused:




Ok, before you actually respond, it was a joke!

---

### Post by lemuriaX on 2008-07-11
ok - I thought it would be interesting to hear what people thought about the security issues discussed in that article. Anyone?

---

### Post by lemuriaX on 2008-07-11
Hmm...well, ok.

For some reason I thought that an article that started off saying stuff like:

"Given their critical role, the expectation would be for package managers to be extremely secure. We examined ten popular package managers (APT, YUM, YaST, etc.) for Linux and BSD systems and found vulnerabilities in all of them. The attacks discussed here can give attackers the ability to read or erase any file on your computer, capture passwords, set up a backdoor into your system, etc. without needing to compromise any keys or passwords."

might be of interest to discuss in the security forum.

But - maybe not.

---

### Post by simonapnic on 2008-07-11
DNS Poisoning anyone ?
Just imagine an attacker spoofing your DNS record for the repository you're using and its mirrors.
He can probably give you anything he wants.

---

### Post by Jesdisciple on 2008-07-11
I was going to ask if anything could be done about it, but then I read CERT's synopsis.

Is there anything the maintainters of package managers can do?

---

### Post by kevmitch on 2008-07-11
Can someone clear up how/when/if apt authenticates packages and/or metadata?

---

### Post by eldragon on 2008-07-11
> **simonapnic said:**
> DNS Poisoning anyone ?
Just imagine an attacker spoofing your DNS record for the repository you're using and its mirrors.
He can probably give you anything he wants.

nope, not anything he wants, just signed packages.

the vulnerability relies on freezing packages that are known to be buggy. i think its quite a long shot if you ask me. quite doable, but how long till it gets found. seems like too much work right now.

---

### Post by Jesdisciple on 2008-07-11
> **kevmitch said:**
> Can someone clear up how/when/if apt authenticates packages and/or metadata?I gather that all 10 of the tested package managers authenticate packages; that's why the attacker can only send signed packages.

---

### Post by lemuriaX on 2008-07-11
Thanks for the input. Yes, I think the main vulnerability they are discussing involves someone with ill intent having an official mirror and then purposefully serving signed but outdated packages that have a known vulnerability, which they could then use to hijack your system. I'm not really that knowledgable about all this though, so that's why I thought it would be interesting to see what people here had to say about it. Hopefully it is as eldragon said, a long shot.

---

### Post by hyper_ch on 2008-07-12
basically you have to
(1) become an official mirror
(2) freeze a package with a known security flaw
(3) try to get into that machine

---

### Post by Jesdisciple on 2008-07-12
The vulnerability relies on the package manager's gullibility to go ahead and download a package with a low version number.  Do the package contents specify the software's version (near the beginning)?  If so, the user could tell the package manager the current version (as seen on the official site) and the manager could then refuse to complete a download which was marked with a low version.

Objections?  Elaborations?

---

### Post by kwilliam on 2008-07-12
I've got a practical question. Why can't I get SSL to work with APT? I installed apt-transport-https, which according to the 
[package's page]("http://packages.ubuntu.com/hardy/apt-transport-https"):

[INDENT]This package contains a APT https transport. It makes it possible to use 'deb [https://foo](https://foo) distro main' lines in the sources.list.[/INDENT]

I changed a few of my sources in /etc/apt/sources.list file to use https instead of http. But now when I try to run sudo apt-get update, I get the following output:
```

Ign https://security.ubuntu.com hardy-security Release.gpg
Get:1 http://security.ubuntu.com hardy-security Release.gpg [189B]
Hit http://archive.ubuntu.com hardy Release.gpg
Ign http://archive.ubuntu.com hardy/main Translation-en_US
Ign https://security.ubuntu.com hardy-security/main Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy/universe Translation-en_US
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy-updates Release.gpg
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign https://security.ubuntu.com hardy-security/restricted Translation-en_US
Hit http://archive.ubuntu.com hardy-backports Release.gpg
Ign http://archive.ubuntu.com hardy-backports/main Translation-en_US
Ign http://archive.ubuntu.com hardy-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy-backports/universe Translation-en_US
Hit http://security.ubuntu.com hardy-security/main Sources
Ign https://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://archive.ubuntu.com hardy-backports/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy-proposed Release.gpg
Ign http://archive.ubuntu.com hardy-proposed/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy-proposed/main Translation-en_US
Ign http://archive.ubuntu.com hardy-proposed/multiverse Translation-en_US
Ign http://archive.ubuntu.com hardy-proposed/universe Translation-en_US
Hit http://archive.ubuntu.com hardy Release
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Ign https://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy-updates Release
Hit http://archive.ubuntu.com hardy-backports Release
Ign https://security.ubuntu.com hardy-security Release
Hit http://archive.ubuntu.com hardy-proposed Release
Hit http://archive.ubuntu.com hardy/main Packages
Hit http://archive.ubuntu.com hardy/restricted Packages
Hit http://archive.ubuntu.com hardy/main Sources
Hit http://archive.ubuntu.com hardy/restricted Sources
Ign https://packages.medibuntu.org hardy Release.gpg
Ign https://security.ubuntu.com hardy-security/main Packages
Hit http://archive.ubuntu.com hardy/universe Packages
Hit http://archive.ubuntu.com hardy/universe Sources
Hit http://archive.ubuntu.com hardy/multiverse Packages
Hit http://archive.ubuntu.com hardy/multiverse Sources
Hit http://archive.ubuntu.com hardy-updates/main Packages
Hit http://archive.ubuntu.com hardy-updates/restricted Packages
Hit http://archive.ubuntu.com hardy-updates/universe Packages
Ign https://security.ubuntu.com hardy-security/restricted Packages
Hit http://archive.ubuntu.com hardy-updates/main Sources
Hit http://archive.ubuntu.com hardy-updates/restricted Sources
Hit http://archive.ubuntu.com hardy-backports/main Packages
Hit http://archive.ubuntu.com hardy-backports/restricted Packages
Hit http://archive.ubuntu.com hardy-backports/universe Packages
Hit http://archive.ubuntu.com hardy-backports/multiverse Packages
Hit http://archive.ubuntu.com hardy-backports/main Sources
Hit http://archive.ubuntu.com hardy-backports/restricted Sources
Hit http://archive.ubuntu.com hardy-backports/universe Sources
Ign https://security.ubuntu.com hardy-security/universe Packages
Hit http://archive.ubuntu.com hardy-backports/multiverse Sources
Hit http://archive.ubuntu.com hardy-proposed/restricted Packages
Ign https://security.ubuntu.com hardy-security/multiverse Packages
Hit http://archive.ubuntu.com hardy-proposed/main Packages
Hit http://archive.ubuntu.com hardy-proposed/multiverse Packages
Hit http://archive.ubuntu.com hardy-proposed/universe Packages
Err https://security.ubuntu.com hardy-security/main Packages
  couldn't connect to host
Err https://security.ubuntu.com hardy-security/restricted Packages
  couldn't connect to host
Err https://security.ubuntu.com hardy-security/universe Packages
  couldn't connect to host
Err https://security.ubuntu.com hardy-security/multiverse Packages
  couldn't connect to host
Ign https://packages.medibuntu.org hardy/free Translation-en_US
Ign https://packages.medibuntu.org hardy/non-free Translation-en_US
Ign https://packages.medibuntu.org hardy Release
Ign https://packages.medibuntu.org hardy/free Packages
Ign https://packages.medibuntu.org hardy/non-free Packages
Err https://packages.medibuntu.org hardy/free Packages
  SSL: certificate subject name (*.dunnewind.net) does not match target host name 'packages.medibuntu.org'
Err https://packages.medibuntu.org hardy/non-free Packages
  SSL: certificate subject name (*.dunnewind.net) does not match target host name 'packages.medibuntu.org'

```

Do the main Ubuntu servers not support SSL connections? If so, that's outrageous. If not, what do I need to change?

---

### Post by hyper_ch on 2008-07-12
why should they support ssl?

---

### Post by Jesdisciple on 2008-07-12
Er, hyper, isn't that obvious?  Shouldn't a server be capable of HTTPS?

---

### Post by hyper_ch on 2008-07-12
why?

---

### Post by kevmitch on 2008-07-12
> **hyper_ch said:**
> why?

So that you know that the server is who it says it is. Https offers both encryption and most importantly authentication.

Here's a thought: maybe you need to install the certificate for [https://security.ubuntu.com](https://security.ubuntu.com). Not sure exactly how you'd go about that though.

---

### Post by kevmitch on 2008-07-12
It also looks like there's a problem with the certificate for packages.medibuntu.org. It says that the expected host name is *.dunnewind.net. But this needs to be packages.medibuntu.org in order to work. You might try using a dunnewind.net address directly in your sources.list to get around that one.

---

### Post by kwilliam on 2008-07-12
> **kevmitch said:**
> Here's a thought: maybe you need to install the certificate for [https://security.ubuntu.com](https://security.ubuntu.com). Not sure exactly how you'd go about that though.
Hmm, that's a good point. But [https://security.ubuntu.com](https://security.ubuntu.com) isn't even a valid website, so I have no idea how one could get it's certificate. :-(

> **hyper_ch said:**
> why?
To prevent man-in-the-middle attacks, according to the article.

---

### Post by hyper_ch on 2008-07-13
> **kevmitch said:**
> So that you know that the server is who it says it is.
Correct me if I'm wrong but in this article they managed to become an official mirror... so it is the servre how it says it is... so how would SSL help here?

> **kevmitch said:**
> Https offers both encryption and most importantly authentication.
How would that help with the packages? They are digitally signed? This described attack just doesn't upgrade older, signed packages with a security leack that then can be exploited... I still don't see how SSL will help here...

> **kwilliam said:**
> To prevent man-in-the-middle attacks, according to the article.
Where is there a man-in-the-middle attack?

---

### Post by kwilliam on 2008-07-13
SSL doesn't help at all against the main attack discussed in the article, which involves becoming an official mirror and using the knowledge of what packages are installed on your computer to attack when security holes are found in one of those packages. However, if you actually read the page, under "**Protecting Yourself: Things You Can Do Today**", it says:

[LIST]
[*]Use HTTPS for mirror communication. Unfortunately, this is generally only available with paid support services (and only protects you against man-in-the-middle attacks, not malicious mirrors). However, by running a distribution with HTTPS support on their mirrors, a man-in-the-middle attacker cannot easily launch an attack as though it were a mirror.
[/LIST]

**Without SSL, an even worse attack could be done.** While your package manager is talking to the repository, a third party could jump in between, claim it is the repository, and send you malicious packages. Thus, *even if you were using a repository you trust* (like the main security.ubuntu.com repository) a man-in-the-middle attack would leave you in the same trouble.

Obviously, a DNS spoofing attack could do the same thing, but might be harder to pull off. But the whole Internet is vulnerable to DNS spoofing, so they'll probably come up with a fix for DNS spoofing. In contrast, a fix already exists for man-in-the-middle spoofing: using HTTPS.

---

### Post by hyper_ch on 2008-07-13
still, how would a man-in-the-middle attack work if the packages are all signed? He can only give you a signed older package... but then he would do the same as the poisonous official mirror...

---

### Post by Jesdisciple on 2008-07-13
AFAIK, the very act of checking a signature is part of SSL, although not necessarily HTTPS.

---

### Post by lemuriaX on 2008-07-14
Found a couple other discussions about this that are interesting...

at Linuxquestions.org: 
[http://www.linuxquestions.org/questions/linux-security-4/attacks-on-package-managers-654969/](http://www.linuxquestions.org/questions/linux-security-4/attacks-on-package-managers-654969/)

at Debian forums:
[http://forums.debian.net/viewtopic.php?t=28668&sid=2c9e681a48278b0a8f459da06d99967f](http://forums.debian.net/viewtopic.php?t=28668&sid=2c9e681a48278b0a8f459da06d99967f)

---

### Post by kwilliam on 2008-07-14
Well, if anyone figures out how to use apt-transport-https, let me know. In the mean time, I've given up and removed the "s"s from my "http"s, because the worst the attack can do is keep me from getting security updates*, and I'm doing that to myself by waiting for an explanation of why HTTPS isn't working.

(*Note that technically, the attack does more than this, because it gives the attacker the IP addresses of vulnerable computers than can then be exploited immediately, whereas if I merely stop upgrading packages, the attacker would have to sweep the whole Internet to find my computer, but whatever.**)

** Who can really be concerned about this when DNS poisoning would be infinately worse, yet remarkably has rarely ever been done, despite it being possible for many many years?

---

