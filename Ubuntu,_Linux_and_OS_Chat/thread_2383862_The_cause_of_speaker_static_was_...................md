---
title: "The cause of speaker static was ............................"
date: 2018-01-30
forum: Ubuntu, Linux and OS Chat
---

### Post by kansasnoob on 2018-01-30
We've all dealt with this at one time or another - PC has static in one or both speakers. The first step is to narrow it down to being a problem within the computer itself or something external. That's always pretty easy if you have another computer to swap with. If the other computer produces no static in the same location using the same peripherals, and the effected computer still produces static in it's new location with totally different peripherals you know it's something within that computer.

Of course it could be anything inside the computer from a bad cooling fan to a failing motherboard. The only thing you can do is rule out one thing at a time by either disconnecting it or swapping parts. One of the most common culprits I've found is the power supply itself but that's also generally about the last thing I try if there are no other symptoms of a failing power supply. Oh, something worth having on hand is a USB sound dongle to use just to see if the static persists using it as well as the onboard audio. In this case that solved it, but it's not a real solution.

Well I ran across something that I'd never run across before. I was reviving an old Biostar AMD AM2+ mobo which had always worked OK but had been retired a few months ago and replaced with a more energy efficient PC. I knew it had no static problem when it was tucked away out of sight a few months ago, and I didn't notice any static when I first hooked it back up prior to swapping in some different components. I did swap in a used Athlon 4850e CPU that I knew had been working OK when I boxed it up.

So I was down to either the motherboard, CPU, or power supply. I swapped in a Sempron 140 and the static was reduced by at least 95% - in fact I never would have noticed static at that level - it was barely audible with the sound set to run at full volume (with allow over 100% set as well). It's worth mentioning that the Sempron 140 uses much less power at the wall - according to my Kill-a-Watt meter that box with the Sempron 140 installed uses around 40 to 60 watts depending on load whereas with the Athlon 4850e it uses around 55 to 90 watts. So I thought it could still be the power supply.

Then after sleeping on it I thought this AM about anything and everything I've changed in recent months. One of those "things" was thermal compound. I'd started using Protonix grease in applications where electrical conductivity should not be an issue. It seems to be great stuff and since it's a grease rather than a paste cleanup is much easier. So I swapped the Athlon 4850e back in using Noctua NT-H1 which I use anywhere that electrical conductivity might be an issue.

I'll be darned - zero static now! But I still had to rule out the possibility of some goofy fluke so I pulled the cooler and replaced the NT-H1 with Protonix and sure as the world the static was back! Pulled the cooler and replaced the Protonix with NT-H1 again and the static was gone. So somehow the CPU was radiating just enough electrical interference with the Protonix grease probably conducting that EMI into the cooler which then radiated it to the onboard audio. Who'd of thunk it?

I'm not knocking the Protonix because I've used it on probably 3 dozen PC's without issue but I just HAD to share this silliness :biggrin:

---

### Post by kansasnoob on 2018-01-30
I decided to try one more thing - a different cooler with each type of compound. With a different cooler (totally different design) I get NO static regardless of which compound I use. So it's a combination of the three components. With certain CPU's and certain coolers some thermal compounds can result in audible EFI.

---

### Post by #&amp;thj^% on 2018-01-30
> **kansasnoob said:**
> I decided to try one more thing - a different cooler with each type of compound. With a different cooler (totally different design) I get NO static regardless of which compound I use. So it's a combination of the three components. With certain CPU's and certain coolers some thermal compounds can result in audible EFI.

Wow>>  this is good infirmation to keep in mind when trouble shooting.
Thanks for your findings kansasnoob. BTW Long time no see.

---

### Post by Geoffrey_Arndt on 2018-01-31
This is also another reason passively cooled systems (no, fan . . no incoming dust) like the Sys76 Meerkat reduces these kind of issues.

---

### Post by kansasnoob on 2018-02-01
> **Geoffrey_Arndt said:**
> This is also another reason passively cooled systems (no, fan . . no incoming dust) like the Sys76 Meerkat reduces these kind of issues.

Just disconnecting the fan made no difference, but I do get what you're saying. I've built a few newer machines using ASRock mobos with embedded CPU's and passive coolers. They're sweet. With prices continuing to drop on SSD's we'll soon see many computers with zero moving parts. Actually I've torn apart a few dead laptops that already filled that bill, but they were fried so I can't say that worked out yet.

---

