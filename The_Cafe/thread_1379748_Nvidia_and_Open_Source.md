---
title: "Nvidia and Open Source"
date: 2010-01-12
forum: The Cafe
---

### Post by JDShu on 2010-01-12
Hey guys, I've been reading about strategy lately (long commutes are a great motivator for reading) and I was thinking about the open source strategy of NVidia. Here are some of my ideas floating around. Note that I make some assertions here.

ATI's open source strategy for Linux is starting to bear fruit now, and in the near future ATI oss drivers will be on par with Nvidia proprietary drivers on the Linux desktop. In such a situation, ATI gains the edge in the Linux market because although driver quality is most important to Linux users, a fraction of them will like oss drivers over proprietary.

So what does Nvidia do? I think they've considered this already. This is revealed from their attitude towards Nouveau, which is that they're not going to help or hinder it. This decision is a no-brainer, because it keeps Nvidia's open source options open. If and when the ATI oss drivers become functionally equivalent to the Nvidia drivers, the presence of Nouveau allows Nvidia to begin supporting oss drivers at a lower cost than if it didn't exist.

This is not to say that Nvidia would being supporting oss drivers, they're just keeping options open. They are likely to compare the cost of switching to oss drivers and staying with proprietary (maybe they instead pump money into the proprietary drivers and make them super awesome) and go from there. So this would be the cost of releasing documentation vs any possible losses from decreased Nvidia purchases or increased investment in the proprietary drivers.

The conclusion from this is that if you believe that:

- The ATI oss drivers are going to become as good as Nvidia proprietary drivers soon.
- A significant fraction of Linux users care about open source.
- open source drivers for Linux are cheaper for a company to maintain than proprietary drivers.
 
Then you should expect Nvidia to begin offering oss drivers in the near future as well.

There concludes my admittedly naive analysis on what Nvidia's possible oss strategy. Flaws in my reasoning? Lack of understanding somewhere? Plain wrong assumptions? I'd love some input.

---

### Post by Frak on 2010-01-12
Or they'll abandon Linux if they see the market is moving away from them. Seriously? They don't care. Linux isn't a killer market for them.

---

### Post by JDShu on 2010-01-12
> **Frak said:**
> Or they'll abandon Linux if they see the market is moving away from them. Seriously? They don't care. Linux isn't a killer market for them.

I considered that, but they do care enough to make drivers for Linux right now. Granted, I understand that Nvidia Linux drivers share a majority of code with their Windows and Mac drivers. 

Of course, such an outcome would hearten open source enthusiasts... it would be a clear triumph of open source over proprietary.

---

### Post by RiceMonster on 2010-01-12
Hmmm... I think they'll just continue to let nouveau do it's thing, personally. The most I could ever see them doing is releasing the specs, and I don't think that's very likely.

---

### Post by JDShu on 2010-01-12
Yeah, when I said open source strategy, I basically meant releasing specs, which I understand is what ATI did. They might have assigned one or two guys in addition or something, not completely sure.

---

### Post by Frak on 2010-01-12
> **JDShu said:**
> I considered that, but they do care enough to make drivers for Linux right now. Granted, I understand that Nvidia Linux drivers share a majority of code with their Windows and Mac drivers. 

Of course, such an outcome would hearten open source enthusiasts... it would be a clear triumph of open source over proprietary.

The only reason they support it right now is because they had, at one point, a large following of Linux users who exclusively used Nvidia because they had good support for Linux. If that market dwindles, they'll just quit. By quit, I don't mean they'll stop Linux driver development (some commercial users depend on it for workstation uses) but they won't release as often nor shoot for improved releases. Since the codebase between Windows and Linux are largely the same, deployment isn't much of an issue.

As for a "triumph", that would show a flaw in the Open Source model. It can cause proprietary companies to pull out of the market, thus reducing the financial viability of the platform as a whole.

---

### Post by boriskarloffinablender on 2010-01-12
nvidia provide their prop drivers mainly for workstations. they aren't going anywhere soon.

---

### Post by JDShu on 2010-01-12
> **Frak said:**
> The only reason they support it right now is because they had, at one point, a large following of Linux users who exclusively used Nvidia because they had good support for Linux. If that market dwindles, they'll just quit. By quit, I don't mean they'll stop Linux driver development (some commercial users depend on it for workstation uses) but they won't release as often nor shoot for improved releases. Since the codebase between Windows and Linux are largely the same, deployment isn't much of an issue.


Interesting, so what you are saying is that Nvidia has an "all or nothing" approach to the Linux market. This could very well be the case since its so small relative to Windows. I'll ponder this some more. Nvidia clearly wants to keep the Linux market, but perhaps the cost of maintaining control once ATI catches up is not worth it.

> 
As for a "triumph", that would show a flaw in the Open Source model. It can cause proprietary companies to pull out of the market, thus reducing the financial viability of the platform as a whole.

Nice catch, although for the consumer, as we mentioned above, its one or the other anyway so there is little difference.

---

### Post by Frak on 2010-01-12
> **JDShu said:**
> Nice catch, although for the consumer, as we mentioned above, its one or the other anyway so there is little difference.

You just can't call Nvidia if something goes wrong.

---

### Post by blueshiftoverwatch on 2010-01-12
> **Frak said:**
> The only reason they support it right now is because they had, **at one point**, a large following of Linux users who exclusively used Nvidia because they had good support for Linux.
That's still the case. When I was building my computer a few months ago I didn't consider getting an ATI video card for that reason. I know some Linux users are buying ATI's because of how awesome their driver support is predicted to be in the future. But if I'm building a computer I want something that I know works the way it's supposed to right now. Not a promise of something that might possibly work in the future. Especially when that something costs in the area of around $200.

---

### Post by JDShu on 2010-01-12
> **Frak said:**
> You just can't call Nvidia if something goes wrong.

True. We're moving into another level of speculation here, but would it be viable for ATI to provide support for their oss drivers or perhaps an open source company providing paid support?

---

### Post by Frak on 2010-01-12
> **blueshiftoverwatch said:**
> That's still the case. When I was building my computer a few months ago I didn't consider getting an ATI video card for that reason. I know some Linux users are buying ATI's because of how awesome their driver support is predicted to be in the future. But if I'm building a computer I want something that I know works the way it's supposed to right now. Not a promise of something that might possibly work in the future. Especially when that something costs in the area of around $200.

I have an x1600 and a 4850 that **FLY** with the Linux Open Source drivers. It puts the Nvidia drivers to shame.

> **JDShu said:**
> True. We're moving into another level of speculation here, but would it be viable for ATI to provide support for their oss drivers or perhaps an open source company providing paid support?

Since it is a 3rd party software, it introduces an unknown point of failure that could be a financial loss for AMD. They could go over all of the hardware components but not know that the actual cause of the problem is with this rapidly developing driver.

---

### Post by AllRadioisDead on 2010-01-12
You talk about linux as if it actually has a significant market share.

---

### Post by JDShu on 2010-01-12
> **ihermit said:**
> You talk about linux as if it actually has a significant market share.

Its all about cost and benefit. It doesn't matter how significant the market share is as long as either company can profit. Otherwise, why did ATI release the specs? From the goodness of their hearts?

---

### Post by Frak on 2010-01-12
> **JDShu said:**
> Its all about cost and benefit. It doesn't matter how significant the market share is as long as either company can profit. Otherwise, why did ATI release the specs? From the goodness of their hearts?
They didn't want to maintain a Linux port. Releasing the specs saved them money. Nvidia only does it because they don't need to radically change the codebase to support Linux. An entire Linux division costs a lot, a LOT, of money to keep up.

---

### Post by boriskarloffinablender on 2010-01-12
> **JDShu said:**
> Its all about cost and benefit. It doesn't matter how significant the market share is as long as either company can profit. Otherwise, why did ATI release the specs? From the goodness of their hearts?

all the bad press about their prop driver probably helped motivate them.

---

### Post by Frak on 2010-01-12
> **boriskarloffinablender said:**
> all the bad press about their prop driver probably helped motivate them.
Nah, AMD bought them. AMD has a good reputation of opening their hardware specs.

---

### Post by JDShu on 2010-01-12
> **Frak said:**
> They didn't want to maintain a Linux port. Releasing the specs saved them money. Nvidia only does it because they don't need to radically change the codebase to support Linux. An entire Linux division costs a lot, a LOT, of money to keep up.

Exactly, releasing specs saved them money and meant they didn't have to compete as hard with their proprietary drivers. What is interesting is that they released the specs (which is still expensive) rather than bowing out of the Linux market completely.

---

### Post by Frak on 2010-01-12
> **JDShu said:**
> Exactly, releasing specs saved them money and meant they didn't have to compete as hard with their proprietary drivers. What is interesting is that they released the specs (which is still expensive) rather than bowing out of the Linux market completely.
What amazed me is how fast they released the specs. It was like, AMD bought ATi. Week later: AMD releases ATi hardware specifications.

I was like [noparse]:O[/noparse]

---

### Post by JDShu on 2010-01-12
LOL maybe my flaw is assuming that they're all rational. Its actually that AMD loves open sourcing things.

---

### Post by AllRadioisDead on 2010-01-13
> **JDShu said:**
> LOL maybe my flaw is assuming that they're all rational. Its actually that AMD loves open sourcing things.
They didn't open source anything.
They released the specs, that's about it.
The drivers are under development by the community.

---

### Post by msrinath80 on 2010-01-13
What we really need to understand is that while these two are trudging along, Intel is making decent strides with it's integrated graphics technology which balances power consumption with performance. For those who play light games and do simple CAD work, the Intel graphics are a pretty good option. With every reduction in the die size, the Integrated graphics is getting closer and closer to the CPU. I'd not be surprised if the mid-range graphics market is actually captured by Intel within the next few years! Any thoughts??

---

### Post by boriskarloffinablender on 2010-01-13
> **msrinath80 said:**
> What we really need to understand is that while these two are trudging along, Intel is making decent strides with it's integrated graphics technology which balances power consumption with performance. For those who play light games and do simple CAD work, the Intel graphics are a pretty good option. With every reduction in the die size, the Integrated graphics is getting closer and closer to the CPU. I'd not be surprised if the mid-range graphics market is actually captured by Intel within the next few years! Any thoughts??

intel's linux drivers are pretty poor compared to windows.

---

### Post by JDShu on 2010-01-13
> **msrinath80 said:**
> What we really need to understand is that while these two are trudging along, Intel is making decent strides with it's integrated graphics technology which balances power consumption with performance. For those who play light games and do simple CAD work, the Intel graphics are a pretty good option. With every reduction in the die size, the Integrated graphics is getting closer and closer to the CPU. I'd not be surprised if the mid-range graphics market is actually captured by Intel within the next few years! Any thoughts??

I would be very impressed if intel chipsets could compete with lower end ATI and Nvidia cards. Still, this arena of competition is quite different. Intel probably has to worry about ARM more than ATI or Nvidia.

---

### Post by 3rdalbum on 2010-01-13
> **JDShu said:**
> 

The conclusion from this is that if you believe that:

- The ATI oss drivers are going to become as good as Nvidia proprietary drivers soon.

That's where your entire argument falls down. There's still a massive gap between Nvidia and ATI performance on Linux. ATI's fastest cards are theoretically much faster than Nvidia's; but on Linux ATI's fastest cards are slower than Nvidia's.

And would you buy an ATI card after knowing exactly how many relatively recent cards were abandoned in ATI's driver back in 2008? I certainly wouldn't.

And let's not forget video decode acceleration. Nvidia got a two year head-start and most video players these days support VDPAU. And it's stable as. ATI's equivilant exists in their drivers, but nobody's actually been able to test it because there are no specifications released for it, and no patches for any video players to support it.

With video decode acceleration, ATI's best hope of catching up is to adopt VDPAU as the API. But there's no sign of any of these problems being fixed, except by the efforts of open-source developers who, by definition, will trail behind the proprietary driver.

---

### Post by JDShu on 2010-01-13
> **3rdalbum said:**
> That's where your entire argument falls down. There's still a massive gap between Nvidia and ATI performance on Linux. ATI's fastest cards are theoretically much faster than Nvidia's; but on Linux ATI's fastest cards are slower than Nvidia's.


Hence the assumption. First I should say, I kind of cheated by saying "soon" ambiguously. However, I think that there is a widespread belief that ATI oss drivers are progressing well and should achieve function parity in the near future (the exact amount of time isn't too important, just that it is believed that the gap will close eventually, and that this "eventually" is not a decade away or something)

---

### Post by AllRadioisDead on 2010-01-13
> **JDShu said:**
> Hence the assumption. First I should say, I kind of cheated by saying "soon" ambiguously. However, I think that there is a widespread belief that ATI oss drivers are progressing well and should achieve function parity in the near future (the exact amount of time isn't too important, just that it is believed that the gap will close eventually, and that this "eventually" is not a decade away or something)
Actually, yes the exact amount of time is very relavenet to someone making a decision about which card to buy. As a user with an HD 4850 card, I'm using the OSS drivers now and it's not much of an improvement. The proprietary driver handles 2D well enough, and I could actually play 3D games. The only thing that bugged me was the stupid flickering it did whenever I opened a wine app.

---

### Post by JDShu on 2010-01-13
> **ihermit said:**
> Actually, yes the exact amount of time is very relavenet to someone making a decision about which card to buy. As a user with an HD 4850 card, I'm using the OSS drivers now and it's not much of an improvement. The proprietary driver handles 2D well enough, and I could actually play 3D games. The only thing that bugged me was the stupid flickering it did whenever I opened a wine app.

The point is not whether consumers buy a card today or not. The premise is if and when ATI oss drivers become as functional as Nvidia ones, what will Nvidia do? In fact, in a perfect (theoretical) world, it does not matter if this point in time was in the far future, the theory would (hopefully) still hold. Of course in reality, we can't do that because you don't know how they might change their strategies due to external circumstances.

---

