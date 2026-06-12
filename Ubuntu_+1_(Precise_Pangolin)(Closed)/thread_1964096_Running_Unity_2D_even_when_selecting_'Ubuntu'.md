---
title: "Running Unity 2D even when selecting 'Ubuntu'"
date: 2012-04-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by iniquiTrance on 2012-04-23
This problem started when I noticed my Compiz settings weren't working in Precise Pangolin 12.04 LTS. Even though 'wobbly windows' and 'desktop cube' were checked off in Compiz, they still weren't working.

So I ran:

```
echo $DESKTOP_SESSION
```

which returned:

> ubuntu-2d.

I select 'ubuntu' when logging in, yet still appear to be running Unity 2D. How can I get to Unity 3D?

Thanks!

---

### Post by Dragonbite on 2012-04-23
Your video card may not be able to handle Unity 3D.  My other laptop cannot, but my current one can.

you could run "lspci" to get some information on your video and see if there are any updated or proprietary drivers you can install.

Also, I don't know if it works, but look for the program (cannot remember the name right now) that will scan your system and look for components that there are proprietary (which cannot be distributed with the CD) drivers.

---

### Post by iniquiTrance on 2012-04-23
Thanks for the reply. Everything was working natively in 11.10 though. I just installed bumblebee (I have nVidia optimus), and everything seems to be working now. Is this a good solution? I didn't need to install bumblebee in Oneiric...

---

### Post by iniquiTrance on 2012-04-23
Hmm, i seem to be getting /usr/bin/Xorg errors now periodically...

---

### Post by Dragonbite on 2012-04-23
Honestly I don't know anything about Bumblebee, just that nVidia can be a PITA at times.

---

### Post by grahammechanical on 2012-04-23
How up to date is your system? Were you using a Nvidia driver and did it get deactivated so that an open source driver took over that would only give you Unity 2D?

Regards.

---

### Post by Yellow Pasque on 2012-04-24
> Were you using a Nvidia driver and did it get deactivated so that an open source driver took over that would only give you Unity 2D?

You have it backwards. It's the proprietary nvidia driver that screws up the open-source intel driver's 3D on optimus/hybrid systems. To use the nvidia card for rendering, one needs to remove the proprietary nvidia driver and use bumblebee/ironhide (and the optirun command).

---

### Post by grahammechanical on 2012-04-24
I was trying to determine why your system reverted to Unity 2D when it was already working in Unity 3D. Or perhaps you never did have Unity 3D working in the first place. It is not easy to tell from your first post.

Furthermore, I do not see anything in your first post about you having an optimus video system. In fact you fail to say anything about your hardware.

And in your second post you said this:

> I just installed bumblebee (I have nVidia optimus), and everything seems to be working now. Is this a good solution? I didn't need to install bumblebee in Oneiric...

So, what driver were you using in 11.10. And did you do a fresh install of 12.04? Or upgrade 11.10 and get stuck with that same driver?

---

