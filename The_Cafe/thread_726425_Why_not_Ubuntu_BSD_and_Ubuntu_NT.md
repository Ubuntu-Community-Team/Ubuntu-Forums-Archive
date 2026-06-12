---
title: "Why not Ubuntu BSD and Ubuntu NT?"
date: 2008-03-16
forum: The Cafe
---

### Post by icett on 2008-03-16
Ubuntu Linux is here since a long time now and it very successful. Canonical being a very strong company financially is ideally in a position to grab a large percentage of global desktop OS market if it adopts the following strategies:



1- Complete coverage of the UNIX platform:


There are two UNIX-like platforms 1- Linux and 2- BSD. However BSD is closer to UNIX than Linux. Indeed its the purest UNIX I think. Also Apple's Mac is based on BSD. So why not Ubuntu covers BSD as well? I think if Ubuntu decides to include BSD too it would be very beneficial for Canonical in the long term.


2- Coverage of the NT platform:


I would also suggest Canonical to create their own version of the OS for the NT platform as well. Why leave the NT platform alone for M$ to do whatever they wish. I would not ask Canonical to just clone the NT system of M$ but develop one of their own based on the NT technology and design. NT is not inherently an unstable and insecure platform. It is because of the wrong implementation of M$ of the NT design codes etc. which is responsible for the creation of such unstable and insecure OSes series which is called Windows.


3- The name/s of all 3 Oses i.e. Linux based, BSD based and NT based should be changed to something catchy, attractive and modern. 



This will make Canonical covering the entire popular platforms of the desktop market and in time make ground for Canonical to have a considerable position in the global OS market. What you think about all this?

---

### Post by p_quarles on 2008-03-16
You can already get Debian built around a BSD framework. If the demand is there, I'm sure Canonical will start porting that to Ubuntu as well. However, neither Linux nor any of the *BSDs are certified as UNIX. 

The NT platform is under a restrictive copyright and does not allow for redistribution or modification. Building an Ubuntu version on top of that (without Microsoft's permission -- unlikely to say the least) would be illegal.

---

### Post by sumguy231 on 2008-03-16
If you're talking about the BSD utilities, then I belive those are already in the repositories.
If you're talking about the a BSD kernel, Debian has a Debian GNU/NetBSD port. But it's incomplete and not really worth the effort if you ask me. Linux has more applications, and more hardware support.

> 3- The name/s of all 3 Oses i.e. Linux based, BSD based and NT based should be changed to something catchy, attractive and modern.
I don't see anything wrong with "Ubuntu", myself. It's definitely unique.

> However BSD is closer to UNIX than Linux. Indeed its the purest UNIX I think. 
There isn't really "purest", just certified and not certified. Mac OS is certified as a UNIX now, but I think it's a waste of money because clearly nobody cares anymore.

---

### Post by init1 on 2008-03-16
> **icett said:**
> Ubuntu Linux is here since a long time now and it very successful. Canonical being a very strong company financially is ideally in a position to grab a large percentage of global desktop OS market if it adopts the following strategies:



1- Complete coverage of the UNIX platform:


There are two UNIX-like platforms 1- Linux and 2- BSD. However BSD is closer to UNIX than Linux. Indeed its the purest UNIX I think. Also Apple's Mac is based on BSD. So why not Ubuntu covers BSD as well? I think if Ubuntu decides to include BSD too it would be very beneficial for Canonical in the long term.


2- Coverage of the NT platform:


I would also suggest Canonical to create their own version of the OS for the NT platform as well. Why leave the NT platform alone for M$ to do whatever they wish. I would not ask Canonical to just clone the NT system of M$ but develop one of their own based on the NT technology and design. NT is not inherently an unstable and insecure platform. It is because of the wrong implementation of M$ of the NT design codes etc. which is responsible for the creation of such unstable and insecure OSes series which is called Windows.


3- The name/s of all 3 Oses i.e. Linux based, BSD based and NT based should be changed to something catchy, attractive and modern. 



This will make Canonical covering the entire popular platforms of the desktop market and in time make ground for Canonical to have a considerable position in the global OS market. What you think about all this?
A BSD Ubuntu would be possible but a NT Ubuntu would not. NT is owned by Microsoft. I suppose maybe they kernel from ReactOS could be used, but it's not anywhere near stable yet. Also, the name "Ubuntu" is fine with me.

---

### Post by k2t0f12d on 2008-03-16
> **icett said:**
> Ubuntu Linux is here since a long time now and it very successful. Canonical being a very strong company financially is ideally in a position to grab a large percentage of global desktop OS market if it adopts the following strategies:

1- Complete coverage of the UNIX platform:

There are two UNIX-like platforms 1- Linux and 2- BSD. However BSD is closer to UNIX than Linux. Indeed its the purest UNIX I think. Also Apple's Mac is based on BSD. So why not Ubuntu covers BSD as well? I think if Ubuntu decides to include BSD too it would be very beneficial for Canonical in the long term.

I don't see the advantage this would create.  BSD UNIX is not substantively different enough from Ubuntu GNU/Linux to warrant the amount of attention you described.  It would be more advantageous to pursue GNU/Linux development unfettered, rather then try to be everything to everyone.

> **icett said:**
> 2- Coverage of the NT platform:

I would also suggest Canonical to create their own version of the OS for the NT platform as well. Why leave the NT platform alone for M$ to do whatever they wish. I would not ask Canonical to just clone the NT system of M$ but develop one of their own based on the NT technology and design. NT is not inherently an unstable and insecure platform. It is because of the wrong implementation of M$ of the NT design codes etc. which is responsible for the creation of such unstable and insecure OSes series which is called Windows.

This is much more interesting.  NT is substantively different enough from GNU *and* UNIX to possibly warrant attention.  The problem with NT is that its very design collides with the underlying interest in Ubuntu's goals with GNU/Linux.  See [this]("http://catb.org/~esr/writings/taoup/html/ch03s01.html#id2892028") piece of writing by Eric Steven Raymond for more detail on why I think that is so.

> **icett said:**
> 3- The name/s of all 3 Oses i.e. Linux based, BSD based and NT based should be changed to something catchy, attractive and modern. 

This will make Canonical covering the entire popular platforms of the desktop market and in time make ground for Canonical to have a considerable position in the global OS market. What you think about all this?

Overall, Ubuntu isn't large enough to sustain that kind of ambition.  The desktop market remains too thinkly spread to launch multiple concurrent distribution and development strategies.  The best idea is the one that is present but unspoken in your posting.  That is that in the future operating systems will become completely transparent to the user.

> **p_quarles said:**
> You can already get Debian built around a BSD framework. If the demand is there, I'm sure Canonical will start porting that to Ubuntu as well. However, neither Linux nor any of the *BSDs are certified as UNIX.

Nor should they be.  Linus is already hot about gcc developers being over-attentive to the points of slavishness to specification rather then results.  It is much better for the systems future growth to *aim for* single UNIX spec, but not focus on that exclusively.  If there is a better way to do something that maintaining certification would prohibit, the cert becomes a liability, not an advantage.

> **p_quarles said:**
> The NT platform is under a restrictive copyright and does not allow for redistribution or modification. Building an Ubuntu version on top of that (without Microsoft's permission -- unlikely to say the least) would be illegal.

It would be *very* easy for Ubuntu to collaborate with the ReactOS and WINE projects to start a free software NT-based distribution.  Microsoft can enforce copyright against *its* implementation of the API, but have no legal recourse under copyright law with respect to other developer's instantiations.  They could presumably sue under patent law, except that the outcome of such a lawsuit would be irreversible and permanently change the landscape of their patent portfolio, without which they would be unable to pursue FUD as effectively as they have in the past.

---

