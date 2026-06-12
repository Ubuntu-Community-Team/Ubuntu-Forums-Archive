---
title: "Pangolin Performance Overheating"
date: 2008-11-01
forum: System76 Support
---

### Post by Lee_Machine on 2008-11-01
I just purchase the new Pangolin and upon opening it up I upgraded to 8.10.
The laptop would freeze up and I didn't know why. I thought it might be a heat issue as it gets really hot.

sure enough after installing lm-sensor and gnome-sensor applet the GPU, mainboard, and CPU all overheat just from normal use. Web browsing, playing videos.

I searched for hours for a thread that would help but I cannot find one for my hardware. 

Any help would be wonderful.

The specs are:

Pangolin Performance
panp4n
Core2Duo t5800
nVidia GeForce 9300M GS 512MB DDR2 

I even have all effects turned off and my GPU is idle at 60C!

I hope this is a software issue and not hardware, as I live in Japan and dont want to have to send it back for repairs!

---

### Post by marcor on 2008-11-01
I have a similar problem. I have been running hardy for about two months without any problems on my panp4i. But when I upgraded to 8.10 I started to get sudden freezes very often(about every 10 minutes). So much that the system is now unusable. Plus I can't set the screen resolution to a wide screen aspect ratio. This is very annoying too. I suspect there is some major bug either in intrepid or in the system76 drivers.

Marco

---

### Post by jdb on 2008-11-01
I'm sure that you will get a response from thomasaaron Monday, but in the meantime you might try this.

Open a terminal and type top.

A window will open that shows the top CPU users and a column showing the % of CPU use.
If you have a process up around %100, that is the culprit.

To close top type q.

jdb

---

### Post by Lee_Machine on 2008-11-01
> **marcor said:**
> I have a similar problem. I have been running hardy for about two months without any problems on my panp4i. But when I upgraded to 8.10 I started to get sudden freezes very often(about every 10 minutes). So much that the system is now unusable. Plus I can't set the screen resolution to a wide screen aspect ratio. This is very annoying too. I suspect there is some major bug either in intrepid or in the system76 drivers.

Marco
but 
Mine did the sudden freeze thing until turned off all desktop effects under appearance.

*edit*

I just installed nvclock from source. It's a tool to used if I want to overclock my GPU and do Quadro faking, and control fan speed.

It says that the temperature is steady around 32C which is good and obviously wrong.

Fan speed is only available using the binaries. So I did the command. nvclock -F 60

and it says fan control is not supported for my video card. damn!
 
Then I read that this program does not fully support Gfroce 9 yet.

It sucks that my first Ubuntu laptop had to did this. Ive been with Ubuntu since Warty!

---

### Post by gila_monster on 2008-11-01
I am still running 8.04 on my Pangolin. I think I'll wait for thomasaaron's sage response before proceeding with the update. Two things, for what they are worth:

[LIST]
[*]I updated my other laptop (Gateway, four or five years old), and have not noticed any increase in how long the fan is on. I can't vouch for the actual temperature of the chips, as I can't get the sensors to work with the applet. Maybe I'll play with it tonight.
[*]The CPU temp on the Pangolin runs between 40 and 45 C most of the time. I haven't seen the GPU temperature go below 46 at any point, and the fan runs at varying speeds, but all the time.
[/LIST]

I'm curious as to what my CPU/GPU temps ought to be in general. I haven't had the Pangolin long enough to develop a good metric for that.

---

### Post by Lee_Machine on 2008-11-02
Ok, so I no longer think that it is a overheat issue. I started using the new Nvidia driver 177 and i no longer get heat spikes, but at random intervals the system will freeze and require a reboot. from 10 minutes to a few hours. 

Defiantly not a stable system that I can use for school work. But I have confidence that the issue will be resolved.

I've also attached a copy of my log file.

---

### Post by thomasaaron on 2008-11-03
OK, first, we've not experienced any overheating issues in our in-house testing. Second, none of the temps mentioned in this thread are indicative of overheating.

Second, if you hose your system by overclocking your gpu, that can't be covered under warranty.

That said, let's try figure out what's going on:
Can you give me steps to reproduce (what programs are you running when it freezes, etc...) I'll try to reproduce it in the shop. Also, if you still think you're overheating, please provide specific temps, and I'll compare them to what I'm seeing.

---

### Post by Lee_Machine on 2008-11-03
I no longer think that it is a heat issue. The temperatures stay stable at around 50-55C on everything.

The only issue that I have is the laptop will freeze up at random times. The applications that im running vary from VLC to Firefox.

I dont use it to much as I'm having this issue.


I wanted to downgrade back to 8.04 but I cannot get a CD to install.

I either get a busy box error or when I reboot with the Live-CD and I choose either install ubuntu for run it live it doesn't do anything. The computer just locks up.

I tried multiple CDs and downloaded different flavors. Is there some sort of setting is BIOS maybe that prevents installing a new OS?

And again thanks for your help. I love the laptop. It just keeps crashing on me. 

I'm sure its just a simple bug somewhere.

---

### Post by thomasaaron on 2008-11-03
A CD install may not work with anything but the newest cd. I would encourage you to install 8.10 64-bit, but you need a freshly downloaded CD. 

I think you'll find that Intrepid works fine on your computer. It sounds like you have have a botched upgrade for whatever reason. 

So, install 8.10 64-bit and then run the System76 driver. Then reboot. Contact me at support(at)system76(dot)com if you have any questions.

If you really need 8.04, try installing it in low-graphics mode. To do this, press f4 when you see the live cd menu. Then select low-grapics mode and hit enter twice.

---

### Post by Guitar John on 2008-11-03
I'm going to go against my better judgment and chime in here because, even though I do not (currently) own a system76 computer, I have been having the same problem for several months.

I suspected a heat issue as well, and I still haven't ruled that out.  I have done a fair amount of googling in search of a solution to no avail, so perhaps it will turn up here.

Cheers,
John

---

### Post by thomasaaron on 2008-11-03
Lee_Machine has re-installed, and that seems to have fixed the problem. Lee Machine, please let us know if you continue to have difficulties.

---

### Post by Lee_Machine on 2008-11-03
I was able to re-install 8.10 bit bit in low graphics mode. I have no heat issues now. Like the guy from tech support said sometimes with upgrading some packages get corrupted. 

Ubuntu is running like it should and so is the Pangolin.

Thank you S76 for the help.

---

