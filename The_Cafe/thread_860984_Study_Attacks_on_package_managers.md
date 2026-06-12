---
title: "Study: Attacks on package managers"
date: 2008-07-16
forum: The Cafe
---

### Post by newbie2 on 2008-07-16
> The University of Arizona is publishing a study on security problems with package management systems. The core problem would appear to be that tools like yum and apt will happily install versions of packages with known vulnerabilities if they think that's the most recent version available. And feeding such packages to the package managers is not a big challenge: "To give an example of how easy it is for a malicious party to obtain a mirror, we ran an experiment where we created a fake administrator and company name and leased a server from a hosting provider. We were able to get our mirror listed on every distribution we tried (Ubuntu, Fedora, OpenSuSE, CentOS, and Debian) and our mirrors were contacted by thousands of clients, even including military and government computers!"
[http://lwn.net/Articles/289883/](http://lwn.net/Articles/289883/)
:rolleyes:

---

### Post by Tomatz on 2008-07-16
WTH???

Why Why Why?

In windows you can install software with security vulnerabilities whenever and however you want. Package management using repos from trusted sources is far more secure.

The mind boggles :confused:

---

### Post by LookTJ on 2008-07-16
Umm.. where is the example and proof, I don't see no video or pictures of this example. 

Until then, I call this "fud"

---

### Post by beniwtv on 2008-07-16
Umm... Aren't the individual packages PGP signed by the devs GPG key?

I don't think a bad mirror could sign bad packages with someone else's key? Hmm.... 

I don't really have a clue, but if someone has, mind explaining how it works? In my understanding, the GPG signing was introduced right because of this?

:confused:

---

### Post by newbie2 on 2008-07-16
here are some lxer comments :
[http://lxer.com/module/forums/t/27519/](http://lxer.com/module/forums/t/27519/)

---

### Post by fiddledd on 2008-07-16
I wonder who funded the experiment, perhaps it was M...
No, I'm not going to type it, that would be silly. :)

---

### Post by mcduck on 2008-07-16
I understood that the idea was to serve old (vulnerable) versions of packages, so they would be correctly signed.. But the problem then is that the package manager doesn't downgrade packages, or replace existing packages with the same version..

Sounds kind of like the same stuff as all the Linux viruses that, in the end, can't spread or do any harm unless you help them by hand..

They might have a point, but it's doesn't seem to be even closely as serious as they suggest.

---

### Post by beniwtv on 2008-07-16
> **mcduck said:**
> I understood that the idea was to serve old (vulnerable) versions of packages, so they would be correctly signed.. But the problem then is that the package manager doesn't downgrade packages, or replace existing packages with the same version..


Assuming I have a properly signed old package with a version of BIND which has a known vulnerability, and I put it on my mirror. Now, apt will not downgrade to older versions, AFAIK. 

So, I would need to modify my package to be a higher version than the one the target users have already installed, or I need to modify my apt configuration to prefer this package over all others.

The second case would need social engineering, so it's a no-go for an automated attack. The first case would require to modify the contents of the package (changing the file name is not enough), which would render invalid the signature of the package, wouldn't it?

So I'm with mcduck on this, sounds more like a social engineering attack than anything else.

Cheers,

---

### Post by Tomatz on 2008-07-16
> **beniwtv said:**
> Assuming I have a properly signed old package with a version of BIND which has a known vulnerability, and I put it on my mirror. Now, apt will not downgrade to older versions, AFAIK. 

So, I would need to modify my package to be a higher version than the one the target users have already installed, or I need to modify my apt configuration to prefer this package over all others.

The second case would need social engineering, so it's a no-go for an automated attack. The first case would require to modify the contents of the package (changing the file name is not enough), which would render invalid de signature of the package, wouldn't it?

So I'm with mcduck on this, sounds more like a social engineering attack than anything else.

Cheers,

Yeah its pointless. Anyone could create a .deb of an app that used admin privilages, say "start up manager". Then just create a script in the .deb that when installed and ran with gksu from the menu launched SUM and a nasty command begining with rm.

There is not much you can do about it but saying that the linux model is far more secure that other platforms.

---

### Post by wrtpeeps on 2008-07-16
> **Tomatz said:**
> WTH???

Why Why Why?

In windows you can install software with security vulnerabilities whenever and however you want. Package management using repos from trusted sources is far more secure.

The mind boggles :confused:

Why are you bringing windows into this. This has nothing to do with windows. :rolleyes:

---

### Post by ukripper on 2008-07-16
Not very convincing experiment and without detailed report. Therefore, no comments.

---

### Post by Polygon on 2008-07-16
yeah, would like to see more details about this...

how exactly do these attackers get ahold of the ubuntu gpg signing key?

---

### Post by YaroMan86 on 2008-07-16
Mmmm. no. In a way, I believe it CAN be an insecure delivery vector.

However, I don't believe that it IS.

As a programmer, I can usually tell the behavior of specific programs. And I do believe that updates are always pushed in the APT system based off of two things.

1. There's now an existing package whose version is higher.

2. There's now an existing package with a different name than the installed package.

I've observed this behavior both with the official repositories provided by Canonical and from what happens when the Medibuntu repository is installed.

HOWEVER, I doubt viruses will propagate much under a packaging system for a few major reasons.

1. Just about every site I've seen that even bothers to provide a repository provides a form of validation for APT.

2. Just about every site I've seen providing a repository is somewhat major and well-reputed. Places like Medibuntu, winehq, and, of course, Canonical.

3. Repositories tend to be massive things. They have to be run through some sort of HTTP daemon, can provide several package lists, and don't forget the sheer size taken by all the packages. A fellow Ubuntu user and a good friend tells me that the official Ubuntu repository totals to about 200 GiB.

4. Even if the repository was a single package, the idea of a cracker setting up an entire repository just for the sake of propagating a virus seems like a little too much work compared to other, more successful, vectors.

5. There's also the consideration of how ineffective Linux viruses are in the first place. The security model of Linux basically makes it so that the virus has to essentially be chmodded up and hand executed, and even then can only do limited damage, the virus is only likely to take out things in the users home directory, if at all. If the user is smart, then regular backups would be an effective way at snubbing a Linuc virus. And if you're stupid enough to be root all the time, then, sorry, but I think you deserve all the damage the virus gives you, since YOU are the security problem in that case.

5. There's the speed at which security fixes tend to arrive downstream for Linux. The Teardrop vulnerability, once discovered, was fixed in less than 24 hours for Linux, whereas the alternatives took anywhere from a few weeks to a few MONTHs to address the problem. Crackers would write a virus exploiting a security flaw in Linux, only to learn that Linux has already fixed the security flaws and most distros applied the fix.

6. Finally, there's obscurity. Linux is not very common, yet. We're anywhere from 10 to 20 million users. Compared to Windows, we're not even a blip on a cracker's radar. I have read from numerous sources, /. included, that there are only 30 known in-the-wild viruses for Linux. Contrastly, I have also read from the same sources that there are over 50,000 known in-the-wild viruses for Windows. Frankly, Linux, considering its obscurity.

I'm not sure this is as far as FUD. All I see is that this says it COULD, but my personal opinion is that it WON'T or will be an exceptionally rare case.

---

### Post by chucky chuckaluck on 2008-07-16
sounds like someone needs a hobby.

---

### Post by AnLGP on 2008-07-16
sounds like someone has a hobby and is pretty good at reasoning to boot.  I think your reasoning may stand ground and like you said sudo is there for a reason.  That might not save us every time but it's there for good reason.

---

### Post by FuturePilot on 2008-07-16
I don't think this has anything to do with package managers. This has more to do with social engineering. Regardless of the OS you can trick people into installing malicious software. That doesn't seem like a flaw in the package manager. It's called making sure the software **you**, not the **package manager**, install is trustworthy. That includes adding apt sources. That's why you should be careful of what third party repos you add to your system.

---

### Post by YaroMan86 on 2008-07-16
> **FuturePilot said:**
> I don't think this has anything to do with package managers. This has more to do with social engineering. Regardless of the OS you can trick people into installing malicious software. That doesn't seem like a flaw in the package manager. It's called making sure the software **you**, not the **package manager**, install is trustworthy. That includes adding apt sources. That's why you should be careful of what third party repos you add to your system.

Indeed.

But, as I said, there's easier ways to use SO on a user than having to set up a repository.

---

### Post by Tomatz on 2008-07-16
> **chucky chuckaluck said:**
> sounds like someone needs a hobby.

Listen to the guy! He has a beard...

:lolflag:

---

### Post by phrostbyte on 2008-07-16
This isn't about 3rd party repos. This about offical mirrors of the main Ubuntu repository. 

If you add a 3rd party repo you are at the will of the person who made it. Ubuntu repo is peer reviewed and mirrors are suppose to mirror the Ubuntu repo exactly. Mirrors basically clone the main Ubuntu repo, and they are thus much more trusted by users and Ubuntu itself. What this article is saying is it is possible to make a Ubuntu repo which doesn't actually mirror the main Ubuntu repo.

It's a serious security risk.

---

### Post by Tomatz on 2008-07-16
> **phrostbyte said:**
> This isn't about 3rd party repos. This about offical mirrors of the main Ubuntu repository. 

If you add a 3rd party repo you are at the will of the person who made it. Ubuntu repo is peer reviewed and mirrors are suppose to mirror the Ubuntu repo exactly. Mirrors basically clone the main Ubuntu repo, and they are thus much more trusted by users and Ubuntu itself. What this article is saying is it is possible to make a Ubuntu repo which doesn't actually mirror the main Ubuntu repo.

It's a serious security risk.

Wouldn't you need to switch to that mirror to download from it?

---

### Post by phrostbyte on 2008-07-16
> **Tomatz said:**
> Wouldn't you need to switch to that mirror to download from it?

Sure. But many people use the mirrors (they are usually much faster) and Ubuntu pretty much encourages using them, which is not really a bad thing either. But a mirror should be a mirror, it should mirror the contents of the main Ubuntu repo. That there is no accountable mechanism is troubling. I will continue to use mirrors, because the mirrors I use are from reputable organizations, but I think this can be considered a problem.

---

### Post by Tomatz on 2008-07-16
> **phrostbyte said:**
> Sure. But many people use the mirrors (they are usually much faster) and Ubuntu pretty much encourages using them, which is not really a bad thing either. But a mirror should be a mirror, it should mirror the contents of the main Ubuntu repo.

Hmmm maybe a list of verified safe mirrors should be put up on the forums. I always use the main us mirror anyway as the uk one is slow so i'm not really worried by this.

---

### Post by phrostbyte on 2008-07-16
> **Tomatz said:**
> Hmmm maybe a list of verified safe mirrors should be put up on the forums. I always use the main us mirror anyway as the uk one is slow so i'm not really worried by this.

I use GATech because I regularly get 2-3 MB/sec downloads.

To add: This vulnerability does not mean they get put viruses or rogue pacakges and crap into a mirror. Apt will not install packages which are not signed, and even the slightest modification of packages will cause them to become unsigned. But packages which are already signed but contain security problems can be inserted in. Not as bad a viruses but it can still be a problem.

---

### Post by Tomatz on 2008-07-16
> **phrostbyte said:**
> I use GATech because I regularly get 2-3 MB/sec downloads.

I only have 2Mb-sec max download speed from my isp and us-main always max's that out :)

---

### Post by Tomatz on 2008-07-16
> **phrostbyte said:**
> 
To add: This vulnerability does not mean they get put viruses or rogue pacakges and crap into a mirror. Apt will not install packages which are not signed, and even the slightest modification of packages will cause them to become unsigned. But packages which are already signed but contain security problems can be inserted in. Not as bad a viruses but it can still be a problem.


Yeah i know. It wouldnt be hard to stick an **rm -rf** or worse in some package though. There are many that you quite normally run as root and dont even give it two thoughts :(

---

### Post by phrostbyte on 2008-07-16
> **Tomatz said:**
> Yeah i know. It wouldnt be hard to stick an **rm -rf** or worse in some package though. There are many that you quite normally run as root and dont even give it two thoughts :(

If you stick in an offical Ubuntu package, it would become unsigned and thus it wouldn't install. Signing uses a hash of the file and then encrypts the hash using a private key, the technology is pretty much foolproof, there is no realistic way around it.

The only problem is not everything that is an Ubuntu package is secure, but a mirror could serve any Ubuntu package, even outdated ones with known security flaws.

---

### Post by madjr on 2008-07-16
> **Tomatz said:**
> Yeah its pointless. **Anyone could create a .deb of an app that used [COLOR="Red"]admin privilages[/COLOR]**, say "start up manager". Then just create a script in the .deb that when installed and ran with gksu from the menu launched SUM and a nasty command begining with rm.

There is not much you can do about it but saying that the linux model is far more secure that other platforms.
[B]
admin privilages[/B] is one of the [problems of **apt**]("http://0install.net/matrix.html")

---

### Post by FyreBrand on 2008-07-16
> **phrostbyte said:**
> If you stick in an offical Ubuntu package, it would become unsigned and thus it wouldn't install. Signing uses a hash of the file and then encrypts the hash using a private key, the technology is pretty much foolproof, there is no realistic way around it.

The only problem is not everything that is an Ubuntu package is secure, but a mirror could serve any Ubuntu package, even outdated ones with known security flaws.Right.  The malware wouldn't be installed via the package.  An older "exploitable" package could be installed by the malicious repo and then **that **vulnerability exploited.  It still seems like a difficult and fragile attack route, but the concept is there.

---

### Post by YaroMan86 on 2008-07-16
> **phrostbyte said:**
> This isn't about 3rd party repos. This about offical mirrors of the main Ubuntu repository. 

If you add a 3rd party repo you are at the will of the person who made it. Ubuntu repo is peer reviewed and mirrors are suppose to mirror the Ubuntu repo exactly. Mirrors basically clone the main Ubuntu repo, and they are thus much more trusted by users and Ubuntu itself. What this article is saying is it is possible to make a Ubuntu repo which doesn't actually mirror the main Ubuntu repo.

It's a serious security risk.

Somehow, I think it would be a little more difficult for a cracker to convince the maintainer of a mirror of the official repositories. Those are typically professionally monitored. I doubt a virus would make it in the repo that way unless those responsible for the mirror are lazy.

---

### Post by cardinals_fan on 2008-07-16
> **madjr said:**
> [B]
admin privileges[/B] is one of the [problems of **apt**]("http://0install.net/matrix.html")
Eh?  I think you misunderstood what he was saying.  The app would require root privileges AFTER installation.  The system used to install it is irrelevant.

---

### Post by Tomatz on 2008-07-16
Autopackage is good also :)

---

### Post by madjr on 2008-07-16
> **cardinals_fan said:**
> 
>  Originally Posted by **madjr**

**admin privileges** is one of the [problems of apt]("http://0install.net/matrix.html")

Eh?  I think you misunderstood what he was saying.  The app would require root privileges AFTER installation.  The system used to install it is irrelevant.

thats exactly the problem with APT.

why would i need to type in my password just to install a simple app  like *screenlets* from getdeb ?

why can't i just install it as **user**? maybe one of the screenlets has some **malware** on it... should it go into my system folders?

but **it did** ask me for my password, because indeed it's getting installed in the **system folders**.

on the other hand by this comparison (check ***"Non-root install of system"***):

[http://0install.net/matrix.html](http://0install.net/matrix.html)

only APT (and similar) installs every package in the system folders.

*Autopackage, Klik, Java WS, Zero Install, etc.* let me install it as **user**, so if my user gets "F****d" i only need to delete it and create a new one.

Can Apt be made more secure ? Yes, but only if the devs *care* to improve it or become aware of the design flaws.

software needs to evolve to face new incoming problems

---

### Post by cardinals_fan on 2008-07-16
> **madjr said:**
> thats exactly the problem with APT.

why would i need to type in my password just to install a simple app  like *screenlets* from getdeb ?

why can't i just install it as **user**? maybe one of the screenlets has some **malware** on it... should it go into my system folders?

but **it did** ask me for my password, because indeed it's getting installed in the **system folders**.

on the other hand by this comparison (check ***"Non-root install of system"***):

[http://0install.net/matrix.html](http://0install.net/matrix.html)

only APT (and similar) installs every package in the system folders.

*Autopackage, Klik, Java WS, Zero Install, etc.* let me install it as **user**, so if my user gets "F****d" i only need to delete it and create a new one.

Can Apt be made more secure ? Yes, but only if the devs *care* to improve it or become aware of the design flaws.

software needs to evolve to face new incoming problems
I agree, it just doesn't apply to the point made above.

---

