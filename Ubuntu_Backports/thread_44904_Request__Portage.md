---
title: "Request:  Portage"
date: 2005-06-28
forum: Ubuntu Backports
---

### Post by duffman9908 on 2005-06-28
I tried compiling Portage myself, however it is unstable and doesn't work.  If somebody could make a Portage Deb package that would be great.

---

### Post by Mez on 2005-06-28
o_O

Portage = Gentoo right?

This sint gentoo - and i dont think portage and apt would work well together.

Plus, not in debain, not in breezy.... no backport :D

Speak to the MOTU

---

### Post by mattheweast on 2005-06-28
Fun idea, but Mez is right, this is the wrong section of the forum: portage can't be backported, because it is not present in Ubuntu. The MOTU would not take it on, this is a project for someone to do just for a laugh. Would be interested in knowing how it goes though!

M

---

### Post by chol on 2005-06-28
When debian already has apt-build, why would one even need portage?
I'd suggest putting some time into streamlinging this and all gentoo zealots and other compiling lovers would perhaps be pleased :)

c

---

### Post by jdong on 2005-06-28
Isn't Portage also the name of a file manager?

---

### Post by mattheweast on 2005-06-28
AFAIK it is a package manager, which ships with gentoo.

There is a file manager called [Gentoo](http://www.obsession.se/gentoo/), perhaps that is what you are thinking of?

---

### Post by duffman9908 on 2005-06-29
[SIZE=3][FONT=Arial] I was just thinking that if Ubuntu had the ability to install through apt-get, alien, and portage.  There would be no need to look anywhere else for a Linux that "just works"[/FONT][/SIZE]

---

### Post by sjmorgan on 2005-06-29
[QUOTE=duffman9908][SIZE=3][FONT=Arial] I was just thinking that if Ubuntu had the ability to install through apt-get, alien, and portage.  There would be no need to look anywhere else for a Linux that "just works"[/FONT][/SIZE][/QUOTE]A GNU/Linux distribution is more than just a package manager.

Diversity and choice are good.

---

### Post by obiwan on 2005-07-13
I would use portage in ubuntu to have access to java libraries and keep them up to date.

---

### Post by jdong on 2005-07-13
Funny thing... I've attempted to port Portage over to Debian, but it was a flop... What a gargantuan mess Portage is! Even in Python, it's not modularized enough that ebuild subsystems can be substituted with apt/dpkg equivalents without ripping code apart everywhere!

---

### Post by wantilles on 2005-07-14
[QUOTE=sjmorgan]A GNU/Linux distribution is more than just a package manager.[/quote]

Really?

The package management system of a distribution is the most important part of it.

[QUOTE=sjmorgan]Diversity and choice are good.[/QUOTE]

What "choice"?

In comparison to Gentoo, who is **instantly & constantly** updated and **there are no versions**, Ubuntu is **standing still**.

For example, **Firefox 1.0.5 was released yesterday**.

**Today, it is in Portage** and a simple:

```
emerge -pv --newuse --columns mozilla-firefox
```

will install it, **fully optimized for my architecture & sub-architecture**.

In comparison, in Ubuntu what do we get?

We **will get Firefox 1.0.5 after SIX MONTHS** with the next release.

And please, do not bother to mention "the backports". They are just a **pathetic excuse**.

If you want to give life to this **static, asthmatic & paleolithic** distribution:

- "aggressive" package building of new software not just backports
- new software not only for x86 but also for amd64

---

### Post by Kyral on 2005-07-14
Then go use Gentoo. No one is stopping you. Linux is all about choices. If you don't like A you can use B.

---

### Post by mr_pouit on 2005-07-14
[QUOTE=wantilles]Really?

The package management system of a distribution is the most important part of it.



What "choice"?

In comparison to Gentoo, who is **instantly & constantly** updated and **there are no versions**, Ubuntu is **standing still**.

For example, **Firefox 1.0.5 was released yesterday**.

**Today, it is in Portage** and a simple:

```
emerge -pv --newuse --columns mozilla-firefox
```

will install it, **fully optimized for my architecture & sub-architecture**.

In comparison, in Ubuntu what do we get?

We **will get Firefox 1.0.5 after SIX MONTHS** with the next release.

And please, do not bother to mention "the backports". They are just a **pathetic excuse**.

If you want to give life to this **static, asthmatic & paleolithic** distribution:

- "aggressive" package building of new software not just backports
- new software not only for x86 but also for amd64[/QUOTE]
 :roll: 
i was using gentoo before, and :
- i don't have anymore the time to install/update gentoo : waiting a couple of hours a prog to be build.... :/
- IMHO, gentoo's gain of performances is "mainly a dream" : my pc is as fast as it was under gentoo...
- if you don't like ubuntu, why posting here, so aggressively ? everyone has the choice to use the GNU/Linux distribution he wants to !

and do you think you have the right to judge a distribution like this ? do you have a superiority complex ?  :-) 

Indeed, that's not the topic, but you got on my nerves, especially by using bold as you did  :|

---

### Post by DJ_Max on 2005-07-14
[QUOTE=jdong]What a gargantuan mess Portage is! Even in Python, it's not modularized enough that ebuild subsystems can be substituted with apt/dpkg equivalents without ripping code apart everywhere![/QUOTE]
It wasn't meant to be, and for good reasons. It does however run on OS X. With that said, you want Portage you have to use Gentoo, or even better, try a BSD, as Gentoo was based on BSD, but still has some of the Linux shortcomings.

---

### Post by jdong on 2005-07-14
[QUOTE=wantilles]Really?

The package management system of a distribution is the most important part of it.



What "choice"?

In comparison to Gentoo, who is **instantly & constantly** updated and **there are no versions**, Ubuntu is **standing still**.

For example, **Firefox 1.0.5 was released yesterday**.

**Today, it is in Portage** and a simple:

```
emerge -pv --newuse --columns mozilla-firefox
```

will install it, **fully optimized for my architecture & sub-architecture**.

In comparison, in Ubuntu what do we get?

We **will get Firefox 1.0.5 after SIX MONTHS** with the next release.

And please, do not bother to mention "the backports". They are just a **pathetic excuse**.

If you want to give life to this **static, asthmatic & paleolithic** distribution:

- "aggressive" package building of new software not just backports
- new software not only for x86 but also for amd64[/QUOTE]

The rapid development of Gentoo leads to MANY downfalls. Stability is the biggest one.

I've been FIRED from a LAMP admin job because of Gentoo (MySQL security update hosed libmsql.so)... These kinds of mistakes are UNACCEPTABLE in an enterprise-class distribution.

If you like Portage, GO USE IT. There are PLENTY of how-to's for using Portage on other distributions...

This is NOT a backports topic. Period.

---

