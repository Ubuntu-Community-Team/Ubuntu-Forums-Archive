---
title: "Forbes.com : &quot;A setback for Linux&quot;"
date: 2005-05-26
forum: The Cafe
---

### Post by nocturn on 2005-05-26
From The Register : [http://www.theregister.co.uk/2005/05/26/bitkeeper_fiasco_is_setback_for_linux/](http://www.theregister.co.uk/2005/05/26/bitkeeper_fiasco_is_setback_for_linux/)

About the Bitkeeper fiasco.  
I personally feel that they are blowing this way out of proportion.  
Though, the incident does show the danger in using proprietary software, even when it is offered for free.

---

### Post by dataw0lf on 2005-05-26
Well, I think Torvalds and McVoy have been the ones 'blowing things out of proportion', but that's just me.

---

### Post by Lovechild on 2005-05-26
McVoy dislikes the fact that he and his aggressive use of licensing got.. pwned - if one might.

honestly Git was developed in a few months and it's already mature enough to handle something as big as the Linux kernel, that's not bad - I dunno why they thought it would be such a big problem before that a closed source program was our only salvation?

---

### Post by poofyhairguy on 2005-05-26
[QUOTE=Lovechild]
honestly Git was developed in a few months and it's already mature enough to handle something as big as the Linux kernel, that's not bad - I dunno why they thought it would be such a big problem before that a closed source program was our only salvation?[/QUOTE]

Personally I always saw Linus using that software as an olive branch. "See, using Linux doesn't mean you are a zealot about open software. The kernel is maintained by closed software for cripes sake." I've used it before to defend Linux. Now I feel bad about it....

---

### Post by TravisNewman on 2005-05-26
I have quite a few mixed feelings about this.

I do think that if an open source, fully capable alternative exists, Linus might want to think about switching.

but if he doesn't, he doesn't, and it's not a big deal.

---

### Post by tread on 2005-05-27
Andrew Tridgell has been portrayed a bit unfairly in that article, hasn't he? Besides, I think it's hypocritical to applaud him for Samba and criticise him for Bitkeeper .. it wasn;t as if he was trying to clone Bitkeeper anyway.

---

### Post by 23meg on 2005-05-27
while i'm saddened that my long wait for 2.6.12 just got even longer, i don't think this will have any long-term impact. it's just a shame that Linus and his folks didn't allocate a small bit of their time to develop a good open source alternative before "disaster" sturck, since it was so obvious that it would strike someday.

---

### Post by rjs on 2005-05-27
When asked why he called the new software, "git," he said. "I'm an egotistical bastard, so I name all my projects after myself. First Linux, now git."

God he's a funny bastard. What's amazing is that english is his third (human) language, and he is still capable of playing with words in it.

paz y amor,
-rjs

---

### Post by nocturn on 2005-05-27
[QUOTE=tread]Andrew Tridgell has been portrayed a bit unfairly in that article, hasn't he? Besides, I think it's hypocritical to applaud him for Samba and criticise him for Bitkeeper .. it wasn;t as if he was trying to clone Bitkeeper anyway.[/QUOTE]

I think he has been portrayed unfairly through the whole episode.
You know that all he did was telnet to the bitkeeper port and typing h or help (I think) to see a list of available commands.
That's the extend of reverse engineering he did.

---

### Post by nocturn on 2005-05-27
[QUOTE=panickedthumb]I have quite a few mixed feelings about this.

I do think that if an open source, fully capable alternative exists, Linus might want to think about switching.

but if he doesn't, he doesn't, and it's not a big deal.[/QUOTE]

The bad thing about Torvalds using bitkeeper for the kernel development was that all kernel devs were forced to use bitkeeper too, although many objected to the non-free nature of the software.

Even without a fully capable alternative, what happened clearly demonstrated the danger of using such tools, even when offered for free.

---

### Post by nocturn on 2005-05-27
[QUOTE=dataw0lf]Well, I think Torvalds and McVoy have been the ones 'blowing things out of proportion', but that's just me.[/QUOTE]

Yes, they have.  I'm especially disappointed in Linus because not only did he support proprietary software but he also turned on Tridge while all the guy did was telnet to the bitkeeper port to get a list of commands.

I also suspect that McVoy is overplaying the capabilities of his software.

---

### Post by TravisNewman on 2005-05-27
If you're mad at Linus for supporting proprietary software: do you have w32codecs, an mp3 decoder, libdvdcss, or nvidia/ati binary drivers installed? If so, you're also supporting proprietary software.

What concerns me is that bitkeeper, as the article says, found that backdoor that someone tried to implement in the kernel. If git isn't powerful enough to do that, we DO have some security concerns.

---

### Post by nocturn on 2005-05-27
[QUOTE=panickedthumb]If you're mad at Linus for supporting proprietary software: do you have w32codecs, an mp3 decoder, libdvdcss, or nvidia/ati binary drivers installed? If so, you're also supporting proprietary software.
[/quote]

I'm not flaming him for using a proprietary program, just that his decision affected everyone working on the kernel, so effectively requiring them to run non-free software too resulting in the problems we see today.

Secondly, I am somewhat mad about the way he came out against Tridge while all the guy did was get the bitkeeper commands over telnet.  Apparently, Linux thinks it is OK to reverse-engineer the protocols needed for Samba, but not Bitkeeper.

> 
What concerns me is that bitkeeper, as the article says, found that backdoor that someone tried to implement in the kernel. If git isn't powerful enough to do that, we DO have some security concerns.

That is what McVoy said.  I don't know the specifics but it is quite possible that it would have been caught by a system such as SVN too or maybe Git handles it as well.

---

### Post by TravisNewman on 2005-05-27
"Apparently, Linux thinks it is OK.."

Thank god I'm not the only one who tries to type Linus and accidentaly types Linux. All the time ;)

---

### Post by WildTangent on 2005-05-27
[QUOTE=panickedthumb]What concerns me is that bitkeeper, as the article says, found that backdoor that someone tried to implement in the kernel. If git isn't powerful enough to do that, we DO have some security concerns.[/QUOTE]
that would worry me as well, one person having control of...well i dont even know how many people use linux...that would definately be bad

-Wild

---

### Post by NoTiG on 2005-05-27
the part i dont understand is: McVoy says the cost of offering free support to Linux developers has grown to more than $500,000 a year, and he can't afford to keep paying the tab himself. "It was just becoming prohibitively expensive," he says.


So why does this mean that the linux developers can't use bittkeeper WITHOUT support? for free? Why is it free, and with free support... or not at all ??

---

### Post by Jenda on 2005-05-27
McVoy, above all, desires to sell, and therefore he overplays the power of BK. No offence against him - he's trying to make a living.
> 
that would worry me as well, one person having control of...well i dont even know how many people use linux...that would definately be bad
I heard an estimate of 30 M, which I like a lot...

---

### Post by biguns on 2005-05-27
The real question is do you think that open source is viable as a business model. Some good points were made against it in the article . 

I hope they are not true....

---

### Post by nocturn on 2005-05-30
[QUOTE=biguns]The real question is do you think that open source is viable as a business model. Some good points were made against it in the article . 

I hope they are not true....[/QUOTE]

I support Free Software for moral reasons, the question whether it is a viable business model is of lesser importance, although I do believe it is.

The point is that if each public funded entity would release the software they create under the GPL, a lot of the public's money could be saved for not doing the same job multiple times.
So, governments should adopt Linux (or another Free OS), they should improve it where needed and release the changes back to the community, benfitting everybody and providing Linux developers with a living while not needing business.

---

