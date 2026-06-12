---
title: "GPLv3 for the Linux kernel?"
date: 2006-01-31
forum: The Cafe
---

### Post by nocturn on 2006-01-31
Linus has stated that the Linux kernel will not be moving to the GPLv3 when it is released.

The specific reason seems to be the clause in the new license putting a lid on the use of DRM in GPL'ed software.

What do you all think about this?  Should the kernel move to the new license?

---

### Post by nocturn on 2006-01-31
I really support the new license (v3).  It is great to see them address the problem with both patents and DRM, two things I consider a grave threat to Free Software and Freedom in general.

---

### Post by Gadren on 2006-01-31
No matter whether GPLv2 or 3 is better, Linux cannot practically move to it.  To do so would require approval from every single contributor to the kernel.

---

### Post by Viro on 2006-01-31
Bigger numbers are not always better ;). To relicense the kernel will require a lot of work in getting all the contributors to agree on moving to GPL v3. Now, if you've ever run a committee, you will know that getting 100% support is impossible. Just look at most democratic governments, and you'll see what I mean. 

Without 100% support for the move, there are 2 possible outcomes. They can stay put with the v2 license (after all, why fix what ain't broke?) or they can opt to move to v3 and re-code all the parts of the kernel that can't be moved to v3 (a potentially difficult task).

So the question is, why bother with the upgrade to v3?

---

### Post by Miguel on 2006-01-31
Hi nocturn,

I think that, if it happens, it will take a long time. Maybe kernel 2.8. Maybe. The question is: what do we gain with GPLv3? And the answer is: "DRM and patents are issued directly". I do fear that, with Digital "Restrictions" Management and "Treacherous" Computing, we are again facing that primordial "Freedom or Death" question.

Freedom or death. Are people ready to risk it? I don't know. Especially now that companies seemed to start supporting linux (again, I would not need companies supporting linux if they really respected linux users). Someone said at osnews that Linus should avoid things like Disney using linux to create movies that wouldn't play on linux.

Anyway, I personally would support a calmed down approach from the Kernel. Without absolutes. With an open mind. And, please, not too slow. Let's see what happens.

Jus tmy two cents

---

### Post by Lovechild on 2006-01-31
This poll with change nothing, it is meaningless to ask non copyright holders if they think switching license would be a good idea. 

That being said, if you want a gplv3'ed kernel it seems that OpenSolaris might be the way to go, at least if SUN dual license their code.

---

### Post by nocturn on 2006-01-31
[QUOTE=Gadren]No matter whether GPLv2 or 3 is better, Linux cannot practically move to it.  To do so would require approval from every single contributor to the kernel.[/QUOTE]

Actually not.  If you licensed things with the standard text of the GPLv2, it specified licensed under the GPL version 2 or later.

It's also not a technical problem for Linus but rather a disagreement with the limits the GPLv3 places on the use of DRM.

---

### Post by nocturn on 2006-01-31
[QUOTE=Lovechild]This poll with change nothing, it is meaningless to ask non copyright holders if they think switching license would be a good idea. 

That being said, if you want a gplv3'ed kernel it seems that OpenSolaris might be the way to go, at least if SUN dual license their code.[/QUOTE]

The poll is merely a means to seek the opinion of the people on the forum since be do have a vested interest in this project.

And how do you know there are no copyright holders here?  I mean, there may be people present that contribute to the kernel development (I do say "may").

---

### Post by Viro on 2006-01-31
[QUOTE=nocturn]Actually not.  If you licensed things with the standard text of the GPLv2, it specified licensed under the GPL version 2 or later.
[/quote]

The standard text in the kernel is to use GPL version 2 _only_. This is thanks to Linus' foresight, because if you leave the "or later" clause, you are at the mercy of whoever writes the GPL. This is Linus' posting on [lkml](http://lkml.org/lkml/2006/1/25/273), concerning GPL 3. Notice he stresses that the kernel is GPL 2 only and does not default to GPL 3.

> 
It's also not a technical problem for Linus but rather a disagreement with the limits the GPLv3 places on the use of DRM.

How can a license ever be a technical problem?

---

### Post by nocturn on 2006-01-31
[QUOTE=Viro]The standard text in the kernel is to use GPL version 2 _only_. This is thanks to Linus' foresight, because if you leave the "or later" clause, you are at the mercy of whoever writes the GPL. This is Linus' posting on [lkml](http://lkml.org/lkml/2006/1/25/273), concerning GPL 3. Notice he stresses that the kernel is GPL 2 only and does not default to GPL 3.
[/quote]

I know Linus did this (or he could not choose to stay at version 2).  But I don't know about the code/modules that weren't written by him.  So parts of the kernel may become GPLv3 automatically.


> 
How can a license ever be a technical problem?

I actually meant a practical problem.  He is not holding the v3 of because of any work load because of the changes, he is holding it off because he does not agree with the contents.

---

### Post by Viro on 2006-01-31
[QUOTE=nocturn]I know Linus did this (or he could not choose to stay at version 2).  But I don't know about the code/modules that weren't written by him.  So parts of the kernel may become GPLv3 automatically.
[/quote]

So what is the point of the poll? It all rests with Linus and the kernel developers who have explicitly licensed their code with the GPL 2 license. 

> 
I actually meant a practical problem.  He is not holding the v3 of because of any work load because of the changes, he is holding it off because he does not agree with the contents.

You're ignoring the fact that some of the developers have either gone missing from the scene, or have died. I can't find the LKML posting for this claim, but it was made on the mailing list. If they have died, the copyright passes to the heirs of the developer, and their permission is needed to relicense the kernel to GPL v3. You can't just relicense it without permission, as it could have major repercussions down the road.

Even in the absence of these problems, the problem of getting *all* developers to agree to the change in license is a major issue. If you think it isn't a problem reaching an agreement, you have never worked in a large group/committee. 

There are _many_ _practical_ problems with moving the kernel to GPL v3. I don't know why you keep insisting there are none, and why so many non-developers are jumping up and down about Linus not wanting to move to GPL v3.

---

### Post by nocturn on 2006-01-31
[QUOTE=Viro]So what is the point of the poll? It all rests with Linus and the kernel developers who have explicitly licensed their code with the GPL 2 license. 
[/quote]

The point of the poll is that Linux disagrees with the new license.  I wanted to know where the forum users stand on this, the intent of the poll is not to change the kernel license.

I happen to support the new version because of the patent and DRM clauses.

> 
There are _many_ _practical_ problems with moving the kernel to GPL v3. I don't know why you keep insisting there are none, and why so many non-developers are jumping up and down about Linus not wanting to move to GPL v3.

I know that, but I mean that these practical reasons are secondary.  Linus is not rejecting v3 on a practical base, but because he does not agree with the DRM clause.  

I for one would welcome the switch of all kernel code in the long run, though I realize it would take time, but it can be done one module at a time if it is wanted.

---

