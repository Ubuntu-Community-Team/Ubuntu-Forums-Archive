---
title: "Virtual Box Window 7, horrible sound."
date: 2009-01-16
forum: Virtualisation
---

### Post by Alfx on 2009-01-16
Everything else works just find.
I didnt find any other people complaining about this issue.

The sound on window 7 is horrible it stutters and has weird noise.(Like bad encoding or something)

It happens with pretty much every sound.

How do I fix this?

Thanks

---

### Post by HotShotDJ on 2009-01-16
Open virtualbox, but don't start the guest OS (windows 7).  Highlight the vm and then click on "Settings" in the VirtualBox tool bar.  Select Audio from the left panel.  Make sure "enable audio" is checked off (it probably is already or you wouldn't hear any sound at all).

Notice the "Host Audio Driver" and "Audio Controller" drop downs. Methodically experiment with these settings until sound is tolerable.  On my system using VirtualBox 2.1 on Ubuntu 8.10 Host with Windows Visa guest, Host Audio is set to PulseAudio and Audio Controller is set to ICH AC97 with good results.

---

### Post by Paqman on 2009-01-16
You could try switching the sound system that Virtualbox is using for that VM. Go into the options for the VM and try switching between Pulseaudio/OSS/ALSA and see what works.

Otherwise it's a Win 7 problem. It is Beta software after all.

---

### Post by HotShotDJ on 2009-01-16
> **Paqman said:**
> Otherwise it's a Win 7 problem. It is Beta software after all.That's a good point.  I was going to also suggest installing guest additions, but I wonder if that is possible with Windows 7.

---

### Post by Alfx on 2009-01-16
> **HotShotDJ said:**
> That's a good point.  I was going to also suggest installing guest additions, but I wonder if that is possible with Windows 7.

Yes it possible, Ive done it.
I tried switching between Pulseaudio/OSS/ALSA...
No luck, they all give me the same crapp audio.

><

---

### Post by inobe on 2009-01-17
uninstalling and reinstalling guest additions fixed any issue with sound in all platforms for what ever reasons.

---

### Post by HotShotDJ on 2009-01-17
> **inobe said:**
> uninstalling and reinstalling guest additions fixed any issue with sound in all platforms for what ever reasons.Alfx:  Did this work for you as well?

---

### Post by verlyn13 on 2009-01-18
Hello,

I had that same problem with WinXP on Vbox. I ended up resetting my sound card drivers and installing Pulseaudio with some help from Ubuntu Forum threads.  Then I selected Pulseaudio and it works much better.

I am also having a problem with Windows 7 on Vbox 2.1, but I have NO SOUND.  Win7 detects a "Multimedia Audio Controller" but it won't detect the correct driver (ICH AC97 with Pulseaudio) I've done a lot of reading on the internet and it looks like an uncommon problem. It seems that Win7 automatically detects and installs the right driver for everyone else.  

I've tried:
1) all combinations of drivers with ICH AC97 and SB16
2) reinstalling Win7 several times and checking "enable audio" and different times during installation
3) reinstalling guest additions several times
4) reinstalling Vbox 2.1 from repositories AND the website
5) looking for a generic ICH AC97 windows driver on the internet, difficult to find, and none work

Any help with this would be greatly appreciated,
Thanks

---

### Post by verlyn13 on 2009-01-18
Update:

I downloaded some realtek ac97 drivers for Vista (6285_Vista_APO_PG536.zip)
that windows 7 accepted, and the sound works but is scratchy and terrible sounding.

---

### Post by HotShotDJ on 2009-01-19
> **verlyn13 said:**
> I downloaded some realtek ac97 drivers for Vista (6285_Vista_APO_PG536.zip) that windows 7 accepted, and the sound works but is scratchy and terrible sounding.Under the audio settings in VirutualBox, underneath the Host Audio Driver drop-down menu, there should also be an Audio Controller drop-down.  On my set up, I can choose either the standard ICH AC97 controller or Soundblaster 16 controller.  I've never had any reason to switch them, but I suspect the issues listed in this thread may involve the AC97 driver.  Perhaps Windows 7 might have better support for the Soundblaster 16 controller.  (I have no way of testing this hypothesis myself... just throwing it out there as a possibility).

---

### Post by HotDogBunToo on 2009-02-09
> **HotShotDJ said:**
> Under the audio settings in VirutualBox, underneath the Host Audio Driver drop-down menu, there should also be an Audio Controller drop-down.  On my set up, I can choose either the standard ICH AC97 controller or Soundblaster 16 controller.  I've never had any reason to switch them, but I suspect the issues listed in this thread may involve the AC97 driver.  Perhaps Windows 7 might have better support for the Soundblaster 16 controller.  (I have no way of testing this hypothesis myself... just throwing it out there as a possibility).

I've been here before, the problem with the SoundBlaster 16 option is that Win7 does not recognize any sound device upon startup.  So I'm over here stuck with ICH AC97 as the sole option for device.  And as others noted, it is pretty scratchy.

---

### Post by HotShotDJ on 2009-02-10
> **HotDogBunToo said:**
> I've been here before, the problem with the SoundBlaster 16 option is that Win7 does not recognize any sound device upon startup.  So I'm over here stuck with ICH AC97 as the sole option for device.  And as others noted, it is pretty scratchy.Have you tried upgrading to version 2.1.2 of VirtualBox.  They have added Windows 7 support to that version, and maybe it has solved this problem.

See: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)  (I recommend that you follow the instructions for Debian-based Linux distributions.  You'll find them about half way down that page).

---

### Post by vgrisham on 2009-03-05
The Soundblaster16 setting doesn't work at all. 

This must be an issue with Virtualbox's support of Windows 7. I have a separate partition with Windows 7 and have no such issue. I also have Windows XP installed in Virtualbox with Alsa and ICH97 with no scratchiness. 

It's going to take time I guess.

---

### Post by rumpkin on 2011-02-27
I ended up installing the latest AC97 drivers which list Win7 support, ignored the rest and got the sound to work.  As previously posted the audio cuts and scratches.  I got it to happen much less frequently by bumping up the allocated memory for the Virtual Win7.  I haven't done anything extensive in testing other than watch a bunch of netflix through the virtual box but that seemed to help considerably.  Hope that helps until this gets fixed in future releases.

---

### Post by CharlesA on 2011-02-27
This thread is talking about virtualbox 2.1.2. The latest version is 4.0.4. You shouldn't have to install any entra drivers inside of Win7 to get the sound to work.

---

### Post by rumpkin on 2011-02-27
[I]This thread is talking about virtualbox 2.1.2. The latest version is  4.0.4. You shouldn't have to install any entra drivers inside of Win7 to  get the sound to work.

[/I]I just installed everything new and fresh three days ago and still had to go get the drivers for Win7 to recognize the sound device.  I'm still fairly new to this so perhaps I did something incorrectly but I just followed the general instructions and ran into the same issues listed above.

---

### Post by CharlesA on 2011-02-27
What version of VirtualBox are you using and which audio chipset do you have it set for?

I've been using it since 3.2 without any problems.

---

### Post by rumpkin on 2011-02-28
I am using 3.2...the version that you download through Ubuntu software center.  The only reason I found this forum in the first place was because when I installed win7 I had the same sound problems described.  I used a legit OEM copy of Win7 Home Edition if that makes a difference.

---

### Post by CharlesA on 2011-02-28
Looks like mine is set like this:

Host Driver: ALSA Audio Driver
Controller: Intel HD Audio

I'm also using 4.0.4, so it might be different in 3.2.

---

