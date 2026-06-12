---
title: "Emergency ! 10 th crash with OOo2 beta :) What are repositories masters waiting for ?"
date: 2005-12-02
forum: Repositories &amp; Backports
---

### Post by tassou on 2005-12-02
Hi,
the fact that breezy was shiped by default with a (highly) buggy office suite can be understood. Choice was made at early stage to use this major version and the release date of OOo2 was delayed.

BUT now OOo2 *stable* has been release several weeks ago. 2.0.0 does not include any change in dependancies, it is *only* a less buggy release.

So why aren't repositories updated yet ?? It is a HI priority, I do not consider OOo2 beta as usable on a daily basis. It is an *emergency* to provide **official** support for OOo2 stable, in **official repository**. - I mean, I do not want to write on each set of ubuntu CDs I distribute every day : "Sorry, unlike in previous version, there is no office suite usable on breezy, so you may consider using an unofficial unsupported repository, or taking the up2date suse rpm with alien, or better : installing OOo1". -

Please do not give me some links to how-to install OOo2 stable, I exactly know how to do the unofficial way.
In this particular case, the how-to **should** be : **apt-get update; apt-get upgrade**.

Sorry to be so crude, but I really like ubuntu and I consider this lack as an inconstitency in its policy.

Paul

PS : I give you this 10th bugs found (moreover I do not use OOo2 really often) : 
start OOo2, clique File > Wizards > Web page
and enjoy your crash. In some particular cases it will work after 30 seconds of cpu at 100%, in others it would just loop until you kill it.

---

### Post by 23meg on 2005-12-02
It won't be included in the main repositories. There's only a chance that it may be backported. [quote=tassou]
Sorry to be so crude, but I really like ubuntu and I consider this lack as an inconstitency in its policy.[/quote]On the contrary, it's consistency; the policy is not to provide any updates except security ones, to increase distro stability.

---

### Post by tassou on 2005-12-02
Ok.
So what is considered as a security update ?
Because I could probably find plenty of way to crash a OOo2 session, and to anoy the end-user. 

If there were a flaw that could permit to remove some files in the user home directory, would it be considered as a security issue that would need an update ?

Anyway, even if it is not a security update, updating OOo2 would be straightforward and ** would increase distro stability**. While not doing so preserves the poor stability when using the office suite.

So it is still inconsistant to me :)

Backports are aimed to provide *new versions* of software. OOo2 stable is *not* a new version, it is the same as the beta with bugfixes.

By and large, doing so leads every ubuntu users to install OOo1 from repositories, or to add unsupported foreign repositories (very bad IMHO), or for the more experimented - to skip the packaging manager and to install it by hand -.
Result : deprecated version, or newest version with pakaging integrity broken. Is it what you wish to ubuntu users ?

I still think it is a big problem. Shipping beta was a bad idea but not planed, now they can fix this mistake, it is time to do so :razz: 

Thanx

Paul

---

### Post by towsonu2003 on 2005-12-02
I have to agree to this one, although I'm not angry or frustrated as the poster... 

my OOo2 keeps crashing as well (2 crashes in last 5 uses -ok I used it 10 times at most after fresh 5.10 install :) ), and I would appreciate the stable OOo2 in the main as bug fix / security update as well. 

Or, (knowing that this is not very probable after seeing firefox 1.5 being backported -in future- but not in main) I am also okay with waiting a couple of months for Dapper, no big deal, but that's because I'm not a heavy 'office' user (->used OOo2 10 times in last 2 months in ubuntu). :)

good luck...

PS. What does Debian stable users do with their old software, for god sake? <= joke
PS2. I think we (newbies) are a little bit too much used to the Windows style of updating?

---

### Post by tassou on 2005-12-02
Sorry, I was not angry neither frustrated :D 
- I am more likely a bad french english-user ;) -

The point is that ubuntu (and breezy in particular) is the only desktop distro that do not care that much about the office suite provided.

I am a latex fan, and the only reason why I sometime launch open office 2 is to provide direct and quick support to peoples from my school that installed breezy recently (following my advice).

I know that when we get involved in more fundamental issues, we quickly forget the newbies problems. This is a HUGE one, and I can not understand that ubuntu does not take more in consideration that it is the **only** desktop distro that does **not** include proper, official AND working OpenOffice2. I repeat myself, but it is fully inconsistent with its policy.

Meantime, ubuntu offers a high level of quality and usability that I really appreciate when I urge newcoming people to use a linux distro :)

---

### Post by 23meg on 2005-12-02
[QUOTE=tassou]Ok.
So what is considered as a security update ?[/quote]An update that fixes a security flaw which may lead to control of any aspect of the distro to be compromised. 
[QUOTE=tassou]
If there were a flaw that could permit to remove some files in the user home directory, would it be considered as a security issue that would need an update ?[/QUOTE]If it were proven to be a software flaw that removed those files against the user's will, it would.
> 
Backports are aimed to provide *new versions* of software. OOo2 stable is *not* a new version, it is the same as the beta with bugfixes.Wrong; anything except security and showstopper updates normally provided by Ubuntu qualifies for backports. Note that backports are now official, though. 

Your best bet is to search the backports forum to see if there's a request already (I bet there are more than five), and if not, place a request.

---

### Post by jdong on 2005-12-02
[QUOTE=23meg]Your best bet is to search the backports forum to see if there's a request already (I bet there are more than five), and if not, place a request.[/QUOTE]

there have been at least 5 requests... It's not in Dapper yet, and after repeatedly trying to contact the Openoffice maintainers for Ubuntu, could not come up with a good reason for it.

In the meantime, the repository:
```

deb http://people.ubuntu.com/~doko/OOo2 ./

```

provides Openoffice 2.0 final packages. They are made by the primary Openoffice guy here at Ubuntu, so they're high-quality packages. Why he hasn't uploaded that to Dapper yet, don't ask me! :)

A lot of us share your frustration... we don't blame you.

---

### Post by jdong on 2005-12-02
[QUOTE=tassou]
PS : I give you this 10th bugs found (moreover I do not use OOo2 really often) : 
start OOo2, clique File > Wizards > Web page
and enjoy your crash. In some particular cases it will work after 30 seconds of cpu at 100%, in others it would just loop until you kill it.[/QUOTE]
This problem still happens. I'll file a bug report for it, as this is a serious problem...


Note that bugs aren't necessarily permanently stuck in Ubuntu stable releases. There are "-backports" and "-updates" repositories for that. "-backports", maintained by me and the Backports Team, brings new versions from the in-develop version back to the stable version. "-updates" isolates fixes for serious bugs (like the kind you reported) and brings these specific patches back to the stable version. Both are able to solve this problem once the developers address it in some way.

BTW, [http://bugzilla.ubuntu.com/show_bug.cgi?id=20404](http://bugzilla.ubuntu.com/show_bug.cgi?id=20404) is the bug I filed on your behalf.

---

### Post by arnieboy on 2005-12-02
not a bug in my case. upgrade to OO2 with automatix. things work minus any probs.

---

### Post by tassou on 2005-12-03
lol, a bit a advertising ... That is slightly off-topic :)
If you do not have the bug, it is only because your version is 2.0.0 stable, not because any magic fix done by your script.
Using automatix, or setting an up2date repository (what this script actualy does) is exactly the same, the only difference is that setting it myself I do not have to fire a unofficial script with root privilege :p

regards


paul

---

### Post by arnieboy on 2005-12-03
[QUOTE=tassou]lol, a bit a advertising ... That is slightly off-topic :)[/quote]
no this is not advertising. I am just telling everyone the quickest way to upgrade to oo2.
> If you do not have the bug, it is only because your version is 2.0.0 stable, not because any magic fix done by your script.
my script does not do any magic. it only makes life easier for a whole lot of people. u havent done anything good for anyone till date. I am sure u sneer at your parents as well.

> Using automatix, or setting an up2date repository (what this script actualy does) is exactly the same, the only difference is that setting it myself I do not have to fire a unofficial script with root privilege :p
I never begged u to use automatix and NOT do things on ur own. U are welcome to do whatever u feel like. Automatix makes life easy for people. that does not mean u need to use it. and yes, it activates your root account but that does and WILL NOT break anybody's system. 
u and ur ill-informed group of dorks need to go somewhere else and get a life.

---

### Post by tassou on 2005-12-03
lol, a bit a advertising ... That is slightly off-topic :)
If you do not have the bug, it is only because your version is 2.0.0 stable, not because any magic fix done by your script.
Using automatix, or setting an up2date repository (what this script actualy does) is exactly the same, the only difference is that setting it myself I do not have to fire a unofficial script with root privilege :p

regards


paul

---

### Post by tassou on 2005-12-03
lol, a bit a advertising ... That is slightly off-topic :)
If you do not have the bug, it is only because your version is 2.0.0 stable, not because any magic fix done by your script.
Using automatix, or setting an up2date repository (what this script actualy does) is exactly the same, the only difference is that setting it myself I do not have to fire a unofficial script with root privilege :p

Jdong, thank you for your help, now I know that you (ubuntu gurus) are aware of this point of you, I just wait. Anyway, thank you again for your great work !

regards


paul

---

### Post by jdong on 2005-12-03
[QUOTE=arnieboy]not a bug in my case. upgrade to OO2 with automatix. things work minus any probs.[/QUOTE]
Interesting... how does Automatix install OOo2 final? Using the ooo-debianize scripts and OOo official binaries? people.ubuntu.org/~doko?

Even doko's packages suffer partly from a 1-minute stall during this procedure, so it seems like it may be a Ubuntu patch that causes it.

---

### Post by tassou on 2005-12-03
[QUOTE=jdong]
Even doko's packages suffer partly from a 1-minute stall during this procedure, so it seems like it may be a Ubuntu patch that causes it.[/QUOTE]

ok I apologize for what I said, if this one does not depend upon the revision of OOo but on an ubuntu patch. Tested on official gentoo OOo2 stable : no bug neither.

---

### Post by jdong on 2005-12-03
Hmm, that means it may be a patch that Ubuntu applies that causes the issue.

Though the build number for openoffice shows up as 129, the Ubuntu developers did patch it up quite a bit, such that it's extremely close to the final release.


Now, if we can only isolate what patch is causing this behavior....


In the Gentoo package, did you compile with USE="gnome", and verify that GNOME integration works?

---

### Post by arnieboy on 2005-12-03
[QUOTE=jdong]Interesting... how does Automatix install OOo2 final? Using the ooo-debianize scripts and OOo official binaries? people.ubuntu.org/~doko?

Even doko's packages suffer partly from a 1-minute stall during this procedure, so it seems like it may be a Ubuntu patch that causes it.[/QUOTE]
yes it uses doko's repos to upgrade to OO2 final. havent faced any issues yet..

---

### Post by tassou on 2005-12-03
not compiled for this one, used the precompiled one made by gentoo (I am trying to fight global warming ;) ) but with the gnome flag , yes.
I am afraid that one is unlikely to be really a bug, as if I start again a web page wizard, it takes only 5 seconds to come. Sorry, maybe it is only a poor piece of code in OOo2. 
What about you ? Here for my last test on breezy with OOo2 beta :
- 1st start : 40 seconds to come
- 2nd start : 5 seconds

on gentoo it seems to be quicker, but the behaviour is roughly the same.
But when I opened this thread, no wizard would come at all after clicking on Web page ... maybe only a bad coincidence.
Thanks again.

paul

---

### Post by jdong on 2005-12-03
Just weird... I don't know if the Webpage wizard uses Java or somthing, because we know that Ubuntu's GCC Java is inherently slow...


NOTE: the Gentoo precompiled Openoffice is the same as openoffice.org's binaries.

---

