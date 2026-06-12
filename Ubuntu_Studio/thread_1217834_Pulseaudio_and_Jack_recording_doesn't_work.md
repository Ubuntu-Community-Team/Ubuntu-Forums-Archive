---
title: "Pulseaudio and Jack recording doesn't work"
date: 2009-07-20
forum: Ubuntu Studio
---

### Post by Luke.Hoersten on 2009-07-20
I have the default pulseaudio and I'm trying to use Ardour to record some stuff. Pulseaudio volume control shows the mic is working but it seems nothing in Jack or Ardour can pick up the mic. When I start qjackctl from the command line, it says it's suspending pulseaudio which I'm assuming is because they conflict. How can I get my mic input from pulseaudio to Ardour?

---

### Post by raboofje on 2009-07-20
The most common approach is to shut down pulseaudio while doing audio work. This is exactly what the 'suspending pulseaudio' message means.

When you open the 'connect' window in qjackctl, at the 'Audio' tab, do you see 'system' as a "readable client / output port" and ardour as a "writable client / input port"? Can you connect the two? That should basically do it.

---

### Post by Luke.Hoersten on 2009-07-21
Pulseaudio does suspend but connecting the system inputs to the Ardour ins doesn't seem to work. Ardour seems to get no sound while I can still see the volume shoot up in the Pulseadio volume control for the input device so I know it's getting to the Pulseaudio just fine.

---

### Post by sgx on 2009-07-22
> **Luke.Hoersten said:**
> Pulseaudio does suspend but connecting the system inputs to the Ardour ins doesn't seem to work. Ardour seems to get no sound while I can still see the volume shoot up in the Pulseadio volume control for the input device so I know it's getting to the Pulseaudio just fine.

I think you must create a project in ardour, and make some hardware selection first, to make the jackd connection get past the Ardour front door and into the sound room.

Cheers

---

### Post by Luke.Hoersten on 2009-07-22
I've actually been recording with ardour for years and this problem started w/ Pulseaudio. I know how to connect everything from jackd all the way through ardour but I'm pretty convinced that the audio from the mic is being highjacked before it even gets to jackd.

---

### Post by trulan on 2009-07-23
I've never had a problem with it, but apparently some have.  Check out this page:
[http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/)

---

### Post by markbuntu on 2009-07-25
You can always get the pulseaudio module-pulse-jack that will connect pulseaudio and jack together. If you are using jaunty you need to get the pulseaudio source code and dpkg it and then install module-pulse-jack. It works, lots of people use it.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by martinbaselier on 2009-07-26
Jack is meant for low latency. Pulseaudio is not. It's not a good idea to combine them.

---

### Post by markbuntu on 2009-07-29
> **martinbaselier said:**
> Jack is meant for low latency. Pulseaudio is not. It's not a good idea to combine them.

That depends entirely on what you are trying to do. If you are trying to record some streaming audio into ardour it is perfectly usable for that and is the easiest way to do it. Latency is irrelevant when use of pulse-jack does not involve anything that needs close time synchronization.

---

### Post by martinbaselier on 2009-07-31
Since he wants to use a mic, I presume it's for recording music. In that case you would want the lowest possible latency.

---

### Post by Luke.Hoersten on 2009-08-02
I figured out the problem. I have two sound cards which Pulseaudio is combining so I can record from both. When Pulseaudio is paused, the better external soundcard doesn't work with Jack for some reason so I have to send it in the first one. I suspect disabling the integrated soundcard will fix the issues.

Thanks for your help guys.

---

### Post by markbuntu on 2009-08-03
If that card works with pulseaudio it should work with jack since pulse and jack use the same alsa driver (unless the second card is a firewire device). Have you tried changing the input and output hw in jack control. The hw designation can change when you reboot but you can fix that here

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

---

