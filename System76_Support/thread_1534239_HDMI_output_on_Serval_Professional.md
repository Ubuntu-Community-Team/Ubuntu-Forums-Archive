---
title: "HDMI output on Serval Professional?"
date: 2010-07-19
forum: System76 Support
---

### Post by volkerbradley on 2010-07-19
Hi,
Just connected a HDMI cable from my new Serval Pro to a TV.  
Could not display the video or the sound on the TV.
How is this done?
Thanks.

---

### Post by thomasaaron on 2010-07-19
Please go to System > Administration > nVidia Xserver Settings. You should be able to detect and enable the HDMI monitor from there.

---

### Post by volkerbradley on 2010-07-19
Hi,
Thanks for your response.  Unfortunately, I still need more help.
I have opened the NVIDIA X Server Settings Application
I have clicked on all the headers that I find there, ie. Xserver Display Configuration, X Screen 0 and all the subheadings, GPU 0 and all the subheadings and nvidia settings Configuration.  
I am unable to find the place to enable HDMI output
Could you point me in the right direction?

---

### Post by zitch on 2010-07-19
When you open the NVIDIA X Server Settings, enter *X Server Display Configuration*.  If you don't see the other screen in the "Layout" screen you may have to press the "Detect Display" button (with the HDMI cable plugged into the laptop and the screen, and probably with the screen on).  From there, you should either be able to pick the screen from the "Layout" box, or select the screen from the "Model:" dropdown in the "Display" tab. 

[IMG]http://dl.dropbox.com/u/424679/Pictures/screenshots/Screenshot-NVIDIA%20X%20Server%20Settings.png[/IMG]
(What I have displayed here is the secondary DVI screen I have at work, but I have tested this on my 40" Samsung through HDMI at home!  I'll add some instructions for audio later.)

When I switch to the secondary screen, I proceed to press the "Configure..." button and select "TwinView".  

[IMG]http://dl.dropbox.com/u/424679/Pictures/screenshots/Screenshot-Configure%20Display%20Device.png[/IMG]

Once I press the "OK" button on that box, I click on the "Apply" button and usually within 5 or so seconds, both screens are up.  There's a confirmation popup that counts down from 15 that you have to OK after this.

To get audio from my Serval Pro (serp5) though HDMI to my TV, I had to go into System->Preferences->Sound.  Go to the hardware tab, and change the "Settings for the selected device:" dropdown to "Digital Stereo (IEC958) Output + Analog Stereo Input".  (Note that the model number in parenthesis might be different)

[IMG]http://dl.dropbox.com/u/424679/Pictures/screenshots/Screenshot-Sound%20Preferences.png[/IMG]

Then make sure that the "Output volume" on top is not set all the way left and not muted.  And make sure your TV / Surround System is on, has the volume set to an audible volume, and is not muted.

Hope this helps.

---

### Post by volkerbradley on 2010-07-20
Yes, these instructions were very helpful.  Thank you for taking the time to write them.
I have one residual question.  On my TV, to which the HDMI cable is connected, I can see the wallpaper of my computer but I cannot see any of the open applications.  For example, I cannot see an open terminal or Nautilus displayed on the TV.
Included are my two configuration screens.
[http://dl.dropbox.com/u/5383640/HDMI-1.png](http://dl.dropbox.com/u/5383640/HDMI-1.png)
[http://dl.dropbox.com/u/5383640/HDMI-2.png](http://dl.dropbox.com/u/5383640/HDMI-2.png)
Could you point me in the right direction?

---

### Post by zitch on 2010-07-20
Basically, you have your Samsung screen setup as a "second screen" to the right of your main screen (Check the "Position" field in your second screenshot).  You can drag an existing application to the right of your existing screen and it should show up on your Samsung.  In my setup, I actually have my secondary screen to the right of my laptop, so I leave the position where it were.  If I want to put apps there, I simply drag their windows to the right to that screen:
[IMG]http://dl.dropbox.com/u/424679/Pictures/screenshots/Screenshot-multimonitors.png[/IMG]

If you want to reposition where the Samsung is in relation to the main screen, you can click-and-drag the box in the Layout output to change its position.  For example, if my secondary screen was my TV and I wanted it above my main screen because my laptop is on the coffee table, which is from my perspective "below" the TV, I can arrange it like so:
[IMG]http://dl.dropbox.com/u/424679/Pictures/screenshots/Screenshot-NVIDIA%20X%20Server%20Settings-1.png[/IMG]

If you wanted the TV to "clone" your main screen, you can drag it over the other window as so:
[IMG]http://dl.dropbox.com/u/424679/Pictures/screenshots/Screenshot-NVIDIA%20X%20Server%20Settings-2.png[/IMG]

Unfortunately, that will only show a portion of my main screen.  If you want a 1-to-1 clone between the main screen and the TV, you will have to set your main screen to the same resolution of the TV, which in your case, would be 1280x720, or as close to it as you can (My own Serval Pro screen and my Gateway secondary screen seems to have 1360x768 as the closest resolution, but I have 16/10 ratio monitors.  Your main monitor is a TV-standard 16/9 ratio, so you might have different resolutions available).  

You can also set the "Position" of the second screen to "Clones", but you will still have the issue where the TV will only see a subset of your main monitor if it can't go up to the same resolution.  In my 40" samsung's case, it go up to 1920x1080 while my Serval has a 1920x1200 screen, so I usually just place the TV in the "middle" of my main monitor (I have to set the Position to "Absolute" to be able to do this).  This actually works out for me anyways as my Gnome panels stay just off screen on my TV while I can see them on my laptop.

---

### Post by mpenda on 2010-08-14
Hello.
I have a Serval Serp6 and I can't get the HDMI audio to work. When I go to System-->Preferences-->Sound under the hardware tab, I only have Analog options.

Video works just fine.

Thanks.

---

### Post by thomasaaron on 2010-08-19
We've got the same problem on our shop computer. Working on it now. I believe we're in contact by email.

---

### Post by reid_rsv869 on 2010-12-22
I have a Serp6 and also want to use HDMI.  Was this issue fixed and if so, can you share any additional info?

thanks

Reid

---

### Post by volkerbradley on 2010-12-22
> **thomasaaron said:**
> We've got the same problem on our shop computer. Working on it now. I believe we're in contact by email.
Hi Thomas,
I saw that you were working on the HDMI-sound issue sometime ago.  What was the final outcome?
I also would like to have sound working when I have connected my laptop to the TV via a HDMI connection.
If HDMI sound still does not work, would an additional SPDIF connection from the computer to the TV provide sound or would the HDMI connection block the sound from the SPDIF connection?
Thanks.

---

### Post by isantop on 2010-12-22
Actually, we've found out this is a bug in Ubuntu, and Audio over HDMI on Nvidia based systems will not work. It is being fixed in 11.04.

For now, SPDIF should work fine, and using Analog until then is also an option.

---

### Post by volkerbradley on 2010-12-22
> **isantop said:**
> Actually, we've found out this is a bug in Ubuntu, and Audio over HDMI on Nvidia based systems will not work. It is being fixed in 11.04.

For now, SPDIF should work fine, and using Analog until then is also an option.
Just finished spending more hours than I care to admit trying to get sound from my computer to play on the TV. So far no luck.  The HDMI video picture is beautiful however.
I have a Samsung model LN-T3253H TV.  This TV has no SPDIF port.  This was confirmed by a Samsung support person.
I tried connecting a 3.5mm audio cable from the headset port on the laptop to the 3.5mm audio port labeled PC IN on the TV.  I then played an audio file on the computer.  There was no sound on the TV.
Do you have any other suggestions?
Thanks.

---

### Post by reid_rsv869 on 2010-12-23
Ian -

Sorry to be so lame but I need a bit of clarity on this...

What's the SPDIF output on my Serp6?  Pretty sure I don't have an SPDIF-out port, so it must be..what...a cable conversion (analog out to SPDIF in on the TV (if it has one) )?  Can that be right? 

Thx

Reid

---

### Post by reid_rsv869 on 2010-12-23
Sorry - must be wrong (who could imagine that? :->  ) The Serp6 spec say's there's a S/PDIF out port.  Never tried it.

thx

---

### Post by volkerbradley on 2010-12-23
> **reid_rsv869 said:**
> Sorry - must be wrong (who could imagine that? :->  ) The Serp6 spec say's there's a S/PDIF out port.  Never tried it.

thx
A post elsewhere states that SPDIF is a type of connection and not a type of connector.  It can be optical or coaxial. TOSLINK, RCA and TS type optical are types of connectors used for SPDIF connections.
Does anyone know what type of SPDIF connector is on this laptop and the name of a manufacturer who makes a cable that would connect to the SPDIF port of the Serval Pro?

---

### Post by Idyll on 2012-01-07
I too have no sound over my HDMI even after enabling the sound thought the settings.  Is this a known issue I suppose?  Would be nice to see an update here in the forum and any work arounds available.

---

### Post by isantop on 2012-01-09
After enabling the HDMI audio, go to the hardware tab and select the HDMI output device. With audio playing in the background, change the "Profile" setting until the sound is audible. This will change depending on the output device connected to the HDMI port, but one of them will work.

---

