---
title: "What is your opinion about CentOS ?"
date: 2020-12-09
forum: Ubuntu, Linux and OS Chat
---

### Post by linuxyogi on 2020-12-09
I have never used CentOS. I like the very long support time but I have heard that the default repos are not that large in comparison to Debian/Ubuntu & to install stuff like VLC & other multimedia apps it becomes necessary to add additional repos. Is that true ? What is your opinion about CentOS as a desktop distro ?

This is my WiFi

```
$ inxi -Nn
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet driver: r8169 
           IF: enp2s0 state: down mac: 60:45:cb:87:53:a5 
           Device-2: Ralink MT7601U Wireless Adapter type: USB driver: mt7601u 
           IF: wlx0e4b880019ac state: up mac: 0e:4b:88:00:19:ac 


```

I searched & found that it is not supported out of the box. So that's another downside.

---

### Post by mIk3_08 on 2020-12-09
I prefer this is best for sever even Ubuntu and etc. as long that it is Linux. It is best to Serve.

---

### Post by Frogs Hair on 2020-12-09
This may be of interest to users and potential users of Cent OS. 

[https://blog.centos.org/2020/12/future-is-centos-stream/](https://blog.centos.org/2020/12/future-is-centos-stream/)

---

### Post by SeijiSensei on 2020-12-09
I began using RedHat on servers and later migrated to CentOS. The change in direction of the CentOS team described in the link Frog's Hair cites above has started me thinking that I might move to Ubuntu Server.

---

### Post by EuclideanCoffee on 2020-12-09
I'm a CentOS user who moved to Debian. Ubuntu for my personal workstation. I dislike the IBM influence. I use RHEL at work everyday however. If you are looking for corporate American experience, that is where you go.

---

### Post by mastablasta on 2020-12-10
> **linuxyogi said:**
> I have never used CentOS. I like the very long support time but I have heard that the default repos are not that large in comparison to Debian/Ubuntu & to install stuff like VLC & other multimedia apps it becomes necessary to add additional repos. Is that true ? What is your opinion about CentOS as a desktop distro ?

This is my WiFi

```
$ inxi -Nn
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet driver: r8169 
           IF: enp2s0 state: down mac: 60:45:cb:87:53:a5 
           Device-2: Ralink MT7601U Wireless Adapter type: USB driver: mt7601u 
           IF: wlx0e4b880019ac state: up mac: 0e:4b:88:00:19:ac 


```

I searched & found that it is not supported out of the box. So that's another downside.

you add a repo and install a module. same as you might need to in Ubuntu. dkms will take care of kernel updates. the only downside is the kernel is then"tainted" so secure boot has to be off.

A mentioned here
> **Frogs Hair said:**
> This may be of interest to users and potential users of Cent OS. 
[https://blog.centos.org/2020/12/future-is-centos-stream/](https://blog.centos.org/2020/12/future-is-centos-stream/)

you can now forget about long term support as they just dropped it.
i always thought this was a community build from source code with all Red Hat branding removed.

---

### Post by grahammechanical on 2020-12-10
As a home user I have a question or two.

Why would a commercial enterprise use CentOS? Because the owners of the enterprise do not want to pay the Red Hat fees?

Would IT department administrators recommend running a commercial enterprise on a server OS that was a development release?

As I understand it CentOS 8 is a stable release and CentOS Stream is a development release. It also seems to me that the future of any commercial enterprise running CentOS is to become a production environment tester for Red Hat at their own expense and own liability.

Am I right in thinking that from now on any community developed distribution of Linux that accepts developers who are Red Hat employees runs the risk of being absorbed/taken over by Red Hat?

Regards

---

### Post by Frogs Hair on 2020-12-10
> Am I right in thinking that from now on any community developed  distribution of Linux that accepts developers who are Red Hat employees  runs the risk of being absorbed/taken over by Red Hat?

It certainly sounds that way in the linked blog.

> CentOS Stream continues after that date, serving as the upstream (development) branch of Red Hat Enterprise Linux. Upstream doesn't sound  like it's a  community maintained project.

---

### Post by DuckHook on 2020-12-10
I'm saddened that the sense of *community* in so many distros is being strangled to death as big companies buy the platform and then reflexively apply their proprietary fixations on their shiny new FOSS "asset".

When Redhat assimilated CentOS and then in turn were assimilated by IBM, this was a preordained outcome. I don't know whether "resistance is futile", but the Borg parallel is by equal measures scary, depressing and accurate.

I suppose we should expect an influx of CentOS refugees interested in giving Ubuntu's tires a few kicks now.

---

### Post by grahammechanical on 2020-12-10
This discussion has got me thinking. I do not think that Mark shuttleworth will sell Canonical out of greedy desire for more millions. I have in mind some businesses that were founded by an individual, listed on the stock market and at some point the board of directors pushed out the founder and then the board arranged a merger/sell out that let them take away millions of dollars/pounds.

Without independent Linux server operating systems Linux itself could be superseded by corporate developed code. An old generation of IBM bosses let Microsoft run off with the PC operating system. Is a new generation of IBM bosses scheming to assimilate the server operating system by making Linux irrelevant? Is Android dependent on Linux kernel development? Or is Android an independently developed offshoot of Linux?

It was not my intention to take this thread off topic. I regret the direction my thoughts have moved in. Sorry.

Regards

---

### Post by guiverc on 2020-12-11
I use CentOS on a server, I liked the long (10 year) supported life.  **
(it had a feature that Debian didn't have; a feature I've never used; I wish I'd used Debian though; mainly as I know it better)

As a desktop, it's rather old software wise in my opinion, and I'd like use something else (a Ubuntu or Debian).  Almost anything that can be made to work in another GNU/Linux, can be made to work in CentOS or any other GNU/Linux, however I find Debian & Ubuntu easier to deal with.  (so I'd return to age of software).

For a desktop, Ubuntu (or *flavors*) would likely be my choice, Debian a close second.


** *I'd used only the older releases of CentOS, and hadn't noticed if I upgrade it's got a shorter life!!   That may mean newer software, but it removes what I liked about CentOS*

---

### Post by linuxyogi on 2020-12-12
> **mastablasta said:**
> you add a repo and install a module. same as you might need to in Ubuntu. dkms will take care of kernel updates. the only downside is the kernel is then"tainted" so secure boot has to be off. 

I never needed to do anything in Ubuntu or Mint or Arch to get my wifi hardware to work. I went to the CentOS IRC channel some months back & they told me that my wifi hardware is not supported out of the box.

> **mastablasta said:**
>  you can now forget about long term support as they just dropped it. 

In that case there is absolutely no reason left (for me) to install CentOS.

---

### Post by DuckHook on 2020-12-12
> **grahammechanical said:**
> Is a new generation of IBM bosses scheming to assimilate the server operating system by making Linux irrelevant?
I don't think they are scheming so much as fumbling. My time among the executive crowd affirms—for me at least—that the mind&#8209;set and culture of proprietary space is one of secrecy, ownership, locked doors and closed thinking. This works for proprietary stuff. In fact, it is necessary. Coke's or KFC's existence depends on their "secret" recipes. Without trademarks, copyrights, patents and other "owned" intellectual products, companies from Apple to Microsoft to Disney would cease to be. However, their creed is the very antithesis of the FOSS principles that underlie the Linux ecosystem.

So, what happens when this closed proprietary universe gains control of a FOSS asset? Despite their best intentions (and some of them have actually noble intentions) they haven't a clue what to do. Their proprietary mindset—the one that got them their S&P 500 status—is so at odds with the mindset needed for the FOSS world that they cannot make the needed leap of imagination. How does one make money with something that keeps no secrets, has no owner, cannot be locked down and demands complete transparency?

The problem with IBM owning Redhat (and by extension CentOS) is that they cannot help but impose their corporate culture onto their new "asset". There's nothing inherently toxic about IBM's corporate culture. They are a decent company that makes useful products. Their culture is only toxic when applied to FOSS. And they do not and can not ever understand that dynamic.
> Is Android dependent on Linux kernel development? Or is Android an independently developed offshoot of Linux?
A bit of both, but more the latter. And as time goes on, it becomes ever more the 800 lb gorilla of offshoots. Google is a special case of proprietary thinking. Unlike IBM, Google actually does get what FOSS is all about. Google is probably the single biggest corporate contributor to the Linux kernel. Unlike the suits at IBM, it understands the geek world better than anyone because it grew out of that world. In fact, it understands it so well that it knows how to leverage FOSS to further its own very self&#8209;interested ends.

Had Google bought CentOS, it would have kept the CentOS culture in place and then milked it for all it was worth. In fact, it would have discovered ways to milk it that no one had ever conceived. And that happens only if you understand the culture well enough to work with it rather than against it.

---

### Post by #&amp;thj^% on 2020-12-12
> **DuckHook said:**
> I don't think they are scheming so much as fumbling. My time among the executive crowd affirms&#8212;for me at least&#8212;that the mind&#8209;set and culture of proprietary space is one of secrecy, ownership, locked doors and closed thinking. 
 it becomes ever more the 800 lb gorilla of offshoots. Google is a special case of proprietary thinking. Unlike IBM, Google actually does get what FOSS is all about. Google is probably the single biggest corporate contributor to the Linux kernel. Unlike the suits at IBM, it understands the geek world better than anyone because it grew out of that world. **_In fact, it understands it so well that it knows how to leverage FOSS to further its own very self&#8209;interested ends._**

Had Google bought CentOS, it would have kept the CentOS culture in place and then milked it for all it was worth. In fact, it would have discovered ways to milk it that no one had ever conceived. And that happens only if you understand the culture well enough to work with it rather than against it.
Sadly this is where my heart breaks personally.
Truthfully "It's business."
Thanks DuckHook I always get a good take away from your well placed thoughts. ;)

---

### Post by DuckHook on 2020-12-12
> **1fallen said:**
> Sadly this is where my heart breaks personally.
Truthfully "It's business."
Though I understand where you are coming from and sympathize with your feelings, I wouldn't say that I find it heartbreaking. As mentioned, I come from that world. It was very good to me. I imagine that most forum members derive worldly income and sustenance from that self&#8209;same proprietary world, so I have no problem with any company leveraging FOSS *provided they leave FOSS well enough alone*.

The problem arises when the proprietary model cannot resist the temptation to meddle. When IBM buys something like CentOS, they take the culture that has made *them* (IBM) successful and try to shoehorn it onto this ideological opposite—this oddball creature that they suddenly now control. This usually means destructive strategies like embrace&#8209;extend&#8209;extinguish, or feature creep, or subverting its open source nature by adding increasingly restrictive closed source add&#8209;ons (Virtualbox's extension pack comes to mind and was one of the major reasons that I switched from Vbox to KVM), or, as IBM has done, twist it into something contrary to its nature.

In the world of platforms and Distros, an asset is never just an object. It comes with a lot of intangibles: its own culture comprised of creeds, norms, traditions, a history and, most of all, a community of developers, users and enthusiasts. Unlike the proprietary world, this community is amorphous, shifting and hard to pin down. Their loyalties cannot be bought. They can only be earned through a demonstrated commitment to those intangibles. IBM is fumbling CentOS because they are treating it simply as an object and does not understand those intangibles.

This is not something that we need worry about with Google.

It's not Google's exploitation of Linux that concerns me. Linux exists to be exploited. After all, you and I are doing that right now. No… in fact, I'm so sure that Google recognizes the immense value of Linux's contribution to their continuing supremacy that they will continue to support its development and the greater FOSS ecosystem. As mentioned, unlike IBM, Google really gets the value of FOSS—not least because it doesn't make its money from selling OSes, so it doesn't look upon FOSS as any sort of threat.

With Google, it's other things that we need to worry about. But that would be a real hijack of this thread and off topic.

---

### Post by #&amp;thj^% on 2020-12-12
Whoops, may have misunderstood me. and your reply is spot on in both our views.
Please tell me where I de-railed, I would like to correct that in the future.

---

### Post by DuckHook on 2020-12-12
> **1fallen said:**
> …Please tell me where I de-railed…
:-s
No de&#8209;railing here as far as I'm concerned. Just an interesting exchange. Everything A-Okay.

---

### Post by zebra2 on 2020-12-12
> **DuckHook said:**
> so I have no problem with any company leveraging FOSS *provided they leave FOSS well enough alone*.

I use to replace the MSDOS on my computer back in the 80's and 90's with a copy of DR DOS. Dr Dos always seemed to be a step ahead of MS Dos. The two along side of each other kind of stole each others ideas into the early 2000's. At some point DR DOS was acquired by Caldera which also had a proprietary linux release Caldera Linux. Caldera later became SCO Linux. SCO also proprietary started a big lawsuit regarding the argument as to who owned UNIX. SCO, IBM, Novell, and even Microsoft became part of the suit. In the end and after a few years of litigation all of these parties including Microsoft had to give up ownership of various patents. There was only one winner in the whole conundrum, LINUX.  Even though linux wasn't a party to the lawsuit the court ruled that linux wasn't an infringement on unix patents due to the fact that it was non proprietary FOSS and GPL compliant. In addition I will myself add that Linux is "Unix like" but not Unix compliant. The court drilled into the core of Linux and determined that is was a legit OS and free of patent violations.   

Hence the quote at the beginning of this post gets a great big +1.  I kind of understand some of the FOSS militancy often found here , it is a core concept..  Great thread here, Thanks.

PS: What is my opinion of CentOS, actually, none.

---

### Post by DuckHook on 2020-12-13
> **zebra2 said:**
> …SCO also proprietary started a big lawsuit regarding the argument as to who owned UNIX…
SCO's demise was good riddance. I don't usually indulge in schadenfreude over the death of an enterprise, but SCO had degenerated into nothing more than a patent troll. Its lawsuit was just a last gasp Hail Mary extortion play to cover up its own business ineptitude and gross incompetence. The only sad part in that ordeal was the suffering of the good people who got caught up in the backwash of SCO's wreckage.

---

### Post by mastablasta on 2020-12-14
Rocky linux is being setup as alternative and in same way as the old CentOS was (but hopefully without the delays in patches and updates). project is still in early stage so we have to wait and see what will come out of it.

10 years of support (at least with only security patches) is good for older machines.

---

### Post by kevdog on 2020-12-14
I don't work in the corporate tech world -- far from it.  Other than the attitude of "this is the way it is and we've always used it", it seems like a great excuse to move away toward something Debian based.  How hard of transition would that be?

---

### Post by DuckHook on 2020-12-14
> **kevdog said:**
> …How hard of transition would that be?
So many factors. Here are just some:

[LIST]
[*]How central is CentOS to the enterprise?
[*]How many rigs are using it?
[*]How mission&#8209;critical are those rigs?
[*]How many human hours would be involved in not only migrating, but relearning Linux the Debian way vs the RHEL way?
[*]How exposed would the enterprise be while all of this relearning is taking place?
[*]What is the likelihood of serious errors being introduced by the migration itself? (Some systems have so much customization that simply documenting it is both a chore and a risk.)
[*]What functional holes exist in Debian that don't exist (or are easily handled) in RHEL?
[*]But most of all, "why are we being forced into a huge migration just because IBM has decided to divorce an entire community?" It is open source after all, isn't it? One of the biggest points of FOSS is that it can be forked any time, to forestall exactly this sort of dereliction.
[/LIST]
It could be excruciating.

---

### Post by mastablasta on 2020-12-15
> **DuckHook said:**
> 
[LIST]
[*]But most of all, "why are we being forced into a huge migration just because IBM has decided to divorce an entire community?" It is open source after all, isn't it? One of the biggest points of FOSS is that it can be forked any time, to forestall exactly this sort of dereliction.
[/LIST]


fork is the most logical path.

i hope they can make it. i have old Nvidia GPU that could benefit from 10 year support on stable kernel & drivers. if nothing else, i could add a couple of controlers, connect it to TV and make steam/Play on linux box out of it. it seems such a waste to throw away working hardware.

---

### Post by DuckHook on 2020-12-15
> **mastablasta said:**
> fork is the most logical path.

i hope they can make it.
I do too. Thanks for pointing us to the glimmerings of the start of that fork. For the curious, here's a link to Rocky Linux that mastablasta had alluded to earlier: [https://rockylinux.org/](https://rockylinux.org/)

Not much there yet, but do keep in mind that the distro has just been conceived.

One more philosophical broadside and then I'll give it a rest:

Frankly, it flabbergasts me how much big companies are both tone deaf to and ignorant of the communities that support their "assets". IBM in particular is a company that is mono-maniacally focused on their big corporate customers and utterly oblivious to the larger reality around them. Consider:

[list=1]
[*]They buy an asset (CentOS), but then abandon its roots, its creeds, its traditions, its very raison d'être.
[*]In doing so, they perforce also abandon its huge community of enthusiasts, users and (most importantly for IBM) devs.
[*]This means that they have, in effect, hollowed out all value from this asset that they paid so much for.
[*]The only thing left is its name: "CentOS". So they paid… what?… some ridiculous coin for the right to use a name.
[*]Meanwhile, the community that made that name worth something picks itself up after being so flippantly abandoned and coalesces around a new fork. The new fork takes on most of the value that the old asset used to have.
[/list]
Just what has IBM managed to achieve? Why do they keep reaching into their hat and pulling out such skunks?

They pulled something similar with their original runaway success, the IBM PC.

They pulled another one with what was arguably the best consumer OS of its time, OS/2.

When it comes to dealing with us common folk, they seem hell bent on shooting themselves in the foot.

---

### Post by Shibblet on 2020-12-16
I could be wrong... but didn't IBM purchase RedHat in 2018?  Do you think they had anything to do with dropping CentOS?

---

### Post by DuckHook on 2020-12-16
> **Shibblet said:**
> I could be wrong... but didn't IBM purchase RedHat in 2018?  Do you think they had anything to do with dropping CentOS?
Of course no one has reports from the inner sanctum of the management group, but it's almost certainly an IBM decision. Unless things have changed dramatically from when I was dealing with them, Big Blue is an obsessively monolithic organization. The Red Hat holdovers would have little say over things like "assets". If Big Blue has changed, it would be in things like letting devs work in T-shirts and hang surfboards over their desks. But when it comes to anything to do with assets, this would continue to be the exclusive domain of the suits.

---

### Post by Shibblet on 2020-12-17
> **DuckHook said:**
> Of course no one has reports from the inner sanctum of the management group, but it's almost certainly an IBM decision. Unless things have changed dramatically from when I was dealing with them, Big Blue is an obsessively monolithic organization. The Red Hat holdovers would have little say over things like "assets". If Big Blue has changed, it would be in things like letting devs work in T-shirts and hang surfboards over their desks. But when it comes to anything to do with assets, this would continue to be the exclusive domain of the suits.

I've never head to deal with IBM directly.  I have noticed though, that most companies have shown that it benefits their own interests to contribute to Free and Open Source projects.  Google helped pioneer the Chromium project, which has produced many different Web Browsers over the years, including now, Microsoft's Edge.

I mean, Canonical itself is more of a "tech-support" company (for lack of a better term).  They make their money in professional software support.  They also contribute to MANY different Open Source projects such as Snaps and Launchpad (PPA's).  Whether or not we like these services (I'm not big into Snaps yet), they do offer assistance to the entire Linux community.

Canonical even tried changing up the formula too with ideas like Unity and Mir.  Both of which may not have stayed around too long, but were great ideas, and forward thinking.  Again, whether or not we like these ideas, they contribute a lot to the Linux community.

I guess what I am getting at, is that IBM may have just shot themselves in the foot.

---

### Post by DuckHook on 2020-12-17
Wow. A world of thoughts to unpack here. Many are not aware of this, but IBM makes significant contributions to the Linux kernel. I assume they make similar contributions to other FOSS projects, but I'm less sure of this.

They do this out of enlightened self interest. IBM realizes that by supporting Linux, they get the benefit of a resource that is orders of magnitude more valuable than the resources they put in. If they make no contribution, then the health of this goose is imperilled. No more golden eggs. So they do their part to feed the goose. They get to bask a little in the reflected glory too, which is always valuable to any company that wants to burnish its image.

Their problem with CentOS is that it doesn't feel valuable. If anything, it feels like a parasite. On a perfunctory level, it appears to draw potential users away from their revenue generator: RHEL. Why pay for Red Hat if you can install a free version? Solution: get rid of the free version. It's a really dumb and shortsighted thought process, but that's the way a suit thinks.

So what will happen? Here's a thread posted just now on our very own forums from a CentOS refugee: [CentOS Transplant]("https://ubuntuforums.org/showthread.php?t=2455350") (I hope the OP doesn't mind my using him as a reference). This is going to happen in droves. Instead of driving their CentOS users to RHEL, those poor souls will move to Debian/Ubuntu, or Arch, or Gentoo, or Slack. And they will have a very foul taste in their mouths for IBM.

Organizations like IBM simply have no feeling for the value of a community. They don't get the fact that although CentOS users may not be feeding their bottom line directly, those users have a ton of ***indirect*** influence over things like the *popularity* of RHEL, eventual adoption of paid Red Hat support as the enterprise grows, introduction of budding devs and new enthusiasts to the RHEL ecosystem, mind&#8209;share, cachet, reputation and, not least, the awesome benefits derived from sheer genius.

An example of the latter is CERN. There's no assembly of expertise more frighteningly lofty than the collective geniuses at CERN. They discover new matter by smashing subatomic particles together at almost&#8209;luminal velocities for crying out loud. They also run on CentOS. Presumably, they are so tech savvy that they know more about Linux than IBM. Certainly, they feel no need for paid support. But in return for the use of a "free" OS, they churn out innovations in apps, services, cluster tech, cloud tech, supercomputing tech etc etc that dwarf what they would pay in services. IBM derives *immense* value from these innovations, but they can't wrap their heads around the simple fact that such derivation is due in part to the communal nature of CentOS.

Google doesn't think that way. Google gets the above concept in spades. You would never see Google neutralizing a large and vibrant FOSS community because it wasn't contributing to the immediate bottom line, or because Google got tired of supporting that non&#8209;paying community.

I'd love to see CERN now move to Ubuntu. But it's more likely that a collection of such tech&#8209;heads will choose Arch.

So yes, I too think IBM have shot themselves in the foot (yet again!). I've given up expecting them to understand or appreciate mass markets or alien concepts like "communities". They just can't seem to get their heads wrapped around anything to do the hoi polloi.

---

### Post by Chanath on 2020-12-18
Why should anyone be worried about what happens to CentOS, especially here?

---

### Post by kc1di on 2020-12-18
My opinion is that it was a good server OS used by many- It will force some corps to get paid support for RHEl or find an alternative.  But as Chanath said why are we worried about it here.
Some may even migrate to Ubuntu :)

---

### Post by QIII on 2020-12-18
> **Chanath said:**
> Why should anyone be worried about what happens to CentOS, especially here?

Did we sign some sort of "I will only be interested in Ubuntu" manifesto when we came here?

---

### Post by hrsetrdr on 2020-12-18
> **linuxyogi said:**
> I have never used CentOS. I like the very long support time but I have heard that the default repos are not that large in comparison to Debian/Ubuntu & to install stuff like VLC & other multimedia apps it becomes necessary to add additional repos. Is that true ? What is your opinion about CentOS as a desktop distro ?


I use CentOS from time to time as a desktop OS.    Adding additional repos isn't difficult, just a different system of package management than that of Debian and derivatives.     I did have a problem with their network manager app in one install.    Fedora is more current, but it can be like running Debian Sid, and sometimes things got wrong.    Someone on the Debian forums once said:   "one thing about running Unstable- when it breaks you get to keep the pieces".

---

### Post by DuckHook on 2020-12-18
> **Chanath said:**
> Why should anyone be worried about what happens to CentOS, especially here?
Why? Because we are indirect beneficiaries of CentOS too. In the FOSS world, when ideas get created, they also get shared. A vibrant alternative community contributes to the greater good. It also keeps Canonical on its toes. One of the reasons that Microsoft and Google no longer innovate as keenly as they once did is because they have become quasi monopolies with all of the sclerotic fossilization that accompanies such status. Note how they only come up with new stuff these days by leveraging their massive capital to buy startups. Their in&#8209;house innovation is pretty pathetic.

So reduction of proper alternatives is a danger to Linux. The FOSS community is especially susceptible to the disappearance of proper alternatives. While it is true that we have dozens of tiny distros, these little squirts can't get traction. Single maintainer distros don't constitute real alternatives. They are fragile and undependable for mission-critical use. Example: I used to depend on Crunchbang for some old laptops that I had revitalized for friends. The demise of that distro soured a few of them on Linux in general.

CentOS was a really good cousin to Ubuntu. A 10 year support cycle is a tremendous advantage and just what the doctor ordered for many use cases. Note that Ubuntu LTS only has 5 years of support. You have to pay for more, and it's of questionable reliability because it has such a small user base.

FOSS has a very different dynamic than the proprietary world. Proprietary software behaves as if the market is a zero sum game: Apple can only grow if Microsoft surrenders market share. This is not true, but it doesn't hurt Apple (or Microsoft) to behave that way. But in the FOSS world, it's the opposite. With apologies to Dumas, it's more like "one for all and all for one". The health of each distro contributes to the vibrancy of the larger general community.

The death of CentOS will be painful for all of us.

---

### Post by hrsetrdr on 2020-12-19
> **DuckHook said:**
> Why? Because we are indirect beneficiaries of CentOS too. In the FOSS world, when ideas get created, they also get shared. A vibrant alternative community contributes to the greater good. It also keeps Canonical on its toes. One of the reasons that Microsoft and Google no longer innovate as keenly as they once did is because they have become quasi monopolies with all of the sclerotic fossilization that accompanies such status. Note how they only come up with new stuff these days by leveraging their massive capital to buy startups. Their in&#8209;house innovation is pretty pathetic.

So reduction of proper alternatives is a danger to Linux. The FOSS community is especially susceptible to the disappearance of proper alternatives. While it is true that we have dozens of tiny distros, these little squirts can't get traction. Single maintainer distros don't constitute real alternatives. They are fragile and undependable for mission-critical use. Example: I used to depend on Crunchbang for some old laptops that I had revitalized for friends. The demise of that distro soured a few of them on Linux in general.

CentOS was a really good cousin to Ubuntu. A 10 year support cycle is a tremendous advantage and just what the doctor ordered for many use cases. Note that Ubuntu LTS only has 5 years of support. You have to pay for more, and it's of questionable reliability because it has such a small user base.

FOSS has a very different dynamic than the proprietary world. Proprietary software behaves as if the market is a zero sum game: Apple can only grow if Microsoft surrenders market share. This is not true, but it doesn't hurt Apple (or Microsoft) to behave that way. But in the FOSS world, it's the opposite. With apologies to Dumas, it's more like "one for all and all for one". The health of each distro contributes to the vibrancy of the larger general community.

The death of CentOS will be painful for all of us.

I found the "Like" button on this forum.     

   [ATTACH=CONFIG]287581[/ATTACH]

---

### Post by Chanath on 2020-12-20
> **DuckHook said:**
> 

The death of CentOS will be painful for all of us.

Well, CentOS isn't dead, only it became CentOS Stream. You can use the existing CentOS until 31st December 2021. Or, you can transfer your existing CentOS to [CentOS Stream]("https://www.centos.org/centos-stream/"), and it never becomes EOL. OpenSuse Tumbleweed also never becomes EOL. They are not that unstable. I use OpenSuse Tumbleweed, so I know.
Ubuntu development release only stops for few weeks, until a new repo name is finalised.

---

### Post by grahammechanical on 2020-12-20
And there I was thinking that I had taken this thread off topic!

One reason why we are discussing CentOS here is that sometimes we like a good discussion. We get different points of view. It is a way of keeping the forum active.

Regards

---

### Post by mastablasta on 2020-12-21
> **Chanath said:**
> They are not that unstable. I use OpenSuse Tumbleweed, so I know.


stable means that packages stay the same. you get only security patches, but to same package version. so Tumbleweed and stream are in fact very unstable.

there are apps other apps out there that you need to first test them out, see if everything works, and only then do the upgrade. the upgrades usually take about 6 months to complete. depends on the changes and how testing goes. we are  for example we are just doing major ERP upgrade which will take us about 4 months. for PC OS we use windows 10 business and they don't get any OS upgrades for couple of years (mine is i believe 2 or 3 years old and even that one was pushed by me). before the first upgrade is due things need to be tested first. also before applying updates that are automatically pushed to home users, they test them. so even if we get only security patches they are often delayed for us (unless they are urgent).

that's normal. we are medium sized company and have 6000+ PC. you don't want any to fail. or cause some chain issue. when you are at home, you get an issue, search the web and maybe within same or next day you are able to find a solution. if you are a company you can't afford to loose minutes.  7 years ago they calculated that for every hour we have some sort of a downtime we lose about 300.000 EUR. based on income now this has more than doubled.

my point is stable is what businesses need. and many uses CentOS to test before moving to Redhat. you can't test 4 month only to find that in the mean time packages you were testing against changed 7 times.  many also used it as go to software for servers. especially smaller companies.

---

### Post by DuckHook on 2020-12-21
> **Chanath said:**
> Well, CentOS isn't dead, only it became CentOS Stream.
If not technically dead, then certainly undead. What's left will be an animated corpse—a zombie. It would be no different than if Canonical decided to stop issuing LTS and just stuck to Standard releases. I would leave. So would most others… in droves. As I already stated:
> **DuckHook said:**
> A 10 year support cycle is a tremendous advantage and just what the doctor ordered for many use cases.

---

### Post by DuckHook on 2021-03-30
Welcome new development on this issue: [https://www.theregister.com/2021/03/30/almalinux_project_issues_first_stable_release/](https://www.theregister.com/2021/03/30/almalinux_project_issues_first_stable_release/)

Not sure the RHEL/IBM flywheels will like it, but phooey on them.

---

### Post by QIII on 2021-03-30
Red Hat's announcement was like a kick in the guts out of the blue.  I had been considering changing one of my web servers to CentOS from Ubuntu.  Sigh.

I hope one of the distros in the article succeeds.

---

### Post by DuckHook on 2021-03-30
> **QIII said:**
> &#8230;I hope one of the distros in the article succeeds.
The chances look good. There's a large pent up demand like yours waiting for such distros.

I know I'm repeating myself, but it's a crying shame that organizations like IBM haven't a clue about the real value of the **community** that is behind their "assets". If they valued this community properly, they could leverage it to mutual benefit rather than alienate it.

But it is what it is (and they are who they are).

---

### Post by mikewhatever on 2021-03-30
I understand the CentOS issue is a big deal for some, so I hope those people won't get too upset, but I couldn't care less.
It is somewhat naive to to expect IBM to pay billions for RH, and then allow CO give it away for free.

---

### Post by DuckHook on 2021-03-30
> **mikewhatever said:**
> …
It is somewhat naive to to expect IBM to pay billions for RH, and then allow CO give it away for free.
Au contraire,

What I think is naïve is IBM expecting RHEL to continue to grow while basically flipping the bird at its community roots. I dont' know if you've read my prior post: [https://ubuntuforums.org/showthread.php?t=2454943&page=3&p=14007830#post14007830](https://ubuntuforums.org/showthread.php?t=2454943&page=3&p=14007830#post14007830)

Linux isn't like the world IBM comes from. Offend the community—offend the dynamic that gives the asset its value in the first place. And, witness what's happening with Rocky and AlmaLinux, they won't be able to suppress that community anyways. So they buy themselves nothing but bad blood with their move. It's foolish, blind and asinine all at the same time. It is the IMB PC and OS/2 all over again. They keep shooting themselves in the foot.

---

### Post by mastablasta on 2021-03-31
> **DuckHook said:**
> 
I know I'm repeating myself, but it's a crying shame that organizations like IBM haven't a clue about the real value of the **community** that is behind their "assets". 

They reduced their own mana. :)

---

