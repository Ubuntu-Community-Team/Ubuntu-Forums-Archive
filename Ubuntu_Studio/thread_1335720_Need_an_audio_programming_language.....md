---
title: "Need an audio programming language...."
date: 2009-11-23
forum: Ubuntu Studio
---

### Post by nick937 on 2009-11-23
What I am wanting to do is be able to enter an audio clip;
& based on the pauses in the audio, extract the words.

anyone have ideas for what would be best to do this with?

windows or linux

---

### Post by raboofje on 2009-11-24
Praat is a well-known open source speech analysis program, though I'm not sure if it's so advanced it'll recognize words...

---

### Post by nick937 on 2009-11-24
> **raboofje said:**
> Praat is a well-known open source speech analysis program, though I'm not sure if it's so advanced it'll recognize words...

it does not need to recognize words.. I am going to try and filter out all the background noise, except the speech.


So..
All it needs to recognize is the lack of noise (speech)

example:

(pause) "hello" (pause) "my" (pause) "name" (pause)

may have to slow down the audio in order to catch the pauses..


ill look into praat this after noonn

---

### Post by barisurum on 2009-11-24
> I am going to try and filter out all the background noise, except the speech.

You can eliminate the background noises of frequencies other than the speech with an equalizer. The best app to do this job is JAMin. You have to have a jack enabled setup for this to work though.

First you play the clip with a jack friendly player (audacious comes to my mind). Dont forget to set the player to jack output. Connect the player to JAMin using qjackctl. And finally connect JAMin to a recorder of your choice (ardour or rezound comes to mind). While playing you can experience with equalizer settings (there are many in JAMin) and find the speech's original spectrum. Then you can pull the other frequency sliders all the way down to eliminate the noise. And finally record the clean signal to a wav file. 

Hope this helps you. Cheers!

---

### Post by raboofje on 2009-11-26
> **nick937 said:**
> All it needs to recognize is the lack of noise (speech)

(pause) "hello" (pause) "my" (pause) "name" (pause)

Aaaah! If I recall correctly Audacity has pretty nice noise removal if you need it.

There are a couple of 'audio splitters', mostly geared towards splitting tracks of longer recordings, but they might work on a smaller scale too.

For example [http://wavbreaker.sourceforge.net/index.html](http://wavbreaker.sourceforge.net/index.html)

---

