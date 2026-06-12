---
title: "About trust"
date: 2011-07-20
forum: Security
---

### Post by Bardobrave on 2011-07-20
Hi all.

I'm fine tuning my 11.04 ubuntu on a new machine and I'm starting to wonder seriously about security (my girlfriend's windows system had a serious intrusion a couple of days ago and I feel a bit worried).

When I search the web for information about new apps, system tuning, etc... I see usually that blogs and community pages makes references to scripts, apps and packages without any concern about it's security. However, I come to think, who can assure that they are secure? When can I install a package (out of official repositories) and be reasonably sure that it doesn't contains malicious code?

Can you only trust official repositories?
Can you trust something when it's referenced on official ubuntu community pages?
Can you trust something when it's referenced on blogs with a certain degree of impact on the community?
Can you trust something when hundreds of users seems to use it without problems, although no one of them seems to have checked it?

There is any guideline to follow on this matter?

---

### Post by dasan on 2011-07-20
I think you should install from official and your trusted sources only..
for small script and command you can see man pages and check it in all the way.

---

### Post by Bardobrave on 2011-07-20
Yeah.... is "your trusted sources" what makes me wonder, when a source can be trusted?, what exactly mean these brief three words?

---

### Post by Grenage on 2011-07-20
While I could answer those questions individually, it can probably be summed up in a paragraph.

There is a degree of trust with any software you did not write, and that level will vary depending on the source.  High-traffic areas such as the official repositories are generally regarded to be quite trustworthy, but you can *never* be 100% sure.  Low traffic areas such as unknown websites with obscure scripts are less trustworthy.

Common sense and personal judgement on a case by case basis is the way to go.

---

### Post by Bardobrave on 2011-07-20
> **Grenage said:**
> Common sense and personal judgement on a case by case basis is the way to go.

Well... I can easily understand this, but don't make me feel better.

I will give you the real example that started my questioning:

I usually use PS3 Media Server on my machines to stream multimedia content to my PS3.

[http://www.ps3mediaserver.org](http://www.ps3mediaserver.org)

This is a project developed by some people with a life span of several years and I am totally trust about it. However, usually it's a pain to install it because of it's dependency of other packages.

Recently I found on their official forums a .deb package developed by one user that allows to automatically install it and all it's dependencies with a single click.

And here were born my suspicions. Many people seems to have used the package without problems... but, what prevents it's creator to have included into the package it's own exploit and await the proper moment to make an attack?

I found the app, and the install package itself, referenced on the community wiki:

[https://help.ubuntu.com/community/Ps3MediaServer](https://help.ubuntu.com/community/Ps3MediaServer)

Now, this is a source I trust the most. So all things are saying to me, "it's ok, you can use it" but don't feel totally comfortable about it... maybe I'm quite paranoid these days.

---

### Post by Grenage on 2011-07-20
> **Bardobrave said:**
> what prevents it's creator to have included into the package it's own exploit and await the proper moment to make an attack.

Nothing.  If it's a popular deb then the chances are higher that someone has inspected it, but they may not have; a bit of paranoia is good, but don't let it ruin your life.

For example, there was recently a deb on Gnome-Look which would wreck a machine it was used with.

---

### Post by Soul-Sing on 2011-07-20
> Can you only trust official repositories?

yes the off. Ubuntu software sources can be trusted==> 100%
we have to, because otherwise we have nothing trustful in our hands. Sometimes we have to rely on the work of others.
The alternative is to build to your own distro.....:D

---

### Post by Bardobrave on 2011-07-20
Well... the reliability of ubuntu repositories is out of discussion. What I am asking for is for any rule of thumb to keep in mind when having to "rely on the work of others".

I know it's mainly a matter of logic and awareness, but I supose that should be some "practical guidances" further than "follow your guts"

---

### Post by Grenage on 2011-07-20
I have two PCs at home; my desktop and my laptop.  My laptop doesn't really contain any sensitive information, so I am quite liberal with installing software.  I don't check the code because I am not competent enough to do so.  My Laptop is used for internet banking and other such affairs, so I am very careful about what I install.

If the application source is unknown to you and there isn't an obvious user-base, be sceptical and cautious; otherwise, you're going to be ok most of the time.

---

### Post by stevennlv on 2011-07-20
I think your concerns are perfectly logical. But I'm not sure I have a good answer for you. I just created an Ubuntu VM to surf the web because even with almost 30 years of user experience I could not secure a new install of win7.

I found an article on line a while back saying that in the not too distant past someone had managed to insert trojans in to the MS update servers. 

Personally, and no offense meant to all the folks who work so hard to write all of this cool software, I don't think you can really trust anybody any more.

Even if the guys that write this stuff are straight as an arrow I'm sure some bad guy would love to break in to the repositories and fill it full of all kinds of bad payloads.

I guess the only practical answer (if you're not spiffy enough to write you own operating system that is) is to get some knowledge and some tools and run some extensive diagnostics on your system then back up to non-rewritable media; like file locked DVD's. Then, WHEN, not if your system gets FUBARed you have a clean base state to restore from.

---

### Post by bodhi.zazen on 2011-07-20
> **Bardobrave said:**
> Hi all.

I'm fine tuning my 11.04 ubuntu on a new machine and I'm starting to wonder seriously about security (my girlfriend's windows system had a serious intrusion a couple of days ago and I feel a bit worried).

When I search the web for information about new apps, system tuning, etc... I see usually that blogs and community pages makes references to scripts, apps and packages without any concern about it's security. However, I come to think, who can assure that they are secure? When can I install a package (out of official repositories) and be reasonably sure that it doesn't contains malicious code?

Can you only trust official repositories?
Can you trust something when it's referenced on official ubuntu community pages?
Can you trust something when it's referenced on blogs with a certain degree of impact on the community?
Can you trust something when hundreds of users seems to use it without problems, although no one of them seems to have checked it?

There is any guideline to follow on this matter?

You will need to decide either to:

1. Trust the repos.

2. Review the source code yourself and start running pen testing until you are happy with #1

---

### Post by stlsaint on 2011-07-20
I suggest if you are going to install apps that are not in the trusted repos than a very simple way to test them is to install them in a virtual machine first. Also you can always take a gander at the source code you are installing!! :popcorn:

---

### Post by walt.smith1960 on 2011-07-20
I have 2 or more Linux installs on one drive.  I use a boot manager where I don't believe they can see one another.  One has only software from the repository. I use that install for activities that could involve the potential for identity theft, fraud etc.  The second install is used for casual web browsing, unknown .deb packages etc. I don't know if that idea is perfect but I can sleep at night using it.

---

### Post by Dangertux on 2011-07-20
You know what the best part of open source software is?

Its source code is open and you can view/audit it at will. It's hard not to trust something when there is nothing to hide.

---

### Post by bodhi.zazen on 2011-07-20
> **walt.smith1960 said:**
> I have 2 or more Linux installs on one drive.  I use a boot manager where I don't believe they can see one another.  One has only software from the repository. I use that install for activities that could involve the potential for identity theft, fraud etc.  The second install is used for casual web browsing, unknown .deb packages etc. I don't know if that idea is perfect but I can sleep at night using it.

That works. My guess is most people simply use virtualbox.

Fedora offers a few fine options, including an xguest account as well as "sandbox". both use selinux to confine your activities.

[http://www.bress.net/blog/archives/195-Firefox-in-a-sandbox-with-Fedora.html](http://www.bress.net/blog/archives/195-Firefox-in-a-sandbox-with-Fedora.html)

Running firefox (or personally I use midori) in a selinux sandbox is tighter then a ... er ... dual booting or a VM (without additional hardening of the guest or second os).

---

### Post by Bardobrave on 2011-07-21
> **stlsaint said:**
> I suggest if you are going to install apps that are not in the trusted repos than a very simple way to test them is to install them in a virtual machine first. Also you can always take a gander at the source code you are installing!! :popcorn:

Now this make perfectly sense, I should have thought it before :rolleyes:

---

### Post by Bardobrave on 2011-07-21
> **Dangertux said:**
> You know what the best part of open source software is?

Its source code is open and you can view/audit it at will. It's hard not to trust something when there is nothing to hide.

Totally agree, sadly I lack the time and the knowledge to check it in most of the cases.

This is why I would like to know when someone has done it before. There isn't some type of "secure list"? (rather than official repositories, wich I think is actually what they are :p now I'm starting to think by myself... great...)

---

### Post by tgm4883 on 2011-07-21
> **Bardobrave said:**
> Totally agree, sadly I lack the time and the knowledge to check it in most of the cases.

This is why I would like to know when someone has done it before. There isn't some type of "secure list"? (rather than official repositories, wich I think is actually what they are :p now I'm starting to think by myself... great...)

Nope, no secure list. IMO trust is never 100%, it's just a probability. The more people using a PPA and not reporting issues means it is more probable that it is safe. If you trust the writers of the software, see if they have a PPA available. Trusting online is very similar to real life. How do you know what friends you can trust?

---

### Post by sneakyimp on 2011-07-21
Bardobrave, I approve of your question and your perseverance in seeking an answer.  I had a server hacked recently.  The ssh daemon was compromised and even contained some pretty ASCII art saying "YOU BEEN PWNED LOL".  This really pissed me off and I've since been learning a lot about ubuntu security.

If you are expecting a simple answer, then you are out of luck.  There is no simple answer.  On the other hand, the answers you and I have been getting have been very disappointing to me. 

The basic idea is that Ubuntu is FREE software, some of which is written by some paid folks at Red Hat, Canonical, Microsoft, Google, etc.  Other code is written by god-knows-who from god-knows-where. I would imagine that the percentage of professionally written code in Microsoft Windows 7 is much higher than the percentage in Ubuntu, but the community that creates Ubuntu is *much* larger. One of the sayings in open source community has something to do with many eyes making the bugs more obvious.

If you want some specific technical information about how to determine what is or is not safe on your computer, start reading about [apt](https://help.ubuntu.com/community/AptGet/Howto).  Apt is the software manager for Ubuntu (and its predecessor Debian) and the way it works is to check [repositories](https://help.ubuntu.com/community/Repositories/Ubuntu) for software packages that are [painstakingly packaged](https://wiki.ubuntu.com/PackagingGuide/Complete) by knowledeable volunteers or sometimes paid folks.  You have little control over what software is available or what's in a package unless you want to go create one yourself.  I don't recommend it.

You can **harden** your installation of Ubuntu by doing a number of things:
* turn off unnecessary services that you don't use
* edit configuration files and iptables to exclude unauthorized access from foreign places or strange IP blocks
* be VERY careful about which packages you install.

Now that last point is, I think, what you are really asking about.  **Can I trust package X?**.  This is what I've been looking into for days and the answer depends on the package but there is more information available to you for a given package.

apt starts with your **sources.list** file which is found it */etc/apt/sources.list*. This is a list of repository urls that host software you might want to install.  You'll note that each URL in that file is followed by words like "main," "restricted," "universe," and "multiverse". I'm not sure what the term is for these categories or whatever, but if you limit yourself to just **main**, excluding all the others, then you are limiting your installed software to only the innermost collection of files for Ubuntu.  If you include multiverse, then you are being considerably more promiscuous with your software installations and you might want to assess your installations on a package-by-packages basis if you really need those multiverse items.

What is perhaps even more important is that you should make sure the URLS themselves are trustworthy.  archive.ubuntu.com is a lot better than hax-r-us.moneystealers.cn.

If you want to dive really deep into this, then start reading about [SecureApt](http://wiki.debian.org/SecureApt) and you'll learn that packages are digitally signed and that apt maintains a list of trusted keys that it consults when installing new software.

Personally, I tend to use main and universe while exluding restricted and multiverse. If you want to see a case study of a compromised sever and the forensics performed on it and also the steps being taken to move it, consider reading [these](http://www.linuxquestions.org/questions/linux-newbie-8/centos-5-ssh-compromised-cant-yum-update-889457-new/) [threads](http://www.linuxquestions.org/questions/linux-security-4/configuring-and-hardening-a-new-server-to-replace-compromised-machine-891764/). There are some really smart guys over at linuxquestions.org and they've been very helpful to me.

---

### Post by sneakyimp on 2011-07-21
I take it back that signed packages are checked.  Check out your dpkg config:
```

# Do not enable debsig-verify by default; since the distribution is not using
# embedded signatures, debsig-verify would reject all packages.
no-debsig

```

:(

---

### Post by Bardobrave on 2011-07-22
Thanks for your posts SneakyImp, there are some pretty clues I can use.

It seems a bit dissapointing to me that a community as big as this doesn't have some workgroup dedicated to check for the reliability of popular sources.

I can understand that the spirit of the free code should make it "somewhat unnecesary" but I think that a great security risk live beneath the global idea of "we are linux, we are secure, this software will be ok if 50k people have installed it. Someone should had checked it already"

I've seen that truly popular packages, elements and configuration modules (from icon collections to wallpapers, desktop plugins, etc...) are published through PPAs and everyone seems to feel fine about it. I see it in lots of community pages where thousands of users access and donwloads them.

I think... being Ubuntu the largest used linux distro, and probably one with the less expert users (due to it's size and the easy of use of the own distro) it would be fairly easy for some b@st@rd to take a popular script or decorative add-on, make slightly changes to it, add some malware to get keylogs, publish it on community pages and wait for people installing it. Sooner or later the danger will be detected and dealed with, but the sole idea makes me feel somewhat unsafe. 

Surely linux is an os very effective in security terms, asking for root permissions to almos any dangerous activity, however I'm wondering if the fast growth of ubuntu worldwide won't represent a risk of becoming target of malicious individuals that could represent a danger for further expansion and for the entire community.

---

### Post by amiacamal on 2011-07-22
Imagine tho, If there were a group dedicated to saying "This source is a-ok". If the group verified a source, and the source was THEN compramised, then what? "well it was ok when we checked it!".

---

### Post by Grenage on 2011-07-22
> **Bardobrave said:**
> Thanks for your posts SneakyImp, there are some pretty clues I can use.

It seems a bit dissapointing to me that a community as big as this doesn't have some workgroup dedicated to check for the reliability of popular sources.

I can understand that the spirit of the free code should make it "somewhat unnecesary" but I think that a great security risk live beneath the global idea of "we are linux, we are secure, this software will be ok if 50k people have installed it. Someone should had checked it already"

I've seen that truly popular packages, elements and configuration modules (from icon collections to wallpapers, desktop plugins, etc...) are published through PPAs and everyone seems to feel fine about it. I see it in lots of community pages where thousands of users access and donwloads them.

I think... being Ubuntu the largest used linux distro, and probably one with the less expert users (due to it's size and the easy of use of the own distro) it would be fairly easy for some b@st@rd to take a popular script or decorative add-on, make slightly changes to it, add some malware to get keylogs, publish it on community pages and wait for people installing it. Sooner or later the danger will be detected and dealed with, but the sole idea makes me feel somewhat unsafe. 

Surely linux is an os very effective in security terms, asking for root permissions to almos any dangerous activity, however I'm wondering if the fast growth of ubuntu worldwide won't represent a risk of becoming target of malicious individuals that could represent a danger for further expansion and for the entire community.

The work involved on checking the code for every version of software commonly used would be immense, truly immense.  The same can really be said of any of the main OSs.

---

### Post by Bardobrave on 2011-07-22
> **amiacamal said:**
> Imagine tho, If there were a group dedicated to saying "This source is a-ok". If the group verified a source, and the source was THEN compramised, then what? "well it was ok when we checked it!".

Yeah, what I'm wondering is a system where someone checks for integrity and incorporates it to a "trusted repository" from where people can rely. 

When a new version of the package comes, the check is remade and the new version added to the repository.

When trusted repository is compromised, intrusion is detected soon, repaired and, due to be centraliced, easily distributed to even unaware users.

---

### Post by Bardobrave on 2011-07-22
> **Grenage said:**
> The work involved on checking the code for every version of software commonly used would be immense, truly immense.  The same can really be said of any of the main OSs.

Of course I'm aware of this. I only wonder why there is no group trying to do his best into this while there are lots of communities self-centered in dozens of other projects almost as hard as this.

I mean... being security a main matter in Ubuntu (as it's own publicity stands for) there isn't intheresting to deal at least with the idea?

Also I'm not proposing to check every bit of code that anyone publishes. But I think that it could be a group of people monitoring somewhat popular elements that could be integrated into this trustful repositories.

All comes here because I feel that the idea of being secure only because something is used by lots of people is somewhat like saying "Hey, if tobacco would be harmful there wouldn't be millions of smokers". And this sounds to me like a great no-no when something bears security as his flagship, because it could drive millions of users to a false sensation of inmunity.

This, IMHO is a truly danger for the evolution of a project like Ubuntu.

---

### Post by amiacamal on 2011-07-22
Personally, im working towards bringing myself to a level where i can petrsonally check code i want to install. in the meantime all i can do is install from repo's and software centre, hope, and look out for oddities on my system!

---

### Post by bodhi.zazen on 2011-07-22
> **Bardobrave said:**
> It seems a bit dissapointing to me that a community as big as this doesn't have some workgroup dedicated to check for the reliability of popular sources.

Well, you are a member of the community, if you want such a group nothing is stopping you from starting one.

"The community" does have a security team, but they limit their activity to the packages in the repositories for obvious reasons, you can not expect the Ubuntu community to police all of the various opens source projects.

---

### Post by sneakyimp on 2011-07-22
> **bodhi.zazen said:**
> Well, you are a member of the community, if you want such a group nothing is stopping you from starting one.

Well said!

And we could start by trying to enforce signatures.  A very kind security guru I'm in touch with has informed me that only one of the 3 major distros actually bothers to verify signatures.

I think it's also very important to realize a technical point here as it will likely give you an idea of the difficulty involved.  All a signature does is let you verify that a particular document was "signed" by some particular individual.  If that signature is on a checksum, you know (let's ignore the whole monkey chain of steps about encryption blah blah blah) the individual has *signed* the checksum document.  Checking the checksum document against the actual checksum of the package is an additional step and even that doesn't verify that the code is not malicious.  All the signature means is that some individual signed the document.  Whether you trust that individual is still up to you. Think about it for a moment: Do you personally know anyone involved in the Ubuntu packaging team?

A signature in no way assures that the code is safe, but it does help to assign blame when a bad package is discovered.  That blame can be assigned to all individuals who have the private key used to sign the package. This blame may ultimately tarnish their reputation or even send them to jail. It doesn't fix the code.

Even understanding how the signatures work is a chore.  Now consider that there are some 380 packages in a clean install of Ubuntu 10.04.  I believe a full-blown linux install has about 5 million lines of code. Assuming you could find 500 people qualified to perform a code audit (which sounds really tough IMHO -- such a person must be *very* smart) then each one is charged with auditing 10,000 lines of code every single time a release is produced.

There's no doubt in my mind that there is work that could be done here. The trick is finding out where we can help rather than moaning about it.

---

### Post by bodhi.zazen on 2011-07-22
> **sneakyimp said:**
> And we could start by trying to enforce signatures.  A very kind security guru I'm in touch with has informed me that only one of the 3 major distros actually bothers to verify signatures.

The forums is not the way to communicate such questions with the developers. Use launchpad (file a bug report against security), but I do not understand the technical details of what you mean by "checking signatures".

---

