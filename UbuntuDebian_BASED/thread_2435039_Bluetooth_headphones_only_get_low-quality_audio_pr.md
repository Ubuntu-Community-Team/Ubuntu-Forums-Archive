---
title: "Bluetooth headphones only get low-quality audio profile"
date: 2020-01-15
forum: Ubuntu/Debian BASED
---

### Post by p5music on 2020-01-15
I am using a Lenovo G50 notebook with KDE Neon (Ubuntu 18.04).
I am able to connect my bluetooth headphones Panasonic RP-HF400B.
But I see only one audio profile associated to it (headset with mic).
I need the A2DP profile so I can listen to music and video in high quality audio.
Also in pavucontrol there is no quality audio sink.
Is it possible to have it on my system?
Thanks in advance.

---

### Post by CelticWarrior on 2020-01-15
Mine (and I think in all similar situations) actually has A2DP as the default. Never tried switching to HFP because with the Ubuntu notebook I don't use it for voice communications, just to listen to music and videos.

Maybe try deleting and pairing again?

I could be also a problem with the Bluetooth device itself, early specifications didn't support A2DP, but a Lenovo G50 isn't that old, I think.

---

### Post by slickymaster on 2020-01-15
*Thread moved to  [I]"Ubuntu/Debian BASED*".

---

### Post by jimmyrus on 2020-01-15
> **p5music said:**
> I am using a Lenovo G50 notebook with KDE Neon (Ubuntu 18.04).
I am able to connect my bluetooth headphones Panasonic RP-HF400B.
But I see only one audio profile associated to it (headset with mic).
I need the A2DP profile so I can listen to music and video in high quality audio.
Also in pavucontrol there is no quality audio sink.
Is it possible to have it on my system?
Thanks in advance.
Seems to be with the headphones since its paring as a headset. Bluetooth will ask the device what it is and automatically hook
up to it. and if pavucontrol won't show a2dp, something is definitely wrong with either the installation of that or with your hardware.

---

### Post by CatKiller on 2020-01-15
> **p5music said:**
> 
Also in pavucontrol there is no quality audio sink.

It's not at the PulseAudio stage, it's at the Bluetooth pairing stage that the devices negotiate which profile to use. Because Bluetooth is low-bandwidth and the standard started a long time ago you have to choose between using a microphone and having crappy audio or good audio and no microphone. When you pair headphones with a microphone, like yours, the Bluetooth stack defaults to being able to use the microphone, which means crappy audio quality. 

You can choose a different profile at the time you pair your devices, and the Bluetooth stack will remember your selection next time you connect those devices. There is also a configuration option somewhere (probably in a text file) to pretend that the headset profile was never created.

---

### Post by CelticWarrior on 2020-01-15
No, that's not the experience I have and I've used several Bluetooth headphones already.
The bluetooth pairing process negotiates and stores all the profiles available for any given device. With headsets most support both A2DP and HFP but the default profile used has always been A2DP. Then, if HFP is needed it either switches automatically (like with Android) or the user has to manually change it in sound settings.

The OP seems to be complaining about not being able to select A2DP. This can have few, very few causes. One that I already mentioned - unsupported by the Bluetooth card - can be ruled out because the notebook isn't so old (A2DP started with v2.x). Next is a drivers problem and/or it's not correctly identifying the paired headphones (identifying it as a simple mono headset)

---

### Post by jimmyrus on 2020-01-16
> **CelticWarrior said:**
> No, that's not the experience I have and I've used several Bluetooth headphones already.
The bluetooth pairing process negotiates and stores all the profiles available for any given device. With headsets most support both A2DP and HFP but the default profile used has always been A2DP. Then, if HFP is needed it either switches automatically (like with Android) or the user has to manually change it in sound settings.

The OP seems to be complaining about not being able to select A2DP. This can have few, very few causes. One that I already mentioned - unsupported by the Bluetooth card - can be ruled out because the notebook isn't so old (A2DP started with v2.x). Next is a drivers problem and/or it's not correctly identifying the paired headphones (identifying it as a simple mono headset)
yep thats kinda what I said too about it being a headphone issue but it could also be a flaky bluetooth device. OP do you have any problems with bluetooth in general? Any other issues? And are you using the stock bluetooth that came with that box or did you add another?

---

### Post by p5music on 2020-01-16
@[**[COLOR=#000000]jimmyrus[/COLOR]**]("https://ubuntuforums.org/member.php?u=2133269")
I am using the onboard bluetooth system.
My headphones set worked on another notebook in A2DP mode, with Linux or Windows, although the connection was soon interrupted and fallbacked to low quality sink.
With current Lenovo notebook bluetooth mouse MS3600 is doing very well, no delays, no falling into sleep mode or energy save mode.
I have to say on this Lenovo with Windows10 sound was heavily stuttering.
On this KDE system, bluetooth sound is not stuttering but it is low-quality because of the A2DP option is totally missing.

---

### Post by jimmyrus on 2020-01-16
> **p5music said:**
> @[**[COLOR=#000000]jimmyrus[/COLOR]**]("https://ubuntuforums.org/member.php?u=2133269")
I am using the onboard bluetooth system.
My headphones set worked on another notebook in A2DP mode, with Linux or Windows, although the connection was soon interrupted and fallbacked to low quality sink.
With current Lenovo notebook bluetooth mouse MS3600 is doing very well, no delays, no falling into sleep mode or energy save mode.
I have to say on this Lenovo with Windows10 sound was heavily stuttering.
On this KDE system, bluetooth sound is not stuttering but it is low-quality because of the A2DP option is totally missing.
Kinda answered your own question didnt you? pointing back to junky headphones isnt it? I mean if they fail on another system in both linux and windows and bluetooth
works fine for everything else but your headphones, it seems pretty obvious. And of course sound doesn't stutter with low quality why would it? Pushing a ton less data
through to get low quality audio. 

Get a replacement set of headphones or get better headphones.

---

### Post by p5music on 2020-01-17
If it is useful to know, I can point out that the bluetooth headphones are working perfectly with my Android smartphone.
Using some random Linux distros on the Asus S300CA laptop I could experience prolonged periods of acceptable functioning in A2DP mode, although the system used to kick that sink out when it would.
Is it possible to force the A2DP option in some config files (although I do not want to break my two-day fresh system)?

---

### Post by jimmyrus on 2020-01-17
> **p5music said:**
> If it is useful to know, I can point out that the bluetooth headphones are working perfectly with my Android smartphone.
Using some random Linux distros on the Asus S300CA laptop I could experience prolonged periods of acceptable functioning in A2DP mode, although the system used to kick that sink out when it would.
Is it possible to force the A2DP option in some config files (although I do not want to break my two-day fresh system)?
Not really helpful to know since your phone isnt doing the same things your pc does and is using a different os. Don't matter if you like the answer or not, but everything points to your headphones. The
fact it does the same thing on any pc using different hardware and os from win to linux, and it behaves the same way. celticwarrior said that the device tells the system what it can do and it works. your
headphones are either defective or junk. you can try to put a .asoundrc file out there to do things but that aint gonna change junk hardware. And if your walking around your room with headphones on
and it stutters but have yoru phone in your pocket that explains alot.

---

