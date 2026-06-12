---
title: "HDMI is not displayed in the “Sound” settings"
date: 2017-12-06
forum: Virtualisation
---

### Post by satimis on 2017-12-06
Hi all,

Ubuntu 16.04 desktop

HDMI is not displayed in the “Sound” settings.  Please advise how to get it back

Regards
satimis

---

### Post by frappe792 on 2017-12-06
There has been mixed success on this page [https://itsfoss.com/how-to-fix-no-sound-through-hdmi-in-external-monitor-in-ubuntu/](https://itsfoss.com/how-to-fix-no-sound-through-hdmi-in-external-monitor-in-ubuntu/)

maybe it will help

---

### Post by satimis on 2017-12-06
> **frappe792 said:**
> There has been mixed success on this page [https://itsfoss.com/how-to-fix-no-sound-through-hdmi-in-external-monitor-in-ubuntu/](https://itsfoss.com/how-to-fix-no-sound-through-hdmi-in-external-monitor-in-ubuntu/)

maybe it will help
Hi,

Thanks for your link.

Through difficulty I got sound back on the newly installed VM by running following command on Terminal;```

$ pulseaudio -k && sudo alsa force-reload

```
login

Then sound comes back.

On the new VM
-> System Settings -> Sounds
Play sound through```

Analog Output/No Amplifier
Build-in Audio

Analog Output/Amplifier
Built-in Audio

```

Selecting either of them can get sound on the built-in speaker of the display.  But I couldn't get sound on the external speakers


On Host
-> Settings -> Sounds
Play sound through```

HDMI/DisplayPort
Caicos HDMI Audio [Radeon HD 6400 Series]

Digital Output (S/PDIF)
Built-in Audio

Line Out
Built-in Audio

```

Seleting```

HDMI/DisplayPort
Caicos HDMI Audio [Radeon HD 6400 Series]

```
I get sound on the built-in speaker of the display.

Seleting either of the other two settings I got sound on the external speakers.

I found all running Ubuntu VMs
on Play sound through```

HDMI/DisplayPort
Caicos HDMI Audio [Radeon HD 6400 Series]

```
is missing.  I suppose I need to install driver to get it back?

Regards
satimis

---

### Post by Yellow Pasque on 2017-12-06
If you're in a VM, you're not going to see the host's audio devices. qemu or Virtualbox or whatever will emulate a sound device. I'm confused by your post.

---

### Post by howefield on 2017-12-06
Thread moved to the "*Virtualisation*" forum.

---

### Post by SeijiSensei on 2017-12-06
> **Temüjin said:**
> If you're in a VM, you're not going to see the host's audio devices. qemu or Virtualbox or whatever will emulate a sound device. I'm confused by your post.

Me, too.  My host computer has HDMI as its default output.  When I run a VM I hear the sound via HDMI.  

Just as a test to make sure I wasn't deluding myself, I ran a Mint 17.1 VM in VirtualBox on top of my Kubuntu 14.04 system.  I played a video in the guest that used Flash and heard the sound via HDMI.

---

