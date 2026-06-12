---
title: "How do I record sound from my speakers in Audacity?"
date: 2009-07-25
forum: Ubuntu Studio
---

### Post by Rytron on 2009-07-25
Hi.
How do I record sound from my speakers in Audacity? I can record from a microphone but this is a long way when I merely want to record directly from my speakers.
Attached is a picture of the volume control and the various input sources. What is the exact meaning of:
Mic?
Front Mic?
Line?
Cd?
Thanks.

---

### Post by kayosiii on 2009-07-25
I am pretty sure that this exact question has been asked before on these forums. Please search before posting...

There are a few possibilities 
1) if the sound you are recording can be played from a jackified app. learn to use jack. Jack lets you connect inputs and outputs between programs.
2) Get a cable that goes from your line out to your line in and record from your line in.
3) There may be some way of setting up alsa to do what you want.

---

### Post by Grishka on 2009-07-25
use JACK. there's no better option.

---

### Post by Rytron on 2009-07-26
> **Grishka said:**
> use JACK. there's no better option.

Okay. I find JACK tricky to use. In time I'm sure I will get the hang of it. Thanks.

---

### Post by Grishka on 2009-07-26
> **Rytron said:**
> Okay. I find JACK tricky to use. In time I'm sure I will get the hang of it. Thanks.

are you using [qjackctrl](apt://qjackctrl)? the version in the repos is cumbersome, compile from cvs or use the version from [frasten's ppa](https://launchpad.net/~frasten/+archive/ppa). it'll make some difference. also, try [patchage](apt://patchage). it'll let you connect applications comfortably.

---

### Post by archanadevi on 2009-07-26
You are correct [kayosiii]("http://ubuntuforums.org/member.php?u=74537") .

---

### Post by Rytron on 2009-07-26
> **Grishka said:**
> are you using [qjackctrl](apt://qjackctrl)? the version in the repos is cumbersome, compile from cvs or use the version from [frasten's ppa](https://launchpad.net/~frasten/+archive/ppa). it'll make some difference. also, try [patchage](apt://patchage). it'll let you connect applications comfortably.

Thank you Grishka. I will heed to your advice.

---

