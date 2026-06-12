---
title: "Theater sound controls"
date: 2010-08-18
forum: System76 Support
---

### Post by bk7777` on 2010-08-18
I have Leopard system and am using it as part of my home theater system.  I was using XP on another system and got tired of the OS and Microsofts poor business practices.
 
Anyway one thing that the XP did that I have not figured out in ubuntu is sound control.  I seem to be getting 5.1 sound thru my receiver which is connect to the computer via fiber.  However there does not seem to be much control thru the OS.
 
I assume that there are additional packages I need to load.  Can anyone direct me to them so the system shows speaker controls.  More than just left right 2 channel balance.  A white noise test would be good proving that it knows and lets me test all 5.1 channels.
 
Is there something that would give a visual as to which codecs are in use i.e. Dolby, DTS, THX, Dolby HD or DTS HD.  Would there be a way to set the a default / perfered codec to use as well?  DTS if far superior to Dolby if the movie has the encoding.
 
FYI I am having no issues with playing blue-rays that have been copied to the hard drive on the computer.  The single .m2ts files are huge (Blind Side is 30GB) but they are just as sharp as if I was playing them thru my PS3.  The thing I really like is no menu garbage.  You click the file and it plays the movie.  I will be glad to give more detail if anyone is interested.
 
Thanks,
Brian

---

### Post by isantop on 2010-08-18
Most volume, balance, and fade controls should be going through your receiver. It should also tell you what codec is in use. If this isn't the case, go ahead and tell me and see what I can dig up about controlling that.

If memory serves me correctly, you should be able to control balance and fade from the output section of the Sound Preferences Dialog. It's not adjusting each channel individually, but it works in a pinch. I may be wrong about fade controls though.

---

### Post by bk7777` on 2010-08-18
While I agree the receiver can display the codecs I still have little or no control via the computer.  I have attached screen shots of the sound settings avaiable to me.
 
I can put the receiver into "Pure Audio" mode.  This mode will play it exactly as the computer sends it channel for channel.  However again there does not seem to be much control other than left right balance or 2 channel sound.
 
I reviewed synaptic and put in the key word sound.  There is a lot there to choose from but not much discription.  I only looked at the Unbuntu icons entries.  I really do not want to be loading and unloading drivers for trial and error purposes.
 
There are a lot that talks about sound server?  What is that?
 
one of the reasons I picked this unit was the fact that it states on the S76 website that the unit is "**Sound:** 7.1 channel surround" and it has an optical / fiber connection.
 
I can not believe that s76 does not already have a recomended or automatically loaded thru the "S76 driver" sound control selections.
 
Again I am really looking for control.  Something that I can test with, specifically one speaker at a time with white noise or tones.
 
Quality sound and controls have been around for years.
 
Remember I am new to Ubuntu and still have a lot to learn.  Is there device manager function that I have not found yet or something that gets in more detail about controling the sound card?
 
Thanks,
Brian

---

### Post by bk7777` on 2010-08-21
Should I assume that since no one is responding that there are no such controls in Ubuntu?
 
Thanks,
Brian
 
:-({|=

---

### Post by Perfect Storm on 2010-08-21
See if Pavucontrol is something you're looking for.

---

### Post by bk7777` on 2010-08-29
What is Pavucontrol?
 
It is a command or what?
 
 
Further information.  I got into the setup on my receiver to insure that is would show me which codec was in use as I trying playing differnt types of video and audio.
 
What I found is the computer is only sending PCM BIT streams via the fiber connection.  (PCM may be wrong but it is a BIT stream,  sorry short term mem).
 
Any way there has to be a way to control it via the OS.  My PS3 by default uses BIT streams as well but there are options to change it.  Correct me if I am wrong but the PS3 OS is a flavor of Linux or is it that the PS3 can run Linux?
 
Trying to provide additional information.
 
Thanks,
Brian

---

### Post by bk7777` on 2010-08-31
I figured out pavucontrol and loaded the code.
 
I now have a visual for sound control volume but it still only shows 2.0 channel sound.
 
Again if my receiver is in direct mode I only get left and right sound.  No center, no rear or sub.
 
We are making progress but not there yet.
 
I did submit a bug report to launchpad.net/system76.
 
bug # 627206
 
Thanks,
Brian
 
#-o

---

### Post by bk7777` on 2010-09-04
FYI for your all still having issue with no theater sound controls.  Here is what I sent to Carl of S76.
 
Carl,
 
I have learned a lot this pass 24 hours but it is not good.
 
I have been reading the Intel documentation which most of it is windows specific. They do not seem to have a lot of Linux / Ubuntu help.
 
To date I have tried three different physical sound configurations.
 
1) S/PDIF via optical
2) HDMI
3) Analog
 
After each change the system was freshly booted.
 
Options 1 and 3 got the same results. Only 2.0 channel output or left/right channels only
 
Option 2 No sound at all no matter what the settings.
 
Additional details:
 
Option 1 S/PDIF via optical:
 
In reading the Intel documentation it states that it is not uncommon for the system to only output left and right channels and recommended using analog connections to get up to 8 channels. Ok for now let assume that Intel or the computer industry is not in-line with the home theater world. Which may still be the case. I am fully aware of this because Creative Labs makes an external interface (which I have) that takes 5.1 channel analog output and converts it to S/PDIF via optical or coax. I used the box on my old P4 Window XP system to get 5.1 surround sound to my receiver and it works well.
 
Option 2 HDMI:
 
I asked you specifically before I purchased the system based on a posted review if the required physical jumper was now installed by default on your systems. You stated it was and I took your word for it. If that is the case why does it not work?
 
Option 3 Analog:
 
Attached are two more screen shots. One is showing that VLC is feeding the system a 5.1 audio stream. (left, right, rear left, rear right, center and sub) Yet the second screen shot is showing that it is only putting out a 2.0 audio stream. Again Ubuntu thinks it only has a two channel card.
Further reading of the Intel manuals it specifically states the audio driver has to tell the sound card to re-task two of three ports for 5.1 multi-channel. If you want 7.1 it has to re-task task three of four ports.
 
Now what?
 
How do we get Ubuntu to re-task the audio card? I can not believe that if Ubuntu understands the card is multi channel then it will give a lot more options than just analog/digital Stereo or off.
 
Thanks,
Brian

---

### Post by bk7777` on 2010-09-05
[FONT=Arial][SIZE=4]Carl,[/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][COLOR=black]I have again been doing more testing and found some interesting results.[/COLOR][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][COLOR=black]I wanted to see if it was the hardware that was having issues and thankfully the hardware is fine. Everything is pointing to Ubuntu.[/COLOR][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][COLOR=black]I decided to disconnect the existing hard drives with Ubuntu on them and put a freshly formatted drive in and install Win 7 64 bit. I also installed all the software for Win 7 from Intel and ran tests.[/COLOR][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][COLOR=black]What I found is Intel driver recognizes any and all changes to what is plugged in on the fly and pops a window up of the change asking me to confirm the change.[/COLOR][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][COLOR=black]My first test was to use the optical connection and found that in direct mode it would only produce sound in the left and right speakers or 2.0 channel sound. However it was sending the signal to tell the receiver to switch to the Dolby Codec. If I enabled the Pro Logic function in the OS it did send out 5.1 test signals but not much control. The short answer is it works within Win 7 but is primitive at best.[/COLOR][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][COLOR=black]The second test was all analog. As soon as I started plugging in cables again I was prompt for the change and had to answer a few questions. Once configured, I had full control of each individual speaker, 5.1 channels and could send test signals to each. Side note I believe it is the way I have my rear speakers attached to the receiver creating this problem. With the audio driver configured in 5.1 mode. I was not getting any rear speaker sound. However, when I switched it to 7.1 and disable the side speakers in the window it worked just fine.[/COLOR][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][COLOR=black]I did not do any testing with the HDMI connection.[/COLOR][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][COLOR=black]I am sure you know this but want to cover the base anyway. Intel states that the on-board sound controller driver is a “Realtek [/COLOR][COLOR=black]ACL[/COLOR][COLOR=black] audio driver”. Is there an Ubuntu equivalent library or settings?[/COLOR][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][COLOR=black]Needless to say I am learning a lot about the system but getting frustrated with Ubuntu at the same time.[/COLOR][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][COLOR=black]I look forward to hearing from you.[/COLOR][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][COLOR=black]Thanks,[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=4][COLOR=black]Brian[/COLOR][/SIZE][/FONT]

---

### Post by bk7777` on 2010-09-06
[FONT=Times New Roman][SIZE=4]Carl,[/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][FONT=Arial]I spent most of my evening digging thru the forums and ended up putting together an almost 100% solution from five different sources. The sources were 1) bug report, 2) forums, sound problem solutions guide, 3) intel.com, 4) realtek.com, 5) alsa-project.org. [/FONT][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][FONT=Arial]With all of reading and testing it comes down to making two changes in Ubuntu for the Leopard.[/FONT][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][FONT=Arial]1) File name = /etc/modules[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=4][FONT=Arial]Add to end of file = “snd-hda-codec-realtek”[/FONT][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][FONT=Arial]2) File name = /etc/modprobe.d/alsa-base.conf[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=4][FONT=Arial]Add to end of file = “options snd-hda-codec-realtek”[/FONT][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][FONT=Arial]Reboot[/FONT][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][FONT=Arial]Your suggestion in the bug report made me look closer at the file but your syntax was wrong for the leopard. I suggest that you make it part of the system76 drivers since Ubuntu configures it as a standard 2 channel speaker card.[/FONT][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][FONT=Arial]By making the above changes the system now gives me 15 more additional options on how to configure the sound options. The only thing missing is a way to send out test signals to each individual channel / speaker. Do you know of command within Ubuntu?[/FONT][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][FONT=Arial]I like VLC as my default video and audio player and I assume the other players will require this adjustment as well. The VLC must have 2 changes in preferences: S/PDIF box must be checked if using optical/coax S/PDIF connections and output type must be set to ALSA. [/FONT][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][FONT=Arial]By making the above changes Ubuntu will change the codec data stream sent to the receiver to be the same as the source. I was seeing on my receiver and enjoying great sound from codec’s such as DTS when playing Blu-rays and DVDs, Dolby from DVDs and mkv files and plan old 2 channel PCM for stereo sources such as avi and mp3. [/FONT][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][FONT=Arial]Do I consider this a closed issue? NO. There are few items that still need to be reviewed, confirmed and fixed.[/FONT][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][FONT=Arial]Once I got the sound codec’s working via optical I stopped testing analog. I figured that your all’s lab can do this and confirm my findings.[/FONT][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][FONT=Arial]Second, there is still the issue of why it will not work via HDMI. To be honest I have not retested this but it is on my to do list. I would like your input and procedures on what has to be checked on the system to see if all the correct connections are in place. I am assuming that there should be a cable coming from the mother board to plug into the [/FONT][/SIZE][/FONT][FONT=Arial][SIZE=4][FONT=Arial]GPU[/FONT][/SIZE][/FONT][FONT=Arial][SIZE=4][FONT=Arial]. I have not been to nvidia.com to review the documentation on the card yet. Tristan Schmelcher talks about an internal S/PDIF link cable in his review. Where is it and what does it look like?[/FONT][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][FONT=Arial]Third, alsamixer is a must. There is a gnome version of this as well and both should be part of the system76 driver install. I like the terminal version better than the gnome version but the users need to understand they have to run the “sudo alsactl store 0” command to save their settings. Most of the surround speakers are muted by default and in the last column it should be set to 8 channels.[/FONT][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][FONT=Arial]Forth, Tristan Schmelcher brings this up in his review as well about the sound cutting out occasionally. I am getting this as well but only when a codec that is greater than PCM 2 channel is in use. Tristan’s solution was to replace / install another sound card. This is happening on my Leopard only once in a while. I would say 2 or 3 times in an hour and there is no pattern that I have found so far. Tristan’s thinking is the problem stems from EM noise within the system. I have no way to disprove this. What is system76 position on correcting this issue? Since it seems to be ok for 2 channel playback and cuts out during higher channel counts. I am thinking that the processes that drive the sound card may only need a higher “nice” value / priority in the system. It almost seems to be kernel / CPU starved. Which solution is correct, Tristan’s, mine or does system76 have a solution? I am more than willing to test further but to do so I would need process names to “renice” for testing. I have no clue what they are called.[/FONT][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][FONT=Arial]I will have to say I almost have the perfect theater system setup. If we can get these last few bugs worked out it will be ultimate.[/FONT][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][FONT=Arial]I look forward to hearing back from you.[/FONT][/SIZE][/FONT]
 
[FONT=Arial][SIZE=4][FONT=Arial]Thanks,[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=4][FONT=Arial]Brian[/FONT][/SIZE][/FONT]

---

