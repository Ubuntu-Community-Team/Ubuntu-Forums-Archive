---
title: "Hydrogen samples are sounding very distorted"
date: 2010-03-02
forum: Ubuntu Studio
---

### Post by djm227 on 2010-03-02
I've been getting sick of booting back up into windows in order to use Beatcraft, so I thought I'd give Hydrogen a try today.

I really like the layout of it....but ALL samples in it are messed up.  I don't really know how to explain it...they're distorted, but not all the time.  They sound different every time I click it.  Everything sounds fine when exported, but I can barely make a beat with it sounding like this.  I had a feeling it might of been something to do with a driver...but I don't really know anything about that.  I'm using ALSA right now, which seems to be the only thing that semi works for me.

I could really use some help here...thanks.

---

### Post by JayPeeJay on 2010-03-02
I would check to make sure that the preferences are set to a sample rate that is compatible with your sound card.  For example, I use Audacity for recording, which is automatically set to 32 bit float 44100, and my sound card is an older one that needs to be set at 16 bit, 44800 sample rate.  I was having some distortion issues as well untill I made that switch.

---

### Post by djm227 on 2010-03-03
I gave it a try, but unfortunately it did nothing.

---

### Post by Capoeira on 2010-03-03
i have this problem sometimes with some VSTis. The problem seems jack. Did you try it out without jack (alsa)?

---

### Post by AutoStatic on 2010-03-03
Hello djm227,

Which version of Hydrogen?
Which version of Ubuntu?
What type of soundcard? Could you post the output of the terminal command **aplay -l** ?
Could you post a screenshot of the Hydrogen Preferences window and then specifically the Audio System tab?

Thanks!

Jeremy

---

### Post by djm227 on 2010-03-03
> **Capoeira said:**
> i have this problem sometimes with some VSTis. The problem seems jack. Did you try it out without jack (alsa)?

Worked great!  It's weird though...I tried it without jack yesterday but it told me "a driver could not be found".  Works fine today though, thanks.

---

