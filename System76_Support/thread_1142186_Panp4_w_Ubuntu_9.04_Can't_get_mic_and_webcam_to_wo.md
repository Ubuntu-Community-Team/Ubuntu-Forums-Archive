---
title: "Panp4 w/ Ubuntu 9.04: Can't get mic and webcam to work on Skype"
date: 2009-04-28
forum: System76 Support
---

### Post by flukeairwalker on 2009-04-28
I clean installed 9.04 by formatting "/". Didn't format the home drive. So far I've set up Medibuntu, the System76 driver, and a few programs I find essential. Also the nVidia driver version is 180, the most recent one. I know my webcam turns on and off through the lsusb command. Camera Monitor does not recognize it turning on and off.
On Skype I can't see video, I can't send video, I can hear audio, I can send audio. I thought 9.04 was going to fix these problems. What can I do?

---

### Post by riseringseeker on 2009-04-29
> **flukeairwalker said:**
> I clean installed 9.04 by formatting "/". Didn't format the home drive. So far I've set up Medibuntu, the System76 driver, and a few programs I find essential. Also the nVidia driver version is 180, the most recent one. I know my webcam turns on and off through the lsusb command. Camera Monitor does not recognize it turning on and off.
On Skype I can't see video, I can't send video, I can hear audio, I can send audio. I thought 9.04 was going to fix these problems. What can I do?

I'm guessing, since you added medibuntu, that you got skype from there, rather than the skype site.  Which one did you install?  I've had better luck installing skype-static (sudo apt-get install skype-static), it also allows the user avatars and pictures to be displayed as opposed to the "sudo apt-get install skype" version which does not.

Does skype show the cam on your Pangolin, does it work with cheese?

---

### Post by flukeairwalker on 2009-04-29
I installed it from the Medibuntu repository as it's what the computer recommended to me. Does the Skype site even have the 64 bit version?

No, the webcam isn't working on Cheese. I haven't gotten it to work with any program.

---

### Post by riseringseeker on 2009-04-30
> **flukeairwalker said:**
> I installed it from the Medibuntu repository as it's what the computer recommended to me. Does the Skype site even have the 64 bit version?

You know, I've never thought about which version the Skype site itself has.  It may indeed check what you are running and only offer the appropriate d/l, but I really don't know.

You may try the following, which I used when I first had troubles with skype.  Copy and paste these one at a time into a terminal.

```
sudo apt-get purge skype
```

```
sudo apt-get install skype-static
```

The first will delete the current skype implementation, the second will install a version that has worked better for me.  If it's not working now, you've nothing to lose by trying it.

I found the "skype-static" allows you to have an avatar, and see other peoples avatars, while the plain "skype" does not.  In looking around, that appears to be a bug with the medibuntu 64 bit version.  Overall I found it just works better anyway.

> No, the webcam isn't working on Cheese. I haven't gotten it to work with any program.

Tom will have to address this, as it should work with the System76 driver in cheese.  (Tom, reinstall/re-restore the drivers?)  Once it works in cheese, it will likely work in skype.

As to the microphone, does it work in sound recorder?  (Applications->Sound and Video->Sound Recorder)  I had to change the sound preferences on my Wild Dog to get the microphone working by adding an "input" and "mux" slider, and unmuting/increasing volume on them, it would not work any other way.  I also had to add "surround" to get the speakers working, but I assume yours are, or you would have mentioned it.

---

### Post by thomasaaron on 2009-04-30
Try the webcam in Ekiga. Read all of this to make sure you're on the right track...

> 
INSTALLING THE WEBCAM DRIVER
Your computer should arrive with any necessary drivers already installed. However, if you've run any updates, particularly kernel updates, since getting the computer, there is a chance the webcam driver will need to be recompiled. To do that, simply run your System76 Driver (System > Administration > System76 Driver > Install (tab) > Install (button)) and then reboot your computer.

TURNING YOUR WEBCAM ON
Knowing if your webcam is on can be a little tricky, as there is no LED or icon indicating its state. To find out if it is on, open a terminal (Applications > Accessories > Terminal) and run this command...
lsusb
...and then press the Fn-F10 buttons and run lsusb again. Your output from both runs of lsusb should differ by a single line. Here is my output from running lsusb, pressing Fn-F10, and then running lsusb again...

oem@ubuntu:~$ lsusb
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

...I pressed Fn-F10 here...

oem@ubuntu:~$ lsusb
Bus 008 Device 002: ID 5986:0300 Acer, Inc
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Notice that after I press Fn-F10 and run lsusb again, I see this line (which was not present on the first run of lsusb)...
Bus 008 Device 002: ID 5986:0300 Acer, Inc

That is the line that indicates my webcam is turned on. If I press Fn-F10 again and run lsusb, that line will be gone, indicating my webcam is turned off. Your line may differ slightly. The point is, if it appears and disappears when you press Fn-F10, it is your camera line.

APPLICATIONS THAT WORK WITH YOUR WEBCAM
Here are the applications that are known to work with your webcam:
1. Ekiga Softphone: It's already installed on your system (Applications > Internet > Ekiga Softphone)
2. Skype: Install via this tutorial: [http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)
3. Cheese: Install by running this command in a terminal: sudo apt-get install cheese

USING YOUR WEBCAM WITH A SUPPORTED APPLICATION
I recommend getting your webcam going with Ekiga Softphone first. Ekiga has always worked well, whereas Cheese has be broken a couple of times and Skype may require some internal configuration.

1. First turn off all applications that use the webcam. If the application (like Ekiga and Skype) creates an icon in the upper toolbar, right-click that icon and select "Quit" in the resulting submenu. Just shutting the application window sometimes isn't good enough. If multiple applications are trying to connect with the webcam, it probably won't work.
2. Turn on your webcam per the instructions above.
3. Open your application. If you're using Ekiga, you probably will need to click the webcam icon on the left side of the Ekiga control panel.

You should now see yourself on the Ekiga control panel.   


Regarding the mic in Skype, make sure the sound device configuration for skype is set up as:

Sound in: hda-intel
sound out: pulse

---

### Post by flukeairwalker on 2009-05-06
Okay, I've tried all that. The mic works when it feels like. The webcam doesn't work at all. I feel I should mention that webcam and mic are veryu important to me, as I'm stationed in Korea while my family is in Texas and Puerto Rico, and it would be great if I could chat with them. Getting this to work is a really big deal for me.

---

### Post by thomasaaron on 2009-05-06
OK. Re-imaging my shop Pangolin. Will get it working and post screenshots. Standby...

---

### Post by thomasaaron on 2009-05-06
OK, First, do this...

> First, run your System76 Driver (System > Administration > System76 Driver > Install Tab > Install Button) and reboot your computer.

Second, double-click on the speaker icon in the upper right corner of your screen. In the resulting Sound Control Panel, make sure your Sound Device is set to "HDA Intel (Alsa Mixer)." Then go to Edit > Preferences. (If you are using Ubuntu 8.10 or 9.04, you will have to click the Preferences button.) Make sure all available checkboxes have been selected. This will make more sliders available on the sound control panel. On the sound control panel, make sure that PCM, Master and Front (or whatever combination of these you have) are not turned down too low or muted.

Third, go to System > Preferences > Sound. Make sure all drop-down selectors are set to Autodetect. Click the first Test button to see if you now have sound.   

Then, set up your system like the attached screenshots.

---

### Post by thomasaaron on 2009-05-06
...AND these...

---

### Post by flukeairwalker on 2009-05-09
Wow! That's some attention to detail you paid there. I can't believe you went through all that trouble just to make sure my mic worked! I feel like buying another computer from you guys just for that.

Think you could do the same for the webcam? ;)

---

### Post by herman94 on 2009-06-07
> **thomasaaron said:**
> OK, First, do this...

  

Then, set up your system like the attached screenshots.
*Thank you very much for your screenshots. I only needed to activate ONE capture microphone I could see on your picture. Everything is solved now. COMPLIMENTS...!*

---

### Post by gmxgeek on 2009-06-09
I am having a similar issue getting the webcam on my laptop to work. Panp4 as well. lsusb outputs
```

Bus 002 Device 003: ID 0402:5606 ALi Corp.

```

I am installed the System76 Drivers multiple times with no success. There is no /dev/video device, and no programs acknowledge the camera.

---

### Post by kumarnat on 2009-06-09
Hi

Thanks for listing the applications with which the webcam works, I have an eeepc 1000 he with ubuntu 9.04 and I installed cheese as suggested and the webcam works just fine.

Thanks

---

### Post by silvertuna on 2009-06-21
My Skype doesnt work with other Skype users, Skype to Skype, Skype users online do not appear as online in my Skype.  But i can use my Skype to call landlines.  Sound and video works.  I have tried the Medibuntu (AMD64) Skype and Skype static, both have the same problem.

I have a Pangolin 64 bit running Jaunty.
My Skype worked in Intrepid fine.

Suggestions?

---

### Post by silvertuna on 2009-06-22
Got Skype to work fine by downloading this:

[http://www.skype.com/go/getskype-linux-ubuntu-amd64](http://www.skype.com/go/getskype-linux-ubuntu-amd64)

It's labeled for Intrepid, but is working fine in Jaunty.  The Jaunty version in the Medibuntu repository would not work for me.

---

### Post by silvertuna on 2009-08-03
thomassaaron, post #8 the first screenshot recommending "default" settings in skype sound i think conflicts with earlier post #5:

> Regarding the mic in Skype, make sure the sound device configuration for skype is set up as:
Sound in: hda-intel
sound out: pulse

maybe i misunderstand something - please clarify should we select "default" or "hda-intel-pulse" in the skype settings?

---

### Post by thomasaaron on 2009-08-04
I know it looks like a discrepancy, but it's not. The settings I mentioned for Skype are correct.

---

