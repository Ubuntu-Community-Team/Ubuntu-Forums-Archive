---
title: "Open Source Automatic Writer"
date: 2011-09-05
forum: The Cafe
---

### Post by iampriteshdesai on 2011-09-05
Hey guys,
I've made this amazing software which automatically writes your assignments/letters which looks like its been hand written. You simply have to past the text in  box.
I wanted your opinion about it.
Here's a link:
[http://collegeczar.com/asswriter]("http://collegeczar.com/asswriter")

Here is a video of it in action:
[Youtube]("http://bit.ly/aawriter")

Its an Open source project like Ubuntu.
Thanks.

---

### Post by dniMretsaM on 2011-09-05
That actually looks hand written. Seems pretty cool.

---

### Post by Enigmapond on 2011-09-05
Pretty cool. The font's a little strange. Can that be changed? Good job though!

---

### Post by LowSky on 2011-09-05
What's a roll number?

Anywho doesn't look like my handwriting so FAIL!

:p

---

### Post by juancarlospaco on 2011-09-05
It writes on my WHAT?  &#10687;_&#10687;

---

### Post by Thewhistlingwind on 2011-09-05
OP was ts;dr (Too stupid, didn't read.)

Unless you can explain the heavy wizardry involved for this, I can only doubt you.

At any rate the intentions in making something to "Automatically generate schoolwork" can't be pure.

EDIT: Read the OP.

Not bad, now you need to figure out how to make individual handwriting a font.

---

### Post by sffvba[e0rt on 2011-09-05
@OP... Awesome job.  Nice application :)


404

---

### Post by cgroza on 2011-09-05
You can tell it has been automatically generated because every letter is identical.
In real handwriting, there are slight variations of i.e "a" and other letters.
You could have more candidate images for a letter, and randomly choosing one of them should make it more natural.

---

### Post by nmaster on 2011-09-05
> **cgroza said:**
> You can tell it has been automatically generated because every letter is identical.
In real handwriting, there are slight variations of i.e "a" and other letters.
You could have more candidate images for a letter, and randomly choosing one of them should make it more natural.

good idea.

you could create further variability by adding random noise after choosing a letter.  a Gaussian distribution approach would be most natural and it would ensure that most letters would look different while still have the "average letter" be the same (over the course of a long assignment).

---

### Post by FuturePilot on 2011-09-05
People still use handwritten letters?

---

### Post by iampriteshdesai on 2011-09-05
> **dniMretsaM said:**
> That actually looks hand written. Seems pretty cool.
thanks!

---

### Post by iampriteshdesai on 2011-09-05
> **Enigmapond said:**
> Pretty cool. The font's a little strange. Can that be changed? Good job though!
yeah, its an open soure project. I've added 4 default fonts you can add others. Its very simple to add extra fonts.

---

### Post by iampriteshdesai on 2011-09-05
> **LowSky said:**
> What's a roll number?

Anywho doesn't look like my handwriting so FAIL!

:p
A roll no is something we have over here in schools and colleges...
unique id 
you'd have to create a font of your handwriting to get an exact replica.

---

### Post by iampriteshdesai on 2011-09-05
> **not found said:**
> @OP... Awesome job.  Nice application :)


404
thanks

---

### Post by iampriteshdesai on 2011-09-05
> **cgroza said:**
> You can tell it has been automatically generated because every letter is identical.
In real handwriting, there are slight variations of i.e "a" and other letters.
You could have more candidate images for a letter, and randomly choosing one of them should make it more natural.
If you take a closer look, you'll see that I've added random rotations, size changes and different fonts. I am looking for more fonts which look like the one's i've used to make it look more random.

---

### Post by iampriteshdesai on 2011-09-05
> **nmaster said:**
> good idea.

you could create further variability by adding random noise after choosing a letter.  a Gaussian distribution approach would be most natural and it would ensure that most letters would look different while still have the "average letter" be the same (over the course of a long assignment).
how can gaussian distribution be applied to a font?

---

### Post by nmaster on 2011-09-07
> **iampriteshdesai said:**
> how can gaussian distribution be applied to a font?

the image of each letter is merely a 2D signal.  pass the signal through a filter with pseudo-randomly chosen coefficients (hence the gaussian distribution) in order to blur the letter in different ways. random filter weights would bend the letter in different ways each time.

after reading what i originally wrote, i could see how it was confusing. an additive noise model would not be appropriate. this would also distort the background of the image, which would be silly since the paper should just look like paper.

---

### Post by iampriteshdesai on 2011-09-07
> **nmaster said:**
> the image of each letter is merely a 2D signal.  pass the signal through a filter with pseudo-randomly chosen coefficients (hence the gaussian distribution) in order to blur the letter in different ways. random filter weights would bend the letter in different ways each time.

after reading what i originally wrote, i could see how it was confusing. an additive noise model would not be appropriate. this would also distort the background of the image, which would be silly since the paper should just look like paper.
Great idea.
So using your method even a single font can be varied to drastically change its appearance. 
Do you have any example of it?

---

### Post by BrokenKingpin on 2011-09-08
Who needs to hand write assignments these days? Even in high school I was required to type out my assignments and hand them in....

---

### Post by iampriteshdesai on 2011-09-08
> **BrokenKingpin said:**
> Who needs to hand write assignments these days? Even in high school I was required to type out my assignments and hand them in....
My college requires hand written assignments....

---

### Post by nmaster on 2011-09-10
> **iampriteshdesai said:**
> Great idea.
So using your method even a single font can be varied to drastically change its appearance. 
Do you have any example of it?

no sorry, i've never needed to implement something like this.  i honestly only just thought of this after taking a look at the OP's project.

you'd need to be somewhat clever about constructing the filter(s) though.  you want to make sure that the output still resembles the input.  my guess is that it isn't a trivial problem and would depend on the font and alphabet.

if it turns out that you can do this with a linear filter, then you just need to convolve the two images. as far as implementing 2d convolution... that's easy:
[http://www.mathworks.com/help/techdoc/ref/conv2.html](http://www.mathworks.com/help/techdoc/ref/conv2.html)
[http://docs.scipy.org/doc/scipy/reference/generated/scipy.signal.convolve2d.html](http://docs.scipy.org/doc/scipy/reference/generated/scipy.signal.convolve2d.html)

if you could use different filters (or sets of filters) to mimic different personality profiles that would be nifty.  try and fool a handwriting analyzer ;)

---

### Post by undecim on 2011-09-10
> **BrokenKingpin said:**
> Who needs to hand write assignments these days? Even in high school I was required to type out my assignments and hand them in....

I remember in 6th-8th grade, all our assignments were hand-written. I started missing those days when the online classes I was taking in high school were all required to be turned in as .doc files instead of e.g. a text box on the web page. Even short answer stuff, multiple choice quizzes...

---

