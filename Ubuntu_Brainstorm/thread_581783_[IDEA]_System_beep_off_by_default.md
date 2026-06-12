---
title: "[IDEA] System beep off by default"
date: 2007-10-19
forum: Ubuntu Brainstorm
---

### Post by greeneemer on 2007-10-19
_Summary:_
The system beep is on by default after an installation. This should be off.
_Rationale:_
I don't know anyone who doesn't turn this one off after hearing it the first time (if they can find where to). It does not add any extra usability, but it annoys people.
_Implementation Plan:_
Just turn it off in the default configuration. Those who really want it will probably know how to turn it on again.

This is a repost of the same idea from the Gutsy idea pool.
Link: [http://ubuntuforums.org/showthread.php?t=430910](http://ubuntuforums.org/showthread.php?t=430910)

---

### Post by glupee on 2007-10-19
beep? what beep?

---

### Post by m0eman on 2007-10-19
Maybe if a soundcard was detected, no system beep, but if no soundcard is recognized, the system beep is enabled. (I should have voted other(I voted yes)

---

### Post by greeneemer on 2007-10-19
> **glupee said:**
> beep? what beep?Launch a terminal and press tab. This is the easiest way I came to think of.

---

### Post by screaminj3sus on 2007-10-19
My sound works perfectly in gutsy, but whenever I delete and icon off of my desktop for an example I get the system beep.

---

### Post by zsouthboy on 2007-10-19
> **m0eman said:**
> Maybe if a soundcard was detected, no system beep, but if no soundcard is recognized, the system beep is enabled. (I should have voted other(I voted yes)

I would accept this as a compromise.

At the same time, I can deal with just blacklisting the system buzzer module on my own boxen.

I don't know how often a "normal" user will even encounter the "beep" - except for the login screen (if the sound is turned off for that event)

---

### Post by Zdravko on 2007-10-20
The system beep is a kind of a system's response to user's actions. I don't see a real reason why it should be disabled.

---

### Post by glotz on 2007-10-20
It's a unix thing. It is there because it is useful. Should be ON by default.

---

### Post by Lozz on 2007-10-20
> **m0eman said:**
> Maybe if a soundcard was detected, no system beep, but if no soundcard is recognized, the system beep is enabled. (I should have voted other(I voted yes)

The beep is very annoying in my opinion but this sounds like a fantastic compromise.

---

### Post by Zdravko on 2007-10-21
Don't remove the beep. It is pure classic!

---

### Post by YetAnotherNoob on 2007-10-21
The pc speaker beep is a joke.  It is a hangover from the old terminal days and (IMHO) should not be on by default.

If ubuntu is serious about breaking out of the home/hobbiest realm and into an office environment it should be disabled.  Having systems sounds in an office is a definte no-no.  Especially when the are as loud and obnoxious as the pc speaker.

Keep in mind there is no volume for this like there is for wav.

---

### Post by usien on 2007-10-22
off by default.imo visual feedback should be enabled by default, it looks great on compiz and you don't have to jump off your seat when you hear that dreaded BEEP!

---

### Post by m0eman on 2007-10-22
> **usien said:**
> off by default.imo visual feedback should be enabled by default, it looks great on compiz and you don't have to jump off your seat when you hear that dreaded BEEP!

Does metacity support visual feedback instead of a system beep? If so this would be great.

---

### Post by tubasoldier on 2007-10-22
From the inner recesses of old technology the system beep comes up and bites me as I compile my latest java program during class. Heads turn and eyes stare as I have just rudely interrupted the professor with my old crappy technology.

It should seriously be off. There is no reason why it should remain on. For those who think it is truly useful, you can enable it on your own.

---

### Post by Biochem on 2007-10-22
There is a way to turn it off !!!!

PLEASE tell me how I tried System>Administration>Sound>SystemBeep and uncheck it but it's still there even in Open office.

Off course, off by default it would be a good idea. The few nostalgic who wants it would probably know how to modify this behavior anyway.

---

### Post by Xbehave on 2007-10-22
always off! even if your soundcard isnt detected he beep is just a pain at best (or worse an insult its like "hi im ubuntu you dont have sound but...BEEEEEP....have a headache instead"
p.s ubuntu is linux for humands not for nostalgic geeks who enjoy beeps and terminals
p.p.s visual feedback is a bit of a pain its better to highlight the taskbar entry and leave it at that by default, lets not end up with windows nudging you

---

### Post by usien on 2007-10-22
> **m0eman said:**
> Does metacity support visual feedback instead of a system beep? If so this would be great.

system > preferences > sound > system beep > check visual system beep and uncheck enable system beep

the 'Flash Window Titlebar' option looks great with compiz!

---

### Post by exile on 2007-10-22
Please TURN IT OFF! Or as part of the install just ask the question in an advance tab or something?

"Do you wish system beep to be enabled?" with a suitably concise explanation of what the hell it is for the average user.

---

### Post by Shootfast on 2007-10-23
For the love of god, yes please! Turn this off. Or just blacklist pcspkr if a sound card is detected

---

### Post by allquixotic on 2008-02-04
On my Lenovo Thinkpad X60, the system beep is sent via the BIOS attaching to the soundcard momentarily, and sending a 100.0% **maximum volume**, high-pitched beep through the soundcard. If no headphones are plugged in, the laptop itself emits a rather loud beep from the speaker, but that's not the worst part... if you're wearing headphones, a single system beep comes out at about 130 dB! It's absolutely insane that they would design a computer that does this, without any visible way to at least change the volume (read: turn it WAY the heck down!)

By this logic, every single time I install a new distro or kernel image, I have a script that finds all pcspkr.ko modules in /lib/modules/ and does a **sudo rm -f** on them. It also does a modprobe -r -f on them.

I find this feature to be EXTREMELY annoying (and even physically painful) when I accidentally leave it enabled and I am nearly deafened. It's obsolete. And hardware manufacturers have to exacerbate the problem by deafening their users. It's the biggest complaint I have about this otherwise wonderful laptop.

Regards,

Sean

---

### Post by CarpKing on 2008-02-04
Please turn it off by default.  It is annoying and serve no useful purpose (or if it does to someone it's a small enough niche that I cannot even comprehend what that use would be).  Those of you who voted to have it on by default should tell us how it benefits any sort of user, especially a non-technical one.

---

### Post by pacsum on 2008-02-06
Since I moved to Ubuntu last May I've seen a lot of threads about this with no succes.
By this you can see how much this forums influence the developers.

---

