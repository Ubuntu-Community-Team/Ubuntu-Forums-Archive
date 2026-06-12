---
title: "Audio suddenly not working, seems to be a software issue"
date: 2024-02-17
forum: Ubuntu/Debian BASED
---

### Post by arius88 on 2024-02-17
Using Lubuntu 22.04 with the LXQt desktop environment.

The audio has been cutting out on my computer all day. It's across applications. Firefox, VLC media player, it all stops working. The "Volume Control" Mixer shows signal pumping, but nothing comes out my speakers. 

Oddly, it seemed to consistently fix it if I disconnected and reconnected the internet. (Sometimes muting and unmuting would work too.) But it would only work for about 30 seconds to a minute and then stop. And now those things don't work either. In a moment I'm going to reboot the computer and see if that helps, but even if it does, I need to know what is going on because this happened briefly the other day as well and I'm sure it will happen again. 

I'm wondering if the is related to another problem I've been having since installing Lubuntu: the internet stops working constantly and needs to be disconnected and reconnected in order to keep going. All of a sudden all the websites stop loading at once.

After doing some research about the sound issue, I ran dmesg today and the following error popped up all over the place: 

"warning: `iwconfig' uses wireless extensions which will stop working for Wi-Fi 7 hardware; use nl80211." I have no idea what that means or HOW to use nl80211.

It also yielded warnings to the effect that "txop exceeded phylen" (got that one a lot) and "array-index-out-of-bounds" was the first thing that came up. Something about virtualbox.

I would greatly appreciate any advice, as I really have no idea how to fix this, and I can't watch TV until I do.

---

### Post by arius88 on 2024-02-17
Update: I rebooted the machine. The audio came back. It worked for about a minute and 45 seconds and then it kicked out again. I disconnected and reconnected the wireless internet, voila, it works again - for about 30 seconds.

---

### Post by arius88 on 2024-02-17
Further update - it looks like if I just wait a while, without playing any sound, the sound will come back. (And then disappear again within about 30-120 seconds)

---

### Post by arius88 on 2024-02-18
I ran inxi. Not sure if any of this is useful.

~$ inxi -SMA
System:
  Host: axxus-0401u3u Kernel: 6.5.0-18-generic x86_64 bits: 64
    Desktop: LXQt 0.17.1 Distro: Ubuntu 22.04.4 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop System: LENOVO product: 0401U3U v: ThinkCentre A70z
    serial: <superuser required>
  Mobo: LENOVO model: N/A serial: <superuser required> BIOS: LENOVO
    v: 98KT26AUS date: 03/21/2011
Audio:
  Device-1: Intel NM10/ICH7 Family High Definition Audio
    driver: snd_hda_intel
  Sound Server-1: ALSA v: k6.5.0-18-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes

---

### Post by arius88 on 2024-02-18
Also also, I'm realizing that I normally use the headphone jack to power speakers, but I am cat-sitting and didn't bring any speakers or headphones and am relying on my computer's built-in speakers. So perhaps it IS a hardware issue...? It's just weird the way it craps out, I have to pause all audio playback, and then it comes back after a certain amount of time... but it won't come back if the audio is running.

---

### Post by ninoivanov on 2024-02-26
It's the death of the speaker-part of your soundcard (the headphone jack(s) expected to work many years longer). Mine died in the second or third year, and the machine is by now a teenager - the headphone jack continues to work. I.e. not Linux-related - install Windows, and you will see the same phenomenon - first, it will maybe work there 5-10 min rather than 30 seconds, but gradually, will degrade there, too...

---

### Post by arius88 on 2024-04-29
> **ninoivanov said:**
> It's the death of the speaker-part of your soundcard (the headphone jack(s) expected to work many years longer). Mine died in the second or third year, and the machine is by now a teenager - the headphone jack continues to work. I.e. not Linux-related - install Windows, and you will see the same phenomenon - first, it will maybe work there 5-10 min rather than 30 seconds, but gradually, will degrade there, too...

Thanks, yeah. I figured it was something like that. I got it home and plugged the speakers back into the headphone jack and I'm fine.

---

