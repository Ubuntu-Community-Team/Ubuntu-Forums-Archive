---
title: "Autotune for linux"
date: 2009-06-05
forum: Ubuntu Studio
---

### Post by WhyWontThisWork on 2009-06-05
Hi, I'm Looking for something which will allow me to autotune my voice... if you know of anything let me know please!!

---

### Post by conradin on 2010-04-01
[http://web.mit.edu/tbaran/www/autotalent.html](http://web.mit.edu/tbaran/www/autotalent.html)

---

### Post by DerickX on 2010-04-02
I think VocProc is an better one
[http://hyperglitch.com/dev/VocProc](http://hyperglitch.com/dev/VocProc)

---

### Post by adamantoi on 2010-04-02
agree with derick, i recommend VocProc.

---

### Post by bluefoxox on 2010-10-01
Can someone point me to the documentation on VocProc?  I am not having much luck getting it to work.

---

### Post by AutoStatic on 2010-10-01
Hello bluefoxox, there is no documentation. What's not working?

---

### Post by bluefoxox on 2010-10-01
I simple to not know how to use it.  I want to play with voice files, video files, etc.  I don't know where to start. I am a big fan of Ray Williams Johnson on youtube, saw this video [http://www.youtube.com/raywilliamjohnson#p/u/0/EBB7sYeCPoE](http://www.youtube.com/raywilliamjohnson#p/u/0/EBB7sYeCPoE) and decided I wanted to learn about autotune.

So, where to start?

---

### Post by bluefoxox on 2010-10-01
I think I am going to go to Windows for what I want to do.  Found a website [www.analogx.com](www.analogx.com) with many many tools for playing with audio files.

---

### Post by jssquared on 2010-11-01
Seemed like this would be the place to find some help on how to use vocproc, Any help would be appreciated.  Here is where I  am at currently using ubuntu 10.10:

I installed fftw3-dev, lv2-c++-tools, gtkmm-2.4, and vocproc through the software center

I  just started using linux this week and am just not sure if everything  installed correctly and how to actually utilize the vocproc software and  have found practically nothing on how to use it.  All I have ran  across was a video on youtube that just shows a person using it with  yoshimi and this thread. I tried to install yoshimi through the software center and when  I tried to open it a window popped up that said "bad things happened,  yoshimi strategically retreats."  

If there is any way you can help I would really appreciate it,

Thanks

---

### Post by jssquared on 2010-11-01
Correction, I installed the packages from synaptic package manager

---

### Post by Pablo_F on 2010-11-01
The bad thing is, very probably, that the jack daemon is not running. Install qjackctl (aka Jack Control or Control Jack) if you don't have it. Launch it and start the jack daemon (start button) **before** yoshimi. 

Jack is the sound server you need to use most of the music and audio oriented programs in Linux. In contrast, pulseaudio is the sound server oriented towards desktop use.

Note that if jack is started you will not have sound from apps that are not "jackified", i.e., that behave as jack clients. You can correct this if you install the package "pulseaudio-module-jack". It does not matter if you install software through the software center, synaptic, or apt-get, although this particular software package is not in the software center so you must use synaptic or just do a "sudo apt-get install pulseaudio-module-jack" in a terminal. Then for this to work you have to create the pulseaudio ports in jack with (open a cli with ALT-F2):

**pacmd load-module module-jack-sink channels=2**

Another program I recommend is patchage. In patchage you make the jack virtual connections (you also can make them in qjackctl, connect window). Audio ports are blue, jack midi ports are red and alsa midi ports are green. "System" is your soundcard, or better said, the device that jack is using as the final stage of the audio chain in the software side. In qjackctl this is called the "interface" when you use the same device for capture and playback (the usual thing to do).
 
You will see that yoshimi has a jack midi input but you may encounter other apps that only show green ports, i.e., alsa midi ports. You cannot connect alsa midi output ports to jack midi input ports. This is solved with the a2jmidid software and you launch it with:

**a2jmidid**

If you happen to have a midi keyboard, use:

**a2jmidid -e**

Now, back to vocproc. 

As vocproc is a LV2 audio effects plugin you need a LV2 host. LV2rack will do it. Install zynjacku (which can load lv2 instruments) which will install lv2rack, and launch lv2rack. Then load the vocproc.

Make connections in patchage. 

Cheers! Pablo

---

### Post by mango42 on 2010-11-01
A very 'lucid' explanation, **Pablo_F** ;-)

Just one point about **a2jmidid** that AutoStatic reminded me about - it's a daemon so needs to 'terminate and stay resident'

ie: **a2jmidid &** - this can also be set to run automatically from QJackCtl's options tab on the setup page.

---

### Post by Pablo_F on 2010-11-01
Thank you Mango42!

I have checked that if you launch it from ALT+F2 the ampersand is not needed, but it doesn't hurt either. 

To get jack and (these) friends running with one click, I suggest the following "script after start up":

a2jmidid -e & pacmd load-module module-jack-sink channels=2 & patchage &

And the "script after shutdown":

killall patchage a2jmidid jackd

And then, in the Misc tab, start jack audio server on application (i.e. qjackctl) startup.

The "artsshell -q terminate" is completely useless. In jack1 (karmic and lucid default jack) I am using "pulseaudio -k" but then you also want to avoid pulseadio autospawning. 


On the other hand, I have been trying the vocproc lv2, to no avail. I am not seeing what happens here. Anyone? LV2rack shows two inputs (left and right) and one output (vocproc). I have made several combinations of connections and settings in vocproc with a thrash guitar in yoshimi, to no avail. 


Anyway, I hope I helped jssquared with some basics of linux audio.

Cheers! Pablo

---

### Post by AutoStatic on 2010-11-01
> **Pablo_F said:**
> On the other hand, I have been trying the vocproc lv2, to no avail. I am not seeing what happens here. Anyone? LV2rack shows two inputs (left and right) and one output (vocproc). I have made several combinations of connections and settings in vocproc with a thrash guitar in yoshimi, to no avail.First input (most probably the left input) is the carrier, so any softsynth or instrument, the second input is the formant, so your voice. Output is mono.

When it comes to autotuning, now there's Zita AT1: [http://www.kokkinizita.net/linuxaudio/zita-at1-doc/quickguide.html](http://www.kokkinizita.net/linuxaudio/zita-at1-doc/quickguide.html)

Amazing little app. Available for Lucid in my PPA.

---

### Post by Pablo_F on 2010-11-01
Thank you Auto!

Oh, I was missing the obvious... :oops: I have set the vocproc to formant correction instead of vocoder!

On the other hand, yoshimi is giving xruns as hell with distorted and thrash guitars, with or without the vocproc. However, it seems to work fine with a clean guitar. All of this, is in ubuntu maverick that I have installed to test and put in the shoes of newcomers. Yoshimi is 0.058.1. Jack is jackdmp 1.9.6., default settings (p=1024, n=2, r=44100, realtime mode) with my hw:M2496 (m-audio audiophile 2496) which is alone in IRQ 22.

EDIT: I have tried the Zita AT1. Cool. I am curious about vocoders and voice autotuning, but in my heart I really hate them from the day I listened to that infamous song of Cher. I don't mind or even notice if the singer is a bit out of tune, but I really detest the autotune effect. As a joke between friends it can be funny though.

Cheers! Pablo

---

### Post by jssquared on 2010-11-01
WOW I must say, I did not expect such a fast reply that was so helpful.  Thanks everyone for your input!!  Especially Pablo! :)  I got everything installed and everything running (as far as I know) except vocproc, the final goal.  I tried opening the vocproc plugin with the lv2rack > Effects > Load  and opened it from that list.  The only thing that happens is lv2rack closes.  Probably missing something that I don't even know exists yet. Any thoughts on why this is working?


Also Pablo, I am not a hugh fan of the autotune effect in mainstream but let me tell you, me and my buddies have a blast messing with it while having a few drinks, lol!!!  The reason I am even exploring this is because the only source we have at the moment for a autotuner is an app on the iphone (t-pain app), So we all gather around the table and hook the speakers up to the iphone and have a blast.  I figured this would allow for a bit more flexability AND A MIC!!!!  Feelin like a real rock star.

Anyways thanks again!!!

---

### Post by Pablo_F on 2010-11-02
> The only thing that happens is lv2rack closes. Probably missing something that I don't even know exists yet. Any thoughts on why this is working?

Sometimes plugins make hosts crash. Try again and again. If it is a no-go, maybe your jack setting is not stable enough for your system or this version or LV2rack is a bit buggy, I am not sure. In adition to LV2rack (if it keeps on crashing) there are other LV2 host like traverso, qtractor or ardour. 

There is another vocoder in synaptic, called lv2vocoder. You also can try autotalent by Tom Baran (ladspa) or the LV2 version, called talentedhack. The binary:

[http://code.google.com/p/talentledhack/downloads/detail?name=autotalent1.82_linux_x86.tar.gz](http://code.google.com/p/talentledhack/downloads/detail?name=autotalent1.82_linux_x86.tar.gz)

you have to extract the files and copy or move the folder and its contents to /usr/lib/lv2. You can use "sudo nautilus" or the terminal with something like:

sudo cp -av autotalent.lv2 /usr/lib/lv2

The autotuner suggested by Autostatic: There is no binary for maverick, afaik. Compiling is not that difficult though.

Some of these plugins are available as LADSPA aswell (another plugin API). A simple host is Jack-rack (similar to LV2rack but for ladspa plugins). 

Happy autotuning! Pablo

---

### Post by lexen on 2011-06-22
I have it installed on 11.04 but I don't know how to get it started.

---

### Post by Pablo_F on 2011-06-22
Please, explain what you did and what you are trying to achieve so that someone can help you...

Cheers, Pablo

---

