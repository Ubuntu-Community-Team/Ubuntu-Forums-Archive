---
title: "Hardening full metal jacket"
date: 2007-06-02
forum: Server Platforms
---

### Post by deadlinx on 2007-06-02
Hi,

I use Ubuntu, I want to increase safety, I use:

- a good firewall configuration,
- Snort,
- Tripwire,
- Chkrootkit,
- Rootkithunter,
- Bastille,

but I want more, I want kernel hardening, but Ubuntu seems not to have an easy support to hardening (like Fedora does) or something like an hardened version (like Hardened Gentoo).

- SELinux needs the old sysvinit and anyway, after tuning doesn't work very well, anyway it's not well 
  supported yet.

- Apparmor suffers the recently porting, is not perfectly supported yet.

- Vsecurity, unstable,

- RSBAC, very good, but need a lot of time in studying and tuning, too much to protect a desktop

- GRSecurity is perfect, I use it, but since the 2.6.19.2 patch PAX doesn't really apply and there's no the 
  stack protection, the bug is not correct yet.

In the end my problem is:

- lack of a serious kernel hardening Ubuntu-way for servers or geek-desktop

- lack of good tutorial explaining how to recreate a Ubuntu kernel from a vanilla one.

I mean I never found, a good tutorial explaining how to recreate all Ubuntu kernel tunings to a new vanilla, so when I built a vanilla patched with GRSecurity, I don't know how to compile the ipw3945 support because there's problem with the 2.6.2x kernel and I can't find a tutorial explaining me how to solve this problem, but Ubuntu team has solved it, but how they did? We don't know!

---

### Post by craigp84 on 2007-06-04
Fruitcake.

---

### Post by smbm on 2007-06-04
> **craigp84 said:**
> Fruitcake.

That made me laugh a lot. :p Thanks for cheering me up at work.

---

### Post by deadlinx on 2007-06-04
Hi,

I like joking, 
but I've written some questions so, 
if you know something about it, 
please,  
reply your good ideas, 
anyway, 
no-one has time to waste...

deadlinx

---

### Post by deadlinx on 2007-06-06
Hi,

**_no useful replies_**...

does it mean there's no Ubuntu administrator really interested in securing his machine...uhm?
I don't think so!


This is not a blog so it's not useful there's a writer and other people only readers, don't you?

What about the community support?

_**What about the helpful spirit every free software user should have?**_

I don't think my post is so stupid and doesn't deserve a, _**useful**_, reply

---

### Post by jtc on 2007-06-06
> **deadlinx said:**
> 
does it mean there's no Ubuntu administrator really interested in securing his machine...uhm?


I'd say a lot of system administrators are more concerned about how to best configure their daemons, what privileges to give their users etc.  I'm not saying kernel hardening isn't useful, but it won't do you much good if someone can drive a bandwagon through PHP or OpenLDAP.

Then there are the time-costs and the trade-offs against usuability. Again I'm not saying that the tools you are talking about don't have any importance, simply that they might not be the highest priority on all systems.

---

### Post by deadlinx on 2007-06-06
Hi,

> **jtc said:**
> Again I'm not saying that the tools you are talking about don't have any importance, simply that they might not be the highest priority on all systems.

I agree, but all possible tuning, you mentioned, are avaliable via-RSBAC and surely grant us more security!

Not only there's no a serious Ubuntu project  about kernel hardening, like other distro do (Gentoo etc), 
but also some people is joking about it, 
but I think they stop laughing if their servers will be owned by a high skilled cracker: 
security is not an optional apart for Win fans...

deadlinx

---

### Post by craigp84 on 2007-06-06
> are avaliable via-RSBAC and surely grant us more security!

Ok, so where do you draw the line? Encase the box in a 4ft thick titanium container, hide it somewhere under the sea? Wow, sounds great. Lan party at your place 2nite?

Now if you're researching security solutions, i don't know, maybe to better your employment prospects, then more power to you. Rock on.

Blindly chewing through every security product on the planet however, isn't very purposeful.

> Not only there's no a serious Ubuntu project about kernel hardening, like other distro do (Gentoo etc)

At this point, ubuntu is firmly a desktop targeted distribution with specific focus on ease of use. That's it. There is a baby "server" product in the making, but it's in it's extreme infancy, and not much of a "server" oriented distro - yet. There's a few other off-shoots (kubuntu, xubuntu), but loosely all focused at providing an easy to use linux desktop.

So why on earth would there be a security focus? Does security make the desktop easier to use? No.

Sounds like you're in the wrong distro.

Yet another case of "New Hammer" syndrome i think. Ubuntu is everyone's new hammer - even though it's not the most appropriate tool in a lot of cases.

Oh - and please, noone start casting up "but security's important" type stories; i'm not disagreeing. It's just not high enough priority here, right now. I do think ubuntu's security standards should be at the "good enough" standard, and in my opinion, they already significantly surpass that mark. [Sometimes]("http://ubuntuforums.org/showthread.php?p=2782722") i [wonder]("http://ubuntuforums.org/showthread.php?t=413580") [about]("http://ubuntuforums.org/showthread.php?t=435278") the [community]("http://ubuntuforums.org/showthread.php?t=337063") of [users]("http://ubuntuforums.org/showthread.php?t=72284") [though.]("http://ubuntuforums.org/showthread.php?t=221922")

> but also some people is joking about it

No hard feelings were intended above, it was just my sense of humour, please don't take that personally (i don't think you have anyway - good for you).

> but I think they stop laughing if their servers will be owned by a high skilled cracker

Well, while i in no way agree with the following logic, it is undeniable that a certain population of the unprofessional IT community are quite happy for their clients systems to be compromised occasionally - it's additional work which is additional dollars for them. That type of person would probably be open to cutting the hacker in on the deal?

As for me, you're right, i don't really want someone pedaling spam through my systems. If someone broke into a server of mine, and i found out about it i would be upset. I'm sure i'd be infinitely more p1ssed if it was an un-skilled hacker though.

> security is not an optional apart for Win fans

Security *products* very much are optional - for windows and linux, to be fair, more so linux, there's too many easily expoloitable things out of the box with windoze (updates are security products for this purpose).

*Security* is a journey, not a destination as the quote goes - this is turning into my favourite quote on here!

More seriously, there's a gross misconception in your statement. I don't believe it's windows that's poor at security so much as the users. Take a look around these forums. See the numbers of reports of intrusions. This is normally more of a reflection on the user, than their product. This increased rate of break ins has somehow magically increased linearly with the amount of clowns using ubuntu. You draw your own conclusions.

---

### Post by Cheese Sandwich on 2007-06-07
:lol: Great thread!

IMO, on a philisophical point, it's always a fun thought exercise to think about how to make things in general more secure, more so than practically needed. Just like it's fun to think about how to thwart others' security. :)

---

### Post by deadlinx on 2007-06-13
[QUOTE=craigp84;2793138 You draw your own conclusions.[/QUOTE]

Next saturday will be a Linux_meeting not far from my home,
I read about the talks titles, there's one about how to use RSBAC for 
protecting a desktop Linux_box...

In the end maybe I'm not the only people looking for a secure desktop distro.

For instance:
an executable stack is, in theory, a danger, it's a fact, 
i consider this a point to look at, 'cause I think increasing securing is
always a good idea surely better than playing with Xgl and so on.

deadlinx

---

### Post by gaten on 2007-06-14
I would personally like to see a more concentrated effort by the Ubuntu community to create a "hardened" distro as well. My advice is to post an idea in the Gusty Gibbon (or whatever) forums, there is already one for including an option for setting up an EFS  during install.

I wish I could help  you, I really do, but I'm afraid that's all I have to offer. I totally agree with your statement about securing things as much as possible; the fact that it is not 'user friendly' stems from the fact that no one has sat around and *made* it such. 

Perhaps I'll throw Feisty into a VMware image and see if I can get GRSec to work, I've heard good things about it. Please, let me know if you get any further with this topic, I'm interested in your findings and helping if I can.

---

### Post by jtc on 2007-06-14
deadlinx: Perhaps you could take a look at the ubuntu-hardened list?

[https://lists.ubuntu.com/mailman/listinfo/ubuntu-hardened](https://lists.ubuntu.com/mailman/listinfo/ubuntu-hardened)

Not very active, but still.

---

