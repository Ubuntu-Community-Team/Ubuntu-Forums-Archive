---
title: "Darter, no sound after update"
date: 2007-04-12
forum: System76 Support
---

### Post by jml on 2007-04-12
I don't know if this is a problem specific to my Darter, or to Ubuntu in general.  I had a completely functioning system for several weeks after getting my Darter, sound, movies, internet the works.  While I was experimenting with a digital music player, (SanDisk, Sansa e260) the update manager alerted me to new updates.  After I finished working with the sansa, I downloaded the updates.  The next time I turned on my computer, the little volume control applet was non-functional.  Now my Darter has no sound!  When I click on the volume icon, or try to use any sound application I get the following error message.  "No volume control or Gstreamer plugins/ or devices found."  I checked with Synaptic and all of the plug-ins are listed as being installed so I don't know if the problem rests with The sansa, (it shouldn't its set up as a removable mass storage device,) or with my configuring Sound Juicer to encode in mp3 format, or if the update from Ubuntu caused the problem?  Any thoughts would be appreciated because a silent laptop is a sad thing to behold.:( 

Joe

---

### Post by crichell on 2007-04-12
Hi Joe,

Run the System76 Driver (System > Administration > System76 Driver Installer).  Sound should be restored after you reboot.  Make sure you are connected to the internet before running the driver.

Carl

---

### Post by jml on 2007-04-12
Thanks for the quick reply, Carl.  I'll try it when I get home tonight.  I routinely connect by wireless and that still seems to be working ok.  For saftey, is it necessary to do this driver install with a wired connection?

Joe

ps, except for this glitch, the Darter has been a dream.  I have several of out IT tech's drooling over it.;)   jml

---

### Post by crichell on 2007-04-12
> For saftey, is it necessary to do this driver install with a wired connection?


No, wireless is fine.  I'm pretty sure running the driver will take care of it.

> ps, except for this glitch, the Darter has been a dream. I have several of out IT tech's drooling over it. jml

I love mine too :)

---

### Post by MarkID on 2007-04-12
Same here.  And still  no sound after after running the S76 Driver Installer and rebooting.

(Still love the Darter though.)

---

### Post by crichell on 2007-04-12
Hi Mark,

Can you open volume control?  Is there a line through the speaker or an error message when you try to open volume control?

Thanks, Carl

---

### Post by MarkID on 2007-04-12
> **crichell said:**
> Hi Mark,

Can you open volume control?  Is there a line through the speaker or an error message when you try to open volume control?

Thanks, Carl

There's a circle slash through the volume icon.  When I click on it, I get this message:

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

---

### Post by jml on 2007-04-12
That is one of the two error messages I got last night as well.  (I posted the other already.)  When I get home from work tonight, I'll check back with this forum thread if the driver reinstall soes not work for me.

Joe

---

### Post by crichell on 2007-04-12
Can you guys post the output of this command:

```
cat /proc/asound/version
```

We've tested the updates here and never lost sound - i.e. didn't have to run the driver.  Clearly something is amiss.  If anyone else has lost sound please post.

Thanks

---

### Post by Rotarychainsaw on 2007-04-12
cat /proc/asound/version

Advanced Linux Sound Architecture Driver Version 1.0.14rc2.
Compiled on Mar 23 2007 for kernel 2.6.17-11-generic (SMP).

cat /proc/asound/cards 

--- no soundcards ---

---

### Post by crichell on 2007-04-12
thanks rotary - nice avatar

What version of the System76 driver do you have (check in Synaptic).  The alsa version looks off.

---

### Post by Rotarychainsaw on 2007-04-12
Driver version 1.9.9

I must say, when I run the driver from a terminal it looks like it doesn't finish. Some sound stuff looks like its getting compiled from source, but it ends with an error. I was told that was normal though.

---

### Post by crichell on 2007-04-12
What error is the driver ending with?

---

### Post by Rotarychainsaw on 2007-04-12
I know make is usually pretty verbose, so here is the last few lines. The driver installer says to reboot like everything went well.

make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
/opt/system76/system76-driver/src/system76-sound/acore/pcm_native.c: At top level:
/opt/system76/system76-driver/src/system76-sound/acore/pcm_native.c:3607: error: conflicting types for ‘snd_pcm_f_ops’
/opt/system76/system76-driver/src/system76-sound/include/sound/pcm.h:450: error: previous declaration of ‘snd_pcm_f_ops’ was here
make[3]: *** [/opt/system76/system76-driver/src/system76-sound/acore/pcm_native.o] Error 1
make[2]: *** [/opt/system76/system76-driver/src/system76-sound/acore] Error 2
make[1]: *** [_module_/opt/system76/system76-driver/src/system76-sound] Error 2
make: *** [compile] Error 2

---

### Post by crichell on 2007-04-12
That's definantly not ending correctly.

Run the following command:

```
sudo apt-get install build-essential linux-headers-`uname -r`
```

Let me know if those are already installed.  Try running the driver again.

---

### Post by Rotarychainsaw on 2007-04-12
Already installed.

---

### Post by crichell on 2007-04-12
Let's re-install the system76 driver and give it another shot.

```
sudo apt-get install --reinstall system76-driver
```

---

### Post by jarsin on 2007-04-12
I too am having this problem on a pangolin v2.  The sound icon has a circle with a line through it.  I tried all of the above steps and reinstalled the system 76 driver from the command line and still have the issue.  Any other ideas?

cat /proc/asound/version:
Advanced Linux Sound Architecture Driver Version 1.0.14rc2.
Compiled on Mar 21 2007 for kernel 2.6.17-11-generic (SMP).

---

### Post by MarkID on 2007-04-12
My results are virtually identical to those posted by Rotary.  I too tried reinstalling from the terminal and still no sound.  Please advise.

---

### Post by Rotarychainsaw on 2007-04-12
OK, got it working. I forced driver version 1.9.8 and then 1.9.7. I tried running both of those and I don't think they finished, but they might have installed whatever 1.9.9 needed. After re updating to 1.9.9 and installing, I get sound now. Yay!

---

### Post by MarkID on 2007-04-12
> **Rotarychainsaw said:**
> OK, got it working. I forced driver version 1.9.8 and then 1.9.7. I tried running both of those and I don't think they finished, but they might have installed whatever 1.9.9 needed. After re updating to 1.9.9 and installing, I get sound now. Yay!

Rotary, can you post an easy to follow operation for this fix?  Thanks.

---

### Post by Rotarychainsaw on 2007-04-12
I'll tell you what I did, but I don't give any guarantees haha. I'd wait for Carl to chime in as I might have had a different problem or something. 

Open synaptic
search for 76 and find the system76 driver
click on it and go up to the package menu, click force version.
Pick 1.9.8 and hit apply to downgrade
I ran the driver from a terminal to see what it did (type 'system76-driver')
I don't remember what it did, but I might have done it more than once.
Then I went back to synaptic and downgraded the driver again to 1.9.7
then I ran the driver installer again a couple times (I think it kept locking up)
Then I forced the 1.9.9 version again in synaptic 
and ran the driver installer one last time. 
It worked for some reason.

---

### Post by jml on 2007-04-12
Carl, your suggestion to me to run the System 76 Driver application worked.  My sound has been restored.  Thanks for the quick response and your obvious concern for customer support.

Joe

---

### Post by MarkID on 2007-04-12
> **Rotarychainsaw said:**
> I'll tell you what I did, but I don't give any guarantees haha. I'd wait for Carl to chime in as I might have had a different problem or something. 

Open synaptic
search for 76 and find the system76 driver
click on it and go up to the package menu, click force version.
Pick 1.9.8 and hit apply to downgrade
I ran the driver from a terminal to see what it did (type 'system76-driver')
I don't remember what it did, but I might have done it more than once.
Then I went back to synaptic and downgraded the driver again to 1.9.7t
then I ran the driver installer again a couple times (I think it kept locking up)
Then I forced the 1.9.9 version again in synaptic 
and ran the driver installer one last time. 
It worked for some reason.

Thanks.  I will wait for Carl, but I'll keep you operation in mind.

My problem wasn't with 1.9.9.  My Darter worked perfectly after installing 1.9.9.  My sound broke when I installed some other, more recent, updates.

---

### Post by Rotarychainsaw on 2007-04-13
Yeah, me too. My sound was working before and the 1.9.9 driver would give me those errors, but I think I saw a kernel update and that was when it stopped working.

---

### Post by crichell on 2007-04-13
Rotary, good work getting it rolling.  The following steps should result in the same fix:

```
sudo apt-get remove --purge system76-driver
```

You may see errors about directories not being empty.  Run the following command:

```
sudo rm -r /opt/system76
```

Clean re-install

```
sudo apt-get install system76-driver
```

Run the driver (System > Administration > System76 Driver Installer)

Reboot and you should be good to go.

---

### Post by MarkID on 2007-04-13
> **crichell said:**
> Rotary, good work getting it rolling.  The following steps should result in the same fix:

```
sudo apt-get remove --purge system76-driver
```

You may see errors about directories not being empty.  Run the following command:

```
sudo rm -r /opt/system76
```

Clean re-install

```
sudo apt-get install system76-driver
```

Run the driver (System > Administration > System76 Driver Installer)

Reboot and you should be good to go.

Yeah!  I have sound again!

Thanks to the community (Rotary and Joe), awesome support from S76 (thanks Carl), and a little technical knowledge on my part, we solved this problem.  That's what I love about Linux  -- and S76.

---

### Post by jarsin on 2007-04-13
> **crichell said:**
> Rotary, good work getting it rolling.  The following steps should result in the same fix:

```
sudo apt-get remove --purge system76-driver
```

You may see errors about directories not being empty.  Run the following command:

```
sudo rm -r /opt/system76
```

Clean re-install

```
sudo apt-get install system76-driver
```

Run the driver (System > Administration > System76 Driver Installer)

Reboot and you should be good to go.

Edit: I cant read directions.  Everything now works.  Thanks a lot!!

---

### Post by MorphWVUtuba on 2007-04-14
Hey all,

I have a Gazelle Value ordered in December and I had the same issue after the 2.6.17.1-11.37 kernel upgrade today.  Once I ran the s76 driver I had sound after the reboot, but neither "Fn+F6/F7/F8" nor the speaker mute button above the F2 key has any control over the mixer.  I changed the panel icon settings to control headphones, PCM, speakers, all with no change to the keyboard controls.  I tried the instructions that Carl posted to uninstall --purge the s76 driver & reinstall, but after running it & rebooting I still have the same symptom.:confused: 

Any thoughts/suggestions?

---

