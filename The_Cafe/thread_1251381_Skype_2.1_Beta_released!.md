---
title: "Skype 2.1 Beta released!"
date: 2009-08-27
forum: The Cafe
---

### Post by Jay_Bee on 2009-08-27
And it works with pulseaudio :guitar:
[http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/)

---

### Post by FuturePilot on 2009-08-27
:o:o:o:o:o:o IT'S ABOUT TIME.
Going to test it now.

---

### Post by credobyte on 2009-08-27
> 

[LIST]
[*]1 Ghz processor or faster.
[*]256 MB RAM.
[/LIST]
:lolflag:

---

### Post by Ric_NYC on 2009-08-27
> **Jay_Bee said:**
> And it works with pulseaudio :guitar:
[http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/)

Thanks.

---

### Post by LowSky on 2009-08-27
sweet, hopefully my lenovo S10 works this time around without me having to pull my hair out

---

### Post by Regenweald on 2009-08-27
[http://www.skype.com/go/getskype-mid](http://www.skype.com/go/getskype-mid)

Got this link in another thread. Has anyone tested the two for differences ? Or has the above simply been released as an incremental 2.*** release ?

---

### Post by upptown on 2009-08-27
Tried it.  Yep, Pulse works but now my bluetooth headset doesn't.  In fact the audio settings tab doesn't have any options other than Pulse audio server (local).  Any ideas?  Interestingly, revert back to 2.0 and the headset works flawlessly.  I should add that I had no issues getting 2.0 to work with bluetooth.  I running 9.04 on a HP Pavilion dx6000.

---

### Post by brookie on 2009-08-27
I just installed it w/o uninstalling the old version first. Audio works, but can't change settings as mentioned. No problem. Test video failed. Just green garbled screen. 

Had to launch it with bash script for the preload lbv4l workaround found in the forums:

#!/bin/bash
sleep 2
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

Video works with this on my Logitech Quickcam Messenger camera.

---

### Post by credobyte on 2009-08-27
Pulse works just fine, however, I don't see any big changes. Yes, some new chat features ( new @ Linux version ), but .. I'm not sure if it's worth a try ( already uninstalled ).

---

### Post by neoforest on 2009-08-27
2.1.0.47 installed today on a 9.04 Jaunty that did not have any previous Skype installed. PulseAudio is the only choice in sound config window.

Tried it with Logitech Pro 9000 USB Camera/Microphone...
Drumroll...

Microphone does not work.

I plugged an older headset/microphone into sound card...
It worked for one call but not on subsequent (3-4) calls.

---

### Post by binbash on 2009-08-27
Pulseaudio works great, overall it is a nice release.

---

### Post by Phreaker on 2009-08-28
I can't believe it, but it's true! Can somebody test, because I don't have Ubuntu atm
[http://www.skype.com/intl/en/download/skype/linux/](http://www.skype.com/intl/en/download/skype/linux/)

---

### Post by HappinessNow on 2009-08-28
I don't generally use Skype but it looks very nice.

---

### Post by kirsis on 2009-08-28
Thanks for the heads up, I'm downloading it now. :smile:

---

### Post by Phreaker on 2009-08-28
I'm going to wait for your response : )

---

### Post by Jay_Bee on 2009-08-28
For people saying they can't configure devices, please check the release notes - [https://developer.skype.com/LinuxSkype/ReleaseNotes#head-3f52da06443fa3fab9e439904758c5a03a5e41f8](https://developer.skype.com/LinuxSkype/ReleaseNotes#head-3f52da06443fa3fab9e439904758c5a03a5e41f8)

---

### Post by kirsis on 2009-08-28
Havent tested audio/video quality (and likely wont for some time as I only use that when my girlfriend is out of town), but typing indicator and message editing = fixed (I always considered the absence of these features on Linux as bugs, not missing features :))

Cant comment on any other possible new features (such as sms sending, which is supposedly included), as I dont use them.

---

### Post by mrgnash on 2009-08-28
Crashtastic!

---

### Post by Rackstar on 2009-08-28
Runs perfectly now!

CPU drop of 98% :D

---

### Post by wieman01 on 2009-08-28
Ah, that's exciting. Downloaded it and testing it right now.

---

### Post by shiva.n on 2009-08-28
Can someone who has tested it give some more information?
 
1. If pulseaudio is the only option, what about those who have uninstalled pulseaudio?
 
2. My curent install of Skype (version before 2.1), works on ALSA, but cant use any other sound applications. If I choose pulseaudio, CPU usage hits the roof in a few minutes. Can someone comment on the CPU usage with the new version, especially when using other sound applications.

---

### Post by wieman01 on 2009-08-28
> **shiva.n said:**
> Can someone who has tested it give some more information?
 
1. If pulseaudio is the only option, what about those who have uninstalled pulseaudio?
 
2. My curent install of Skype (version before 2.1), works on ALSA, but cant use any other sound applications. If I choose pulseaudio, CPU usage hits the roof in a few minutes. Can someone comment on the CPU usage with the new version, especially when using other sound applications.
Hello, 

1. It also works with esound, I don't use Alsa at the moment.
2. CPU usage is just fine. Usage stays well below 30% on my 5 year old PC.

---

### Post by spodesabode on 2009-08-28
> **neoforest said:**
> It worked for one call but not on subsequent (3-4) calls.

Exactly the same problem on Ubuntu Jaunty 64-bit. One phone call and then it stops. Restart the pulseaudio daemon and then restart skype and I can make another call.

Other than that - huge improvement!

---

### Post by hanzomon4 on 2009-08-28
I had to install PA on Kubuntu and it works but capture does not work. When I had a Ubuntu jaunty install with kubuntu-desktop PA worked fine.

Fixed

---

### Post by rajeev1204 on 2009-08-28
woohoo 64 bit version is available!

Off to test this :)

---

### Post by Simian Man on 2009-08-28
I have been using this for a while now (it has been available, they just now updated their download page).  It is *much* better than the old version in every way.  I'm also glad the download no longer says Fedora 6 or 7.  That was just ridiculous :).

---

### Post by hotweiss on 2009-08-28
About time...

---

### Post by spongypants23 on 2009-08-28
Will this work on Jaunty even though there's only Hardy and Intrepid packages?

---

### Post by FuturePilot on 2009-08-28
> **spongypants23 said:**
> Will this work on Jaunty even though there's only Hardy and Intrepid packages?

Yes. It says 8.10**+** meaning 8.10 and above. And I've already installed it on Jaunty and it works fine.

---

### Post by gradinaruvasile on 2009-08-28
> **shiva.n said:**
> Can someone who has tested it give some more information?
 
1. If pulseaudio is the only option, what about those who have uninstalled pulseaudio?
 
2. My curent install of Skype (version before 2.1), works on ALSA, but cant use any other sound applications. If I choose pulseaudio, CPU usage hits the roof in a few minutes. Can someone comment on the CPU usage with the new version, especially when using other sound applications.

It works with alsa on jaunty. I am using it. 
I tried with pulseaudio on karmic, but thats a mess. It doesnt work. But pulseaudio is really messed up in karmic so...

Look out for video issues. If u have a webcam that worked with the previous version and in 2.1 get green image or static, you migh try this:

[http://forum.skype.com/index.php?showtopic=411441&st=0&gopid=1886611&#entry1886611]("http://forum.skype.com/index.php?showtopic=411441&st=0&gopid=1886611&#entry1886611")

---

### Post by diablo75 on 2009-08-28
... I've been using skype for a while and I was kind of under the impression that it already worked with pulse audio (it's what I have 2.0 configured to use for my output sounds; I do still have to set it to use "HDA ATI SB (hw:SB,0)" for my input (microphone).  But yeah, been using pulse as an output for quite a long time now...

Are there any other new features worth mentioning besides the "new" pulse support?

---

### Post by jbernardo on 2009-08-28
For me it is working on karmic kubuntu-netbook lpia. Had to repackage it as I am running lpia instead of i386, but it works well, without pulseaudio.

---

### Post by RedSingularity on 2009-08-28
Everything looks good except my user icons.  I could never get them to show up for some reason.  Both my own and people on my friends list.

---

### Post by hotweiss on 2009-08-28
Does anyone have solution for the microphone problem?

---

### Post by Ric_NYC on 2009-08-28
> **hotweiss said:**
> Does anyone have solution for the microphone problem?

That's something... The users should not fix software problems. Don't they test the program before releasing it to the public?

---

### Post by hotweiss on 2009-08-28
Ok, I got the microphone working by following these steps:

1. exit skype

2. sudo apt-get install pavucontrol

3. pulseaudio --kill

4. pavucontrol

5. start skype

6. make a test call with pavucontrol on

7. your mic should for some reason magically work now

---

### Post by potam on 2009-08-29
It works!!! Jaunty, 4 GHZ CPU, 1 GB RAM, 20% CPU usage during call (prev. was 100% in both core). Just tested the sound, I don't need video feature.

---

### Post by meho_r on 2009-08-29
> **Shadow121 said:**
> Everything looks good except my user icons.  I could never get them to show up for some reason.  Both my own and people on my friends list.

Try with skype static.

---

### Post by karimone on 2009-08-29
I'm sorry, i really feel stupid, but I can't install skype on ubuntu 9.04. I get an error about overwriting a file "CallConnecting.wav"

Any help?

---

### Post by JillSwift on 2009-08-29
> **karimone said:**
> I'm sorry, i really feel stupid, but I can't install skype on ubuntu 9.04. I get an error about overwriting a file "CallConnecting.wav"

Any help?
Remove any prior installation first. (And fear not, your settings will live unless you specify complete removal.)

---

### Post by karimone on 2009-08-29
> **JillSwift said:**
> Remove any prior installation first. (And fear not, your settings will live unless you specify complete removal.)

Thanks a lot! Now works and skype is really awesome now.

---

### Post by wolf4914 on 2009-08-29
Thanks a lot! That helped in my case

---

### Post by samuraitor on 2009-08-30
I have a logitech usb headset which does not work in skype 2.1, but it perfectly worked  in the non-beta skype.

In skype, under sound devices, the only option I get to configure is pulseaudio server (local).

How can I add my usb headset to support it ?

---

### Post by matthewbpt on 2009-08-30
> I have a logitech usb headset which does not work in skype 2.1, but it perfectly worked in the non-beta skype.

In skype, under sound devices, the only option I get to configure is pulseaudio server (local).

How can I add my usb headset to support it ?

If you install the padevchooser package from synaptic and then run it (it'll appear in the Multimedia and video menu) you'll get a new tray applet that loks like a heaphone plug. When your headset is plugged in left click on the icon and click 'Volume Control.' Then in the output devices tab you should see your headset. If you click on the arrow next to your headset you can change it to 'default' so pulse will use it for sound output. Then if you go to the Input tab you can also set its microphone as the default input in the same way, then skype should use it when pulseaudio is selected as the output device. Also when you unplug it the default will automatically change back to your other onboard sound card, and I think when you plug it in the default will change back to your headset (unless you choose to change its default setting later).

---

### Post by kostkon on 2009-08-30
> **matthewbpt said:**
> If you install the padevchooser package from synaptic and then run it (it'll appear in the Multimedia and video menu) you'll get a new tray applet that loks like a heaphone plug. When your headset is plugged in left click on the icon and click 'Volume Control.' Then in the output devices tab you should see your headset. If you click on the arrow next to your headset you can change it to 'default' so pulse will use it for sound output. Then if you go to the Input tab you can also set its microphone as the default input in the same way, then skype should use it when pulseaudio is selected as the output device. Also when you unplug it the default will automatically change back to your other onboard sound card, and I think when you plug it in the default will change back to your headset (unless you choose to change its default setting later).
Or they can just right-click on *Skype*'s audio stream in the *Applications* tab and select *Move Stream...* and in the list that will appear select their headset. This will send the sound coming from *Skype* to the headset. All other sounds will continue to play from the sound card.

---

### Post by Paqman on 2009-08-31
> **hotweiss said:**
> Ok, I got the microphone working by following these steps:

1. exit skype

2. sudo apt-get install pavucontrol

3. pulseaudio --kill

4. pavucontrol

5. start skype

6. make a test call with pavucontrol on

7. your mic should for some reason magically work now

I'm getting the exact same. Strange.

---

### Post by karimone on 2009-09-01
Anyone found any delay during the calls with the new skype?

---

### Post by nullrend on 2009-09-04
> **hotweiss said:**
> Ok, I got the microphone working by following these steps:

1. exit skype

2. sudo apt-get install pavucontrol

3. pulseaudio --kill

4. pavucontrol

5. start skype

6. make a test call with pavucontrol on

7. your mic should for some reason magically work now

I had already installed pavucontrol when I followed this great HOWTO: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) . Here's what ended up happening:
1. Exit Skype
2. Kill pulseaudio with "$ pulseaudio --kill"
3. When running pavucontrol the application crashed. Pavucontrol is PulseAudio's volume control.

Since I couldn't get the thing to run, nor PulseAudio to restart, I rebooted. After reboot:
1. Ran pavucontrol
2. Started Skype
3. Did a test call. It worked.

I guess I'll have to keep pavucontrol open all the time...

Using Ubuntu 8.10 x86_64

---

### Post by limegreenpatato on 2009-10-01
Ok. so i have the same problem with skype where my mic isn't working.  So i installed PulseAudio Volume control and i set my mic as default in the input devices....when i talk into it, it shows the volume bar moving up and down.  But when i go to make a call with skype it still doesn't pick up any sound.  Does the test call thing actually work??

anyone have any ideas?  thanks.

---

### Post by Auslegung on 2009-10-01
So far (about 20 minutes), Skype hasn't crashed on me nor resorted to eating up over 50% of my computer resources.  It actually idles at about 2-5%, but when speaking it goes to 20-30%, which is ok by me.  This is the longest it's ever worked without problems, since I updated to 9.04.

This may be a placebo effect, but I think the sound is clearer, too.

---

### Post by ghostwriter78 on 2009-10-21
Hi all,

unfortunately, skype 2.1 doesnt work for me. (ubuntu 9.04)

I use usb headset (logitech) for voice and loudspeakers for ringing.
Had to change in skype 2.0 away from pulseaudio because of 100%cpu problem.
Everything worked fine for months.

Now after update to 2.1 skype is unusable!
I cant get usb headset to be configured or accessed by pulseaudio, and cant change from pulseaudio to alsa.

Some suggest that pulseaudio should be removed, but when trying to do so, synaptic forces me to remove also ubuntu-desktop! that cant be right.

Tried also isntalling PA manager, but there is nothing to manage except volume. cant find any way to select which device to use.

how can i do to get either the previous skype running, or to fix the config issue. Please not i need to run ringing on speaker and voice on headset.

kind regards
Tibor

---

### Post by Auslegung on 2009-10-21
Ghostwriter, you should be able to simply sudo apt-get remove, or sudo apt-get purge skype.  Then, if you install it from sudo apt-get install skype, or from synaptic, I think it'll be the old 2.0, not beta.

Skype was working great for a couple of weeks, but recently every phone call has incredible static and lag, as if I'm calling on a 56k connection.  I'm in Korea with 45mbps download and 15mpbs upload, so I doubt that speed is the issue.  When I use Skype on my XP partition it works just fine.  Can anyone else confirm this?  Running it in terminal tells me nothing.  btw, at first it was only phone calls to my one friend, so I assumed it was a connection issue between VoIP and his company, but in the past week or so it has gotten so I can't understand anyone I call.  I freakin hate Windoze, but until these sort of issues go away (and I know this one isn't even Linux's fault), I can't jettison it.

---

### Post by benibuntu on 2009-11-04
> **Auslegung said:**
> Ghostwriter, you should be able to simply sudo apt-get remove, or sudo apt-get purge skype.  Then, if you install it from sudo apt-get install skype, or from synaptic, I think it'll be the old 2.0, not beta.

Skype was working great for a couple of weeks, but recently every phone call has incredible static and lag, as if I'm calling on a 56k connection.  I'm in Korea with 45mbps download and 15mpbs upload, so I doubt that speed is the issue.  When I use Skype on my XP partition it works just fine.  Can anyone else confirm this?  Running it in terminal tells me nothing.  btw, at first it was only phone calls to my one friend, so I assumed it was a connection issue between VoIP and his company, but in the past week or so it has gotten so I can't understand anyone I call.  I freakin hate Windoze, but until these sort of issues go away (and I know this one isn't even Linux's fault), I can't jettison it.

Have the exact same problem here: after the update from ubuntu 9.04 and skype 2.0 to 9.10 and 2.1 beta, it became totaly unusable. I'm using the version provided in medibuntu repositories, but the same happens with the one downloaded from the site.

It's probably something related to pulseaudio, wich is also an anoyance in this 2.1. With 2.0 from the old jaunty, I was able to choose between pulse or other devices in skype menu, wich is very important to me as I have skype usb headsets and I also need the ringing on other device (plugw, speakers, etc). Now only pulse is available and we trust it's solved in next versions, as many told.

I've tried skype-common and skype-static packages, the same lag. Can anyone confirm that this is a pulseaudio related issue? I've tried to look ubuntuforums as well.

Does anyone know where to find a 2.0 version? I use skype as my landline phone and the lag (+ the pulse audio non-separation of ringing/headset) is killing. I need to have at leas a temporary sollution and don't want to downgrade ubuntu because of one program.

---

### Post by yanns on 2009-11-16
[http://download.skype.com/linux/skype-debi...0.72-1_i386.deb]("http://download.skype.com/linux/skype-debi...0.72-1_i386.deb")To downgrade your skype installation

I have the same lag too. I hope we can find a solution, because, otherwise, I find the integration with pulse very good. I could switch my input / output without any problems. That's cool.

---

### Post by Francewhoa on 2010-03-14
Same here. Skype 2.1 installer doesn't work with Ubuntu 8.04 LTS desktop. The following worked for me [http://ubuntuforums.org/showpost.php?p=8919096&postcount=6](http://ubuntuforums.org/showpost.php?p=8919096&postcount=6)

---

