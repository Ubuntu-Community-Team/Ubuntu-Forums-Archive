---
title: "Totem Gstreamer and Pulseaudio dont work with jack running"
date: 2012-06-28
forum: Ubuntu Studio
---

### Post by jesushero on 2012-06-28
I've just installed a fresh 12.04, on a pretty decent system with an M-Audio 1010LT. Surprisingly few problems (compared to the last couple of releases), and pretty much everything worked out of the box. But, the one I haven't solved yet is how to get Totem (and gstreamer/pulseaudio apps in general) to work once jack has been started.

Audacious and Xine both have the option to run with jack. In totem I haven't found that yet. Ideally, I would like jack to start automatically on booting up, and everything else to run on jack.

I must admit I have little to no experience of XFCE, I've been using Gnome for many years now.

By the way, it seems like Pulseaudio sources/sinks are appearing in Jack by default, but they're just not working.

---

### Post by sgx on 2012-07-01
I think ubuntu is designed for pulse to control 'home entertainment',
and jack to separately control quality recording, and the playing
of software instruments.

Aqualung is a totem-like media player, designed to utilize jackd,
with automatic connections. vlc also works well. I don't think it is
lucky, to have jackd autostart on a system. It would be default
behavior, were it a good advantage. You can keep a jackd command
in your .bash_history, and tap the up-arrow in a terminal a few times
to retrieve it. Qjackctl should not be needed with aqualung, and can
be a bugs teammate. 

Cheers

---

