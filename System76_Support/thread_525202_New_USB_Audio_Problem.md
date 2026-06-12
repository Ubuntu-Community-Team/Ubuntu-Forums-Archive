---
title: "New USB Audio Problem"
date: 2007-08-14
forum: System76 Support
---

### Post by Tomone on 2007-08-14
I have a problem with my usb audio (not the same problem as the one with the Plantronic headphones). My computer shows that the device is connected; in the volume adjustment, it's shown as an option and I can adjust the levels. There is just no sound. Does anyone have any ideas?

---

### Post by fbusy on 2007-08-14
what audio card is it..? what u running? moreeee info.. if you are talking about mobile pre from m-audio which is usb connected, i used to madfuload to install it. hope it helps

---

### Post by thomasaaron on 2007-08-14
Yes, more info please.
System 76 model number?

Best,
Tom

(Try going to System > Preferences > Sound and selecting the USB audio device...)

---

### Post by Tomone on 2007-08-14
I'm on a brand new Pangolin with feisty.
The volume control calls the audio "PowerWave USB Audio" (it looks like it's made by Griffin Technology) and I know that it works since I can plug it into my Windows machine and it does fine.

Also, in the Sound controller, the "Test" button causes an error message when the option is changed from "Autodetect" to any specific device. This doesn't bother me but I thought I'd mention it in case it's relevant.

---

### Post by thomasaaron on 2007-08-15
OK. I'll do some testing on it and see what I come up with.

Thanks,
Tom

---

### Post by thomasaaron on 2007-08-15
I just tested a brand spankin' new Pangy with LogitechUSB headphones and it worked perfectly. Here's what I did:

1. Make sure your sound device is set to the USB device (Double-click speaker icon. In resulting window,  go to File > Change Device > USB...)

2. In the sound settings (System > Preferences > Sound) I set everything to the USB device in the drop down menus).

That's it.

If you are getting errors, I'm wondering if you have some other conflicting app running.

Also, just to be sure, run your System 76 driver (System > Admin > System 76 driver). I'd use the 'Restore' tab and button. Just in case somebody forgot to run it in Manufacturing.

Also, if this doesn't help, please post the output of these commands:

cat /proc/asound/version
lsmod | grep -i usb   (with headphones attached)

---

### Post by matthyx on 2007-08-16
Hello,

I have the same problem with Dapper LTS i386 on a Thinkpad R40 with my Powerwave:

mb@marvin:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).

mb@marvin:~$ lsmod | grep -i usb
snd_usb_audio          79296  0
snd_usb_lib            16640  1 snd_usb_audio
snd_rawmidi            25504  1 snd_usb_lib
snd_hwdep               9376  1 snd_usb_audio
snd_pcm                89864  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
usbhid                 39904  0
snd                    55268  12 snd_usb_audio,snd_rawmidi,snd_seq_device,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
usbcore               130820  6 snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd

---

### Post by thomasaaron on 2007-08-16
While somebody on this particular forum may be able to help, we don't do any testing with Thinkpads.

You might try upgrading to Feisty and the most current version of ALSA.
You're W-A-Y behind the times! :lolflag:

---

### Post by Tomone on 2007-08-16
Here are the outputs: 

$ cat/proc/asound/version
bash: cat/proc/asound/version: No such file or directory

$ lsmod |grep -i usb
snd_usb_audio          81920  1 
snd_usb_lib            18176  1 snd_usb_audio
snd_hwdep              10372  1 snd_usb_audio
snd_pcm                81028  3 snd_usb_audio,snd_hda_intel,snd_pcm_oss
snd_rawmidi            25984  2 snd_usb_lib,snd_seq_midi
snd                    56452  16 snd_usb_audio,snd_usb_lib,snd_hwdep,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usbhid                 26592  0 
hid                    27392  1 usbhid
usbcore               134280  6 snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd

When I changed all of the sound settings to usb, programs weren't able to play any sound.
Also, I know that I have the s76 driver because I had to reinstall it when my sound shut off altogether when I was following someone's advice and getting the newest ALSA files.

---

### Post by thomasaaron on 2007-08-17
You should put a space between 'cat' and '/proc'.

If you tried to install Alsa yourself, there is a good chance you didn't put the correct USB parameter in the config command. The System 76 driver can re-do this for you correctly.

Did you run the driver after installing it? (Just trying to cover all bases...)
System > Administration > System 76 Driver (Then select 'Restore' tab and 'Restore Button'). 

Theoretically, this should get your sound back to where it needs to be.

Assuming you have all of your sound settings correct, your problem seems to be either...

1. Your ALSA is hosed.
2. Your USB headphones are not supported.

I'm guessing #1.

---

### Post by Tomone on 2007-08-17
Here's the correct output: 

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14.
Compiled on Aug 17 2007 for kernel 2.6.20-16-generic (SMP).

I've restored the driver, so that's not it. And I've reinstalled the ALSA drivers too, but still no sound.

---

### Post by thomasaaron on 2007-08-20
OK. I'm having a difficult time understanding EXACTLY/EVERYTHING you've done. Here is where I need clarification?

1. You said you re-installed the ALSA drivers. It looks like you have the right version of ALSA, but when you were compiling it, did you use the usb-audio switch? If not, it won't work.

2. You said you restored the drivers. Does that mean that you downloaded the drivers from our repositories or that you just re-ran the driver that came stock on the machine?  If you did the former, it will not work, and you need to contact me via email to get the current driver. If you ran the driver that came on the machine, that is correct.

If you did the correct thing in #1 and #2, and you can still not get output from your USB headphones, either they are just not supported or something is not configured correctly in your sound device settings.

If mistakes were made with either 1 or 2 above:
The correct configuration command when installing ALSA is:
```
sudo sh configure --with-oss=yes --with-cards=hda-intel,usb-audio --with-kernel=/usr/src/linux-headers-`uname -r`/
```

And you can contact me via email for the correct driver.

---

### Post by Tomone on 2007-08-21
As for the s76 drivers, I ran the one that came on the machine.

For the ALSA stuff, I reinstalled it using the package manager. This did nothing. Then, using someone's advice, I went to the ALSA website and got the newest version. In the process of installing those on my computer, I lost sound completely (which I have since fixed) but I couldn't get that finished and reinstalled the version from the package manager.

"when you were compiling it, did you use the usb-audio switch?":
What's the usb-audio switch? I just reinstalled everything through the package manager. It sounds like I'm missing something

I tried running that configuration command and get: 
sh: Can't open configure

---

### Post by thomasaaron on 2007-08-21
Ultimately, you don't really have to worry about compiling ALSA yourself.
Running the System 76 Driver version that came with your computer should install the correct ALSA version and configure it properly for your system.

To get a feel for how this is done, you can go to a command line and type...

sudo gedit /opt/system76/system76-driver/src/sound.py

...and have a look at how we configure it.

With that, your USB headphones should work. If they still do not, I would borrow a different brand (LogiTech always seems to work well) and see if that changes anything.

---

### Post by Tomone on 2007-08-21
Thanks, I'll try to try out some other usb phones and see if that works. If it does, I might just get some new ones for myself.

---

### Post by Tomone on 2007-08-23
IT'S WORKING!
I have no idea how. Three hours ago, I know it wasn't, but now it is. I don't think that I changed anything, but something must be different. I don't even care though. It's working now and I hope that it stays that way.
Thank you Thomas for your help, even though we didn't figure out what was going wrong, it's all good now.

---

### Post by thisispeace on 2007-08-23
So here's a little nuance issue:

Where is the speaker icon in KDE Ubuntu?  I don't see anything on the task bar.

---

### Post by gaussian on 2007-08-23
> 
So here's a little nuance issue:

Where is the speaker icon in KDE Ubuntu? I don't see anything on the task bar.


Run kmix from the command line. This will restore it in KDE.

---

