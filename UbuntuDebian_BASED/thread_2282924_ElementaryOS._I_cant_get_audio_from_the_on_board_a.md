---
title: "ElementaryOS. I cant get audio from the on board audio jack"
date: 2015-06-17
forum: Ubuntu/Debian BASED
---

### Post by A46R on 2015-06-17
I'm pretty new to linux in general.

I cant get audio on a desktop I threw together. Im using some cheap Amazon brand USB-powered speakers that have a standard AUX cable. They work just fine in windows, but on elementary and Ubuntu they don't work. 

I can use the volume slider (and even the keyboard volume keys) to control volume but but no sound comes out

I have tried disconnecting and reconnecting both the USB power and the AUX connection several times, and i have confirmed the speakers work in Win-7 

I've gone to sound settings tried both "devices" displayed in the out put section 

and I got alsa report thing.[ Link here]("http://www.alsa-project.org/db/?f=108d4a85bf9ddd3e96d41f3b2ef7ed9cc5b316df")

Im wondering if editing or tweaking something in here could help me. If so how do i fix this?

Thank you for reading this

---

### Post by thenh813 on 2015-06-19
Open a terminal (assuming you know how) and type the command:
```
alsamixer
```
If you don't know how to open the terminal, it's usually in system utilities or accesories.
I'l explain what it does and means.
Alsamixer is a command line input/output volume control utility.
[[IMG]http://s6.postimg.org/6kz7fvdrh/capture17306.jpg[/IMG]]("http://postimg.org/image/6kz7fvdrh/")
The first one is always master volume (main output),  if it says MM instead of OO like mine does it is muted. Simpel press the "M" key to toggle this. Look for the "PCM" volume control, and check to make sure it is not muted as well. Use the right arrow key to go over to PCM, and press the up arrow until it says 0dB gain, or turn it down to 0dB gain if the value is positive. This will ensure that the applications are outputting the maximum level to the card to amplify/convert to sound without distortion. Turn up the "Master" volume to 25% or similar and turn the speakers on, at a decent volume (maybe 50-75%), it might be either too quiet or loud, adjust the Master volume until it sounds right. If anything looks unusual, no sound card is found by alsamixer, or you are unable to unmute or increase volume on PCM or Master, this indicates a driver issue. I can walk you through acquiring/enabling the correct driver. If alsamixer does work, this indicated the regular volume utility (usually has an icon in the taskbar) is not configured correctly. It might not be changing any device, not changing the correct device or not configured which "volume adjustment" is the correct one to change. If this is the case, please tell me what utility you are using (Gnome/Ubuntu volume control, KDE volume control, Retrovol, etc).

 Furthermore, I would like a maximized fullscreen screenshot of:

1:    Alsamixer running in the terminal.
2: Alsamixer, press F2 and use the arrows and enter to select /proc/cards.
3: Alsamixer, press F2 and use the arrows and enter to select /proc/devices.
4: Alsamixer, press F2 and use the arrows and enter to select /proc/version.
5: Alsamixer, press F2 and use the arrows and enter to select /proc/PCM.

This way I know what card and how many different outputs/cards there are.
I will be checking this thread again in the morning for the next few days, waiting for a reply.

---

### Post by A46R on 2015-06-23
Thanks for your help! I turned up the volume on "master", "speaker", and "PCM" and made sure all bars said "00" at the base and have nothing to do with "M" I'm still no getting any audio. I just went as far as to unplug my DVI and go back to VGA because i thought  a digital audio signal was trying to be sent. Still no Audio. 

As for screen shots. Whenever i press print screen my system saves a all black picture into my pictures file. I'm guessing the built in screen shot feature is not working correctly. I will look into installing another screen shot tool (have any recommendations?) [Strike that battle for another day]

Took photos with phone and uploaded.




Cards:
[IMG]http://i.imgur.com/5px8itVl.jpg[/IMG]




Devices:
[IMG]http://i.imgur.com/gGE7IWol.jpg[/IMG]





Version:
[IMG]http://i.imgur.com/kqtCLPSl.jpg[/IMG]





PCM:

[IMG]http://i.imgur.com/vW973W3l.jpg[/IMG]


please advise.

---

### Post by thenh813 on 2015-07-02
ALC66X series cards. I never got my ALC665 to work. Ever.

 However, I'v heard this works on Laptops. Open a terminal (logged in as root with sudo -i, of course).

```

echo 'options snd-hda-intel model=laptop' | sudo tee -a /etc/modprobe.d/options

```

Then reboot. Tell me if it works.

Also, I'd put master at about 50%, because if it does work your in for a surprise LOL.
Reduce PCM until it has a dB gain of 0, or you may get slight distortion on some devices.
But, I suppose those tips applies when it works. Here's to hoping it does.
I'l check back tomorrow. Sorry for the late reply. Don't worry about the screenshots, they're fine.
I can suggest a screenshot utility after we get this fixed.

---

