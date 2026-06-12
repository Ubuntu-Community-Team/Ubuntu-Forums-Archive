---
title: "Apple not allowing open source apps in any of their app stores?"
date: 2010-11-26
forum: The Cafe
---

### Post by madjr on 2010-11-26
i was viewing this nice presentation about how linux app stores can use crowdsourcing for QA and it mentions it:

[http://opensolutions.coss.fi/pdf/Henri_Bergius.pdf](http://opensolutions.coss.fi/pdf/Henri_Bergius.pdf)



*or full here:*
[http://bergie.iki.fi/blog/application_quality_assurance_in_linux_distributions/](http://bergie.iki.fi/blog/application_quality_assurance_in_linux_distributions/)


right now it seems this affects iOS , but might also become the same in the new osX lion app store.

So is this really true?
are they banning any app simply because they are open source?

some of the best software is foss, and i think stuff like this might even be illegal in some places like europe...

---

### Post by earthpigg on 2010-11-26
plenty of threads on it if you look around.

here's the condensed version of what i have gathered:

GPL'd *[GNU]("http://www.gnu.org/software/software.html")* software cannot be present in the App Store due to legal threats from the Free Software Foundation.

All other GPL'd apps need to be approved by ***every*** relevant copyright owner prior to being included in the App Store without worry. Some Free Software projects using the GPL make contributors assign copyright ownership to the project's leadership, and some don't. Those with a sole entity owning all of the code can be in the App Store if that entity is ok with it. Those that don't require contributors to assign copyright to the single entity will be removed from the App Store if a single contributor demands it.

BSD licensed software is fine.

Most other Open Source licenses are fine, too.

---

### Post by Merk42 on 2010-11-26
> **earthpigg said:**
> GPL'd *[GNU]("http://www.gnu.org/software/software.html")* software cannot be present in the App Store due to legal threats from the Free Software Foundation.
I'm glad this was the second post before this thread turned into another $proprietarySoftwareCompany is evil thread.

---

### Post by Zerocool Djx on 2010-11-26
Dude, it's apple,.. did you really think otherwise? Why is this even posted? LOL!?!?

---

### Post by tgalati4 on 2010-11-26
In before the Apple-Bashing lock.

---

### Post by Merk42 on 2010-11-26
> **Zerocool Djx said:**
> Dude, it's apple,.. did you really thing otherwise? Why is this even posted? LOL!?!?
*Reads title*
*hits reply to bash company that isn't FOSS*
*doesn't bother reading content of thread*

---

### Post by saulgoode on 2010-11-27
> Apple not allowing open source apps in any of their app stores?
It is more accurate to say that Apple is not allowing any open source apps *out* of their app stores.

In order for someone to download software from Apple's store, they must enter into a contractual agreement with Apple to not engage in certain activities, even though some of those activities may be permitted by the copyright licenses attached to the software. This agreement is effectively a sales contract, noting that the "sale" transaction may not demand any monetary exchange. The terms and conditions of this contract have nothing to do with licensing, since Apple holds no rights on the software to license.

Some of the extra conditions put in place by the Apple store's contract dictate that any software obtained from the store fails to qualify as Free Software. The [Free Software Definition]("http://www.gnu.org/philosophy/free-sw.html") does not delineate between license terms and contract terms. A prohibition against commercial use or a limitation on the number of devices the software the software runs on encroaches on the customers' freedom to use the software, regardless of whether the restriction is accomplished through copyright licensing, patent licensing, or contractual agreement. 

In theory, the same analysis suggests that software obtained from the Apple app store should not be considered Open Source software, and in spirit this is true. Unfortunately, the wording of the [Open Source Definition]("http://www.opensource.org/docs/osd") only directly confronts the issue of "*the license*" of the software -- the originators of the Open Source Initiative failed to address the possibility that restrictions might be instituted through contracts (such as the terms and conditions of the Apple app store).

Regardless whether the copyright licensing of the software is GPL, BSD, MIT, or any other Free/Open Source license, when obtained from the Apple app store, software will not be Free Software and, aside from a technical deficiency in the wording of the OSD, it will not be Open Source. This has nothing to do with the original licensing of the software, but is owing to the contractual restrictions established by Apple.

---

### Post by madjr on 2010-11-27
ok, thanks guys.

i suppose this is just in the apple store (and maybe in the w7phone market too?), not in other apps stores like the android market or webos?

---

### Post by Dr. C on 2010-11-27
This is an Apple and at this point a RIM (Blackberry) problem. Microsoft does not impose terms that are in conflict with the licenses of its suppliers. [http://store.microsoft.com/tou/#noticesoftware]("http://store.microsoft.com/tou/#noticesoftware") and [http://marketplace.windowsphone.com/resources/en-us/Windows%20Marketplace%20Customer%20Service%20Agreement.pdf]("http://marketplace.windowsphone.com/resources/en-us/Windows%20Marketplace%20Customer%20Service%20Agreement.pdf"). Ever wonder how Microsoft Windows became so popular? It is not by censoring Windows software on the basis of its license agreements. Google (Android) has as Open Source exception that effectively allows most FLOSS.  [http://www.google.com/mobile/android/market-tos.html]("http://www.google.com/mobile/android/market-tos.html"). RIM apparently however is willing to listen [http://us.blackberry.com/legal/]("http://us.blackberry.com/legal/") as they will >  use commercially reasonable efforts to address any concerns you may have.It would be interesting to see what would happen if the FSF actually approached them. GNU Go on the Blackberry?

---

### Post by stmiller on 2010-11-28
There is a version of VLC in the store:

[http://itunes.apple.com/us/app/vlc-media-player/id390885556?mt=8](http://itunes.apple.com/us/app/vlc-media-player/id390885556?mt=8)

Here is a related mailing list post discussing the license:

[http://mailman.videolan.org/pipermail/vlc-devel/2010-November/077486.html](http://mailman.videolan.org/pipermail/vlc-devel/2010-November/077486.html)

---

### Post by Dr. C on 2010-11-28
> **stmiller said:**
> There is a version of VLC in the store:

*Link to  pirated software removed from quote *

Here is a related mailing list post discussing the license:

[http://mailman.videolan.org/pipermail/vlc-devel/2010-November/077486.html](http://mailman.videolan.org/pipermail/vlc-devel/2010-November/077486.html)

A ***pirated*** version of VLC in the Apple store.

---

### Post by czr114 on 2010-11-28
> **saulgoode said:**
> It is more accurate to say that Apple is not allowing any open source apps *out* of their app stores.

Technically, there's no free software on iOS. Digital signatures and hardware lockout ensure that only software with proprietary signature extensions may be run. The user is not free to tinker, modify, or recompile said software.

The platform is Tivoized.

---

### Post by Dr. C on 2010-11-28
> **czr114 said:**
> Technically, there's no free software on iOS. Digital signatures and hardware lockout ensure that only software with proprietary signature extensions may be run. The user is not free to tinker, modify, or recompile said software.

The platform is Tivoized.

Tivoization alone does not prevent Free Software from a platform. What is preventing Free Software in the Apple store is the terms of use which turn all software in the Apple store into non Free Software, by adding restrictions to the use and distribution of the software. Apple could for example use terms similar to those of Microsoft: > WITHOUT LIMITING THE FOREGOING, COPYING OR REPRODUCTION OF THE SOFTWARE OR MERCHANDISE TO ANY OTHER SERVER OR LOCATION FOR FURTHER REPRODUCTION OR REDISTRIBUTION IS EXPRESSLY PROHIBITED, UNLESS SUCH REPRODUCTION OR REDISTRIBUTION IS EXPRESSLY PERMITTED BY THE LICENSE AGREEMENT ACCOMPANYING SUCH SOFTWARE OR MERCHANDISE. [http://store.microsoft.com/tou/#noticesoftware]("http://store.microsoft.com/tou/#noticesoftware") and avoid this problem.

---

