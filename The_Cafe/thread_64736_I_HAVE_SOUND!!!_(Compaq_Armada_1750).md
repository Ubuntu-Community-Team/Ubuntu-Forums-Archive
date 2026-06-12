---
title: "I HAVE SOUND!!! (Compaq Armada 1750)"
date: 2005-09-12
forum: The Cafe
---

### Post by mhancoc7 on 2005-09-12
I am just so excited about the fact that I finally after a year of trying finally have sound working on my Compaq Armada 1750. I have been though a few different distros including Warty Ubuntu and SimplyMepis. I decided to give Hoary Ubuntu a shot and within just a few days I have everything working on my laptop. I am running Win4Lin, Wine, Jpilot. I also have my DSL connection up and running and all my devices are automounting perfectly.

If any one has a Compaq Armada 1750 and is running the Hoary Ubuntu and needs help with sound I would be glad to help you out with what worked for me. I am not a Linux expert by any stretch, but I have become fairly familiar with the sound on the Compaq Armada 1750.

God Bless, Jereme
jeremehancock(at)whatwouldjesusdownload(dot)com

---

### Post by ProfBib on 2005-09-27
I already use Ubuntu on my desktop, but would like to install it on my Compaq Armada 1750 as well.  What was your solution to the vexing lack of sound?

---

### Post by YourSurrogateGod on 2005-09-27
A word of advice, don't post your e-mail address in a public forum, unless you enjoy receiving spam.

Congrats on getting sound to work :) . I felt the same way when I had my printer functioning flawlessly.

---

### Post by tseliot on 2005-09-27
[QUOTE=mhancoc7]I am just so excited about the fact that I finally after a year of trying finally have sound working on my Compaq Armada 1750. I have been though a few different distros including Warty Ubuntu and SimplyMepis. I decided to give Hoary Ubuntu a shot and within just a few days I have everything working on my laptop. I am running Win4Lin, Wine, Jpilot. I also have my DSL connection up and running and all my devices are automounting perfectly.

If any one has a Compaq Armada 1750 and is running the Hoary Ubuntu and needs help with sound I would be glad to help you out with what worked for me. I am not a Linux expert by any stretch, but I have become fairly familiar with the sound on the Compaq Armada 1750.

God Bless, Jereme
[email]jeremehancock@whatwouldjesusdownload.com[/email][/QUOTE]
I think you should write a guide (when and if you have the time) about it. A good HOWTO can save time and avoid frustration to many users.

---

### Post by mhancoc7 on 2005-09-29
Ok I have just finished my first How To: I will be posting it later tonight. I have put together a package that includes the tools necessary to create a Compaq Setup Disk. It can be very useful especially for checking and editing your irq settings.

You can download the How To package here:
[http://www.whatwouldjesusdownload.com/compaq_armada_1750_sound_setup_ubuntu.tar.gz](http://www.whatwouldjesusdownload.com/compaq_armada_1750_sound_setup_ubuntu.tar.gz)

I hope that this will be helpful.

God Bless, Jereme

---

### Post by ProfBib on 2005-10-17
Bravo to you, Jereme!

I used your how-to package and now have working sound on my Compaq Armada 1750! 

Just FYI, you may want to change the irq setting included in your sample modules file (irq=9): in the "README" file it is set to (irq=5) and it is the latter that does the trick!

Thanks for the help!  I am now 100% (K)Ubuntu on both desktop and laptop!

--Evan

---

### Post by mhancoc7 on 2005-10-17
I am so excited to hear that you got it working. It is nice to have the laptop come alive when I turn it on.

I left the irq setting in the example set to irq=5 because I have had several people email me and say that worked for them and it was the original setting on my Compaq Armada 1750. I had to change my setting to 9 as well, but I figured it is better to try it with the default setting and then if it does not work change it to 9.

Thank you so much for letting me know that you got it working. 

God Bless, Jereme

---

### Post by ProfBib on 2005-10-19
Jereme,

Thanks for the clarification - I noticed your note about having to switch IRQ to 9 after I posted.  Guess I jumped the gun a little!  Anyway, thanks for your help!

---

### Post by ProfBib on 2005-10-19
Just an update

I wasn't satisfied with the performance of Kubuntu on my Armada (probably due to the age of the machine and lack of memory), so I decided to do a fresh install with what now seems like a long-term friend on my desktop, mainly Ubuntu.

The sound configuration worked fine with one caveat:  I had to insert

snd-es1688

into the /etc/modules file, as well.  I wonder why this step was unnecessary in Kubuntu...

I am also happy to report that there is a SIGNIFICANT improvement in performance with Ubuntu/Gnome.

---

### Post by mhancoc7 on 2005-10-20
I am not sure why you had to add that. It sounds like you have a different sound card than I do. 

I use Hoary Ubuntu Gnome and love it as well. I have wondered about trying Kubuntu as well as Breezy, but I think I am going to stick with Hoary Gnome. It runs great on my Compaq Armada 1750. My laptop has been upgraded quite a bit. It has a 500mhz Pentium III processor, 320MB RAM, and a 40GB hard drive. Ubuntu really screams on it.

God Bless, Jereme

---

### Post by majikstreet on 2005-10-20
[QUOTE=YourSurrogateGod]A word of advice, don't post your e-mail address in a public forum, unless you enjoy receiving spam.

Congrats on getting sound to work :) . I felt the same way when I had my printer functioning flawlessly.[/QUOTE]
@YourSurrogateGod he could post it like whatever at whatever dot com

@mhancoc7  enjoy :)

---

### Post by mhancoc7 on 2005-10-21
@majikstreet

Yeah, I should know better. I have edited it like you suggested. Thanks for the suggestion. 

God Bless, Jereme :)

---

### Post by tbrminsanity on 2006-08-12
Thank you so much.  I have been tring to get sound working on my Compaq Armada ever since I loaded Xubuntu on it (about 4 months ago).  The best solution I got so far was CD music and that was it.  Now it works without a hitch.  You rock!

:D

---

### Post by mhancoc7 on 2006-08-12
Awesome!!! I am glad that this thread is still being found useful. I don't have my Compaq anymore, but I remember how long it took me to get the sound working. Thanks for letting me know it worked for you.
Jereme

---

### Post by combat chuck on 2007-03-08
I just wanted to add a thank you to this thread because it helped me finally get the sound working on my Compaq Armada 1750.  I've been messing around with linux on this machine for four months now, and this was the breakthrough.

I'm running Linux Mint "Bianca".  I had already installed the bios (that's a pain in the neck, btw), so I made sure the sound was enabled and copied down the resource settings for the card.  Then I added two rows to the /etc/modules file:

snd-es18xx
sb io=0x0220 dma=0 mpu_io=0x330 irq=5

Another thing I did, which I got from a different forum and may nor may not have played a part in getting the sound to work was to create a file in /etc/modprobe.d/ titled "soundcard" and enter the following:

alias sound-slot-0 snd-card-0
alias snd-card-0 snd-es18xx
options snd-es18xx enable=1 isapnp=0 port=0x0220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=0 dma2=1

I'm a linux noob, so I don't really know if adding that extra file helped.  Also, I should note that ALSA doesn't seem to work.  I've got sound through OSS, and not in stereo, but it's definitely better than total silence.

Thanks!

---

