---
title: "on resume from suspend, sometimes it incorrectly thinks my headphones are plugged in"
date: 2013-12-24
forum: System76 Support
---

### Post by superjoe30 on 2013-12-24
Model Name: Bonobo Extreme
Model Number: bonx7
Ubuntu Version: 13.10
Driver Version: 13.10.5

Steps to duplicate the problem:

1. Plug in headphones.
2. Take out the headphones.
3. Suspend the laptop.
4. Resume the laptop.
5. About 50% of the time the laptop will think you still have headphones plugged in when actually you do not. So if you try to play audio, no sound comes out. You can fix it by plugging in headphones and taking them out, or rebooting.

---

### Post by ddraper2 on 2013-12-25
Install the Pulseaudio volume control and you should be able to reset the output device from headphones to speakers.

[https://apps.ubuntu.com/cat/applications/precise/pavucontrol/](https://apps.ubuntu.com/cat/applications/precise/pavucontrol/)

---

