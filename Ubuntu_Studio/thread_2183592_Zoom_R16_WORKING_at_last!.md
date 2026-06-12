---
title: "Zoom R16 WORKING at last!"
date: 2013-10-25
forum: Ubuntu Studio
---

### Post by mightysween on 2013-10-25
Since I have been trying to solve this for about 3 years, I thought I would share this great news for Zoom R16 owners... with the help of other users/developers at Linux Audio forums, we have come up with the necessary code to make the R16 work for 8 channels of 24-bit, 96KHz recording.

This requires recompiling the kernel with a modificaiton to /sound/usb/quirks-table.h

Set JACK to "capture only"... playback through the R16 does not work.

I have tested it in Ubuntu Studio 13.10 (as well as AVLinux 6.0.1)

Known Issues (please share any more you find!):   

1. Sample rate can not be changed once Jack has started.  To change it, stop Jack, unplug and plug back in the R16, and set up Jack with the new sample rate.

2. No playback on R16

3. Control Surface features not working.


Here is the code... ENJOY!! 

> { 
        /* ZOOM R16 in USB 2.0 mode */ 
        USB_DEVICE(0x1686, 0x00dd), 
        .driver_info = (unsigned long) & (const struct snd_usb_audio_quirk) { 
                .ifnum = QUIRK_ANY_INTERFACE, 
                .type = QUIRK_COMPOSITE, 
                .data = (const struct snd_usb_audio_quirk[]) { 
                        { 
                                .ifnum = 0, 
                                .type = QUIRK_IGNORE_INTERFACE 
                        }, 
                        { 
                                .ifnum = 1, 
                                .type = QUIRK_AUDIO_STANDARD_INTERFACE 
                        }, 
                        { 
                                .ifnum = 2, 
                                .type = QUIRK_AUDIO_STANDARD_INTERFACE 
                        }, 
                        { 
                                .ifnum = 3, 
                                .type = QUIRK_MIDI_STANDARD_INTERFACE 
                        }, 

{
				.ifnum = 4,
				.type = QUIRK_AUDIO_FIXED_ENDPOINT,
				.data = & (const struct audioformat) {
					.formats = SNDRV_PCM_FMTBIT_S24_LE,
					.channels = 8,
					.iface = 1,
					.altsetting = 1,
					.altset_idx = 1,
					.attributes = UAC_EP_CS_ATTR_SAMPLE_RATE,
					.rates = SNDRV_PCM_RATE_44100 |
						    SNDRV_PCM_RATE_48000 |
						    SNDRV_PCM_RATE_88200 |
						    SNDRV_PCM_RATE_96000,
					.rate_min = 44100,
					.rate_max = 96000,
					.nr_rates = 4,
					.rate_table = (unsigned int[]) {
							44100, 48000, 88200, 96000
					}
				}
			},



                        { 
                                .ifnum = .1 
                        }, 
             		

			} 

       		 } 

}, 


Link to original discussion:

[http://linux-audio.4202.n7.nabble.com/re-Zoom-R16-td87487.html]("http://linux-audio.4202.n7.nabble.com/re-Zoom-R16-td87487.html")

---

### Post by mightysween on 2013-10-25
Just to clarify the "Capture Only" thing... you CAN run duplex if you use a second device for playback.  Just set them manually in the spots underneath the dropdown menu for duplex/capture/playback in Jack.  Often, you will need to set up each application the first time you run it in Jack's "Connect" screen (or something like Patchage) in order to make them record on one device and playback on another

---

### Post by mightysween on 2013-11-15
Control surface IS working.   I am using A2JMIDID package to bridge the ports.   

For Ardour 3 use the built-in MIDI setup to connect R16 out to the Mackie Control Port...bingo.   

For Ardour 2, use qjackctl patchbay and create 3 separate Input Sockets, one each for Ardour control, ardour mcu, and ardour seq -- and then create an R16 output socket and connect it to all three input sockets (this will NOT work if you try to put control, mcu, and seq ports in a single input socket).

Faders, transport, shuttle wheel are all working.

---

### Post by Chasehead on 2014-02-01
Oh man this is so exciting! I have been dying to use my R16 with linux since I purchased it a few years ago as a Macbook Pro/Logic user. I even built a powerful hackintosh recently for the sole purpose of using the R16 and Logic, but now I have a great excuse to start using Ubuntu for absolutely everything! Huge thanks and I can't wait to try this! 

As for recompiling the kernel, do you think the developers of Ubuntu Studio and other music production-oriented distrobutions would be willing to add this code to the next release? That would make it even easier for us regular folk. I'll have to learn how to do this now on a testing system to give er a whirl.

---

### Post by Hamish_Low on 2014-02-22
Hi, 

I don't want to ask a stupid question but how do I recompile the kernel with a modificaiton to /sound/usb/quirks-table.h?

Thanks

---

### Post by Hamish_Low on 2014-02-24
Okay, getting some advice on linux-audio-user list...could this quirk be added as a feature request for the next LTS version?  Have just requested on Launchpad...

---

### Post by Nistegmos on 2014-06-21
Thanks for this info.  I think this maybe explains why I couldn't get playback thru my R8 to work.  Maybe it's a similar thing.  I also tried the second interface for duplex configuration and started to get results in reaper, but i got confused while i was doing it.  i will check this later.  i use pulseaudio but recently installed wineasio.

---

### Post by marc-andr2 on 2015-03-01
I was excited when I found this thread... I downloaded the latest lowlatency kernel image and realised the quirk file doesn't exist anymore... You guys know how I could get it working now?

---

