---
title: "Selecting channels from dual M-Audio cards"
date: 2009-11-14
forum: Ubuntu Studio
---

### Post by soltanis on 2009-11-14
I do volunteer work for a student radio station. We have a middle-aged box just sitting around that I popped two M-Audio cards (the Envy24 variety) into. These cards use break-out boxes that have 4 channels of what I assume can be 1/4" unbalanced stereo or balanced mono inputs and outputs; since I have two cards, we have 8 total inputs and 8 total outputs between the two cards.

I have also installed a Linux flavor (not Ubuntu, but I should be able to translate if anyone can help me). Ideally, what this server will do is automatically record the audio coming in over the channels, and play them out on the output channels simultaneously. In the ways that I've seen these boxes configured, they should be able to accept at least 4 balanced stereo inputs.

Linux sets up and correctly detects the cards and alsa configures itself correctly, but I'd like to be able to separate the incoming audio by channel instead of by card. In other words, I'd like to be able to arecord just channel #3 and #4 instead of having to record all 4 input channels on the card simultaneously.

Is there any way to do this? Does this job require pulseaudio (which I dislike strongly)? Anyone have anything to offer?

Thanks.

---

### Post by RaumTrug on 2009-11-15
as pulse is rather thought for handling "multimedia" sound stuff, like having multiple apps mixed together to one pcm output, for serious recording you'd rather want to use jack in order to record multichannel stuff, it will allow you to address each channel independently, all you need is recording progs that are jack compatible (mustn't be ardour, there's a tiny tool calle mhwaveedit that does bare minimum + can be driven in multiple instances for recording channels independently).

as for using 2 soundcards (need to be "word clocked" together, i.e. connect one s/pdif output from the "master" to an s/pdif input of the "slave" and set the option to slave sample rate to digital input for the "slave" with the envy24control tool), you'll need to define an alsa config file merging the two cards virtually to one device, then that device can be used from jack like a single soundcard. i have never done such, but it is said to work; the info here can be useful: [http://alsa.opensrc.org/index.php/TwoCardsAsOne](http://alsa.opensrc.org/index.php/TwoCardsAsOne)

good luck!

---

### Post by soltanis on 2009-11-16
So to clarify I'm doing this on CentOS 5.3. I downloaded and compiled ecasound and jack, and set the appropriate limits in /etc/security/limits.conf for the daemon. However, since I'm using two M-Audio 44 cards for this job, I am not sure how I should combine them into a single card since the given tutorial assumes a certain configuration that I don't have.

Also, I cannot synchronize the word clocks on the cards, but I do believe that this shouldn't be necessary because I am not going to try recording stereo samples from two different cards at once -- just two channels from the same card.

---

