---
title: "Audacity kills qjackctl on application startup"
date: 2010-06-08
forum: Ubuntu Studio
---

### Post by asuastrophysics on 2010-06-08
Hi everyone

Whenever I try to launch Audacity with qjackctl already running, Audacity kills jack. I have no idea why. I even tried launching qjackctl as root, so that Audacity wouldn't have permission to do so. Same thing. In terminal, all it says is "killed".

Does anyone know why this happens? All I want to do is simply practice my bass on my computer. I hit "record" in Audacity, so that the computer plays back my bass through the speakers. If I don't use jack, I get crackling sounds and an increasingly lengthy delay in playback.

Can anyone help me? This really isn't that hard. I'm not asking much of my computer. I'm running good hardware, there is no reason for this...

---

### Post by asuastrophysics on 2010-06-08
bump

I'm sorry I bumped it so early! i really just want to practice my electric bass. right now it's impossible. I'm running the RT kernel, and audacity is giving me MASSIVE xruns, of up to half a second or more. (I'm guessing, because jack can't run with audacity running) 
The delay problem goes away if I only have audacity running and nothing else. 

Does anyone know why?

---

### Post by asuastrophysics on 2010-06-08
The only solution I've found for this is to just share the entire music folder on daap, then open up your windows 7 netbook that you bought at staples 3 months ago, and open up winamp. now choose your DAAP library. unplug your stereo from your desktop ubuntu pc. Now plug both the microphone and your stereo output jack into your netbook. Launch audacity on windows 7. BAM!!! No audio delays at all!!! From an Atom processor!!!

Is there another solution to this problem besides completely avoiding the ubuntu-studio OS?

---

### Post by asuastrophysics on 2010-06-08
EDIT: delete

---

### Post by cchhrriiss121212 on 2010-06-08
If all you want to do is hear your bass then there is no need to use audacity. Just use jack connections to route the bass signal straight to your playback channels. Its also not a good idea to run things as root.

---

### Post by Breambutt on 2010-06-08
Didn't know Bootsy visited these forums too, how awesome is that.

How do you connect the bass anyway, directly to the sound card or with a preamp or something? Might be that you've misconfigured JACK, setting latency too low or something dodgy going on with the input/output interface.

Also did you try using ALSA in Audacity? PulseAudio once again fails with tasks like this and the delay makes it completely unplayable for some people.

---

### Post by AutoStatic on 2010-06-09
Record your bass with another recording program that works better with JACK, like Qtractor.
Audacity and JACK don't get along because Audacity uses an extra layer to talk to JACK (PortAudio), that's where the massive xruns come from probably.

---

### Post by asuastrophysics on 2010-06-11
I tried installing qtractor, but it won't launch. In terminal, I get "bus error". Then, for the next 10 minutes, every program I try to launch crashes with the same error. 

I have no idea what is causing this, but it seems that qtractor is completely unusable. 

If i wanted to wire my input to my output port using jack, how do I go about doing it? I tried connecting some things under "Connections" in jack, but none of them seem to do this. Can someone give me a small tutorial on how to connect stuff? there doesn't seem to be any sort of user guide for qjackctl on their website...

---

### Post by cchhrriiss121212 on 2010-06-12
First open qjackctl and press start. Then go to the connections window, select the capture channel that your bass is connected to on the left and select the output channels your speakers are connected to on the right and press connect.

Regarding qtractor, are you running jack when you open it? If so what error message does jack give?

---

### Post by Pablo_F on 2010-06-12
"System" represents your audio hardware.
capture_1: first analog input. 
playback_1: first analog output.

You have to connect system:capture_1 to both system: playback_1 and system: playback_2.

Connect your gear to the first analog input of your card and you are done.

If something goes wrong, please tell us the card you have, jack settings, user PAM limits, and kernel and distribution versions: 

$ aplay -l
$ cat .jackdrc
$ ulimit -r
$ ulimit -l
$ uname -r
$ cat /etc/*release*

Cheers! Pablo

---

### Post by asuastrophysics on 2010-06-15
> **Pablo_F said:**
> "System" represents your audio hardware.
capture_1: first analog input. 
playback_1: first analog output.

You have to connect system:capture_1 to both system: playback_1 and system: playback_2.

Connect your gear to the first analog input of your card and you are done.

If something goes wrong, please tell us the card you have, jack settings, user PAM limits, and kernel and distribution versions: 

$ aplay -l
$ cat .jackdrc
$ ulimit -r
$ ulimit -l
$ uname -r
$ cat /etc/*release*

Cheers! Pablo
:popcorn: Thank you for your help. I tried doing the above under "Connections" before, on my own, but it didn't work. 

**Why wasn't it working before?** - Simply put, I was being an idiot. =D>
Under "Settings" in qjackctl, I had the "default" selected for "Interface". The problem with this is, the default card is my onboard sound card, which I don't use. I use a high quality studio edition sound card (SB Audigy 1 FTW!) 
This is why I couldn't hear anything for so long. 

THE SOLUTION (for me): Under "Setup" in qjackctl, I hit the sideways carrot sign > next to "Interface". I then chose "SB Audigy 1 [SB0090] as my device. I restarted jack, and made the appropriate connections.

Thanks to everyone who helped me out!!! :p
It is absolutely an indescribable feeling finally be able to practice my electric bass, now that I can finally hear it! 
:guitar:  Thanks again everyone!

---

### Post by Pablo_F on 2010-06-16
Warning: In different reboots you could have the ID numbers of your cards changed. You should double check the interface each time you reboot the computer or:


Disable the onboard audio device if don't intend to use it at all.

Use the alphanumeric ID of your card, instead of something like hw: x where x is a number. You can see this if you paste in a terminal:

cat /proc/asound/cards

Then write in the interface field:

hw:ID
where ID is the name in [Brackets     ]. Examples:

hw:Intel
hw:Live

---

