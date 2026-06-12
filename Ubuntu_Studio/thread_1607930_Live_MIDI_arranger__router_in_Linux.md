---
title: "Live MIDI arranger / router in Linux"
date: 2010-10-28
forum: Ubuntu Studio
---

### Post by Tarrasque on 2010-10-28
I'm sorry, but I don't know exactly how to call the link of software I'm looking for, so I ended by calling it an "arranger" or "router" in the topic title.

Basically what I'm asking is: if I have a midi keyboard plugged in my UbuntuStudio box, let's say it's on channel 1, is there a program that's capable of altering the notes I'm playing on the fly and "route" them on different midi channel based on "rules"?

Can I' let's say, play a 3 voice chord and have each of the 3 voices be "routed" to channels 2, 3 and 4?

This would be most helpful, and actually is what I'd like to do, to play brass or wind sample sections, where the lowest note is fed to the trombone, the middle to the horn and the highest to a trumpet...


Thks for answers

---

### Post by AutoStatic on 2010-10-28
Hello Tarrasque,

In the standard repositories there is qmidiroute. And both[ FalkTX]("https://launchpad.net/~falk-t-j/+archive/lucid") and [philip5]("https://launchpad.net/~philip5/+archive/extra") have arpage in their PPA's that comes with zonage, another software MIDI router.

Best,

Jeremy

---

### Post by Tarrasque on 2010-10-29
Thanks for the reply. :)

I'll try them as soon as I can. Do you think they are "intelligent" enough to do what I'm looking for? Basically, determine if more than one note is played simultaneously and route all voices to different channels?

BTW, I heard of a program called mididings that could be useful. I think it routes midi events via Python scripting, so it could, I hope, be programmed to do what I want. DOes anyone know it?

P.S.

Falk is the group that develops KXStudio, isn't it? Aren't their repositories for Lucid Lynx? I'm using Maverick, can I use their repositories?

Thanks again

---

### Post by AutoStatic on 2010-10-29
> **Tarrasque said:**
> I'll try them as soon as I can. Do you think they are "intelligent" enough to do what I'm looking for? Basically, determine if more than one note is played simultaneously and route all voices to different channels?That should be possible I think. But I've never played around seriously with these tools as I have no use for them (yet).

> **Tarrasque said:**
> BTW, I heard of a program called mididings that could be useful. I think it routes midi events via Python scripting, so it could, I hope, be programmed to do what I want. DOes anyone know it?Yes I know it, it will probably offer the most flexible routing options. But haven't worked with it either.

> **Tarrasque said:**
> Falk is the group that develops KXStudio, isn't it?Yes, but he's a single person, not a group.

> **Tarrasque said:**
> Aren't their repositories for Lucid Lynx?Yes.

> **Tarrasque said:**
> I'm using Maverick, can I use their repositories?I wouldn't recommend installing packages build for another release. So I'd say no.

---

