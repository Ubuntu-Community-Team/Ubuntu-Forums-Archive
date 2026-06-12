---
title: "Soundfonts seem to have random key velocity"
date: 2012-09-23
forum: Ubuntu Studio
---

### Post by Sylos on 2012-09-23
Hello all.

I have been having this problem for a while and I cant make out whether its just the way the soundfonts are or whether its my set up. When I load a soundfont into Qsynth and play using my M-Audio Oxygen 8 midi keyboard I get odd key velocities. If I play a sequence of notes some of them come out really low volume - like I havent pressed the key properly. This seems to happen with any soundfont I use (I've tried 30 or 40). Its winding me up.

It would be safe to say that I have had a fair bit of trouble getting a working set up and I have a variety of other problems (apps that close when selecting preferences etc). So my system is a bit of a dog to work with in some senses (despite spending a fair bit on building my PC from scratch). I'll spare everyone the rant (nobody needs to read the frustrations vented by a half baked hobby musician) but I will say its riding me like any angry monkey right now (I'm not gonna blame Ubuntu, the devs or any of the usual suspects).

So Im wondering if anyone has any ideas on what is causing this specific issue. I kinda doubt that its all the soundfonts are made such that this happens (that would make them pretty useless in my eyes). It must be something at my end - but what?

Cheers

EDIT: I have tried using the M-audio keyborad velocity settings but it doesnt cure the problem.

---

### Post by jejeman on 2012-09-23
Is this happening only with MIDI keyboard?
I mean, when typing notes and setting velocity for them, is that playing correctly?

---

### Post by Sylos on 2012-09-24
What do you suggest trying it with? Seq24 maybe? I dont do midi sequencing so I dont know what prog to use or how to set them up and use them. If you can give me a suggestion I'll give it a shot.

I have to admit - I lost my rag with it yesterday. Grabbed a Tango Studio DVD I had lying around and whacked it in for an install. Bye bye Ubuntu Studio (for now at least). First impression of Tango seems pretty good. I cant tell for sure but it seems like the presets on Zynaddsubfx sound a lot better than they did before - and it hasnt crapped out on me when changing banks etc (which is nice). Could it be that my poorly running set up was making things sound pants as well?

I have to admit I feel a slight pang of betrayal for leaving Ubuntu Studio - like I've shacked up with the missus' little sister. Im not proud of myself for it but Tango does seem pretty nice.

Anyhow, back to the point - I tried a couple of soundfonts and they seemed to suffer just the same. Its not random actually - it just seems the velocity difference is over sensitive. A very small change in how hard I press results in a seemingly over blown change in volume. The only way to avoid it is to slam each key everytime but that is no good for dynamic pieces. 

Cheers

---

### Post by jejeman on 2012-09-24
Yes, Seq24 would do just fine. Put couple of notes, and alter their velocity, see how volume reacts.
> I have to admit I feel a slight pang of betrayal for leaving Ubuntu Studio - like I've shacked up with the missus' little sister. Im not proud of myself for it but Tango does seem pretty nice.Ha, ha. No betrayal man. Only switching to non FLOSS is. ;)

---

### Post by Sylos on 2012-09-25
Cheers for the support - I feel a little less guilty now. :lolflag:

I couldnt figure out Seq24 - couldnt see how I can input notes etc. I did give Rosegarden a whirl and connected that to Qsynth - the velocities seemed to be doing what I told them to. SO it seems the problem is just the midi input from the keyboard being over sensitive to velocity. Is there any way to change it?

Cheers

---

### Post by Sylos on 2012-09-25
Well - it now seems I cant connect my Maudio Oxygen 8 to Zynnaddsubfx or Yoshimi. They appear in the connections window but I dont get anything through. It still connects to Qsynth though (but the problem persists). 

The love affair with Tango may be brief.....

---

### Post by jejeman on 2012-09-25
> **sylos said:**
> the love affair with tango may be brief.....
 :) :)

---

### Post by Sylos on 2012-09-26
Seems I must have leant on my Maudio and switched the midi channel over. I now have Zynaddsubfx working again. Still no progress on the Soundfonts though. Although it does seem to be worse with some soundfonts than others. Maybe it is just the soundfont.

That being said, I have tried it with Qsampler (linuxsampler front end) and the messages window seems to be saying something about maximum input being exceeded when I press a key on the Maudio. I didnt really think about the significance of it until after I had shut down. I'll captur the message later and post it up - maybe it has something to do with the problem.

As for me and Tango - for now we're trying to talk through our problems. ;) (I'll keep my feet off the sofa is she quits complaining).

Cheers

EDIT: Heres the message from linuxsampler when pressing the keyboard keys:

```
sf2: GetInitialFilterFc() is above the maximum allowed value (max=13500): 27000

```
Using one of the fixed velocity settings on the Maudio irridactes this message and results in a stable key velocity (meaning I cant use velocity for expression etc but at least dont have it dropping to an inaudible level). 

Could it be Im just a ham fisted troll with equipment vastly superior to his skill?

EDIT2: Seems that the error message is dependent on which soundfont I am using. Some have it and some dont.

---

