---
title: "Wineasio Karmic Koala not working"
date: 2010-04-01
forum: Ubuntu Studio
---

### Post by burlikeule on 2010-04-01
Hello Everyone!

I downloaded and installed the newest version of wineasio and the asio.h from Steinberg.
During the installation process and the regsvr32 command were no errors. 

The problem is, if i start an audio application under wine, i dont get any asio channels. 
If i start the winecfg, there are also no wineasio channels.

Jack is working fine with all ubuntu apps, and also with wine. 

May you have any idea, what i made wrong?
Thank you very much for your help in advance!

Yours, 
Carsten

---

### Post by sgx on 2010-04-02
> **burlikeule said:**
> Hello Everyone!

I downloaded and installed the newest version of wineasio and the asio.h from Steinberg.
During the installation process and the regsvr32 command were no errors. 

The problem is, if i start an audio application under wine, i dont get any asio channels. 
If i start the winecfg, there are also no wineasio channels.

Jack is working fine with all ubuntu apps, and also with wine. 

May you have any idea, what i made wrong?
Thank you very much for your help in advance!

Yours, 
Carsten
Hi, install Reaper, windows EnergyXT2, and Cantabile12lite to use as vst hosts, and wineasio will show up in their respective preferences dialogues
for selecting asio devices. Plugins without ilok/pace/dongle almost always work in those hosts. Standalone and plugin versions of Native Instruments and IK Multimedia, among others, work. Computer Music Magazine dvd has dozens that work on every issue in the CM Studio, and Library folders, a steal at $17! 

Commands in wine cannot have blank spaces, they must be filled with *
as in

cd /.wine/drive_c/Program*Files

Some plugins refuse to work unless installed in

/home/user/.wine/drive_c/Program Files/Steinberg/VstPlugins

also, these .dll files were found necessary for one synth or the other over the years...put then in your 
/home/user/.wine/drive_c/windows/system32 folder, free downloads when googled

gdiplus
mfc42
mfc71
msvcp60
msvcp71
msvcp90
msvcr71
msvcr80
msvcr90

Hope this helps!

---

### Post by burlikeule on 2010-04-02
Hey Sgx,

thank you very much for your reply!

After I installed "reaper" i really could choose the wineasio driver!? 

But i still have a small problem. I use the system as a digital crossover and source for music and movies (jack, brutefir, ...) Now i would like to measure the impulse response of the room with a logsweep recorder like the LSR from [www.acourate.de](www.acourate.de) through jack.
The LSR tells me, that there is no ASIO-Driver.

Maybe i can reroute ASIO Channels in reaper to make them "visible" for other wine apps?  

Thanks again very much for your effort!

Carsten

---

### Post by sgx on 2010-04-03
> **burlikeule said:**
> Hey Sgx,

thank you very much for your reply!

After I installed "reaper" i really could choose the wineasio driver!? 

But i still have a small problem. I use the system as a digital crossover and source for music and movies (jack, brutefir, ...) Now i would like to measure the impulse response of the room with a logsweep recorder like the LSR from [www.acourate.de](www.acourate.de) through jack.
The LSR tells me, that there is no ASIO-Driver.

Maybe i can reroute ASIO Channels in reaper to make them "visible" for other wine apps?  

Thanks again very much for your effort!

Carsten

Hi, 
you can specify a number of asio outputs, I took this quote from here:

[http://proaudio.tuxfamily.org/wiki/index.php?title=ASIO_with_Wineasio](http://proaudio.tuxfamily.org/wiki/index.php?title=ASIO_with_Wineasio)

"Wine ASIO allows specifying the number of inputs and outputs via environment variables. 
In BASH this looks like 
export ASIO_INPUTS=4
export ASIO_OUTPUTS=8

Or to set it statically, put above lines in ~/.profile. 

 Finally start your application, and select Wine ASIO as audio output driver, if not chosen automatically."

----------------------------------------------------------------------------------------------------------- 



I installed the acourate demo, and started it with

wine /home/your-name/.wine/drive_c/Program*Files/AudioVero/AcourateTrial/Acourate.exe

It took about 4 minutes to start, a rare experience, first a demo message appeared, then the gui popped open, and I tried dozens of menu options, and all the sub-screens popped up, yielded more screens, widgets all seemed to behave, I followed the logsweep tutorial for recording data within audacity, but I have no mic/preamp hooked up, it looks on the surface as if it might work. There appears to be no preferences option to select an asio driver. If an error appears, I would check their forums. It looks like a pretty nice application, it will be handy when building a recording room, and isolation areas.

Cheers

---

