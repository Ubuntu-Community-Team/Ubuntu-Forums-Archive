---
title: "is Unity desktop open source?"
date: 2016-02-03
forum: Ubuntu, Linux and OS Chat
---

### Post by a-ranchalpedrosa-5 on 2016-02-03
Hi,

I have been using Gnome3 for quite a long time already but I was wondering if Unity desktop is open source, since it looks to me that the fact only ubuntu uses it makes it suspicious somehow. Also, I would like to take a chance and ask what desktop environment, in your opinion, is the best one in terms of support to/by the open source community.

---

### Post by buzzingrobot on 2016-02-03
> **a-ranchalpedrosa-5 said:**
> Hi,

...wondering if Unity desktop is open source...

Yes.

---

### Post by TheFu on 2016-02-03
Seems you are learning the difference between "open source" and "F/LOSS."  No all "open source" licenses are created equal.  For example, MS-Windows source code is "open source" to the Russian government, but that doesn't give them the right to modify it.  Commercial software creators have jumped onto the "open" this/that marketing bandwagon, but sorta miss the entire point of it, IMHO.

BTW, did you google for an answer first?  [https://askubuntu.com/questions/9976/under-which-licence-is-unity-available-is-it-protected-by-any-copyright-or-pate](https://askubuntu.com/questions/9976/under-which-licence-is-unity-available-is-it-protected-by-any-copyright-or-pate)

Look for the source code?  [https://launchpad.net/unity](https://launchpad.net/unity) - BTW, the license is listed right there.  GPLv3 or LPGLv3.

Inside every file of the unity source code will be the license it is released under.  I haven't looked either, but I do know that Canonical requires code contributors to accept their contributor agreement, which isn't a normal GPL thing. [http://www.ubuntu.com/legal/contributors](http://www.ubuntu.com/legal/contributors)  These sorts of agreements are pretty standard to allow the company the ability to sell stuff with code freely given and to change the license later without asking.  Old F/LOSS projects didn't get agreements like these and if they cannot get approval from every contributor at a later time (maybe 15-40 yrs later), then they cannot change the license that project is released under. This may be good or it might be terrible. 

I'd like to see a license that is "F/LOSS" for small companies trying to grow, but fees kick in as the company profits.  For example, facebook, twitter, google, Apple, Canonical, Redhat, SuSE, Mozilla, Plex, Amazon, AT&T, Verizon, BT, (and thousands of others) all use different forms of F/LOSS software and some give back in a way, but not all do.  The gnome project is always fighting for money, so perhaps a different license model is needed?  Trying to be "fair" is a hard thing. What is a "fair" amount for a company like google to pay?

Having a sustainable F/LOSS project model isn't easy. People need to feed their kids, right?

---

### Post by grahammechanical on 2016-02-03
> the fact only ubuntu uses it

Here we have another thing about Free and Open Source Software (FOSS) development and it is the fact that developers are free to follow their own visions. If you think that a certain FOSS project is going in a direction that you do not like then you can take the code and start a new project according to your tastes.

Ubuntu used to be a distribution that was built on Gnome 2 desktop environment and used the Gnome 2 panel as a user interface. Then Gnome.org switched to Gnome 3 desktop environment and the Gnome 3 shell. And the Ubuntu developers thought that they had a better way to do things. So, Ubuntu gained Gnome DE but without Gnome 3 shell. We got Unity instead.

The thing stopping other distributions using Unity is not because Unity is suspect in some way but because they have their own ideas about how things should be done. And do not discount rivalry between developers.

I think that this project is now discontinued but the post proves that Canonical is not stopping anyone for getting access to the Unity source code. Even by those who might be seen as commercial rivals.

[http://news.slashdot.org/story/12/07/19/1529230/ubuntu-unity-ported-to-fedora-using-opensuse](http://news.slashdot.org/story/12/07/19/1529230/ubuntu-unity-ported-to-fedora-using-opensuse)

> Calling Unity "popular" seems like a stretch, but it's certainly where a  lot of Ubuntu work has been lavished; the cooperation that open source  code fosters at least lets **whoever wants to use or develop it do so**.

Regards.

---

### Post by deadflowr on 2016-02-03
Moved to Ubuntu Linux and OS Chat

---

### Post by monkeybrain20122 on 2016-02-03
Unity is completely FLOSS. There is an unofficial port to [ArchLinux]("https://wiki.archlinux.org/index.php/Unity"), so it is not because of any legal or licensing issue that it is not ported to other distros. Based on discussions on their [forum]("https://bbs.archlinux.org/viewtopic.php?id=125423&p=116") it seems that the reason is more of a technical one. Since Unity used patched gnome libraries downstream and they are incompatible with the unpatched gnome libraries upstream, a distro would end up having to maintain and package both if it decides to offer both Unity and gnome spins. A problem faced by the Arch unity people is that something breaks everytime some component in gnome gets updated and the fact that Arch is rolling makes this even more problematic.

---

### Post by grahammechanical on 2016-02-03
Canonical originally wanted the Unity APIs to be merged upstream into the Gnome 3 shell project but the request was refused. Only according to Gnome the request was not refused because no request was received and if there was a request it was not a formal request. I think that was the point that Canonical decided it had to plough its own furrow.

I think a similar situation developed with OpenOffice with community developers becoming convinced that code of employees paid by the corporation that owned OpenOffice was getting priority acceptance over their own code. So, the community developers took the OpenOffice source code as it was open source and started LibreOffice.

---

### Post by ian-weisser on 2016-02-03
> **a-ranchalpedrosa-5 said:**
> since it looks to me that the fact only ubuntu uses it makes it suspicious somehow.

Unity is arguably the most popular desktop on the world's most popular Linux desktop distro.
 Some love it, some hate it, but most new Ubuntu users get Unity by default...and most unskilled users like using it.

Unity, with Mir and Click/Snappy and a couple other projects, are tightly bound to Ubuntu's plans for Convergence.
Other distros uninterested in working well on Phones and Tablets and TVs would quite understandably lack interest in those components.

Also, the birth of Unity was a time of great rancor within and among distros and flavors. Much of the associated FUD and resistance is muted but still present. Another distro introducing Unity, in addition to paying a large technical debt to learn it, would have a fierce internal struggle as that legacy rancor reignited. I suppose other distros do not value the gain to be worth the disruption and risk.

---

### Post by Sweet_Baby_Jamie on 2016-02-04
I have had the same question about the Ubiquity installer.  It's so easy!  Almost every Ubuntu-based OS uses it (Mint, LXLE, probably dozens more), but why not Debian or any Debian-based distro?  Why not *any* non-Ubuntu-based distro?  I would think that any Linux dev would at least borrow elements of it since it's so beginner-friendly and all. At least if I was making a beginner-friendly distro, or a kid-friendly one, I would want an installer that takes the user step by step and makes it simple.

---

### Post by monkeybrain20122 on 2016-02-04
Debian likes to make things difficult. It doesn't even have a real graphic installer (I know, they call that text thing with yes/no prompts and text input boxes a gui)

---

### Post by buzzingrobot on 2016-02-04
> **TheFu said:**
> 
I'd like to see a license that is "F/LOSS" for small companies trying to grow, but fees kick in as the company profits.  For example, facebook, twitter, google, Apple, Canonical, Redhat, SuSE, Mozilla, Plex, Amazon, AT&T, Verizon, BT, (and thousands of others) all use different forms of F/LOSS software and some give back in a way, but not all do.  The gnome project is always fighting for money, so perhaps a different license model is needed?  Trying to be "fair" is a hard thing. What is a "fair" amount for a company like google to pay?



Interesting idea.  Perhaps it could be keyed to the number of installations. Below X, no fees.  Above X, fees. 

 How to make it work is a different matter.  Who do the fees go to? E.g., if a business grabs an Ubuntu install image and sets up 100 desktops, does it pay Canonical a flat fee? Does it pay individual fees to every developer of every package in the distribution? Do I owe someone a fee if I build Github source? 

One approach would be a "bank" that collects all fees -- however they are levied -- and disburses funds throughout the "community". I suspect that would require a level of consensus and trust that I don't think actually exists, however. (And, are  corporate players to be exempt from fees on code they contributed?)

The conflation of "free software" with "free from cost" wasn't much of an issue 30+ pre-internet years ago when RMS began preaching about free software. Software is now a consumer commodity.

---

### Post by ian-weisser on 2016-02-04
> **Sweet_Baby_Jamie said:**
> I have had the same question about the Ubiquity installer.  It's so easy!  Almost every Ubuntu-based OS uses it (Mint, LXLE, probably dozens more), but why not Debian or any Debian-based distro?

Debian is a community-based distro. Any community member who cares deeply about the issue and is willing to do the work....


> **buzzingrobot said:**
> Interesting idea.  Perhaps it could be keyed to the number of installations. Below X, no fees.  Above X, fees.
Many large and small companies contribute software, patches, engineering and testing time, conference support, etc., in lieu of fees.

---

### Post by monkeybrain20122 on 2016-02-04
But if you charge a fee you also become accountable to users, so e.g gnome devs won't be able to pull that my way or the highway stunt of removing features randomly. So maybe they don't even want the money so they can stick to their 'vision'.

---

### Post by TheFu on 2016-02-04
> **monkeybrain20122 said:**
> But if you charge a fee you also become accountable to users, so e.g gnome devs won't be able to pull that my way or the highway stunt of removing features randomly. So maybe they don't even want the money so they can stick to their 'vision'.

Devs aren't accountable to users, they become accountable to whoever paid. Often there is a huge difference. 

Keeping track of licenses really sucks. That isn't a realistic answer, IMHO.
We're a little off topic now.

---

