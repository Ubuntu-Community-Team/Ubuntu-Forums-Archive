---
title: "Linus Torvalds remains doubtful on GPL3"
date: 2007-06-11
forum: The Cafe
---

### Post by Andrewie on 2007-06-11
[http://www.infomaticsonline.co.uk/vnunet/news/2191856/linus-torvalds-remains-doubtful](http://www.infomaticsonline.co.uk/vnunet/news/2191856/linus-torvalds-remains-doubtful)

"I still think GPLv2 is simply the better licence," Torvalds wrote in a posting to the Linux Kernel Developer mailing list on Sunday.

Torvalds oversees contributions to the Linux kernel and can decide to change the licence. The kernel forms the core of the operating system, but Linux distributions contain code from many other open source projects, most of which are governed by the GPL. Each of those projects has to decide if they want to switch to GPLv3 or remain on current GPLv2.

Torvalds over the past months has softened his disapproval of the forthcoming licence. But he denied that he was in any way impressed.

"I was impressed in the sense that it was a hell of a lot better than the
disaster that were the earlier drafts," said Torvalds.

The Linux founder has previously dismissed the licence as "religious ". He disagrees with its attempts to prevent the use of digital rights management and its efforts to undermine the Novell-Microsoft partnership.

He also killed speculation that the Linux kernel would opt for a dual licence, allowing users and distributors to choose between GPLv2 and GPLv3, describing it as "unlikely (and technically quite hard), but at least _possible_ in theory."

No major open source projects have yet lined up behind the licence. Sun Microsystems so far has been one of its most vocal supporters, suggesting that it might choose the licence for its Solaris operating system. But the company has made it very clear that it won't make a decision on the matter before the final version of the licence has been published.

If Sun would pick GPLv3 for Solaris however, that would make it more appealing for the Linux kernel to follow suit. With both projects under the same licence, developers could more easily swap technologies, for instance brining over Solaris' ZFS file system or DTrace, an application performance optimization tool.

"I don't think the GPLv3 is as good a licence as v2, but on the other hand, I'm pragmatic, and if we can avoid having two kernels with two different licences and the friction that causes, I at least see the _reason_ for GPLv3," Torvalds commented in another posting in which he responded to the possibility of Solaris under GPLv3.

"As it is, I don't really see a reason at all [to adopt GPLv3 for the Linux kernel]"

The GPLv3 is currently in the "final call" draft stage. The final version is scheduled for publication by the end of this month.

The general public licence is one of 58 offically approved open source licences. An estimated 80 per cent of all open source projects is governed by the GPL.

---

### Post by Andrewie on 2007-06-11
I have just one question, if the Linux kernel doesn't convert to GPLv3 will that make it illegal to ship any GPLv3 code with Linux distro?

---

### Post by runningwithscissors on 2007-06-12
He will come around when the patent suits start to hit and IBM, Sun etc. just cut Novell-like deals with MS in order to continue using and distributing Linux, leaving independent developers to fight their own battle.

---

### Post by LightB on 2007-06-12
> **runningwithscissors said:**
> He will come around when the patent suits start to hit and IBM, Sun etc. just cut Novell-like deals with MS in order to continue using and distributing Linux, leaving independent developers to fight their own battle.

Yeah, SCO all over again, that wacky IBM!

---

### Post by runningwithscissors on 2007-06-12
> **LightB said:**
> Yeah, SCO all over again, that wacky IBM!Only in this case, any cross-licensing deal would actually be very attractive for IBM because of their massive patent portfolio (much larger than MS'), and guaranteed revenue that they can make off it from MS. MS would gladly take a bit of a hit on such a deal, as at the present time they are not direct competitors in IBM's core markets, but it will remove IBM from being an adversary in the courts.

---

### Post by jrusso2 on 2007-06-12
Funny how different websites interpreted that differently another site was saying how Linus is coming around to GPL v3

---

### Post by BoyOfDestiny on 2007-06-12
> **Andrewie said:**
> I have just one question, if the Linux kernel doesn't convert to GPLv3 will that make it illegal to ship any GPLv3 code with Linux distro?

No, it won't be illegal.

"When we say that GPLv2 and GPLv3 are incompatible, it means there is no legal way to combine code under GPLv2 with code under GPLv3 in a single program. This is because both GPLv2 and GPLv3 are copyleft licenses: each of them says, “If you include code under this license in a larger program, the larger program must be under this license too.” There is no way to make them compatible. We could add a GPLv2-compatibility clause to GPLv3, but it wouldn't do the job, because GPLv2 would need a similar clause.

Fortunately, license incompatibility only matters when you want to link, merge or combine code from two different programs into a single program. There is no problem in having GPLv3-covered and GPLv2-covered programs side by side in an operating system. "
-Richard M. Stallman

[http://gplv3.fsf.org/rms-why.html](http://gplv3.fsf.org/rms-why.html)

---

### Post by Andrewie on 2007-06-12
> **BoyOfDestiny said:**
> No, it won't be illegal.

"When we say that GPLv2 and GPLv3 are incompatible, it means there is no legal way to combine code under GPLv2 with code under GPLv3 in a single program. This is because both GPLv2 and GPLv3 are copyleft licenses: each of them says, “If you include code under this license in a larger program, the larger program must be under this license too.” There is no way to make them compatible. We could add a GPLv2-compatibility clause to GPLv3, but it wouldn't do the job, because GPLv2 would need a similar clause.

Fortunately, license incompatibility only matters when you want to link, merge or combine code from two different programs into a single program. There is no problem in having GPLv3-covered and GPLv2-covered programs side by side in an operating system. "
-Richard M. Stallman

[http://gplv3.fsf.org/rms-why.html](http://gplv3.fsf.org/rms-why.html)

thanks, that was bugging me since Linus said he wasn't going to change it for the first time

---

### Post by forrestcupp on 2007-06-12
"If it ain't broke, don't fix it."  I don't see why we need v.3.  It seems like it just takes away more of the freedom.

---

### Post by jrusso2 on 2007-06-12
"If it ain't broke, don't fix it." I don't see why we need v.3. It seems like it just takes away more of the freedom.


I think the tivoization thing started RMS thinking that some crafty company could get around the four freedoms.

---

### Post by Lord Illidan on 2007-06-12
Aye, there were loopholes in the wording, and the license was written before the internet boom, thus increasing the scope of the abuse.

---

### Post by nphx on 2007-07-02
> **forrestcupp said:**
> "If it ain't broke, don't fix it."  I don't see why we need v.3.  It seems like it just takes away more of the freedom.

Yeah I usually do believe keeping it simple is the best way, but whats wrong is GPL2 is broken, according to copy right laws. Linux GNU gaining momentum the way it is there is a concern to protect the community from those nasty companies who look to prevent progression.

---

