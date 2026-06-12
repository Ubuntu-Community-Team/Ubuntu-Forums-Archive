---
title: "Redshift - anyone try it?"
date: 2010-05-20
forum: The Cafe
---

### Post by standingwave on 2010-05-20
Looks interesting. Might give it a go when I get the time to set it up.

> If you’re anything like me you probably spend far too much time in  front of your computer screen(s). We’re all acutely aware that this  isn’t entirely fantastic news for our eyes [or our sleep patterns]("http://edition.cnn.com/2010/TECH/05/13/sleep.gadgets.ipad/index.html?hpt=C1") but we stare away  nonetheless.

If so then make sure you check out ‘[Redshift]("http://jonls.dk/redshift/")’ – it  automatically adjusts your screen colour temperature to that of your  surroundings which can help alleviate strain on your eyes.

[http://www.omgubuntu.co.uk/2010/05/tired-eyes-computer-screen-ubuntu.html](http://www.omgubuntu.co.uk/2010/05/tired-eyes-computer-screen-ubuntu.html)

---

### Post by ukripper on 2010-05-20
Great just found ppa repo. Will try later thanks

---

### Post by soapytheclown on 2010-05-20
tried it and hated it, both me and my brother found it hurt our eyes more than anything

---

### Post by Augustine325 on 2010-05-20
I've added it today and love it.  Particularly if you follow the instructions on the OMG Ubuntu blog, you can add a toggle button.  :)

---

### Post by murderslastcrow on 2010-05-20
Huh- very interesting. I'll try it, see if it works well in a variety of situations.

---

### Post by Random_Dude on 2010-05-20
I've just tried it and don't know if it's really worth it. :\

I'll give it a chance for a few days.

---

### Post by tjeremiah on 2010-05-20
using it now and it seems to be working.

---

### Post by undecim on 2010-05-20
Wow, definitely notice the change when I ran it. I'll have to see how it works out over the course of a few days.

---

### Post by cespinal on 2010-05-21
running it right now... toggling it on and off definatly makes a change tho...

---

### Post by gnomeuser on 2010-05-21
I'm a bit concerned that the lead developer doesn't cite any research to indicate that this actually has an impact, let alone how significant. 

Largely I get that old pseudo science vibe from this.

I imagine that if this worked it would have to rely on there being a sensor on the monitor to give it data on the exact local condition rather than relying on external data. 

It also seems to me that many monitors are entirely uncalibrated as it is, one might wonder if the first step might not be to go the gnome color manager route first to ensure a baseline.

---

### Post by mikewhatever on 2010-05-21
Does it really change the color of the screen?

---

### Post by Random_Dude on 2010-05-21
Well, that didn't last 24 hours. Way too much red.

I agree with gnomeuser, there are a lot of variables to consider. It might have the opposite effect.

Cheers :cool:

---

### Post by Linye on 2010-05-21
> **gnomeuser said:**
> I'm a bit concerned that the lead developer doesn't cite any research to indicate that this actually has an impact, let alone how significant. 

Largely I get that old pseudo science vibe from this.



This article may explain the reason behind it.

[http://edition.cnn.com/2010/TECH/05/13/sleep.gadgets.ipad/index.html?hpt=C1]("http://edition.cnn.com/2010/TECH/05/13/sleep.gadgets.ipad/index.html?hpt=C1")

---

### Post by TheNerdAL on 2010-05-21
My computer screen sure looks old now. lol

---

### Post by TheNerdAL on 2010-05-21
Okay, I don't like it, how do I remove it?

Does this command work to remove it?
```
sudo aptitude remove redshift
```

---

### Post by undecim on 2010-05-21
wow, woke up this morning and my screen was REALLY red.

I think I'm going to leave it toggled off until about 7 pm

---

### Post by Rasa1111 on 2010-05-21
> **TheNerdAL said:**
> Okay, I don't like it, how do I remove it?

Does this command work to remove it?
```
sudo aptitude remove redshift
```


sudo apt-get autoremove redshift

should do it.

---

### Post by TheNerdAL on 2010-05-21
> **Rasa1111 said:**
> sudo apt-get autoremove redshift

should do it.

Too late, I already did that code. :O Is that bad? :(

---

### Post by Rasa1111 on 2010-05-21
> **TheNerdAL said:**
> Too late, I already did that code. :O Is that bad? :(


 no, not bad. 

Did it to what you wanted it to?

 You can still run ```
sudo apt-get autoremove redshift
```
if there is anything left over from it, that should clean it out. 
and it wont hurt anything. 

 but if you got your desired results..
no worries, right? :)

---

### Post by TheNerdAL on 2010-05-21
> **Rasa1111 said:**
> no, not bad. 

Did it to what you wanted it to?

 You can still run ```
sudo apt-get autoremove redshift
```
if there is anything left over from it, that should clean it out. 
and it wont hurt anything. 

 but if you got your desired results..
no worries, right? :)

Thanks. I worry a lot when I think I do things bad, lol.

---

### Post by Rasa1111 on 2010-05-21
> **TheNerdAL said:**
> Thanks. I worry a lot when I think I do things bad, lol.


 No worries bro, 
that is societies fault. lol ;)

---

### Post by muazfa on 2010-05-21
My desktop became a little red when i run redshift. Just waiting for will change or not

---

### Post by gnomeuser on 2010-05-21
> **Linye said:**
> This article may explain the reason behind it.

[http://edition.cnn.com/2010/TECH/05/13/sleep.gadgets.ipad/index.html?hpt=C1]("http://edition.cnn.com/2010/TECH/05/13/sleep.gadgets.ipad/index.html?hpt=C1")

But the two aren't comparable, Redshift as I understand it attempts to continually slightly alter the warmth of colors. The article describes removing artificial light sources at night only to improve sleep. Apples meet Oranges.

The latter btw. is executed in a manner that can only be described as highly unscientific and entirely without protocol or premise. The former so far appears to be based entirely on hunches and guesswork.

Problems with Redshift in no specific order:
It has not been established that a statistically significant effect is present. Negative influence has not been assessed (e.g. doing A might improve B but significantly harm C given D). It appears that it provides a static calculation of the position of the Sun but does not take into account the surroundings, the weather, the lighting conditions, the vision of the user and so on. 

Given the evidence presented the only conclusion the intellectually honest critical thinking skeptic can draw is that Redshift has little if any basis in science. Furthermore, if an effect can be shown to exist and the hypothesis that altering the warmth of the colors results in a statistically significant improvement reproducing this outside of controlled laboratory conditions will be practically impossible.

Never the less it is an interesting idea, I would love to see more justification for it and boat loads of data showing that the approach is viable in the real world. 

One thing is clear though, computers are here to stay and as are other light sources. We would benefit from examining how it impacts the body, if improvements are needed and if so what our options are.

---

### Post by undecim on 2010-05-21
Mine seems to be more red in the morning/afternoon than the evening. (and yes, I've checked my latitude and longitude )

---

### Post by Rasa1111 on 2010-05-21
This might actually be useful to astronomers. lol
:)

---

### Post by DouglasAWh on 2010-05-26
> **gnomeuser said:**
> 
I imagine that if this worked it would have to rely on there being a sensor on the monitor to give it data on the exact local condition rather than relying on external data. 

Really?  Latitude and Longitude is exact enough for you?  The earth's rotation is pretty well established with sunsets and sunrises easy to predict.

The idea is to look like the *sun* not like the inside of your office/coffee shop/whatever.  It's also not supposed to mimic the actual sunlight.  For instance, clouds are not taken into account and shouldn't be, IMO.

Now, whether a monitor looking more like the sun can help your sleep patterns may need some backing up, but I didn't get the feeling from what you wrote that that's what you were questioning.

If you don't like it, fine, but I just don't understand your reasoning.  Please feel free to elaborate.

EDIT: actually, I see now why there could be some confusion: "Redshift adjusts the color temperature of your screen according to your surroundings."  "Surroundings" is pretty vague.

---

### Post by ethanay on 2010-05-26
> **gnomeuser said:**
> I'm a bit concerned that the lead developer doesn't cite any research to indicate that this actually has an impact, let alone how significant. 

Largely I get that old pseudo science vibe from this.

I imagine that if this worked it would have to rely on there being a sensor on the monitor to give it data on the exact local condition rather than relying on external data. 

It also seems to me that many monitors are entirely uncalibrated as it is, one might wonder if the first step might not be to go the gnome color manager route first to ensure a baseline.

1. it's pretty well established that white light affects circadian rhythm through inhibiting melatonin production or uptake or something.  the more red light vs white light @ night, the better our natural sleep cycles will function.  sleep experts have been recommending no computer/TV in addition to no caffeine at night time before bed.

2. it's also pretty well established that staring at white light projected AT us in a dark environment sucks for our eyes -- both in terms of eye strain (long-term vision loss) and night vision (short term).  more red @ night is easier on the eyes, /ceteris paribus/.  of course, we also have to factor in things like contrast, and functionality (e.g, the importance of color accuracy to what we're doing).  but it's not rocket science.  it's worked for astronomers for years.

the research/practical experience is out there...spend a few minutes in google scholar and i'm sure you'll find some interesting stuff.  you seem to have the analytical mind for it. :guitar:

imo, this is a great first effort at vastly increasing the usability/health impact of computer use.  f.lux is a more finished product, but i'm sure RedShift will get there.

---

### Post by Firestem4 on 2010-05-26
Red light causes less stress on our eyes because it has a much lower frequency compared to every other visible color in the light spectrum.

An exerpt from Wikipedia:

Rhodopsin in the human rods is less sensitive to the longer red wavelengths of light, so many people use red light to help preserve night vision as it only slowly depletes the eye's rhodopsin stores in the rods and instead is viewed by the cones
source:[http://en.wikipedia.org/wiki/Night_vision](http://en.wikipedia.org/wiki/Night_vision)

Since the visible red spectrum is the lowest visible spectrum of color that we can see, anything below that is too slow to discern (Infared). Compare that to blue and Violet which have the shortest wavelenghts and the highest frequency. These colors tend to cause more stress to our eyes (especially at night when our Rods are taking over).

Also, from a very interesting website talking about Rods and Cones:
"The light response of the rods peaks sharply in the blue; they respond very little to red light. This leads to some interesting phenomena:
Red rose at twilight: In bright light, the color-sensitive cones are predominant and we see a brilliant red rose with somewhat more subdued green leaves. But at twilight, the less-sensitive cones begin to shut down for the night, and most of the vision comes from the rods. The rods pick up the green from the leaves much more strongly than the red from the petals, so the green leaves become brighter than the red petals!
The ship captain has red instrument lights. Since the rods do not respond to red, the captain can gain full dark-adapted vision with the rods with which to watch for icebergs and other obstacles outside. It would be undesirable to examine anything with white light even for a moment, because the attainment of optimum night-vision may take up to a half-hour. Red lights do not spoil it"

[http://hyperphysics.phy-astr.gsu.edu/hbase/vision/rodcone.html](http://hyperphysics.phy-astr.gsu.edu/hbase/vision/rodcone.html)

---

