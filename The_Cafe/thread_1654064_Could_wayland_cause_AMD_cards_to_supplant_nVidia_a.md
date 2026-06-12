---
title: "Could wayland cause AMD cards to supplant nVidia as cards of choice for linux users?"
date: 2010-12-27
forum: The Cafe
---

### Post by Dustin2128 on 2010-12-27
I've been looking at wayland a little bit and it seems intriguing, eliminating dependence on x server. Anyway, looking at the wikipedia page, it says nVidia currently has no plans on supporting it in their proprietary drivers. The reason why they're so big on linux systems is because their proprietary drivers "just work". You can pretty much plug in any card that says nvidia, and expect to be gaming in 5 minutes or less. ATI's been catching up a bit since their acquisition by AMD, in both open and closed drivers. If they do support wayland and nvidia doesn't, do you think that 
a. nvidia will feel the competitive pressure and start supporting it,
b. nouveau drivers will improve exponentially,
c. nvidia users will just use x, or
d. AMD cards will become the most popular on linux systems

sorry if this is a duplicate thread, I couldn't find any others though. (But it seems like a topic that would have come up at least once before)

---

### Post by bxcrx on 2010-12-27
Nope Nvidia would not give up their audience they currently have for no good reason.  Nvidia makes drivers for Linux usage first before they make it for X per say. If Nvidia plans to keep it's Linux fans happy they will support new display managers whether its X, or Wayland.   

The devil is in the details and Nvidia wants to make sure it has all of it's details before is speaks about anything.  If anything they are telling the truth currently -- We don't work with it therefore we're not going to say we currently support it, and we don't know when we will.

The case has to prove itself first.

---

### Post by handy on 2010-12-27
My understanding on why the nVidia drivers have always been in good shape for the distros, is that there are some very big companies that work with graphics & they use lots of very expensive nVidia cards.

As a spin off, the lowly distro user has been well looked after by nVidia.

AMD have been putting an enormous amount of work into the FOSS driver stack. They have opened much of their code & technical details & contributed extremely important code to the FOSS driver stack. This is why over the last year or so the AMD open drivers have come along in leaps & bounds.

The way I see it, is that ultimately the AMD cards will perform optimally on Linux kernel based systems & will be kept up to date with all of the changes in the Linux kernel based systems far better than nVidia or any other closed system, due in combination to the open assistance from AMD & the many FOSS dev's that will be maintaining the driver stack - "for free".

This will very likely cause nVidia to eventually open up their code & technical information also, in an effort to compete with AMD, as AMD will also eventually have a Linux system driver base of such quality that they can compete with nVidia at the very top end in graphic design where nVidia now has it on its own.

In the end, it will be all good for the lowly us. :)

---

### Post by ubunterooster on 2010-12-27
AMD and ATI have been the same company for years (or have they always been?) the name was what was changed.

As AMD is more involved overall in Linux (in raw numbers) than is Nvidia, it seems likely to me that any large change would help AMD catch up and surpass Nvidia

---

### Post by JDShu on 2010-12-28
We don't even know if Wayland really will supplant X, and if it does, it'll be a very long time before it happens. I think we're talking 3+ years, and when its that far into the future, especially in today's age of rapid technology growth, the future is impossible to predict. All sorts of things can change.

---

### Post by handy on 2010-12-28
> **ubunterooster said:**
> AMD and ATI have been the same company for years (or have they always been?) the name was what was changed. 

AMD bought ATi in 2006. The name has recently changed from ATi to AMD re. the GPU's.

---

### Post by Lucradia on 2010-12-28
nvidia will still dominate the graphics market as the most supported video card.

> **JDShu said:**
> We don't even know if Wayland really will supplant X, and if it does, it'll be a very long time before it happens. I think we're talking 3+ years, and when its that far into the future, especially in today's age of rapid technology growth, the future is impossible to predict. All sorts of things can change.

You know, not everyone knows thatt he word "Supplant" means "to replace," and will probably say "a supplement?" To your word if they are "too lazy to look it up."

Anyway, my opinion to your reply: No. It really won't take that long; big companies like nvidia, who adapt to X rather than the other way (AMD isn't good at adapting in terms of graphics; while their processors are awesome at adapting, in comparison to Intel) will adapt quickly to wayland.

---

### Post by handy on 2010-12-28
> **Lucradia said:**
> nvidia will still dominate the graphics market as the most supported video card.

Hows that?

If a GPU manufacturer presents with better value for money; better performance; reliability; more up to date drivers; open drivers as well, why wouldn't it be more popular?

When nVidia came on the scene the Voodoo cards were the ducks guts. nVidia Riva 128 made dramatic inroads into the Voodoo dominance due to it out performing the Voodoo GPU's. Then the TNT came along & that was basically the end of the Voodoo reign. Eventually nVidia bought the Voodoo company.

So I don't see any reason why nVidia has to hold onto its crown when the vote comes from the people's choice. AMD are well positioned to steal the crown & I certainly hope that they do. As they have shown their support for Linux & FOSS.

---

### Post by Lucradia on 2010-12-28
> **handy said:**
> So I don't see any reason why nVidia has to hold onto its crown when the vote comes from the people's choice. AMD are well positioned to steal the crown & I certainly hope that they do. As they have shown their support for Linux & FOSS.

AMD is going to start producing On-Die GPUs with their motherboards, which will require a different support method over normal on-board graphics.

As for dedicated graphic cards, whether they be mobile or desktop; I've had nothing but trouble (choppy composition, very little support for 3D Composition in open-source land with the newest model of video cards, etc.) with ATI and Intel, so it's no wonder why I like nvidia over them. Some 5XXX cards still don't support most 3D Composition, etc. while my nvidia GTX 470 does fully, albiet still a bit choppy (especially on Cube in compiz.)

---

### Post by murderslastcrow on 2010-12-28
You need to realize there are some industries where Linux dominates the graphics processing elements, most notably 3d animation. If NVIDIA didn't supply GPUs for those businesses at all, they would lose a big chunk of their revenue. It's in their best interest to support whatever is most popular in open source for those businesses.

However, I should also make it clear that Ubuntu isn't the dominant choice for those businesses, since they're using mission-critical software where speed and efficiency are the most important thing. They tend to use specialized distributions, which may not be so apt as Ubuntu to drop X early.

I think it'll be a little while after Ubuntu adopts Wayland for all the graphics companies to pay attention, unless Canonical becomes partners with NVIDIA in some fashion. You need to realize this involves writing brand new software for a specific distribution when most other distributions will likely continue to use X for a bit longer. It wouldn't make much sense to support it without popularity in the open source community.

We should support the open source endeavors to do graphics drivers in the meantime. Outside of that, I would recommend any serious gamers to stick to X for the time being and sacrifice the small performance increase Wayland could bring.

---

### Post by handy on 2010-12-28
> **Lucradia said:**
> AMD is going to start producing On-Die GPUs with their motherboards, which will require a different support method over normal on-board graphics.

As for dedicated graphic cards, whether they be mobile or desktop; I've had nothing but trouble with ATI and Intel, so it's no wonder why I like nvidia over them.

You aren't taking the currently available info' & using it to project into the realm of future possibilities.

Using our own personal experience as the basis for your projections is unfortunately a very limiting approach when it comes to seeing future possibilities. :)

---

### Post by Lucradia on 2010-12-28
> **handy said:**
> Using our own personal experience as the basis for your projections is unfortunately a very limiting approach when it comes to seeing future possibilities. :)

Especially when personal experiences label lexmark as the most horrible linux printer, and they have no plans to make it more supported. Your Theory = Debunked.

Also, I've always learned something in linux, "Older is better" when it comes to drivers. (Except Lexmark)

---

### Post by handy on 2010-12-28
> **Lucradia said:**
> 
Especially when personal experiences label lexmark as the most horrible linux printer, and they have no plans to make it more supported. Your Theory = Debunked. 

I'm not trying to personally bring you down. :)

& no, my theory is not debunked. There are always exceptions to the rule. & the parameters of discussions on forums are all very loose. We don't define our meanings of words nor do we define the boundaries of our discussion. So misunderstandings are rife under such circumstances.

If you reread what I said & think about it for a while you may understand my meaning.

> **Lucradia said:**
> 
Also, I've always learned something in linux, "Older is better" when it comes to drivers. (Except Lexmark)

I've been driving since 1972, (& my real name is not Lexmark) so I'll always be a better driver than you!

See what I mean about definitions? :)

---

### Post by Lucradia on 2010-12-28
> **handy said:**
> I'm not trying to personally bring you down. :)

& no, my theory is not debunked. There are always exceptions to the rule. & the parameters of discussions on forums are all very loose. We don't define our meanings of words nor do we define the boundaries of our discussion. So misunderstandings are rife under such circumstances.

Even though we're using defined words and symbols right now?

> I've been driving since 1972, (& my real name is not Lexmark) so I'll always be a better driver than you!

See what I mean about definitions? :)

> If you reread what I said & think about it for a while you may understand my meaning.

You're the one misunderstanding now. :)

---

### Post by handy on 2010-12-28
> **Lucradia said:**
> Even though we're using defined words and symbols right now?





You're the one misunderstanding now. :)

Sorry, I didn't mean to turn you into a troll. I'll leave this thread now, enjoy yourself. :)

[I]**[edit:]** Actually I won't leave the thread, I'll just put you on my ignore list so that I won't be able to irritate you anymore.

That works. :)[/I]

---

