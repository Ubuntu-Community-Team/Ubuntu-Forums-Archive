---
title: "Need help setting up jacks for ubuntu operating system"
date: 2013-07-19
forum: Ubuntu Studio
---

### Post by chicken0408 on 2013-07-19
I recently installed ubuntu as dual-boot mode on my Windows 7 laptop, HP Pavilion dv6-6c35dx, and I can't get the headphone/microphone jack to work. The laptop actually has 3 jacks: from left to right, 1 mic jack and 2 headphone jacks. I tried to follow some instructions using Qjackctl and Realtime support methods, but they are too general and I am no ubuntu expert. I kept having errors since I can't put in the right configurations. I appreciate any advices and instructions on this matter, as detailed and specific as possible. Thank you in advance.

---

### Post by jejeman on 2013-07-19
> **chicken0408 said:**
> II can't get the headphone/microphone jack to work.To work how/what? What do you want to do? No sound output on headphones jack?

---

### Post by chicken0408 on 2013-07-20
Yeah, there's no output through the headphone, and I want to make the headphones jacks work to be able to listen to music. Btw, the microphone jack works fine now after rebooting a couple of times so we don't have to worry about that anymore.

---

### Post by jejeman on 2013-07-20
Give
```
aplay -l
```
```
cat  /proc/asound/card*/codec#* | grep Codec
```
Now, you said that you have two headphone (output) jacks, right? Or is it one headphone, other line out? Does both don't work? What about built in speakers, if there are any?
Does it not work only with JACK (i saw you mention Qjackctl) or in general?

---

