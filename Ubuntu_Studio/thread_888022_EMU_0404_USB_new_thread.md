---
title: "EMU 0404 USB new thread"
date: 2008-08-12
forum: Ubuntu Studio
---

### Post by grastein on 2008-08-12
Hi, everyone! 

I hope someone can help me, I have the EMU 0404 USB and it is not working "out of the box". I know that. But I know that someone has made it work! 

There is an other thread about this subject, but it is (to me) a very large and hard to figure out. 

My question is: are there anyone who can give me any hints how to make in work. just a bite! ...

I have seen on ALSA wiki that "Emu has delivered data sheets to developer". but it seems to be a long time ago. Are there any progress in that? 

well, Are there anyone who can help a not too experienced linux user? in anyway? or know where to start. 
that would be appreciated!


Simon Grástein! :)

---

### Post by klss on 2008-09-05
Hi there.

You need to update the 0404 USB firmware via Windows first.

In this case the card defaults to 44.1 after turning it on.

This way you can run very basic 44.1 via the snd_usb_audio.

However. I guess you'll experience XRUNS ( scratched sound)
once in a while. As I said the driver works rather by coincidence
on a very basic functionality basis.

Cheers

---

### Post by Mourner on 2008-09-15
I wonder if there any progress on the driver at all. :(
It's the only issue that prevents me from using Ubuntu instead of Windows XP. That scratches and overall instability (e.g. sound system crash after 10 minutes of playing) make it totally unusable for me.

---

### Post by klss on 2008-09-15
If you get along with 44.1/16, you need to install the newest ALSA > 1.0.17 manually.

Underruns/Hickups will disappear.


Here is a nice script: [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

You need to change a line inside for snd-usb-audio driver support:
----------------  
#alsa-driver
cd /usr/src/alsa/alsa-driver*
./configure --with-cards=all --with-card-options=all --with-seqencer=yes --prefix=/usr
make
make install

----------------------

I introduced a more advanced script over here, which covers above, mulitple ALSA package select, 2.6.27 kernel(non-Ubuntu), pulseadio,...  support:

[http://ubuntuforums.org/showpost.php?p=5792918&postcount=104](http://ubuntuforums.org/showpost.php?p=5792918&postcount=104)

Enjoy.

Cheers

---

### Post by Mourner on 2008-09-18
Awesome, thanks a lot for such a helpful answer! Will try that out ASAP and report my success here. 44.1/16 is perfectly fine for me. :)

---

### Post by Mourner on 2008-09-18
Just tried this script (with your modifications) - after rebooting the scratches/crashes remained - cat /proc/asound/version stills says that ALSA 1.0.16 is running, maybe I forgot to do something afterwards?

---

### Post by bofphile on 2008-09-20
For information, I filed a bug on lauchpad, it concerns the E-MU 0202 USB but it's the same basic hardware as the 0404: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/243381]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/243381")

---

### Post by klss on 2008-09-21
> **Mourner said:**
> Just tried this script (with your modifications) - after rebooting the scratches/crashes remained - cat /proc/asound/version stills says that ALSA 1.0.16 is running, maybe I forgot to do something afterwards?

Try my latest script version -  [http://ubuntuforums.org/showpost.php?p=5792918&postcount=104](http://ubuntuforums.org/showpost.php?p=5792918&postcount=104) . 

You can just run it again.

I added some comments inside the script, especially how to log the output. This way you can see if something went wrong.

Please let me know how it worked.

Cheers

---

### Post by klss on 2008-09-21
> **bofphile said:**
> For information, I filed a bug on lauchpad, it concerns the E-MU 0202 USB but it's the same basic hardware as the 0404: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/243381]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/243381")

Hi.

Alsa is neither supporting the EMU 0202USB nor EMU 0404USB officially (status: driver 1.018.rc3). They just made Alsa recognizing the card. 

If these boxes work, they work by coincidence and 44.1/16 only

It seems that some Alsa designers got the specs and even a test system from EMU almost a year ago. 

I tried to get in touch with Clemens Ladisch about it. No response. If've seen some people at several places offering help. They do not seem to be interested.

Afaik there is one major difference between 0202 and 0404. 
The 0404 is working in asynchronous transfer mode (slaving the PC).

Cheers

---

### Post by bofphile on 2008-09-21
Hi,

Thanks for the clarification. I thought the 0404 USB device only had some extra connectivity (S/PDIF I/O ...), and therefore would work the same way as the 0202 box.

Regarding the development of the driver, the last time I saw anything going on was on the alsa-dev mailing list: [http://thread.gmane.org/gmane.linux.alsa.devel/51724/focus=51861]("http://thread.gmane.org/gmane.linux.alsa.devel/51724/focus=51861")

From there I thought those devices would work without problem at 44.1kHz/16bits on the following alsa-driver release. But even with Intrepid Alpha 6, I still have a problem (mainly a glitch every 30 secs or so). The weird thing is my device worked flawlessly on Fedora 9 last time I tried.

Do you think we can still hope to have a full featured driver in the near future ? Or is there not enough demand to develop it?

---

### Post by uhappo on 2008-09-21
We need the driver for 0404 USB!

---

### Post by klss on 2008-09-22
> **bofphile said:**
> Hi,

Thanks for the clarification. I thought the 0404 USB device only had some extra connectivity (S/PDIF I/O ...), and therefore would work the same way as the 0202 box.

Regarding the development of the driver, the last time I saw anything going on was on the alsa-dev mailing list: [http://thread.gmane.org/gmane.linux.alsa.devel/51724/focus=51861]("http://thread.gmane.org/gmane.linux.alsa.devel/51724/focus=51861")

From there I thought those devices would work without problem at 44.1kHz/16bits on the following alsa-driver release. But even with Intrepid Alpha 6, I still have a problem (mainly a glitch every 30 secs or so). The weird thing is my device worked flawlessly on Fedora 9 last time I tried.

Do you think we can still hope to have a full featured driver in the near future ? Or is there not enough demand to develop it?

THX for that link. I digged a bit into it.

The discussion ended by the time they figured out that they need the control codes to set the registers. :roll:

I don't think it is too difficult to write a quirk for that card if you have these control codes. 
And as I said, EMU stated over here [http://ubuntuforums.org/showpost.php?p=4892734&postcount=157](http://ubuntuforums.org/showpost.php?p=4892734&postcount=157) that they have delivered these to ALSA development.

I think there are quite some people around -including me - who'd like to get the EMU driver. The 0404 USB is well known for its sound quality. 

Cheers

---

### Post by Mourner on 2008-09-26
> **klss said:**
> Try my latest script version -  [http://ubuntuforums.org/showpost.php?p=5792918&postcount=104](http://ubuntuforums.org/showpost.php?p=5792918&postcount=104) . 

You can just run it again.

I added some comments inside the script, especially how to log the output. This way you can see if something went wrong.

Please let me know how it worked.

Hi! Your script worked flawlessly this time. The scratches disappeared and overall the sound system seems more stable, but still after approx 30 minutes of playing the system started hanging (first the sound stops working and then eventually all running applications stop to respond).

---

### Post by klss on 2008-09-27
> **Mourner said:**
>  but still after approx 30 minutes of playing the system started hanging (first the sound stops working and then eventually all running applications stop to respond).

Hmmh. :confused: Never happened to me. 

30 minutes is quite a long time. Obvious problems usually occur within seconds. 

Is it a sporadic problem? Perhaps you should try to trace it down a bit more.

---

### Post by uhappo on 2008-09-28
Did I undestand this right?

If I run that script from klss, my 0404 USB should work?

---

### Post by klss on 2008-09-28
> **uhappo said:**
> Did I undestand this right?

If I run that script from klss, my 0404 USB should work?

Yep. It'll work.44.1/16  only. Flawless. Playback only! 
SPDIF/Toslink works via plughw:X,1

I am trying hard to get in touch with the ALSA designers.
I still havn't figured out who actually received the data 
from EMU.

Cheers

---

### Post by bofphile on 2008-09-29
> **klss said:**
> 
I am trying hard to get in touch with the ALSA designers.
I still havn't figured out who actually received the data 
from EMU.

Cheers

Isn't it a developer named James who received the datasheets from E-Mu ?
[https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=emu]("https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=emu")

---

### Post by klss on 2008-09-30
> **bofphile said:**
> Isn't it a developer named James who received the datasheets from E-Mu ?
[https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=emu]("https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=emu")

Yes, that's him and at least one other guy. I finally got in touch with the guys at ALSA. 

They - these two persons only - do have the datasheets available, but are not allowed to share them. 
They estimate the effort to get the driver developed a week of continuous work. 
Since they have only hours during the weekends for designing the drivers - it'll probably take a while - they have not even started yet.

I'll keep you posted.

Cheers

---

### Post by Mourner on 2008-09-30
> **klss said:**
> Hmmh. :confused: Never happened to me. 

30 minutes is quite a long time. Obvious problems usually occur within seconds. 

Is it a sporadic problem? Perhaps you should try to trace it down a bit more.

It occurs after a couple of tens of minutes playing music with Rhytmbox (if I don't play music, it always works fine) - haven't checked this with another player though, will do this soon.

First the sound stops, then every new launched application doesn't respond (e.g. Firefox that was launched before the hang happened is working, but Terminal or FF when closed and launched again just hang immediately after launching). Even shutdown doesn't work. So the system becomes totally unusable until a full reset.

---

### Post by klss on 2008-10-01
> **Mourner said:**
> It occurs after a couple of tens of minutes playing music with Rhytmbox (if I don't play music, it always works fine) - haven't checked this with another player though, will do this soon.

First the sound stops, then every new launched application doesn't respond (e.g. Firefox that was launched before the hang happened is working, but Terminal or FF when closed and launched again just hang immediately after launching). Even shutdown doesn't work. So the system becomes totally unusable until a full reset.

Are you running a rt-kernel (Ubuntu-Studio)? Do you have network traffic ongoing at the time the system hangs up? 

Any strange messages in the logfiles (syslog,messages,kern.log,dmesg) under /var/log?

Cheers

---

### Post by TimCastle on 2008-10-07
klss, thank you for your script. I have tried both scripts and both versions of alsa on fresh installs of hardy and intrepid. 

In /etc/modprobe.d/alsa-base, I set 
options snd-usb-audio index=0
options snd-hda-intel index=1

I do not think this has anything to do with my problem. 
 
In every case, when system/preferences/sound is set to ALSA, my emu 0404 usb sounds very distorted. 

But when system/preferences/sound is set to Autodetect/OSS/PulseAudio, my emu 0404 usb sounds OK. 

Please, help me k l s kenobi; you're my only hope.  Why does my emu 0404 usb sound distorted with ALSA?

---

### Post by klss on 2008-10-08
Most probably a sample rate issue.

Did you upgrade the firmware via Windows? Otherwise it runs 48khz by default.

Some applications like Amarok do output/resample to 48khz. 

Could be that your Pulse runs 48khz.

Pulse streams also via Alsa. It shouldn't be Alsa causing your issues.

Run following command while playing back, assumung the EMU is the 1st soundcard. 

$ cat /proc/asound/card0/stream0

The first couple of lines in the output should look like this:

Playback:
  Status: Running
    Interface = 1
    Altset = 1
    URBs = 8 [ 1 1 1 1 1 1 1 1 ]
    Packet Size = 274
    Momentary freq = 44098 Hz (0x5.8320)
  Interface 1


This way you can checkout what samplerate you are actually running, while playing back.


Note: Modify your alsa-base file for better sound to :

options snd-usb-audio index=0 nrpacks=1



Good luck.

---

### Post by klss on 2008-10-09
Hi folks.

Another hint :

Since you're all able to install the Alsa driver manually, I recommend to 
tweak the usbaudio driver a bit.

If you use my Alsa download and installation script you need to edit following file (use the download only option first): 

$ sudo gedit /usr/src/Alsa-1.0.18rc3/alsa-driver-1.0.18rc3/sound/usb/usbaudio.c

Find following section (line 1922)
---------------------
snd_pcm_hw_constraint_minmax(runtime, SNDRV_PCM_HW_PARAM_PERIOD_TIME,
				     1000 * MIN_PACKS_URB,
				     /*(nrpacks * MAX_URBS) * 1000*/ UINT_MAX);

-------------------------
change it to
-------------------------
snd_pcm_hw_constraint_minmax(runtime, SNDRV_PCM_HW_PARAM_PERIOD_TIME,
				     125 * MIN_PACKS_URB,
				     /*(nrpacks * MAX_URBS) * 1000*/ UINT_MAX);


---------------------
and save it.


Now run my script again and install Alsa.

Let me know what you think!

Cheers

---

### Post by fisk0 on 2008-10-12
I have a E-mu 0404 PCI card and consider to install Ubuntu on that computer, does anybody know if the PCI version is supported?
And if it is, does anybody know about anything similar to E-mu's "PatchMix DSP" program that allow you to set up different sound effect chains for every port of the card?
I usually play internet radio streams through another ubuntu system with an old and noisy soundblaster card, and have set up PatchMix on my XP machine to run a compressor, leveler and noise gate on the input from that computer.

---

### Post by klss on 2008-10-14
Hi.

Checkout this [http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1](http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1)

Your card is supported.

Good luck

---

### Post by uhappo on 2008-11-18
Any news about USB 0404?

Mine works out of the box in intrepid, but only in 16bit and output only

---

### Post by soundcheck on 2008-11-19
> **uhappo said:**
> Any news about USB 0404?

Mine works out of the box in intrepid, but only in 16bit and output only

Nobody is working on it over there at ALSA.
It needs a week of work to get it going according to the devlopper.

I don't get the specs by myself. Otherwise I would have started  to look into it already.

---

### Post by pacmansyu on 2008-11-26
Just wanted to add to the list of (partial) successes... audio output works on new install of Intrepid (8.10), no modifications necessary. 44.1khz, 16 bit.

---

### Post by uhappo on 2008-12-11
So whats this?

> 
SCOTTS VALLEY, CA - December 1, 2008 - E-MU Systems today announced that for the first time it will release as open source the Macintosh driver stack for its award winning USB 2.0 audio interface products - the 0202USB, 0404USB, and TrackerPre. The Software Developer Kit will be available on the SourceForge developer’s website in early December and can be found at:[https://sourceforge.net/projects/zaudiodrivermac/](https://sourceforge.net/projects/zaudiodrivermac/). The software will be released under the GNU Lesser General Public License or LGPL v3, which enables developers to commercially redistribute products derived from this code base.

The Software Developer Kit will include the E-MU USB 2.0 driver interface specification and necessary source code for adding new features, enhancing performance, or porting to other Operating Systems.

"We are releasing this code to the public to enable programming enthusiasts the ability to experiment with and to extend the capabilities of our products, which we find being used in a variety of applications outside of the MI space proper. I'm convinced that our clever user base will come up with innovative variations not addressed by our mainstream activities," said Michael Lee, marketing manager for E-MU Systems. "I'm excited to see the results generated by the OpenSource community."


---

### Post by soundcheck on 2008-12-11
Sounds cool. Probably they're gonna phase out the 0404/0202. ;)

We should let the ALSA folks know. Where did you find it?

---

### Post by soundcheck on 2008-12-11
I posted it at the ALSA mailing list. Let see if somebody is answering.

Perhaps the other thing coming up with this would be the availability
of the datasheets to public. In the end the NDA wouldn't make any sense 
any longer. I'll check it out.

---

### Post by TimCastle on 2008-12-11
Thank you for the good news uhappo. People still need full EMU0404 support! Let's hope it is right around the corner. Oh, and if you work on this soundcheck, thanks as always - your work is much appreciated.

---

### Post by uhappo on 2008-12-12
I found it at Gearslutz-forums

[http://www.gearslutz.com/board/3722314-post1.html](http://www.gearslutz.com/board/3722314-post1.html)

I've got no skills to work with drivers, but I'm anxious to use my EMU in ubuntu. Now, get those drivers going on...!!!

---

### Post by bofphile on 2008-12-14
So there's still hope to see my 0202 USB device work flawlessly under Ubuntu some day. Great news !:p
I just hope the Alsa developers will be motivated enough to work on this.

---

### Post by soundcheck on 2008-12-23
Hi folks.

To enjoy 24/96 or other formats run or configure the 0404 under Windows with this format. Then DON'T turn it off to keep the settings. 

Now startup Linux. Startup you application of choice with 24/96 and output
to plughw.

Enjoy 24/96 under Linux!! It's really worth a try.

Now you need an application sampling everything to 24/96.

I'd recommend MPD - Music Player Daemon - for this and other reasons. It IMO sounds best of all apps under Linux anyhow.

Have a look at my MPD-Wiki at DIY-Audio for directions:

[DIY-Audio MPD Wiki]("http://www.diyaudio.com/wiki/index.php?page=Digital+Sources") 

Cheers

---

### Post by Matteye on 2008-12-29
I am fairly new to recording, and this is my first post on this forum. I am trying to use the E-Mu 0404 with Garage Band, and I have a couple questions:

1) When recording guitar using the direct line in, the playback is only out of the left speaker. When i record into Garage Band with the standard mic on my mac, this is not the case. What am I doing wrong?

2) I am getting a lot of hissing with my guitar. I'm using a standard acoustic with an insert pickup. Adjusting gain does not seem to work.

Any help would be greatly appreciated! Thanks.

MF

---

### Post by uhappo on 2009-01-17
Bump?

---

### Post by soundcheck on 2009-01-18
Hi there.

I am running the 0404 currently at 24/96. I switched to 96 under Windows.
The setting will remain as long as you don't touch the power-switch.
I'll do upsampling with MPD/Audacious and now my own player application.

A quite nice workaround.

Cheers

---

### Post by klotz on 2009-01-18
How do you "not touch the power switch" when you switch the device from a Windows computer to a Linux computer?

It seems like this might be ripe for someone to use usbsnoop and post the code so we can write a user-level USB utility to send whatever data they send for 96Khz (perhaps it's a register, or perhaps it's a firmware load).

---

### Post by ubuntoyou2 on 2009-01-21
I think he means turning the EMU 0404 USB off at the mains.  Maybe it keeps the settings.

---

### Post by kaworufw on 2009-01-24
Apart from setting the sample rate in Windows, you may also use the S/PDIF input to set the sample rate "memorised" in the emu0404 usb.  Again the max rate it can memorise is 96kHz....

For resampling in Linux a simple trick is to edit your ~/.asoundrc file.  No extra software is required.  ALSA will resample your stream using libsamplerate.  I'm using the "samplerate_best" which is just best_sinc in libsamplerate.

> 
defaults.pcm.rate_converter "samplerate_best"

pcm.!default {
	type plug
	slave {
		pcm "hw:0"
		rate 96000
	}
}


Anyway with the opensource of Mac driver I am really looking forward to better support of EMU0404 USB in Linux.... such as supporting 176.4kHz and 192kHz samplerate...

---

### Post by klotz on 2009-01-24
The 0404 may be able to keep settings but the 0202 is bus powered so switching computers powers it off.
The zmacsound drivers have 2 ways to set sample rate.
One uses isochronous usb which libusb 0.1 in Ubuntu doesn't support.
I tried to hack it but so far failed.
The other uses an 'extension unit' which appears to be an endpoint.
It looks promising.  It sets a calculated clock value.
I hope to wriyte a cmd-line util to set sample rate.

I can't use alsa resampling.  I need hardware sampling at 96khz for my digital signal processing application.  Right now it is stuck at 44.1khz...

Or are you all saying the sampple rate setting is nonvalatile and if set once with the windows or mac driver, that it will remain set through complete power off?

---

### Post by ubuntoyou2 on 2009-01-26
It must be a month since the mac drivers were open-sourced. It'll make life a lot easier when we have the drivers.
Meanwhile, I downloaded the latest ALSA drivers, utils etc,  1.0.19 and still couldn't get the 0404 USB to work. Tried the Soundcheck method too.No joy.  Strangely, it worked under OSS so I can finally listen to my EMU on Ubuntu. I just tried OSS as a wild shot; I'd tried everything else!!

---

### Post by kaworufw on 2009-01-28
> **klotz said:**
> The 0404 may be able to keep settings but the 0202 is bus powered so switching computers powers it off.
The zmacsound drivers have 2 ways to set sample rate.
One uses isochronous usb which libusb 0.1 in Ubuntu doesn't support.
I tried to hack it but so far failed.
The other uses an 'extension unit' which appears to be an endpoint.
It looks promising.  It sets a calculated clock value.
I hope to wriyte a cmd-line util to set sample rate.

I can't use alsa resampling.  I need hardware sampling at 96khz for my digital signal processing application.  Right now it is stuck at 44.1khz...

Or are you all saying the sampple rate setting is nonvalatile and if set once with the windows or mac driver, that it will remain set through complete power off?

Yes. The sample rate being "memorized" in the EMU0404 USB is non-volatile.  It keeps the setting even it is power cycled.  But it is up to 96kHz only.  Setting it to 176.4kHz or 192kHz it will return to 44.1kHz after power cycle.

---

### Post by kaworufw on 2009-01-28
> **ubuntoyou2 said:**
> It must be a month since the mac drivers were open-sourced. It'll make life a lot easier when we have the drivers.
Meanwhile, I downloaded the latest ALSA drivers, utils etc,  1.0.19 and still couldn't get the 0404 USB to work. Tried the Soundcheck method too.No joy.  Strangely, it worked under OSS so I can finally listen to my EMU on Ubuntu. I just tried OSS as a wild shot; I'd tried everything else!!

Do you use pulseaudio?  The new versions (i.e. 0.9.11 and newer) loses the support to EMU0404USB in contrast to previous version.  Try to use aplay directly to see if you can get some sound.  

aplay -D plughw:0 <wave file>

You may need to use plughw:1 or 2 if you have any other sound interfaces.

Currently I use ALSA directly by setting EMU0404USB as default ALSA device instead of pulseaudio, by using the .asoundrc in my earlier post.

---

### Post by uhappo on 2009-01-29
Why do you folks want to upsample? If the source is 44100?

---

### Post by klotz on 2009-01-29
> **uhappo said:**
> Why do you folks want to upsample? If the source is 44100?
I am not working with 44.1KHz audio signals.

I am working with radio frequency signals which have been converted to the high audio range, so getting 96KHz and 192KHz sample rates are the reason I bought the EMU-0202.  

By using two channels and 192KHz sample rate, you can them obtain data from 192KHz of radio spectrum, for demodulation or display.

You can read about this process in general terms by searching the web for software defined radio.

---

### Post by uhappo on 2009-02-20
Bumpty bum?

---

### Post by bofphile on 2009-02-20
Is there still any hope to have a working driver in a foreseeable future ? :-?
It seems like no one is working on it.

---

### Post by z0idberg on 2009-02-28
I'm interested in this too! I posted a question about the status on the alsa-devel mailing list a few days ago. As I've poked around a little more since then, I've found that a lot of people have been asking the same thing as me, and usually been referred to the same guy.

One discussion I found was this: [http://mailman.alsa-project.org/pipermail/alsa-devel/2008-December/013362.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2008-December/013362.html)
So someone did offer to take a look at it, I have no idea if they've done progress or not... Any other news on this?

---

### Post by bofphile on 2009-03-04
I've seen this discussion going on the alsa-dev mailing list:
[http://thread.gmane.org/gmane.linux.alsa.devel/60490/focus=60574]("http://thread.gmane.org/gmane.linux.alsa.devel/60490/focus=60574")

But nothing concrete at this moment.

---

### Post by v.stiff on 2009-04-16
Hi guys! 

I'm praising too for a better support of 0404 usb in linux.

Currently using jack as a primary sound server, killed pulse and routed everything through jack, it gives a bit more flexibility, more predictable resampling, and whenever I want to play my zynaddsubfx I can do it

Are there any news from the fields? :)

---

### Post by TimCastle on 2009-04-16
I too still need full EMU 0404 USB support! 
The current ALSA playback sound quality is inferior to windows with ASIO. 
I have not been able to use wine, or vmware/virtualbox windows xp to playback with ASIO. I do not think it is possible.

---

### Post by Yako on 2009-04-20
> **kaworufw said:**
> For resampling in Linux a simple trick is to edit your ~/.asoundrc file.  No extra software is required.  ALSA will resample your stream using libsamplerate.  I'm using the "samplerate_best" which is just best_sinc in libsamplerate.

Thanks, using 44100 for the sample rate fixed my distortion problems.

I had to remove PulseAudio and install Esound first though to get any sound at all:

[http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html)

---

### Post by beat on 2009-04-21
I tried the jaunty jackalope release candidate and wasn't able to get sound through my emu 0404 usb. Anyone had the same problem? Everything worked flawlessly with no configuration required on intrepid.

---

### Post by TimCastle on 2009-04-21
beat, try [soundcheck's ALSA Upgrade Script]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")

it worked for me

I am using Jaunty, and ALSA.

---

### Post by beat on 2009-04-21
It worked in jaunty? But are you still using pulseaudio?

---

### Post by z0idberg on 2009-04-24
> **beat said:**
> I tried the jaunty jackalope release candidate and wasn't able to get sound through my emu 0404 usb. Anyone had the same problem? Everything worked flawlessly with no configuration required on intrepid.
Same for me... if I open a terminal and write "pulseaudio -k", sound works for a few seconds (using the test button in sound preferences in Gnome) then stops working. I did file a bug when encountering the same problem in Arch Linux; [http://pulseaudio.org/ticket/510](http://pulseaudio.org/ticket/510) . I tried upgrading to PulseAudio 0.9.15 in Arch, which gives me sound, but just static.

---

### Post by thyraios on 2009-04-24
Emu 0404 usb doesn't work for me either after upgrading to 9.04. The only way I could make it work is by setting playback to OSS in Sound Preferences... 
It has nothing to do with upgrading. The card is recognized but alsa won't start streaming.

---

### Post by beat on 2009-04-24
Setting playback to OSS also worked for me. But using OSS isn't really an option. I think I might keep using Intrepid until this is fixed. Anyone tried upgrading alsa like TimCastle suggested? I also filled a bug in ubuntu's launchpad [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/363342](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/363342) .

---

### Post by thyraios on 2009-04-25
I tried soundcheck's ALSA Upgrade Script and it did not work for me. I've noticed that ALSA generally behaves strange. If I set in Sound Preferences playback to onboard soundcard (HDA Intel Stac92xx Analog (ALSA)) I get the same error as I get for EMU 0404 USB. If I set playback to Pulse Audio Sound Server onboard sound works but when I try to switch the stream to EMU 0404 it suddenly stops playing and if I switch back to onboard sound it resumes playback.

---

### Post by z0idberg on 2009-04-26
> **thyraios said:**
> I tried soundcheck's ALSA Upgrade Script and it did not work for me. I've noticed that ALSA generally behaves strange. If I set in Sound Preferences playback to onboard soundcard (HDA Intel Stac92xx Analog (ALSA)) I get the same error as I get for EMU 0404 USB. If I set playback to Pulse Audio Sound Server onboard sound works but when I try to switch the stream to EMU 0404 it suddenly stops playing and if I switch back to onboard sound it resumes playback.
What happens if you try "pulseaudio -k" in a terminal and then try the test button in sound prefereces (using PulseAudio and the E-MU)? For me, sound works for a few seconds after killing PA, my uneducated guess is that sound works because PA restarts and then stops working because the sink is suspended...

---

### Post by thyraios on 2009-04-26
> **z0idberg said:**
> What happens if you try "pulseaudio -k" in a terminal and then try the test button in sound prefereces (using PulseAudio and the E-MU)? For me, sound works for a few seconds after killing PA, my uneducated guess is that sound works because PA restarts and then stops working because the sink is suspended...

I cannot test it because I couldn't find the option in my BIOS to disable onboard sound and because of this after I enter pulseaudio -k the stream is automatically on the onboard card and I cannot change it (no pulse audio volume control working).

---

### Post by beat on 2009-04-26
On some older motherboards you can only disable onboard sound by changing motherboard jumpers.

---

### Post by thyraios on 2009-04-28
it's not that old (Inspiron 1525) but the BIOS doesn't have to many features. Anyway it turned out that the RT Kernel didn't like my dual core cpu (I was using Ubuntu Studio) and was using the second cpu at 100% all the time (my laptop was getting hot really fast and the 9cell battery would hold the system on for less that 2 hours :O ) so I reinstalled ubuntu (desktop-release) and everything seems to be ok now (exept for EMU 0404 of course).
Can someone estimate when will the next alsa-pulse update will be available?

---

### Post by soundcheck on 2009-04-28
Hi folks.

Seems to be a never ending story with the 0404. 
It would need a real hacker who takes the open OSX code and ports it to Linux. They estimated a week of work to get the EMU going. 


BTW. Jaunty comes with a Alsa 1.0.18 which is more then half a year behind  the current .19 stable release (the one installed with my upgrade-script). Though it won't make a difference from an 0404 perspective.

I hope you tried the basic tests to find out, if the 0404 gets recognised at all.

BTW. I completely removed pulseaudio.  I got no issues with it any longer. ;)

If you try to get the 0404 going, you need to do it with "plughw:X,X". plughw won't try to set the paramters on the 0404. It just sends everything out.
Using "hw" will cause problems.

Good luck

---

### Post by soundcheck on 2009-04-29
> **thyraios said:**
> it's not that old (Inspiron 1525) but the BIOS doesn't have to many features. Anyway it turned out that the RT Kernel didn't like my dual core cpu (I was using Ubuntu Studio) and was using the second cpu at 100% all the time (my laptop was getting hot really fast and the 9cell battery would hold the system on for less that 2 hours :O ) so I reinstalled ubuntu (desktop-release) and everything seems to be ok now (exept for EMU 0404 of course).


The rt-kernel used by Ubuntu is a mess. I do agree. 
As a matter of fact the rt-kernel Gurus (Ingo Molnar/Thomas Gleixner) started to look into it with 2.6.29 first time in two years.
They completly revised the old kernel rt-patch.

The "maintainers" from 2.6.26 onwards, never really had the rt-patch under control.

The pity: Jaunty is running on 2.6.28. The only way forward: Make your own kernel.



Cheers

---

### Post by beat on 2009-05-03
I'd really appreciate some detailed instructions (newbie here) on how to get my emu 0404 usb to work on jaunty.

---

### Post by v.stiff on 2009-06-02
Good news guys, I've found a patch at official alsa wiki: [https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=emu&show_comments=1](https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=emu&show_comments=1)
and it works for me too!

Here is link to patch: [http://pastie.org/483899](http://pastie.org/483899)

---

### Post by bofphile on 2009-06-02
Thanks for the link. How can I apply this patch ? And does it work with the 0202 USB ?

---

### Post by v.stiff on 2009-06-02
> **bofphile said:**
> Thanks for the link. How can I apply this patch ? And does it work with the 0202 USB ?
I dunno, but I think should work since they have same driver in windows and mac os x. I installed it by typing something like:

apt-get source alsa-base
cd alsa-driver-1.0.18.dfsg/debian/patches
wget [http://pastie.org/483899.txt](http://pastie.org/483899.txt) -O emu_usb.patch
echo emu_usb.patch >> series
cd ../..
debchange -i
dpkg-buildpackage -rfakeroot -uc -b
sudo debi

I may miss something, since it there was a lot of trials-and-errors

---

### Post by klotz on 2009-06-04
> **v.stiff said:**
> I dunno, but I think should work since they have same driver in windows and mac os x. I installed it by typing something like:

apt-get source alsa-base
cd alsa-driver-1.0.18.dfsg/debian/patches
wget [http://pastie.org/483899.txt](http://pastie.org/483899.txt) -O emu_usb.patch
echo emu_usb.patch >> series
cd ../..
debchange -i
dpkg-buildpackage -rfakeroot -uc -b
sudo debi

I may miss something, since it there was a lot of trials-and-errors

I have an 0202 that's at 44.1Khz.

I satisfied various dependencies (devscripts, quilt, debconf-utils) and this completed.  I rebooted, but, in alsamixer I still see only the extension unit toggle, and no way to set it to "0" or "100%" as described in [https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=emu&show_comments=1](https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=emu&show_comments=1)

I tried enabling the extension unit, but it was still fixed at 44.1 KHz using hw:.

I don't know how the value enumerations work in alsa either so I can't help get them to display, but I can report that this sequence of commands at least succeeded.

---

### Post by v.stiff on 2009-06-04
> **klotz said:**
> I have an 0202 that's at 44.1Khz.

I satisfied various dependencies (devscripts, quilt, debconf-utils) and this completed.  I rebooted, but, in alsamixer I still see only the extension unit toggle, and no way to set it to "0" or "100%" as described in [https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=emu&show_comments=1](https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=emu&show_comments=1)

I tried enabling the extension unit, but it was still fixed at 44.1 KHz using hw:.

I don't know how the value enumerations work in alsa either so I can't help get them to display, but I can report that this sequence of commands at least succeeded.
I did some research (because after kernel upgrade installing new deb's didn't work anymore :)) and found interesting thing:

```
$ apt-file find /lib/modules/2.6.28-11-generic/kernel/sound/usb/snd-usb-audio.ko 
linux-image-2.6.28-11-generic: /lib/modules/2.6.28-11-generic/kernel/sound/usb/snd-usb-audio.ko
```

so, it means that installing these deb's doesn't install kernel module, and I actually got it working by running sudo make install before, but I haven't found how to load it into running kernel (modprobe didn't help) then installed debi and did reboot, and it worked after that :)

If you see only Extension units - it means it doesn't work, see attached screenshot

try doing this (after creating deb, as described above):

./configure --with-cards=usb-audio,hda-intel
make
sudo make install-headers install-modules
sudo depmod -F /boot/System.map-`uname -r`

---

### Post by klotz on 2009-06-04
That worked; thank you!  I can now set the slider to 100% and get 48KHz sampling. This is a major breakthrough for the 0202.

---

### Post by klotz on 2009-06-05
It looks like the range 0-1 comes from the USB device directly:

```
parse_audio_extension_unit -> build_audio_procunit -> get_min_max -> get_ctl_value -> snd_usb_ctl_msg

```
However, build_audio_procunit has a special case in it for 
 ```
type == USB_PROC_UPDOWN && cval->control == USB_PROC_UPDOWN_MODE_SEL
```
which hard-codes the min/max values instead of querying get_min_max.

So it might be that adding another case to build_audio_procunitfor 
```
 if (type == USB_XU_CLOCK_RATE && cval->control == USB_XU_CLOCK_RATE_SELECTOR) {
  cval->min = 1;
  cval->max = 5;
  cval->res = 1;
  cval->initialized = 1;
} ...
```

This is totally hypothetical as I don't know much about alsa; I just tracked down where the 0-1 range came from to the USB bus code for snd_usb_ctl_msg in usbaudio.c.  (Which, by the way, is the file where normal sampling rate setting is done so eventually possibly a quirk there is a better solution, but anything that works is great for now.)

---

### Post by v.stiff on 2009-06-05
> **klotz said:**
> So it might be that adding another case to build_audio_procunitfor 
```
 if (type == USB_XU_CLOCK_RATE && cval->control == USB_XU_CLOCK_RATE_SELECTOR) {
  cval->min = 1;
  cval->max = 5;
  cval->res = 1;
  cval->initialized = 1;
} ...
```
looks reasonable! But as far as I understand cval->min should be 0. You should make this as a patch too.

---

### Post by danmbox on 2009-06-07
Are there any datasheets available? The usbmixer patch ([http://pastie.org/483899](http://pastie.org/483899)) must be based on something...

I have an E-MU 0202, and currently have to do my recording on windows. Even if the sample rate issue is resolved (ideally for 96 kHz), 24 bit resolution is still unsupported.

---

### Post by v.stiff on 2009-06-07
> **danmbox said:**
> Are there any datasheets available? The usbmixer patch ([http://pastie.org/483899](http://pastie.org/483899)) must be based on something...
as far as I know the only source of information is opensource'd mac os x drivers for emu.

> I have an E-MU 0202, and currently have to do my recording on windows. Even if the sample rate issue is resolved (ideally for 96 kHz), 24 bit resolution is still unsupported.
what do you mean by that? messages from jackd initialization:

ALSA: final selected sample format for playback: 24bit little-endian

you can try a simple test: record the sample with 100db dynamic range played by card itself. the quiet tone would be lost in 16-bit. you can ensure first, that it's played by raising recording level - so that loud signal would be clipped, but quiet would definitely get into working range.

---

### Post by CannibalZerg on 2009-06-08
> 
So it might be that adding another case to build_audio_procunitfor 
```
 if (type == USB_XU_CLOCK_RATE && cval->control == USB_XU_CLOCK_RATE_SELECTOR) {
  cval->min = 1;
  cval->max = 5;
  cval->res = 1;
  cval->initialized = 1;
} ...
```


You're right, but cval->min should be 0 and there is no need to check cval->control . 

[SIZE="3"][COLOR="Gray"]_alsa-driver patch:_[/COLOR][/SIZE](deprecated)

New patch is available at [http://www.pastie.org/504385](http://www.pastie.org/504385)
Also added External "Source clock" selector. By default it's internal (i.e. External OFF). I'm plannig to add the rest of functionality ("Soft limit" switch and "SPDIF format" switch).


To apply patch, follow these steps:
1.Download and untar alsa-driver source.
2```

$ cd alsa-driver-1.0.xx
$ wget http://pastie.org/504385.txt
$ patch -p0 < 504385.txt
$ ./configure 
$ make 
$ sudo make install

```
3.Reboot (or reload snd-usb-audio)

---

### Post by klotz on 2009-06-08
> **danmbox said:**
> Are there any datasheets available? The usbmixer patch ([http://pastie.org/483899](http://pastie.org/483899)) must be based on something...

I have an E-MU 0202, and currently have to do my recording on windows. Even if the sample rate issue is resolved (ideally for 96 kHz), 24 bit resolution is still unsupported.

This may be an issue with your recording software or your alsa configuration.  The only native 24-bit format the 0202 supports is SND_PCM_FORMAT_S24_3LE, three bytes little-endian.

---

### Post by klotz on 2009-06-08
> **CannibalZerg said:**
> You're right, but cval->min should be 0 and there is no need to check cval->control . New patch is available at [http://www.pastie.org/504385](http://www.pastie.org/504385)
Also added External "Source clock" selector. By default it's internal (i.e. External OFF). I'm plannig to add the rest of functionality ("Soft limit" switch and "SPDIF format" switch).
...


Thanks for moving this forward!

In re the code comment: 
```
/*E-Mu 0404USB samplerate control quirk*/
```

The samplerate quirk is for the 0202 and 0404 both.

However, the 0202 doesn't have SP/DIF and doesn't have (at least that I can see) a wordclock input.

I don't know about the soft limit.

Leigh.

---

### Post by CannibalZerg on 2009-06-08
> **klotz said:**
> T

However, the 0202 doesn't have SP/DIF and doesn't have (at least that I can see) a wordclock input.

I don't know about the soft limit.

I have only 0404 USB, so I'm not sure what kind of controls and endpoints presents in 0202USB, please post the results of the command
```
$lsusb -vd 0x41E:0x3F02
```
It will help me with reversing of OS/X driver.

---

### Post by v.stiff on 2009-06-08
> **CannibalZerg said:**
> You're right, but cval->min should be 0 and there is no need to check cval->control . New patch is available at [http://www.pastie.org/504385](http://www.pastie.org/504385)
I think it's better to do check cval->control, just to (possibly) simplify maintenance in future. And for the same reason, I'd make call to [FONT="Courier New"]get_min_max(cval, valinfo->min_value);[/FONT] only after all quirks, not with quirk. Patch works, sampling rate changes now from 44.1 to 192khz (direct monitoring lights turning off). Thanks for your work!

---

### Post by CannibalZerg on 2009-06-08
> **v.stiff said:**
> I think it's better to do check cval->control, just to (possibly) simplify maintenance in future. And for the same reason, I'd make call to [FONT="Courier New"]get_min_max(cval, valinfo->min_value);[/FONT] only after all quirks, not with quirk. Patch works, sampling rate changes now from 44.1 to 192khz (direct monitoring lights turning off). Thanks for your work!

While clock_rate_xu_info[] has only one item, additional check of cval->control is unnecessary. I don't think, that samplerate endpoint can control any other functions than sampling rate. I think it's better to do additional check of card UID.
Look at get_min_max(...) code, first three lines will overvrite all results of any previous quirk.

---

### Post by v.stiff on 2009-06-08
> **CannibalZerg said:**
> While clock_rate_xu_info[] has only one item, additional check of cval->control is unnecessary. I don't think, that samplerate endpoint can control any other functions than sampling rate. I think it's better to do additional check of card UID.
Look at get_min_max(...) code, first three lines will overvrite all results of any previous quirk.
I mean: [FONT="Courier New"]if (quirk1) {...} else { if (quirk2) {...} else {get_min_max()}}[/FONT]. As far as I understand your patch it does [FONT="Courier New"]if (quirk1) {...} else {get_min_max}[/FONT] and after that [FONT="Courier New"]if (quirk2) {...}[/FONT] Check by card UID is not a good idea as for me, because there is a Tracker Pre, and maybe more usb cards to come, and it is somewhat too 'coupled'.

---

### Post by klotz on 2009-06-08
> **CannibalZerg said:**
> I have only 0404 USB, so I'm not sure what kind of controls and endpoints presents in 0202USB, please post the results of the command
```
$lsusb -vd 0x41E:0x3F02
```
It will help me with reversing of OS/X driver.

Thank you!
[http://pastie.org/504844](http://pastie.org/504844)

Leigh.

---

### Post by CannibalZerg on 2009-06-08
**klotz**, thanks, it seems that EMU0202 USB has only samplerate control endpoint.
**v.stiff**, you're right, I've missed correct if(){}else{if(){}else} statements. Thanks!

---

### Post by danmbox on 2009-06-09
> **klotz said:**
> This may be an issue with your recording software or your alsa configuration.  The only native 24-bit format the 0202 supports is SND_PCM_FORMAT_S24_3LE, three bytes little-endian.

I thought 24-bit was not supported by ALSA, but maybe I was wrong. Unfortunately I will be away from my card for two weeks (traveling) so I can't check.

I guess "arecord -f S24_LE" will activate 24-bit capture. Is it safe to assume that if arecord records the audio, it will be a "true" 24-bit signal (as opposed to a software scaled one)?

> **v.stiff said:**
> you can try a simple test: record the sample with 100db dynamic range played by card itself. the quiet tone would be lost in 16-bit. you can ensure first, that it's played by raising recording level - so that loud signal would be clipped, but quiet would definitely get into working range.

How do I do this? Loop a cable from the card's output to its microphone input? But what volume setting to use in alsamixer (for output) and, more importantly, for the 0202's pre-amplifier gain control (I mean the physical knob on the unit itself)?

---

### Post by klotz on 2009-06-09
> **CannibalZerg said:**
> http://pastie.org/504385.txt

This patch works for the EMU-0202 up to 96KHz (3, 60%) but I'm not able to get 176400 (4, 80%) or 192600 *5, 100%) to work.  The EMU-0202 claims to support those rates if Direct Monitor is off.  I see neither Stereo or Mono monitor light lit, but I still don't get 176400 or 192600 working.

I saw you requested the patch to be checked in in Alsa Bug #4410 and I'd give it a +1 but it might be nice to decide whether this issue is fixable or if the quirk should be 0-3 on the 0202, at least for now.

---

### Post by CannibalZerg on 2009-06-09
> The EMU-0202 claims to support those rates if Direct Monitor is off. I saw you requested the patch to be checked in in Alsa Bug #4410 and I'd give it a +1 but it might be nice to decide whether this issue is fixable or if the quirk should be 0-3 on the 0202, at least for now.
**klotz**, It's strange. OS/X driver doesn't contain any device depended code in samplerate switching routine. 
Emu0404 hardware automaticaly turn "Direct monitoring" off, when selecting 176 or 192.
Tell me, please, does 176.4 and 192.0 values presents in Windows EMU Control Applet? Please, post its screenshot, if it possible.

Here is the descriptors for samplerate control endpoints:
(emu0404) ** UNRECOGNIZED:  0f 24 08 0c 01 e3 01 05 04 33 00 00 01 07 00
(emu0202) ** UNRECOGNIZED:  0f 24 08 0c 01 e3 01 05 02 03 00 00 01 07 00
May be i've missed something, and one of theese bytes contain max_value (like 04 and 02), but without specifications I can't speek with confidence.

---

### Post by bofphile on 2009-06-09
Here is a screenshot of the E-MU 0202 USB control panel on Vista:
[IMG]http://bofphile.free.fr/Images/emu0202.png[/IMG]

---

### Post by CannibalZerg on 2009-06-09
**bofphile**,thanks! Looks good, all 6 values are present. So quirk max_value=5 is correct.

---

### Post by bofphile on 2009-06-09
If you need anything else, just ask. ;)
Thanks a lot for the work you're doing, I was beginning to think my device would never work fully on Ubuntu.

---

### Post by CannibalZerg on 2009-06-09
**bofphile**,**klotz**
I found (for 0404), that with External SPDIF Clock Source windows control applet remove 176 and 192 values from samplerate dropdown listbox. But 0202 haven't such option as SPDIF and "Clock source". Maybe my latest patch with "Clock Source" switch is incorrect.
 So I need additional information:
1.Screenshot of alsamixer with my latest patch applied ([http://www.pastie.org/504385](http://www.pastie.org/504385))
2.In windows turn "Direct monitoring" ON (Stereo or mono), then try to set sampling rate to 176.4. Is it:
2.a -There is no 176.4 value available;
2.b -"Direct monitoring" led goes OFF;
2.c - someting else.

3. Try to remove "Clock Source" functionality from patch:
3.1. Replace existing usbmixer.h with original one (from alsa-driver archive);
3.2. Apply mellowman's patch ([http://pastie.org/483899](http://pastie.org/483899))
3.3. Manually add *min/max val* quirk to *build_audio_procunit()* routine
3.4. Recompile, install.
3.5. Post alsamixer screenshot.

If item 3 is difficult for you, let me know, and I'll post intervening patch. 
Thank you for your cooperation.
P.S. I'll try to find 0202 hardware for debugging

---

### Post by v.stiff on 2009-06-09
> **danmbox said:**
> How do I do this? Loop a cable from the card's output to its microphone input? But what volume setting to use in alsamixer (for output) and, more importantly, for the 0202's pre-amplifier gain control (I mean the physical knob on the unit itself)?
On my card software volume in alsamixer doesn't affect anything, only hardware knobs do. I can't say exact position to set on your device, just loop output to mic input, send two sine tones (audacity might help you), one, for example, 1khz at 0db, and one, 10khz, at -100db, and watch them, for example, in jaaa/japa. Then adjust mic gain/output level to the point where loudest signal is **recorded** at 0db, then watch at the quiet one. In 16bit it would be lost under the noise floor

---

### Post by bofphile on 2009-06-09
1. I applied your latest patch following those steps (after downloading and untaring alsa-driver-1.0.20 in my home directory):
```
sudo apt-get install patch
cd alsa-driver-1.0.20
wget http://pastie.org/504385.txt
patch -p0 < 504385.txt
./configure 
make 
sudo make install

```

Screenshot of alsamixer:
[IMG]http://bofphile.free.fr/Images/alsamixer_0202.png[/IMG]

2. In Windows, with "Direct Monitoring" on (stereo or mono), if I choose 176,4kHz or 192kHz, the LED goes off.

Step 3 is a little difficult for me, so if you could post the modified patch, I would be grateful. Also to apply it, do I have to just redo the steps above ?

---

### Post by klotz on 2009-06-09
**CannibalZerg** I don't have easy access to a Windows box at the moment but if nobody else here can do this I'll try.

Creative says that the 0202 does not do 176.4 or 192 on MacOS, so there's probably no hints in the zaudiodrivermac source.  EMU.com [http://tinyurl.com/2aw7hc](http://tinyurl.com/2aw7hc) says "Macintosh analog operation up to 96kHz only at this time."

So, it may be that limiting the 0202 to 96KHz is appropriate until someone figures out what magic the closed Windows driver uses.

---

### Post by CannibalZerg on 2009-06-10
**bofphile**, alsmixer screenshot is enough for me, there is no need to modifying any patches at this time, thanks.
**klotz**It's a kind of unpleasant surprise :-( I hope that I'll find someone in my city, who can borrow me a 0202USB device for a couple weeks. I have some ideas, but without hardware I can't test it properly.

*Added here.*
**klotz**, it's not so hopeless. I've been found the same remark about sample rate in EMU 0404 USB User Manual too:
> &#8226; Record and Playback support for a multitude of sample rates: 44.1k, 48k, 
88.2k, 96k, 176.4k, 192k. (176.4k &192k available on PC version only)

---

### Post by _SPU_ on 2009-06-10
May be some usb stream analysis tool will be helpful under windows?
In theory we just need to dump a packet sequence when rate changes from E-MU panel. Or I'm wrong?
Anyway I don't have 0202... only 0404.

---

### Post by CannibalZerg on 2009-06-11
**_SPU_**,in such way I've been found control packets for emu0404. But UsbSniff doesn't dump control packets correctly. USBTrace, for example, is a good programm, but it's non-free, and have a limitations in demo version. If someone can capture 0202 usb control packets with USBTrace, while sample rate switching , it will be helpful.

---

### Post by bofphile on 2009-06-11
I'll try to do it later in the day although I never used such a program.

---

### Post by bofphile on 2009-06-11
Okay this is my first try with the program. I started the capture at 44.1kHz then every 10 secs or so I changed the samplerate like this:
44.1->48->88.2->96->176.4->192.

Also I didn't play any music when doing this, don't know if this make any difference.
[http://bofphile.free.fr/Divers/capture_44to192_0202.csv]("http://bofphile.free.fr/Divers/capture_44to192_0202.csv")
[http://bofphile.free.fr/Divers/capture_44to192_0202.txt]("http://bofphile.free.fr/Divers/capture_44to192_0202.txt")
[http://bofphile.free.fr/Divers/capture_44to192_0202.utl]("http://bofphile.free.fr/Divers/capture_44to192_0202.utl")

---

### Post by CannibalZerg on 2009-06-11
**bofphile** 
Thanks, but if you have some free time, Do the next steps, please:
1. Clear the log.
2. Start capture.
3. Change samplerate.
4. Stop capture
5. Save log in **HTML** format. (txt format is good enough, but it doesn't contain timestamps) 
(Do the steps 2-4 as fast as you can. No more additional moves, just switch samplerate at one value and immediately stop the capturing.)

Repeat this procedure fo the next values:
44->48; 48->88; 88->96; 96->176; 176->192; 192->44; 44->192;
P.S.And,yes - no music playing when capturing.

---

### Post by bofphile on 2009-06-11
44.1->48:
[http://bofphile.free.fr/Divers/4448.html]("http://bofphile.free.fr/Divers/4448.html")

Sample rate was changed at sequence #12

48->88:
[http://bofphile.free.fr/Divers/4888.html]("http://bofphile.free.fr/Divers/4888.html")

Sample rate was changed at sequence #16

88->96:
[http://bofphile.free.fr/Divers/8896.html]("http://bofphile.free.fr/Divers/8896.html")

Sample rate was changed at sequence #16

96->176.4:
[http://bofphile.free.fr/Divers/96176.html]("http://bofphile.free.fr/Divers/96176.html")

Sample rate was changed at sequence #12

176.4->192:
[http://bofphile.free.fr/Divers/176192.html]("http://bofphile.free.fr/Divers/176192.html")

Sample rate was changed at sequence #12

192->44:
[http://bofphile.free.fr/Divers/19244.html]("http://bofphile.free.fr/Divers/19244.html")

44->192:
[http://bofphile.free.fr/Divers/44192.html]("http://bofphile.free.fr/Divers/44192.html")

---

### Post by CannibalZerg on 2009-06-11
Yes, that it's!! :-)

> The sample rate was changed at sequence #12
Actually #13-#21, but it doesn't matter. Proceed with other values, please.

**bofphile**, thanks a lot. I need some time to analyse it.

---

### Post by bofphile on 2009-06-11
Sorry I forgot the last two. ;)

---

### Post by CannibalZerg on 2009-06-11
**bofphile** Hm, I'm a little bit confused, the control packets are absolutely identical to emu0404 ones.
Here the simple kernel module, which does nothing, but tries to set samplerate to 176.4:
[http://www.maxishare.net/en/file/16385/emu0202usb-test-tar-gz.html]("http://www.maxishare.net/en/file/16385/emu0202usb-test-tar-gz.html")
Please test it, if it possible. Here the mini-tutorial:

1.Untar source files.
2.Make it ("kernel-source" package must be installed)
```
make -C /lib/modules/`uname -r`/build M=`pwd`
```
3.Set sample rate in alsamixer to 44;
4.Close all media players and mixers (alsamixer, KDE/GTK mixer applet).
5.Unload emu0202 drivers from kernel
```
sudo modprobe -rv snd-usb-audio
```
6.Turn the "Direct monitor" on (stereo or mono);
7.Load test module:
```
sudo insmod emu0202usb.ko
```
8.At this moment "Direct monitor" led should goes off;
9.Unload test module:
```
sudo rmmod emu0202usb.ko
```
10.Post the results of the command:
```
sudo cat /var/log/messages.log | grep Foo_EMU
```
11.Load emu0202 driver back:
```
sudo modprobe snd-usb-audio
```

---

### Post by bofphile on 2009-06-11
I didn't find the package named "kernel-source" (Did you mean "linux-source"?), so I tried without it:
After untaring, I launched the terminal and went into the folder and this is what I got for the make command:
```
make: entrant dans le répertoire « /usr/src/linux-headers-2.6.28-11-generic »
  Building modules, stage 2.
  MODPOST 0 modules
make: quittant le répertoire « /usr/src/linux-headers-2.6.28-11-generic »

```

Can I continue or should I install kernel-source ?

---

### Post by klotz on 2009-06-11
Before this gets too far, can someone else with an 0202 on Linux confirm that 96Khz works but higher sample rates don't?  Am I the only one reporting this?

---

### Post by bofphile on 2009-06-11
Do I have to use a file with a samplerate of 176.4 or 192kHz to do this test ? If so do you have a sample I could use ?

---

### Post by CannibalZerg on 2009-06-12
> **bofphile said:**
> 
```
make: entrant dans le répertoire « /usr/src/linux-headers-2.6.28-11-generic »
  Building modules, stage 2.
  MODPOST 0 modules
make: quittant le répertoire « /usr/src/linux-headers-2.6.28-11-generic »

```
Can I continue or should I install kernel-source ?
Sorry, I'm an Arch-Linux user, and I forgot, that package names may differs in Ubuntu.  
It seems that source code compiled successefully, check is *emu0202usb.ko* file presents in a folder. If so, you can proceed.
> Do I have to use a file with a samplerate of 176.4 or 192kHz to do this test ? If so do you have a sample I could use ?
You can't play any sound samples with this test-driver, it doesn't have such a functionality. It doesn't have any functionality, but sending 3 control packets  to 0202usb device.
  The result of this test-module is: 5 lines with debug information in *message.log*, and, I hope, turning "Direct monitor" led off. That's all, nothing else.

> Before this gets too far, can someone else with an 0202 on Linux confirm that 96Khz works but higher sample rates don't? Am I the only one reporting this?
**klotz**, it's good to see you again, can you test this test-module too?

---

### Post by bofphile on 2009-06-12
The file emu0202usb.ko is not present in the folder.

Also for the sound samples, I meant to try with your previous patch (504385), not this test-driver.

---

### Post by CannibalZerg on 2009-06-12
**bofphile** install linux-headers-2.6.xx-xx package, and try again.
I haven't particular sound samples, usually I'm using resamplers in ~/.asoundrc . AFAIK aplay command has option -r
Something like:
```
aplay -D hw:1,0 -r 192000 some_file.wav
```

P.S. Also install *build-essential* package.

---

### Post by _SPU_ on 2009-06-12
I have slightly offtopic question...
Does anybody have a problem with 0404 and dmix like me?
[https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/375993](https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/375993)

---

### Post by CannibalZerg on 2009-06-12
**_SPU_**, yes, I have the same problem. It's seems, that dmix works at 48k.

---

### Post by bofphile on 2009-06-12
Okay, I did your test and this the result.

- First, at step 4, I had to kill "mixer_applet2" and "pulseaudio" to properly unload the module.

- As you said in step 8, the "Director Monitor" LED went off (I tried with stereo) when I loaded the test module.

- This is the output of "**sudo cat /var/log/messages | grep Foo_EMU**" (I had to delete the .log of messages because it couldn't find the file otherwise):
```
[  897.631419] Foo_EMU_0202:  Starting module....
[  897.631687] Foo_EMU_0202: Get current samplerate: SUCCESS: 0x0
[  897.631934] Foo_EMU_0202: Set samplerate: SUCCESS: 0x4
[  897.632053] Foo_EMU_0202: Get new samplerate: SUCCESS: 0x4
[  926.166062] Foo_EMU_0202:  Unloading module....

```

---

### Post by CannibalZerg on 2009-06-12
**bofphile** good job, thanks a lot. :D
So, it **can** switch to 174 or 192, it's a good news.

I think, I'll find a problematic piece of code in alsa in recent days.

---

### Post by Super*Skunk on 2009-06-12
Hi all I am installing the patch on my openSuSe box box now and would be happy to help in any way I can.

Keep up the good work you crazy penguins!

---

### Post by klotz on 2009-06-12
> **CannibalZerg said:**
> **bofphile** good job, thanks a lot. :D
So, it **can** switch to 174 or 192, it's a good news.

I think, I'll find a problematic piece of code in alsa in recent days.

It's quite likely the problem is elsewhere, perhaps even in the applications I'm using.  I get only noise out when I specify higher than 96KHz in the USB request and tell my alsa client app to use the same rate; however if I lie to the alsa app and tell it to request 96Khz yet leave the device set for 192Khz I get resampled audio.

So in conclusion, I agree with you that if there's a problem, it's probably not in the USB code or the device setup.

---

### Post by CannibalZerg on 2009-06-13
**Super*Skunk** what device do you have, 0404 or 0202?
**klotz** can you switch your system to runlevel 3 (to eliminate possible interference with GTK mixer applet, or any other software)
```
$sudo telinit 3
$sudo /etc/init.d/gdm stop
```
and try to set sample rate higher than 96kHz in alsamixer. Is slider still stuck at 60%?

---

### Post by _SPU_ on 2009-06-13
> **CannibalZerg said:**
> **_SPU_**, yes, I have the same problem. It's seems, that dmix works at 48k.
No no. I set it explicitly to 44.1 (defaults.pcm.dmix.rate 44100). Sound with dmix at 48 is really different (it skips some samples). Problem is somewhere around bit depth.
Here is my test config (asound.conf):
```

defaults.pcm.dmix.rate 44100 #to avoid wrong rate

#True setup (like it must be in the alsa)
 pcm.test {
  type asym
  playback.pcm {
    type plug
    slave.pcm "dmix:USB"
  }
  capture.pcm {
    type plug
    slave.pcm "dsnoop:USB"
  }
}



#Clean setup

pcm.emu {
  type plug
  slave {
    pcm "hw:0"
    rate 44100
  }
}


#Setup with dmix only

pcm.emutest{
 type plug
 slave.pcm "emudmix"
}
 

pcm.emudmix {
  type dmix
  ipc_key 1234
  slave {
    pcm "hw:0,0"
    rate 44100
  }
}

```


pcm.emu gives me a clear sound like it must be, but only one stream allowed.
pcm.emudmix and pcm.test gives me a noisy sound like you can here in this sample: [http://launchpadlibrarian.net/26683352/sound.tar.gz](http://launchpadlibrarian.net/26683352/sound.tar.gz)

---

### Post by klotz on 2009-06-13
> **CannibalZerg said:**
> 
**klotz** can you switch your system to runlevel 3 (to eliminate possible interference with GTK mixer applet, or any other software)
```
$sudo telinit 3
$sudo /etc/init.d/gdm stop
```
and try to set sample rate higher than 96kHz in alsamixer. Is slider still stuck at 60%?
Sorry I missed this; I've been out of touch.
The slider is not stuck at 60%.  It works properly.
However, my capture application gets only white noise when the 0202 is set to rates higher than 96Khz.
If I specify "hw:" and tell my app the sample rate is 192KHz, I get noise.
If I specify "hw:" and set a sample rate of 96Khz in the app, I get resampled data.
So perhaps the problems is in Alsa or my app.

---

### Post by Super*Skunk on 2009-06-14
Hi again, sorry for the slow reply but it is the weekend!  I have an 0404 usb, I have succesfully played back 44/16 and 24/96 samples through plughw:0,0 using hw:0,0 or trying to set sample rates up to heaven seems to cause a crap-out needing a full restart to fix.  btw I am in the UK so I may be out of time with the rest of you.

cheers boys

---

### Post by z0idberg on 2009-06-14
[QUOTE=CannibalZerg]...[/QUOTE]
Hi, I'm the one who posted ALSA bug #4410, I didn't notice these patches in the comments until today. I'll probably try them tomorrow... If I understand correctly, this should work with ALSA 1.0.20. What would be the best way to apply them on Arch Linux... I'm guessing abs?

Anyway, big thanks to you and mellowman and everyone else working to get the E-MU cards working better on Linux!

---

### Post by CannibalZerg on 2009-06-15
> **klotz said:**
> 
The slider is not stuck at 60%.  It works properly.
However, my capture application gets only white noise when the 0202 is set to rates higher than 96Khz.

If so, can you modify your post at ALSA bug #4410? Please add remark, that playback works for all sample rates, but 24/176 and 24/192 doesn't work for capturing. Unfortunately I can't check capturing right now, but I'll do it ASAP.

**_SPU_**, I found the reason of 24 bit dmix dirty sound. But problematic piece of code is written in assembler. I'll try to make a patch, but I'm not familiar with asm for Linux.

**Super*Skunk**, sorry, English isn't my native language. You can't switch sample rate to value higher than 96k. Am I right? Btw, my time zone is GMT+02.

**z0idberg**, yes, it works with alsa 1.0.20 on Arch Linux ;).

---

### Post by klotz on 2009-06-15
> **CannibalZerg said:**
> If so, can you modify your post at ALSA bug #4410? Please add remark, that playback works for all sample rates, but 24/176 and 24/192 doesn't work for capturing. Unfortunately I can't check capturing right now, but I'll do it ASAP.
Done. Thanks for all your work and sorry for the confusion.  I have not tested playback, only capture.

---

### Post by z0idberg on 2009-06-15
I just wanted to add that the patch worked well for me in Arch Linux, as expected, but even when playing at the "right" rate, I get some background noise (which also appeared before, when I used .asoundrc to force playback at 44100). I have no idea what might cause this... but at least I suppose we're moving in the right direction :).

---

### Post by _SPU_ on 2009-06-15
> **CannibalZerg said:**
> **_SPU_**, I found the reason of 24 bit dmix dirty sound. But problematic piece of code is written in assembler. I'll try to make a patch, but I'm not familiar with asm for Linux.
Thx. Good news :) Btw, I use x64 distrib.
May be I can help somehow? I'm also not familiar with "asm for Linux", but I don't think that there is a big difference :)

---

### Post by CannibalZerg on 2009-06-15
[SIZE="5"][COLOR="Magenta"]_Latest DMix patch:_[/COLOR][/SIZE]
Dmix sound distortion fix:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4577]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4577")
Patch also available at:
[http://www.pastie.org/512796]("http://www.pastie.org/512796")

The list of required packages necessary to apply the patch:
**build-essential,patch,wget**

mini How-to:
1. Download **alsa-lib** source code archive;
2. Untar;
3. Enter the following commands:
```

$cd alsa-lib-1.0.xx
$wget http://www.pastie.org/512796.txt
$patch -p0 < 512796.txt
$./configure
$make
$sudo make install

```
4. No reboot is needed.

**SPU**, please copy *bugtrack* link into your bugreport [https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/375993](https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/375993). 
**z0idberg**, this patch should solve your problem too.

[SIZE="1"][I]P.S. It seems, that softvolume has similar bug with distortion, when volume slider is not at max value. 
Here the routing path of sound streams in .asoundrc:
1) wav--(16/44)-->[plug 24bit ]--(24/44)-->[softvol 100%]--(24/44)-->[dmix]--(24/any)-->[hw]: **no distortion**
2) wav--(16/44)-->[plug 24bit ]--[COLOR="Red"](24/44)-->[softvol  90%]--(24/44)[/COLOR]-->[dmix]--(24/any)-->[hw]: **distortion**
3) wav--[COLOR="Green"](16/44)-->[softvol 90%]--(16/44)[/COLOR]-->[plug 24bit  ]--(24/44)-->[dmix]--(24/any)-->[hw]: **no distortion**[/I][/SIZE]

---

### Post by Super*Skunk on 2009-06-15
> **CannibalZerg said:**
> 
**Super*Skunk**, sorry, English isn't my native language. You can't switch sample rate to value higher than 96k. Am I right? Btw, my time zone is GMT+02.

not exactly, I can record at 192khz through JACK/ardour but the sound is extremley distorted and jackd stops when I try to play it back.

I take it that for 192khz I should set clock rate to 100?
also it is worth noting that I have only installed alsa-driver 1.0.20 with patch.  I have left other alsa comonents at the stock SuSe versions (1.0.18 for most)

I suffer no sound quality problems with 44khz.  at 96k playback is fine, but recording suffers from some dropout and clicking. maybe because I have a usb webcam attached?

---

### Post by _SPU_ on 2009-06-15
**CannibalZerg,** thanks! It works :)
I don't use softvolume, but in future it will be added by default for 0202/0404. Too many bugs with 24bit format I think... :(

P.S. Is there any standard way to switch internal dmix rate together with the device rate?

---

### Post by CannibalZerg on 2009-06-16
**Super*Skunk**, thanks for report. Please check playback at 24/192 with *aplay*. If you don't have 192kHz wav, you can use resampler. Put this text into *~/.asoundrc*
```
pcm.emu {
  type plug
  slave {
    pcm "hw:0,0" #put corretct device addr here
    format S24_3LE
    rate 192000
  }
}
```
and then run:
```
$aplay -D emu some.wav
```

**_SPU_**
> Is there any standard way to switch internal dmix rate together with the device rate?
It's not, AFAIK.

---

### Post by z0idberg on 2009-06-16
I just wanted to add that the second patch did, indeed, seem to solve my second problem. Now, I don't want to celebrate too early, but things seem to work very well and it's nice to have working sound playback under Linux! Thank you and keep up the good work!

A semi-related question: if I'm not mistaken, when I play a audio CD with Sound Juicer in Gnome I still have to set the E-MU to 48000 Hz to get nice sound. Why/where along the way does the sound get upsampled from 44.1 KHz to 48?

---

### Post by _SPU_ on 2009-06-16
**z0idberg,** just add this line to .asoundrc:
```
defaults.pcm.dmix.rate 44100
```
or you can define your own setup with dmix plugin without the above global override.

---

### Post by CannibalZerg on 2009-06-16
Well, guys, here is another one patch. It's for **softvol** plugin, now.
As I've mentioned above, there was a problem with 24bit sound stream.

[SIZE="5"][COLOR="Magenta"]_Latest SoftVol patch:_[/COLOR][/SIZE]
Patch link:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4578]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4578")
Mirror:
[http://www.pastie.org/514225]("http://www.pastie.org/514225")

Traditional mini how-to:
The list of required packages necessary to apply the patch:
**build-essential,patch,wget**

1. Download alsa-lib source code archive;
2. Untar;
3. Enter the following commands:
```
$cd alsa-lib-1.0.xx
$wget http://www.pastie.org/514225.txt
$patch -p0 < 514225.txt
$./configure
$make
$sudo make install
```

If you have previously applied dmix patch, just skip steps 1 and 2.

---

### Post by _SPU_ on 2009-06-16
I'll add this patch to my bugreport.

---

### Post by Super*Skunk on 2009-06-17
added the lines you suggested to ~/.asoundrc and tried to play something back, sounded crap as expected, then I pushed the clock rate selector up to 100 tried again and it sounds perfect.  I'll just grab that new patch and then do the same again

---

### Post by Super*Skunk on 2009-06-17
yep, same result....

 I don't even know what dmix is tbh lol.

---

### Post by z0idberg on 2009-06-17
> **_SPU_ said:**
> **z0idberg,** just add this line to .asoundrc:
```
defaults.pcm.dmix.rate 44100
```
or you can define your own setup with dmix plugin without the above global override.

Oh, it was that simple. Thank you! 

Anyway, this makes for another question; whether I set the soundcard to 44.1 or 48 KHz, when I play back a sound file with different samplerate it's inevitably going to be resampled, right? So does this always happen in ALSA (in that case I guess it would make sense to start playing around with the different quality settings in libsamplerate) or is there such a thing as hardware resampling, and does it work?

---

### Post by _SPU_ on 2009-06-17
There is no hardware resampling, so every sound will be resampled to the rate you set for dmix.
But if you change your .asoundrc, alsa must reconfigure itself on the fly, so it's not a big problem to change the rate manually, when you need this.

---

### Post by Super*Skunk on 2009-06-23
:roll:  *twiddles thumbs* *thinks of new command*
stomach < /home/chris/kitchen/fridge/beer.can > /home/chris/toilet/toilet.can

---

### Post by klotz on 2009-06-25
@CannibalZerg I want to try testing again but I cannot get alsa-base to compile due to 

```
make[2]: *** No rule to make target `/home/klotz/alsa-driver-1.0.18.dfsg/alsa-kernel/pci/maestro3.c', needed by `maestro3.c'.  Stop.

```
I see there is a fix for this in the CVS but it looks like I won't be able to get it today.

---

### Post by CannibalZerg on 2009-06-25
**klotz** try to compile snd-usb-audio module only
```
$./configure --with-cards=usb-audio
$make

```

---

### Post by v.stiff on 2009-06-25
> **klotz said:**
> ```
make[2]: *** No rule to make target `/home/klotz/alsa-driver-1.0.18.dfsg/alsa-kernel/pci/maestro3.c', needed by `maestro3.c'.  Stop.

```
I see there is a fix for this in the CVS but it looks like I won't be able to get it today.
I encountered that thing during my course of initial module compilation :)

If you have debian patches (you do have them if you fetched source via [FONT="Courier New"]apt-get source[/FONT]) then you can just apply patch named remove_maestro3.patch from debian/patches/

---

### Post by klotz on 2009-06-25
> **v.stiff said:**
> I encountered that thing during my course of initial module compilation :)

If you have debian patches (you do have them if you fetched source via [FONT="Courier New"]apt-get source[/FONT]) then you can just apply patch named remove_maestro3.patch from debian/patches/

Thanks @v.stiff, that worked.  I had thought the Debian patches were applied by default.

I reapplied the basic emu patch, the dmix patch, and the softvol patch, make install on both alsa-driver and alsa-lib, reboot, and alsamixer fails to find the device.  I get this message when I power on the EMU-0202:

```
Jun 25 10:13:25 pinstripe pulseaudio[4554]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
```

I will re-fetch the alsa-lib and install a pristine copy and see if that fixes the recognition problem.

EDIT: I reapplied patches and am not having the "fallback" problem.  I don't see any new controls in alsamixer, other than sample rate.

The EMU-0202 moved to card 0, presuambly because my on-board sound device got disabled somehow in the new alsa.

---

### Post by v.stiff on 2009-06-25
> **klotz said:**
> Thanks @v.stiff, that worked.  I had thought the Debian patches were applied by default.
As far as I understand patches applied on a copy of sources. I have no other explanation of how remove_maestro3 patch rolled back :)

> I will re-fetch the alsa-lib and install a pristine copy and see if that fixes the recognition problem.
I had recognition problem only when I forgot some switches, especially one that **CannibalZerg** suggested

---

### Post by v.stiff on 2009-06-25
> **klotz said:**
> 
EDIT: I reapplied patches and am not having the "fallback" problem.  I don't see any new controls in alsamixer, other than sample rate.

The EMU-0202 moved to card 0, presuambly because my on-board sound device got disabled somehow in the new alsa.
Paste here commands you type to fetch/patch/compile the driver. It's weird that you had it working previously, and now it disappeared

---

### Post by Yako on 2009-07-05
> **CannibalZerg said:**
> You're right, but cval->min should be 0 and there is no need to check cval->control . New patch is available at [http://www.pastie.org/504385](http://www.pastie.org/504385)
Also added External "Source clock" selector. By default it's internal (i.e. External OFF). I'm plannig to add the rest of functionality ("Soft limit" switch and "SPDIF format" switch).


Great, thanks.
Is there a way to make the driver set the appropriate sample rate according to the audio stream it is fed?

---

### Post by uhappo on 2009-07-06
So, what is the right way to get 0404 USB working?

There are so many patches and posts that keeping up with the progress is a bit hard.

Could someone update the first post or something, so that every update is easy to download/follow?

---

### Post by Josko on 2009-07-06
Didn't read this for a while so I'm quite out now.
But CannibalZerg if you need some E-MU 0202 USB test I'll do it. I own this one. But tell me which patches should I use.

---

### Post by CannibalZerg on 2009-07-07
**Josko**, **uhappo**
[SIZE=4][COLOR=Magenta]_Here's the latest patches:_[/COLOR][/SIZE]

- [[COLOR=Gray]_alsa-driver_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=7420874&postcount=79")(deprecated)
- [[COLOR=Blue]_Dmix [SIZE=1](for v.1.0.20 and earlier)[/SIZE]_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=7461306&postcount=129") 
- [[COLOR=Blue]_Softvol [SIZE=1](for v.1.0.22 and earlier)[/SIZE]_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=7468405&postcount=135")

---

### Post by jsevi83 on 2009-07-11
What about the E-MU Tracker Pre USB? Nobody else has it? It's very similar to E-MU 0202 USB. I applied the patches and I can set the clock rate in alsamixer, so recording and playback work perfect (except for recording at values higher than 96kHz = 176,4kHz and 192kHz sound with distortion). Thank you!!!

---

### Post by kaworufw on 2009-08-08
> **CannibalZerg said:**
> **Josko**, **uhappo**
[SIZE="4"][COLOR="Magenta"]_Here's the latest patches:_[/COLOR][/SIZE]

- [[COLOR="Blue"]_alsa-driver_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=7420874&postcount=79")
- [[COLOR="Blue"]_Dmix_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=7461306&postcount=129")
- [[COLOR="Blue"]_Softvol_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=7468405&postcount=135")

Thanks CannibalZerg and all the guys here.  I have not visited this thread for long and the patch is really a breakthrough on the process!  I have just applied the patch and the clock rate selector works sweeeetly.  Thanks :)

---

### Post by _SPU_ on 2009-08-31
ALSA 1.0.21 released!
Patches for dmix and softvol are included in this release, but we need a new patch for alsa-driver for frequency selector :(

---

### Post by klotz on 2009-08-31
> **_SPU_ said:**
> ALSA 1.0.21 released!
Patches for dmix and softvol are included in this release, but we need a new patch for alsa-driver for frequency selector :(

What's the issue for the frequency selector patch?

---

### Post by nrwilk on 2009-08-31
Heya, everyone.

Is anyone else here using an emu 0404 USB with Kubuntu Jaunty?  Does anyone have any idea how to enable sound playback for non-KDE4 apps?

The emu works flawlessly with everything that ships with KDE 4, but not things that I actually want to use, such as Firefox (flash), Renoise, VLC, Audacity, Amarok 1.4.8, etc...

Does anyone know if there is a way to enable sound with these apps?

Thanks!

---

### Post by Macdelaney on 2009-09-01
Hey guys,
I'm clueless regarding computer audio, but I have a few hours to buy a soundcard and for what I've read the 0202 is fully functional under linux, can any of you please confirm this for me so I can take the plunge without fear?

---

### Post by CannibalZerg on 2009-09-01
> **_SPU_ said:**
> ALSA 1.0.21 released!
Patches for dmix and softvol are included in this release, but we need a new patch for alsa-driver for frequency selector :(
**Current sample-rate patch works fine for alsa-driver v.1.0.21.**

**Macdelaney**, E-mu0202/0404USB is almost full functional. Comparing with Win-driver, main differencies are: 
1)Manual sample-rate selector(alsa-driver patch should be applied first);
2)Record at 176kHz and 192kHz produce nothing, but "white noise" (MacOS-driver has similar limitation);

---

### Post by v.stiff on 2009-09-01
> **_SPU_ said:**
> ALSA 1.0.21 released!
Patches for dmix and softvol are included in this release, but we need a new patch for alsa-driver for frequency selector :(
Is there a place where this patches are discussed? What is the reason to not include it?

---

### Post by Macdelaney on 2009-09-01
> **CannibalZerg said:**
> The "old" patch should work, I'll check it and update links, if necessary.

**Macdelaney**, E-mu0202/0404USB is almost full functional. Comparing with Win-driver, main differencies are: 
1)Manual sample-rate selector(alsa-driver patch should be applied first);
2)Record at 176kHz and 192kHz produce nothing, but "white noise" (MacOS-driver has similar limitation);

Thanks for your reply, but please clarify this for me. 
1) After the alsa-driver patch it should work fine, right?
2) That's only when recording and doesn't happen with playback?

I'm sorry about the off, but I have 2 hours left and can't afford to make a mistake. Thanks for your help

---

### Post by CannibalZerg on 2009-09-01
**Macdelaney**, after applying patch you can playback any sound content: 44, 48, 88, 96, 174, 192kHz. But you should set corresponding sample-rate manually in alsamixer (or KDE KMix), in other case, you've got sound distortion.

---

### Post by Macdelaney on 2009-09-01
That's great, since I just ordered it and was afraid I misunderstood you and couldn't play 192khz!
Thanks for your helpful replies and I wont keep dragging this great thread off topic

---

### Post by Dimak_XXZZ on 2009-09-11
Hello, I've bought E-MU 0202 soundcard and now all i need works (with CannibalZerg's patch for alsa-driver). Can i help with something ?
Seems capture at 192000 and 176400 doesn't work, are there any progress on it ?

---

### Post by kashuapo on 2009-10-25
Has anyone else had a problem setting up jackd (with qjackctl) to capture at 96kHz with the 0404?  Capture at 48kHz works fine, but at 96kHz there is no input whatsoever (not even white noise, as is the case at 192kHz).  The log from qjackctl looks similar at 48kHz and 96kHz with no error messages.

I am running alsa 1.0.21 with CannibalZerg's patch, and can successfully record/play up to 96kHz with arecord/aplay.

---

### Post by bofphile on 2009-11-10
Is there a way to change the default samplerate when using pulseaudio under Karmic ?
It's a little annoying to have to change the default sound output to alsa everytime I want to use a different sample rate than 44.1kHz. Pulseaudio remains useful the rest of the time, for example to change the default soundcard.

---

### Post by diegooo on 2009-11-16
I don't have global volume working with both ubuntu mixer and alsamixer too. I finally can set clock rate from alsamixer and I hear perfect music: to have 44.1 i need to select clock rate 0, is this normal ?
I suppose for 48 it will be 20 and so on. I presume this is normal. Just like to know. Can someone help here ?

In any case I will never thx enough for this great job. It's sweat to have 0404 working.

---

### Post by v.stiff on 2009-11-20
> **diegooo said:**
> I don't have global volume working with both ubuntu mixer and alsamixer too.
you can use dmix/softvol in alsa or pulseaudio if you need it. Soundcard itself have no internal digital volume control.

> I finally can set clock rate from alsamixer and I hear perfect music: to have 44.1 i need to select clock rate 0, is this normal ?
I suppose for 48 it will be 20 and so on. I presume this is normal. Just like to know. Can someone help here ?
Yes, you are right.

> In any case I will never thx enough for this great job. It's sweat to have 0404 working.
And the worst thing is that you have to do it every time you  upgrade your kernel. Can someone from ubuntu alsa/kernel community 
tell us why this patch isn't included in repository ?

---

### Post by Josko on 2009-11-26
Anybody knows when this patch is making it's way officialy to ALSA sources? Just to know when should I expect it in distributions.

---

### Post by titopoquito on 2009-12-05
> **CannibalZerg said:**
> Here's the latest patches:

- [[COLOR="Blue"]_Softvol [SIZE="1"](for v.1.0.20 and earlier)[/SIZE]_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=7468405&postcount=135")

Hi all,

from what CannibalZerg and _SPU_ wrote, the softvol patch should be included in alsa-lib 1.0.21 and later. I found parts of the dmix patch, but could not find any of the softvol patch. I am not a programmer, so forgive me if I have overseen it, but are you sure that the softvol patch IS actually in there?

Big kudos to all who contributed here, I am desperately awaiting my 0202 USB to be shipped the next days and appreciate your work on these boxes very much :)

---

### Post by jitup on 2009-12-06
hello,
I was just curios about what verison of alsa is included in the ubuntu studio 9.10 64 bit distro? should the Emu o4o4 usb work out of the box with it?

---

### Post by egor_sid on 2009-12-08
Hello everyone in this awesome thread.  I must ask for you assistance.  I am a relatively new user of linux and a newbie when it comes to applying patches and building from source, I've done it, but it's still quite unclear as a whole.  I just spent a few hours reading through all the posts in this thread trying to get alsa to let me set the sample rate for my 0404.  I have had little success.  I'm not on ubuntu but I'm running sidux which is debian sid, basically.  I downloaded and applied all three patches, the drive patch and the library patch, and i seem to have done so successfully, but alas after reboot alsamixer gives me the attached screen.  CannibalZerg and others have provided some detailed instructions to people, i would be extremely grateful if you guys could help me out.
Some specific questions are: do I need to unload any modules before make install? does it matter if I make install as root or sudo? do I need to get the source from apt-get or is the alsa website good enough?


THANKS!

---

### Post by CannibalZerg on 2009-12-08
> **titopoquito** I found parts of the dmix patch, but could not find any of the softvol patch.
Hmm, you're right, how could I miss this issue...
> **jitup**I was just curios about what verison of alsa is included in the ubuntu studio 9.10 64 bit distro? should the Emu o4o4 usb work out of the box with it?
Run the command:
```
cat /proc/asound/version
```
There is still no "out of the box" functionality, you should apply patches.

**egor_sid** I'm an Arch-Linux user, for example, it doesn't matter which distro you have.
It seems, that your alsa-driver isn't patched yet ("Clock rate" selector should appear in alsamixer). 
Try to patch alsa-driver again (previously remove driver sources and untar them again, to ensure that you have unpatched sources before applaying the patch).
You don't need to load/unload any modules before patching alsa-driver kernel module. (module should be reloaded after applying the patch, but I recommend you just reboot the OS)
You can use any sources: from repo, or from Alsa website(ensure, that you've got the correct version from alsa website, previous versions can be found at [ftp://ftp.alsa-project.org/pub](ftp://ftp.alsa-project.org/pub)) 
> does it matter if I make install as root or sudo 
It doesn't matter. But dont run "make" as root - it's not good practice to compile something using root account, due to security issues.
> CannibalZerg and others have provided some detailed instructions to people 
IMHO Step-by-step instruction is detailed enough.But you're rigth, I forgot about pre-requiered packages.
Before applying patches, you should install these developer's packages: **build-essential**,**linux-headers**,**patch**,**wget**

---

### Post by titopoquito on 2009-12-08
> **CannibalZerg said:**
> Hmm, you're right, how can I miss this issue...


Hi CannibalZerg, thanks for looking at this and for posting the bug report, I appreciate your work on this!

Still struggling with my new 0202 USB which arrived today ... ;)

---

### Post by Macdelaney on 2009-12-08
> **titopoquito said:**
> Hi CannibalZerg, thanks for looking at this and for posting the bug report, I appreciate your work on this!

Still struggling with my new 0202 USB which arrived today ... ;)

All I had to do to get my 0202 working was patch the alsa-driver, what problem are you having?

btw I'm also an ArchLinux user, but I think the version included in ubuntu is new enough to not require the other stuff.

---

### Post by titopoquito on 2009-12-09
> **Macdelaney said:**
> All I had to do to get my 0202 working was patch the alsa-driver, what problem are you having?

btw I'm also an ArchLinux user, but I think the version included in ubuntu is new enough to not require the other stuff.

I had to install newer alsa-lib and alsa-driver. The biggest problem I am having or had was to make alsa use it correctly. It's sort of try-and-error for now, but it looks like I got it working. Let's hope it survives reboot. 
aplay ended with an error "aplay: set_params:979: sample format not available" and other programs (xmms, audacious, mplayer etc.) refused to play a sound - although I already knew that the driver was actually working, because audacity could both record and play sounds.
mplayer for example now works, but only if I call it with the options "-ao alsa -af resample=44100:0:0", else sound is distorted. I don't know why - clock rate is set to 0 which should mean 44.1 kHz and should only affect capture I think. :confused:

---

### Post by egor_sid on 2009-12-09
SUCCESS!!
Thank you CannibalZerg!  I'm getting beautiful 48000 Hz sound out of my EMU.  I followed the steps, it's strange because I think I did the same thing last time, but maybe I screwed up somewhere, or maybe becuase it was 3 am and my computer was telling me to go to sleep. hah.

This is absolutely awesome.

---

### Post by CannibalZerg on 2009-12-15
[SIZE="4"][COLOR="Magenta"]_Latest alsa-driver patch: (for v.1.0.22.0 and earlier)_[/COLOR][/SIZE]
Since v.1.0.22.1 you don't need to apply this patch
(run *cat /proc/asound/version* to get version info)

New version of alsa-driver patch is available:
[[COLOR="Navy"]http://www.pastie.org/743114[/COLOR]]("http://www.pastie.org/743114")

(Patch is cumulative! It should be applied to "original" source code, not to already patched one! Just follow "how-to".)

What's new:
[LIST=1]
[*]Added "Soft Limiter" and "SPDIF Out format" controls;
[*]Added automatic sample rate adjustment for both playback and capture. (Capture has higher priority than playback: if recording is active - occasional playback at different sample rate will not spoil captured wav);
[/LIST]

**Mini how-to:**
The list of required packages necessary to apply the patch:
**linux-headers, build-essential, patch, wget**

1. Download alsa-driver source code archive;
2. Untar;
3. Enter the following commands:
```

$ cd alsa-driver-1.0.xx
$ wget http://pastie.org/743114.txt
$ patch -p0 < 743114.txt
$ ./configure 
$ make 
$ sudo make install

```
4. Reboot

P.S. Guys, please don't quote my messages which contain announces of "Latest version". This announces may be edited later to mark them "deprecated", when newer version will be available.

---

### Post by bofphile on 2009-12-15
CannibalZerg, I've tested your patch and it works just fine on Karmic but I have a question: What does "automatic sample rate adjustment for both playback and capture" mean exactly? That depending on the content, the sample rate of the device is changed accordingly ?

And I don't think this would work with the default pulse configuration of Karmic, right ? Because the pulse audio server resamples everything to the sample rate specified in the ~/.pulse/daemon.conf file

---

### Post by CannibalZerg on 2009-12-15
> **bofphile said:**
> What does "automatic sample rate adjustment for both playback and capture" mean exactly? That depending on the content, the sample rate of the device is changed accordingly ?

When you start playing sound content, driver automatically adjust sample rate (just like windows driver does). And yes, it seems useless for pulseaudio users, due to fixed rate in ~/.pulse/daemon.conf.
P.S. I'm not using pulseaudio nor jack nor dmix. I prefer to use my EMU for listening high-quality music and watching video without any resempling. And I a little bit tired to change sample-rate in alsa-mixer, so I decide to modify the patch.

---

### Post by ubuntoyou2 on 2009-12-16
@CannibalZerg : that's a great idea. So if you switch from an audio cd to dvd, for instance, the sample rate will change automatically. Excellent.

I notice you mentioned the pulse audio sample rate setting of 44100 which explains why my audio was stuck at that sample rate and I couldn't change it. Have uninstalled pulseaudio and will apply your latest patch.
Thanks for all the great work. I'll let you know how it works.

---

### Post by ubuntoyou2 on 2009-12-16
After uninstalling pulse i've no audio.  Can the sample rate problem be fixed with pulse? Bad Karmic ;-)

---

### Post by CannibalZerg on 2009-12-18
> Can the sample rate problem be fixed with pulse? 
There is no problem with sample rate after applying patch, it's work just fine. Pulseaudio server runs at fixed rate and resample all sound streams, and alsa-driver correctly switch emu0404usb to this sampling rate.
If you change **default-sample-rate** in ~/.pulse/daemon.conf and restart Pulseaudio daemon, emu0404usb driver *automatically* switch hardware sample rate.

---

### Post by ubuntoyou2 on 2009-12-18
@CannibalZerg Thanks for the reply.  So is it the case that if i'm listening to a dvd, pulseaudio will downsample the audio to 44.1Khz from 48Khz? I understand that emu0404 will still play this at pulseaudio's samplerate.
  However if I change the default sample rate in ~/.pulse/daemon.conf to 48Khz then the sound will be routed to emu 0404 usb at the correct sample rate. But with this new configuation, cd audio will be upsampled to 48Khz. In otherwords, everything will be played at 48Khz. 
Doesn't this defeat the purpose of your new patch which is to use alsa to automatically change samplerates to that of your source material without having to make adjustments to aslamixer? Or am I getting all my facts wrong?
I noticed that some Karmic Kola users have been reporting problems with pulseaudio, the biggest being the difficulty of getting back to alsa. Kbuntu doesn't have this issue as pulseaudio hasn't been integrated into Kbuntu the way it has in Ubuntu.
Thanks to you I did finally have audio from my emu usb soundcard.  But I did notice the sound quality wasn't as good as on windoze and suspect this is due to the downsampling of dvd audio.
One day it'll all be perfect lol

---

### Post by bofphile on 2009-12-20
I found a way to listen to my music and movies at the correct sample rate without changing the configuration file of pulseaudio. When I watch videos, I use SMPlayer with the audio output set to alsa and for the music, I use the defaut configuration of pulseaudio (which is 44.1kHz). This way, with the latest patch, the sample rate is changed automatically.

What would be great, is the possibility to change the sample rate/bit depth on the fly in the gui of pulseaudio/sound preference. I hope this will be addressed in the future version of pulseaudio.

---

### Post by dptkby on 2009-12-21
Is there any chance of getting this included in ALSA? I haven't tried the patch as I don't have access to my regular Linux box at the moment, but if it works (as I'm sure it does), sound playback on Linux using the 0404 is coming together very well! Of course, not having to patch the kernel would be even more convinient :).

Anyway, thank you for your work!

---

### Post by Macdelaney on 2009-12-21
Some of CannibalZerg's work is already in alsa if I'm not mistaken (the dmix patch and some other stuff if I recall correctly), so I'm guessing they are at least aware of this missing bit and for some chose not to include it.

---

### Post by dptkby on 2009-12-21
> **Macdelaney said:**
> Some of CannibalZerg's work is already in alsa if I'm not mistaken (the dmix patch and some other stuff if I recall correctly), so I'm guessing they are at least aware of this missing bit and for some chose not to include it.
Yeah, I meant the samplerate patch. Coming to think of it, I believe the patches included in ALSA were those that applied to alsa-lib, while the samplerate patch is for alsa-driver. I don't know if that has anything to do with it, though.

---

### Post by CannibalZerg on 2009-12-21
> Yeah, I meant the samplerate patch. Coming to think of it, I believe the patches included in ALSA were those that applied to alsa-lib, while the samplerate patch is for alsa-driver. I don't know if that has anything to do with it, though.
I'm working on it. My alsa-lib "softvol" patch isn't accepted yet (and there is still no any reaction on my messages, not at alsa-bugtrack nor at alsa-dev mailing lists). So, I don't think it will be easy to "push" alsa-driver patch to upstream - kernel-develovers don't like noob's patches.

---

### Post by sgx on 2009-12-21
> **CannibalZerg said:**
> I'm working on it. My alsa-lib "softvol" patch isn't accepted yet (and there is still no any reaction on my messages, not at alsa-bugtrack nor at alsa-dev mailing lists). So, I don't think it will be easy to "push" alsa-driver patch to upstream - kernel-develovers don't like noob's patches.
As an experiment, create an .rpm and .deb of your work that would
work using a certain specified ubuntu installation with your .deb/.rpm
to enable features x, y, and z to work on specific em-u hardware. I would require a minimum donation at least $5 Amazon giftcard to access the download. Post at forums like kvr, reaper, harmony central etc, wherever disgruntled musicians gather, proclaiming available hardware that works in linux, the first step in luring converts that will endure.
Cheers

---

### Post by Macdelaney on 2009-12-21
> **sgx said:**
> As an experiment, create an .rpm and .deb of your work that would
work using a certain specified ubuntu installation with your .deb/.rpm
to enable features x, y, and z to work on specific em-u hardware. I would require a minimum donation at least $5 Amazon giftcard to access the download. Post at forums like kvr, reaper, harmony central etc, wherever disgruntled musicians gather, proclaiming available hardware that works in linux, the first step in luring converts that will endure.
Cheers

Why not make it free and accept donations? 
I would definitely donate right now, and probably many others would too.

---

### Post by ubuntoyou2 on 2009-12-21
I'd upgraded from Jaunty to Karmic and things were getting worse and worse. So just did a fresh install and updated everything and my EMU usb is working "out of the box" as it is. Not sure of the samplerate though.  I did notice that before the reinstallation, when i rebooted into windows the samplerate of emu had changed to 44.1Khz which meant that when I tried to play a dvd, I couldn't until I changed the samplerate back to 48Khz.
Due to bootloader problems, I can't boot into windows at the moment,so don't know if that's still the case.  Working on it. You need lots of holidays with Linux!!
Good workaround bofphile. Might yet have to try it.

---

### Post by ubuntoyou2 on 2009-12-21
Hated repeating myself 8-)

---

### Post by okkyn on 2009-12-22
Hi, greeting to you all. I followed this thread since I acquired E-MU 0202 couple months ago. Good news is I can get wonderfull sound out from my EMU. Bad news is, it limited to 44.1 kHz and 48 kHz. I could get 44.1 from Audacious, Rythmbox and aplay; and 48 from VLC. But I want to play my 24/96 collection as is! :-x No matter what I did, I never got sample rate above 48 kHz. I can slide sample rate bar in alsamixer up, but the sound was distorted.

To whom successfully play above 48 kHz sampling rate, what is your player and configuration setup? For the reference, I use:
- ALSA 1.0.22 with the latest rate patch (automatic rate selector)
- Ubuntu karmic
- E-MU 0202 USB.

BTW, thank you for all efforts to make this wonderful soundcard works :)

---

### Post by klotz on 2009-12-24
@CannibalZerg I tested your rate-sensing patch on Ubuntu Koala and it works.  Thank you.  I filed an Ubuntu bug asking for them to take your patches upstream.

Instead of quoting, I'm linking to the patch instructions here:
[http://ubuntuforums.org/showpost.php?p=8502257&postcount=177](http://ubuntuforums.org/showpost.php?p=8502257&postcount=177)

Also, I had to do this as well, for Ubuntu Koala:
  patch -p1 < debian/patches/remove_maestro3.patch
  ./configure --with-cards=hda-intel,usb-audio

(HDA Intel support for mobo sound.)

I'm not sure, but it seems that "apt-get source alsa-driver" applies patches only the first time, and if you remove the alsa-driver-1.0.20+dfsg directory and try again, "apt-get source alsa-driver" fails to apply Ubuntu patches.  So I had to remove alsa* to force re-download.

Leigh.

---

### Post by CannibalZerg on 2009-12-25
> **klotz said:**
> @CannibalZerg I tested your rate-sensing patch on Ubuntu Koala and it works.  Thank you.  I filed an Ubuntu bug asking for them to take your patches upstream.

Thanks, but it's seems to be OK now. Today I've received confirmation from alsa-dev team, that patch will be accepted soon.(Softvol patch is also accepted). Thanks again for support.

> I'm not sure, but it seems that "apt-get source alsa-driver" applies patches only the first time, 
Try to run *make clean* command before applying patch.

---

### Post by dptkby on 2009-12-31
> **CannibalZerg said:**
> Thanks, but it's seems to be OK now. Today I've received confirmation from alsa-dev team, that patch will be accepted soon.(Softvol patch is also accepted). Thanks again for support.
Are you talking about the samplerate patch? If so, I take it your noob patch will end up in the kernel, eventually :). Good news, anyway!

---

### Post by soundcheck on 2010-01-10
Hi folks.


The 0404 is running 24/192 in async mode now


```

E-MU Systems, Inc. E-MU 0404 | USB at usb-0000:00:06.1-1.4.4, high speed : USB Audio

Playback:
  Status: Running
    Interface = 1
    Altset = 10
    URBs = 6 [ 8 8 8 8 8 8 ]
    Packet Size = 586
    Momentary freq = 192000 Hz (0x18.0000)
   Interface 1
    Altset 10
    Format: S24_3LE
    Channels: 2
    Endpoint: 1 OUT (ASYNC)
    Rates: 192000
    Data packet interval: 500 us

```


To test it you might try this:


```


SOX 14.3.0 ( parameters might differ from other revisions) 
sox -D -t wav -e signed-integer -b 24 -r 96000 yourinput-file.wav  -t wavpcm -e signed-integer -b 24 your192k-file.wav rate -v -I -s 192000
(Change file parameters accordingly)


Playback:

ecasound -B:rt -b:32 -r:80 -f:s24_le,2,192000,i -i:your192k-file.wav -o:alsahw,O,0


```


You can use my Alsa upgrade script (follow below link) to install Alsa 1.0.22.1 (install the snapshot)

Cheers

---

### Post by klotz on 2010-01-10
> **soundcheck said:**
> The 0404 is running 24/192 in async mode now

This is play only, not record, right?  So does this mean 1.0.22.1 includes the sample rate patches?

---

### Post by Macdelaney on 2010-01-11
For some reason I keep getting this error, has this happened to anyone else?
I can't find a solution that works!
Im in Arch btw

```
  CC [M]  /home/mac/Downloads/alsa-driver-1.0.22.1/usb/usbaudio.o
/home/mac/Downloads/alsa-driver-1.0.22.1/usb/usbaudio.c:1350: error: redefinition of &#8216;set_format_emu_quirk&#8217;
/home/mac/Downloads/alsa-driver-1.0.22.1/usb/usbaudio.c:1309: note: previous definition of &#8216;set_format_emu_quirk&#8217; was here
make[3]: *** [/home/mac/Downloads/alsa-driver-1.0.22.1/usb/usbaudio.o] Error 1
make[2]: *** [/home/mac/Downloads/alsa-driver-1.0.22.1/usb] Error 2
make[1]: *** [_module_/home/mac/Downloads/alsa-driver-1.0.22.1] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.32-ARCH'
make: *** [compile] Error 2

```

---

### Post by CannibalZerg on 2010-01-11
> **klotz said:**
> This is play only, not record, right?  So does this mean 1.0.22.1 includes the sample rate patches?

Yes, 1.0.22.1 includes the samplerate patch, finally.

> For some reason I keep getting this error, has this happened to anyone else?
It seems, that you've applied samplerate patch to 1.0.22.1, there is no need to do it any more.

---

### Post by Macdelaney on 2010-01-11
I'm trying to apply the latest alsa-driver patch since I hear everything in the wrong frequency by default. If I don't have to do that anymore, do I have to do anything else that I may be missing?

---

### Post by CannibalZerg on 2010-01-11
> **Macdelaney said:**
> I'm trying to apply the latest alsa-driver patch since I hear everything in the wrong frequency by default. If I don't have to do that anymore, do I have to do anything else that I may be missing?
I've compiled and tested 1.0.22.1 version from official alsa website(without any additional patches). It's works just fine. 

One possible reason is that capture is active.
> Added automatic sample rate adjustment for both playback and capture. (Capture has higher priority than playback: if recording is active - occasional playback at different sample rate will not spoil captured wav);
 

Run the command, and check Capture Status
```
cat /proc/asound/card1/stream0
```
Change *card1* to correct card number in your system. If you're using spdif output, replace *stream0* with *stream1*;

---

### Post by Macdelaney on 2010-01-11
I'm sorry to dump all of this here, but capture is not running and I still get sound in the wrong sample rate. I'm using Alsa 1.0.22 available from the Arch repositories, so this should work I believe.
Can anyone make any sense out of this? 



```
mac@goomba alsa-driver-1.0.22.1 $ cat /proc/asound/card0/stream0
E-MU Systems, Inc. E-MU 0202 | USB at usb-0000:00:1d.0-2, full speed : USB Audio

Playback:
  Status: Running
    Interface = 1
    Altset = 3
    URBs = 8 [ 2 2 2 2 2 2 2 2 ]
    Packet Size = 200
    Momentary freq = 47938 Hz (0x2f.f000)
  Interface 1
    Altset 1
    Format: S16_LE
    Channels: 2
    Endpoint: 1 OUT (ASYNC)
    Rates: 44100
  Interface 1
    Altset 2
    Format: S24_3LE
    Channels: 2
    Endpoint: 1 OUT (ASYNC)
    Rates: 44100
  Interface 1
    Altset 3
    Format: S16_LE
    Channels: 2
    Endpoint: 1 OUT (ASYNC)
    Rates: 48000
  Interface 1
    Altset 4
    Format: S24_3LE
    Channels: 2
    Endpoint: 1 OUT (ASYNC)
    Rates: 48000

Capture:
  Status: Stop
  Interface 2
    Altset 1
    Format: S16_LE
    Channels: 2
    Endpoint: 2 IN (ASYNC)
    Rates: 44100
  Interface 2
    Altset 2
    Format: S24_3LE
    Channels: 2
    Endpoint: 2 IN (ASYNC)
    Rates: 44100
  Interface 2
    Altset 3
    Format: S16_LE
    Channels: 2
    Endpoint: 2 IN (ASYNC)
    Rates: 48000
  Interface 2
    Altset 4
    Format: S24_3LE
    Channels: 2
    Endpoint: 2 IN (ASYNC)
    Rates: 48000
mac@goomba alsa-driver-1.0.22.1 $ 

```

---

### Post by fmarx358 on 2010-01-29
First, may I thank CannibalZerg and the testing contributors for such a great step foreward in getting the emu units to work.
This *is* an "awesome thread", not least in the sense that we can see the advances unfold ....

Second, I've got to report I'm only 1/2 way there:
    the good news:
         1) setting the rate via the "Clock Rate Selector" slide bar in alsamixer is
             working flawlessly;
    the bad news:
         1)  automatic rate setting is not working
         2)  spdif toggle is not working

It is as if the first patches are fine, but that the second set is not having any effect in alsa-driver.

I've attempted quite a bit to find the way foreward on my own:
    I'm running a straight debian sid system, kernel 2.6.32.5, but backed off to 2.6.29,
    to no avail.
Switched to the git repository, no difference.
Tried to compile with debug, to use the printk at the end of
    usbaudio.c:set_format, and am still working on getting that to work .....

Is anyone else having trouble, e.g., toggling spdif (my central problem) in alsamixer?

Thank you



Update (1215+500):
    I've got the printk working, and finally found the output in dmesg (???):

usbcore: registered new interface driver snd-usb-audio
setting done: format = 32, rate = 44100..44100, channels = 2                                                 [from initialisation]
  datapipe = 0x8400, syncpipe = 0x8480
setting done: format = 32, rate = 44100..44100, channels = 2                                                 [from aplay file.wav]
  datapipe = 0x8400, syncpipe = 0x8480
setting done: format = 32, rate = 44100..44100, channels = 2                                                 [from aplay file.wav]
  datapipe = 0x8400, syncpipe = 0x8480
                                                                                                                                          [from mplayer somedvd.iso, after having set alsamixer to 48000]
aplay[24454]: segfault at 2f534543 ip b7658dc8 sp bf9f75f0 error 4 in libasound.so.2.0.0[b762e000+c3000]
setting done: format = 32, rate = 44100..44100, channels = 2
  datapipe = 0x8400, syncpipe = 0x8480

In between the first two aplay's, I slide the alsamixer slider up and down - it is not registering in dmesg.

I'm in the process of recompiling alsa-lib, from git repository, will report further ....

Update2:

O.k.:
    1)  recompiled and reinstalled the git alsa-lib, and the segfault appears to be unrelated, related rather to external events,
eg., suspending and then killing aplay, or stopping alsamixer while playing....
    2)  now:
         i)  added
     pcm.pcmUsb {
                type hw
            card USB
      }
      pcm.48dmix {
            type dmix
            ipc_key 1024
                slave { 
                          pcm "pcmUsb"
                   format S24_3LE
                           period_time 0
                   period_size 1024
                           buffer_size 8192
                           rate 48000
                }
      
} 
to .asoundrc; run /etc/init.d/alsa-utils restart, and then mplayer -ao alsa:device=plug=48dmix, and get:

                             a)  mplayer reports running at 48000
          b) dmesg reports:
                                                                     setting done: format = 32, rate = 48000..48000, channels = 2
                   datapipe = 0x8400, syncpipe = 0x8480
          c) alsamixer slider remains at 0 (44100)
          d) sound is distorted until I move the alsamixer slider to 1 (48000), at which point sound is correct.

So, ..., I'm not sure what that means ....

---

### Post by CannibalZerg on 2010-01-30
> 1) recompiled and reinstalled the git alsa-lib, and the segfault appears to be unrelated, related rather to external events,
eg., suspending and then killing aplay, or stopping alsamixer while playing....
**fmarx358**, as I mentioned above, there is no need to apply any patches. Just get the latest alsa-driver(v.1.0.22.**1**), alsa-lib and alsa-utils from [www.alsa-project.org](www.alsa-project.org), compile and install it.

> In between the first two aplay's, I slide the alsamixer slider up and down - it is not registering in dmesg.
It's ok, my patch doesn't contain any printk calls.
> Is anyone else having trouble, e.g., toggling spdif (my central problem) in alsamixer?
Yes, "spdif format" toggle doesn't work. But "spdif out" itself works (with some bugs and limitations). If you want to play sound through the SPDIF, you should use device "hw:0,1" or "plughw:0,1"  ("0" means device number; if you have more than one soundcard, run "aplay -l"  to find device number of emu0404). Or you can put in .asoundrc something like:
```

pcm.usb_an{
   type plug
   slave{
      pcm "hw:0,0"
      format S24_3LE
  } 
  hint{
    show on
    description "EMU-0404USB output"
  }
 }

pcm.usb_dig{
   type plug
   slave{
      pcm "hw:0,1"
      format S24_3LE
  } 
  hint{
    show on
    description "EMU-0404USB SPDIF output"
  }
 }

```
And try to run "aplay -D usb_dig some_wav.wav"
But be prepared: if you play something through SPDIF, any occasional playback to analogue subdevice will cause segfault. Unfortunately I don't have another one soundcard with full-featured SPDIF in/out to fix SPDIF related bugs.

---

### Post by fmarx358 on 2010-01-30
[HTML]
CannibalZerg, thank you, that explains a lot.

o.k.:

1)  I haven't been patching, rather switching from the 1.0.22.1 tar-ball to the git-repository -
     but of course they are identical.

2)  Am I correct in the following understanding of automatic rate switching:
     -D hw:0,0 requires the user to set the state of the hardware
     -D plug:dmix is what you've altered, such that, when the patches are working,
          just playing a file through that interface will find the rate of the incoming stream,
          and set the state of the hardware itself?

3)  My central problem: s/pdif is not working correctly; here's an account:
     A) my external DAC has led's which light up when it senses something at the other
         end of the wire or not, red for inactive, green for active;
     B) when the usb-audio module is loaded, but the 0404 is powered off, the light is red;
     C) module still loaded, then when the 0404 is powered on, the light switches green;
     D) when I do aplay -D hw:0,1 that_wav.wav, it switches back ** red **;
         when I end aplay, it switches back green

4) When I was having so much problems understanding the 0404 and usb-audio, I broke down
    and went over an installed the winxp drivers;  during that process, emu upgraded the firmware
    at some point, from 4.?.? to 8.?.?, in other words to a very recent firmware.
    A) I got spdif working (with help from asio4all) there; so I know:
        i) 0404 works
       ii) external DAC works

5) I'm getting the following error with your .asoundrc suggestion (and the rest of .asoundrc commented out):

    Playing WAVE 'track01.cdda.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
    ALSA lib pcm_params.c:2150:(snd1_pcm_hw_refine_slave) Slave PCM not usable
    aplay: set_params:1031: Broken configuration for this PCM: no configurations available

     A) if I alter pcm "hw:0,1" to pcm "plughw:0,1", then:
          i) the external DAC's light * stays green *;
         ii) no sound
        iii) after several seconds:

            underrun!!! (at least 0.002 ms long)
            underrun!!! (at least 0.002 ms long)
                                                
Thank you again[/HTML]

---

### Post by CannibalZerg on 2010-01-31
> **fmarx358 said:**
> [HTML]
Am I correct in the following understanding of automatic rate switching:
     -D hw:0,0 requires the user to set the state of the hardware
     -D plug:dmix is what you've altered, such that, when the patches are working,
          just playing a file through that interface will find the rate of the incoming stream,
          and set the state of the hardware itself?

No, sampletate adjastment is a part of alsa-driver. Dmix patch was written to eliminate sound distortions for S24_3LE format in previous version of alsa-lib. Dmix itself is a software mixing plugin, which allows you to play several sound streams simultaneously. Software mixing is possible only at one samplerate, so any sound stream will be resampled before mixing. When you're using dmix - automatic samplerate adjustment is quite useless, because sound stream after dmix will have constant samplerate (48000kHz for example).

>  underrun!!! (at least 0.002 ms long)
 underrun!!! (at least 0.002 ms long)

I can't help you with SPDIF, in my case playback through hw:0,1 doesn't affect buffer underrun, but I can't check is there any sound or not, sorry.

---

### Post by Mocchi on 2010-01-31
Hi, CannibalZerg

I'm very happy with your work and E-MU 0404 USB! I enjoy good sound on Ubuntu Studio 9.10.

Now my device works correctly on alsa-driver v.1.0.22.1 but it didn't on alsa-driver 1.0.20 with your patch. 

```
$uname -a
Linux 7675A63 2.6.31-9-rt #152-Ubuntu SMP PREEMPT RT Thu Oct 15 05:01:14 UTC 2009 i686 GNU/Linux
```At first, I did.
```
$ sudo apt-get install alsa-source
$ cd /usr/src
$ sudo tar xjvf alsa-source.tar.gz2
$ cd modules/alsa-driver
$ sudo wget http://pastie.org/743114.txt
$ sudo patch -p0 < 743114.txt
$ sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r)
$ sudo make
$ sudo make clean
$ sudo make install
$ sudo shutdown now -r
```After reboot, I connected my device and turn it on. Then
```
[  603.440183] usb 1-4.3: new high speed USB device using ehci_hcd and address 7
[  603.527376] usb 1-4.3: configuration #1 chosen from 1 choice
[  603.548213] snd_usb_lib: Unknown symbol snd_verbose_printk
[  603.557485] snd_usb_lib: Unknown symbol snd_verbose_printk
[  603.564809] snd_usb_lib: Unknown symbol snd_verbose_printk
[  603.568193] snd_usb_lib: Unknown symbol snd_verbose_printk
[  769.665783] usb 1-4.3: USB disconnect, address 7
```I thought there are some conflicts between your patch and this package. I reinstall the kernel image and got alsa-driver v.1.0.20 in ALSA website and patch, compile and install. But the same messages I got.

Then I reinstalled the kernel image and installed the latest alsa-driver from ALSA website. Then it works well. Thanks for your great work!

Now I'm very satisfied but I think it good to tell this problem to you.
I wonder The way you post this thread is only good for generic kernel.

---

### Post by klotz on 2010-03-04
Great news!  alsa 1.0.22-1 has appeared in Koala backports:

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.31/+bug/503829](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.31/+bug/503829)

I just added backports to my sources and used synaptic to make sure that linux-backports-modules-2.6.31 was installed, rebooted, and I have auto-sensing of sample rate up to 96KHz input, same as with the patch procedure.

---

### Post by bofphile on 2010-03-21
What is the best settings to use in "/etc/pulseaudio/daemon.conf" for the sample format ?

I think I should use a bit depth of 24bits but I'm not sure which one to choose:
"default-sample-format=  The default sampling format. Specify one of u8,s16le, s16be, s24le, s24be, s24-32le, s24-32be, s32le, s32be float32le, float32be, ulaw,  alaw. Depending on the endianess of the CPU the formats s16ne, s16re, s24ne,  s24re,  s24-32ne,  s24-32re,  s32ne,  s32re, float32ne,  float32re  (for native, resp. reverse endian) are available as aliases."

Also I'm mainly listening to 16bits/44.1kHz files, I've read it's best to use a bit depth of 24bits if the soundcard supports it (at least on Windows Vista/7). Is it also true on the Linux side ?

Thanks.

---

### Post by sgx on 2010-03-22
> **bofphile said:**
> What is the best settings to use in "/etc/pulseaudio/daemon.conf" for the sample format ?

I think I should use a bit depth of 24bits but I'm not sure which one to choose:
"default-sample-format=  The default sampling format. Specify one of u8,s16le, s16be, s24le, s24be, s24-32le, s24-32be, s32le, s32be float32le, float32be, ulaw,  alaw. Depending on the endianess of the CPU the formats s16ne, s16re, s24ne,  s24re,  s24-32ne,  s24-32re,  s32ne,  s32re, float32ne,  float32re  (for native, resp. reverse endian) are available as aliases."

Also I'm mainly listening to 16bits/44.1kHz files, I've read it's best to use a bit depth of 24bits if the soundcard supports it (at least on Windows Vista/7). Is it also true on the Linux side ?

Thanks.
In general, mastering finished projects done in 24bit resolution gives the mastering technician room to change things with minimal sound degradation.
Depending on your target audience, and your system quality, it may be
OK to do 16 bit, to save on system overhead. If your system gets maxed out at 24 bit and 48/96khz, on the kind of projects you do, then go lower until you can upgrade, or optimize your gear.
Like they say, if its good enough for Britney CDs... ;)
Cheers

---

### Post by CannibalZerg on 2010-03-22
> Also I'm mainly listening to 16bits/44.1kHz files, I've read it's best to use a bit depth of 24bits if the soundcard supports it 
EMU alsa-driver accepts only 24bit format. Even when you feed it with 16bit samples, alsa scales it to 24bit automatically.

> **bofphile said:**
> What is the best settings to use in "/etc/pulseaudio/daemon.conf" for the sample format ?

I think I should use a bit depth of 24bits but I'm not sure which one to choose:

Native format for E-Mu0404USB is S24_3LE, so I think that *s24le* value will be OK. But I recommend you to use *s32le* for pulseadio. 32bit processing is more accurate and faster than 24bit one.

---

### Post by bofphile on 2010-03-22
> **CannibalZerg said:**
> EMU alsa-driver accepts only 24bit format. Even when you feed it with 16bit samples, alsa scales it to 24bit automatically.



Native format for E-Mu0404USB is S24_3LE, so I think that *s24le* value will be OK. But I recommend you to use *s32le* for pulseadio. 32bit processing is more accurate and faster than 24bit one.

I suppose this is the same for E-Mu 0202USB ?

Thanks sgx and CannibalZerg for your advices. ;)

---

### Post by floflooo on 2010-04-04
On Ubuntu Studio, my EMU 0404 USB works fine when I use PulseAudio. However, I don't seem to be able to use it when JACK is running. See on the screenshot how only MIDI ports are available for the EMU, no input or output. Hence, I'm not able to record from it in Ardour.

Has anyone this issue, or is it working for everyone?

---

### Post by VFXCode on 2010-04-05
Hallo,
I am a debian user and i installed latest kernel (2.6.34-rc3) just for this driver for my EMU 0404.
I have one question thou, while everything works well (Samplerate selector and auto sample rate sensing)
all play back programms resample EVERYTHING to 48Khz, exept jackd which i used to test the samplerate sensing. I dont have pulseaudio installed so it is not it.
How do you output your audio at its own sample rate?


Thnx

---

### Post by floflooo on 2010-04-08
I don't know about this VFXcode. I use the defaults in terms of sampling rate.
Do you manage to record from the EMU 0404 using JACK?

---

### Post by VFXCode on 2010-04-12
No actually i haven't. I am not intrested in recording, just only non-oversampling or down-sampling playback

---

### Post by floflooo on 2010-04-13
Ok, thanks...
I found out that my card is fine, but JACK has to be setup to use it. See:
[http://ubuntuforums.org/showthread.php?t=1377954](http://ubuntuforums.org/showthread.php?t=1377954)
and 
[http://ubuntuforums.org/showthread.php?t=1416061](http://ubuntuforums.org/showthread.php?t=1416061)

---

### Post by Zolan on 2010-05-31
Hi, first of all I'd like to thank and congratulate CannibalZerg for his awesome contribution to the linux world.
But awesome as it is, I'm having a little trouble with it. I recently switched to Arch, and although I'm using a fairly recent alsa and the soundcard is recognized I have a very annoying issue. I have sound playback but it sounds very "dirty", like if the frequency was wrong, and I don't have the clock rate selector anymore so I can't change it. I've been searching for a solution to this, and I've tried a few things but none have worked so far. The weird thing is that last night I could listen to some mp3's but watching a a movie in .mkv would sound like this, and now the problem has spread system-wide. Any help would this would be greatly appreciated since I'm not sure what to try next.

Here is a list of my alsa packages and versions.
```
[zolan@goomba ~]$ yaourt -Q | grep alsa
==> List all installed packages
extra/alsa-firmware 1.0.23-1
extra/alsa-lib 1.0.23-1
extra/alsa-oss 1.0.17-1
local/alsa-tools 1.0.22-1
extra/alsa-utils 1.0.23-2

```and here's how my alsamixer looks like 

[IMG]http://imgur.com/TS90G.png[/IMG]

Again, any help would be greatly appreciated.
Thanks

---

### Post by sgx on 2010-06-01
Hi, if you have a gui package manager for arch, uninstall as many audio apps as you can.Brutality. Try to leave only

alsamixergui
alsaplayer
aconnectgui

one video player, vlc or xine

jackd and qjackctl.

Now you can test your i/o
with few weirdo apps confusing things
Cheers

---

### Post by Zolan on 2010-06-01
Since I just installed the OS I don't have a lot of "weird" apps. Just mplayer for video, and Rhythmbox music. 
Curious thing is that I try to see if installing alsa-plugins helped, and when I rebooted I noticed that I can play mp3's fine using mplayer, but if I use Rhythmbox or try to playback a mkv movie, everything starts going wrong again. This is very weird, and I'm really not sure what to look for, much less what to do.
Thanks for your reply sgx, and any further help would be greatly appreciated.

---

### Post by Zolan on 2010-06-01
Never mind, the same thing happens my other soundcard so it's not Emu related, I messed up something else.

---

### Post by sgx on 2010-06-02
> **Zolan said:**
> Since I just installed the OS I don't have a lot of "weird" apps. Just mplayer for video, and Rhythmbox music. 
Curious thing is that I try to see if installing alsa-plugins helped, and when I rebooted I noticed that I can play mp3's fine using mplayer, but if I use Rhythmbox or try to playback a mkv movie, everything starts going wrong again. This is very weird, and I'm really not sure what to look for, much less what to do.
Thanks for your reply sgx, and any further help would be greatly appreciated.
Hi, mplayer, due to its many updates, is sometimes problematic, as the
apps around it can't always be tested to remain compatible. Full featured
players like amarok and rythmbox have complexity as a side effect, so I
suggested the minimums to test. 

Codecs and their handlers can also be troublesome, ffmpeg and gstreamer are commonly used to juggle many codecs between the various player gui,
and updates to video codecs try to keep pace with hardware being sold. 
Cheers

---

### Post by v.stiff on 2010-07-06
Does anyone know why is this patch still not included in official alsa or ubuntu package patches?

Where is the open source promise: 'When you found the bug, just release the patch'?

Two years ago I recommended all my friends to use linux instead of windows, now I'm not only stopped doing this (because it's open-ness is a lie) but thinking to move back. Every ubuntu upgrade is soo much painful and frustrating for me. When I was young it was fun to search couple hours for patches and to compile them, but now I'm just tired of it.

Look at the Firefox and Google Chrome. Yes, Firefox is definitely worlds better than IE, but honestly it's still terrible comparing to what a good browser is.

---

### Post by klotz on 2010-07-30
It was working for me in ubuntu backports, because the changes made it into alsa.  However, with Ubuntu Lucid and 2.6.32-24, I now get a 100% CPU utilization loop as soon as I turne on the EMU-0202 and then nothing works (no mouse, no kbd, except remote ping) until I hard reset.

---

### Post by bofphile on 2010-07-31
I noticed this problem too. So for now I removed the alsa-backports and only use the device at 44,1kHz. Furthermore when I installed them, I could not turn off bluetooth on my Thinkpad anymore.
I briefly tried a live cd of Ubuntu Maverick, and the problem didn't seem to be present. I could change the sample rate without problem with the stock alsa-drivers.

---

### Post by TimCastle on 2010-08-13
Do you use the EMU 0404 USB for hi-fi playback? 

Is there anyway to get alsa to use hw: instead of the plughw: ?

hw:CARD=USB,DEV=0
    E-MU 0404 
    Direct hardware device without any conversions
hw:CARD=USB,DEV=1
    E-MU 0404 
    Direct hardware device without any conversions
plughw:CARD=USB,DEV=0
    E-MU 0404 
    Hardware device with all software conversions
plughw:CARD=USB,DEV=1
    E-MU 0404 
    Hardware device with all software conversions

---

### Post by klotz on 2010-09-07
Here's the status AFAIK in Ubuntu Maverick Meerkat 10.10 Beta:

CannibalZerg's patch: "Added functionality for E-mu 0404USB/0202USB" [1] is in “alsa-driver” 1.0.23+dfsg-1ubuntu3 source package in The Maverick Meerkat [2] which was accepted [3].

[1] [http://mailman.alsa-project.org/pipermail/alsa-devel/2009-December/024097.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2009-December/024097.html)

[2] [https://launchpad.net/ubuntu/maverick/+source/alsa-driver/1.0.23+dfsg-1ubuntu3](https://launchpad.net/ubuntu/maverick/+source/alsa-driver/1.0.23+dfsg-1ubuntu3)

[3] [https://lists.ubuntu.com/archives/maverick-changes/2010-September/006742.html](https://lists.ubuntu.com/archives/maverick-changes/2010-September/006742.html)

---

### Post by Spcomb on 2010-10-11
What's the status on EMU USB support in recent versions of ALSA?

I've been trying to get my EMU 0202's volume control and sample rate control to work on a non-GUI Debian/testing box with ALSA 1.0.23 and a 2.6.32-5-amd64 kernel, but without very much luck so far.

The card's "PCM" volume control hasn't worked properly on any Ubuntu or Debian box that I've tried using it on (full output volume even at 3%, or no effect at all), and with this Debian box, not even the PCM Mute toggle works. Additionally, the sample rate control doesn't seem to work with anything except the default 44.1kHz.

Currently, I'm able to use it at 24bit/44.1kHz with a separate softvol control using the following ~/.asoundrc snippet:

```
## Emu 0202 with software volume control
pcm.emu_softvol {
    type                softvol

    slave {
        pcm {
            type                hw

            # Emu 0202
            # this is well-hidden, because we NEVER want to directly access this
            # doing so will blow our ears...
            card                1
            device              0
        }

        format              S24_3LE
    }

    control {
        name            "Softmaster"
        card            1
    }
}

## Emu 0202 with rate/format conversion
pcm.emu {
    type                plug

    slave {
        pcm             emu_softvol

        format          S24_3LE
        channels        2

        # optional resampling, but ideally this should work without, 
        # automatically choosing the correct sample rate
#        rate            44100
    }
}

```With the rate statement active, speaker-test samples at 44.1kHz and 48kHz sound "okay", with /proc/asound/card1/pcm0p/sub0/hw_params showing a 44100 rate.

However, without the rate statement, a `speaker-test -c 2 -D emu -t sine -f 200 -r 48000` sounds utterly distorted, even though the hw_params mentioned above shows the correct 48000 rate, leading me the believe that the USB interface's sample rate isn't getting set correctly.

Taking a quick look at the 1.0.23 ALSA source code, I can only find a part of the patch against 1.0.22 found earlier in this thread. In particular, the manual sample rate control was omitted? In theory, it looks like the automatic sample rate detection should be there, but for whatever reason, it doesn't seem to work.

Playing a sample with 192kHz doesn't cause the Direct Monitor LED on the device to deactivate, indicating that the device isn't changing the sample rate.

ALSA 1.0.22 on Ubuntu 10.04 with a 2.6.32-21-generic kernel seems to act exactly the same way. I haven't had a chance to test the patched 1.0.22, so I don't know if this is a regression, or some other issue on my end. Neither do I know if the PCM volume control is even supposed to work.

EDIT: Had another look at the ALSA 1.0.23 sources, and the samplerate patch IS there in its entireity, just refactored. I just can't figure out how to access the various XU controls from alsamixer, all I see is one boolean switch labeled "Extension Unit"...?

---

### Post by klotz on 2010-10-11
> **klotz said:**
> Here's the status AFAIK in Ubuntu Maverick Meerkat 10.10 Beta:

CannibalZerg's patch: "Added functionality for E-mu 0404USB/0202USB" [1] is in “alsa-driver” 1.0.23+dfsg-1ubuntu3 source package in The Maverick Meerkat [2] which was accepted [3].

[1] [http://mailman.alsa-project.org/pipermail/alsa-devel/2009-December/024097.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2009-December/024097.html)

[2] [https://launchpad.net/ubuntu/maverick/+source/alsa-driver/1.0.23+dfsg-1ubuntu3](https://launchpad.net/ubuntu/maverick/+source/alsa-driver/1.0.23+dfsg-1ubuntu3)

[3] [https://lists.ubuntu.com/archives/maverick-changes/2010-September/006742.html](https://lists.ubuntu.com/archives/maverick-changes/2010-September/006742.html)

Ubuntu 10.10 was released yesterday.  Has anyone tried it yet to see if 96KHz support is present?

---

### Post by KingBongo on 2010-10-17
Hi. I am looking into buying either an 0202 USB or an 0404 USB unit. At this point I am only interested in playback. Is any of these units now working for that purpose, and at which sample rates/number of bits? 

I am not buying any of them before they can be easily set up, preferably out of the box. I am prepared to add some back-ports, upgrade stuff, but not much more than that. After that I should have perfect sound (almost) 100% sure. Let's just say I am worn out after some graphics cards I have had ;)

Can anyone tell me what the status is for these cards? Please.

---

### Post by klotz on 2010-10-17
> **KingBongo said:**
> Hi. I am looking into buying either an 0202 USB or an 0404 USB unit. At this point I am only interested in playback. Is any of these units now working for that purpose, and at which sample rates/number of bits? 

I am not buying any of them before they can be easily set up, preferably out of the box. I am prepared to add some back-ports, upgrade stuff, but not much more than that. After that I should have perfect sound (almost) 100% sure. Let's just say I am worn out after some graphics cards I have had ;)

Can anyone tell me what the status is for these cards? Please.

What version of Linux do you plan to use?  I'm planning to test Ubuntu Maverick in a few days to see if it works out of the box at 96KHz sampling.  The ALSA patches cannibalzerg submitted were accepted, and they were in Ubuntu Lucid backports for a while, but then it broke.  So I'm hoping that with a straight distribution it works.  Others (not on Ubuntu) reported no problems with the Alsa sources.

---

### Post by Yako on 2010-10-17
> **KingBongo said:**
> Hi. I am looking into buying either an 0202 USB or an 0404 USB unit. At this point I am only interested in playback. Is any of these units now working for that purpose
[...]
Can anyone tell me what the status is for these cards? Please.

Hi, I read your post, and decided to plug my 0404 USB unit into my laptop, which has a pretty much fresh installation of Ubuntu 10.10. All I had to do is go to System > Preferences > Sound > Output, and the EMU 0404 USB device automagically appeared there. I selected it, and tested it with some FLAC audio file in Totem, and it seems to work out-of-the-box. System volume controls work as well.

I think the sample rate is 44.1kHz, since that's the default one. I have no idea how to test different sample/bit rates though. Hope this helps a bit.

---

### Post by klotz on 2010-10-17
> **Yako said:**
> I think the sample rate is 44.1kHz, since that's the default one. I have no idea how to test different sample/bit rates though. Hope this helps a bit.
If you have alsamixer installed you can do this at a shell command prompt:
(assuming it's the only other device beside onboard sound):

**$ **alsamixer -c1

It will say EMU-0404 at the top.

If the sample rates work, there will be a sample rate indicator/control on the right.
If it just says "Extension Unit" and shows MM inside it, then the sample rate patch isn't in.

---

### Post by KingBongo on 2010-10-18
Thank you guys. Nice to hear there is some progress :) Please try it on Ubuntu 10.10!

klotz:
I am running Ubuntu 10.10 :) The reason is that my X-Fi Surround USB sound card now finally works without any issues. I am looking for an upgrade though.

EDIT: Sorry. I overlooked that you already tried it in Maverick. Please check with different sample rates as well.

---

### Post by Yako on 2010-10-18
> **klotz said:**
> If you have alsamixer installed you can do this at a shell command prompt:
[..]

It says "Clock rate selector", which has 6 different settings. If I change it the audio becomes distorted (and frequency of the sound is higher), which I assume means the card's sample rate is increased, but the driver still sends audio in the old sample rate.
I don't know how to make Ubuntu pick a certain sample rate, but looking at it, it seems the driver is able to set the sample rate automatically:

Stereo capture works as well! In decent quality. I used Audacity for audio capture, and selecting a certain project sample rate in Audacity seems to pick the corresponding Clock Rate in Alsamixer automatically, up to 96 kHz.


Edit: Also, [this](http://i.imgur.com/xcSAI.png) is a pretty epic error message. :)

---

### Post by KingBongo on 2010-10-24
Ok. Maybe I will have to pull my hair out another time! I ordered the 0404 USB. It looks like it works with 44.1kHz/16bit material (what I have) out-of-the-box now so I am confident.

---

### Post by KingBongo on 2010-11-01
Hi guys! Now I really need some help here! My 0404 arrived and seemed to work well for a short while, and then POFF! left channel died and has been dead ever since :(

Help please. I don't even know where to start! I know about how to do changes in sound preferences, but that is about it.

EDIT: Ok. Something seems to have been messed up. The central volume control (on multimedia keyboard) seems to be controlling the left channel only. What controls the right channel? I don't know, lol. It seems like the left channel is assigned as rear and the right channel as front or something like that. Please help me out here.

---

### Post by billnace on 2010-11-04
I'm having the same problem as Kingbongo.  It seems the pulseaudio master volume is only altering the left channel on my emu 0404, only thing it does to the right channel is mute it if you go down to 0%.  Kingbongo, the volume controls within programs should work  (i.e. banshee, rhythmbox, etc.), as should the volume controls for the individual app under pulseaudio (click the sound icon, preferences, applications).  Your multimedia keys are tied into the pulse master volume control, which is where the problem lies.  Anyone out there have an idea for a fix?  I'm really laughing at this now, since the master didn't work at all for me in Lucid, and now I guess the problem's 50% fixed.

---

### Post by KingBongo on 2010-11-04
billnace:
Ahhh. Thank you! As you probably have guessed, it's exactly like that for me too. I don't know, but this problem seems easy to fix compared to most of the other stuff, :P I might be uninformed though. I guess we will just have to wait for a fix. As annoying as it is, I still can live with that as long as it does not affect the sound.

---

### Post by Kreukels on 2010-11-15
> **Yako said:**
> It says "Clock rate selector", which has 6 different settings. If I change it the audio becomes distorted (and frequency of the sound is higher), which I assume means the card's sample rate is increased, but the driver still sends audio in the old sample rate.
I don't know how to make Ubuntu pick a certain sample rate, but looking at it, it seems the driver is able to set the sample rate automatically:


Every applications audio gets mixed and resampled by PulseAudio. Deafault is 44.1khz. If you turn up the slider thus increasing the sampling frequency, the pitch goes up because 44.1khz is replayed in less time. ie. the USB interface expects more samples per second but gets fed the same.

You can tell Pulse to resample at a higher frequency in /etc/pulse/daemon.conf (making it a global setting)
Or perhaps tell Pulse to stop resampling at all and hence decreasing Pulses burden.

---

### Post by TimCastle on 2010-11-15
Can we avoid resampling playback altogether? 

I see

hw:CARD=USB,DEV=0
E-MU 0404
Direct hardware device without any conversions
hw:CARD=USB,DEV=1
E-MU 0404
Direct hardware device without any conversions
plughw:CARD=USB,DEV=0
E-MU 0404
Hardware device with all software conversions
plughw:CARD=USB,DEV=1
E-MU 0404
Hardware device with all software conversions

But I can't get ALSA to work with hw:, only plughw

---

### Post by klotz on 2010-11-25
Just checked in Ubuntu Maverick 10.10 and the EMU-1010 works at 96 KHz sampling and the clock rate settings from programs work automatically.  So both those patches are indeed working.

Leigh.

---

### Post by molotov256 on 2010-11-29
Not sure if this is news to anyone else, but I got my 404USB to work in Ardour for playback and recording in UbuntuStudio 10.10.  All I had to do was go through Setup in JACKControl and select the device for input and output.

Not sure why I'd been banging my head up against the wall for so long over that, lol... now I can stop recording in Windows! Yea!

---

### Post by klotz on 2010-12-14
This just in...the EMU-0202 has been replaced by the EMU-0204:


[http://www.emu.com/corporate/dealer/files/E-MU0204USB/0204%20Sales%20Guide.pdf](http://www.emu.com/corporate/dealer/files/E-MU0204USB/0204%20Sales%20Guide.pdf)

[http://www.floridamusicco.com/proddetail~prod~0204_usb_audio_interface.htm](http://www.floridamusicco.com/proddetail~prod~0204_usb_audio_interface.htm)

---

### Post by Youman on 2011-01-06
I have the new **0204 EMU** Soundinterface here on my desk. Unfortuantely it does not work out of the box.


lsusb output is:

Bus 002 Device 003: ID 041e:3f19 Creative Technology, Ltd 

Can I make this device to run? I think it is similar to the 0202 device.
I'am not advanced in linux. If you have an sugestion plase eplain it.

Chis

I have added the output of lsusb -v to my post.
Maybe it helps?

---

### Post by Youman on 2011-01-17
Hi,

I have sent the 0204 back. Thats a pity, because I think it sounds a little bit better than the 0202.

---

### Post by altwazar on 2011-01-29
Playback works fine, but microphone to quiet.
When using windows mic work as intendent, in linux (ubuntu 10.10 and others) i can barely hear it.
Does anyone here have the same problem?

---

### Post by klotz on 2011-02-05
EMU-0202 seems to be broken again. Ssound card input fails.

Diagnostics:
alsamixer fails with 
  "cannot load mixer controls: Invalid argument"

I get this when I turn it on in dmesg:

```
[  583.562286] usb 1-1.4: new high speed USB device using ehci_hcd and address 9
[  583.662878] 9:1:1: endpoint lacks sample rate attribute bit, cannot set.
[  583.663247] 9:1:2: endpoint lacks sample rate attribute bit, cannot set.
[  583.663617] 9:1:3: endpoint lacks sample rate attribute bit, cannot set.
[  583.663993] 9:1:4: endpoint lacks sample rate attribute bit, cannot set.
[  583.664830] 9:1:5: endpoint lacks sample rate attribute bit, cannot set.
[  583.665253] 9:1:6: endpoint lacks sample rate attribute bit, cannot set.
[  583.665618] 9:1:7: endpoint lacks sample rate attribute bit, cannot set.
[  583.666089] 9:1:8: endpoint lacks sample rate attribute bit, cannot set.
[  583.666492] 9:1:9: endpoint lacks sample rate attribute bit, cannot set.
[  583.666869] 9:1:10: endpoint lacks sample rate attribute bit, cannot set.
[  583.667242] 9:1:11: endpoint lacks sample rate attribute bit, cannot set.
[  583.667994] 9:2:1: endpoint lacks sample rate attribute bit, cannot set.
[  583.668364] 9:2:2: endpoint lacks sample rate attribute bit, cannot set.
[  583.668742] 9:2:3: endpoint lacks sample rate attribute bit, cannot set.
[  583.669112] 9:2:4: endpoint lacks sample rate attribute bit, cannot set.
[  583.669611] 9:2:5: endpoint lacks sample rate attribute bit, cannot set.
[  583.669986] 9:2:6: endpoint lacks sample rate attribute bit, cannot set.
[  583.670499] 9:2:7: endpoint lacks sample rate attribute bit, cannot set.
[  583.670861] 9:2:8: endpoint lacks sample rate attribute bit, cannot set.
[  583.671369] 9:2:9: endpoint lacks sample rate attribute bit, cannot set.
[  583.671859] 9:2:10: endpoint lacks sample rate attribute bit, cannot set.
[  583.672233] 9:2:11: endpoint lacks sample rate attribute bit, cannot set.
[  583.695621] 9:1:1: endpoint lacks sample rate attribute bit, cannot set.
```

Eventually I'll get (here with 10 instead of 9, since I've repeated the test)
```

[  784.732753] 10:2:1: usb_set_interface failed
[  789.726801] 10:2:1: usb_set_interface failed
[  794.720885] 10:2:1: usb_set_interface failed
[  799.715979] 10:2:1: usb_set_interface failed
[  804.709091] 10:2:1: usb_set_interface failed
[  809.786982] 10:2:1: usb_set_interface failed
[  814.780645] 10:2:1: usb_set_interface failed
[  819.775501] 10:2:1: usb_set_interface failed
[  824.768466] 10:2:1: usb_set_interface failed
[  829.762546] 10:2:1: usb_set_interface failed
[  835.880334] 10:2:1: usb_set_interface failed
[  840.873402] 10:2:1: usb_set_interface failed
[  845.867485] 10:2:1: usb_set_interface failed
[  850.861581] 10:2:1: usb_set_interface failed

```

I'm on 2.6.35-26-generic-pae build from Ubuntu Maverick 10.10.

I wonder if this change is somehow related, either in that it has, or perhaps hasn't, happened.

> 
The Audio Class v2 support code in 2.6.35 added checks for the
bInterfaceProtocol field.  However, there are devices (usually those
detected by vendor-specific quirks) that do not have one of the
predefined values in this field, which made the driver reject them.

To fix this regression, restore the old behaviour, i.e., assume that
a device with an unknown bInterfaceProtocol field (other than
UAC_VERSION_2) has more or less UAC-v1-compatible descriptors.


[http://amailbox.org/mailarchive/linux-kernel/2010/9/18/4621391](http://amailbox.org/mailarchive/linux-kernel/2010/9/18/4621391)

---

### Post by klotz on 2011-02-07
OK, moved some PCI cards around and I now get EMU-0202 working again.
The "lacks attribute bit" is still there but seems to be a warning.
I also validated on a fresh upgrade from 10.04 to 10.10 on a laptop.
Leigh.

EDIT: OK, broken again.  doing apt-get remove pulseaudio and reboot seems to make it more stable.

---

### Post by snop on 2011-03-23
I managed to make E-MU 0204 to work under Ubuntu 10.04 and 10.00. More info here:
[http://ubuntuforums.org/showthread.php?t=1713011](http://ubuntuforums.org/showthread.php?t=1713011)

Edit: It seems that Ubuntu 11.04 already has this patch applied. At the time of writing this 11.04 is still in beta.

---

### Post by johnme on 2011-03-27
I am using Ubuntustudio 10.04 and Alsa 1.0.23.
The 0404 plays analog out is working.

Recently, I tried to use the SPDIF output of 0404 USB.
But get error messages such as:

snd-pcm failed OR pcm_hw_params_setting

depending on the playback software used.

I cannot find the "snd-pcm" nor "pcm_hw_params_setting" strings in config files.

Please advise.

---

### Post by macramole on 2012-05-08
Hey, 

I'm was having the same issue under Fedora 16, when I turned down the master volume in gnome only the left channel was going down.

I fixed it in Sound Settings > Hardware, selected the E-Mu and changed the profile to Digital Stereo Duplex IEC958.

Hope it works for you too !

Cheers

---

### Post by RussianNeuroMancer on 2012-06-27
New Flash plugin 11.3 (part of Chrome 20) works pretty bad for me with E-Mu 0204. When I playback audio in some music player, and open page (in Chrome) with Flash content at the same time, audio become crackling until I stop playback and terminate flash plugin (or close the Chrome). The other workaround is move audio channels from E-Mu to integrated audio adepter (or to HDMI audio output) in pavucontrol.

Looks like this Flash update expose some deep ALSA bug (or maybe PulseAudio, but I really doubt in this). With 11.2 In Firefox this bug is not reproducible.

So, anyone experience same issue?

---

### Post by RussianNeuroMancer on 2012-07-04
> **RussianNeuroMancer said:**
> New Flash plugin 11.3 (part of Chrome 20) works pretty bad for me with E-Mu 0204.Looks like this is not issue with driver, but problem with Flash 11.3 PPAPI. There is big problems with audio playback in new PPAPI Flash 11.3 even on Windows. Example: [https://code.google.com/p/chromium/issues/detail?id=134193](https://code.google.com/p/chromium/issues/detail?id=134193)

---

### Post by pagingmrherman on 2012-11-06
Has anybody ever got this thing to record at 24/192?  Mine plays back 24/192 flac files w/ no problems and it can record at 24/96 by using the following command:
  arecord -f S24_3LE -c2 -r 96000 -D hw:1,0 >test2496.wav

But, if I try this command:
  arecord -f S24_3LE -c2 -r 192000 -D hw:1,0 >test24192.wav

I get nothing but static. 

I've read that you have to use the windows driver to set the sample rate.  Is this true??  If this can play at 192khz I'd think that _somehow_ it could record...

PW

P.S. This was tested using Ubuntu 12.10 which has alsa 1.0.25

---

### Post by thyraios on 2012-11-08
Tested 24/96 (worked) and 24/192 (didn't work)
I also found out (I don't do much recording and usually stick with 41.1) that jack uses ["SND_PCM_FMT_S32_LE, which is the format used by all current 24 bit audio cards except for some USB interfaces that actually use 24 bits rather than 24-packed-in-32-bits."]("http://linux-audio.com/jack/") does that affect any of you (like when recording in ardour)?

---

### Post by pagingmrherman on 2012-11-08
Jack sits on top of alsa so that really has nothing to do with the problem.  The is issue is with the alsa driver itself.

If arecord doesn't work at 192khz, then NOTHING is going to work - not jack, not pulseaudio, not sox, not <insert software here>.  ALL that stuff sits on top of alsa.  It's kind of like saying "hey my telephone doesn't work" when you don't even have dial tone when you pick up the line.

On a more positive note though, I did install the very last 0404 driver ever released from creative labs onto a Windows Vista laptop (I feel sooo dirty), upgraded the firmware to ver8.??, and was able to record at 24/192 using audacity with the directsound drivers.   So this thing *can* record at 192khz but it is a 100% proprietary solution.  

Now, from what I can understand, in the windows world, directsound has been deprecated by MS and now sits on top of some other layer of software.  HOWEVER, there are also some OTHER drivers called ASIO drivers that are similar to alsa in the linux world, that give you direct low-level access to the sound card itself.  

Soooo, based on this information, *I think*, to truly get 24/192 recordings from this sucker, you have to (in Windows) 

1) have an ASIO driver installed for your sound card (this may or may not be included with the driver that comes from creative labs)
2) capture sound using some software that uses the ASIO interface


I know this is a super long winded post but I've been trying to figure out what's the cheapest possible way to record high-quality 24/192 digital audio for taping live music.  And from what I can tell, a used E-MU 0404 is *ALMOST* there.  If I have to use windows, I guess I will but it would be much simpler if this thing worked with linux.  Or, maybe I'll settle for 24/96 like everyone else.  

I know it's insane to even want to record at 24/192 but hey, who cares, disk space is cheap and if it's good enough for Neil Young, it's good enough for me.  


PW

---

### Post by pagingmrherman on 2012-12-03
OK, I have confirmed that there is no way to record 24/192 w/ linux and the e-mu 0404.  BUT, I did get it to record 24/192 on a vista laptop by installing the latest drivers, compiling ASIO support into audacity and finally, then I can export 24/192 wav and/or flac files.  Not elegant but it works.

PW

---

