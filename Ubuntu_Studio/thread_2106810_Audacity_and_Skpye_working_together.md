---
title: "Audacity and Skpye working together"
date: 2013-01-20
forum: Ubuntu Studio
---

### Post by JerryReed on 2013-01-20
I love using Skype, especially for working with training coaches. I also use Audacity for recording audio. I am using Ubuntu Studio which actually runs in xfce instead of Gnome.  I have a Behringer X1222 USB Audio Mixer for inputs. Here's the issue:   Skype runs great when it runs by itself. I get all the sound settings correct and get both receive and send audio. When I launch Audacity, it captures the input codec from the mixer and takes it away from Skype leaving Skype without the ability to get input from the CODEC. Is there any way for both Skype and Audacity to share the same input CODEC? What I need to do is record audio from the mixer and at the same time allow this audio to be the audio input for Skype.

---

### Post by ttoine on 2013-01-21
You should use Pulse Audio in Skype and in Audacity. It is not possible to use Alsa for more than one application at a time.

Then, in the sound preferences, just select the Behringer sound card as Input and Output. Can you confirm that it is available in the sound preferences of Ubuntu Studio ?

---

