---
title: "JACK software is blocking my webcam"
date: 2015-03-29
forum: Ubuntu Studio
---

### Post by matthew45 on 2015-03-29
Hello.

I've got a problem. Few months ago I was fighting with JACK to make it working on my Ubuntu computer. Finally, everything is working, I can record audio with Ardour, I can use JACK input and output, everything is fine, but.. When the JACK server is started, my video camera is not working. I've got Creative Live! Cam Socialize. When Jack server is stopped, my camera is working(in Skype and Cheese software). But when it's started, Skype have no signal from cam(LED is not lighting) and Cheese is showing 'There was an error playing video from the webcam'. How can I fix it?

---

### Post by jejeman on 2015-04-04
Obviosly your cam is a soundcard as well. Is it?
Choose that sound card to use with JACK, see how it goes.

---

### Post by matthew45 on 2015-12-06
Hi!

I'm here after few months. Still I've got this problem with my webcam and JACK software. When JACK server is started, it is blocking my webcam from working. If I choose my webcam to be used by JACK as default soundcard, it doesn't change anything. 
Somebody has a similar problem here: [http://askubuntu.com/ques...]("http://askubuntu.com/questions/645336/use-webcam-with-pulseaudio-while-jack-is-running")

Is there any way to let my webcam be free from JACK software? I have no need to use my webcam as a soundcard/microphone, because I've got external in/out sound card what is working very good with JACK software. The only thing I need is release my webcam from JACK and running video on Skype with this webcam.

---

### Post by marseille2 on 2015-12-20
I'm having similar issues with Skype 4.3. Since it's not designed to use anything but pulseaudio, I'm looking at apulse (emulates PA) so I can still run Jackd. I haven't tested it yet, but you might want to check it out.

Github [https://github.com/i-rinat/apulse](https://github.com/i-rinat/apulse)

Ubuntu PPA for utopic and trusty [https://launchpad.net/~kirillshkrogalev/+archive/ubuntu/apulse](https://launchpad.net/~kirillshkrogalev/+archive/ubuntu/apulse)

---

