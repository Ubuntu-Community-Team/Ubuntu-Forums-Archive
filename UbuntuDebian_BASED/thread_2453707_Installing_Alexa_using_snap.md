---
title: "Installing Alexa using snap"
date: 2020-11-15
forum: Ubuntu/Debian BASED
---

### Post by Elven Decker on 2020-11-15
Hi,
Does anyone have any experience installing Alexa from snap on Ubuntu?  I'm using 20.10.

$ alexa.alexa-run
xcb_connection_has_error() returned true
Traceback (most recent call last):
  File "/snap/alexa/2/bin/alexa.py", line 20, in <module>
    main()
  File "/snap/alexa/2/bin/alexa.py", line 10, in main
    alexa_audio_device.init()
  File "/snap/alexa/2/bin/alexa_audio_device_pulse.py", line 29, in init
    + str(pa.strerror(error), 'ascii'))
Exception: Could not create pulse audio output stream: No such device or address

apulse, alsa-base, and alsa-utils are installed.  I'm using the pulseaudio snap.

Thanks!

---

### Post by Elven Decker on 2020-11-16
I found a better instruction set:  [URL="https://www.96boards.org/projects/AmazonAlexaVirtualDevice/"]https://www.96boards.org/projects/AmazonAlexaVirtualDevice/
[/URL]
No need to run alexa, it is set up as a server waiting for you to point to it with your browser.

That being said, loading "sudo snap install --devmode pulseaudio" as instructed breaks my audio, and once I remove the snap the "Settings/Sound" panel does not work properly.  Still looking for a full solution.

Full solution found, issue SOLVED.  See mycroft at: [https://mycroft.ai/get-started/#community-releases](https://mycroft.ai/get-started/#community-releases)

Works like a charm, easy to install, made for linux, open source, very clear documentation, active community, and opt-in privacy.

---

