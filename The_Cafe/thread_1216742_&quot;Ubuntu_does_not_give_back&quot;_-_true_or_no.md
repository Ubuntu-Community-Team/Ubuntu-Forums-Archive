---
title: "&quot;Ubuntu does not give back&quot; - true or not?"
date: 2009-07-18
forum: The Cafe
---

### Post by Screwdriver0815 on 2009-07-18
Hi @all

in the last time I again read more and more comments on some german Linux sites which state, that Ubuntu would always just use open source software and does not give back patches.
This would result in issues like "the Fedora guys wonder why certain Laptops work with their version of the gnome power manager but in Ubuntu some more Laptops also work fine - and there is no patch from Ubuntu available at Fedora"...

Of course also the Kroah-Hartman stuff is mentioned ("Ubuntu does no work at the Kernel")

But the work of Ubuntu, like Upstart, the Gnome-stuff and so on is not mentioned...

So as I assume that also some developers read in this forum I would like to hear the opinion of "the other side" and also from you users: do you care about all these reproaches?

Or generally spoken: is it true that Ubuntu only takes and hides their improvements and patches from the world of FOSS?

I don't want to start any flameing. 

In my opinion we as users of Ubuntu should be thankful to the Debian guys for delivering a strong base. We also should be thankful to the big companies and all the developers, not limited to the Ubuntu MOTUS and so on. But also at Red Hat, Novell, and all the private developers.

In my eyes Ubuntu also gives back. But I am not really sure because I don't know the universe of FOSS. 
If Ubuntu does not give back anything, wouldn't it be like this that the other companies would kick Ubuntu to the Linux Foundation or a similar institution which could judge whether Ubuntu behaves in the right way?

whats your opinion?

---

### Post by JDShu on 2009-07-18
As far as I know, since its open sources, Ubuntu can't just hide anything. Also, Ubuntu has submitted patches to the linux kernel, though the small number of these patches has been criticized.

---

### Post by doas777 on 2009-07-18
there are some commercial things that canonical does that are not OSS (ubuntuOne for instance, or the payfor codecs/dvd players) that cannot be given back to the community. In this sense Cannonical and Ubuntu are differant things. in terms of core os software, pretty much everything but drivers are unencumbered, and available as source. it may not be easy to find, I don't know, but it's prolly out there. 
ubuntu also takes packaging further than many distros, and as a result has a lot of dependencies. if you want to use one component, but not another, then it may be harder to get the code to work correctly.

---

### Post by Screwdriver0815 on 2009-07-18
> **JDShu said:**
> As far as I know, since its open sources, Ubuntu can't just hide anything. Also, Ubuntu has submitted patches to the linux kernel, though the small number of these patches has been criticized.

in the comments I mentioned, the people say: "Ubuntu uses the stuff and of course because Ubuntu is licensed under the GPL it is legal what they do. But they do not deliver their patches to the original developers who have designed the base programs. So this means a not-delivered patch is a patch which does not exist"

To me this means that all the developers of the software are waiting for patches. And they get patches from all the distros. And Ubuntu puts them into their Distro and maybe puts them into Launchpad. But as the developer waits on his mailbox he does not get an e-mail from Ubuntu with the patch... 

and this is the reason to critisise... while I am not really sure, if the developer also really gets mails from Gentoo, Arch, Suse, Red Hat, all these 1-man-distros...?

for me it is not, as the developer could have a look either into Ubuntu or into Launchpad if he really needs a Ubuntu-patch... :confused:

So, I am still confused. Is Ubuntu just leeching?

---

### Post by ibutho on 2009-07-18
The main criticism I have seen about Ubuntu and Canonical in general is they do not contribute as much as others and sometimes its difficult to get patches from them. Another criticism is that some of Canonicals own projects are closed source whilst companies like Red Hat, opensource most of their applications/projects.

---

### Post by castrojo on 2009-07-18
> **Screwdriver0815 said:**
> in the comments I mentioned, the people say: "Ubuntu uses the stuff and of course because Ubuntu is licensed under the GPL it is legal what they do. But they do not deliver their patches to the original developers who have designed the base programs. So this means a not-delivered patch is a patch which does not exist"

Patches made to debian are available here: [http://patches.ubuntu.com/](http://patches.ubuntu.com/)
This usually includes any patches we are carrying to upstream. Patches are sent to upstreams all the time. All changes to the vanilla kernel are maintained at [http://kernel.ubuntu.com/git](http://kernel.ubuntu.com/git)

Can you ask the people in those forums what specific patches they are talking about? If there are patches that Ubuntu is carrying that should be upstream they can reach me directly at jorge (at) ubuntu.com

---

### Post by danbuter on 2009-07-18
The whole point of a distribution is to package all of the various programs into one usable package. Ubuntu does that exceedingly well. There is no requirement to submit _anything_ to anyone in the GPL. IMO, the best thing Ubuntu contributes to Linux is marketing, which most of the other companies pretty much suck at.

---

### Post by Screwdriver0815 on 2009-07-18
> **ibutho said:**
> The main criticism I have seen about Ubuntu and Canonical in general is they do not contribute as much as others and sometimes its difficult to get patches from them. Another criticism is that some of Canonicals own projects are closed source whilst companies like Red Hat, opensource most of their applications/projects.

okay... Canonical has 122 or maybe 200 employees... Red Hat 2800... and Novell has 4100...

but even when they calculate it as "patch per employee" this does not mean anything because all the other Linux companies are much older and actually "own" more programs. So if you want to add a patch you must know about all the technical stuff. This is done easier when you know the program from the base on.

Launchpad is or will be open source soon
and all the other stuff is open source, except the Ubuntu ONE.

So I don't know, why this is wrong?

If I would develop something, I am free to chose the license, right? Or not? 
If others open source their stuff, they do it also because they want to get improvements by users. I don't think that they just open-source their stuff because they are so generous.

But I want to bring the discussion back to the software-part. 

When I have a Ubuntu with all the stuff in it, which is delivered with Ubuntu:
are all the parts of the system, lets say, patched from Ubuntu? And when I take for example a Debian testing: will there be absolutely no Ubuntu-code in there? Because the Debian guys don't get the code because it is too difficult to get it? So is then maybe the Ubuntu-stuff better and the Debian testing could be better if they would get the code out of Ubuntu?
What do the other distro's better in this case? I as a user can get a Launchpad account really easy. When I search at Red Hat or Mandiva for a similar database or something which tracks code, I just don't find anything.
So what is easier in the Red Hat or Mandriva system?

---

### Post by Screwdriver0815 on 2009-07-18
> **whiprush said:**
> Patches made to debian are available here: [http://patches.ubuntu.com/](http://patches.ubuntu.com/)
This usually includes any patches we are carrying to upstream. Patches are sent to upstreams all the time. All changes to the vanilla kernel are maintained at [http://kernel.ubuntu.com/git](http://kernel.ubuntu.com/git)

Can you ask the people in those forums what specific patches they are talking about? If there are patches that Ubuntu is carrying that should be upstream they can reach me directly at jorge (at) ubuntu.com

the discussion was basically about the gnome power manager. But as I am no developer I don't have any clue...

The problem is that all the time, when this discussion comes up and some really serious and deeper questions like "can you please explain?" "could you please give an example?" are asked, the discussion has ended because I don't get any answers on these questions.

This also the reason why I have started this thread. Because all these statements are confusing me and I also feel that sometimes Ubuntu is treated really unfair.

But I would like to quote your post in the next discussion (which will come up for sure), if this is okay for you?

---

### Post by 23meg on 2009-07-18
> **Screwdriver0815 said:**
> 
To me this means that all the developers of the software are waiting for patches. And they get patches from all the distros. And Ubuntu puts them into their Distro and maybe puts them into Launchpad. But as the developer waits on his mailbox he does not get an e-mail from Ubuntu with the patch... 

and this is the reason to critisise... while I am not really sure, if the developer also really gets mails from Gentoo, Arch, Suse, Red Hat, all these 1-man-distros...?

for me it is not, as the developer could have a look either into Ubuntu or into Launchpad if he really needs a Ubuntu-patch... :confused:

So, I am still confused. Is Ubuntu just leeching?

The problem here is that we have to work with literally thousands of upstreams, and each have their own habits and preferences regarding how they'd like to get patches, if at all, and different levels of proximity to us. Some only want them in their bug tracker, some want them in their mailing list, some by personal mail, whereas some will eagerly pursue the Ubuntu bug tracker at Launchpad for patches. Accommodating everyone's workflows perfectly is difficult, and takes time to get right.

Ubuntu is a relatively young project, and especially in the early days, there have been some blunders regarding bug triage and patch workflows. The bad press around those *real* issues did get mixed up with lots of non-issues made up by people whose main motivation was to make a fuss, and resulted in a somewhat foul reputation for Ubuntu. But pretty much everyone who has a stake in them will agree these days that those issues have been sorted out, and the issues we continue to have don't have any greater significance than those of any other major distribution.

[QUOTE=Screwdriver0815]
When I have a Ubuntu with all the stuff in it, which is delivered with Ubuntu:
are all the parts of the system, lets say, patched from Ubuntu? [/QUOTE]

No, only the parts that absolutely need to be patched are. We try to stay as close to upstream as possible. That not only makes things better for upstream and other distributions, but makes it easier for us to maintain things as well.

[QUOTE=Screwdriver0815]And when I take for example a Debian testing: will there be absolutely no Ubuntu-code in there?[/QUOTE]

There will most certainly be Ubuntu patches there, as well as patches from lots of other distributions. The same is valid for every other distribution. 

[QUOTE=Screwdriver0815]Because the Debian guys don't get the code because it is too difficult to get it? So is then maybe the Ubuntu-stuff better and the Debian testing could be better if they would get the code out of Ubuntu?[/QUOTE]

Sometimes Debian people can refuse to get the patches (which they're absolutely entitled to), and historically, yes, it's been somewhat difficult to get patches for some components as well, but that's no longer the case.

[QUOTE=Screwdriver0815]What do the other distro's better in this case?[/QUOTE]

It's hard to tell, and it's pretty subjective.

[QUOTE=Screwdriver0815]the discussion was basically about the gnome power manager. But as I am no developer I don't have any clue...[/QUOTE]

It's probably this: [http://hughsient.livejournal.com/46484.html](http://hughsient.livejournal.com/46484.html)
Which resulted in this: [http://blogs.gnome.org/hughsie/2007/11/14/ubuntu-and-gnome-power-manager/](http://blogs.gnome.org/hughsie/2007/11/14/ubuntu-and-gnome-power-manager/)

[QUOTE=Screwdriver0815]
The problem is that all the time, when this discussion comes up and some really serious and deeper questions like "can you please explain?" "could you please give an example?" are asked, the discussion has ended because I don't get any answers on these questions.[/QUOTE]

That usually is a sign that people are simply reiterating hearsay, rather than forming an opinion based on any real evidence, which tends to happen a lot on web forums, and makes it impossible to have a proper discussion.

---

### Post by castrojo on 2009-07-18
> **Screwdriver0815 said:**
> the discussion was basically about the gnome power manager. But as I am no developer I don't have any clue...

In the past there have been problems with this, which Richard talked to me about and as far as I know we've gotten alot better about this. Again, if this is a problem then someone needs to tell me exactly which patches need to be sent upstream.

> The problem is that all the time, when this discussion comes up and some really serious and deeper questions like "can you please explain?" "could you please give an example?" are asked, the discussion has ended because I don't get any answers on these questions.

Yes, this happens alot. The way to "fix" this is not to talk to random people on forums, but rather to the upstream themselves.

> This also the reason why I have started this thread. Because all these statements are confusing me and I also feel that sometimes Ubuntu is treated really unfair.

Sometimes. And sometimes someone isn't sending patches. 

> But I would like to quote your post in the next discussion (which will come up for sure), if this is okay for you?

Sure, I'm not really interested in who wins the argument though, just which patches upstream feels they're not getting exposure to.

---

### Post by bodhi.zazen on 2009-07-19
Thank you whiprush and 23meg for taking the time to write such well thought out responses on this thread.  It is much appreciated when developers take the time to answer some of these questions directly.

---

### Post by Screwdriver0815 on 2009-07-20
> **bodhi.zazen said:**
> Thank you whiprush and 23meg for taking the time to write such well thought out responses on this thread.  It is much appreciated when developers take the time to answer some of these questions directly.

i want to do the same. Thank you very much, whiprush and 23meg for presenting your views and for clearification in this.

I also appreciate your posts very much.

---

### Post by drkages on 2009-07-20
> **Screwdriver0815 said:**
> 
If I would develop something, I am free to chose the license, right? Or not? 
If others open source their stuff, they do it also because they want to get improvements by users. I don't think that they just open-source their stuff because they are so generous.



Firstly:

I agree with you that developers are free to choose the license, however I disagree with you, that there are developers that release their applications not simply for the sake of improvements, but some developers may genuinely feel generous in the distribution of their code, in the hope that someone else will find it useful as they have, and for the holistic development of applications and IT across the world.

Secondly:
I know this is different that the line of discussion before, but in the topic of giving back. I wanted to know the extent that distros like Ubuntu and Fedora and Cooperations like Canicol and Red hat give back, by helping or providing platforms for younger developers to participate. For example I know that MS gives suites such as Visual Studio at a drastically discounted rate, and often fund research projects out of University from all parts of the world....

---

