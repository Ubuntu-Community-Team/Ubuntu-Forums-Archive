---
title: "How to get sound working in Jaunty on Virtualbox?"
date: 2009-04-25
forum: Server Platforms
---

### Post by shaggy999 on 2009-04-25
I just installed jaunty into virtualbox and I wanted to set up ampache + mpd. Unfortunately, despite being able to get mpd to run and connect a client to it I cannot get any sound output.

Here's what I did:

Install Jaunty
Install linux-headers-server + build essential (for virtualbox additions compilation)
Install linux additions
Install alsa-base + alsa-utils + mpd + ncmpc
Then ran asoundconf list
Then ran asoundconf set-default-card <output from previous command>
Then started mpd manually. It stated it found an alsa device
Then started mpc and told it to play a file. It says it's playing a file and shows the little bar moving as it plays -- but no sound!! The music I'm playing is in flac format if that matters.

Note that mpd and ncmpc are both on the virtual machine... I'm not trying to stream to the host. And the virtual machine's soundcard is enabled. In fact I previously had intrepid server installed on here and was using moc to play music just fine.

Anybody have any ideas?

---

### Post by shaggy999 on 2009-04-25
And then.... somehow it magically works. I fiddled with installing pulseaudio and trying 'asoundconf set-pulseaudio' which would get programs like moc and mpd running, but would not play sound. Then I uninstalled pulseaudio ran 'asoundconf unset-pulseaudio' and then 'asoundconf reset-default-card'.

I can't remember if I did anything else, but I *finally* got it working (and without the need for pulseaudio, thankfully). I really don't know what I did though that made it work.

---

