---
title: "Gutsy Upgrade On Gazelle Value"
date: 2007-10-09
forum: System76 Support
---

### Post by pak33m on 2007-10-09
Hello everybody,

In need of some advice here.  Last night I decided to upgrade my Gazelle Value with Feisty to Gutsy.  

**How I upgraded**

```
sudo apt-get update 
sudo apt-get upgrade
Alt + F2 and entered gksu update-manager -c -d
Clicked on the upgrade button
```

**What happened**

[LIST]
[*]In the middle of the install I was prompted to Keep or Replace a file but I do not exactly remember what the file was called, except acpi something or other but I chose to Keep the file. 

[*]I was prompted once more after that only to accept the suggested install and remove.  After the install I rebooted and X nothing loaded expect BusyBox.
[/LIST]

**What I did about it so far**

[LIST]
[*]Typed reboot at the BusyBox prompt and tried to access recovery mode to no avail.  
[*]However I was able to select the previous kernel.

[*]I checked the logs and I noticed the message that the "kernel modules not loaded" and "could not find BIOS".

[*]I tried to run the System76 driver update but I was prompted that the updates would have come from Ubuntu.
[/LIST]


I wanted to ask in the System76 forum first because I am not sure if this is something specific to System76.  I have done some searching but only found so much info with regards to both the upgrade and System76.  Appears to me that some file is being referenced that is not present or incorrectly named.

If I need to include more info I will straight away.  Any help would be appreciated,

Jimmy

---

### Post by thomasaaron on 2007-10-10
Hi, Jimmy.

Actually, I got your phone message yesterday, but it pooped out at the phone number! (Also, I've not seen a post on the other forums...)

The "cannot find bios" part is interesting. I recently had a computer give the busybox prompt with a fresh Gutsy kernel. Turned out it needed a bios update.

I'm not sure what happened with your upgrade, but I'm sure some light will be shed on it, as full-scale Gutsy testing begins in-house today.

Maybe somebody on the forums can help, but if not I'd recommend running the good kernel. I'll try to duplicate the problem when I get to the Gazelles.

Best,
Tom

---

### Post by tgalati4 on 2007-10-10
It's nice to see the community just slightly ahead of the corporate curve.

---

### Post by pak33m on 2007-10-10
Hi Tom,

I am glad to have offered my Gazelle Value up to the Gutsy table of sacrifice in the name of System76 and the community, he he.  Sorry for the exaggeration, I was listening to The Last Temptation of Christ Soundtrack today.

No really, I was able to get a good kernel albeit limited in some functionality.  I tired running the System76 restore to no avail.  

I could not find any other info that would simply have me replace a file or something other than reinstalling fresh of Gutsy.  I believe that this is the next step.

As of a few minutes ago I created a backup of my home directory and am ready for a fresh install of Gutsy.  Before I do though I wanted to ask if the System76 driver update would work after the install? Or anything else I should know or do? Would System76 like for me to operate on my Gazelle Value any more than I have?

Thanks,

Jimmy

---

### Post by thomasaaron on 2007-10-10
No, the System 76 driver won't do anything. It might look like it is working, but it isn't actually patching anything.

The version that supports Gutsy, though, should be out by next Friday.

---

### Post by pak33m on 2007-10-10
Tom,

Ok, so even if I do a fresh install of Gutsy will my graphics card, wireless, etc. no longer work and/or work properly? What will I lose? 

If so, should I should wait until Friday to perform a fresh install of Gutsy?

Thanks,

Jimmy

---

### Post by thomasaaron on 2007-10-10
Wireless should work fine.

After installing:
sudo apt-get update && sudo apt-get --assume-yes dist-upgrade

For Graphics:
sudo apt-get install nvidia-glx
sudo dpkg-reconfigure xserver-xorg
(Choose all defaults EXCEPT: select all possible resolutions, select "nvidia" for the driver, choose "Advanced" near the end.)

sudo reboot

After that, you may or may not have any problems with sound. I think it might end up working out OK. If your sound works, let me know if headphone jack sense is working.

Other than that, you *should* be OK.

---

### Post by pak33m on 2007-10-10
Tom,

Again thank your for your swift response.

One concern that I do have that i just thought of when considering whether to upgrade to Gutsy or fall back to Feisty is that I plan to be using my Gazelle Value to DJ a gig.  And to do this I run a mini-jack line (to RCA on the other end) out of the headphone jack.

I plan to at least try the upgrade (because I am dangerous), follow your instructions post-install and post my results.  If sound does not work I will just reinstall Feisty in the meanwhile and/or wait for Friday.

---

### Post by thomasaaron on 2007-10-10
I'm not sure when your gig is. But if sound is not working right under Gutsy, I can send you instructions for compiling alsa that will (99% chance) bring everything back up to speed.

I'm getting ready to split, but I can do that as early as tomorrow afternoon. Just send me an email.

---

### Post by pak33m on 2007-10-10
Tom,

Oh yeah, guess I forgot to tell you that my gig is on Saturday.  No worries though because even if sound is no working I will either reinstall Feisty and/ or strictly use vinyl and CDs.  And there is nothing better than putting my hands back on vinyl again!

---

### Post by pak33m on 2007-10-10
So, I performed a fresh install of Gutsy on my Gazelle Value. During the text-based install I noticed that the screen changed and appeared as if out of Yars Revenge.  This happened until the CD popped out.  I hit enter and she rebooted.

I can confirm that both wireless and graphics are working but sound is not.  No biggie for now.

I ran 
```
sudo apt-get update && sudo apt-get --assume-yes dist-upgrade
```

I did not reconfigure xserver-org, as graphics seemed to be working properly.  This is unless it is recommended by System76?

I will keep abusing my Gazelle Value and continue to post with any further results.

---

### Post by pak33m on 2007-10-11
After upgrading my Gazelle Value to Gutsy I have noticed several items of concern (except no sound of course):

[LIST]
[*]Yars Return effect (or big and pixelated) on shutdown and restart
[*]Dim screen after login
[*]Dim screen at random but frequent during normal use
[*]Hard drive slow to respond
[*]Possible misinformation on CPU usage
[*]CPU2 (Core 2 Duo) using more processing than CPU1
[/LIST] 
  
That is what I have so far.  

GNOME 2.20.0 has some awesome enhancements.

---

### Post by thomasaaron on 2007-10-11
Hi, Jimmy.

WOW! I've not thought about Yars Revenge since I was a kid with an Atari! My favorite, though, was Berzerk.

I forgot to tell you about the "Yar" effect. Yes, it does that. (But I guess you know that now.) To get through it, you must psychologically resign yourself to patience. Very difficult, I know.

While your graphics seem OK, I think they are using the nv driver instead of the nvidia driver. So, they are probably not accelerated.

I think you can either or adjust or kill the dimming effect by going to System > Preferences > Power Management.

Not sure about the HD/CPU stuff. I've not gotten that far yet. I'd be surprised, though, if Gutsy was less efficient that Feisty.

Best,
Tom

---

### Post by pak33m on 2007-10-11
Tom,

Considering the "Yar" effect that I am having would you recommend that I follow your instructions for reconfiguring xserver-org?

> For Graphics:
sudo apt-get install nvidia-glx
sudo dpkg-reconfigure xserver-xorg
(Choose all defaults EXCEPT: select all possible resolutions, select "nvidia" for the driver, choose "Advanced" near the end.)

Or should I just leave well enough alone?! It is no biggie really, as I know that System76 is working to get an update ready for it for Friday.

---

### Post by thomasaaron on 2007-10-11
You will not experience Yar's revenge again. It is only during a disk install.
You can follow the instructions.

---

### Post by peestandingup on 2007-10-11
Thomas, im not trying to jack this thread, but I just have a quick question that I didnt think needed another thread started.

When exactly do you guys plan on having Gutsy pre-loaded on your new machines?? Im probably gonna order one right then & there. Also, you mentioned in the other thread that you will have the wireless N cards option available right after the update as well???

---

### Post by thomasaaron on 2007-10-12
Keep an eye on the web site. When you click "configure" gutsy will appear as the OS. It should be on Oct. 18-20.

There is a big shortage of the "n" cards. While they will work natively with Gutsy, they may not be available until around the first week of November.

---

### Post by pak33m on 2007-10-12
Firstly, I just had to say that peestandingup is the funniest nick I have ever heard! Ha ha.

Tom,

> No, the System 76 driver won't do anything. It might look like it is working, but it isn't actually patching anything.

The version that supports Gutsy, though, should be out by next Friday.

Is there an expected time that you might expect to have the System76 driver version for Gutsy today? No biggie if yo do not expect it today I will just have to reinstall Feisty today to make my DJ gig tomorrow.  Unless you would recommend compiling ALSA on Gutsy which you asked me to email about.

---

### Post by thomasaaron on 2007-10-12
Sorry. When I said "Next Friday," I meant the 19th (i.e. to coincide with the release of Gutsy). Sorry if that was misleading.

If you want to re-compile ALSA, I can send you instructions. But at this point, there is no big guarantee on it until I've done the in-house testing.

---

