---
title: "UNR on an Asus eeePC 1005PEB is a complete mess."
date: 2010-01-24
forum: Ubuntu Moblin Remix
---

### Post by JanHammer on 2010-01-24
As far as I know, the 1005PEB is identical to the 1005PE (confirmed), yet UNR seems completely thrown off by it. I'll try to describe the problem ...

It boots from the USB drive just fine, everything seems to be running smooth and installing it has no issues whatsoever. Installation completes, I restart, boot into the new installation of Ubuntu... and the mouse and keyboard aren't working. They don't do a thing. The caps-lock doesn't even toggle. So, I do a hard reboot just thinking this might be some kind of bizarre one-time thing and I was temporarily right. So, I begin to do some exploring of UNR and see that the home screen is incredibly slow; almost unusable. While this is going on I notice these things:

1: I have no sound
2: There's a kernel error at the top
3: Wifi is really funky (but that's not a big deal because there's a fix on the hardware page for UNR)

After realizing something is really not right here I decide to try to do updates only to have to fight with the wifi for it. So after getting tired of fighting the flaky wifi I install the fix for it, which brings up a prompt saying I need to restart for them to take effect. Sure, why not?

Well I reboot and I have no mouse or keyboard control again.

Things I've done to try to fix this: 

[LIST=1]
[*]Googling for hours
[*]Reinstalling UNR at least 3 times
[*]Redoing the USB drive image twice
[*]Self-immolation
[*]EDIT: Installing windows 7
[/LIST]

---

### Post by chadraytay on 2010-01-25
It's not just you. I posted same thing 4 days ago...

---

### Post by CharlesBasengaKiyanda on 2010-02-04
Same symptoms except for the wifi (did all the updates without problems) on a 1005PE.

Try to boot into UNR without the AC plugged in. I read on a bug report that in that case, the keyboard and mouse work. Worked for me once though I didn't try to replicate that behaviour several times.

I noticed the interface was completely unusable as it was too slow to respond and I get the kernel panics. Everything was fine with the live-usb, so I don't quite understand what's wrong. I've basically done everything you list except installing windows 7 (I didn't erase it to start with.) I'm at the point where I'm downloading the latest daily build of lucid to try that.

---

### Post by JanHammer on 2010-02-05
> **CharlesBasengaKiyanda said:**
> Same symptoms except for the wifi (did all the updates without problems) on a 1005PE.

Try to boot into UNR without the AC plugged in. I read on a bug report that in that case, the keyboard and mouse work. Worked for me once though I didn't try to replicate that behaviour several times.

I noticed the interface was completely unusable as it was too slow to respond and I get the kernel panics. Everything was fine with the live-usb, so I don't quite understand what's wrong. I've basically done everything you list except installing windows 7 (I didn't erase it to start with.) I'm at the point where I'm downloading the latest daily build of lucid to try that.

Yeah the fact that the live boot of it works perfect is what I don't understand the most.

---

### Post by CharlesBasengaKiyanda on 2010-02-05
I just did a BIOS update instead of installing the daily lucid and it solves all the problems. No multitouch (yet), but I'll figure this out later. wifi seems fine so far. Keyboard and mouse works. Sound (out) works. cheese recognizes the camera.microphone may still not be recognized but I'd read something somewhere about fixing that. Interface is as responsive as expected. I'm happy so far!

---

### Post by CharlesBasengaKiyanda on 2010-02-06
ok, this is all on my 1005PE, but the behaviour was essentially the same. My steps were the following:

initially installed UNR 9.10 and the problematic behaviour occured. I did:

1- bios update (resolved most of the problems except the non-working microphone. I also started noticing a flaky wireless.)
2- installed backports:
linux-backports-modules-wireless-karmic-generic
linux-backports-modules-alsa-karmic
solved the wireless issue, but not the sound
3- went to system -> sound -> hardware. Under 'Profile', I selected 'Analog surround 4.0 output + Analog stereo input'. microphone now works in recorder, I can play sounds as well (tested with movie player). I didn't check if skype sees the microphone, but I would imagine so.

I haven't tested the multitouch. As far as I can tell, that's the last thing I would have to fix, but I'm more used to the side-scrolling, so I'm leaving it as is for now.

Hope this helps someone.

[UPDATE: Just checked with skype and it either doesn't work or it does but the input level is really, really low. Very strange.]

---

### Post by macabuntu on 2010-02-09
hey i downloaded the bios file and updater from asus but still cant figure out how to update the dang bios if you could tell me how to update the bios it would be awesome

---

### Post by silverdulcet on 2010-02-10
> **CharlesBasengaKiyanda said:**
> 
3- went to system -> sound -> hardware. Under 'Profile', I selected 'Analog surround 4.0 output + Analog stereo input'. microphone now works in recorder, I can play sounds as well (tested with movie player). I didn't check if skype sees the microphone, but I would imagine so.

[UPDATE: Just checked with skype and it either doesn't work or it does but the input level is really, really low. Very strange.]

If you want the microphone to function in skype and other sip/voice chat apps follow the tip here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/449855/comments/41]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/449855/comments/41")

1. Install linux-backports-modules-alsa-karmic-generic
2. Install pavumeter
3. Run pavucontrol, Select Input Devices tab, unlock the two microphone channels, then change one so that it is not the same level as the other one. I set one channel to 2% and the other to 95%. Then lock them again.

I've tested it with the Skype echo test and my sip account using empathy with telepathy-sofiasip. 

Not the ideal solution, but for now it works.

---

### Post by CharlesBasengaKiyanda on 2010-02-10
> **macabuntu said:**
> hey i downloaded the bios file and updater from asus but still cant figure out how to update the dang bios if you could tell me how to update the bios it would be awesome

I think there's a way to do this by essentially booting with a usb device attached, but I can't remember now. I updated it using the windows partition. Asus preinstalls on there a utility to update the bios. It was self-explanatory, quick and rather painless.

Am not at home right now, but I can check in the instruction manual when I get home. I think that's where I saw it.

---

### Post by CharlesBasengaKiyanda on 2010-02-10
> **silverdulcet said:**
> 
3. Run pavucontrol, Select Input Devices tab, unlock the two microphone channels, then change one so that it is not the same level as the other one. I set one channel to 2% and the other to 95%. Then lock them again.


Is the microphone actually stereo? I can't quite remember right now.

---

### Post by silverdulcet on 2010-02-10
> **CharlesBasengaKiyanda said:**
> Is the microphone actually stereo? I can't quite remember right now.

If you look at the bezel, there are two holes, on to the right of the webcam and on two the left passed the webcam led. The inputs on that control panel are called Left and Right Input as well. So it would seem that it is.

---

### Post by Despot on 2010-03-28
Hey guys,

Thanks for all your tips on getting UNR working. I was fortunate enough to not run into most of the mouse/keyboard issues, so I guess Asus is probably shipping out new units with the updated firmware.

One thing I haven't found a solution for--I can't connect to my wireless access point in UNR. It's using WEP encryption with a 128-bit ASCII key, and I can connect just fine when I'm running Windows 7 (Starter). In UNR, NetworkManager keeps prompting me for the key and never connects.

I can connect to other WAPs while running UNR, so I know the wireless is working to some extent under UNR. However, the other WAPs all use WPA.

I can connect to this WAP with other devices (iPhone, my older laptop running Ubuntu 9.04), so I'm reasonably sure it's a configuration issue for this particular wireless network adaptor in UNR. After Googling a bit, I've tried connecting manually through wpa_supplicant, with no luck. Here's the configuration I'm using:

```

network={
	ssid="spider"
	key_mgmt=NONE
	wep_key1="xxxxxxxxxxxxx"
}

```

The log is attached. The relevant line seems to be:

```

Authentication with 00:40:05:5b:9d:b1 timed out.

```

I also looked at the NetworkManager messages in /var/log/daemon.log, and the same thing seems to be happening:
```

Mar 28 16:23:10 min NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Mar 28 16:23:10 min NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar 28 16:23:13 min NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Mar 28 16:23:23 min NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Mar 28 16:23:23 min NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar 28 16:23:24 min NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Mar 28 16:23:26 min NetworkManager: <info>  wlan0: link timed out.
Mar 28 16:23:34 min NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Mar 28 16:23:34 min NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar 28 16:23:35 min NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Mar 28 16:23:45 min NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Mar 28 16:23:45 min NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar 28 16:23:46 min NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Mar 28 16:23:56 min NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Mar 28 16:23:56 min NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar 28 16:23:57 min NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Mar 28 16:24:05 min NetworkManager: <info>  wlan0: link timed out.
Mar 28 16:24:07 min NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Mar 28 16:24:07 min NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar 28 16:24:08 min NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Mar 28 16:24:11 min NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Mar 28 16:24:11 min NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Mar 28 16:24:11 min NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets

```

I'm not sure what to try next, does anyone have any pointers?

---

### Post by Despot on 2010-04-05
No ideas? I would really like to be running UNR on my netbook by default, but the lack of connectivity makes it sort of pointless to do so.

---

### Post by MonthOLDpickle on 2010-04-06
Did you try updating? Though I have a different netbook a friend used (Mini 9) I only ran into it being slow (which updating fixed) and his U300 dongle.

---

### Post by stuart.trusty on 2010-04-22
As a point of divergent experience, I just installed ubuntu-9.10-netbook-remix-i386.iso on the Eee PC 1005PEB and networking authenticated fine with a 128 bit WEP key.  Keyboard and mouse, etc. are all OK; I did update the firmware.  

Stuart Trusty
Linux Labs International, Inc.

** Correction, it is a 64-bit key.  I would have deleted my post on this account, but you can only Edit and not Delete as far as I can see lol

---

