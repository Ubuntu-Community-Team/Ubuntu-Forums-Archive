---
title: "Detune plugin/effect for linux?"
date: 2011-12-20
forum: Ubuntu Studio
---

### Post by decomp on 2011-12-20
Hi All!

I am looking for an effect that will 'detune' a track about 5% in realtime.

I have recorded a guitar track in ardour, and would like to send a copy out to a bus, detune it, and pan each to the left and right - the idea is to make it sound like the guitar was recorded twice, for a thicker sound.

I have found harmonizers and pitch shifters in rakarrack but they only have settings for a complete note - I just want a little bit.

Anyone know where I can find a detune plugin?

---

### Post by zero2xiii on 2011-12-21
Hay,

Maybe you can try:
Jackrack > Frequency > Pitch Shifter > Pitch Scaler

This might help. Not exactly a "detune" as I think it also changes the speed.. Not sure... I cant test it with a guitar only sound (Dont have one at hand.) Also play with the wet/dry value. That might help a bit with the timing issue, seeing as you can keep somewhat of the original sound in your mix.

Cherz

---

### Post by Sylos on 2011-12-22
Not directly an answer to your question but if your looking to fatten the guitar out a little I always just duplicate the track in ardour and then offset the time of it a little. You can then pan them however you prefer for your track. It gives instant power and fattness without any real hassle.

Might be worth a shot if you cant find a detune.

Cheers

---

### Post by transmogrifox on 2011-12-22
Actually the [Shifter]("http://rakarrack.sourceforge.net/effects.html#Shifter") effect in Rakarrack is able to do this.  Set it to "Whammy" mode, then set the whammy slider to whatever amount you want to detune.  It will detune smoothly from 0 up to a full octave, but you can set the interval to say, 1, so that you have a finer control over the amount of detune.  This is how you would want to adjust it to get a slight amount of detune.

I agree Harmonizer only does full intervals, but Shifter does everything in between.   You can also do some crazy stuff with the Sequence effect set in a shifter mode.  

In the git repository there is also an effect called [Infinity]("http://rakarrack.sourceforge.net/effects.html#Infinity"), which is also able to detune by turning the rate up, but it creates beat frequencies if you try to mix dry signal with it, so it's better for creating dizzy doppler and rotational effects.  The reason I mention it is because it can be used with milder adjustments to enhance the spatialization of the sound and help "Fatten" things up.

Another effect that may interest you is [Shuffle]("http://rakarrack.sourceforge.net/effects.html#Shuffle").  This allows you to selectively shuffle different frequency bands to left and right.  This in combination with some delay and detune (shifter) can be used to help separate the sound into something that sounds like two instruments.

---

### Post by decomp on 2011-12-22
Hey Guys!

I tried a bunch of pitch shifters and they all gave a pretty tinny weird sound as the end result. So I tried using ardours built in pitch shifter and that worked much better. It's definitely more work as it's not in real time so I have to duplicate every guitar track and then apply the shifter. It also ended up with a weird phasing effect so I offset the time slightly as well and that took care of it. 

Thanks everyone for your suggestions!

---

