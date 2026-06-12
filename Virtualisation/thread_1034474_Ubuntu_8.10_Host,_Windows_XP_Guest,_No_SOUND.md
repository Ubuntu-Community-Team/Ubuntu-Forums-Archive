---
title: "Ubuntu 8.10 Host, Windows XP Guest, No SOUND"
date: 2009-01-08
forum: Virtualisation
---

### Post by nightfire117 on 2009-01-08
Just finished installing. I got this 'cause I *need* some native XP apps, and since VirtualBox completed everything without a hitch (this is my first time using it) I'm very pleased and it's definitely helped me on my way to using exclusively Linux (or particularly, Ubuntu).

HOWEVER. There is an issue. I can't get any sound. I've got a rather complicated setup and even Ubuntu has issues with the sound. My sound card is a SoundBlaster Live! 24-Bit USB, and as we all know is a horrible card for Linux but awesome for Windows. I have speakers plugged in the back and headphones in the front, and I have to unmute it when I switch to/fro in Gnome.

So I start up the VM and Windows installs the "new hardware." I used AC97 and "PULSE" and then "ALSA" but neither worked. 

Also, my USB isn't working in the VM, could that be part of the issue? I'm sure there'd be some conflicts, though, if the sound card was detected in XP and I installed the drivers for that.... When I go into the VM settings, it says:

```

Failed to access the USB subsystem.

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {f39438d7-abfd-409b-bc80-5f5291d92897}
Callee: 
IMachine {ea6fb7ea-1993-4642-b113-f29eb39e0df0}
```

Any help would be fantastic, thanks. =]

~Night

---

### Post by nightfire117 on 2009-01-08
Well, kind of fixed. After a couple more restarts the VM sound worked just fine. Then I exited. Now VLC won't play DVDs, even though DVD support on my comp sucked and needed a lot of help to begin with in 8.10 (the new VLC I guess?). So I'm gonna update my system, reboot and hope that fixes it... if not I'm going to install an old VLC. I loved the old ones, but this new one... I don't like it at all, anyway.

USB issue still stands. >.<

~Night

---

