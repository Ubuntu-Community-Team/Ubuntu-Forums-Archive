---
title: "jackrouter in lucid / wine"
date: 2010-05-05
forum: Ubuntu Studio
---

### Post by c00kie55 on 2010-05-05
Well i though that i cut use jackrouter.ini like in windows
and edit virtual numbers of audio channels but i cant even find it
i have tried to do a search from / on name JackRouter.ini but nothing shows up ?
what shall i look after...

or how do i set the number off wineasio channels in Ubuntu lucid 64 bit 
is it possible..

---

### Post by thorgal on 2010-05-05
there's a README file in the wineasio source code. You should read it first. It has the answers to your question.

---

### Post by c00kie55 on 2010-05-05
yep you where right 

the simple command was ASIO_OUTPUTS=24 /home/gorm/.wine/drive_c/Program*Files/NAME OF THE APP

now i got 24 virtual outputs from that application and do still love Ubuntu

thanX

so how do i give it realtime prio 

ASIO_OUTPUTS=24 chrt -f 89  /home/gorm/.wine/drive_c/Program*Files/NAME OF THE APP
 
or is there another way

---

### Post by c00kie55 on 2010-05-05
ASIO_INPUTS=4 ASIO_OUTPUTS=24 chrt -f 89  /home/gorm/.wine/drive_c/Program*Files/NAME OFF THE APPLICATION

give me 4 inputs and 24 outputs in that app.. and realtime off 89 (i hope)

---

### Post by thorgal on 2010-05-06
there is no need to change the RT priority level of the app as you did. The wineasio "driver" is a jack client and its jack_process callback is taken care of by the jackd audio thread which has RT prio (if you started jack in RT mode). What you are doing is different: you give RT prio to wine ... that's not very convenient as it will compete with the jack audio thread, which you definitely don't want ;)

so forget about the chrt stuff you added to your command line, jackd should take care of that if already started in RT mode.

---

### Post by c00kie55 on 2010-05-07
Ok how about some hard disk prio as it seams wine is a little slow with wave files
and for some strange reason wine seams to be allitle better with emulated sound drivers can that be true.. i guess wine is build to be as stable as possible but i wants to suck all the power out of it.

also my cpu's is by default on ondemand but i wants it to be at performance as it seams
more stable in wine less xruns i dont want to chance it on each reboot is there a way
 
i have noticed that the swap is almost never in use why. do i have to fill the rams
before system uses the swap file

guess i also wants lots of money a bigger house and a beautiful rock-guitar .. 

 
[CENTER][LEFT][LEFT] 		
[/LEFT]
[/LEFT]
[/CENTER]

---

### Post by c00kie55 on 2010-05-07
LOL

with chrt -f 89 dsp 30-40 under load 5-10 in idle and it seams pretty stable there
without chrt -f 89 dsp 50-80 it has about 20 in idle mode and its bouncing a lot 



maybe it is becource i have renamed wineasio.dll.so wineasio.dll and copied to system32 folder to get the app to register it.. and now it needs realtime rules

---

### Post by thorgal on 2010-05-07
my guess is: if you fill up your RAM and need more mem, swap will kick in.

I sometimes use wineasio and never have any xrun, even at sub 1ms of latency. This is because my jack setup is rock solid. Remember, get jack to perform well under heavy DSP load. wineasio will be a jack client and should perform well as well. But the smaller the audio buffer size, the higher the CPU load. So forget about ondemand (CPU speedstep or whatever clockrate jump mechanism) and use your CPU at full speed. 

About the wineasio dll, yes, you have to register it
```

regsvr32 path-to-libwineasio.dll.so

```

---

### Post by c00kie55 on 2010-05-07
well some wine apps dont se wineasio.dll.so but wineasio.dll in system32  folder

and my concern is that when i rename wineasio it loses  the rt rights 

[U]so how do i give 
/home/gorm/.wine/drive_c/windows/system32/wineasio.dll  realtime rights[/U] 

regsvr32  /home/gorm/.wine/drive_c/windows/system32/wineasio.dll (works without  realtime ithink)
regsvr32  /home/gorm/.wine/drive_c/windows/system32/wineasio.dll.so (same as  below) 
regsvr32 winasio.dll.so (works only in some apps)

by  the way i only got a intelhda (realtek alc 688 or somthing) in this  notebook
and i can get it to run at low latency 16 frames to but i  wants it to be stable when its running alot of things at the same time  and under wine so normaly i use 512 frames 
and buffer of 2 witch  gives me 23.2 ms latency the same as i use in windows with asio4all but i  would offcourse love to see it running at 16 frames when running 24  channels  of a sampler filled with waves under wine 

i would like  to forget about ondemand (CPU speedstep or whatever clockrate jump  mechanism) and use your CPU at full speed. but as default this machine  seams to work with ondemand i have just loaded cpu frequency scale to  the panel and its says my cpu's is ondemand i can chance it to  performace but at next reboot it will be back to ondemand i wants it to  remember the settings

---

### Post by thorgal on 2010-05-07
you have maybe a power manager thingy that is kick-started by your windows manager (GNOME ? KDE ?). You can disable this power manager or set a profile of your choice and save it as default. 
In my case, I just disabled any power management from the WM. I wrote a couple of lines in /etc/rc.local

```

cpufreq-set -c 0 -g performance
cpufreq-set -c 1 -g performance

```

(Dual core CPU)

You can alwso recompile your kernel and disable speedstep all together.

About your wineasio comments, I cannot fully understand the issues you are facing since I never experienced them. But remember that your laptop will not perform like a desktop that is built and configured for multitrack recording, multi-synth processing, etc. My own laptop (old by nowadays standard, a 1.6 GHz pentium M, 1 GB RAM) is able to do some multitrack recording at small lat (which is sort of useless in this case) but as soon as I fire up a software instrument (say Pianoteq for example, where small lat becomes important), it is about unusable :/

---

### Post by c00kie55 on 2010-05-07
it seams more easy to add thoes 2 lines in  /etc/rc.local than to recompile
i have a core2 duo 2 but guess its the same way

i got a laptop to with a delta 44 sound card.. but it dosent seam much better i have some more in and outs thats it ?
the cpu is also alittle slower 1.86 duo core and notebook is 2.3 duo 2 core 2 (centrino2)

you are ofcource welcome to come by and i will make you understand.. I live in copenhagen ;)

---

### Post by c00kie55 on 2010-05-07
well it didn't work the script also says

In order to enable or disable this script just change the execution bits.

how do i do that.

---

### Post by c00kie55 on 2010-05-07
is this the right command sudo chmod +x /etc/rc.local

---

### Post by thorgal on 2010-05-07
yes it is.

PS: if time allowed I would pass by ;) but time is very precious for me these days (I became a dad not long ago)

---

### Post by c00kie55 on 2010-05-07
you should tru to kids then:guitar: it takes all your time x 2 but congrats anyway 
well i added thoes two lines

cpufreq-set -c 0 -g performance
cpufreq-set -c 1 -g performanceto  /etc/rc.local
and then 
sudo chmod +x /etc/rc.local

but it still chance back to ondemand ?

---

### Post by thorgal on 2010-05-07
then it's your WM causing this (gnome or kde power management tool).

---

