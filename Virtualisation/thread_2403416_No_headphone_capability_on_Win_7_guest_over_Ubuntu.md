---
title: "No headphone capability on Win 7 guest over Ubuntu host"
date: 2018-10-11
forum: Virtualisation
---

### Post by performex on 2018-10-11
Hello,

I'm running Ubuntu 18.04 on a Dell Optiplex 7020 with the usual architecture. 

I have Windows 7 Home Basic virtualized in a VirtualBox manager.

Everything works fine except I can't get the headphone jack to work.

I can use my Logitech USB headset just fine, but I can't get a TRS mic or headphones to work.

There are 12 combinations under audio settings regarding host audio drivers paired with VM audio drivers.

The only 2 that work are ALSA audio driver with Intel HD Audio and PulseAudio with Intel HD Audio.

These allow me to use the computer's speaker, but the headphone and mic options are greyed out in control panel > hardware and sound > sound.

It's my experience that the issue may be OS driver related, so I installed two different Intel chipset drivers.

Neither worked.

Any ideas, guys?

---

### Post by submiliand98 on 2018-10-31
Hi Performex 
Go inside the sound settings and when you plug in the headphones:
1 Look at the amount of loudness, put it up and make sure the "silent" option is not ticked.
2 Under the "Settings for Headphones" section, press the "Audit" button and see the sound from the headphones by scrolling through the check buttons in the open window.
3 Complete the Ubuntu updates, open the terminal, and write first:
> $ sudo apt-get update
And after the list of repositories has been updated, write:
Code: [Selection]
> $ sudo apt-get dist-upgrade
And let all the updates be done. Then restart the laptop and see if there is still a problem or not

---

