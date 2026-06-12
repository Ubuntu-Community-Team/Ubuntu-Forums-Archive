---
title: "Deb files: Possible trojan creation"
date: 2007-11-03
forum: Server Platforms
---

### Post by hyperair on 2007-11-03
I had just been discussing with a friend about the apparent absence of Linux viruses/other forms of malware, and how it may pick up should Linux be adopted on a much wider scale.

I read some articles about how a virus in Linux would probably die out rather rapidly due to the hostile conditions for a virus to survive on a Linux box. However something did pop up on my mind which got me a little concerned. 

There are many places where you can download deb files without authentication or whatnot. Let's say, I decided to compile a deb from source for a certain software. However, I rigged the postinst/preinst scripts to create a script which will reside in the /etc/rcX.d folders. Since deb files are installed by root, the script(s) will have the permissions necessary to drop the files off (trojan). 

As a result, the trojan will be run (as root) upon system startup. Having root permissions, this trojan process will be able to detect all the users' home folders, and be able to read any files inside them (address books, history files). Social engineering could be used to make the virus spread, through E-mail, for instance, via sendmail. The deb file could be attached, as a means of spreading the trojan. This could all be done in the background without the user noticing. 

The trojan could then just sit around and open a port and connect to a server to receive instructions and whatnot, and become one of those zombie computers which can be used for DDoS-ing servers.

What I've just highlighted here is that it seems to be possible to create a virus that not only survives, but thrives in Linux, via the deb file. Perhaps (and I certainly hope so) I might have missed out something here that makes all this impossible. But should it be possible, I think that this is a matter worth looking into.

---

### Post by CptPicard on 2007-11-03
Sorry to be blunt, but... O RLY -- no ****, Sherlock :)

As a rule, whenever you run any executable code on your machine, in particular as root, you run the risk of being 0wned, no matter the operating system. This is neither a specific Linux problem nor should come as a surprise to anyone that if you install software on your machine from an untrusted .deb, this is exactly what could happen.

It's exactly the same as if you downloaded some random .exe from the Internet and executed it as Administrator on your Windows box. Of course .debs are not exactly executables so the situation is not QUITE as bad as on Windows but still... (EDIT: ok, so the installation scripts are...)

This is why it is important to use signed stuff from trusted repos. I know a lot of Ubuntu n00bs don't seem to like repos for some strange reason and insist that things should work as they do in Windows, and this worries me -- as users, they are probably as badly security-conscious as they were on Windows, and the OS will NOT be able to protect them if they willingly let anyone use their root rights without concern for what might happen... of course, Linux DOES offer some protection against even trojaned executables if you configure them properly (as in, run servers under unprivileged users etc), but as a rule of thumb, only install what you trust.

---

### Post by Steveway on 2007-11-03
You don't install .deb files from untrusted sources.
We have the trusted repositories from wich we install everything.
If you install a .deb from an untrusted source and it is infected then it is your own fault.

---

### Post by LaRoza on 2007-11-03
> **hyperair said:**
> 
There are many places where you can download deb files without authentication or whatnot. Let's say, I decided to compile a deb from source for a certain software. However, I rigged the postinst/preinst scripts to create a script which will reside in the /etc/rcX.d folders. Since deb files are installed by root, the script(s) will have the permissions necessary to drop the files off (trojan). 

I think that this is a matter worth looking into.

What is the point? That a user can bork their own system?

This is no problem of Linux, it is a a PICNIC issue. (Problem In Chair, Not In Computer)

Something to look into? If you want to look into user stupidity, you better have a lot of time on your hands.

---

### Post by hyperair on 2007-11-03
Well what I was trying to point out here is that, while we can expect the users to be security-conscious enough to take the steps necessary to keep their systems secure, truth be told there are a lot of people who are stupid enough to simply install software on their computers. A lot of these stupid people are also the system administrators of the computers in their home, and hence have root access. 

This scenario might be rather hard to think of now, but come one day if and when the Linux Desktop really takes off and becomes the most widely used system in desktop PCs, how sure are you this won't grow into a larger problem?

Also, trying to be fair here, though I'm usually biased against Windows, if a Windows user doesn't simply download and click .exes on their computer, granting administrative access where necessary, Windows viruses won't spread easily too. And though I hate to admit it, what I've just pointed out here points towards Windows being not far behind Linux in terms of security.

> It's exactly the same as if you downloaded some random .exe from the Internet and executed it as Administrator on your Windows box. Of course .debs are not exactly executables so the situation is not QUITE as bad as on Windows but still...
...there are people stupid enough to do that. 

p.s. I posted this for a healthy discussion, so I'd appreciate it if nobody gets too offended/opinionated and begins a flamefest, not that anyone has, but in case the thread continues growing.

---

### Post by Steveway on 2007-11-03
There are disscusions on the mailing lists that talk about making it harder for people to install random .deb files on their computers (or even impossible).
If you think you have something necesarry to say then you should participate there.

---

### Post by CptPicard on 2007-11-03
> **hyperair said:**
> Well what I was trying to point out here is that, while we can expect the users to be security-conscious enough to take the steps necessary to keep their systems secure, truth be told there are a lot of people who are stupid enough to simply install software on their computers. A lot of these stupid people are also the system administrators of the computers in their home, and hence have root access. 

And at that point, there is absolutely nothing you can do to help them on any general-purpose computational device where you still give them the right to do whatever they please. What should we do? Restrict their machines from the outside to running only approved software?

This has nothing to do with the OS in question, it's pretty much a fundamental point of computation... you have no way of knowing what is in the .deb as long as you give the user root. It has a lot to do with the halting problem of Turing machines and stuff :)

> This scenario might be rather hard to think of now, but come one day if and when the Linux Desktop really takes off and becomes the most widely used system in desktop PCs, how sure are you this won't grow into a larger problem?

It's not hard to think of because it's frankly obvious. To me, more of a nightmare scenario would be a break-in into the repositories as that is a central point of failure. It's still a better system than just downloading random .debs of the net; at least there is someone vouching for the correctness of the code.

> Also, trying to be fair here, though I'm usually biased against Windows, if a Windows user doesn't simply download and click .exes on their computer, granting administrative access where necessary, Windows viruses won't spread easily too. And though I hate to admit it, what I've just pointed out here points towards Windows being not far behind Linux in terms of security.

User granting root to random code will always risk compromising the system on any OS. Linux is more secure than Windows for a number of reasons, but this is not one of them -- if you leave the door open, it does not matter if you live in a straw shack or a bank vault.

Of course, having trusted repositories of open source code with trust chains extending all the way to the developers, is something Windows really doesn't offer, so the Linux way of doing things is way superior to the "Windows way". If you want to get rid of the PICNIC problem, educate the user -- it's the only way.

---

### Post by hyperair on 2007-11-03
> **Steveway said:**
> There are disscusions on the mailing lists that talk about making it harder for people to install random .deb files on their computers (or even impossible).
If you think you have something necesarry to say then you should participate there.

I see. What mailing lists are these, and where can I join them?

> **CptPicard said:**
> And at that point, there is absolutely nothing you can do to help them on any general-purpose computational device where you still give them the right to do whatever they please. What should we do? Restrict their machines from the outside to running only approved software?[quote]
I guess you're right in this aspect. We cannot really do anything to stop them running only approved software. Such a thing would definitely spark an outburst, and make things much more complicated to the newbies.

[QUOTE=CptPicard;3699550]It's not hard to think of because it's frankly obvious. To me, more of a nightmare scenario would be a break-in into the repositories as that is a central point of failure. It's still a better system than just downloading random .debs of the net; at least there is someone vouching for the correctness of the code.
It has happened before (I'm not sure which package manager it was referring to though), but granted they didn't manage to hack the signing key as well, so the hacked Debs didn't make it to those who made sure the packages were verified and authenticated. The packages were fixed the next day.

> **CptPicard said:**
> User granting root to random code will always risk compromising the system on any OS. Linux is more secure than Windows for a number of reasons, but this is not one of them -- if you leave the door open, it does not matter if you live in a straw shack or a bank vault.
Great analogy you have there. I guess it really is hard to protect the system from root misuse when the user himself/herself gives the code root privileges.

> **CptPicard said:**
> Of course, having trusted repositories of open source code with trust chains extending all the way to the developers, is something Windows really doesn't offer, so the Linux way of doing things is way superior to the "Windows way". If you want to get rid of the PICNIC problem, educate the user -- it's the only way.
Very true. However, educating the user.. it's hard to do that isn't it. A lot of people do not take the initiative to learn. I guess it's good enough that Ubuntu drops hints everywhere that 3rd party applications should be trusted before they be installed.

---

### Post by Steveway on 2007-11-04
> I see. What mailing lists are these, and where can I join them?
[http://ubuntuforums.org/showthread.php?t=562529&highlight=scary+mailing+list](http://ubuntuforums.org/showthread.php?t=562529&highlight=scary+mailing+list)

---

### Post by ruibernardo on 2007-11-04
> **hyperair said:**
> I guess it's good enough that Ubuntu drops hints everywhere that 3rd party applications should be trusted before they be installed.
I totally agree with this. People are using Ubuntu and Linux as no harm can be done (virus and firewall) and because many of them think that all that has "opensource" on the brand, it's safe.

The users must be told that using a third party repository - I'm not talking about developers repositories,  *generally* they're safe - like getdeb and others, where everybody can build a package and put it there represents a risk. Many users (most of them, I've even been criticised about this suggestion) don't look twice about who really did build that package and what it really installs and who did really compile it, they just want the "latest version" without having the work of compiling sources, all this with the wrong assumption that linux is bullet proof.

If Ubuntu users start to use third party repositories as a "download site" without any precautions about the origin of the software they are installing "because linux is safe", then the users definitely must be educated. If not, Ubuntu is risking its reputation of a safe OS and will just be as safe as windows.

Getdeb users and package builders, don't take this personally, it's a question of logic and philosophy. I know who really did compile and build a package from a developer or Ubuntu repository , but I can't say the same about a getdeb (and others) packages/repository.

Sorry for how this sounds, but I'm talking about educating users about "bad habits".

---

### Post by Can+~ on 2007-11-04
I had an idea that would partially fix this.

As there is a list to download applications, why not make a black list with applications/repos that shouldn't be executed/added, and propmt a "This item/repository is blacklisted".

Pretty much like the body works, when there is a problem, it learns from it, and then knows how to react when that virus strikes again. So this blacklist will be produced by users which had bad experiences with some repository or software, upload it, and if it's something that affects more users, start blacklisting it, avoiding the metastasis.

---

### Post by evets on 2007-11-05
> **LaRoza said:**
> What is the point? That a user can bork their own system?

This is no problem of Linux, it is a a PICNIC issue. (Problem In Chair, Not In Computer)

Something to look into? If you want to look into user stupidity, you better have a lot of time on your hands.

I just saw your How to Mark a Thread SOLVED. Thanks, that's the cause of my hair loss, as I have been scratchin' my head for weeks tryin' to figure that out. :)

---

### Post by primski on 2007-11-06
PICNIC lol, first time i see this, brilliant.

---

