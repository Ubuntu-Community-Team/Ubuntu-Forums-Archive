---
title: "Idea: Hardware Proprietary Codec PCI Card"
date: 2008-05-11
forum: The Cafe
---

### Post by Xanderfoxx on 2008-05-11
What if I developed a PCI Express 1x card, and put a whole bunch of licensed proprietary codecs on the card in interchangeable sockets?

This way, one would never need to use proprietary software codecs in an otherwise free and open source computer.

My initial idea is this: We use a set of registered and open source dummy codecs that transparently offload the requests for encoding, decoding, or transcoding to the hardware, which takes care of the actual tasks given, and allows things as abominably proprietary as WMA, WMV, MP3, MOV, DIVX, RA, RV, and such to be encoded, or at least decoded. The card takes care of all DRM functions through a central controller chip, which also schedules tasks between codec modules, and therefore, we can open files protected by DRM, such as DVDs, CDs, and MP3s.

Do you think that

[LIST=1]
[*]This would be feasible/possible?
[*]This would be desirable/demanded?
[/LIST]

You may correct me on any point or assumption, but please redirect outright flames to /dev/null. Thank you in advance!

---

### Post by hessiess on 2008-05-11
it would solve the lack of DRM support on Linuix, witch may make media companys more willing to suport it. problem would be that if sutch a divice could be macufactured, would offitial linux drivers actualy exist.

---

### Post by Polygon on 2008-05-11
it could techincally work, but getting all the licencing squared away would be a nightmare, and the legaities would be too. You would have to get EVERYONE to agree to this.

not to mention it owuld be outdated quickly...an update to like the mp3 or dvd spec = bam outdated

---

### Post by Xanderfoxx on 2008-05-11
The fact that it would be outdated fairly quickly is a good point. We might do firmware on interchangable flash chips that can be updated yearly (subscription per year), but does not really interface the operating system expect through the controller chip, open source drivers, and the dummy codecs.

---

### Post by eragon100 on 2008-05-11
Why is this interesting? What's wrong with just pushing the ubuntu-restricted-extras button whenever as part of the post install setup procedure (i.e. together with any available propietary drivers in restricted and updates) :confused:

---

### Post by Xanderfoxx on 2008-05-11
Because, then you'd actually have the proprietary drivers, or replacements for them, in your OS.

So I take it you are against?

---

### Post by Xanderfoxx on 2008-05-11
Yeah, the DRM could easily be done in hardware, or at least in upgradeable firmware.

And to answer the questions of others, this is only until we can move the market over to open standards, and that will take a long time.

Other question: The proprietary drivers given have restrictions on their use. If they are relagated to hardware, one would treat it like any other physical immovable object: ignore it unless it's broke, or hits you in the face.

Another question: This would ensure the OS is pure, since every codec is covered.

I'm repeating myself, so I'll be quiet now.

---

### Post by Frak on 2008-05-11
Sounds good in concept, but since updates are being launched around everyday, and with the threat of firmware holes being exploited there is some weariness to it.

Good idea though, still.

EDIT
Forgot about drivers. If its DRM hardware, then DRM enforced drivers usually accompany it (what MS calls double satisfaction)

---

### Post by LaRoza on 2008-05-11
Hardware DRM is the worst kind.

---

### Post by Frak on 2008-05-11
> **LaRoza said:**
> Hardware DRM is the worst kind.
Does it make you think of Trusted Computing?

---

### Post by LaRoza on 2008-05-11
> **Frak said:**
> Does it make you think of Trusted Computing?

You are psychic.

---

### Post by qazwsx on 2008-05-11
No!

I don't want invest to H.264 or Divx PCI hardware :) and upgrades.


Besides some open source codecs  (x264, xvid) are just wonderful. Me likes. Just compare them to closed source equivalents. I just can't feel your patent related pain ](*,)  ](*,)

Fluendo offers closed source decoders.

---

### Post by Frak on 2008-05-11
> **LaRoza said:**
> You are psychic.
Even better Mind-Reader (TPM_TakeOwnership has disabled the use of the word "psychic" in an effort to help out those who profit on the phrase "Mind-Reader". Thank you for your understanding.)

---

### Post by red_Marvin on 2008-05-11
I would think that those who want the codecs to just work tm would find it easier to just install them as eragon100 said, and those who don't want proprietary codecs in their os would likely want to avoid it in hardware too.

Another problem is the target audience, Windows and Mac users get codecs because MS or Apple or whoever pays somebody license fees, so those who remain, linux users and others would be the target which is a fairly small market, but "oh, and you need extra hardware" won't convert many people to linux.

However if it could be built in and integrated into the soundcard or something like that then it might become profitable.

---

### Post by Xanderfoxx on 2008-05-18
Understood. You make perfect sense. Thank you.

---

### Post by Xanderfoxx on 2008-05-18
Excellent! Thank you for the tip.

---

### Post by jpkotta on 2008-05-18
Ignoring the fact that this isn't the sort of problem that makes sense to solve in hardware, it would be more expensive and more work than just getting the codecs legally bought and paid for.  Because you have to get the licensing squared away for either hw or sw.  With software, that's basically the only monetary cost, because we'll assume that free software programmers will or have implemented it.  With hardware, you have many more costs, many more potential problems that are harder to fix, etc.

---

