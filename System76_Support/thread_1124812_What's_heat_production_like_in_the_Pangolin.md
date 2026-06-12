---
title: "What's heat production like in the Pangolin?"
date: 2009-04-13
forum: System76 Support
---

### Post by Sarai the Geek on 2009-04-13
This may seem like an odd question but for those of you with the Pangolin Performance, how hot does your laptop usually get?
I've had two laptops over the past two years that have had really awful lifespans, and also run quite hot. Correlation doesn't imply causation, of course, but a constant temperature around 160+ cannot be good for the hardware.
I'm now in the market for a new laptop and it would be great if I didn't get burns on my legs as I did with my macbook! :lolflag:

What's the word?

---

### Post by 3Miro on 2009-04-13
I guess it depends on the model, the 9300M motherboards are somewhat on the warm size, not bad though. 

Here is what mine does:

Normal work (docs, pdf, LaTeX, Open Office, FireFox) CPU is about 30 - 40 and GPU 57 - 63 (Celsius, don't get confused). On heavy CPU apps the CPU gets to 50 with the GPU in low 60s.

Haven't tried games.

It will be less if I turn off compiz or at least the cube, however, I have become to consider the 3D cube as irreplaceable part of the desktop functionality.

More often than not I do use it as suggested i.e. on top of my lap. I have not suffered any burns yet, it is warm but its fine.

---

### Post by Sarai the Geek on 2009-04-14
Great! I'm pretty impressed with the specs versus price on the pangolin, seems very reasonable and golly, can't beat the customer service.

---

### Post by 3Miro on 2009-04-14
I am sure if you get sys76 laptop and install windows on it, you will still get better support here than from Dell. I really like it that people are not like: "You changed the OS on the computer, we void your warranty"

---

### Post by Lee_Machine on 2009-04-14
I know S76 doesn't "officially" support Windows on their computers, BUT they do offer a detailed howto for dual booting, along with all the drivers needed. 

Which helps a lot, about 4 months ago I put a copy of XP on a 4 year old customs PC...wow hunting down all the drivers was a pain!!!!!!!

[http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine](http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine)

and the drivers,

[http://knowledge76.com/index.php/Panp4](http://knowledge76.com/index.php/Panp4)

---

### Post by 3Miro on 2009-04-14
My sister had to reinstall windows on her somewhat older computer. It windows, so everyone is supposed to have drivers for it, right? Took her 2 days to find the sound driver (computer wasn't Dell, just to clarify).

So with a Linux machine you may still get better windows support.

---

### Post by Lee_Machine on 2009-04-14
> **3Miro said:**
> 
So with a Linux machine you may still get better windows support.

Just to be fair that is also due to how dedicated the Linux community is to helping each other out. 

Enjoy the Pangoline, I have one and it works wonderfully. With Windows on it Im able to play such newer games as Half-Life 2 at max settings, and Elder Scrolls 4 at almost max. 

Heat wise....I would recommend putting the computer on a table, and not your lap. :lolflag:

(When playing said games)

---

### Post by Eldera on 2009-04-14
Newbie Question: How does one access/display the temperature?

My Pangolin runs warmer to the touch than my Acer and now I am curious if it is staying within safe limits?

Thank you, 76ers

---

### Post by Lee_Machine on 2009-04-14
Install X-Sensors from Add/Remove

---

### Post by 3Miro on 2009-04-14
On my desktop I play Oblivion (Elder Scrolls V) flawlessly. I have not tried it on the laptop.

X sensors do not work for me (it is some sort of a strange bug, many people have it). I installed command line lm-sensors and also nvidia x-server settings.

---

### Post by Eldera on 2009-04-14
3Miro
> X sensors do not work for me (it is some sort of a strange bug, many people have it). I installed command line lm-sensors and also nvidia x-server settings.

How did you install these? All I know is there are three ways to install things: apt-get, add-remove, and synaptic. And I have only used add-remove in windows.

I know you and I got machines about the same time, so I feel that there is a high probablity that if X sensors do not work for you, they will not work for me. 

I haven't tried anything yet. I thought there was something already installed on the machine, and I only needed to know where.

Thanks, Eldera

---

### Post by Cygnia on 2009-04-14
I've been following this thread since I received shipment of my new Pangolin last Friday (and am liking it a lot!) and also want to monitor the temps since this is my first laptop. I just installed xsensors using Synaptic, which also installed lm-sensors automatically (presumably as the backend.) I can confirm that xsensors does not work, with only a blank window opening with no content. More interesting, though is I can't find lm-sensors anywhere on the drive, though Synaptic indicated it was installing it, and indeed trying to run it in the terminal returns a "command not found" message. Maybe there's a problem with the install of the backend program? Anyway I thought it was interesting and hope to see if someone else more educated than me can figure it out.

---

### Post by thomasaaron on 2009-04-14
We dont' test with lm-sensors, but I know it works with some machines and not with others.

A good program to use to monitor your nVidia card is...

nvidia-settings

---

### Post by Sarai the Geek on 2009-04-14
I use "acpitempf" in Conky, but there is also an applet for gnome-panel that monitors temperature, it's in synaptic under "sensors-applet". It's not very configurable, though.

---

### Post by ResumeMan on 2009-04-14
My Pangolin CPU runs at about 45-50C in normal use, and goes up to about 70-80 when running World of Warcraft in Wine. I don't monitor any other temperatures.

---

### Post by 3Miro on 2009-04-14
I installed X-Sensors via Add/Remove and when it wasn't working I started researching why. There is a bug with it not recognizing the newer CPUs or something of the sort. It works neither on my desktop (AMD) nor on my laptop (Intel).

I configured lm-sensors manually (there is a pretty straight forward step-by-step script). I can just call "sensors" from the command line and it gives me the CPU temp. I even made a small python script that calls it every 2 seconds so I can continuously monitor the thing.

KDE has a CPU temp monitor tool that works on my Desktop.

For GPU temps, I use Nvidia-Setting.

---

### Post by Eldera on 2009-04-14
I found nvidia-settings. Thank you everyone.

---

### Post by Sarai the Geek on 2009-04-14
> **ResumeMan said:**
> My Pangolin CPU runs at about 45-50C in normal use, and goes up to about 70-80 when running World of Warcraft in Wine. I don't monitor any other temperatures.

Sweet. My hp right now is running about 60 during normal use and spikes up to 80 (gpu has gotten up to 95) when I'm running virtualbox. So the pangolin should be a little cooler, and hopefully my chillmat will help as well.

---

### Post by flukeairwalker on 2009-04-15
I haven't been taking my Pangolin anywhere recently, so I have it running with the battery out on top of a cooling rack. It's running now at 59C, which I guess is a normal number. Since my laptop is currently the center of my entertainment center, I leave it on all the time since I'm always using it.

---

### Post by 3Miro on 2009-04-15
> **flukeairwalker said:**
> I haven't been taking my Pangolin anywhere recently, so I have it running with the battery out on top of a cooling rack. It's running now at 59C, which I guess is a normal number. Since my laptop is currently the center of my entertainment center, I leave it on all the time since I'm always using it.

Have you tried to stop the cooling rack and see if it will get hotter. My Pangolin is well closed from below that cooling mat makes no difference for me.

---

### Post by flukeairwalker on 2009-04-15
Sometimes I turn off the cooling rack at night so it's a bit quiet, and no, the computer doesn't get too much hotter, going up to 63-64c.

---

