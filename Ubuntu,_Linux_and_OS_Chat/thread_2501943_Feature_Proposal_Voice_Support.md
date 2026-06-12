---
title: "Feature Proposal: Voice Support"
date: 2024-10-27
forum: Ubuntu, Linux and OS Chat
---

### Post by tderflinger on 2024-10-27
Dear Ubuntu Fans,

With the advancement of voice technology, like TTS (text-to-speech) and STT (speech-to-text), I would like to propose a deeper integration of voice into the Ubuntu Desktop OS.
Things like a voice assistant (think Siri) could be an integral part of Ubuntu Desktop and maybe new voice APIs integrated in the OS.
There are also now available great open source TTS applications, like Piper ([https://github.com/networkedaudio/piperTTS](https://github.com/networkedaudio/piperTTS)) and others that could be leveraged.

Are there already projects running tackling this area?

What does the community and Canonical think about this? 

Feedback welcome!

Best,
-Thomas D.

---

### Post by grahammechanical on 2024-10-27
This is not a matter for Ubuntu developers but for the developers of the desktop environment and the user interface. Pleas see

[https://extensions.gnome.org/extension/6742/blurt/](https://extensions.gnome.org/extension/6742/blurt/)

[http://web.mit.edu/ghudson/dev/nokrb/third/gnome-speech/doc/gnome-speech.html](http://web.mit.edu/ghudson/dev/nokrb/third/gnome-speech/doc/gnome-speech.html)

Be happy testing the code.

Edit: And then there is this

[https://addons.mozilla.org/en-GB/firefox/addon/transkriptor-audio-to-text/](https://addons.mozilla.org/en-GB/firefox/addon/transkriptor-audio-to-text/)

Regards

---

### Post by werewulf75 on 2024-10-27
Complete voice support should be integral to the OS, not just TTS and STT, but actual operation of the OS and apps through interactive voice control so that particularly visually impaired and blind users could  use their computers easily. Users with various other disabilities would likewise benefit, e.g. those unable to use KB and mouse. If this has to be done at the WM/DE level, fine, so let it be at the default one. Relevant APIs should be provided for 3rd party developers so their apps could easily integrate into this. The technology is there.

---

### Post by tderflinger on 2024-10-29
Yes, I also think integration at the OS level would be preferable to just in the desktop GUI level. For example, I might want to generate a voice file out of a text in the console. One standard command would be great here. Also, 3rd party applications might want to tap into voice capability, so some form of API would be nice.

---

### Post by grahammechanical on 2024-10-29
> Yes, I also think integration at the OS level would be preferable to just in the desktop GUI level

How would you define "OS level."  In my mind that would be the Linux Kernel. An internet search reveals many offerings. They seem to be applications. Some are command line only but they are still applications running on a distribution running on Linux.

I have just done a search for devices that do text to speech recognition. In my opinion it would be cheaper to pay a friend to spend an hour or two reading to you than to buy one of these devices. A person could have a cup of tea or coffee and a chat at the same time.

There are solutions around for those who are hearing impaired and visually impaired. If these are the perceived needs.

Regards

---

### Post by Shibblet on 2024-10-29
One of the primary functions of language models (what they call AI), is the ability to (for lack of a better term) "comprehend" what you are saying before turning it into text, and/or computer commands.

Example:

Spoken:  "What's the name of that guy in the movie with that thing?"
Heard:  "What name fat guy in movie and thadding?"
AI Language Model:  "What  thename (What's the name) fat-guy (of that guy) inmovie (in the movie) andthadding? (with that thing?)

Reply:
Co-Pilot:  "Let me direct you to Bing."
Alexa:  "Here are movies featuring fat guys."
Google:  "Here is a list of movies featuring Andy Thadding"

The interpretation of what is said, to how the computer "comprehends" and translates to text is one of the hardest things to overcome.  It's almost impossible to do this anymore without a language model (AI).  It translates what it hears into what's "most likely" to have been said by processing things like language, grammar, and sentence structure.

This is why Microsoft has their "Co-Pilot," Google has "Google AI," Brave-Browser has "Leo," etc.  These are all web-interface designed to assist the user as quickly and efficiently as possible.

---

### Post by grahammechanical on 2024-10-29
If I remember correctly from years ago - speech to computer commands programs had to be trained to fit the users speech methods and accent. Even then results were far from accurate.

Regards

---

### Post by tderflinger on 2024-10-30
Yes, I think at the Kernel level would be too deep. The kernel already is very big. I think the best would be a daemon that exposes a speech API. The speech API would be TTS and STT. Alternatively, at least bundling a best-in-breed open source speech synthesizer and speech recognizer at the distribution level. For example Ubuntu desktop could bundle by default an open source TTS/STT application. Then, users would not need to install anything if they needed speech capabilities. 

GNOME Speech is great, but what about terminal users in Ubuntu server edition? Also, there is KDE and all the other window systems, will they define their own APIs?

---

