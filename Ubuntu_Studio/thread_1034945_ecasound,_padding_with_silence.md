---
title: "ecasound, padding with silence?"
date: 2009-01-09
forum: Ubuntu Studio
---

### Post by rylleman on 2009-01-09
I'm experimenting with ecasound for using it in a bash-script I'm writing and there are a few things I haven't been able to figure out.

First I want to add silent padding to the start of the audio. In ecasound 2.5.0 and later you should be able to use "playat" but the version in Ubuntus repo's are 2.4.6.1 so playat wont work. I don't want the users of my script to have to do anything else than a apt-get to install ecasound. Is there any other way to pad the start of the file?

Second question is also about padding, but at the end. I want to add silence. Tried to use -t: with a time-value longer than the original audio and hoped that ecasound would fill with silence for the desired length which it didn't. So, how do I pad with silence at the end?

---

### Post by rylleman on 2009-01-10
Nevermind, I went with Sox instead and were able to do what I wanted with that.

---

